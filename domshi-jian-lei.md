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

####描述DOM事件捕获的具体流程


####Event对象的常见应用



####自定义事件