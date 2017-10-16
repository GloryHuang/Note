#####阻止事件冒泡和默认事件

```js
 function stopBubble(e){

 if(e && e.stopPropagation){

   e.stopPropagation()

  }else{

   window.event.cancelBubble=true

  }
  return false
```




#####法二



    function preventDefa(e){ 
      if(window.event){ 
        //IE中阻止函数器默认动作的方式  
        window.event.returnValue = false;  
     }else{ 
        //阻止默认浏览器动作(W3C)  
        e.preventDefault(); 
      }  
    } 
