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
