---
categories: 
- 前端
- Node
tags:
- Node
- fs
---
# 文件模块  fs

### **检测文件是否存在**

- fs.stat/fs.statSync
```javascript
// 同步
// cosnt res = fs.statSync('./test01.js') //同步
// res.isDirectory(); //false
// res.isFile(); //true
// const res = fs.statSync('./test999.js') //找不到的文件直接报错

// 异步
  fs.stat('./test01.js',(err, res)=>{
    if(err){
        // 出错： 如文件不存在
      console.log(err)
    }else{
        console.log(res.isDirectory()); //false
        console.log(res.isFile()); //true
    }
  });
```
### 创建文件

- fs.mkdir
```javascript
// 同步
// fs.mkdir('demo',(err)=>{
// 成功没有返回参数
//   if(err){
//     console.log(err);
//   }else{
//     console.log('创建成功');
//   }
// })

// 异步
 fs.mkdirSync('demo2')
```

### （新建）写入文件（覆盖内容）
- fs.writeFile
```javascript
// 异步
fs.writeFile('hello','hehe1',(err)=>{
  if(err){
    console.log(err)
  }else{
    console.log('写入成功')
  }
});
// 同步
// fs.writeFileSync('hello','hehe1')
```
### （新建）追加文件（追加内容）
- fs.appendFile
```javascript
// 异步
// fs.appendFile('hello','hehe1',(err)=>{
//   if(err){
//     console.log(err)
//   }else{
//     console.log('追加写入成功')
//   }
// });
// 同步
// fs.appendFileSync('hello','hehe1')
```
###  读取文件
- fs.readFile
```javascript
// 异步
// fs.readFile('hello',(err, res)=>{
//   if(err){
//     console.log(err)
//   }else{
//     console.log(res) // buffer
//     console.log(res.toString()) //字符输出
//   }
// });
// 同步
// fs.readFileSync('hello').toString()
```
### 读取文件目录

```javascript
// 读取文件目录
fs.readdir('hello',(err, res)=>{
  if(err){
    console.log(err)
  }else{
    console.log(res) //文件名列表: [] 
  }
});
// console.log(fs.readdirSync('hello'))
```
### 重命名（可移动覆盖）

```javascript
// 读取文件目录
// 异步
fs.rename('./dd.js','./hello/dd.js',(err)=>{
  if(err){
    console.log(err)
  }else{
    console.log('重命名成功')
  }
})
// fs.renameSync('./hello/dd.js','gg.js');
```
### 删除文件
```javascript
// 删除文件
// 异步
fs.unlink('./dd.js', (error) =>{
  if (error) {
  console.log(error)
  } else {
  console.log('成功的删除文件')
  }
})
// fs.unlinkSync('./dd/dd.js')
```
### 删除文件夹
```javascript
// 删除文件夹
// 异步
fs.rmdir('./dd', (error) =>{
  if (error) {// 文件夹非空会报错
  console.log(error)
  } else {
  console.log('成功的删除了目录：logs')
  }
})
// fs.rmdirSync('./dd')
```
### 相关包
- mkdirp

### 管道流
 - **读取文件流**

 ```javascript
var readStream=fs.createReadStream('./data/input.txt');
var count=0;
var str='';
readStream.on('data',(data)=>{
    str+=data;
    count++;
})
readStream.on('end',()=>{
    console.log(str)
    console.log(count)
})
readStream.on('error',(err)=>{
    console.log(err);   
})
 ```
 - **写入文件流**

 ```javascript
var str = '';
for(var i=0;i<500;i++){
    str+='我是从数据库获取的数据，我要保存起来1111\n';
}
var writeStream=fs.createWriteStream('./data/output.txt');
// 标记文件末尾，否则finish不会触发
writeStream.end();
writeStream.on('finish',()=>{
    console.log('写入完成');
})
 ```
 - **管道流**

```javascript
const fs = require('fs');
const readStream = fs.createReadStream('./data/demo.zip')
const writeStream = fs.createWriteStream('hehe.zip')
// <source>.pipe(<target>)
readStream.pipe(writeStream);
```

