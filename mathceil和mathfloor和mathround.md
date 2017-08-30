###Math.ceil和Math.floor和Math.round

####Math.ceil(天花板函数)

    Math.ceil向上取整
    
####整数的时候 向上取整
    
    

    console.log(Math.ceil(16));

    //16

    console.log(Math.ceil(16.1));

    //17

    console.log(Math.ceil(16.5));

    //17

    console.log(Math.ceil(16.8));

    //17


####负数的时候 等于它自己

    console.log(Math.ceil(-16));

    //-16

    console.log(Math.ceil(16.1));

    //-16

    console.log(Math.ceil(16.5));

    //-16

    console.log(Math.ceil(-16.8));

    //-16
    



####Math.floor(地板函数)

    Math.floor向下取整

    

####整数的时候 等于它自己

    

    

    console.log(Math.floor(16));

    //16

    console.log(Math.floor(16.1));

    //16

    console.log(Math.floor(16.5));

    //16

    console.log(Math.floor(16.8));

    //16

####负数的时候 向下取整

    console.log(Math.floor(-16));

    //-16

    console.log(Math.floor(16.1));

    //-17

    console.log(Math.floor(16.5));

    //-17

    console.log(Math.floor(-16.8));

    //-17


####Math.round取整(四舍五入)

    Math.round();    //四舍五入    

####整数的时候 四舍五入

    console.log(Math.round(16));

    //16

    console.log(Math.round(16.1));

    //16

    console.log(Math.round(16.5));

    //17

    console.log(Math.round(-16.8));

    //17

  
####负数的时候 大于5减

    console.log(Math.round(-16));

    //16

    console.log(Math.round(-16.1));

    //16

    console.log(Math.round(-16.5));

    //16

    console.log(Math.round(-16.8));

    //-17
