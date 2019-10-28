## redux优势：
1、单一数据源 Store 状态树  
2、状态只读 不能直接写入redux状态 通过reducer  
3、状态只能通过纯函数改变
  
## 纯函数：
一个函数的返回结果只依赖于它的参数，并且在执行过程里面没有副作用（改变其他变量）
  
## MVC与MVVM：
### MVC：
Model：模型对象负责在数据库中存取数据  
View：视图是依据模型数据创建的  
Controller：控制器负责从视图读取数据，控制用户输入，并向模型发送数据  

### MVVM：
ViewModel：Model（数据层）-View（视图层）-ViewModel（数据视图层），是一种<b>双向数据绑定</b>的响应式框架，
数据驱动视图，数据变化不需要修改DOM，直接更新DOM。
