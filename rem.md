###Rem

* 常见移动端web适配方法

 * PC
    
   * 960/1000px 居中
   
   * 盒子模型,定宽,定高
   
   * display:inline-block
   
 
 * 移动Web
 
  * 定高,宽度百分比
  
  * flex
  
  * Media Query(媒体查询)
  
  
###Rem原理

 * 字体单位
 
   * 值根据html根元素大小而定, 同样可以作为宽度、高度等单位
   
   
 * 适配原理
  
   * 将px替换成rem,动态修改html的font-size适配
   
   
 * 兼容性
 
   * ios 6以上android 2.1以上,基本覆盖所有流行的手机系统
   
 
###Rem计算

```js
    //获取视窗宽度(Viewport)
    let htmlWidth = document.documentElement.clientWidth || document.body.clientWidth;

    //获取视窗高度
    let htmlDom = document.getElementsByTagName('html')[0];

    //设置html的font-size
    htmlDom.style.fontSize = htmlWidth / 10 + 'px';
```