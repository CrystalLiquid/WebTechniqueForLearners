## 基本语法
### 声明
```javascript
//注释：可变变量
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
//此外js还支持switch，与C语言格式完全相同
//for和while也与C语言完全相同
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
## 面向对象
### 注意事项
```javascript
//构造函数的函数返回基本类型 'xx' null true undefined 123 没有用，用数组，里面的基本类型也会消失
function fno(){
	return 0;
}
let kk = new fno();//console.log输出没有结果
```
