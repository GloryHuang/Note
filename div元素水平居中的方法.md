###水平居中

####水平居中布局

 * 水平居中
  
   * 对于行内元素(inline)：text-align: center;
   * 对于块级元素(block)：设置宽度且 marigin-left 和 margin-right 是设成 auto
   * 对于多个块级元素：对父元素设置 text-align: center;，     
 对子元素设置 display: inline-block;；或者使用 flex 布局
   
####垂直居中布局

 * 垂直居中
 
  * 对于行内元素(inline)
   
    * 单行：设置上下 pandding 相等；或者设置 line-height 和 height 相等

    * 多行：设置上下 pandding 相等；或者设置 display: table-cell; 和 vertical-align: middle;；或者使用 flex 布局；或者使用伪元素

   * 对于块级元素(block)：下面前两种方案，父元素需使用相对布局
    * 已知高度：子元素使用绝对布局 top: 50%;，再用负的 margin-top 把子元素往上拉一半的高度
    * 未知高度：子元素使用绝对布局 position: absolute; top: 50%; transform: translateY(-50%);
    * 使用 Flexbox：选择方向，justify-content: center;
   
####水平垂直居中布局

 * 水平垂直居中
 
   * 定高定宽：先用绝对布局 top: 50%; left: 50%;，再用和宽高的一半相等的负 margin 把子元素回拉
   
   * 高度和宽度未知：先用绝对布局 top: 50%; left: 50%;，再设置 transform: translate(-50%, -50%);
   
   * 使用 Flexbox：justify-content: center; align-items: center;
响应式设计 
 


####注

* 行内元素的内边距对左、右、下起作用。
* 行内元素的外边距只对左、右起作用。
   
* 行内元素只能容纳文本或者其他行内元素。不可以设置宽高，其宽度随着内容增加，高度随字体大小而改变， 内联元素可以设置外边界，但是外边界不对上下起作用，只能对左右起作用，也可以设置内边界， 但是内边界在ie6中不对上下起作用，只能对左右起作用