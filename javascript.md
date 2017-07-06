## 事件委托

***
```js

  //获取事件的父元素
  var main = document.getElementsByClassName("main")[0];
  //给相应的父元素添加事件
  main.onclick = function() {

  var event = event || window.event;

  var aaa = event.target ? event.target : event.srcElement;

  if (aaa.id == "btn-save") {

  console.log('123');

  }

  }

```
****