### Scroll和Offset、Client



scrollHeight和scrollWidth，获取网页内容高度和宽度。

一、针对IE、Opera:

scrollHeight 是网页内容实际高度，可以小于 clientHeight。

二、针对NS、FF:

scrollHeight 是网页内容高度，不过最小值是 clientHeight。也就是说网页内容实际高度小于 clientHeight 时，scrollHeight 返回 clientHeight 。

三、浏览器兼容性

```js


var w=document.documentElement.scrollWidth|| document.body.scrollWidth;
var h=document.documentElement.scrollHeight|| document.body.scrollHeight;

注意:区分大小写

scrollHeight和scrollWidth还可获取Dom元素中内容实际占用的高度和宽度。

```

#####网页尺寸offsetHeight

    offsetHeight和offsetWidth，获取网页内容高度和宽度(包括滚动条等边线，会随窗口的显示大小改变)。

一、值

offsetHeight = clientHeight + 滚动条 + 边框。

二、浏览器兼容性

```js

 var w= document.documentElement.offsetWidth || document.body.offsetWidth;
 
 var h= document.documentElement.offsetHeight|| document.body.offsetHeight;
 
```

###scroll
 
  scroll这个单词本身是--卷页，卷曲的意思
  
 * scrollHeight 内、scrollWidth容的宽高
 
  * IE67可以比盒子小、IE8+火狐谷歌不能比盒子小
  
  
 *  scrollLeft/scrollTop
  
  * 被卷去的左侧和头部（浏览器无法显示的左/头部）

  * 一般调用document.body.scrollTop:




