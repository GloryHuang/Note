### 网页尺寸scrollHeight

```js

scrollHeight和scrollWidth，获取网页内容高度和宽度。

一、针对IE、Opera:

scrollHeight 是网页内容实际高度，可以小于 clientHeight。

二、针对NS、FF:

scrollHeight 是网页内容高度，不过最小值是 clientHeight。也就是说网页内容实际高度小于 clientHeight 时，scrollHeight 返回 clientHeight 。

三、浏览器兼容性

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

     var w= document.documentElement.offsetWidth || document.body.offsetWidth;
     var h= document.documentElement.offsetHeight|| document.body.offsetHeight;



#####网页卷去的距离与偏移量

    我们先来看看下面的图：

   ![](http://img.mukewang.com/5347b2b10001e1a307520686.jpg)

    scrollLeft:设置或获取位于给定对象左边界与窗口中目前可见内容的最左端之间的距离 ，即左边灰色的内容。

    scrollTop:设置或获取位于对象最顶端与窗口中可见内容的最顶端之间的距离 ，即上边灰色的内容。

    offsetLeft:获取指定对象相对于版面或由 offsetParent 属性指定的父坐标的计算左侧位置 。

    offsetTop:获取指定对象相对于版面或由 offsetParent 属性指定的父坐标的计算顶端位置 。

    注意:

    1. 区分大小写

    2. offsetParent：布局中设置postion属性(Relative、Absolute、fixed)的父容器，从最近的父节点开始，一层层向上找，直到HTML的body。



####网页尺寸scrollTop




#####scrollTop的兼容写法

        //没有dtd约束的(火狐浏览器不显示)
        // document.title = document.body.scrollTop;
        //有dtd约束的(兼容火狐浏览器)
        // document.title = document.documentElement.scrollTop;

        //兼容写法(三种)
        // document.title=document.body.scrollTop||document.documentElement.scrollTop;

        // document.title = document.body.scrollTop + document.documentElement.scrollTop;

        // document.title=window.pageYOffset;

        //主流写法
        document.title=window.pageYOffset||document.body.scrollTop||document.documentElement.scrollTop;
        
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

