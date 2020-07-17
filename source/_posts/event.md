---
categories: 
- 前端
- Node
tags:
- 事件对象
---
### 事件对象events
- **EventEmitter**

```javascript
const events = require('events');

// 创建事件对象
var eventEmitter = new events.EventEmitter();

setInterval(() => {
// 广播
  eventEmitter.emit('my_event');

}, 3000);
// 监听
eventEmitter.on('my_event', () => {

  console.log('data received succesfully.');

});

// eventEmitter.emit('my_event');
```

