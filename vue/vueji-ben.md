


###Vue

####MVVM模式

*  MVVM拆分解释为：

  - Model:负责数据存储
  - View:负责页面展示
  - View Model:负责业务逻辑处理（比如Ajax请求等），对数据进行加工后交给视图展示
  
    
- MVVM要解决的问题是将业务逻辑代码与视图代码进行完全分离，使各自的职责更加清晰，后期代码维护更加简单

- 用图解的形式分析Ajax请求回来数据后直接操作Dom来达到视图的更新的缺点，以及使用MVVM模式是如何来解决这个缺点的


![](/assets/d1-11.png)

####Vue的使用

![](/assets/d1-12.png)


###Vue常用指令

####差值表达式


```js


    数据绑定最常见的形式就是使用 “Mustache” 语法（双大括号）的文本插值        
    例如：<span>Message: {{ msg }}</span>
    Mustache 标签将会被替代为对应数据对象上 msg 属性（msg定义在data对象中）的值。
    无论何时，绑定的数据对象上 msg 属性发生了改变，插值处的内容都会更新。

    {{}}对JavaScript 表达式支持，例如：
    {{ number + 1 }}
    {{ ok ? 'YES' : 'NO' }}
    {{ message.split('').reverse().join('') }}

    但是有个限制就是，每个绑定都只能包含单个表达式，如下表达式无效：
    <!-- 这是语句，不是表达式 -->
    {{ var a = 1 }}
    <!-- 流控制也不会生效，请使用三元表达式 -->
    {{ if (ok) { return message } }}


```

####v-text

```js
    
     v-text可以将一个变量的值渲染到指定的元素中,例如：
        <div v-text="msg"></div>
        new Vue({
            data:{
                msg:'hello ivan'                                            
               }
        });
        
        输出结果：
        <div>hello ivan</div>        

```


####v-html

```js

    双大括号和v-text会将数据解释为纯文本，而非 HTML 。
      为了输出真正的 HTML ，你需要使用 v-html 指令：
      例如：<div v-html="rawHtml"></div>
          new Vue({
              data:{
                  rawHtml:'<h1>hello ivan</h1>'
                }
          })
          
        被插入的内容都会被当做 HTML,但是对于没有HTML标签的数据绑定时作用同v-text和{{}}
        
    注意：使用v-html渲染数据可能会非常危险，因为它很容易导致 XSS（跨站脚本） 攻击，使用的时候请谨慎，能够使用{{}}或者v-text实现的不要使用v-html



```

####v-cloak

```js
    
     v-cloak指令保持在元素上直到关联实例结束编译后自动移除，v-cloak和 CSS 规则如 [v-cloak] { display: none } 一起用时，这个指令可以隐藏未编译的 Mustache 标签直到实例准备完毕。
    通常用来防止{{}}表达式闪烁问题
    例如：
    <style>
     [v-cloak] { display: none } 
    </style>
    
     <!-- 在span上加上 v-cloak和css样式控制以后，浏览器在加载的时候会先把span隐藏起来，知道 Vue实例化完毕以后，才会将v-cloak从span上移除，那么css就会失去作用而将span中的内容呈现给用户 -->
    <span v-cloak>{{msg}}</span>    
    
     new Vue({
              data:{
                  msg:'hello ivan'
                }
          })

```

####v-model以及双向数据绑定


```js
    
    1、在表单控件或者组件上创建双向绑定
    
    2、v-model仅能在如下元素中使用：
       input
       select
       textarea
       components（Vue中的组件）
       
    3、举例：
       <input type="text" v-model="uname" />
       
     new Vue({
              data:{
                  uname:'' //这个属性值和input元素的值相互一一对应，二者任何一个的改变都会联动的改变对方
                }
          })
          
    4、修饰符：
        .lazy - 取代 input 监听 change 事件
        .number - 自动将输入的字符串转为数字
        .trim - 自动将输入的内容首尾空格去掉




```

####v-bind


