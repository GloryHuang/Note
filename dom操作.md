###DOM操作

#####1.appendChild()插入节点

 * 在指定节点的最后一个子节点列表之后添加一个新的子节点。

    语法:

    appendChild(newnode)
    参数:

    newnode：指定追加的节点。

   ![](http://img.mukewang.com/5398fd020001ad4905890193.jpg)

#####2.insertBefore()插入节点

    insertBefore() 方法可在已有的子节点前插入一个新的子节点。

    语法:

    insertBefore(newnode,node);

    参数:

    newnode: 要插入的新节点。

    node: 指定此节点前插入节点。

    我们在来看看下面代码，在指定节点前插入节点。
    
  ![](http://img.mukewang.com/5395318100010c6806960431.jpg)

  运行结果:

    This is a new p
    JavaScript
    HTML

    注意: otest.insertBefore(newnode,node); 也可以改为:  otest.insertBefore(newnode,otest.childNodes[0]); 



#####3.removeChild()删除节点
    removeChild() 方法从子节点列表中删除某个节点。如删除成功，此方法可返回被删除的节点，如失败，则返回 NULL。

    语法:

    nodeObject.removeChild(node)
    参数:

    node ：必需，指定需要删除的节点。

    我们来看看下面代码，删除子点。
    
   ![](http://img.mukewang.com/5399744d000153a306060342.jpg)
    

#####4.replaceChild()替换元素节点

    replaceChild 实现子节点(对象)的替换。返回被替换对象的引用。 

    语法：

    node.replaceChild (newnode,oldnew ) 
    参数：

    newnode : 必需，用于替换 oldnew 的对象。 
    oldnew : 必需，被 newnode 替换的对象。

    我们来看看下面的代码:
    
   ![](http://img.mukewang.com/539557d70001c3ee07190429.jpg)
    

#####5.createElement()创建元素节点

```js
    createElement()方法可创建元素节点。此方法可返回一个 Element 对象。

    语法：

    document.createElement(tagName)
    参数:

    tagName：字符串值，这个字符串用来指明创建元素的类型。

    注意：要与appendChild() 或 insertBefore()方法联合使用，将元素显示在页面中。

    我们来创建一个按钮，代码如下：

      var body = document.body; 
      var input = document.createElement("input");  
      input.type = "button";  
      input.value = "创建一个按钮";  
      body.appendChild(input); 
 
    效果：在HTML文档中，创建一个按钮。

    我们也可以使用setAttribute来设置属性，代码如下：

       var body= document.body;             
       var btn = document.createElement("input");  
       btn.setAttribute("type", "text");  
       btn.setAttribute("name", "q");  
       btn.setAttribute("value", "使用setAttribute");  
       btn.setAttribute("onclick", "javascript:alert('This is a text!');");       
       body.appendChild(btn);  
 
        效果：在HTML文档中，创建一个文本框，使用setAttribute设置属性值。 当点击这个文本框时，会弹出对话框“This is a text!”。
```  

#####6.createTextNode()创建文本节点
    createTextNode() 方法创建新的文本节点，返回新创建的 Text 节点。

    语法：

    document.createTextNode(data)
    参数：

    data : 字符串值，可规定此节点的文本。

    我们来创建一个<div>元素并向其中添加一条消息，代码如下：
    
   ![](http://img.mukewang.com/53951c200001d32d07130554.jpg)
    