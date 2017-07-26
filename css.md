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

####5.before，after伪元素法

        这个也是让子级元素垂直居中了。如果还想要水平居中的话可以配合其他几种方法配合使用来实现，比如给子
    级元素设置：margin:0 auto;这样就水平和垂直都居中了。

####Flex布局法

        这个方法要充分考虑浏览器的兼容性。要垂直居中的元素也是无需设置宽和高的值，可以用在自适应页面中来实现
    水平垂直居中。

