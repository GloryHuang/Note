###页面性能类

####提升页面性能的方法有哪些?
    
    1.资源压缩合并、减少HTTP请求
    2.非核心代码异步加载--->异步加载的方式--->异步加载的区别
    3.利用非浏览器缓存--->缓存的分类--->缓存的原理
    4.使用CDN
    5.预解析DNS
    
    <meta http-equiv="x-dns-prefetch-control"content="on">
    <link rel="dns-prefetch" href="//host_name_to_prefetch.com">
    
    页面中的所有的a标签,在高级的浏览器中是默认的打开了DNS预解析的这是浏览器的功能,但是如果这个页面是HTTPS协议开头的,很多浏览器是默认关闭DNS预解析的。
    
    
####异步加载
    
    * 异步加载的方式
        
        * 动态脚本加载
        * defer
        * async
        
        
    * 异步加载的区别
    
        * defer是在HTML解析完之后才会执行,如果是多个,按找加载的顺序依次执行
        * async是在加载完之后立即执行的,如果是多个,执行顺序和加载顺序无关
        
        