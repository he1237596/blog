---
categories: 
- 前端
- Npm
tags:
- npm
- nrm
---

清除npm资源缓存
```
	npm cache clean -f
```
用代码更改npm的配置文件
```
	npm config set registry http://registry.npm.taobao.org
```
查看远程包版本信息
```
	npm info <packageName>
```
查看本地包版本信息
```
	npm info <packageName>
```
安装nrm
```
	npm install -g nrm
```
查看镜像列表
```
	nrm ls
```
在nrm添加自己的镜像地址s
```
	nrm add resource_name resource_url
```
切换镜像
```
	nrm use taobao
```
删除
```
	nrm del r_name
```
测试镜像的相应速度
```
	nrm test r_name
```
