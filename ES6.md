# ES6

## let（用来声明变量）

1. lei是一个块级作用域，只在块级范围内有效

~~~javascript
if(true){
    let a=10;
}
//lei只在if里面才有效，而var不具备这个块级作用域的特点，例如：
if(true){
    let a=10;
    var num=20;
}
console.log(a)//结果为underfind
console.log(num)//有效
~~~

2 使用let关键字不会有变量提升

```javascript
console.log(a)//a为underfind
let a=10
```

3 let具有暂时性死区

```javascript
var num=10
if(true){
    console.log(num);//为underfind，因为let的特性，会跟这个绑定
    let num=10
}
```

## 	const(声明常量)

1 具有块级作用域

2 必须赋予初始值

```javascript
const a
//1 Uncaught SyntaxError: Missing initializer in const declaration
```

3  常量的值赋予后，不能更改

### let、const、var 的区别

![](D:/%E9%BB%91%E9%A9%AC%E5%89%8D%E7%AB%AF36%E6%9C%9F%EF%BC%882018%E5%B9%B4%EF%BC%89/ES6/JavaScript%20%E9%AB%98%E7%BA%A7_day05/4-%E7%AC%94%E8%AE%B0/images/var&let&const%E5%8C%BA%E5%88%AB.png)

## 箭头函数

`()=>{}`

1 箭头函数是用来简化函数的

2 在箭头函数中，如果函数中只有一句代码，则执行结果就是返回值，函数体的大括号可以省略

```javascript
const sum=(n1,n2)=>{n1+n2}//可以写成const sum=(n1,n2)=>n1+n2
```

3 如果形参只有一个，小括号也可以省略

~~~javascript
const c=(n)=>b//可以写const c=n=>b
~~~

## 剩余参数

`let students=[n1,...n2]//...n2表示剩余参数，接收所剩余的参数`

## find()

```javascript
var arr=[{
    id:1,name:'ds'
},{
    id:2,
    name:'dff'
}];
arr.find((item,idex)=>item.id==2`)
```

## findIndex()

1 用于找出第一个符合条件的数组成员位置，找不到返回-1

```javascript
let arr=[0,5,10,15];
let index=arr.findIndex(item=>item>12);
console.log(index)//3
```

## includes()

表示数组是否包含给定的值，为布尔值

```javascript
[1,2,3].includes(2)//true
```

## 模板字符串

模板字符串用``来拼接，他可以解析变量

```javascript
let name=`张三`;
let say='hello my name is${name}'

```

模板字符串可以调用函数

```javascript
const fn=()=>{'我是函数'}
let html='我是模板字符串${fn}'
```

## startWith()与endWith()

表示参数字符串是否在原字符串的头部或尾部，为布尔值

~~~javascript
let str='hello world!';
stt.startWidth('hello')//true
~~~

## repeat()

表示将字符串重复几次，返回新的字符串

~~~javaScript
'x'.repeat(3)//xxx
~~~

## set数据结构

类似于数组，但是成员的值都是唯一的，不会重复

### 实例方法

- add(value)：添加某个值，返回 Set 结构本身
- delete(value)：删除某个值，返回一个布尔值，表示删除是否成功
- has(value)：返回一个布尔值，表示该值是否为 Set 的成员
- clear()：清除所有成员，没有返回值

```javascript
 const s = new Set();
 s.add(1).add(2).add(3); // 向 set 结构中添加值 
 s.delete(2)             // 删除 set 结构中的2值   
 s.has(1)                // 表示 set 结构中是否有1这个值 返回布尔值 
 s.clear()               // 清除 set 结构中的所有值
 //注意：删除的是元素的值，不是代表的索引
```

### 遍历

et 结构的实例与数组一样，也拥有forEach方法，用于对每个成员执行某种操作，没有返回值。

```javascript
s.forEach(value => console.log(value))

```

## 模块化

在ES6之前，Javascript出现了AMD模块化（主要在require.js上)，CMD模块化（sea.js) ，commont.js模块化

但是AMD与CMD适用于浏览器端的Javascript，commont.js适用于服务端

ES6模块化规范：

- 每个js文件都是一个独立模块
- **导入模块成员**使用**imort**关键字
- **暴露模块成员**使用**export**关键字

### Node.js中通过**babel**体验ES6模块

1 npm install  --save-dev @babel/color @babel/cli @babel/preset-env @babel/node

2 npm install  --save @babel/polyfill

3 项目根目录创建babel.config.js

4 babel.config.js文件内容如下

~~~javascript
const presets=[
    ["@babel/env",{
        targets:{
            edge:"17",
            firefox:"60",
         	chrome:"67",
            safari:"11.1",
        }
    }]
];
module.exports={presets};
~~~

5 通过运行npx babel-node index.js（index.js是文件名）执行代码

### 导出与导入语法

export default为导出

```javascript
export default{
    
}
```

import 接收名称 from '模块标识符'    表示导入

```javascript
import m1 from './m1.js'
```

按需导出与导入

按需导出语法**export**  let s1=10

按需导入语法 **import**  {s1} from '模块标识符'

```javascript
import {s1,s2} from './m1.js'//表示在m1.js中导入s1,s2
```

