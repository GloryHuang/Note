###Decorator 修饰器

     * Decorator是一个函数,用来修改类的行为(扩展类的行为)

```js
//限制某个属性是只读的
//target：修改的类本身
//name:修改了属性的名称
//descriptor:该属性的描述对象
{
    let readonly = function(target, name, descriptor) {
        descriptor.writable = false; //不允许修改
        return descriptor;
    };



    class Test {
        @readonly //不允许修改
        time() {
            return '2017-11-8'
        }
    }
    let test = new Test();


    // test.time()=function(){
    // 	console.log('reset time');
    // }
    console.log(test.time());
}



{
    let typename = function(target, name, descriptor) {
        target.myname = 'hello';
    }
    @typename
    class Test {

    }

    console.log('类修饰符', Test.myname);

    //第三方库修饰器的js库:core-descriptor; nmp install descriptor
}


```



####日志系统

```js
//日志系统
{
    let log = (type) => {
        return function(target, name, descriptor) {
            let src_method = descriptor.value;
            descriptor.value = (...arg) => {
                src_method.apply(target, arg);
                console.info('log', `${type}`);
            }
        }
    }


    class AD {
        @log('show')
        show() {
            console.info('ad is show!');
        }

        @log('click')
        click() {
            console.info('ad is click');
        }
    }
    let ad = new AD();
    ad.show();
    ad.click();
}
```