## Spinal Tap Case

![题目截图][1]

给出的提示：
[RegExp][2]  
[String.replace()][3]  

要达到的效果：
![测试结果][4]

### 思路

题目要求很明确，把短语或句子中的单词用`-`连接起来，并且全部为小写。

给出了四个测试的短语，其中三个，也就是把`空格`或者`下划线`替换成`-`就行，然后再转小写；难的是`"thisIsSpinalTap"`这种

我的解题思路是这样的，先把`thisIsSpinalTap`这种句型转换成这样`this Is Spinal Tap`，也就是在句中的大写字母前加一个`空格`，再后面就是替换的事情了。
> 不知道能不能不加空格，直接写一个正则匹配，然后替换 ？这样的正则我还真不知道怎么写……

### 代码

```javascript
// 我的代码：
function spinalCase(str) {
  // "It's such a fine line between stupid, and clever."
  // --David St. Hubbins
  var myReg = /[\s_]/g;
  var arr = str.split("");
  
  for(var i=1;i<arr.length;i++){
  
    if(arr[i].charCodeAt(0)>="A".charCodeAt(0) && arr[i].charCodeAt(0)<="Z".charCodeAt(0) && arr[i-1].charCodeAt(0)>="a".charCodeAt(0) && arr[i-1].charCodeAt(0)<="z".charCodeAt(0)){
      arr[i] = " " + arr[i];      
    }
  }
  
  str = arr.join("");
  str = str.replace(myReg,"-");
  return str.toLowerCase();
}

// 网上的代码（来源：http://www.tuicool.com/articles/QZreIfi）
function spinalCase(str) {
  // "It's such a fine line between stupid, and clever."
  // --David St. Hubbins
  str = str.replace(/_/g," ")
        .replace(/([A-Z])/g," $1")
        .replace(/^\s/,"")
        .replace(/\s+/g,"-")
        .toLowerCase();
  return str;
}
```
### 总结
> 效果是实现了，但是代码中的`if`的判断条件，连用3个`&&`感觉不太好，但现在确实没想到更好的办法
> 搜索了一下别人的解法，代码已经付在上面了[链接][5]；比我写的简洁多了，一行代码就搞定了……
> 正则，感觉好难……


  [1]: ./images/1481459267110.jpg "1481459267110.jpg"
  [2]: https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/RegExp
  [3]: https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/replace
  [4]: ./images/1481459548243.jpg "1481459548243.jpg"
  [5]: http://www.tuicool.com/articles/QZreIfi
