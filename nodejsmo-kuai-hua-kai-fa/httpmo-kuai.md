####Http模块

 Nodejs中http模块不解析请求的具体内容，只分离出请求头和请求体

    
* 什么是回调函数？
    
回调是异步编程时的基础，将后续逻辑封装成起始函数的参数，逐层嵌套

    
* 什么是同步/异步？
    
    同步：发送方发送数据后，等待接收方发回响应以后才发下一个数据包的通讯方式
    异步：发送方发出数据后，不等接收方发回响应，接着发送下个数据包的通讯方式


* 什么是I/O?

    文件系统里面 磁盘的写入（in）磁盘的读取（out）


* 什么是单线程/多线程？
        
 一次只能执行一个程序叫做单线程
    一次能执行多个程序叫做多线程


* 什么是阻塞/非阻塞？

    阻塞：前一个程序未执行完就得一直等待
    非阻塞：前一个程序未执行完时可以挂起，继续执行其他程序，等到使用时再执行

* 什么是事件？
    
    一个触发动作（例如点击按钮）

* 什么是事件驱动？

    一个触发动作引起的操作（例如点击按钮后弹出一个对话框）

* 什么是基于事件驱动的回调？
    
    为了某个事件注册了回调函数，但是这个回调函数不是马上执行，只有当事件发生的时候，才会调用回掉函数，这种函数执行的方式叫做事件驱动~这种注册回掉就是基于事件驱动的回调，如果这些回调和异步I/O（数据写入、
读取）操作相关，可以看作是基于回调的异步I/O。只不过这种回调在nodejs中是由事件来驱动的

* 什么是事件循环？

    事件循环Eventloop，倘若有大量的异步操作，如一些I/O的耗时操作，甚至是一些定时器控制的延时操作，它们完成的时候都要调用相应的回调函数，而从完成一些密集的任务，而又不会阻塞整个程序执行的流程，此时需要一种机制来管理，这种机制叫做事件循环
        
 * 总而言之，管理大量异步操作的机制叫做事件循环
 

* EventLoop：

    回调函数队列，异步执行的函数会被压入这个队列；队列被循环查询



####Http性能测试

1.如果没有安装Apache的话，首先要安装Apache

2.window系统到apache安装目录的bin文件，然后命令行执行ab -n1000 -c10 http://localhost:2015/
    
3.找到 apache的bin目录 ab -n1000 -c10 http://www.xxxxx.com/ 输入
    
 * -n1000 总请求数1000 默认值1
 * -c10 并发数10  默认值1
 * -t 测试的时间
 * -p post数据文件1.如果没有安装Apache的话，首先要安装Apache

```cmd
       在git bash中运行 要改为
           ./ab -n1000 -c10 http://localhost:2015/
```
