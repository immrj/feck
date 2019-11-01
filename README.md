## redux优势
1、单一数据源 Store 状态树  
2、状态只读 不能直接写入redux状态 通过reducer  
3、状态只能通过纯函数改变
  
## 纯函数
一个函数的返回结果只依赖于它的参数，并且在执行过程里面没有副作用（改变其他变量）
  
## MVC与MVVM
Model：模型对象负责在数据库中存取数据  
View：视图是依据模型数据创建的  

#### MVC
Controller：控制器负责从视图读取数据，控制用户输入，并向模型发送数据  

#### MVVM
ViewModel：Model（数据层）-View（视图层）-ViewModel（数据视图层），是一种<b>双向数据绑定</b>的响应式框架，
数据驱动视图，数据变化不需要修改DOM，直接更新DOM。

## Symbol
ES6中引入的一种新的基础数据类型，每个Symbol实例都是唯一的，当你比较两个Symbol实例的时候，将总会返回false。
##### Symbol() 和 Symbol.for()
``` JS
let s1 = Symbol()
let s2 = Symbol('another symbol')
let s3 = Symbol('another symbol')

s1 === s2 // false
s2 === s3 // false


let gs1 = Symbol.for('global_symbol_1')  //注册一个全局Symbol
let gs2 = Symbol.for('global_symbol_1')  //获取全局Symbol

gs1 === gs2  // true
```
## Reflect
ES6中为操作对象而提供的新API。  
``` JS  
var obj= {
  name: "chen",
};
Reflect.has(obj, 'name');  // true
Reflect.deleteProperty(obj, 'name');
Reflect.ownKeys (target); // 能获取到以Symbol为key的对象的所以key
```

## 前端工程化
* 库/框架选型  
React、Vue、Angular、jQuery、Antd...  
* 构建、管理工具  
gulp、grunt、webpack、git、svn...
* JS/CSS模块化开发  
less、sass
* 组件化开发与资源管理  
组件开发、复用、静态资源CDN
* 规范化  
编码规范、接口文档及规范、分支管理规范、code review ...

## 防抖与截流
防抖和节流的作用都是防止函数多次调用。区别在于，防抖动是将多次执行变为最后一次执行，节流是将多次执行变成每隔一段时间执行。
 ``` JS
 // 简单的防抖
 // func是用户传入需要防抖的函数
 // wait是等待时间
 const debounce = (func, wait = 50) => {
   // 缓存一个定时器id
   let timer = 0
   // 这里返回的函数是每次用户实际调用的防抖函数
   // 如果已经设定过定时器了就清空上一次的定时器
   // 开始一个新的定时器，延迟执行用户传入的方法
   return function(...args) {
     if (timer) clearTimeout(timer)
     timer = setTimeout(() => {
       func.apply(this, args)
     }, wait)
   }
 }
 // 不难看出如果用户调用该函数的间隔小于wait的情况下，上一次的时间还未到就被清除了，并不会执行函数
 ```
 
 ## 前端性能优化
缓存、CDN、减少请求数量、减小资源大小、优化资源加载、减少重绘回流、懒加载、图片优化...  
预加载`<link rel="preload" href="http://example.com" />`  
预渲染`<link rel="prerender" href="http://example.com" />`  
Webpack优化：production 模式、tree shaking（移除没有使用的代码）、小图base64、按需加载...
