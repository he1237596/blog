---
categories: 
- 前端
- React
tags:
- React
---
```javascript
import React, { createContext } from 'react'
const Test = (props) => {
  console.log(props)  // {a: 1}
  console.log(props.a) // 1
  return <div>ddddddddddd</div>
}
const Context = createContext();
console.log(Context)
const TestPage = () => {
  const store = { a: 1 };
  return (
    <Context.Provider value={store}>
      <Context.Consumer>
        {store => <Test {...store} />}
      </Context.Consumer>
      <div>
        测试页面
      </div>
    </Context.Provider>
  )
}
export default TestPage;
```

```javascript
import React, { createContext, useContext } from 'react'
const Test = () => {
  const { a } = useContext(Context);
  console.log(a) // 1
  return <div>ddddddddddd</div>
}
const Context = createContext();
const TestPage = () => {
  const store = { a: 1 }
  return (
    <Context.Provider value={store}>
      <Test />
      <div>
        测试页面
          </div>
    </Context.Provider>
  )
}
```

