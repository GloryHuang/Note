####缓动框架封装(单个属性)

```js
       //参数变为3个
        function animate(ele,attr,target){
            //先清定时器
            clearInterval(ele.timer);
            ele.timer = setInterval(function () {
                //四部
                var leader = parseInt(getStyle(ele,attr)) || 0;
                //1.获取步长
                var step = (target - leader)/10;
                //2.二次加工步长
                step = step>0?Math.ceil(step):Math.floor(step);
                leader = leader + step;
                //3.赋值
                ele.style[attr] = leader + "px";
                 //4.清除定时器
                if(Math.abs(target-leader)<=Math.abs(step)){
                    ele.style[attr] = target + "px";
                    clearInterval(ele.timer);
                }

            },25);
        }




        //兼容方法获取元素样式
        function getStyle(ele,attr){
            if(window.getComputedStyle){
                return window.getComputedStyle(ele,null)[attr];
            }
            return ele.currentStyle[attr];
        }




```
