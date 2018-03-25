###Flex

* justify-content:

 用于设置或检索弹性盒子元素在主轴（横轴）方向上的对齐方式

 * flex-start: 元素和容器的左端对齐。
 * flex-end: 元素和容器的右端对齐。
 * center: 元素在容器里居中。
 * space-between:元素之间保持相等的距离。
 * space-around:元素周围保持相等的距离。


* align-items:

 属性定义flex子项在flex容器的当前行的侧轴（纵轴）方向上的对齐方式。
 * flex-start: 元素与容器的顶部对齐。
 * flex-end: 元素与容器的底部对齐。
 * center: 元素纵向居中。
 * baseline: 元素在容器的基线位置显示。
 * stretch: 元素被拉伸以填满整个容器。
 
 
* flex-direction:

 属性规定灵活项目的方向
 
 * row: 元素摆放的方向和文字方向一致。
 * row-reverse: 元素摆放的方向和文字方向相反。
 * column: 元素从上放到下。
 * column-reverse: 元素从下放到上。
 
 
 * order:
 
  设置或检索弹性盒模型对象的子元素出现的顺序。
  
  * 元素的属性默认值为0，但是我们设置这个属性为正数或负数。调整元素的位置
  * 以当前元素的下标开始   (-3,-2,-1, (0) ,1,2,3)
  
 
 * align-self:
 
  属性定义flex子项单独在侧轴（纵轴）方向上的对齐方式。
  
  * flex-start: 元素与容器的顶部对齐。
  * flex-end: 元素与容器的底部对齐。
  * center: 元素纵向居中。
  * baseline: 元素在容器的基线位置显示。
  * stretch: 元素被拉伸以填满整个容器。


* flex-wrap:

  属性规定flex容器是单行或者多行，同时横轴的方向决定了新行堆叠的方向

 * nowrap: 所有的元素都在一行。
 * wrap: 元素自动换成多行。
 * wrap-reverse: 元素自动换成逆序的多行
 
 
* flex-flow:  (flex-direction)  (flex-wrap)

 * flex-direction和flex-wrap两个属性经常会一起使用。所以有缩写属性flex-flow。这个缩写属性接受两个属性的值，两个值中间以空格隔开。
 
 
* align-content：

 属性在弹性容器内的各项没有占用交叉轴上所有可用的空间时对齐容器内的各项（垂直）

 * flex-start: 多行都集中在顶部。
 * flex-end: 多行都集中在底部。
 * center: 多行居中。
 * space-between: 行与行之间保持相等距离。
 * space-around: 每行的周围保持相等距离。
 * stretch: 每一行都被拉伸以填满容器。
