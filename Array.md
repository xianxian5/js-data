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
