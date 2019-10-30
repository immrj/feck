## redux优势：
1、单一数据源 Store 状态树  
2、状态只读 不能直接写入redux状态 通过reducer  
3、状态只能通过纯函数改变
  
## 纯函数：
一个函数的返回结果只依赖于它的参数，并且在执行过程里面没有副作用（改变其他变量）
  
## MVC与MVVM：
Model：模型对象负责在数据库中存取数据  
View：视图是依据模型数据创建的  

### MVC：
Controller：控制器负责从视图读取数据，控制用户输入，并向模型发送数据  

### MVVM：
ViewModel：Model（数据层）-View（视图层）-ViewModel（数据视图层），是一种<b>双向数据绑定</b>的响应式框架，
数据驱动视图，数据变化不需要修改DOM，直接更新DOM。

## Symbol：
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
## Reflect:
ES6中为操作对象而提供的新API。  
``` JS  
var obj= {
  name: "chen",
};
Reflect.has(obj, 'name');  // true
Reflect.deleteProperty(obj, 'name');
Reflect.ownKeys (target); // 能获取到以Symbol为key的对象的所以key
```
