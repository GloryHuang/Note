### Navigator对象

Navigator 对象包含有关浏览器的信息，通常用于检测浏览器与操作系统的版本。

对象属性:
    ![](/assets/5354cff70001428b06880190.jpg)

查看浏览器的名称和版本，代码如下:

```js
var browser=navigator.appName; 
var b_version=navigator.appVersion; 
document.write("Browser name"+browser);
document.write("<br>"); 
document.write("Browser version"+b_version);
```

### userAgent

```js
使用userAgent判断使用的是什么浏览器(假设使用的是IE8浏览器),代码如下:

function validB(){ 
  var u_agent = navigator.userAgent; 
  var B_name="Failed to identify the browser"; 
  if(u_agent.indexOf("Firefox")>-1){ 
      B_name="Firefox"; 
  }else if(u_agent.indexOf("Chrome")>-1){ 
      B_name="Chrome"; 
  }else if(u_agent.indexOf("MSIE")>-1&&u_agent.indexOf("Trident")>-1){ 
      B_name="IE(8-10)";  
  }
    document.write("B_name:"+B_name+"<br>");
    document.write("u_agent:"+u_agent+"<br>"); 
} 
```



###screen对象

    screen对象用于获取用户的屏幕信息。

    语法：

    window.screen.属性

    对象属性:
   ![](/assets/5354d2810001a47706210213.jpg)

###屏幕分辨率的高和宽
    
  window.screen 对象包含有关用户屏幕的信息。
    1. screen.height 返回屏幕分辨率的高
    2. screen.width 返回屏幕分辨率的宽
    注意:
    1.单位以像素计。
    2. window.screen 对象在编写时可以不使用 window 这个前缀。
    我们来获取屏幕的高和宽，代码如下:
```js
    document.write( "屏幕宽度："+screen.width+"px<br />" );
    document.write( "屏幕高度："+screen.height+"px<br />" );
```