```js

    1、作用：可以给html元素或者组件动态地绑定一个或多个特性，例如动态绑定style和class
    
    2、举例：
        <img v-bind:src="imageSrc">   
        <div v-bind:class="{ red: isRed }"></div>
        <div v-bind:class="[classA, classB]"></div>
        <div v-bind:class="[classA, { classB: isB, classC: isC }]">
        <div v-bind:style="{ fontSize: size + 'px' }"></div>
        <div v-bind:style="[styleObjectA, styleObjectB]"></div>
           
    3、缩写形式
        <img :src="imageSrc">
        <div :class="{ red: isRed }"></div>
        <div :class="[classA, classB]"></div>
        <div :class="[classA, { classB: isB, classC: isC }]">
        <div :style="{ fontSize: size + 'px' }"></div>
        <div :style="[styleObjectA, styleObjectB]"></div>



```


####v-for

```js

      1、作用：通常是根据数组中的元素遍历指定模板内容生成内容
      
      2、用法举例：
          <div v-for="item in items">
              {{ item.text }}
            </div>
            new Vuew({
                data:{
                    items:[{text:'1'},{text:'2'}]                
                    }
            });
      3、可以为数组索引指定别名（或者用于对象的键）：
          Vue1.0写法:
            <div v-for="(index,item) in items"></div>
            <div v-for="(key,val) in user"></div>
              new Vue({
                data:{
                    items:[{text:'1'},{text:'2'}],
                    user:{uname:'ivan',age:32}
                    }
            });
            
          Vue2.0写法:
            <div v-for="(item, index) in items"></div>
            <div v-for="(val, key) in user"></div>
            <div v-for="(val, key, index) in user"></div>            
             new Vue({
                data:{
                    items:[{text:'1'},{text:'2'}],
                    user:{uname:'ivan',age:32}
                    }
            });
            
       4、v-for 默认行为试着不改变整体(为了性能考虑的设计)，而是替换元素。迫使其重新排序的元素,在Vue2.0版本中需要提供一个 key 的特殊属性，在Vue1.0版本中需要提供一个 track-by="$index":
       
       Vue2.0写法：
       <div v-for="item in items" :key="item.id">
          {{ item.text }}
        </div>
        
       Vue1.0写法：
       <div v-for="item in items" track-by="$index">
          {{ item.text }}
        </div>
        
      5、vue1.0与vue2.0对于v-for使用区别总结：
          1、vue1.0中有$index ，而vue2.0中将$index移除
          2、vue1.0中 (index,item) in list  而 vue2.0 变成了 (item,index) in list的写法
          3、vue1.0中使用 track-by来标记dom对象的唯一性，vue2.0中改成了 :key
          
```

####v-if

```js

    1、作用：根据表达式的值的真假条件来决定是否渲染元素，如果条件为false不渲染（达到隐藏元素的目的），为true则渲染。在切换时元素及它的数据绑定被销毁并重建
    
    2、示例：
        <!-- Handlebars 模板 -->
        {{#if isShow}}
          <h1>Yes</h1>
        {{/if}}

        通常我们使用写法居多：
        <h1 v-if="isShow">Yes</h1>
        
        也可以用 v-else 添加一个 “else” 块：
        <h1 v-if="isShow">Yes</h1>
        <h1 v-else>No</h1>
        
        注意：v-else 元素必须紧跟在 v-if 元素否则它不能被识别。
        
         new Vue({
                data:{
                   isShow:true
                    }
            });

```

####v-show

```js

    1、根据表达式的真假值，切换元素的 display CSS 属性，如果为false，则在元素上添加 display:none来隐藏元素，否则移除display:none实现显示元素
    

    2、示例：
         <h1 v-show="isShow">Yes</h1>
        
         new Vue({
                data:{
                   isShow:true
                    }
            });
            
    3、v-if和v-show的总结：
         v-if和v-show 都能够实现对一个元素的隐藏和显示操作,但是v-if是将这个元素添加或者移除到dom中，而v-show
         是在这个元素上添加 style="display:none"和移除它来控制元素的显示和隐藏的

```

####v-on

