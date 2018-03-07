###通信类

####什么是同源策略和限制

源：协议、域名、端口

同源策源限制从一个源加载的文档或脚本如何与来自另一个源的资源进行交互。这是一个用于隔离潜在恶意文件的关键的安全机制。 

* Cookie、LocalStorage和IndexDB无法读取 

* DOM无法获得 

* Ajax请求不能发送 (Ajax只适合同源通信,跨域不行)


####前后端如何通信

* Ajax(同源下的通信方式)

* WebSocket(不受同源策略的限制)

* CORS(支持跨域通信,也支持同源通信,是一种新的通信方式及标准)

####如何创建Ajax

* XMLHttpRequest对象的工作流程

* 兼容性处理
(XMLHttpRequest只有高级浏览器中支持，低版本中要用xmlhttp=new ActiveXObject(“Microsoft.XMLHTTP”);)

* 事件的触发条件

* 事件的触发顺序


####跨域通信的几种方式

* JSONP(利用Script标签的异步加载来实现的)
![](/assets/QQ图片20180307170052.png)

* Hash(hash改变页面不刷新,url中?后search改变页面是会刷新的,所以search不能做跨域通信)



* postMessage(H5中新增加的处理跨域通信的方式)

* WebSocket(不受同源策略限制)

* CORS(新出的通信标准,是支持跨域通信的Ajax,浏览器会在HTTP头中加一个Orign来支持跨域)


