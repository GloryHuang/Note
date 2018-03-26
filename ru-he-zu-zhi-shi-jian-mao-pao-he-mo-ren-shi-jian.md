###阻止事件冒泡和默认事件

```js
 function stopBubble(e){

     if(e && e.stopPropagation){
          //w3c的方法是：（火狐、谷歌、IE11）
           e.stopPropagation()
      }else{
          //IE10以下
           window.event.cancelBubble=true
      }
      return false
}
```




####法二

默认事件：即浏览器本身具备的功能

```js
    function preventDefa(e){ 
      if(window.event){ 
        //IE中阻止函数器默认动作的方式  
        window.event.returnValue = false;  
     }else{ 
        //阻止默认浏览器动作(W3C)  
        e.preventDefault(); 
      }  
    } 

```
这种是兼容性写法，但是如果你只需要支持高版本浏览器的话，那么如上文一样，一句话即可。

```js
    btn.onclick = function (){ 
      return false; 
    }
```