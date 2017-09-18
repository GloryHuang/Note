#####Web存储


    1.document.cookie（传统的方式）
    存储的大小只有4K，而且解析起来相当复杂

    2.sessionStorage和localstorage
    
    1）设置读取方便。
    2）容量较大，sessionStroage约为5M、 localstorage约为20M
    3）只能存储字符串,可以将对象JSON.stringify()编码后存储