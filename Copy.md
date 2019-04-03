## JS的深拷贝和浅拷贝 

### 理解：深度拷贝针对的是复杂类型，不是基础数据类型，它的意思是拷贝完之后两组数据改变，相互没影响。

### JS的数据类型
1. 基础数据类型 ———— Number、String、Undefined、null、Boolean、Symbol
2. 引用数据类型 ———— object、array、function、date、regexp 等
3. 具体的判断方法 console.log(Object.prototype.toString.call("1").slice(8,-1)) //String

### 不同数据类型的存储方式不同
1. 基础数据类型 ———— 存储在内存中，名字和值都存在栈内存中，固定大小的内存
2. 引用数据类型 ———— 存储在内存中，但是名字和地址存在栈内存中，值存在堆内存中(function是js的一等对象)

### 实现深度拷贝

1. 递归实现深度拷贝
```
var obj = {
		name : "first",
		fn:function(){
			console.log("第一")	
		},
		cc:{
			a:1,
			b:2	
		},
		arr:[1,2,[3,4]]
	}
console.log(Object.prototype.toString.call("1").slice(8,-1)) //String

function copy(obj){
	var newobj = null;
	if(typeof(obj) == "object" && obj != null){
		
		newobj = (obj instanceof Array)?[]:{}
		
		for(var key in obj){
			
			if(typeof obj[key] !== "object"){
				newobj[key] = obj[key]	
			}else{
				newobj[key] = copy(obj[key])
			}	
		}	
		
	}else{
		newobj = obj
	}
	
	return newobj
}

var obj1 = copy(obj)
obj1.cc.a = 6
console.log(obj1); //{a:6,b:2}
console.log(obj);//{a:1,b:2}

```








