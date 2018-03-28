###HTML5

* HTML5新增特性

 * < !DOCTYPE html>
 * 语义化标签
 * 表单类型、表单元素、表单属性、表单事件
 * 多媒体
 * DOM扩展
 * 自定义属性
 * 地理定位
 * Web存储



###新语义化标签

 * < nav> 表示导航
 * < header> 表示页眉
 * < footer> 表示页脚
 * < section> 表示区块
 * < article> 表示文章 如文章、评论、帖子、博客
 * < aside> 表示侧边栏 如文章的侧栏
 * < figure> 表示媒介内容分组
 * < mark> 表示标记
 * < progress> 表示进度
 * < time> 表示日期
 
#####尽量避免全局使用header、footer、aside等语义标签


####兼容处理

 *  在不支持HTML5新标签的浏览器里，会将这些新的标签解析成行内元素(inline)对待，所以我们只需要将其转换成块元素(block)即可使用，但是在IE9版本以下，并不能正常解析这些新标签，但是却可以识别通过document.createElement('tagName')创建的自定义标签，于是我们的解决方案就是将HTML5的新标签全部通过document.createElement('tagName')来创建一遍，这样IE低版本也能正常解析HTML5新标签了
 
 * 在实际开发中我们更多采用的是通过检测IE浏览器的版本来加载三方的一个JS库来解决兼容问题

```js
    <!-- 条件注释 只有ie能够识别 -->
    <!--[if lte ie 8]>
        <script src="html5shiv.min.js"></script>
    <![endif]-->
```
 
###表单

####表单类型
 
 * email 输入email格式
 * tel 手机号码  
 * url 只能输入url格式
 * number 只能输入数字
 * range 范围 滑动条
 * color 拾色器
 * time	时间
 * date 日期 不是绝对的
 * datetime 时间日期
 * month 月份
 * week 星期
 * search 搜索框
 

* 部分类型是针对移动设备生效的，且具有一定的兼容性，在实际应用当中可选择性的使用。

####表单元素（标签）

 * < datalist> 数据列表 与input 配合使用(会根据输入的内容进行匹配)

```html
 <input type=”text” list=”data”>
    <datalist id=”data”>
       <option>男</option>
       <option>女</option>
      <option>不详</option> 
    </datalist>
```
 * < keygen>  生成加密字符串
 
  *  keygen 元素的作用是提供一种验证用户的可靠方法。 
  *  keygen 元素是密钥对生成器(key-pair generator),当提交表单时,会生成两个键,一个是私钥，一个公钥。 
  *  私钥（private key）存储于客户端，公钥（public key）则被发送到服务器。公钥可用于之后验证用户的客户端证书（client certificate）。
  
 * < output>   输出 不可当做数据提交
 * < meter>   表示度量器，不建议用作进度条
```html
<meter value="81" min="0" max="100" low="60" height="80"/>
``` 
 * < progress>< /progress> 进度条

####表单属性

 * placeholder 占位符
 * autofocus 获取焦点
 * multiple 文件上传多选或多个邮箱地址  
 * autocomplete 自动完成，用于表单元素，也可用于表单自身(on/off)
 * form 指定表单项属于哪个form，处理复杂表单时会需要
 * novalidate 关闭验证，可用于< form>标签
 * required 必填项
 * pattern 正则表达式 验证表单
 ```html
 //验证手机号
 <input type="tel" name="tel" required="required"  pattern="^(\+86)?1[3,5,8](\d{9})$">
 ```
####表单事件
 
 * oninput 用户输入内容时触发，可用于移动端输入字数统计
 * oninvalid 验证不通过时触发
 
