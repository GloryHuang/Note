###Proxy 和 Reflect

     * Proxy和Reflect的概念
     * Proxy和Reflect的适用场景

####Proxy 代理

```js
// Proxy 代理
{
    let obj = {
        time: '2017-03-11',
        name: 'net',
        _r: 123
    };


    let momitor = new Proxy(obj, {

        //拦截对象属性的读取
        get(target, key) {
            return target[key].replace('2017', '2018');
        },

        //拦截对象设置属性
        set(target, key, value) {
            if (key === 'name') {
                return target[key] = value;
            } else {
                return target[key];
            }
        },
        //拦截 key in object操作
        has(target, key) {
            if (name === 'name') {
                return target[key] = value;
            } else {
                return target[key];
            }
        },
        //拦截delete
        deleteProperty(target, key) {
            if (key.indexOf('_') > -1) {
                delete target[key];
                return true;
            } else {
                return target[key];
            }
        },
        //拦截Object.keys,Object.getOwnPropertySymbol,Object.getPropertyName
        ownKeys(target) {
            return Object.keys(target).filter(item => item != 'time');
        }
    });
    console.log('get', momitor.time);
    momitor.time = '2018';
    momitor.name = 'wanghao';
    console.log('set', momitor.time, momitor);
    console.log('has', momitor.time, 'name' in momitor, 'time' in momitor);
    console.log('delete', momitor);

    // delete momitor.time;
    // console.log('delete', momitor);

    // delete momitor._r;
    // console.log('delete', momitor);


    console.log('ownKeys', Object.keys(momitor));



}

```



####Reflect

```js
//Reflect

{
    let obj = {
        time: '2017-03-11',
        name: 'net',
        _r: 123
    };

    console.log('Reflect get', Reflect.get(obj, 'time'));
    Reflect.set(obj, 'name', 'mukewang');
    console.log(obj);
    console.log('has', Reflect.has(obj, 'name'));

}


{
    function validator(target, validator) {
        return new Proxy(target, {
            _validator: validator,
            set(target, key, value, proxy) {
                if (target.hasOwnProperty(key)) {
                    let va = this._validator[key];
                    if (!!va(value)) {
                        return Reflect.set(target, key, value, proxy)
                    } else {
                        throw Error(`不能设置${key}到${value}`)
                    }
                } else {
                    throw Error(`${key} 不存在`);
                }
            }

        })
    }



    const personValidators = {
        name(val) {
            return typeof val === 'string'
        },
        age(val) {
            return typeof val === 'number' && val > 18
        },
        moblie(val){

        }
    }



    class Person {
        construcotr(name, age) {
            this.name = name;
            tihs.age = age;
            this.moblie='1111';
            return validator(this.personValidators);
        }
    }


    const person = new Person('lilei', 30);

    console.info(person);


    person.name = 'Han mei mei'
    console.info(person);

}
```