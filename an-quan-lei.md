###安全类

* CSRF

* XSS


####CSRF    


* 基本概念和缩写

    * CSRF，通常称为跨站请求伪造，英文名Cross-site request forgery 缩写CSRF 


* 攻击原理

    * 登录过后记录cookie，其他网站利用接口，用cookie攻击
    
    ![](/assets/QQ截图20180307173357.png)

* 防御措施

    * Token验证(服务器自动向本地存储Token,访问各种接口,没有携带Token,就不能通过验证)
    
    * Referer验证(判断页面来源是不是本站点下的页面是的话执行操作,不是则拦截)
    
    * 隐藏令牌(和token类似把令牌放在HTTP头中,不放在链接上)


####XSS

    * 基本概念和缩写
    
        * XSS（cross-site script，跨站脚本攻击） 
    
    * 攻击原理
    
        * 不需要登录验证，核心原理就是向页面注入脚本 
        
        
    * 防御措施
    
    
    * CSRF和XSS的区别
    
        * XSS是向页面注入js运行，
        * CSRF是利用本身的漏洞去执行接口，
        * CSRF要登录网站