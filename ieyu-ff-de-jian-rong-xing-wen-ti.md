###IE与FF脚本兼容性问题：

---

\(1\) window.event：

表示当前的事件对象，IE有这个对象，FF没有，FF通过给事件处理函数传递事件对象

例如：e=window.event \|\|e;

\(2\) 获取事件源

IE用srcElement获取事件源，而FF用target获取事件源；

例如：var target = e.target \|\| e.srcElement;

\(3\) 添加，去除事件

IE：

```js
element.attachEvent(“onclick”, function(){})
```

```js
element.detachEvent(“onclick”, function(){})
```

FF：

```js
element.addEventListener(“click”,function,true)
```

```js
element.removeEventListener(“click”, function, true)
```

\(4\) 获取标签的自定义属性

```
IE：div1.value或div1\[“value”\]  
FF：可用div1.getAttribute\(“value”\)
```

\(5\) input.type的属性

```
IE：input.type只读  
FF：input.type可读写  

例如：修改input的type属性有些限制。当input元素还未插入文档流之前，是可以修改它的值的，在ie和ff下都没问题。但如果input已经存在于页面，其type属性在ie下就成了只读属性了，不可以修改。在ff下仍是可读写属性。
```

\(6\) innerText textContent outerHTML

```
IE：支持innerText, outerHTML  
FF：支持textContent
```

\(7\) 是否可用id代替HTML元素

```js
IE：可以用id来代替HTML元素  
FF：不可以IE与FF脚本兼容性问题： 

(1) window.event：  
表示当前的事件对象，IE有这个对象，FF没有，FF通过给事件处理函数传递事件对象  
例如：e=window.event \|\|e;

(2) 获取事件源  
IE用srcElement获取事件源，而FF用target获取事件源；  
例如：var target = e.target \|\| e.srcElement;

(3) 添加，去除事件 

IE：element.attachEvent(“onclick”, function) element.detachEvent(“onclick”, function)  
FF：element.addEventListener(“click”,function,true\) element.removeEventListener(“click”, function, true)

(4) 获取标签的自定义属性  

IE：div1.value或div1\[“value”\]  
FF：可用div1.getAttribute\(“value”\)

(5) input.type的属性 

IE：input.type只读  
FF：input.type可读写  

例如：修改input的type属性有些限制。当input元素还未插入文档流之前，是可以修改它的值的，在ie和ff下都没问题。但如果input已经存在于页面，其type属性在ie下就成了只读属性了，不可以修改。在ff下仍是可读写属性。

(6) innerText textContent outerHTML 

IE：支持innerText, outerHTML  
FF：支持textContent

(7) 是否可用id代替HTML元素  

IE：可以用id来代替HTML元素  
FF：不可以
```

