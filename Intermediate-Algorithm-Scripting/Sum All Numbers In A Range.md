## Sum All Numbers in a Range


![题目截图][1]


**给出的提示：**
[Math.max()][2]<br />
[Math.min()][3]<br />
[Array.reduce()][4]<br />

### 题目分析

> 需求很明确：求给定数组中最大和最小两个数之间（包含）的所有数的和
> 如果参数是`[1,4]`,就求`1+2+3+4`的和
> 如果是`[4,1]`,同样是求`1+2+3+4`的和

### 思路
1. 找到参数中的最大值和最小值，那么介于之间的所有数就有了
> `Math.max();Math.min();分别可以获得最大和最小值`
> `也可以把arr排序，也很容易获得最大值和最小值`
2. 把这些数加起来
>` var result =0;把min和max之间所有数往result上加就行了`
> `提示使用Array.reduce()方法，好像还更麻烦了`

### 代码
```javascript
function sumAll(arr) {
  var max = Math.max(arr[0],arr[1]);
  var min = Math.min(arr[0],arr[1]);
  var result = 0;
  
  for(var i=min;i<=max;i++){
    result += i;
  }

  return result;
}

```




  [1]: ./images/1482156735134.jpg "1482156735134.jpg"
  [2]: https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Math/max
  [3]: https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Math/min
  [4]: https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce
