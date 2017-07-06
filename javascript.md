## 事件委托

***
```js
  -------//js版本    

  //获取事件的父元素
  var main = document.getElementsByClassName("main")[0];

  //给相应的父元素添加事件
  main.onclick = function() {

  var event = event || window.event;

  var aaa = event.target ? event.target : event.srcElement;

  //判断元素的id名字是否一致
  if (aaa.id == "btn-save") {
          console.log('123');
      }

  }

```


```jq

    

```
****