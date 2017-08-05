#### 网页尺寸scrollHeight

```
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