###Module模块化


 * 基本概念
 * ES6的基本模块化语法
 * ES6模块的引入:import 
 * ES6模块导出:export


```js 
//不建议
// export let A = 123;


// export function test() {
//     console.log('Test');
// }


// export class Hello {
//     test() {
//         console.log('class');
//     }
// }


let A = 123;
let test = function() {
    console.log('test');
}
class Hello {
    test() {
        console.log('class');
    }

}


export default {
    A,
    test,
    Hello
}

```