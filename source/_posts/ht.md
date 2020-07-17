---
categories: 
- 前端
- HT
tags:
- HT
---
# ht

### node
```javascript

        <style>
            html, body {
                padding: 0px;
                margin: 0px;                
            }            
            .main {
                margin: 0px;
                padding: 0px;
                position: absolute;
                top: 0px;
                bottom: 0px;
                left: 0px;
                right: 0px;
            }
        </style>  

var dataModel = new ht.DataModel(),
graphView = new ht.graph.GraphView(dataModel),
view = graphView.getView();            
view.className = 'main';
document.body.appendChild(view);    
window.addEventListener('resize', function (e) {
   graphView.invalidate();
}, false);     
node1 = new ht.Node();
node1.setName('Node 1');
node1.setStyleMap({ // .s
   'body.color': 'red',
   'select.type': 'circle',
   'select.padding': 3
});
node1.setAttrObject({ // .a            
   age: 35,
   sex: 1,
   hidden: false
});
node1.setPosition(100, 100);// .p
dataModel.add(node1);
dataModel.sm().ss(node1); // sm:getSelectionModel ss:setSelection
```



# 带属性（右侧编辑属性）

```javascript
                dataModel = new ht.DataModel();
                graphView = new ht.graph.GraphView(dataModel);
                propertyView = new ht.widget.PropertyView(dataModel);// 属性view
                splitView = new ht.widget.SplitView(graphView, propertyView);// 分割（最多可传4个参数）
      
                view = splitView.getView();
                view.className = 'main';
                document.body.appendChild(view);    
                window.addEventListener('resize', function (e) {
                    splitView.invalidate();
                }, false);      

				propertyModel = propertyView.getPropertyModel();// 属性model
                
                var property = new ht.Property();
                property.setName('name');   
                property.setDisplayName('Name'); 
                property.setAlign('center');// 中间对齐
                property.setEditable(true);// 可编辑
                propertyModel.add(property);   
                
                property = new ht.Property();
                property.setName('image');   
                property.setDisplayName('Image'); 
                property.setEditable(true);
                property.setEnum({                    
                    values: ['node_image', 'group_image', 'subGraph_image'],
                    labels: ['Node', 'Group', 'SubGraph'],
                    icons: ['node_icon', 'group_icon', 'subGraph_icon']
                });  // 下拉框
                propertyModel.add(property);//添加属性

                property = new ht.Property();
                property.setName('body.color');
                property.setAccessType('style');// 属性类别 style
                property.setValueType('color');
                property.setCategoryName('Style Properties');// 属性类别名称
                propertyModel.add(property);

                property = new ht.Property();
                property.setName('age');
                property.setDisplayName('Age'); 
                property.setAccessType('attr');// 属性类别 Attr
                property.setValueType('int');// 值类型
                property.setAlign('right');
                property.setEditable(true);
                property.setCategoryName('Attr Properties');// 属性类别名称
                propertyModel.add(property); 
                
                property = new ht.Property();
                property.setName('hidden');
                property.setDisplayName('Hidden this node'); 
                property.setColor('red');
                property.setIcon('images/alert.gif');// 图标
                property.setAccessType('attr');
                property.setValueType('boolean');// 布尔类型
                property.setEditable(true);
                property.setCategoryName('Attr Properties');
                propertyModel.add(property);       

                property = new ht.Property();
                property.setName('sex');
                property.setDisplayName('Sex'); 
				property.setColor('red');//颜色
                property.setAccessType('attr');                
                property.setEditable(true);
                property.setEnum([1, 2], ['Male', 'Female']); // 下拉框
                property.setCategoryName('Attr Properties');//属性类别名称
                propertyModel.add(property);  
```

[](https://hightopo.com/codeeditor/index.html?url=https://www.hightopo.com/guide/guide/core/propertyview/examples/example_property.html)



