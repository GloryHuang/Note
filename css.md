## div元素水平居中的方法
```
1.定位法：position:absolute

      如果子级div有定义宽和高的话就可以用这个方法。注意：margin-top,和margin-left的值均为高和宽值一半。

```
![](/assets/QQ截图20170726162119.png)

```
    2. margin:auto法
        这个也可以是定位法。用这个方法要求子级div必须设置宽的值，不然没有效果哦~margin:auto是水平垂直都
    居中，如果仅仅设置水平居中，可设置为margin:auto 0;同理，如果仅仅设置垂直居中，可设置为margin:0 auto.


