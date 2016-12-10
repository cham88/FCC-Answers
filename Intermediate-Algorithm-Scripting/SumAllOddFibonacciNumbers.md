## Sum All Odd Fibonacci Numbers

![题目截图][1]<br>

参考文档链接：
[博客园][2]
[Issue][3]
提供的提示：
[Remainder][4]

### 思路
	
题目的要求很明确，解题思路也很简单
1. 先要获得斐波拉契数列
2. 然后找到其中的奇数
3. 再将这些奇数加起来

### 代码
> 代码可能有点冗长，但是思路很清晰，直来直去的，相信其他的解题方法也是按照这个思路来的

```javascript
function sumFibs(num) {
  if(num<2){
    return 1;
  }
  var fibs = [1,1];//斐波那契数列初始值
  var returnSum = 0;//储存最后的结果
  var oddFibs = [];//奇数
  
  var index = 1; 
  while ((fibs[index] + fibs[index-1])<= num){
      fibs[index+1] = fibs[index] + fibs[index-1];
      index++;
  }//求出不大于num的斐波那契数列
  
/*  
  for(var i=0;i<fibs.length;i++){
    if(fibs[i]%2 == 1){
      oddFibs.push(fibs[i]);
    }
  }//筛选出其中的奇数 ,方法一
 */
  
  oddFibs = fibs.filter(function(value,index,array){
    return value%2==1;
  });//筛选出其中的奇数 ,方法二
  
  for(var j=0;j<oddFibs.length;j++){
    returnSum += oddFibs[j];
  }//求和
  
  return returnSum;  
}
```


  [1]: ./images/1481374517167.jpg "1481374517167.jpg"
  [2]: http://www.cnblogs.com/meteoric_cry/archive/2010/11/29/1891241.html
  [3]: https://github.com/FreeCodeCampChina/freecodecamp.cn/issues/19
  [4]: https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/Arithmetic_Operators#Remainder_%28.25%29
