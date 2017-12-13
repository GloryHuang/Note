###盒模型

####基本概念:盒模型+IE模型

    border+margin+padding+content
    
####标准模型和IE模型的区别
        
    就是计算宽度和高度的不同
    
#####标准模型(不包含padding和border)
    
![](/assets/QQ截图20171213175025.png)
        
#####IE模型

![](/assets/QQ截图20171213175319.png)

####CSS是如何设置这种模型

    box-sizing:content-box;
    box-sizing:border-box;
    

####JS如何设置获取盒模型对应的宽和高




####实例题(根据盒模型解释边距重叠)



####BFC(边距重叠解决方案)