```js

       1、作用：绑定事件监听，表达式可以是一个方法的名字或一个内联语句，如果没有修饰符也可以省略，用在普通的html元素上时，只能监听 原生 DOM 事件。用在自定义元素组件上时，也可以监听子组件触发的自定义事件。
      
      2、常用事件：
          v-on:click
          v-on:keydown
          v-on:keyup
          v-on:mousedown
          v-on:mouseover
          v-on:submit
          ....
          
      3、v-on提供了很多事件修饰符来辅助实现一些功能，例如阻止冒泡等
        事件修饰符有如下：
        .stop - 调用 event.stopPropagation()。
        .prevent - 调用 event.preventDefault()。
        .capture - 添加事件侦听器时使用 capture 模式。
        .self - 只当事件是从侦听器绑定的元素本身触发时才触发回调。
        .{keyCode | keyAlias} - 只当事件是从侦听器绑定的元素本身触发时才触发回调。
        .native - 监听组件根元素的原生事件。
        
      4、示例：
          <!-- 方法处理器 -->
        <button v-on:click="doThis"></button>
        <!-- 内联语句 -->
        <button v-on:click="doThat('hello', $event)"></button>
        <!-- 缩写 -->
        <button @click="doThis"></button>
        <!-- 停止冒泡 -->
        <button @click.stop="doThis"></button>
        <!-- 阻止默认行为 -->
        <button @click.prevent="doThis"></button>
        <!-- 阻止默认行为，没有表达式 -->
        <form @submit.prevent></form>
        <!--  串联修饰符 -->
        <button @click.stop.prevent="doThis"></button>
   
        
       5、v-on的缩写形式：可以使用@替代 v-on:
        <button @click="doThis"></button>

```


###v-on按键修饰符


* 作用说明

```js

    文档地址：http://cn.vuejs.org/v2/guide/events.html#按键修饰符
    
    在监听键盘事件时，我们经常需要监测常见的键值。 Vue 允许为 v-on 在监听键盘事件时添加按键修饰符：
    .enter
    .tab
    .delete (捕获 “删除” 和 “退格” 键)
    .esc
    .space
    .up
    .down
    .left
    .right
    1.0.8+ 支持单字母按键别名。

```

* 可以自定义按键别名

```js

    在Vue2.0 中默认的按键修饰符是存储在 Vue.config.keyCodes中
    // 例如在Vue2.0版本中扩展一个f1的按键修饰符写法：
    Vue.config.keyCodes.f1 = 112

    
    在1.0.17+ 中默认的按键修饰符是存储在Vue.directive('on').keyCodes中                                         
    
    // 例如在Vue1.0中扩展一个f1的按键修饰符写法：
    Vue.directive('on').keyCodes.f1 = 112
      
```   
###自定义指令

 * 当Vue提供的系统指令不能满足需求时，就需要自己定义指令来进行扩展，例如，定义一个v-focus指令来实现文本框的自动获取焦点功能
 
####自定义属性指令

* 写法格式

```js

    定义指令：
    Vue.directive('指令ID，不需要增加v-前缀',function(){
		//实现指令的业务
		this.el //代表使用这个指令的元素对象
	});
	
    使用指令(当做一个元素的属性使用)：
    <input type="text" v-指令ID />

```

* （属性指令应用举例）利用自定义属性指令实现自动获取焦点功能

```js

     定义指令：
    //定义一个 v-focus的属性自定义指令
	Vue.directive('focus',function(){
		this.el.focus(); //实现文本框的自动获取焦点
	});
	
    使用指令：
    <input type="text" v-focus />

```

####自定义元素指令

* 写法格式

```js

    定义指令：
    Vue.elementDirective('指令id',{
        bind:function(){
          //实现指令的业务
		this.el //代表使用这个指令的元素对象
        }
    });
	
    使用指令：
       <指令id></指令id>

```

* （元素指令应用举例）利用自定义属性指令实现日期格式化

```js

     定义指令：
       Vue.elementDirective('datefmt',{
    	bind:function(){
    		var v=this.el.attributes[0].value;	
    		var date = new Date(this.vm[v]); 
    		var year = date.getFullYear();
    		var m = date.getMonth() + 1;
    		var d = date.getDate();
    		//输出： yyyy-mm-dd
    		var fmtStr = year+'-'+m +'-'+d;
    
    		this.el.innerText = fmtStr;			
    	}
    });
    
    new Vue({
    	el:'#app',
    	data:{
    		time:new Date()
    	}    	
    });
	
    使用指令：
        <div id="app">
            <datefmt :dt="time"></datefmt>
        </div>

```


###过滤器

