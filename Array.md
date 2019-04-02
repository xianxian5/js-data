## 数组
### 数组创建
```
var arr = new Array()|| var arr = []
```
### 数组方法集合
一、 数组原型方法
1. join（）
2. push（）和 pop（）
3. shift（）和 unshift（）
4. reverse（）
5. sort（）
6. concat（）
7. slice（）
8. splice（）
9. indexof（）和lastIndexof（）
10. foreach（）
11. map（）
12. filter（）
13. every（）
14. some（）
15. reduce（）和 reduceRight（）
16. from（）
17. of（）
18. copyWidth（）
19. find（）和 findIndex（）
20. fill（）
21. entries（),keys()和valuse（）
22. includes（）
23. flat（）和flatMap（）

#### join（）
```
1.数组转换成字符串，用join中的符号隔开，不改变原来的数组，去掉用正则法replace不改变原来字符串

var arr = [1,2,3]
var nn = arr.join("-");
console.log(arr) //[1,2,3]
console.log(nn)//1-2-3
var mm = nn.replace(/-/g,'') 
console.log(nn) //1-2-3
console.log(mm) //123

2.可以实现重复字符串

function repeatString(str,n){
 var mm = new Array(n+1)
 return mm.join(str)	
}
console.log(repeatString("abc",3))  //abcabcabc
```
#### push（）和 pop（）
1. push（）接收任意数量的参数添加到数组结尾，返回新数组的长度
2. pop（）删除末尾的最后一位，返回删除的值
3. 两个函数都改变原数组
```
var arr = ["a","b","c"]
var mm = arr.push("d","e")
console.log(mm) //5
console.log(arr) //["a","b","c","d","e"]
var cc = arr.pop()
console.log(cc) //e
console.log(arr) //["a","b","c","d"]
```
 #### shift（）和 unshift（）
 1. shift（） 删除第一项，返回删除元素的值，如果是空数组，返回underfined
 2. unshift（） 添加到数组头部，返回新数组长度
 ```
 var arr = ["a","b","c"]
 var mm = arr.unshift("d","e")
 console.log(mm) //5
 console.log(arr) //["d","e","a","b","c"]
 var cc = arr.shift()
 console.log(cc) //d
 console.log(arr) //["e","a","b","c"]
 
 ```
 #### reverse()
 1. 倒叙
 2. 改变原来数组
 ```
 var arr1 = ["ab", "aa", "bc", "ba"];
 console.log(arr1.reverse()); // ["ba", "bc", "aa", "ab"]
 console.log(arr1)//["ba", "bc", "aa", "ab"]
 ```
 #### sort()
 1. 改变原来数组
 2. 在排序时，sort()方法会调用每个数组项的 toString()转型方法，然后比较得到的字符串，以确定如何排序。所以数值排序时候有问题。
 ```
 var arr1 = ["ab", "aa", "bc", "ba"];
 console.log(arr1.sort()); // ["aa", "ab", "ba", "bc"]
 console.log(arr1);// ["aa", "ab", "ba", "bc"]
 var aar2 = [1,2,3,10]
 console.log(aar2.sort()); // [1,10,2,3]
 ```
 3.解决数值数值排序
 ```
 var arr1 = ["ab", "aa", "bc", "ba"];
 console.log(arr1.sort()); // ["aa", "ab", "ba", "bc"]
 console.log(arr1);// ["aa", "ab", "ba", "bc"]
 var aar2 = [1,3,2,1,10]
 console.log(aar2.sort()); // [1,1,10,2,3]

 function compare(v1,v2){
	if(v1<v2){
		return -1;
	}else{
		return 1	
	}
 }
 console.log(aar2.sort(compare))//[1,1,2,3,10]
 ```
 
 #### concat（）
 1. 将参数添加到原数组中,返回新的数组
 2. 不修改原来数组
 ```
 var arr1 = ["ab", "aa", "bc", "ba"];
 var arr2 = ['cc']
 console.log(arr1.concat(arr2))//["ab", "aa", "bc", "ba",'cc']
 console.log(arr1)//["ab", "aa", "bc", "ba"]

 var newarr = arr1.concat({'name':'marry'}) 
 console.log(newarr) //["ab", "aa", "bc", "ba",Object]
 console.log(newarr[4]) //{'name':'marry'}
 
 ```
 3. 与push的区别,第一，返回的不同，第二，concat不改变原数组，push改变。第三，添加数组时concat会把值取出来添加到数组后面，push不会。第四， 利用apply可实现和concat相同效果
 ```
 var arr1 = ["ab", "aa"];

 console.log(arr1.concat(2,3)) //["ab", "aa",2,3]
 console.log(arr1)//["ab", "aa"]

 console.log(arr1.push(2,3)) //4
 console.log(arr1)//["ab", "aa",2,3]

 var arr2 = ["ab", "aa"];
 console.log(arr2.concat([2,[3,4]])) //["ab", "aa",2,[3,4]]
 console.log(arr2.push([2,[3,4]])) //3
 console.log(arr2)//["ab", "aa",[2,[3,4]]]
 
 var arr3 = ["ab", "aa"];
 arr3.push.apply(arr3,[2,[3,4]]);
 console.log(arr3.length) //4
 console.log(arr3) //["ab", "aa",2,[3,4]] 
 ```
 
 
 
 

二、 从object对象继承过来的方法




##  find,filter
```
<!DOCTYPE html>
<html>
<head>
</head>
<body>
    <script>
        var lstVssConfigParaInfo = [{
            "strVssConfigParaName": "FILE_SERVICE_IP",
            "strVssConfigParaValue": "192.168.1.66"
          },
          {
            "strVssConfigParaName": "FILE_SERVICE_PORT",
            "strVssConfigParaValue": "80"
          }]

          var nubip = lstVssConfigParaInfo.find(nub => nub.strVssConfigParaName == "FILE_SERVICE_IP");
          console.log(nubip); //获取的是一条数据

          var nubport = lstVssConfigParaInfo.filter(nub => nub.strVssConfigParaName == "FILE_SERVICE_PORT");
          console.log(nubport); //获取的是一个数组
    </script>
</body>
</html>
```
