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

默认事件：即浏览器本身具备的功能

    function preventDefa(e){ 
      if(window.event){ 
        //IE中阻止函数器默认动作的方式  
        window.event.returnValue = false;  
     }else{ 
        //阻止默认浏览器动作(W3C)  
        e.preventDefault(); 
      }  
    } 


这种是兼容性写法，但是如果你只需要支持高版本浏览器的话，那么如上文一样，一句话即可。


    btn.onclick = function (){ 
      return false; 
    }