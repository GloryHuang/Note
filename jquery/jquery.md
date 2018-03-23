###jQuery


###事件操作


* 事件绑定

 * click()
 * bind()
 * delegate()
 * on()
 
 

####click()

 ```js
  
  click()事件不会重叠
  
  $().click(function(){});
  
  解绑：$().unbiind("click");
  
 ```
 
####bind()

```js

   bind()绑定（可以绑定多个事件）
   
   $().bind("click mouseenter",function(){});
   
   解绑：$().unbind("click");

```

####delegate()

```js

   delegate()绑定（元素，事件或者多个事件，函数）
   $().delegate("div","click mouseenter",function(){

    });

  解绑：$(document).undelegate(".box","mouseenter", fn);
       $(document).undelegate(".box","mouseenter", fn2);





```
