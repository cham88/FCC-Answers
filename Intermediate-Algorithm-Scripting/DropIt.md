## Drop It

![dropIt][1]

给出的提示：
[Arguments object][2]<br />
[Array.shift()][3]<br />
[Array.slice()][4]<br />

### 分析题目

题目前面一大段废话，写得像LOL的攻略…… 看得稀里糊涂orz
继续往下看，原来只不过是要实现一个类似filter的功能；
当然，和filter的功能又不一样
> `让我们来丢弃数组(arr)的元素，从左边开始，直到回调函数return true就停止。`

意思很明确，从arr[0]开始，直到某个值使回调函数return true；就不再对后面的进行检查了

> `第二个参数，func，是一个函数。用来测试数组的第一个元素，如果返回fasle，就从数组中抛出该元素(注意：此时数组已被改变)，继续测试数组的第一个元素，如果返回fasle，继续抛出，直到返回true。`

 这段话几乎已经把代码用语言表述出来了：
> 每次都是检查数组的第一个元素，`func(arr[0])`
> 如果返回false，就从数组中抛出这个元素（即第一个元素），代码就是
> ```
> if(!func(arr[0])){
> 	arr.shift();
> }
> ```
> 返回false还要继续检查原数组中的第二个元素；但由于arr.shift()会改变原数组，使用递归调用自身即可解决 加上一句 return drop(arr,func);
> 当返回true时，就结束，换成代码就是：if(func(arr[0])){return arr;}

> `最后返回数组的剩余部分，如果没有剩余，就返回一个空数组。`
> 解析成代码，就是 if(arr.length===0){return arr;}

最后把代码整理起来，解题方法就出来了

### 代码
```javascript
function drop(arr, func) {
  // Drop them elements.
  if(arr.length===0 || func(arr[0]) ){
    return arr;
  }else{
    arr.shift();
    return drop(arr,func);
  }
  
}

```


  [1]: ./images/1481893225266.jpg "1481893225266.jpg"
  [2]: https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Functions/arguments
  [3]: https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/shift
  [4]: https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/slice
