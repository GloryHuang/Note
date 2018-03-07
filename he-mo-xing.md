###盒模型

####基本概念:盒模型+IE模型

* 文档中每个元素都会被描述为一个矩形盒子，盒子有一个边界，分别为margin edge，border edge，padding edge，content edge。盒子模型分为标准盒子模型和IE盒子模型（微软没有遵从W3C标准）

    
####标准模型和IE模型的区别

* 这两者的关键差别在于：W3C盒子模型——属性高（height）和属性宽（width）这两个值不包括（padding）和边框（border）；IE盒子模型——属性高（height）和属性宽（width）这两个值包含填充（padding）和边框（border）。
                
* 就是计算宽度和高度的不同

####CSS如何设置这两种模型？

* ”标准模式”下各个浏览器是没有区别的，以宽度为例：总宽度=marginLeft+borderLeft+paddingLeft+contentWidth+paddingRight+borderRight+marginRight（W3C标准盒子模型）。页面在”怪异模式”下，css中为元素的width和height设置的值在标准浏览器和ie系列（ie9除外）里的代表的含义是不同的（IE盒子模型）。也就是说在“怪异模式”下ie浏览器使用的IE盒子模型。

* 标准模式和怪异模式些来由？ 

    * 在HTML和CSS的标准化未完成之前，各个浏览器对于HTML和CSS的解析有各自不同的实现，而有很多旧的网页都是按照这些非标准的实现去设计的。在HTML和CSS标准确定以后，浏览器一方面要按照标准去实现对HTML和CSS的支持，另一方面又要保证对非标准的旧网页设计的后向兼容性。因此，现代的浏览器一般都有两种渲染模式：标准模式和怪异模式。在标准模式下，浏览器按照HTML和CSS标准对文档进行解析和渲染；在怪异模式下，浏览器则按照旧有的非标准的实现方式对文档进行解析和渲染。这样的话，对于旧有的网页，浏览器启动怪异模式，就能够使得旧网页正常显示；对于新的网页，则可以先启动标准模式，使得新网页能够用HTML和CSS标准特性。

* 浏览器如何确定使用哪种渲染模式？

    * 知道了这两种渲染模式的来由，那剩下的问题就是浏览器如何能够确定应该使用哪种模式了。其实归根结底就是，浏览器如何能将旧网页和新网页区分开来。 

    * 平常编写网页的时候，一般都会将见到HTML文档的头部会有文档类型声明：DOCTYpe。当浏览器遇到正确的文档声明时，浏览器就会启动标准模式，按照指定的文档类型标准解析和渲染文档。而对于旧有的网页，由于网页编写的当时标准还没有确定，所以一般是不会有文档类型声明的。所以，对于没有文档类型声明或者文档类型声明不正确的文档，浏览器就会认为他是一个旧的HTML文档，就会使用怪异模式解析和渲染该文档。关于DOCTYPE的更详细说明，请戳这里DOCTYPE声明作用和用法详解

* 如何兼容IE模型 

    * 前提是页面处于”怪异模式”，“标准模式”不存在兼容性问题。 
    
        *  假设内容的宽度必须固定为100px
        
        *  wrapper
      
```css

    #box {  
        width:100px !important; // ie9,ff,chrome,opera这样的标准浏览器
        width:160px; //所有的浏览器；它的本意是只对不认识!important的设置。可是ie7、ie8也认识
        +width:160px!important;//ie7
        width:160px/0!important;//ie8
        padding:0 10px;border:20px solid blue;margin:70px;  
    }  


        #box{
             width:100px;
             margin:70px;
             float:left;
        }
        .wrapper{
           padding:0 10px;border:20px solid blue;
        }
```
    
###标准模型(宽高不包含padding和border)
    
![](/assets/QQ截图20180130212438.png)
        
###IE模型(宽高包含padding和border)

![](/assets/QQ截图20180130212326.png)

####CSS是如何设置这种模型

```css

    浏览器默认的是content-box
    box-sizing:content-box;(标准模型)将采用标准模式解析计算
    box-sizing:border-box;(IE模型)将采用怪异模式解析计算
    
```    

####JS如何设置获取盒模型对应的宽和高

```js

    dom.style.width/height(只能取内联样式)
    
    dom.currentStyle.width/height(拿到渲染以后的宽高)(仅IE支持)
    
    window.getComputedStyle(dom).width/height(兼容FF和Chrome)(通用性更好一些)
    
    dom.getBoundingClientRect().width/height
    计算元素在视窗绝对位置四个元素left top height width
```

####实例题(根据盒模型解释边距重叠)

    ovflow:hidden;(创建了一个BFC)
   

####BFC(边距重叠解决方案)

* BFC的基本概念
    
    * 块级格式化上下文
    

* BFC的原理(BFC的渲染规则)
    
    * BFC元素垂直方向的边距发生重叠 
    
    * BFC的区域不会与浮动元素的box重叠(清除浮动)
    
    * BFC是页面上一个独立的容器，内外的元素不会相互影响 
    
    * 计算BFC的高度时，浮动元素也参与计算
    

* 如何创建BFC

    * float值不为none 
    
    * position为absolute或fixed 
    
    * display为inline-block，table-cell，table-caption，flex；
    
    * overflow不为visible
    
    