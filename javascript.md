## 事件委托
```js
有关 event 和 window.event在IE/Opera中，是window.event,

而在Firefox中，是event而事件的对象，

在IE中是window.event.srcElement，

在Firefox中是event.target，而在Opera中则两者都支持。


```



***
```js
  -------//js版本    

  //获取事件的父元素
  var main = document.getElementsByClassName("main")[0];

  //给相应的父元素添加事件
  main.onclick = function() {
  
  var event = event || window.event;

  //srcElement/target：事件源，就是发生事件的元素；
  // FF下是target，IE下是srcElement
  var aaa = event.target ? event.target : event.srcElement;

  //判断元素的id名字是否一致
  if (aaa.id == "btn-save") {
          console.log('123');
      }

  }

```
-------------

```js
    

 -------//jq版本
    
 $(document).on('click', '.modal-footer', function() {

     event = event || window.event;

     var el = event.target ? event.target : event.srcElement;

     if (el.id == "btn-save") {

     console.log('321');

     }
 });



    

```
****