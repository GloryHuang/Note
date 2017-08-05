###DOM操作

#####1.appendChild()插入节点

    在指定节点的最后一个子节点列表之后添加一个新的子节点。

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

    createElement()方法可创建元素节点。此方法可返回一个 Element 对象。
    
    