* Vue提供了一系列的固定逻辑来使程序员更加容易的实现这些功能，这些过滤器称之为系统过滤器，Vue也提供了一个接口用来供程序员定义属于自己的特殊逻辑，Vue称之为自定义过滤器

####系统过滤器

- 关于系统过滤器的使用参考请参考文档：http://v1-cn.vuejs.org/api/#过滤器
- 注意：系统过滤器是Vue1.0中存在的，在Vue2.0中已经删除了

####自定义过滤器

- 文档地址：http://v1-cn.vuejs.org/guide/custom-filter.html

###自定义私有过滤器

* 定义方式

```js

    可以在 new Vue({filters：{}})中的filters中注册一个私有过滤器
    
    定义格式：
    new Vue({
	el:'#app',	
	filters:{		
        '过滤器名称':function(管道符号|左边参数的值,参数1,参数2,....) {
          return 对管道符号|左边参数的值做处理以后的值
        })    
	}
    });
    
    Vue1.0 使用写法：
    <span>{{ msg | 过滤器id '参数1' '参数2' .... }}</span>
    
    Vue2.0 使用写法：
    <span>{{ msg | 过滤器id('参数1' '参数2' ....) }}</span>

```

* (应用示例)自定义全局过滤器实现日期格式化

```js

     1、 定义全局的日期格式化过滤器：
    
        new Vue({
        	el:'#app',
        	data:{
        		time:new Date()
        	},
        	filters:{
        		//定义在 VM中的filters对象中的所有过滤器都是私有过滤器
        		datefmt:function(input,splicchar){
        			var date = new Date(input); 
                	var year = date.getFullYear();
                	var m = date.getMonth() + 1;
                	var d = date.getDate();        	
                	var fmtStr = year+splicchar+m +splicchar+d;
                	return fmtStr; //返回输出结果
        		}
        	}
        });

   2、使用
   
      <div id="app">
		{{ time | datefmt '-' }}  //Vue1.0传参写法
		
        {{ time | datefmt('-') }} //Vue2.0传参写法

	  </div>

```

####自定义全局过滤器

* 定义方式

```js


     可以用全局方法 Vue.filter() 注册一个全局自定义过滤器，它接收两个参数：过滤器 ID 和过滤器函数。过滤器函数以值为参数，返回转换后的值
    
    定义格式：
    Vue.filter('过滤器名称', function (管道符号|左边参数的值,其他参数1,其他参数2,....) {
      return 对管道符号|左边参数的值做处理以后的值
    })
    
    Vue1.0 使用：
    <span>{{ msg | 过滤器名称 '参数1' '参数2' .... }}</span>
    
    Vue2.0 使用：
    <span>{{ msg | 过滤器名称('参数1' '参数2' ....) }}</span>

```

* (应用示例)自定义全局过滤器实现日期格式化

```js

     1、 定义全局的日期格式化过滤器：
    
        Vue.filter('datefmt',function(input,splicchar){
        	var date = new Date(input); 
        	var year = date.getFullYear();
        	var m = date.getMonth() + 1;
        	var d = date.getDate();        	
        	var fmtStr = year+splicchar+m +splicchar+d;
        	return fmtStr; //返回输出结果
        });    

   2、使用
   
      <div id="app">
		{{ time | datefmt '-' }}  //Vue1.0传参写法
		
        {{ time | datefmt('-') }} //Vue2.0传参写法

	  </div>
	<script>  
        new Vue({
        	el:'#app1',
        	data:{
        		time:new Date()
        	}
        });
    </script>

```

###Vue中的AJAX请求

* Vue可以借助于vue-resource来实现AJAX请求


* http请求报文

 * 浏览器与服务器数据交互是遵循http协议的，当浏览器要访问服务器的时候，浏览器需要将相关请求数据提交给服务器（例如：浏览器信息，url地址，参数等），通常是通过请求报文来提交的*    
   
   * 请求报文的格式分为：
   
        * 请求报文行
        * 请求报文头
        * 请求报文体


* http响应报文

   * 当浏览器请求服务器的时候，服务器需要将数据返回给浏览器，这种数据是通过响应报文响应回浏览器的
    
   * 响应报文的格式分为：
   
        * 响应报文行
        * 响应报文头
        * 响应报文体




###vue-resource

