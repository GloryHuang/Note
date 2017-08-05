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
