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
24. 扩展运算符

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
 
#### slice（start,end）
1. 不改变原来数组
2. 返回一个新的数组包含从start开始，end结束（不包含）
3. end是可以选值，如果为空，默认到被切数组的末尾。
4. start可以是负数，就是从末尾开始计算，如果是-1就指的最后一位
```
var arr1 = ["ab", "aa","cc"];
console.log(arr1.slice(0,2))//["ab", "aa"]
console.log(arr1) //["ab", "aa","cc"]

console.log(arr1.slice(0))//["ab", "aa","cc"]
console.log(arr1.slice(-1))//["cc"]
```

#### splice（index,howmany,item1,...,itemX）
1. 改变原来数组
2. 返回的是被除数的项目
3. index、howmany 必填
```
var arr = ["aa","bb","cc"]
var arr1 = arr.splice(0,2,"cc","dd")
console.log(arr) //["cc","dd","cc"]
console.log(arr1) //["aa","bb"]
```

#### indexOf（searchvalue,start）和 lastindexOf（searchvalue,start）
1. searchvalue必填
2. indexOf 中start 可选，0到数组长度之间的值从数组前面开始计算，lastindexOf中start可选，从数组后面开始计算。 
3. 不改变原来数组
4. indexOf 返回第一次出现的下标
5. lastindexOf 返回最后一次出现的下标
6. 不出现返回-1
```
var arr = ["aa","bb","cc","cc"]
var nn = arr.indexOf("cc",1)
console.log(nn) //2
console.log(arr) //["aa","bb","cc","cc"]
var nn1 = arr.lastIndexOf("cc",4)
console.log(nn1) //3

```

#### foreach（(n,i,arr)=>{}）
1. 对数组进行遍历循环，执行函数
2. 没有返回值
3. n每项的值，i下标，arr循环的数组
```
 var arr = ["aa","bb","cc"]
 arr.forEach((n,i,a) => {
	console.log(n,a)
 })
```

#### map()
1. 有返回值
2. 循环执行数组里的每一想
```
arrEvent: function () {
 var _this = this
 var arr = [1,2,3]
 var arr1 = arr.map((n) => {
   return n*n
 })
 console.log(arr) //[1,2,3]
 console.log(arr1) //[1,4,9]
}
```

#### every()
1.  检查所有元素，都正确返回true，有一个错误则返回false，且不再继续执行
```
arrEvent: function () {
var arr = [1, 2, 3, 4, 5];
var arr2 = arr.every((n) => {
return n<3
})
console.log(arr2) //false
}
```

#### some()
1.  检查所有元素，有一项正确，则返回true，否则返回false
```
arrEvent: function () {
var arr = [1, 2, 3, 4, 5];
var arr2 = arr.some((n) => {
return n<3
})
console.log(arr2) //true
}
```

#### fliter（）
1. 过滤作用，返回数组
```
arrEvent: function () {
var lstVssConfigParaInfo = [{
"strVssConfigParaName": "FILE_SERVICE_IP",
"strVssConfigParaValue": "192.168.1.66"
},
{
  "strVssConfigParaName": "FILE_SERVICE_PORT",
  "strVssConfigParaValue": "80"
},
{
  "strVssConfigParaName": "FILE_SERVICE_PORT",
  "strVssConfigParaValue": "8080"
}]

var arr = lstVssConfigParaInfo.filter(n => {return n.strVssConfigParaName == "FILE_SERVICE_PORT"})

console.log(arr)
/*[{
      "strVssConfigParaName": "FILE_SERVICE_PORT",
	"strVssConfigParaValue": "80"
    },
{
  "strVssConfigParaName": "FILE_SERVICE_PORT",
  "strVssConfigParaValue": "8080"
}]*/
}
```

#### find（）
1. 过滤作用，返回单条

```
arrEvent: function () {
var lstVssConfigParaInfo = [{
"strVssConfigParaName": "FILE_SERVICE_IP",
"strVssConfigParaValue": "192.168.1.66"
},
{
  "strVssConfigParaName": "FILE_SERVICE_PORT",
  "strVssConfigParaValue": "80"
},
{
  "strVssConfigParaName": "FILE_SERVICE_PORT",
  "strVssConfigParaValue": "8080"
}]

var arr = lstVssConfigParaInfo.find(n => {return n.strVssConfigParaName == "FILE_SERVICE_PORT"})


}
```

#### reduce（）//arr.reduce(function(total,currentValue, index,arr){},[initialValue])
1. total  计算结束后返回的值
2. currentValue 设置初始化值，如果有，那么reduce执行的次数就是arr.length，如果没有则执行的次数为arr.length-1
3. index下标
4. arr reduce（）执行的数组
5. initialValue 首位计算的值
用法一：求和
```
arrEvent: function () {
	var arr = [1,2,3,4,5]
	var all = arr.reduce((t,c,i,arrn) => {
	console.log(t,c,i,arrn)
	//2 1 0 (5) [1, 2, 3, 4, 5]
	//3 2 1 (5) [1, 2, 3, 4, 5]
	// 5 3 2 (5) [1, 2, 3, 4, 5]
	//8 4 3 (5) [1, 2, 3, 4, 5]
	// 12 5 4 (5) [1, 2, 3, 4, 5]
	return t+c
},2)
console.log(all) //17
}
```
用法二：求积
```
let arr = [1,2,3,4,5]
arr.reduce（（p,c）=> p*c）
```
用法三：去重
```
arrEvent: function () {
let arr = ["aa","bb","ccc","aa","dd"]

let newarr = arr.reduce((p,c) => {
console.log(p,c)
console.log(p.indexOf(c))
if( p.indexOf(c) < 0 ){
  return p.concat(c)
}else{
  return p
}
},[])
console.log(newarr)  //["aa", "bb", "ccc", "dd"]
}

```

#### 扩展运算符 -- 将数组转换成用逗号分隔的参数序列
```
arrEvent:function(){
let arr = [1,2,5,6]
console.log(...arr) //1 2 5 6
console.log(arr) //[1,2,5,6]
}
```

#### Array.from() ———— 将类素组和可遍历的对象转换成真的数组
```
1. 将类素组转换成数组
arrEvent:function(){
let likeArray = {
'0': 'a',
'1': 'b',
'2': 'c',
length:3
}
let newArr1 = Array.from(likeArray)
console.log(newArr1) //["a", "b", "c"]
let newArr2 = [].slice.apply(likeArray)
console.log(newArr2) //["a", "b", "c"]
    }
    
 2. 可以接收两个参数
arrEvent:function(){
console.log(Array.from([1,2,3], (x)=> x*x)) // [1, 4, 9]
}
```
#### Array.of() ———— 将一组值转换成数组
```
arrEvent:function(){
console.log(Array.of(0))//[0]
function arr(){
return [].slice.apply(arguments)
}

var mm = arr(0)
console.log(mm)  //[0]
}
```

#### copywidth(target,start,end)————指定位置的成员复制到其他位置（会覆盖原有成员），然后返回当前数组
1. -target（必需）：从该位置开始替换数据。如果为负值，表示倒数。
2. -start（可选）：从该位置开始读取数据，默认为 0。如果为负值，表示倒数。
3. -end（可选）：到该位置前停止读取数据，默认等于数组长度。如果为负值，表示倒数。
```
arrEvent:function(){
let arr = [1,2,3,4,5]
let newarr = arr.copyWithin(0,3,4)
console.log(newarr)
console.log(arr)//[4,2,3,4,5]
}
```



 
 
 
 

二、 从object对象继承过来的方法
