---
categories: 
- 前端
- 其他
---
# 柯里化

柯里化是函数式编程编程的常用技巧： 将多参数函数转换成单参数函数，这些单参数函数的返回值也是函数。

```javascript
const add = (x,y) => x + y; 
// 变形
const add = x => y => x + y;
const add1 = add1(1);
add1(2); //3
add2(3)	//4
// 传入第一个参数后，第一个值（x）被保留起来，返回的第二个函数可以多次复用
```

# 组合