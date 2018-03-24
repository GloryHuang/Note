###Vue组件

* 组件（Component）是 Vue.js 最强大的功能之一。组件可以扩展 HTML 元素，封装可重用的代码

###组件的定义和注册

- 写法1：使用Vue.extend方法定义组件，使用 Vue.component方法注册组件

   ![](/assets/d3-7.png)

- 写法2:使用 Vue.component方法定义注册组件一步到位

   ![](/assets/d3-8.png)   

- 写法3：将组件内容定义到template模板中
    
   ![](/assets/d3-9.png)
    
- 写法4：将组件内容定义到类型为 x-template的script模板中
    
   ![](/assets/d3-10.png)   
    

###组件中实现指令以及事件绑定
    
   ![](/assets/d3-11.png)
    

###组件中注册子组件
    
   ![](/assets/d3-12.png)
    
###组件中利用component中的is来实现组件切换
    
   ![](/assets/d3-13.png)
   
###实现父组件传值给子组件
    
   ![](/assets/d3-14.png)

###实现子组件传值给父组件
    
   ![](/assets/d3-15.png)
   
###通过v-el获取到dom对象
    
   ![](/assets/d3-16.png)
   
###通过v-ref获取到整个组件的对象
    
   ![](/assets/d3-17.png)
