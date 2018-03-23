###获取元素节点的封装


```js


function getEle(id) {
    return document.getElementById(id);
}

/**
 * 功能：给定元素查找他的第一个元素的子节点,并返回
 * @param   ele
 * @return  {Element|*|Node}
 */
function getFirstNode(ele) {
    var node = ele.firstElementChild || ele.firstChild;
    return node;
}

/**
 * 功能：给定元素查找他的最后一个元素的子节点,并返回
 * @param   ele
 * @return  {Element|*|Node}
 */
function getLastNode(ele) {
    return ele.lastElementChild || ele.lastChild;
}

/**
 * 功能：给定元素查找他的下一个元素的兄弟节点,并返回
 * @param   ele
 * @return  {Element|*|Node}
 */

function getNextNode(ele) {
    return ele.nextElementSibling || ele.nextSibling;
}

/**
 * 功能：给定元素查找他的上一个元素的兄弟节点,并返回
 * @param   ele
 * @return  {Element|*|Node}
 */

function getPrevNode(ele) {
    return ele.previousElementSibling || ele.previousSibling;
}

/**
 * 功能：给定元素和索引值查找指定索引值的兄弟元素节点,并返回
 * @param   ele    元素节点
 * @param   index  索引值
 * @return  {Element|*|Node}
 */
function getEleOfIndex(ele,index) {
    return ele.parentNode.children[index];
}

/**
 * 功能：给定元素查找所有的兄弟元素,将来返回数组
 * @param   ele    元素节点
 * @param   index  索引值
 * @return  {Element|*|Node}
 */
function getAllSublings(ele) {
    //定义一个新数组,装所有的兄弟元素,将来返回
    var newArr = [];
    var arr = ele.parentNode.children;
    for (var i = 0; i < arr.length; i++) {
        //判断：如果不是传递过来元素的本身,那么添加到新数组中。
        if (ele != arr[i]) {
            newArr.push(arr[i]);
        }
    }
    return newArr;
}








```