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

    * 定义:
    DOM结构中各个元素都有自己的盒子(模型),这些都需要浏览器根据各种样式来计算并根据结果将元素放到它该出现的位置,这个过程称为reflow
    
    * 触发Reflow:
    
       * 当你增加、删除、修改DOM节点时,会导致Reflow和Repaint
       * 当你移动DOM的位置,或是搞个动画的时候
       * 当你修改CSS样式的时候
       * 当你Resize窗口的时候(移动端没有这个问题),或者是滚动的时候
       * 当你修改网页的默认字体时    
    
    
####重绘Repaint
    
    * 定义：
        当各种盒子的位置、大小以及其他属性,例如颜色、字体大小等都确定下来之后,浏览器于是把这些元素都按照各种的属性绘制了一遍,于是页面的内容就出现了,这个过程称之为Repaint
        
    * 触发Repaint
    
        * DOM改动
        * CSS改动
    
    

####布局Layout