* Vue与后台Api进行交互通常是利用vue-resource来实现的，本质上vue-resource是通过http来完成AJAX请求响应的

- vue-resource GitHub 地址：https://github.com/pagekit/vue-resource
- vue-resource Http请求api参考（主要看这个）：https://github.com/pagekit/vue-resource/blob/master/docs/http.md

####vue结合vue-resource写法步骤

```js

    1、通过 https://cdn.jsdelivr.net/vue.resource/1.2.1/vue-resource.min.js 下载到vue-resource文件
    
    2、在html页面中通过script标签导入vue-resource.min.js 文件后，就会自动的在Vue对象实例上初始化 $http
    
    3、使用
    // 全局Vue对象写法
        Vue.http.get('/someUrl', [options]).then(successCallback, errorCallback);
        Vue.http.post('/someUrl', [body], [options]).then(successCallback, errorCallback);

    // 在Vue对象中的写法
        this.$http.get('/someUrl', [options]).then(successCallback, errorCallback);
        this.$http.post('/someUrl', [body], [options]).then(successCallback, errorCallback);

```

- vue-resource get请求

```js

    写法格式：
     this.$http.get('请求的url', [可选参数对象，使用{}传参]).then(成功回调函数, 失败回调函数);
     
    成功回调函数参数对象主要属性说明：
    1、url ： 请求的原始url
    2、body： 响应报文体中的数据（我们通常用这个属性获取服务器返回的数据）
    3、其他属性请看文档
    
    举例：
     this.$http.get('http://vuecms.ittun.com/api/getlunbo?id=1').then(function(res){console.log(res.body)}, function(err){//err是异常数据});

```
- vue-resource post请求

```js

     写法格式：
     this.$http.post('请求的url',[可选参数请求报文体对象body,使用{}传参], [可选参数对象，使用{}传参]).then(成功回调函数, 失败回调函数);
     
    成功回调函数参数对象主要属性说明：
    1、url ： 请求的原始url
    2、body： 响应报文体中的数据（我们通常用这个属性获取服务器返回的数据）
    3、其他属性请看文档
    
    注意点：
    $http.post()方法中的第二个参数固定写成：{emulateJSON:true},否则可能造成服务器无法接收到请求报文体中的参数值
    
    举例：
     this.$http.post('http://vuecms.ittun.com/api/adddata?id=1'  //请求的url
     ,{content:'hello'}  //请求报文体中传入的参数对象，多个使用逗号分隔
     ,{emulateJSON:true}  //固定写法，保证服务器可以获取到请求报文体参数值
     ).then(function(res){console.log(res.body)}, function(err){//err是异常数据});


```
- vue-resource jsonp请求

```js

   jsonp请求主要用来解决ajax跨域请求问题，使用jsonp实现跨域首先要保证服务器api支持jsonp请求的格式
    
    
    写法格式：
     this.$http.jsonp('请求的url', [可选参数对象，使用{}传参]).then(成功回调函数, 失败回调函数);
     
    成功回调函数参数对象主要属性说明：
    1、url ： 请求的原始url
    2、body： 响应报文体中的数据（我们通常用这个属性获取服务器返回的数据）
    3、其他属性请看文档
    
    举例：
     this.$http.jsonp('http://vuecms.ittun.com/api/getlunbo?id=1').then(function(res){console.log(res.body)}, function(err){//err是异常数据});

```

#### Vue的生命周期方法

 ![](/assets/d2-6.png)

###Vue过渡动画


 * 通过 Vue.js 的过渡系统，可以在元素从 DOM 中插入或移除时自动应用过渡效果。Vue.js 会在适当的时机为你触发 CSS 过渡或动画
 
* 常用场景有：

  * 1、条件渲染 （使用 v-if）
  * 2、条件展示 （使用 v-show）
  * 3、动态组件
    


####transition的作用

```js

    1、在Vue1.0版本中为了应用过渡效果，需要在实现过渡动画的元素上使用 transition 特性，示例：
     <div v-if="show" transition="my-transition"></div> ,my-transition 可以有程序员自定义名称
      

    2、 在Vue2.0版本中改变成了由 transition特性的写法变成了 <transition></transition>的写法    
     <transition name="fade">
        <p v-if="show">hello</p>
      </transition>
    
```


 * transition通常与下面指令结合在一起使用：
       - v-if
       - v-show
       


