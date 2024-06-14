CSS是一种界面设计语言
<b><div align='center' ><font size='5'>嵌入HTML</font></div></b>
我们可以通过两种方式调用
<b><div align='center' ><font size='5'>直接嵌入</font></div></b>

```
<!DOCTYPE html>
<html lang="zh-cn">
    <head>
        <style type="text/css">
            html,body{
                width: 100%;
                height: 100%;
                font-family: monospace;
            }
        </style>
    </head>
    <body>
    </body>
</html>
```

<b><div align='center' ><font size='5'>文件嵌入</font></div></b>

#### src方式：`<style type="text/css" src="@/..."></style>`
**src方式引入一般是局部作用域或者全局作用域
您可以在head处引入来使得整个html都能使用样式
或者变为`<style type="text/css" scoped src="@/..."></style>`变为局部作用域**
#### @import方式：`<style type="text/css">@import"./..."</style>`
**@import只能是全局作用域，scope标签无法影响**
 
[更多嵌入方式详细见W3School](https://www.w3school.com.cn/css/css_shiyong.asp)
<div align='center' >
	<font size='5'>
		<b>基础语法</b>
	</font>
</div>

<b><div align='center' ><font size='5'>选择器</font></div></b>


```
//类型选择器、class选择器<div class="classname"></div>
.classname {
	attrib: ...
}
```


```
//id选择器 <div id="idname"></div>
#idname {
	attrib: ...
}
```


```
//特定标签类型选择器 <p class="x1"></p>  <p class="x3"></p>
p.x3{
	attrib: ...
}
//只有p标签的class=“x3”被选中
```



```
//页面上全部元素都被选择
* {
	attrib： ...
}
```
