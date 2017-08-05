###Navigator对象

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

```js
