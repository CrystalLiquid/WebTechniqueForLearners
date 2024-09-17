## 基本语法
### 声明
```javascript
//注释：可变变量，不要使用var不要使用var不要使用var!!!
let a = ...;

//常量
const ba = "oh!"; //字符串
const bb = 30; //数字
const bc = true; //布尔
const bd = null;
const be = undefined;


//声明一个函数
function foo(arg){
	
}

const foo2 = ()=>{

}
```

### 条件判断和循环
```javascript
const a = "OK";
const b = "Not OK";
const c = 2;
const d = 3;
if(a===b){//严格比较，只允许相同类型 对立为：!==
	console.log(true);
}
if(a==b){//不检查类型 对立为：!=

}
if(a===b && c===d){//&& xx和xx同时成立

}
if(a===b || c===d){//|| xx或xx同时成立

}
//----------此外js还支持switch，与C语言格式完全相同--------------------
//----------------for和while也与C语言完全相同-------------------------
```
### 字符串拼接
使用"+"，您可以轻松拼接字符串
```javascript
const a = "OK";
const b = "Not OK";
const c = ```ff```; //多行字符串，同样可以拼接
console.log(b.length);//获取字符串长度
let d = b.substring(0,3);//获取子串 "Not"
d = d.toUpperCase() // 转换为大写 小写则：toLowerCase
let f = b.split(" ");//以某个字符为分割，取其他字符成为集合 ["Not","OK"]
console.log(a+b+c+"shit");

```
### 列表（写标题栏选择表单有时候会用）
```javascript
const nums = [1,2,3];
nums.push(4); // 在尾部加入新元素
nums.unshift(2);// 在头部添加元素
nums.pop() //就是pop back，删除最后一个元素
let c = new Array(1,2,3,4) //构造函数，不推荐用
nums.indexOf(1) // 获取 “1” 的索引值
```

### JSON相关
JS还允许您使用json作为对象，用作发送给另外一个网站的表单
```javascript
const json_array = [
{
	key:123,
	uu:null,
	xx:true,
	kk:"cc"
},"11",true
];
const json_object = {
events: {
        st: {
            description: null,
            id: 138586341,
            logo: null,
            name: "30th Anniversary Tour",
	        subTopicIds: [337184269, 337184283],
            subjectCode: null,
            subtitle: null,
            topicIds: [324846099, 107888604]
        }
    }
};
let str = json_object.events.st.id; //访问对象
let num = json_array[0].key;
```

## 函数执行时间控制(延时，异步)
www.bilibili.com/video/BV1cX4y1b7vc
```javascript
setTimeOut(()=>{

},time)//延迟执行

const p1 = new Promise((resolve,reject)=>{
	reject('失败的信息');
	resolve('任务1:成功得到的数据');
})//promise异步
p1.then(data=>{
	return new Promise((resolve,reject)=>{
		resolve('任务2：成功得到的数据')
	})
})
```

## 面向对象
### 注意事项
```javascript
//构造函数的函数返回基本类型 'xx' null true undefined 123 没有用，用数组，里面的基本类型也会消失
function fno(){
	return 0;
}
let kk = new fno();//console.log输出没有结果
//其次不需要new的class成员函数一律写成fn_name=(params...){};
//需要new则fn_name(params...){};
//如果new相当于复制多了一个变量存储函数，不会复制整个类
```
### 规范创建
#### 函数式创建
```javascript
//字面量创建
let o = {
	name:'Off',
	age:20
};//无法批量创建

//规范创建：工厂函数模式
function createobj(n,a){
	let obj={}
	obj.name = n;
	obj.age = a;
	return obj;
}
let o = createobj('Off',20);

//////////////////////////////////////////////
//构造函数创建
let k = new Object();
k.name = 'off';
k.age = 2;
//规范创建：工厂函数模式
function createobj(n,a){
	this.name = n;
	this.age = a;
//不要写return
}
let k = new createobj('off',2);//因此我们知道new构造函数也是普通函数，只有new才能构造
//以上都不推荐使用，因为并非每个人都喜欢函数式开发
```
#### 构造函数创建过程出现的的不合理性
![[nestfunc.PNG]]
这里函数的都是同一个效果，但是创建了两次，用了两个空间来存，因此不太合理
#### prototype：能够解决但是存在安全风险（不推荐）
[教程](https://www.bilibili.com/video/BV15K4y1M721)
#### 关于proto
每个new构造的对象都会有一个_proto_属性，只是不一定有prototype
![[proto.PNG]]
#### 面向对象
```javascript
class son extends father{//son继承father
	constructor(params...){//构造函数
		this.a = 123;
		init();
	}
//你还可以独立写一个启动器
	init(){
		this.set_b();
	}
	set_b(){
		const num = ...
		
	}
}
```