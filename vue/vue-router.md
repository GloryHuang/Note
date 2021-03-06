###路由vue-router

 * 
    在一个系统中会由很多页面组成，在Vue开发中这些页面通常使用的是Vue中的组件来实现的，那么当在一个页面要跳转到另外一个页面的时候是通过改变url路径来实现的，那么这个时候Vue需要知道当前url对应的是哪个组件页面，这个控制z者就是vue-router
  
 * 注意的是：vue-router 在vue2.0版本中做了很大的改动，所以要注意Vue的版本来选择预期对应的vue-router版本

####vue-router资源和介绍

- 配合Vue1.0使用的版本的帮助文档地址：https://github.com/vuejs/vue-router/tree/1.0/docs/zh-cn
- 配合Vue1.0使用的vue-router下载地址：https://cdnjs.cloudflare.com/ajax/libs/vue-router/0.7.10/vue-router.min.js
- 配合Vue2.0使用的版本的帮助文档地址：http://router.vuejs.org/zh-cn/installation.html
- 配合Vue2.0使用的vue-router下载地址：https://unpkg.com/vue-router/dist/vue-router.js

###vue-router在 vue1.0中的使用


   
   ![](/assets/d4-1.png)
    
###vue-router在 vue2.0中的使用

   ![](/assets/d4-2.png)
    
###vue1.0的路由参数定义实现url的传值

   ![](/assets/d4-3.png)
  
###vue2.0的路由参数定义实现url的传值

  ![](/assets/d4-4.png)
  
###vue1中嵌套路由的写法

  ![](/assets/d4-5.png)

###vue2中嵌套路由的写法

  ![](/assets/d4-6.png)
  
  
###watch与计算属性computed

*  watch与computed均可以监控程序员想要监控的对象，当这些对象发生了改变以后，可以触发回调函数做一些逻辑处理

####watch用法举例

- 监听data中定义的属性

  ![](/assets/d4-7.png)

- 监听路由对象$route

  ![](/assets/d4-8.png)
  

####computed用法举例

- 监听data中定义的属性

  ![](/assets/d4-9.png)
  
###Vue1.0与Vue2.0区别总结

  ![](/assets/d4-10.png)


