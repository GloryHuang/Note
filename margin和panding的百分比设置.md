###CSS常见问题

####margin和pading的百分比值

    * margin和pading的百分比值参考的是父级元素的width。
    
####文字超出部分省略

```css
     overflow: hidden;
     text-overflow: ellipsis;
     white-space: nowrap;
 ```
 
 
####子元素margin影响父元素解决办法

 * overflow: hidden;
 
 * border: 1px solid transparent;
 
 * float: left;
 
 * padding-top: 1px;
 
 * position: absolute;

  ![](/assets/margin.png)

####inline-block之间空白间距问题的解决方法
 
 * letter-spacing: -3px;
 
 * word-spacing:-3px;
 
 * 给父元素设置font-size:0;
   
 * 使用float
 
 * 使用html注释消除空格的方法 或者将行内块元素放到一行显示

```html
      <!--尽量不换行-->
      <ul>
        <li>1</l1><li>2</l1><li>2</l1>
      </ul>
 ```  
    

####text-transform

 * 控制文本的大小写
  
  * capitalize:文本中的每个单词以大写字母开头
  * uppercase: 定义仅有大写字母
  * lowercase: 定义无大写字母，仅有小写字母。
