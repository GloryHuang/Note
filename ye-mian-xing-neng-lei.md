###页面性能类

####提升页面性能的方法有哪些?
    
+ 资源压缩合并、减少HTTP请求
+ 非核心代码异步加载--->异步加载的方式--->异步加载的区别
+ 利用非浏览器缓存--->缓存的分类--->缓存的原理
+ 使用CDN
+ 预解析DNS
 
```html  
  
    <meta http-equiv="x-dns-prefetch-control"content="on">
    <link rel="dns-prefetch" href="//host_name_to_prefetch.com">

```
    
页面中的所有的a标签,在高级的浏览器中是默认的打开了DNS预解析的这是浏览器的功能,但是如果这个页面是HTTPS协议开头的,很多浏览器是默认关闭DNS预解析的。
    
    
####异步加载
    
* 异步加载的方式
        
    * 动态脚本加载(用JS创建一个标签,加载到body上,动态创建脚本)
    
    * defer
    
    * async
        
        
* 异步加载的区别
    
    * defer是在HTML解析完之后才会执行,如果是多个,按找加载的顺序依次执行
    
    * async是在加载完之后立即执行的,如果是多个,执行顺序和加载顺序无关
        
        
####浏览器缓存


* 缓存的类型
        
     * 强缓存(在此时间之前,不会和服务器通信,直接从浏览器缓存里拿出来用)
         
         Expires Expires：Thu,21 Jan 2017 23:39:02 GMT
         Cache-Control:Cache-Control:max-age=3600 (相对时间)
             
         拿到资源后在3600秒之内,如果有就不再请求,直接从浏览器里拿
         如果两个请求都发了,直接以后者的请求为准
             
     * 协商缓存
         
          Last-Modifled if-Modifile-Slince  Last-Modifiled:Wed,26 Jan 2017 00:35:11 GMT
          Etag  if-None-Match 
        
        