####Vue中过渡动画的几种常用写法

 * 利用css控制过渡动画
  - Vue1.0写法
   ![](/assets/d3-1.png)
   
  - Vue2.0写法
   ![](/assets/d3-2.png)
   
 - 利用animate.css控制过渡动画
 
  - Vue1.0写法
   ![](/assets/d3-3.png)  

  - Vue2.0写法
   ![](/assets/d3-4.png)
  
 * 利用钩子函数控制过渡动画
 
    - Vue1.0 过渡动画API文档：http://v1-cn.vuejs.org/guide/transitions.html
    - Vue2.0 过渡动画API文档：http://cn.vuejs.org/v2/guide/transitions.html
    
    
 - Vue1.0钩子函数
    ```js
      1、过渡动画进入
          beforeEnter:function(el){}      过渡动画进入之前，一般在这个方法中定义目标元素的初始位置
          enter:function(el,done){}       过渡动画进入中，在这个方法中定义目标元素的结束位置
          afterEnter:function(el){}       过渡动画结束后，通常在这个方法里面重置初始值
          enterCancelled:function(el){}   取消过渡动画时被调用
      
      2、过渡动画离开
          beforeLeave:function(el){}      动画离开之前触发    
          leave:function(el){}            过渡动画进入中触发
          afterLeave:function(el){}       过渡动画离开结束后
          leaveCancelled:function(el){}   取消过渡动画时被调用

    ```
      3、使用示例：
       
      ![](/assets/d3-5.png)
      
- Vue2.0钩子函数

```js
     1、过渡动画进入
          before-enter      过渡动画进入之前，一般在这个方法中定义目标元素的初始位置
          enter             过渡动画进入中，在这个方法中定义目标元素的结束位置
          after-enter       过渡动画结束后，通常在这个方法里面重置初始值
          enter-cancelled   取消过渡动画时被调用
      
      2、过渡动画离开
          before-leave      动画离开之前触发    
          leave             过渡动画进入中触发
          after-leave       过渡动画离开结束后
          leave-cancelled   取消过渡动画时被调用

```

   3、使用示例：
   ![](/assets/d3-5.png)
   
   
####mian.js文件基本内容结构

mian.js文件基本内容结构
```js

    通过前面慢慢的演变，main.js文件中的基本内容结构如下：
    // 1.0 导入vue包
    import Vue from 'vue';
    
    // 2.0 导入 App.vue文件
    import App from './App.vue';
    
    // 3.0 vue-router相关的代码
    // 3.0.1 导入vue-router这个包
    import VueRouter from 'vue-router';  //相当于 <script src="vue-router.js">
    
    // 3.0.2 在Vue对象中通过use()方法来使用vue-router对象
    Vue.use(VueRouter);
    
    // 3.0.3 定义路由对象并且初始化路由规则
    // 3.0.3.1 导入需要注册的组件
    import home from './components/Home.vue';
    
    var vueRouterObj = new VueRouter({
    	linkActiveClass :'mui-active', //将激活的路由添加一个mui-active类名称
    	routes:[
    		{path:'/',redirect:'/Home'},
    		{path:'/Home',component:home},
    	]
    });
    // 4.0 mint-ui的使用
    // 4.0.1 导入mint-ui的样式
    import 'mint-ui/lib/style.min.css'
    // 4.0.2 导入mint-ui的组件包
    import mintUI  from 'mint-ui'
    // 4.0.3 将mintUI对象在Vue中通过use()进行绑定
    Vue.use(mintUI);
    // 5.0 导入mui的css
    import '../statics/mui/css/mui.css'
    import '../statics/mui/css/icons-extra.css'
    
    
    // 6.0 使用vue-resource
    // 6.0.1 导入vue-resource
    import vueResource  from 'vue-resource'
    // 6.0.2 使用
    Vue.use(vueResource);
    
    
    import '../statics/css/site.css'
    // 最后： 将App中的内容编译解析出来替换index.html中的<div id="app"></div>
    new Vue({
	el:'#app',
	router:vueRouterObj,  //使用路由规则对象
	// render:function(create){create(App);}  es5语法
	render:create=>create(App) //es6语法
});

```