## div元素水平居中的方法

####1.定位法：position:absolute

      如果子级div有定义宽和高的话就可以用这个方法。注意：margin-top,和margin-left的值均为高和宽值一半。


####2. margin:auto
        这个也可以是定位法。用这个方法要求子级div必须设置宽的值，不然没有效果哦~margin:auto是水平垂直都
    居中，如果仅仅设置水平居中，可设置为margin:auto 0;同理，如果仅仅设置垂直居中，可设置为margin:0 auto.

####3.display:table-cell

        这个方法主要针对多行文字内容的垂直居中对齐。注意：text-align:center设置了文字的水平居中对齐
    vertical-align:middle设置的是垂直居中对齐。

####4.transform:translate(x,y)
        这个是css3中的新属性，如果子级元素没有设置宽和高值的话可以用这个方法来实现。这在我们做自适应页面
    的时候可以用到。
