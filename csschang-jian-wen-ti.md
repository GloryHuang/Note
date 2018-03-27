###CSS常见问题

* 子元素margin影响父元素解决办法

 * overflow: hidden;
 
 * border: 1px solid transparent;
 
 * float: left;
 
 * padding-top: 1px;
 
 * position: absolute;

  ![](/assets/margin.png)

* inline-block之间空白间距问题的解决方法
 
 * letter-spacing: -3px;
 
 * word-spacing:-3px;
 
 * 给父元素设置font-size:0;
 
 * 标签结束处消除换行符，或者把换行符添加到标签内部
 