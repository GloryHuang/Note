### DOM

```
文档对象模型DOM（Document Object Model）定义访问和处理HTML文档的标准方法。DOM 将HTML文档呈现为带有元素、属性和文本的树结构（节点树）。

HTML文档可以说由节点构成的集合，DOM节点有:

1. 元素节点：上图中<html>、<body>、<p>等都是元素节点，即标签。

2. 文本节点:向用户展示的内容，如<li>...</li>中的JavaScript、DOM、CSS等文本。

3. 属性节点:元素属性，如<a>标签的链接属性href="http://www.imooc.com"。
```

节点属性:
    ![](/assets/5375c953000117ee05240129.jpg)

遍历节点树:
    ![](/assets/53f17a6400017d2905230219.jpg)

```
以上图ul为例，它的父级节点body,它的子节点3个li,它的兄弟结点h2、P。
```

DOM操作:
   ![](/assets/538d29da000152db05360278.jpg)


###节点属性

    在文档对象模型 (DOM) 中，每个节点都是一个对象。DOM 节点有三个重要的属性 ：

    1. nodeName : 节点的名称

    2. nodeValue ：节点的值

    3. nodeType ：节点的类型

    一、nodeName 属性: 节点的名称，是只读的。

    1. 元素节点的 nodeName 与标签名相同
    2. 属性节点的 nodeName 是属性的名称
    3. 文本节点的 nodeName 永远是 #text
    4. 文档节点的 nodeName 永远是 #document

    二、nodeValue 属性：节点的值

    1. 元素节点的 nodeValue 是 undefined 或 null
    2. 文本节点的 nodeValue 是文本自身
    3. 属性节点的 nodeValue 是属性的值

    三、nodeType 属性: 节点的类型，是只读的。以下常用的几种结点类型:

    元素类型    节点类型
      元素          1
      属性          2
      文本          3
      注释          8
      文档          9



