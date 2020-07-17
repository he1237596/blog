﻿---
categories: 
- 前端
- React
tags:
- react-redux
---

>### state

场景: 

1. state其实就是一个对象,state的各种属性是用来共享的数据

   ```js
	const state = {
   		num: 0
	}
   ```

>### action

2.是把数据从应用传递到数据的唯一来源(我理解的就是事件描述:事件名type和其他可能包括新状态属性的参数),通过store.dispatch()调用该函数

   ```js
    const add = () => {
      return {
        type: 'ADD'
      }
    }
   ```
>### reducer

3. 更新state的多个事件或者说是方法的集合,接收更新前的state和action(根据action返回的type类型,执行对应动作,返回新的state),以更新state

   ```js
   function counter (state={默认值}, action) {
    switch (action.type) {
    case 'ADD':
      return {
        ...state,
        num: state.num + 1
      }
    case 'MINUS':
      return {
        ...state,
        num: state.num - 1
      }
    default:
      return state
    }
   }
   ```
>### store

4. 将多个reducer进行合并,保存到store

   ```js
    import { createStore, applyMiddleware,combineReducers } from 'redux'
    import thunkMiddleware from 'redux-thunk'
    import { createLogger } from 'redux-logger'

    import counter from './counter/reducers' //reducer1
    import login from './login/reducers'  //reducer2

    const rootReducer = combineReducers({
      counter,
      login
    })

    const middlewares = [
      thunkMiddleware,
      createLogger()
    ]

    export default function configStore () {
      const store = createStore(rootReducer, applyMiddleware(...middlewares))
      return store
    }
   ```
5. 在项目入口使用store
   ```js
   		import { Provider } from '@tarojs/redux'
   		
   			<Provider store={store}>
            	<Index />
			</Provider>
   ```
6. 项目内dispatch
   ```js
   import { counter } from '../../store/counter/actions'
    @connect(({ login }) => ({
      login
    }), (dispatch) => ({
    //传递事件onSubmit到当前组件
      onSubmit1(data, fn) {
        dispatch(counter(data))
      },
/*   onSubmit2(data, fn) {
       //submit可以为一个promise的请求等异步操作   
       dispatch(submit(data)).then(res => {
         if (fn)
           fn(res)
       })
      },
   */
    }))
   ```


















