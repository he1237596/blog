---
categories: 
- 前端
- 小程序
tags:
- 小程序
- webview
---
# 小程序web-view

背景：公司要做一个统计的echarts图，数据返回为数组，长度大概在5000，直接集成echarts使用，发现dataZoom拖拽卡顿严重，（其实主要是数据返回后渲染时间较长，渲染完成还是OK滴），控制台查看发现应该是微信小程序平台的性能瓶颈限制，考虑使用web-view突破

由于公司使用的是Taro框架来做小程序的，所以遵循Reac的基本开发规范,原生也是同理，直接上代码吧

### HistoryLine组件

```react
import Taro, { Component } from '@tarojs/taro'
// 引入 WebView 组件（原生一致）
import { WebView } from '@tarojs/components'

class HistoryLine extends Component {
  config = {
    navigationBarTitleText: "历史曲线",
    pageOrientation: 'landscape',
  };

  render () {
      // 路由传参
    const { params: { equipmentGroupAttrName, groupId } } = this.$router;
      // 在web页发请求需要小程序的请求头信息(后台接口校验使用，我存在本地，看你喜欢咯)
      // 注意中文字符会被编码，就不用我说了吧，转码！！！
    console.log(`https://xxx.com/area-simple.html?equipmentGroupAttrName=${encodeURI(equipmentGroupAttrName)}&groupId=${groupId}`)
    // console.log(`http://192.168.1.136:5500/area-simple.html?equipmentGroupAttrName=${encodeURI(equipmentGroupAttrName)}&groupId=${groupId}`)
    return (
      <WebView src={`https://xxx.com/area-simple.html?equipmentGroupAttrName=${equipmentGroupAttrName}&groupId=${groupId}`}  />
      // <WebView src={`http://192.168.1.136:5500/area-simple.html?equipmentGroupAttrName=${equipmentGroupAttrName}&groupId=${groupId}`}  />
    )
  }
}
export default HistoryLine;
```

### H5页面

```web-idl
// 主要代码
<div class="lineChart" id="container"></div>
    <script type="text/javascript">
    // 获取传参
      function getQueryVariable(variable) {
        var query = window.location.search.substring(1);
        var vars = query.split("&");
        for (var i = 0; i < vars.length; i++) {
          var pair = vars[i].split("=");
          if (pair[0] == variable) {
            return pair[1];
          }
        }
        return false;
      }

      console.log(window.location);
      // 中文反编码
        var equipmentGroupAttrName = decodeURI(getQueryVariable('equipmentGroupAttrName'));
        var groupId = getQueryVariable('groupId');
  	// 其他业务逻辑（做的echart图，就不放了）
    </script>
```

##### 注意：

1. 小程序在开发工具上，web-view的h5页面可以是放在本地服务上的web，页面内访问的接口可以是非https非域名的接口（需要设置开发工具不校验https和域名）
2. 在手机调试时，即便打开开发者模式，以上环境，H5页面内也无法正常访问接口
   - 如果h5页面部署在本地环境，手机运行到同一wifi环境下，即可正常访问web，无法访问接口
   - 如果h5页面部署在外网环境，如果web服务器时http协议，接口是http协议，可以访问web，无法访问接口
   - 如果h5页面部署在外网环境，如果web服务器时http协议，接口是https协议，可以访问web，可以访问接口
   - 如果h5页面部署在外网环境，如果web服务器时https协议，接口是http协议，可以访问web，无法访问接口（web控制台会报错，提示不支持调用http协议）
   - 如果h5页面部署在外网环境，如果web服务器时https协议，接口是https协议，可以访问web，可以访问接口（完美）
3. 正式发布，必须为2中的最后一条规则，且需要配置微信小程序访问域名白名单：添加H5页面所在服务器域名及其内访问的api域名，规则为：https+备案域名