```html
   <form action="">
        <fieldset>
            <label for="">
                <legend>表单事件</legend>
                邮箱:
                <input type="email" name="" id="txt1">
            </label>
            <label for="">
                用户名:
                <input type="text" name="" id="txt2">
            </label>
            <input type="submit">
        </fieldset>
    </form>
```    
```js
    //表单事件: oninput 当用户输入的时候
    //oninvalid 当验证不通过的时候触发
    var txt1 = document.getElementById("txt1");
    var txt2 = document.getElementById("txt2");
    var num = 0;
    txt1.oninput = function() {
        num++;
        //将字数显示在txt2中
        txt2.value = num;
    }


    //oninvalid 当验证不通过的时候触发
    //一般用于页面不通过时的 设置提示文字
    txt1.oninvalid = function() {
    	this.setCustomValidity("亲,请输入正确的邮箱格式！");
    }
    
``` 
###多媒体

####音频

 * HTML5通过< audio>标签来解决音频播放的问题。
 
```html
   <!--通过指src属性定音频文件的路径-->
  <audio src="music/yinyue.mp3"></audio>
``` 
* 属性：

 * autoplay 自动播放
 * controls 是否显不默认播放控件
 * loop 循环播放
 * preload 预加载 同时设置autoplay时些属性失效


* 兼容处理： 
 ![](/assets/audio.png)
 
 
```html
    <audio controls loop>
        <source src="music/yinyue.mp3">
        <source src="music/yinyue.ogg">
        <source src="music/yinyue.wav">
        抱歉,你的浏览器不支持音频标签!
    </audio>
```
####视频

 * HTML5通过< video>标签来解决音频播放的问题。
 
```html
 <!--通过指src属性定视频文件的路径-->
 <video src="video/movie.mp4"></video>
```
 * 属性：
 
  * autoplay 自动播放
  * controls 是否显示默认播放控件
  * loop 循环播放
  * preload 预加载，同时设置了autoplay，此属性将失效
  * width 设置播放窗口宽度
  * height 设置播放窗口的高度
  
* 兼容处理
   
   ![](/assets/meida.png)

```html
    <video controls autoplay loop>
        <source src="video/movie.mp4">
        <source src="video/movie.ogg">
        <source src="video/movie.webm"> 您的浏览器不支持HTML视频播放功能
    </video>
```

###DOM扩展

####获取元素

 * document.getElementsByClassName ('class') 通过类名获取元素，以类数组形式存在
 * document.querySelector(‘div’) 通过CSS选择器获取元素，符合匹配条件的第1个元素
 * document.querySelectorAll('selector') 通过CSS选择器获取元素，以类数组形式存在

####类名操作

 * Node.classList.add('class') 添加class
 * Node.classList.remove('class') 移除class
 * Node.classList.toggle('class') 切换class，有则移除，无则添加
 * Node.classList.contains('class') 检测是否存在class

###自定义属性

* 在HTML5中我们可以自定义属性，其格式如下data-*=""，例如data-info="我是自定义属性"，通过

 Node.dataset['info'] 我们便可以获取到自定义的属性值。

* Node.dataset是以类对象形式存在的当我们如下格式设置时，则需要以驼峰格式才能正确获取

 data-my-name="itcast"，获取Node.dataset['myName']

###新增API

####多媒体

 * 方法：
 
   * load() 加载、play() 播放、pause() 暂停
 

 * 属性：
 
   * currentTime 视频播放的当前进度、
   * duration:视频的总时间
   * paused:视频播放的状态.
   
   
 * 事件：
 
  * oncanplay: 事件在用户可以开始播放视频/音频（audio/video）时触发。
  * ontimeupdate:通过该事件来报告当前的播放进度.
  * onended:播放完时触发
  
 * 全屏：
 
  * video.webkitRequestFullScreen();
  
####拖拽

 * 在HTML5的规范中，可以通过为元素增加draggable="true"来设置此元素是否可以进行拖拽操作，其中图片、链接默认是开启的。
 
####拖拽元素

 * 页面中设置了draggable="true"属性的元素

####目标元素

 * 页面中任何一个元素都可以成为目标元素
 
