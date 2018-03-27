###CSS基础


####选择器

* 基础选择器

  * 标签选择器 h1,h2
  * 类选择器   .box
  * ID选择器   #box
  * 通配符选择器 *


* 复合选择器

  * 标签指定式选择器 h3.special h3#space
  * 后代选择器  .box h1
  * 并集选择器 #box1,#box2
  

####CSS3新增选择器

* 属性选择器
  
   * 语法：

     * 标志性符号:[]
     
     * ^:开头  $:结尾  *:包含
     
```css
 E[title]:选中页面的E元素,并且需要带有title属性
 E[title="abc"]:选中页面E的元素,并且E需要带有title属性,属性值为abc
 E[title^="abc"]:选中页面E的元素,并且E需要带有title属性,属性值为abc开头
 E[title$="abc"]:选中页面E的元素,并且E需要带有title属性,属性值为abc结尾
 E[title*="abc"]:选中页面E的元素,并且E需要带有title属性,属性值为包含abc
```
* 结构伪类选择器:

```css
	E:first-child 选中父元素中的第一个子元素
	E:last-chhild 选中父元素中的最后一个子元素
	E:nth-child(n) 选中u父元素中的第5个子元素
	n: 0,1,2,3,4,5......
	偶数:2n    even
	奇数:2n-1   odd
	前5个:-n+5;
	E:nth-last-child(3):从后向前选择,选中倒数第3个
	E:nth-last-child(-n+3):选中后3个
	注意:所选到的元素类型 必须是指定的E,否则选择无效

	E:empty  表示元素为空的状态
	E:target 表示元素被激活的状态 要配合锚点使用

```  
* 伪元素:

```css
      通过css模拟出html效果
      E::before
      E::after  必须content属性

```
* 伪元素选择器:
```css
	E::first-letter 选中第一个字母
	E::first-line选中第一行
	E::selection:表示选择的区域 通过设置背景颜色和颜色
 ```
####CSS样式类型

* 内联式(行内式)
* 内嵌式
* 外链式


####HTML标签
 
 * 块级标签
 * 行内标签
 * 行内块标签
 
####块级标签
 
    html、div、p、h1、form、ul、li
  
* 块级标签的三大特点：

  * 一个块级元素独占一行
  * 元素的高度、宽度、行高以及和顶部和底部边距都可以设置
  * 元素宽度在不一致的情况下,是它本身父容器的100%(和父元素的宽度一致,除非设置一个宽度)

####行内元素

    a、span、br、i、em、strong、label
    
* 行内元素的三大特点:

  * 和其它元素都在一行上
  * 元素的高度、宽度、行高以及顶部和底部边距不可设置
  * 元素的宽度就是它包含的文字或图片的宽度,不可改变
   
####行内块元素

     img、input
 
 * 特点:
   
  *  同时具备内联元素、块状元素的特点
  
  
####元素转换

  * 将行内元素转换成块级元素
  
   * display:block;
   
   
  * 将行内元素装换成行内块元素
  
   * display:inline-block
   
   
  * 装换成行内元素
  
   * display:inline
   
   
####CSS三大特性

 * 层叠性：多种样式的层叠
 
 * 继承性:子标记会继承父标记的某些样式
 
   * 字体相关的可继承:color、text、font、line、cursor
   * 不具继承性:边框、外边距、内边距、背景、定位、宽高等
   *  盒子相关的属性不能继承：a标签、h1标签
   
   
 * 优先级
 
   important>内联>ID>伪类|类|属性选择>标签>伪对象>通配符>继承


####CSS伪类

* :link

  伪类将应用于未被访问过的链接。IE6不兼容，解决此问题，直接使用a标签。
  
* :hover

  伪类将应用于有鼠标指针悬停于其上的元素。在IE6只能应用于a连接，IE7+所有元素都兼容。
  
* :active

  伪类将应用于被激活的元素，如被点击的链接、被按下的按钮等。
  
* :visited

  伪类将应用于已经被访问过的链接
  
* :focus

  伪类将应用于拥有键盘输入焦点的元素。
  
 顺序问题：LoVe  HAte原则。
 
####外边距合并问题

![](/assets/QQ截图20180323163709.png)
![](/assets/QQ截图20180323163855.png)
 
 
####行内元素 padding和margin问题

 * 行内元素不要给上下的margin和padding
 * 上下margin和padding会被忽略
 * 左右margin和padding会起作用
 
 
 ####float浮动
 
* 浮动找浮动，不浮动找不浮动
* 浮动只影响后面的元素
* 浮动以元素顶部为基准对齐
* 浮动可是实现模式转换（span 设置浮动可以设置宽高）
* 让块级元素在一行显示

 
####清除浮动的方式

  * 给父容器设置高度 
  * 通过设置clear：left|right|both
  * 给父容器设置overflow:hidden
  * 通过伪元素
  
```css
  
   .clearfix:after{
     content:'';
     height:0;
     line-height:0;
     visibility:hidden
     clear:both;
     display:block;
   }
   .clearfix{
     zoom:1  //兼容ie
   }     
 ```         
                          
 ####CSS可见性
 
  * display:none; 元素隐藏不占位置
  
  * overflow:hidden; 将超出部分隐藏
  
  * visibility:hidden;元素隐藏占位置
 