###DOM事件类


####DOM事件的级别(DOM标准定义的级别)

    * DOM0 element.onclik=function(){}
    * DOM2 element.addEventListener('click',function(){},false)
    * DOM3 element.addEventListener('keyup',function(){},false)
    
######* DOM2和DOM3的第三个参数指定的是冒泡还是捕获
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

    window
        document
            html
                body
                    ...
                        父级元素
                            子级元素
                                目标元素
    

####Event对象的常见应用


* event.preventDefalut()                阻止默认行为
* event.stoppropagation()               阻止冒泡行为
* event.stoplmmediatePropagation()      事件响应优先级
* event.currentTarget()                 
* event.target                          当前被点击的元素
    
###### * event.target在IE中是event.srcElement

####自定义事件