####事件监听

 * 拖拽元素：
  
  * ondrag      应用于拖拽元素，整个拖拽过程都会调用
  * ondragstart 应用于拖拽元素，当拖拽开始时调用
  * ondragleave 应用于拖拽元素，当鼠标离开拖拽元素时调用
  * ondragend	 应用于拖拽元素，当拖拽结束时调用
  
 * 目标元素：
 
  * ondrag 	应用于拖拽元素，整个拖拽过程都会调用
  * ondragstart	应用于拖拽元素，当拖拽开始时调用
  * ondragleave	应用于拖拽元素，当鼠标离开拖拽元素时调用
  * ondragend	应用于拖拽元素，当拖拽结束时调用

###地理定位 
 
 * 在HTML规范中，增加了获取用户地理信息的API，这样使得我们可以基于用户位置开发互联网应用，即基于位置服务 (Location Base Service)

####获取地理信息方式

 * IP地址
 
 * 三维坐标 GPS Wi-Fi 手机信号
 
 * 用户自定义数据
 
  ![](/assets/local.png)
  
####隐私
 
 * HTML5 Geolocation(地理位置定位) 规范提供了一套保护用户隐私的机制。必须先得到用户明确许可，才能获取用户的位置信息。
 
####API详解
 
 * navigator.getCurrentPosition(successCallback, errorCallback, options) 获取当前地理信息
 * navigator.watchPosition(successCallback, errorCallback, options) 重复获取当前地理信息
  
  * 当成功获取地理信息后，会调用succssCallback，并返回一个包含位置信息的对象position  
  
    * Coords(坐标) position.coords.latitude纬度 position.coords.longitude经度
  
    * 当获取地理信息失败后，会调用errorCallback，并返回错误信息error
    
    * 可选参数 options 对象可以调整位置信息数据收集方式
    
###Web存储

* Storage 存储  
   * window.sessionStorage
   * window.localStorage
 
 
* 特性：
  * 设置、读取方便
  * 容量较大，sessionStorage约5M、localStorage约20M
  * 只能存储字符串，可以将对象JSON.stringify() 编码后存储

* 其他：
  
  * WebSQL已经被w3c 放弃了  IndexDB
  
  
####网络状态

 * 通过window.onLine来检测，用户当前的网络状况，返回一个布尔值
 
  *  window.online用户网络连接时被调用
  *  window.offline用户网络断开时被调用 
  
```js
   window.addEventListener("online", function() {
        alert("网络已连接!");
    })
    window.addEventListener("offline", function() {
        alert("网络已断开!");
    })
```
####应用缓存

 * HTML5中我们可以轻松的构建一个离线（无网络状态）应用，只需要创建一个cache manifest文件。
 
###优势:
  
  * 可配置需要缓存的资源
  * 网络无连接应用仍可用
  * 本地读取缓存资源，提升访问速度，增强用户体验
  * 减少请求，缓解服务器负担

####缓存清单

 * 一个普通文本文件，其中列出了浏览器应缓存以供离线访问的资源，推荐使用.appcache为后缀名，添加MIME类型
  
   AddType text/cache-manifest .appcache 
   
   * 例如我们创建了一个名为demo.appcache的文件，然后在需要应用缓存在页面的根元素(html)添加属性manifest="demo.appcache"，路径要保证正确
   
   
####manifest文件格式

* 顶行写CACHE MANIFEST
* CACHE: 换行 指定我们需要缓存的静态资源，如.css、image、js等
* NETWORK: 换行 指定需要在线访问的资源，可使用通配符
* FALLBACK: 当前页面无法访问时退回的页面(回退;  后退)
* 换行 当被缓存的文件找不到时的备用资源 



####Font Awesome 字体框架

 * Font Awesome为您提供可缩放的矢量图标，可以使用CSS所提供的所有特性对它们进行更改，包括：大小、颜色、阴影或者其它任何支持的效果 