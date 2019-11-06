## JSBridge的实现原理

### JS调用Native

#### 注入api/对象

通过WebView提供的接口向js的context（window）注入一个对象或者方法，js调用时，直接执行对应的Native代码逻辑。  
缺点：  
在4.2之前，Android注入JavaScript对象的接口是addJavascriptInterface，但是这个接口有漏洞。4.2以后采用新的接口@JavascriptInterface解决。

#### 拦截URL scheme （cordova）

在UIWebView内发起的所有网络请求，都可以通过delegate函数在Native层得到通知。这样，我们就可以在UIWebView内发起一个自定义的网络请求，
通常是这样的格式：`jsbridge://methodName?param1=value1&param2=value2`
于是Native拦截的请求中，我们只要发现是`jsbridge://`开头的地址，就不进行内容的加载，转而执行相应的调用逻辑。  
`支持iOS6`   
缺点：  
使用iframe.src发送URL SCHEME会有url长度的隐患。  
创建请求，需要一定的耗时，比注入API的方式调用同样的功能，耗时会较长。  

`正常来说是可以通过window.location.href达到发起网络请求的效果的，但是有一个很严重的问题，就是如果我们连续多次修改window.location.href的值，
在Native层只能接收到最后一次请求，前面的请求都会被忽略掉。所以JS端发起网络请求的时候，需要使用iframe，这样就可以避免这个问题。`

#### 改写浏览器原有对象

使用prompt,console.log,alert方式，在android webview这一层可以重写这些方法。  
一般常使用prompt，因为这个在js里使用的不多，用来和native通讯副作用比较少。

### Native调用JS

Native调用js实际就是执行拼接js字符串，从外部调用对应方法，返回js执行结果。因此js方法必须放在全局的Window上。
