###DOM事件类


####DOM事件的级别(DOM标准定义的级别)

    * DOM0 element.onclik=function(){}
    * DOM2 element.addEventListener('click',function(){},false)
    * DOM3 element.addEventListener('keyup',function(){},false)
    
######* DOM2和DOM3的第三个参数指定的是冒泡还是捕获(默认是false冒泡,true捕获)
######* DOM1标准制订的时候没有设计跟事件相关的东西,所以事件级别没有DOM1,但不代表没有DOM1
######* DOM2在IE中是attachEvent
######* DOM3在DOM2的基础上新增了鼠标事件、键盘事件等等

####DOM事件事件模型
    
    * 捕获
    
        从上到下
        
    * 冒泡
    
        从当前元素目标元素往上
        
####DOM事件流

   一个完整的事件流分了3个阶段
    
    * 捕获
    * 目标阶段
    * 冒泡
    
事件流：
     浏览器在对当前页面与用户进行交互的时候,比如说点击鼠标左键,这个左键是这么传到这个页面上的？是怎么响应的？
    
    
 ###### ** 事件通过捕获到达目标元素,从目标元素再上传到window对象

####描述DOM事件捕获的具体流程

```js

    window
        document
            html
                body
                    ...
                        父级元素
                            子级元素
                                目标元素
    
```

```js

<!DOCTYPE html>
<html>
<head lang="en">
    <meta charset="UTF-8">
    <title></title>
</head>
<body>
    <div id="ev">
        <style>
            #ev{
                width:300px;
                height:100px;
                background:red;
                color: #fff;
                text-align: center;
                line-height: 100px;

            }
        </style>
        目标元素
    </div>
    <script>
        var ev=document.getElementById("ev");
        window.addEventListener('click',function(){
            console.log('window capture')
        },true);
        document.addEventListener('click',function(){
            console.log('docuemnt capture')
        },true)
        document.documentElement.addEventListener('click',function(){
            console.log('html capture')
        },true)
        document.body.addEventListener('click',function(){
            console.log('body capture')
        },true)
        ev.addEventListener('click',function(){
            console.log('ev capture')
        },true)
    </script>
</body>
</html>

结果：
window capture
docuemnt capture
html capture
body capture
ev capture



```

####Event对象的常见应用


* event.preventDefalut()                阻止默认行为
* event.stoppropagation()               阻止冒泡行为
* event.stoplmmediatePropagation()      事件响应优先级(按钮绑定了两个click事件A、B，希望点击A之后加上这句话，就可以阻止B的执行。)
* event.currentTarget()                 当前绑定的事件
* event.target                          当前被点击的元素
    
###### * event.target在IE中是event.srcElement

####自定义事件

* Event

```js
    var eve=new Event('custome');
    ev.addEventListener('custome',function(){
        console.log('custome');
    });
    
    ev.dispatchEvent(eve);//触发

```
*  CustomeEvent

区别：用Event和CustomeEvent都是用来做自定义事件的,唯一的区别是
  CustomeEvent除了可以指定事件名,后面还可以跟一个Object来做指令参数。