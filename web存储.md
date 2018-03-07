###Web存储


* document.cookie（传统的方式）
    存储的大小只有4K，而且解析起来相当复杂

* sessionStorage和localstorage
    
    * 设置读取方便。
    * 容量较大，sessionStroage约为5M、 localstorage约为20M
    * 只能存储字符串,可以将对象JSON.stringify()编码后存储

    

####window.sessionStoage

* 生命周期为关闭浏览器窗口
    
* 在同一个窗口下数据可以共享

####window.localStorage

* 永久有效,除非用户手动删除
    
* 可以多窗口共享
    


#####方法详解

```js
setItem(key,value);  设置存储内容
getItem(key);        读取存储内容
removeItem(key);     删除键值为key的存储内容
clear();             清空所有存储的内容
key(n)               以索引值来获取内容
```