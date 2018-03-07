###盒模型

####基本概念:盒模型+IE模型

    border+margin+padding+content
    
####标准模型和IE模型的区别
        
    就是计算宽度和高度的不同
    
###标准模型(不包含padding和border)
    
![](/assets/QQ截图20180130212438.png)
        
###IE模型

![](/assets/QQ截图20180130212326.png)

####CSS是如何设置这种模型

```css

    浏览器默认的是content-box
    box-sizing:content-box;(标准模型)
    box-sizing:border-box;(IE模型)
    
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
    
    