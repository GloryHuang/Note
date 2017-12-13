###渲染机制类

####什么是DOCTYPE及作用
    
    DTD（document type definition,文档类型定义）是一系列的语法规则,用来定义XML或(X)HTML的文件类型.浏览器会使用它来判断文档类型,决定使用何种协议来解析,以及切换浏览器模式。
    DOCTYPE是用来声明文档类型和DTD规范的,一个主要的用途便是文件的合法性验证。如果文件代码不合法,那么浏览器解析便会出现一些差错
    
![](/assets/QQ截图20171213183045.png)

    
####浏览器的渲染过程
    
![](/assets/QQ截图20171213183244.png)
    
    把HTML转换成DOM Tree
    把CSS转换成CSS Tree

####重排Reflow



####重绘Repaint


####布局Layout