#####网页卷去的距离与偏移量

    我们先来看看下面的图：

   ![](http://img.mukewang.com/5347b2b10001e1a307520686.jpg)

```js
    scrollLeft:设置或获取位于给定对象左边界与窗口中目前可见内容的最左端之间的距离 ，即左边灰色的内容。

    scrollTop:设置或获取位于对象最顶端与窗口中可见内容的最顶端之间的距离 ，即上边灰色的内容。

    offsetLeft:获取指定对象相对于版面或由 offsetParent 属性指定的父坐标的计算左侧位置 。

    offsetTop:获取指定对象相对于版面或由 offsetParent 属性指定的父坐标的计算顶端位置 。

    注意:

    1. 区分大小写

    2. offsetParent：布局中设置postion属性(Relative、Absolute、fixed)的父容器，从最近的父节点开始，一层层向上找，直到HTML的body。

```

###scrollTop


####scrollTop的兼容写法

```js
        //没有dtd约束的(火狐浏览器不显示,谷歌只认识他)（IE9+认识他)
        
         document.title = document.body.scrollTop;
         
        //有dtd约束的(兼容火狐浏览器,已经声明DTD（IE678只认识他）(IE9+任何时候))
         document.title = document.documentElement.scrollTop;

        //兼容写法(三种)
        
         document.title=document.body.scrollTop||document.documentElement.scrollTop;

         document.title = document.body.scrollTop + document.documentElement.scrollTop;

         document.title=window.pageYOffset;（火狐/谷歌/ie9+以上支持的(不管DTD)）

        //主流写法
        document.title=window.pageYOffset||document.body.scrollTop||document.documentElement.scrollTop;
     
```

###offset
 
 * 得到对象的宽度和高度
 
 * offsetWidth=width+padding+border

 * offsetLeft 返回距离上级盒子(带有定位)左边的位置,如果父级都没有定位则以body为准,
  
  * offsetLeft从父亲的padding开始算 父亲的boder不算
  
  
 * offsetParent
 
  * 返回改对象的父级 （带有定位）
  
    * 如果当前元素的父级元素没有进行CSS定位(position为absolute或relative，fixed)offsetParent为body。

    * 如果当前元素的父级元素中有CSS定位		(position为absolute或relative，fixed),	offsetParent取最近的那个父级元素。


#### offsetTop style.top 的区别

* 最大区别在于  offsetLeft  可以返回没有定位盒子的距离左侧的位置。而style.top不可以

* offsetTop 返回的是数字，而 style.top 返回的是字符串，除了数字外还带有单位：px。

* offsetTop 只读，而 style.top 可读写。

* 如果没有给 HTML 元素指定过 top 样式，则 style.top 返回的是空字符串。


####判断是否声明DTD

* document.compatMode === "BackCompat"
* BackCompat  未声明
* CSS1Compat  已经声明
 * IE678默认识别CSS1Compat ，无论有没有dtd

####滚动到指定坐标

 * window.scrollTo()可把内容滚动到指定的坐标。


 * scrollTo(xpos,ypos)
 
  * xpos 必需。要在窗口文档显示区左上角显示的文档的 x 坐标。
 
  * ypos 必需。要在窗口文档显示区左上角显示的文档的 y 坐标

###事件对象（event）

 * 普通浏览器支持 event（传参）

 * ie 678 支持 window.event（无参）

####Event属性
 
 * timeStamp 返回事件生成的日期和时间。
 
 * bubbles   返回布尔值，指示事件是否是起泡事件类型。

 * button   返回当事件被触发时，哪个鼠标按钮被点击。
 
 * pageX   光标相对于该网页的水平位置（ie无）

 * pageY  光标相对于该网页的垂直位置（ie无）

 * screenX 光标相对于该屏幕的水平位置

 * screenY  光标相对于该屏幕的垂直位置

 * target 该事件被传送到的对象

 * type  事件的类型

 * clientX 光标相对于该网页的水平位置 （当前可见区域）

 * clientY 光标相对于该网页的垂直位置
 
 
###Cient

 * clientX/clientY  

  * 当前窗口的左上角为基准点
  

 * pageX/pageY低版本浏览器（IE67）不支持,以当前文档的左上角为基准点
 
 * screenX/screenY当前屏幕的左上角为基准点
 
#####Client 
 
* clientWidth	获取网页可视区域宽度（两种用法）

  clientHeight 	获取网页可视区域高度（两种用法）
  
 * 调用者不同，意义不同：
   
   * 盒子调用：指盒子本身。
		
   * body/html调用：可视区域大小。

*  clientX       鼠标距离可视区域左侧距离（event调用）
   clientY       鼠标距离可视区域上侧距离（event调用）

*  clientTop		盒子的上border
   clientLeft		盒子的左border
 
 


####清除选中的内容

```js

window.getSelection ? window.getSelection().removeAllRanges() : document.selection.empty();

//IE9、Firefox、Safari、Chrome和Opera支持：window.getSelection() 
//IE9以下支持：document.selection 

```


###offset/scroll/client区别

* 区别一

```css
 
  （offset/scroll/client宽高）

clientWidth  = width  + padding
clientHeight = height + padding
offsetWidth  = width  + padding + border
offsetHeight = height + padding + border
scrollWidth   = 内容宽度（不包含border）
scrollHeight  = 内容高度（不包含border）


```


* 区别二

```css

（offset/scroll/client上下）

offsetTop/offsetLeft ：
		调用者：任意元素。(盒子为主)
		作用：距离父系盒子中带有定位的距离。
		
scrollTop/scrollLeft:(盒子也可以调用，必须有滚动条)
		调用者：document.body.scrollTop/.....(window)
		作用：浏览器无法显示的部分（被卷去的部分）。
		
clientY/clientX:（clientTop/clientLeft 值的是border）
		调用者：event.clientX(event)
		作用：鼠标距离浏览器可视区域的距离（左、上）。

```



###模拟垂直滚动条口诀


 * 动态设置滚动条的高度 scrollBarHeight = （ 容器的高度 / 内容的高度*容器的高度 ）
   
* 滚动条滚动一次    内容移动的距离
  
  (内容的高度 - 容器的高度)   / (容器的高度 - 滚动条的高度)* 滚动条移动的距离

