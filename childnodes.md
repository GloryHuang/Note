###访问子节点childNodes



   访问选定元素节点下的所有子节点的列表，返回的值可以看作是一个数组，他具有length属性。

   * 语法：

   elementNode.childNodes

   * 注意:
    
   如果选定的节点没有子节点，则该属性返回不包含节点的 NodeList。
    
   ![](/assets/538405fa00010e6c05630357.jpg)


  * 运行结果:

   * IE:

       UL子节点个数:3
       
       节点类型:1
       
       
    * 其它浏览器:

       UL子节点个数:7
       
       节点类型:3
   
* 注意:

     1. IE全系列、firefox、chrome、opera、safari兼容问题

     2. 节点之间的空白符，在firefox、chrome、opera、safari浏览器是文本节点，所以IE是3，其它浏览器是7，如下图所示:

   ![](/assets/538d2b8a000163e303430127.jpg)

    如果把代码改成这样:

    <ul><li>javascript</li><li>jQuery</li><li>PHP</li></ul>

    运行结果:（IE和其它浏览器结果是一样的）

      UL子节点个数:3
      节点类型:1

