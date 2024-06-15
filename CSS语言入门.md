CSS是一种界面设计语言
## 嵌入HTML
我们可以通过两种方式调用
#### 直接嵌入

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

#### 文件嵌入

#### src方式：
`<style type="text/css" src="@/..."></style>`
**src方式引入一般是局部作用域或者全局作用域
您可以在head处引入来使得整个html都能使用样式
或者变为`<style type="text/css" scoped src="@/..."></style>`变为局部作用域**
#### @import方式：
`<style type="text/css">@import"./..."</style>`
**@import只能是全局作用域，scope标签无法影响**
 
[更多嵌入方式详细见W3School](https://www.w3school.com.cn/css/css_shiyong.asp)
## 基础语法

### 选择器

#### 常用选择器                     

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


```
//选择多个元素
e1,e2 {
	attrib： ...
}
```


```
//父元素类型为e1的所有e2类型子元素
e1 > e2{
	...
}
```


| 选择器                                                                                                                       | 例子                    | 例子描述                                  |
| ------------------------------------------------------------------------------------------------------------------------- | --------------------- | ------------------------------------- |
| [`.class`](https://www.w3school.com.cn/cssref/selector_class.asp "CSS .class 选择器")                                        | .intro                | 选择 class="intro" 的所有元素。               |
| `.class1.class2`                                                                                                          | .name1.name2          | 选择 class 属性中同时有 name1 和 name2 的所有元素。  |
| `.class1 .class2`                                                                                                         | .name1 .name2         | 选择作为类名 name1 元素后代的所有类名 name2 元素。      |
| [`#id`](https://www.w3school.com.cn/cssref/selector_id.asp "CSS #id 选择器")                                                 | `#firstname`          | 选择 id="firstname" 的元素。                |
| [`*`](https://www.w3school.com.cn/cssref/selector_all.asp "CSS * 选择器")                                                    | *                     | 选择所有元素。                               |
| [`element`](https://www.w3school.com.cn/cssref/selector_element.asp "CSS element 选择器")                                    | p                     | 选择所有 `<p>` 元素。                        |
| [`element.class`](https://www.w3school.com.cn/cssref/selector_element_class.asp "CSS element.class 选择器")                  | p.intro               | 选择 class="intro" 的所有 `<p>` 元素。        |
| [`element,element`](https://www.w3school.com.cn/cssref/selector_element_comma.asp "CSS element,element 选择器")              | div, p                | 选择所有 `<div>` 元素和所有 `<p>` 元素。          |
| [`element element`](https://www.w3school.com.cn/cssref/selector_element_element.asp "CSS element element 选择器")            | div p                 | 选择 `<div>` 元素内的所有 `<p>` 元素。           |
| [`element > element`](https://www.w3school.com.cn/cssref/selector_element_gt.asp "CSS element>element 选择器")               | div > p               | 选择父元素是 `<div>` 的所有 `<p>` 元素。          |
| [`element_+_element`](https://www.w3school.com.cn/cssref/selector_element_plus.asp "CSS element+element 选择器")             | div + p               | 选择紧跟 `<div>` 元素的首个 `<p>` 元素。          |
| [`element1_~_element2`](https://www.w3school.com.cn/cssref/selector_gen_sibling.asp "CSS element1~element2 选择器")          | p ~ ul                | 选择前面有 `<p>` 元素的每个 `<ul>` 元素。          |
| [`[attribute]`](https://www.w3school.com.cn/cssref/selector_attribute.asp)                                                | [target]              | 选择带有 target 属性的所有元素。                  |
| [`[attribute=value]`](https://www.w3school.com.cn/cssref/selector_attribute_value.asp)                                    | [target=_blank]       | 选择带有 target="_blank" 属性的所有元素。         |
| [`[attribute~=value]`](https://www.w3school.com.cn/cssref/selector_attribute_value_contain.asp)                           | [title~=flower]       | 选择 title 属性包含单词 "flower" 的所有元素。       |
| [`[attribute\|=value]`](https://www.w3school.com.cn/cssref/selector_attribute_value_start.asp)                            | [lang\|=en]           | 选择 lang 属性值以 "en" 开头的所有元素。            |
| [`[attribute^=value]`](https://www.w3school.com.cn/cssref/selector_attr_begin.asp )                                       | a[href^="https"]      | 选择其 src 属性值以 "https" 开头的每个 `<a>` 元素。  |
| [`[attribute$=value]`](https://www.w3school.com.cn/cssref/selector_attr_end.asp)                                          | a[href$=".pdf"]       | 选择其 src 属性以 ".pdf" 结尾的所有 `<a>` 元素。    |
| [`[attribute*=value]`](https://www.w3school.com.cn/cssref/selector_attr_contain.asp)                                      | a[href*="w3school"]   | 选择其 href 属性值中包含 "abc" 子串的每个 `<a>` 元素。 |
| [`:active`](https://www.w3school.com.cn/cssref/selector_active.asp "CSS :active 选择器")                                     | a:active              | 选择活动链接。                               |
| [`::after`](https://www.w3school.com.cn/cssref/selector_after.asp "CSS ::after 选择器")                                      | p::after              | 在每个 `<p>` 的内容之后插入内容。                  |
| [`::before`](https://www.w3school.com.cn/cssref/selector_before.asp "CSS ::before 选择器")                                   | p::before             | 在每个 `<p>` 的内容之前插入内容。                  |
| [`:checked`](https://www.w3school.com.cn/cssref/selector_checked.asp "CSS :checked 选择器")                                  | input:checked         | 选择每个被选中的 `<input>` 元素。                |
| [`:default`](https://www.w3school.com.cn/cssref/selector_default.asp "CSS :default 选择器")                                  | input:default         | 选择默认的`<input>`元素                      |
| [`:disabled`](https://www.w3school.com.cn/cssref/selector_disabled.asp "CSS :disabled 选择器")                               | input:disabled        | 选择每个被禁用的元素。                           |
| [`:empty`](https://www.w3school.com.cn/cssref/selector_empty.asp)                                                         | p:empty               | 选择没有子元素的每个 `<p>` 元素（包括文本节点）。          |
| [`:enabled`](https://www.w3school.com.cn/cssref/selector_enabled.asp "CSS :enabled 选择器")                                  | input:enabled         | 选择每个启用的 `<input>` 元素。                 |
| [`:first-child`](https://www.w3school.com.cn/cssref/selector_first-child.asp "CSS :first-child 选择器")                      | p:first-child         | 选择属于父元素的第一个子元素的每个 `<p>` 元素。           |
| [`::first-letter`](https://www.w3school.com.cn/cssref/selector_first-letter.asp "CSS ::first-letter 选择器")                 | p::first-letter       | 选择每个 `<p>` 元素的首字母。                    |
| [`::first-line`](https://www.w3school.com.cn/cssref/selector_first-line.asp "CSS ::first-line 选择器")                       | p::first-line         | 选择每个 `<p>` 元素的首行。                     |
| [`:first-of-type`](https://www.w3school.com.cn/cssref/selector_first-of-type.asp "CSS :first-of-type 选择器")                | p:first-of-type       | 选择属于其父元素的首个 `<p>` 元素的每个 `<p>` 元素。     |
| [`:focus`](https://www.w3school.com.cn/cssref/selector_focus.asp "CSS :focus 选择器")                                        | input:focus           | 选择获得焦点的 input 元素。                     |
| [`:fullscreen`](https://www.w3school.com.cn/cssref/selector_fullscreen.asp "CSS :fullscreen 选择器")                         | :fullscreen           | 选择处于全屏模式的元素。                          |
| [`:hover`](https://www.w3school.com.cn/cssref/selector_hover.asp "CSS :hover 选择器")                                        | a:hover               | 选择鼠标指针位于其上的链接。                        |
| [`:in-range`](https://www.w3school.com.cn/cssref/selector_in-range.asp "CSS :in-range 选择器")                               | input:in-range        | 选择其值在指定范围内的 input 元素。                 |
| [`:indeterminate`](https://www.w3school.com.cn/cssref/selector_indeterminate.asp "CSS :indeterminate 选择器")                | input:indeterminate   | 选择处于不确定状态的 input 元素。                  |
| [`:invalid`](https://www.w3school.com.cn/cssref/selector_invalid.asp "CSS :invalid 选择器")                                  | input:invalid         | 选择具有无效值的所有 input 元素。                  |
| [`:lang(language)`](https://www.w3school.com.cn/cssref/selector_lang.asp "CSS :lang(language) 选择器")                       | p:lang(it)            | 选择 lang 属性等于 "it"（意大利）的每个 `<p>` 元素。   |
| [`:last-child`](https://www.w3school.com.cn/cssref/selector_last-child.asp "CSS :last-child 选择器")                         | p:last-child          | 选择属于其父元素最后一个子元素每个 `<p>` 元素。           |
| [`:last-of-type`](https://www.w3school.com.cn/cssref/selector_last-of-type.asp "CSS :last-of-type 选择器")                   | p:last-of-type        | 选择属于其父元素的最后 `<p>` 元素的每个 `<p>` 元素。     |
| [`:link`](https://www.w3school.com.cn/cssref/selector_link.asp "CSS :link 选择器")                                           | a:link                | 选择所有未访问过的链接。                          |
| [`:not(selector)`](https://www.w3school.com.cn/cssref/selector_not.asp "CSS :not(selector) 选择器")                          | :not(p)               | 选择非 `<p>` 元素的每个元素。                    |
| [`:nth-child(n)`](https://www.w3school.com.cn/cssref/selector_nth-child.asp "CSS :nth-child(n) 选择器")                      | p:nth-child(2)        | 选择属于其父元素的第二个子元素的每个 `<p>` 元素。          |
| [`:nth-last-child(n)`](https://www.w3school.com.cn/cssref/selector_nth-last-child.asp "CSS :nth-last-child(n) 选择器")       | p:nth-last-child(2)   | 同上，从最后一个子元素开始计数。                      |
| [`:nth-of-type(n)`](https://www.w3school.com.cn/cssref/selector_nth-of-type.asp "CSS :nth-of-type(n) 选择器")                | p:nth-of-type(2)      | 选择属于其父元素第二个 `<p>` 元素的每个 `<p>` 元素。     |
| [`:nth-last-of-type(n)`](https://www.w3school.com.cn/cssref/selector_nth-last-of-type.asp "CSS :nth-last-of-type(n) 选择器") | p:nth-last-of-type(2) | 同上，但是从最后一个子元素开始计数。                    |
| [`:only-of-type`](https://www.w3school.com.cn/cssref/selector_only-of-type.asp "CSS :only-of-type 选择器")                   | p:only-of-type        | 选择属于其父元素唯一的 `<p>` 元素的每个 `<p>` 元素。     |
| [`:only-child`](https://www.w3school.com.cn/cssref/selector_only-child.asp "CSS :only-child 选择器")                         | p:only-child          | 选择属于其父元素的唯一子元素的每个 `<p>` 元素。           |
| [`:optional`](https://www.w3school.com.cn/cssref/selector_optional.asp "CSS :optional 选择器")                               | input:optional        | 选择不带 "required" 属性的 input 元素。         |
| [`:out-of-range`](https://www.w3school.com.cn/cssref/selector_out-of-range.asp "CSS :out-of-range 选择器")                   | input:out-of-range    | 选择值超出指定范围的 input 元素。                  |
| [`::placeholder`](https://www.w3school.com.cn/cssref/selector_placeholder.asp "CSS ::placeholder 选择器")                    | input::placeholder    | 选择已规定 "placeholder" 属性的 input 元素。     |
| [`:read-only`](https://www.w3school.com.cn/cssref/selector_read-only.asp "CSS :read-only 选择器")                            | input:read-only       | 选择已规定 "readonly" 属性的 input 元素。        |
| [`:read-write`](https://www.w3school.com.cn/cssref/selector_read-write.asp "CSS :read-write 选择器")                         | input:read-write      | 选择未规定 "readonly" 属性的 input 元素。        |
| [`:required`](https://www.w3school.com.cn/cssref/selector_required.asp "CSS :required 选择器")                               | input:required        | 选择已规定 "required" 属性的 input 元素。        |
| [`:root`](https://www.w3school.com.cn/cssref/selector_root.asp "CSS :root 选择器")                                           | :root                 | 选择文档的根元素。                             |
| [`::selection`](https://www.w3school.com.cn/cssref/selector_selection.asp "CSS ::selection 选择器")                          | ::selection           | 选择用户已选取的元素部分。                         |
| [`:target`](https://www.w3school.com.cn/cssref/selector_target.asp "CSS :target 选择器")                                     | `#news`:target        | 选择当前活动的 `#news` 元素。                   |
| [`:valid`](https://www.w3school.com.cn/cssref/selector_valid.asp "CSS :valid 选择器")                                        | input:valid           | 选择带有有效值的所有 input 元素。                  |
| [`:visited`](https://www.w3school.com.cn/cssref/selector_visited.asp "CSS :visited 选择器")                                  | a:visited             | 选择所有已访问的链接。                           |

--- 

### Attribute属性分类


---

#### 颜色
##### 常用颜色属性
###### background-color
###### box-shadow
###### text-shadow
###### opacity
###### outline-color
###### border-color

| 属性                                                                                                                |
| ----------------------------------------------------------------------------------------------------------------- |
| [background-color](https://www.w3school.com.cn/cssref/pr_background-color.asp "CSS background-color 属性")          |
| [border-bottom-color](https://www.w3school.com.cn/cssref/pr_border-bottom-color.asp "CSS border-bottom-color 属性") |
| [border-color](https://www.w3school.com.cn/cssref/pr_border-color.asp "CSS border-color 属性")                      |
| [border-left-color](https://www.w3school.com.cn/cssref/pr_border-left-color.asp "CSS border-left-color 属性")       |
| [border-right-color](https://www.w3school.com.cn/cssref/pr_border-right-color.asp "CSS border-right-color 属性")    |
| [border-top-color](https://www.w3school.com.cn/cssref/pr_border-top-color.asp "CSS border-top-color 属性")          |
| [box-shadow](https://www.w3school.com.cn/cssref/pr_box-shadow.asp "CSS box-shadow 属性")                            |
| [color](https://www.w3school.com.cn/cssref/pr_text_color.asp "CSS color 属性")                                      |
| [column-rule-color](https://www.w3school.com.cn/cssref/pr_column-rule-color.asp "CSS column-rule-color 属性")       |
| [opacity](https://www.w3school.com.cn/cssref/pr_opacity.asp "CSS opacity 属性")                                     |
| [outline](https://www.w3school.com.cn/cssref/pr_outline.asp "CSS outline 属性")                                     |
| [outline-color](https://www.w3school.com.cn/cssref/pr_outline-color.asp "CSS outline-color 属性")                   |
| [text-shadow](https://www.w3school.com.cn/cssref/pr_text-shadow.asp "CSS text-shadow 属性")                         |
| [visibility](https://www.w3school.com.cn/cssref/pr_class_visibility.asp "CSS visibility 属性")                      |

---

#### 布局



#### 定位




#### 文本特有
