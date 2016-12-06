## Convert HTML Entities


![Convert HTML Entities][1]

**有帮助的资源：**
[RegExp][2]  	
[HTML Entities][3]

### 思路：
1. 思路一：
   - 写一个正则匹配这些要替换的字符
   - 查出这些字符对应的*HTML Entities*
   - 替换文本中的全部这些字符
2. 思路二：
   - 五种字符，逐一替换成其实体`str.replace().replace()...`
   - 相比第一种思路，代码会短不少，但是感觉扩展性太差了些
### Code
```javascript 
// 思路一:
function convert(str) {
	// &colon;&rpar;
	var HTML_Entities = {
	    "&":"&amp;",
	    "<":"&lt;",
	    ">":"&gt;",
	    '"':"&quot;",
	    "'":"&apos;"
	};
	var myreg = /[&<>"']/g;
	var arr = str.match(myreg);
	
	if(!arr){
	    return str;
	}else{
	    for(var i=0;i<arr.length;i++){
	        str = str.replace(arr[i],HTML_Entities[arr[i]]);
	    }
	return str;
	}
}
```
```javascript
// 思路二：
function convert(str) {
	return str.replace( /&/g,"&").replace(//g,">").replace(/"/g,""").replace(/'/g,"'");
}
```

### 测试
[Convert HTML Entities][4]


  [1]: ./images/1481022467098.jpg "Convert HTML Entities.jpg"
  [2]:https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/RegExp
  [3]: http://dev.w3.org/html5/html-author/charref
  [4]: https://www.freecodecamp.cn/challenges/convert-html-entities
