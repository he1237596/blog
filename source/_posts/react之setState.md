---
categories: 
- 前端
- React
tags:
- React
---
```javascript
	//批量执行
	state = {count: 1}
	// 只会执行一次 count=2（除非传入第二个参数回调函数）
	this.setState({
		count: this.state.count+1
	})
	this.setState({
		count: this.state.count+1
	})
	this.setState({
		count: this.state.count+1
	}) //执行此动作
	
	// 多次执行 count=4
	this.setState(prevState => {
		return {
			count: prevState.count+1
		}
	})
	this.setState(prevState => {
		return {
			count: prevState.count+1
		}
	})
	this.setState(prevState => {
		return {
			count: prevState.count+1
		}
	})
```