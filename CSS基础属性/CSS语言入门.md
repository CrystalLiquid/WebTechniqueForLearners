CSS是一种界面设计语言
MDN官方网站在学习查API的时候是必须随时开着的！否则，查使用案例的时候就要大海捞针
主要看Properties
https://developer.mozilla.org/zh-CN/docs/Web/CSS/
## 嵌入HTML
我们可以通过两种方式调用
#### 直接嵌入

```HTML
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

```CSS
//类型选择器、class选择器<div class="classname"></div>
.classname {
	attrib: ...
}
```


```CSS
//id选择器 <div id="idname"></div>
#idname {
	attrib: ...
}
```


```CSS
//特定标签类型选择器 <p class="x1"></p>  <p class="x3"></p>
p.x3{
	attrib: ...
}
//只有p标签的class=“x3”被选中
```



```CSS
//页面上全部元素都被选择
* {
	attrib： ...
}
```


```CSS
//选择多个元素
e1,e2 {
	attrib： ...
}
```


```CSS
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

#### 颜色
##### 常用颜色属性
###### background-color
###### box-shadow
###### text-shadow
###### opacity
###### outline-color
###### border-color

| 属性                                                                                                                        |        |
| ------------------------------------------------------------------------------------------------------------------------- | ------ |
| [`background-color`](https://www.w3school.com.cn/cssref/pr_background-color.asp "CSS background-color 属性")                | 背景颜色   |
| [`box-shadow`](https://www.w3school.com.cn/cssref/pr_box-shadow.asp "CSS box-shadow 属性")                                  | 盒子阴影   |
| [`color`](https://www.w3school.com.cn/cssref/pr_text_color.asp "CSS color 属性")                                            | 内容字体颜色 |
| [`column-rule-color`](https://www.w3school.com.cn/cssref/pr_column-rule-color.asp "CSS column-rule-color 属性")             |        |
| [`opacity`](https://www.w3school.com.cn/cssref/pr_opacity.asp "CSS opacity 属性")                                           | 透明度    |
| [`text-shadow`](https://www.w3school.com.cn/cssref/pr_text-shadow.asp "CSS text-shadow 属性")                               | 文字阴影   |
| [`visibility`](https://www.w3school.com.cn/cssref/pr_class_visibility.asp "CSS visibility 属性")                            | 可见性    |
| [`text-decoration-color`](https://www.w3school.com.cn/cssref/pr_text-decoration-color.asp "CSS text-decoration-color 属性") |        |
|                                                                                                                           |        |
关于text-decoration-color：
```
/* <color> values */
text-decoration-color: currentColor;
text-decoration-color: red;
text-decoration-color: #00ff00;
text-decoration-color: rgba(255, 128, 128, 0.5);
text-decoration-color: transparent;

/* Global values */
text-decoration-color: inherit;
text-decoration-color: initial;
text-decoration-color: unset;
```

---
##### Outline描边轮廓线属性

| [`outline`](https://www.w3school.com.cn/cssref/pr_outline.asp "CSS outline 属性")                   |
| ------------------------------------------------------------------------------------------------- |
| [`outline-color`](https://www.w3school.com.cn/cssref/pr_outline-color.asp "CSS outline-color 属性") |


---

##### Filter属性
**`filter`** 属性将模糊或颜色偏移等图形效果应用于元素。滤镜通常用于调整**图像、背景和边框**的渲染
```
/* <filter-function> 值 */
filter: blur(5px);
filter: brightness(0.4);
filter: contrast(200%);
filter: drop-shadow(16px 16px 20px blue);
filter: grayscale(50%);
filter: hue-rotate(90deg);
filter: invert(75%);
filter: opacity(25%);
filter: saturate(30%);
filter: sepia(60%);

/* URL */
filter: url("filters.svg#filter-id");

/* 多个滤镜 */
filter: contrast(175%) brightness(3%);
filter: drop-shadow(3px 3px red) sepia(100%) drop-shadow(-3px -3px blue);

/* 不使用滤镜 */
filter: none;
```


---

#### 布局
非常推荐[CodingStartup起码课](https://space.bilibili.com/451368848)的视频，因为他会分开讲的特别清楚，但是内容又是同时呈现，使得思绪不容易断开（  power of timelined logus（bushi  ）

#### Box属性
##### 基本定型属性
**数字+单位**

| [`height`](https://www.w3school.com.cn/cssref/pr_dim_height.asp "CSS height 属性") | 高度     |
| -------------------------------------------------------------------------------- | ------ |
| [`width`](https://www.w3school.com.cn/cssref/pr_dim_width.asp "CSS width 属性")    | **宽度** |

##### 基本定位属性
###### 基本位置属性

| [`top`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/top)                 | **`top`**[样式](https://developer.mozilla.org/zh-CN/docs/Web/CSS)属性定义了定位元素的上外边距边界与其包含块上边界之间的偏移，非定位元素设置此属性无效   |
| ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------- |
| `buttom`                                                                      | **`bottom`[样式](https://developer.mozilla.org/zh-CN/docs/Web/CSS)属性定义了定位元素下外边距边界与其包含块下边界之间的偏移，非定位元素设置此属性无效** |
| [`left`](https://www.w3school.com.cn/cssref/pr_pos_left.asp "CSS left 属性")    | **`left`属性定义了定位元素的左外边距边界与其包含块左边界之间的偏移，非定位元素设置此属性无效。**                                                       |
| [`right`](https://www.w3school.com.cn/cssref/pr_pos_right.asp "CSS right 属性") | 同理                                                                                                          |
###### 高级旋转位置属性
| **transform**                                                                           |                                                                                                                                                                                                                                                                                          |
| --------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [`transform`](https://www.w3school.com.cn/cssref/pr_transform.asp "CSS transform 属性")   | **`transform`** 属性允许你旋转、缩放、倾斜或平移给定元素。这是通过修改 CSS [视觉格式化模型](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Visual_formatting_model)的坐标空间实现的                                                                                                                                              |
| [`transform-origin`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/transform-origin) | **`transform-origin`** CSS 属性让你更改一个元素变形的原点。                                                                                                                                                                                                                                              |
| `transform-style`                                                                       | **`transform-style`** 设置元素的子元素是位于 3D 空间中还是平面中。如果选择平面，元素的子元素将不会有 3D 的遮挡关系。<br><br>由于这个属性不会被继承，因此必须为元素的所有非叶子子元素设置它。<br>`/* Keyword values */`<br>`transform-style: flat;`<br>`transform-style: preserve-3d;`<br>                                                                           |
| `transform-box`                                                                         | **`transform-box`** 属性定义了与 [`transform`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/transform)、[`transform-origin`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/transform-origin) 这两个属性有关联的布局框。详细建议去看[MDN原网址](https://developer.mozilla.org/zh-CN/docs/Web/CSS/transform-box) |
```
/* 关键字值 */
transform: none;

/* 函数值 */
transform: matrix(1, 2, 3, 4, 5, 6);
transform: matrix3d(1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1, 0, 0, 0, 0, 1);
transform: perspective(17px);
transform: rotate(0.5turn);
transform: rotate3d(1, 2, 3, 10deg);
transform: rotateX(10deg);
transform: rotateY(10deg);
transform: rotateZ(10deg);
transform: translate(12px, 50%);
transform: translate3d(12px, 50%, 3em);
transform: translateX(2em);
transform: translateY(3in);
transform: translateZ(2px);
transform: scale(2, 0.5);
transform: scale3d(2.5, 1.2, 0.3);
transform: scaleX(2);
transform: scaleY(0.5);
transform: scaleZ(0.3);
transform: skew(30deg, 20deg);
transform: skewX(30deg);
transform: skewY(1.07rad);

/* 多个函数值 */
transform: translateX(10px) rotate(10deg) translateY(5px);
transform: perspective(500px) translate(10px, 0, 20px) rotateY(3deg);

/* 全局值 */
transform: inherit;
transform: initial;
transform: revert;
transform: revert-layer;
transform: unset;
```

---

##### Border属性介绍（radius常用）

| [`border`](https://www.w3school.com.cn/cssref/pr_border.asp "CSS border 属性")                                                             | 设置边框线，可以以`n单位 线类型 颜色`的格式设置 |
| ---------------------------------------------------------------------------------------------------------------------------------------- | -------------------------- |
|                                                                                                                                          |                            |
| [`border-bottom-left-radius`](https://www.w3school.com.cn/cssref/pr_border-bottom-left-radius.asp "CSS border-bottom-left-radius 属性")    | 设置边框线圆角，左下                 |
| [`border-bottom-right-radius`](https://www.w3school.com.cn/cssref/pr_border-bottom-right-radius.asp "CSS border-bottom-right-radius 属性") | 设置边框线圆角，右下                 |
| [`border-top-left-radius`](https://www.w3school.com.cn/cssref/pr_border-top-left-radius.asp "CSS border-top-left-radius 属性")             | 设置边框线圆角，左上                 |
| [`border-top-right-radius`](https://www.w3school.com.cn/cssref/pr_border-top-right-radius.asp "CSS border-top-right-radius 属性")          |                            |
| ...（*-radius）                                                                                                                            | 设置边框线圆角...                 |
|                                                                                                                                          |                            |
| [`border-top`](https://www.w3school.com.cn/cssref/pr_border-top.asp "CSS border-top 属性")                                                 | 细分每个方向的框线属性                |
| [`border-bottom`](https://www.w3school.com.cn/cssref/pr_border-bottom.asp "CSS border-bottom 属性")                                        |                            |
| [`border-left`](https://www.w3school.com.cn/cssref/pr_border-left.asp "CSS border-left 属性")                                              |                            |
| [`border-right`](https://www.w3school.com.cn/cssref/pr_border-right.asp "CSS border-right 属性")                                           |                            |
|                                                                                                                                          |                            |
| [`border-top-width`](https://www.w3school.com.cn/cssref/pr_border-top-width.asp "CSS border-top-width 属性")                               | 细分调节每个框线的粗细                |
| [`border-left-width`](https://www.w3school.com.cn/cssref/pr_border-left-width.asp "CSS border-left-width 属性")                            |                            |
| [`border-right-width`](https://www.w3school.com.cn/cssref/pr_border-right-width.asp "CSS border-right-width 属性")                         |                            |
| [`border-spacing`](https://www.w3school.com.cn/cssref/pr_border-spacing.asp "CSS border-spacing 属性")                                     |                            |
| [`border-bottom-width`](https://www.w3school.com.cn/cssref/pr_border-bottom-width.asp "CSS border-bottom-width 属性")                      |                            |
|                                                                                                                                          |                            |
| [`border-color`](https://www.w3school.com.cn/cssref/pr_border-color.asp "CSS border-color 属性")                                           | 设置框线全部颜色                   |
| [`border-bottom-color`](https://www.w3school.com.cn/cssref/pr_border-bottom-color.asp "CSS border-bottom-color 属性")                      | 上边缘颜色，你必须设置框线才会出现          |
| [`border-left-color`](https://www.w3school.com.cn/cssref/pr_border-left-color.asp "CSS border-left-color 属性")                            | 根据意思理解                     |
| [`border-right-color`](https://www.w3school.com.cn/cssref/pr_border-right-color.asp "CSS border-right-color 属性")                         |                            |
| [`border-top-color`](https://www.w3school.com.cn/cssref/pr_border-top-color.asp "CSS border-top-color 属性")                               |                            |


---

###### 描边线属性
注意：与border不同outline 不占据空间，绘制于元素内容周围

| **描边线属性**                                                                                            |                                            |
| ---------------------------------------------------------------------------------------------------- | ------------------------------------------ |
| [`outline`](https://www.w3school.com.cn/cssref/pr_outline.asp "CSS outline 属性")                      | solid    /    dash    /  thick + `[color]` |
| [`outline-color`](https://www.w3school.com.cn/cssref/pr_outline-color.asp "CSS outline-color 属性")    |                                            |
| [`outline-offset`](https://www.w3school.com.cn/cssref/pr_outline-offset.asp "CSS outline-offset 属性") |                                            |
| [`outline-width`](https://www.w3school.com.cn/cssref/pr_outline-width.asp "CSS outline-width 属性")    |                                            |
```
/* 样式 */
outline: solid;

/* 颜色 | 样式 */
outline: #f66 dashed;

/* 样式 | 宽度 */
outline: inset thick;

/* 颜色 | 样式 | 宽度 */
outline: green solid 3px;

/* 全局值 */
outline: inherit;
outline: initial;
outline: unset;
```

---


| 所有属性                                                                                                   | **解释** |     |
| ------------------------------------------------------------------------------------------------------ | ------ | --- |
|                                                                                                        |        |     |
|                                                                                                        |        |     |
|                                                                                                        |        |     |
|                                                                                                        |        |     |
|                                                                                                        |        |     |
|                                                                                                        |        |     |
|                                                                                                        |        |     |
|                                                                                                        |        |     |
|                                                                                                        |        |     |
| [vertical-align](https://www.w3school.com.cn/cssref/pr_pos_vertical-align.asp "CSS vertical-align 属性") |        |     |
| [visibility](https://www.w3school.com.cn/cssref/pr_class_visibility.asp "CSS visibility 属性")           |        |     |
|                                                                                                        |        |     |
|                                                                                                        |        |     |
|                                                                                                        |        |     |
|                                                                                                        |        |     |

---
##### Order属性

| [初始值](https://developer.mozilla.org/zh-CN/docs/Web/CSS/initial_value)            | `0`                                                                                                                                                                                                                                                                                                         |
| -------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 适用元素                                                                             | Flex items, grid items, and absolutely-positioned flex and grid container children                                                                                                                                                                                                                          |
| [是否是继承属性](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Inheritance)          | 否                                                                                                                                                                                                                                                                                                           |
| [计算值](https://developer.mozilla.org/zh-CN/docs/Web/CSS/computed_value)           | as specified                                                                                                                                                                                                                                                                                                |
| [动画类型](https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_animated_properties) | an [integer](https://developer.mozilla.org/en-US/docs/Web/CSS/integer#interpolation "Values of the <integer> CSS data type are interpolated via integer discrete steps. The calculation is done as if they were real, floating-point numbers and the discrete value is obtained using the floor function.") |

| **order属性**                                                               |                                                                                                     |
| ------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- |
| [`order`](https://www.w3school.com.cn/cssref/pr_order.asp "CSS order 属性") | **`order`** 属性规定了弹性容器中的可伸缩项目在布局时的顺序。元素按照 `order` 属性的值的增序进行布局。拥有相同 `order` 属性值的元素按照它们在源代码中出现的顺序进行布局。 |
[MDN页面解释](https://developer.mozilla.org/zh-CN/docs/Web/CSS/order)

---

##### Perspective三维元素透视属性
| **perspective属性**                                                                                                |                                                                                                                             |
| ---------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------- |
| [`perspective`](https://www.w3school.com.cn/cssref/pr_perspective.asp "CSS perspective 属性")                      | **`perspective`** 指定了观察者与 z=0 平面的距离，使具有三维位置变换的元素产生透视效果。z>0 的三维元素比正常大，而 z<0 时则比正常小，大小程度由该属性的值决定。                             |
| [`perspective-origin`](https://www.w3school.com.cn/cssref/pr_perspective-origin.asp "CSS perspective-origin 属性") | **`perspective-origin`** 指定了观察者的位置，用作 [`perspective`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/perspective) 属性的消失点。 |
```
/* Keyword value 不透视*/
perspective: none;

/* <length> values 透视*/
perspective: 20px;
perspective: 3.5em;
```
---
##### 最大最小值定型

| **最大最小值定型属性**                                                                                |     |
| -------------------------------------------------------------------------------------------- | --- |
| [`max-height`](https://www.w3school.com.cn/cssref/pr_dim_max-height.asp "CSS max-height 属性") |     |
| [`max-width`](https://www.w3school.com.cn/cssref/pr_dim_max-width.asp "CSS max-width 属性")    |     |
| [`min-height`](https://www.w3school.com.cn/cssref/pr_dim_min-height.asp "CSS min-height 属性") |     |
| [`min-width`](https://www.w3school.com.cn/cssref/pr_dim_min-width.asp "CSS min-width 属性")    |     |

---
##### Columns属性
**主要用于规定文字的布局格式**

| [`columns`](https://www.w3school.com.cn/cssref/pr_columns.asp "CSS columns 属性")                               |                                                                                                                                                                                                                                                                                                                   |
| ------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [`column-count`](https://www.w3school.com.cn/cssref/pr_column-count.asp "CSS column-count 属性")                | [MDN参考](https://developer.mozilla.org/zh-CN/docs/Web/CSS/column-count)需要 与`column-width`配合使用                                                                                                                                                                                                                      |
| [`column-width`](https://www.w3school.com.cn/cssref/pr_column-width.asp "CSS column-width 属性")                |                                                                                                                                                                                                                                                                                                                   |
|                                                                                                               |                                                                                                                                                                                                                                                                                                                   |
| [`column-gap`](https://www.w3school.com.cn/cssref/pr_column-gap.asp "CSS column-gap 属性")                      | 设置元素列之间的间隔（[gutter](https://developer.mozilla.org/zh-CN/docs/Glossary/Gutters)）大小                                                  <br>`/* Keyword value */`<br>`column-gap: normal;`<br>`/* <length> values */`<br>`column-gap: 3px;`<br>`column-gap: 2.5em;`<br>`/* <percentage> value */`<br>`column-gap: 3%;` |
|                                                                                                               |                                                                                                                                                                                                                                                                                                                   |
| [`column-rule`](https://www.w3school.com.cn/cssref/pr_column-rule.asp "CSS column-rule 属性")                   | `column-rule` [简写属性](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Shorthand_properties)可以在多列布局中设定分割线的宽度、样式和颜色<br>`column-rule: dotted;`<br>`column-rule: solid 8px;`<br>`column-rule: solid blue;`<br>`column-rule: thick inset blue;`                                                                        |
| [`column-rule-color`](https://www.w3school.com.cn/cssref/pr_column-rule-color.asp "CSS column-rule-color 属性") |                                                                                                                                                                                                                                                                                                                   |
| [`column-rule-width`](https://www.w3school.com.cn/cssref/pr_column-rule-width.asp "CSS column-rule-width 属性") |                                                                                                                                                                                                                                                                                                                   |
|                                                                                                               |                                                                                                                                                                                                                                                                                                                   |
| `column-fill`                                                                                                 | `/* 关键字值 */`<br>`column-fill: auto;`<br>`column-fill: balance;`<br>`column-fill: balance-all;`<br><br>`/* 全局值 参考MDN都有的*/`<br>`column-fill: inherit;`<br>`column-fill: initial;`<br>`column-fill: revert;`<br>`column-fill: revert-layer;`<br>`column-fill: unset;`                                                |
```
/* Column width */
columns: 18em;

/* Column count */
columns: auto;
columns: 2;

/* Both column width and count */
columns: 2 auto;
columns: auto 12em;
columns: auto auto;

/* Global values */
columns: inherit;
columns: initial;
columns: unset;
```


---

##### Box背景属性

| **背景元素属性**                                                                                                          |                                                                                                                                                                                                                                                                                                                                            |
| ------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| [`background`](https://www.w3school.com.cn/cssref/pr_background.asp "CSS background 属性")                            |                                                                                                                                                                                                                                                                                                                                            |
| [`background-position`](https://www.w3school.com.cn/cssref/pr_background-position.asp "CSS background-position 属性") | 配合背景图片使用top/bottom    left/right    center 或者两个百分比，或者top/bottom    left/right + 百分比/绝对长度                                                                                                                      为每一个背景图片设置初始位置。这个位置是相对于由 [`background-origin`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background-origin) 定义的位置图层的。 |
| `background-color`                                                                                                  | 背景颜色                                                                                                                                                                                                                                                                                                                                       |
| [`background-attachment`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background-attachment)                   |                                                                                                                                                                                                                                                                                                                                            |
| [`background-clip`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background-clip)                               |                                                                                                                                                                                                                                                                                                                                            |
| [`background-blend-mode`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background-blend-mode)                   |                                                                                                                                                                                                                                                                                                                                            |
| [`background-image`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background-image)                             | 用url()函数来添加网络图像或者直接填路径来添加本地图像                                                                                                                                                                                                                                                                                                              |
```
/* 使用 <background-color> */
background: green;

/* 使用 <bg-image> 和 <repeat-style> */
background: url("test.jpg") repeat-y;

/* 使用 <box> 和 <background-color> */
background: border-box red;

/* 将背景设为一张居中放大的图片 */
background: no-repeat center/80% url("../img/image.png");
```

--- 

##### Box显示优先级

| **层次优先级**                                                                           |        |
| ----------------------------------------------------------------------------------- | ------ |
| [`z-index`](https://www.w3school.com.cn/cssref/pr_pos_z-index.asp "CSS z-index 属性") | 越大越在前面 |

---

##### Margin详解（常用设置）(Box设置)
###### 常见问题：
1. 边距重叠：本元素：margin_top ，父元素：margin_buttom，注意，无论有没有直接定义，只要定义重叠，比如两个都设置margin：？px，那也会重叠
2. box-sizing属性设置border-box会覆盖padding属性，使得其突出部分被削除，即使加上border边框也不会影响
[Padding，Margin，Border专门教程](https://www.bilibili.com/video/BV1WA411h7Y1/?spm_id_from=333.337.search-card.all.click&vd_source=b0e43c2699f8a8121ebf635fdc2de169)
###### 相关介绍定义

| **居中边缘**                                                                                          |                                                                                                             |
| ------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------- |
| [`margin`](https://www.w3school.com.cn/cssref/pr_margin.asp "CSS margin 属性")                      | 泛属性，多个数值可以用空格隔开数值。当单个数值的时候，内容的上下左右都按此数值填充增加**框线与上一层框线的空间**/**框线外空间**。两个数值则分别设置上下，左右。**如果是可互动元素，增加的空间不会被检测** |
| [`margin-bottom`](https://www.w3school.com.cn/cssref/pr_margin-bottom.asp "CSS margin-bottom 属性") |                                                                                                             |
| [`margin-left`](https://www.w3school.com.cn/cssref/pr_margin-left.asp "CSS margin-left 属性")       |                                                                                                             |
| [`margin-right`](https://www.w3school.com.cn/cssref/pr_margin-right.asp "CSS margin-right 属性")    |                                                                                                             |
| [`margin-top`](https://www.w3school.com.cn/cssref/pr_margin-top.asp "CSS margin-top 属性")          |                                                                                                             |


---
##### Padding属性详解(Box设置)
###### 常见问题：
1. box-sizing属性设置border-box会覆盖padding属性，使得其突出部分被削除，即使加上border边框也不会影响
[Padding，Margin，Border专门教程](https://www.bilibili.com/video/BV1WA411h7Y1/?spm_id_from=333.337.search-card.all.click&vd_source=b0e43c2699f8a8121ebf635fdc2de169)
###### 表格介绍定义

| **padding属性**                                                                                                                            |                                                                                                             |
| ---------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------- |
| [`padding`](https://www.w3school.com.cn/cssref/pr_padding.asp "CSS padding 属性")                                                          | 泛属性，多个数值可以用空格隔开数值。当单个数值的时候，内容的上下左右都按此数值填充增加**内部空间**/**框线内部空间**。两个数值则分别设置上下，左右。**如果是可互动元素，增加的空间也会被检测**       |
| [`padding-bottom`](https://www.w3school.com.cn/cssref/pr_padding-bottom.asp "CSS padding-bottom 属性")                                     |                                                                                                             |
| [`padding-left`](https://www.w3school.com.cn/cssref/pr_padding-left.asp "CSS padding-left 属性")                                           |                                                                                                             |
| [`padding-right`](https://www.w3school.com.cn/cssref/pr_padding-right.asp "CSS padding-right 属性")                                        |                                                                                                             |
| [`padding-top`](https://www.w3school.com.cn/cssref/pr_padding-top.asp "CSS padding-top 属性")                                              |                                                                                                             |

---
##### Object属性介绍

| **object元素位置**                                                                                          | **可替换元素**（**replaced element**）的展现效果不是由 CSS 来控制的。这些元素是一种外部对象，它们外观的渲染，是独立于 CSS 的。 |
| ------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- |
| [`object-position`](https://www.w3school.com.cn/cssref/pr_object-position.asp "CSS object-position 属性") | 只控制可替换元素，参数可以用百分比，数字单位，特定边left buttom right top                                  |

---
#### 杂项属性设置
##### 字体属性介绍（常用设置）
###### 一般文字设置

| **字体设置属性**                                                                                                 |                     |
| ---------------------------------------------------------------------------------------------------------- | ------------------- |
| [`font`](https://www.w3school.com.cn/cssref/pr_font_font.asp "CSS font 属性")                                | 文字总体属性。大小，颜色等等都可以设置 |
| [`font-size`](https://www.w3school.com.cn/cssref/pr_font_font-size.asp "CSS font-size 属性")                 | 文字大小                |
| [`font-size-adjust`](https://www.w3school.com.cn/cssref/pr_font-size-adjust.asp "CSS font-size-adjust 属性") |                     |
| [`font-stretch`](https://www.w3school.com.cn/cssref/pr_font-stretch.asp "CSS font-stretch 属性")             |                     |
| [`font-weight`](https://www.w3school.com.cn/cssref/pr_font-weight.asp "CSS font-weight 属性")                |                     |
###### 额外文字效果

| **文字属性**                                                                                         |      |
| ------------------------------------------------------------------------------------------------ | ---- |
| [`text-indent`](https://www.w3school.com.cn/cssref/pr_text_text-indent.asp "CSS text-indent 属性") |      |
| [`text-shadow`](https://www.w3school.com.cn/cssref/pr_text-shadow.asp "CSS text-shadow 属性")      | 文字阴影 |
###### 字体间距属性
| [`letter-spacing`](https://www.w3school.com.cn/cssref/pr_text_letter-spacing.asp "CSS letter-spacing 属性") | `letter-spacing` 属性用于设置文本字符的间距表现。在渲染文本时添加到字符之间的自然间距中。`letter-spacing` 的正值会导致字符分布得更远，而 `letter-spacing` 的负值会使字符更接近。[MDN描述](https://developer.mozilla.org/zh-CN/docs/Web/CSS/letter-spacing) |
| --------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
###### 单词间隔属性
| [`word-spacing`](https://www.w3school.com.cn/cssref/pr_text_word-spacing.asp "CSS word-spacing 属性") |  **`word-spacing`** 设置标签、单词之间的空格长度 |
| --------------------------------------------------------------------------------------------------- | ---------------------------------- |

---
##### 透明度（常用设置）

| **透明度**                                                                         |     |
| ------------------------------------------------------------------------------- | --- |
| [`opacity`](https://www.w3school.com.cn/cssref/pr_opacity.asp "CSS opacity 属性") |     |

---

##### 盒子阴影（常用设置）

| [`box-shadow`](https://www.w3school.com.cn/cssref/pr_box-shadow.asp "CSS box-shadow 属性") | 设置盒子边缘的阴影，值通常用多个长度加rgb等等组成，推荐复制网站的来学习[CSSShadow](https://getcssscan.com/css-box-shadow-examples?ref=producthunt) |
| ---------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- |

---
##### Line-height属性

| [`line-height`](https://www.w3school.com.cn/cssref/pr_dim_line-height.asp "CSS line-height 属性") | **`line-height`** [CSS](https://developer.mozilla.org/zh-CN/docs/Web/CSS) 属性用于设置多行元素的空间量，如多行文本的间距。对于块级元素，它指定元素行盒（line boxes）的最小高度。对于非[替代](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Replaced_element)的 inline 元素，它用于计算行盒（line box）的高度 |
| ----------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
关联：inline元素

---
#### CSS排版方式
##### Grid属性介绍(CSS排版方式)
[Grid一定要去看这期视频，比这里看效果好](https://www.bilibili.com/video/BV1XE41177oN/?spm_id_from=333.999.0.0&vd_source=b0e43c2699f8a8121ebf635fdc2de169)
###### 基本父属性

| **grid属性**                                                                                                                | 用来定义矩形框格                          未定义相关子元素属性就只占一格                                                                  | 需要display设定为grid                                                                                                   |
| ------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------ |
| [`grid`](https://www.w3school.com.cn/cssref/pr_grid.asp "CSS grid 属性")                                                    |                                                                                                                    |                                                                                                                    |
| [`grid-template`](https://www.w3school.com.cn/cssref/pr_grid-template.asp "CSS grid-template 属性")                         |                                                                                                                    |                                                                                                                    |
| [`grid-template-rows`](https://www.w3school.com.cn/cssref/pr_grid-template-rows.asp "CSS grid-template-rows 属性")          | 定义行主要通过此属性                                              GridLines可以通过`[name1] n1 [name2] n2`定义快捷名，子元素就可以通过名字来定义位置了 | 定义多少个值就有多少个                                还可以设置`1fr`设置为占等分当前方向长度的一份               还可以用repeat函数设置如5等分repeat(5,1fr) |
| [`grid-template-columns`](https://www.w3school.com.cn/cssref/pr_grid-template-columns.asp "CSS grid-template-columns 属性") | 定义列主要通过此属性                                                                                                         | 定义多少个值就有多少个                                                                                                        |
| [`grid-template-areas`](https://www.w3school.com.cn/cssref/pr_grid-template-areas.asp "CSS grid-template-areas 属性")       | 其实就是上面的一个总体属性（太喜欢css辣）                                                                                             | 设置`"a b"`可以设定row column                  还可以用`"name1 name2 name3 name3"`来命名，但是我仍然不推荐                               |
|                                                                                                                           |                                                                                                                    |                                                                                                                    |
| [`grid-auto-columns`](https://www.w3school.com.cn/cssref/pr_grid-auto-columns.asp "CSS grid-auto-columns 属性")             |                                                                                                                    |                                                                                                                    |
| [`grid-auto-flow`](https://www.w3school.com.cn/cssref/pr_grid-auto-flow.asp "CSS grid-auto-flow 属性")                      |                                                                                                                    |                                                                                                                    |
| [`grid-auto-rows`](https://www.w3school.com.cn/cssref/pr_grid-auto-rows.asp "CSS grid-auto-rows 属性")                      |                                                                                                                    |                                                                                                                    |
| [`grid-gap`](https://www.w3school.com.cn/cssref/pr_grid-gap.asp "CSS grid-gap 属性")                                        | row-gap、column-gap还可以设置每个格子的间隔                                                                                     |                                                                                                                    |

###### 基本子属性

![[grid.PNG]]

| [`grid-column`](https://www.w3school.com.cn/cssref/pr_grid-column.asp "CSS grid-column 属性")                   | 必须与grid-row配合用否则grid-row默认为1 / 1           | 起始（格子开头的位置） / 终止（格子最后达到的位置）                                                                                                      可以用span n来从当前位置扩展n格 |
| ------------------------------------------------------------------------------------------------------------- | ------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| [`grid-column-end`](https://www.w3school.com.cn/cssref/pr_grid-column-end.asp "CSS grid-column-end 属性")       | grid-column细分属性                            |                                                                                                                                                      |
| [`grid-column-gap`](https://www.w3school.com.cn/cssref/pr_grid-column-gap.asp "CSS grid-column-gap 属性")       | grid-column细分属性                            |                                                                                                                                                      |
| [`grid-column-start`](https://www.w3school.com.cn/cssref/pr_grid-column-start.asp "CSS grid-column-start 属性") | grid-column细分属性                            |                                                                                                                                                      |
|                                                                                                               |                                            |                                                                                                                                                      |
| [`grid-row`](https://www.w3school.com.cn/cssref/pr_grid-row.asp "CSS grid-row 属性")                            | **必须与grid-column配合用否则grid-column默认为1 / 1** | **同grid-column**                                                                                                                                     |
| [`grid-row-end`](https://www.w3school.com.cn/cssref/pr_grid-row-end.asp "CSS grid-row-end 属性")                | grid-row细分属性                               |                                                                                                                                                      |
| [`grid-row-gap`](https://www.w3school.com.cn/cssref/pr_grid-row-gap.asp "CSS grid-row-gap 属性")                | grid-row细分属性                               |                                                                                                                                                      |
| [`grid-row-start`](https://www.w3school.com.cn/cssref/pr_grid-row-start.asp "CSS grid-row-start 属性")          | grid-row细分属性                               |                                                                                                                                                      |
|                                                                                                               |                                            |                                                                                                                                                      |
| [`grid-area`](https://www.w3school.com.cn/cssref/pr_grid-area.asp "CSS grid-area 属性")                         | 总体属性（不推荐你用因为可读性依托）                         | **grid-row第一个值 / grid-column的第一个值 / grid-row第二个值 / grid-column的第二个值**                                                                                |



---

##### Flex属性介绍（常用设置）(CSS排版方式)
###### [（重要）Flex相关教程](https://www.bilibili.com/video/BV1qJ411N7TA/?spm_id_from=333.999.0.0&vd_source=b0e43c2699f8a8121ebf635fdc2de169)
###### 表格介绍

| **flex属性**                                                                                  | flex只有父层一个flex container，被display属性定义为flex后，其子对象才会成为flex box，并且除非特别提到，否则都是写在父层flex container的属性里                                                                                                                                               |
| ------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [`flex`](https://www.w3school.com.cn/cssref/pr_flex.asp "CSS flex 属性")                      | flex-grow + flex-shrink + flex-basis，最后一项用于设置最大可分到的剩余空间长度                                                                                                                                                                                      |
| `flex-direction`                                                                            | 指定main-axis，当**row、column**的一个被设置的时候，另一个就变成cross-axis。                                                                                                                                                                                         |
| [`flex-basis`](https://www.w3school.com.cn/cssref/pr_flex-basis.asp "CSS flex-basis 属性")    | 覆写当前容器main-axis的长度，对应属性会失效比如width height                       不设置overflow hidden的时候，如果main-axis为row设置为0与width设置为0效果相同，宽度取决于子元素宽度                                                                                    设置auto则由main-axis对应长度属性设置 |
| [`flex-grow`](https://www.w3school.com.cn/cssref/pr_flex-grow.asp "CSS flex-grow 属性")       | **可以写在子元素总体属性里面**，如class="xx A" class="xx B" .xx {...(这里)}，用于设置子元素占有剩下长度的等分后的几份（main-axis）                                               **也可以写在子元素属性里面**，不过这时候如果没设置其他子元素的话，其他子元素就自动设置0了                                                       |
| [`flex-shrink`](https://www.w3school.com.cn/cssref/pr_flex-shrink.asp "CSS flex-shrink 属性") | **设定如何缩小，可以写在子元素总体属性里面，也可以把份数写在子元素属性里面**，当总体属性里此属性设置为0，无论如何都不会收缩，剩下子元素会超出，只有当子元素再分别设置覆盖才不再超出                                                                                                                                                   |

###### 相关属性
| `justify-content` | 相关：center、flex-start、flex-end、flex-*-reverse。此选项设定的是flex-direction/main-axis的方向上进行对齐，比如说row行，那么就行居中 |
| ----------------- | --------------------------------------------------------------------------------------------------- |
| `align-items`     | **同上，但是设定的是cross-direction的方向，也就是flex-direction没选择的方向进行对齐，比如设置row行，那么它将会在高度方向上进行对齐**                |
| `align-self`      | **写在子元素属性里面，用于个别==子元素==覆写`align-items`设定**                                                          |
注意：设置row的时候start左end右，reverse则相反

| `order` | 写在子元素属性里面，用于设置flex container子元素的排序，纯数字 |
| ------- | -------------------------------------- |


| `justify-content` | [[CSS语言入门#Padding属性详解(Box设置)]]相关：                   |
| ----------------- | --------------------------------------------------- |
|                   | **space-around：每个子元素左右都有相同长度间隔隔开**                  |
|                   | **space-evenly：每个子元素之间都有相同长度间隔隔开**                  |
|                   | **space-between：每个子元素之间都有相同间隔隔开，不同的在于它会取消最左和最右的空间** |



---

#### 函数初步扩展
##### 常用函数
###### rgb()
RGB三色不多说
###### hsl()
###### calc()
通过JavaScript计算后返回实时调整
或者用某个视口等等的长宽来得到对应元素值

| 函数                                                                                                                                          | 描述                             |
| ------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------ |
| [`attr()`](https://www.w3school.com.cn/cssref/func_attr.asp "CSS attr() 函数")                                                                | 返回所选元素的属性值。                    |
| [`calc()`](https://www.w3school.com.cn/cssref/func_calc.asp "CSS calc() 函数")                                                                | 允许您执行计算来确定 CSS 属性值。            |
| [`conic-gradient()`](https://www.w3school.com.cn/cssref/func_conic-gradient.asp "CSS conic-gradient() 函数")                                  | 创建圆锥渐变。                        |
| [`counter()`](https://www.w3school.com.cn/cssref/func_counter.asp "CSS counter() 函数")                                                       | 返回指定计数器的当前值。                   |
| [`cubic-bezier()`](https://www.w3school.com.cn/cssref/func_cubic-bezier.asp "CSS cubic-bezier() 函数")                                        | 定义三次贝塞尔曲线。                     |
| [`hsl()`](https://www.w3school.com.cn/cssref/func_hsl.asp "CSS hsl() 函数")                                                                   | 使用色相-饱和度-亮度模型（HSL）定义颜色。        |
| [`hsla()`](https://www.w3school.com.cn/cssref/func_hsla.asp "CSS hsla() 函数")                                                                | 使用色相-饱和度-亮度-阿尔法模型（HSLA）定义颜色。   |
| [`linear-gradient()`](https://www.w3school.com.cn/cssref/func_linear-gradient.asp "CSS linear-gradient() 函数")                               | 将线性渐变设置为背景图像。定义至少两种颜色（从上到下）。   |
| [`max()`](https://www.w3school.com.cn/cssref/func_max.asp "CSS max() 函数")                                                                   | 使用以逗号分隔的值列表中的最大值作为属性值。         |
| [`min()`](https://www.w3school.com.cn/cssref/func_min.asp "CSS min() 函数")                                                                   | 使用以逗号分隔的值列表中的最小值作为属性值。         |
| [`radial-gradient()`](https://www.w3school.com.cn/cssref/func_radial-gradient.asp "CSS radial-gradient() 函数")                               | 将径向渐变设置为背景图像。定义至少两种颜色（从中心到边缘）。 |
| [`repeating-conic-gradient()`](https://www.w3school.com.cn/cssref/func_repeating-conic-gradient.asp "CSS repeating-conic-gradient() 函数")    | 重复圆锥渐变。                        |
| [`repeating-linear-gradient()`](https://www.w3school.com.cn/cssref/func_repeating-linear-gradient.asp "CSS repeating-linear-gradient() 函数") | 重复线性渐变。                        |
| [`repeating-radial-gradient()`](https://www.w3school.com.cn/cssref/func_repeating-radial-gradient.asp "CSS repeating-radial-gradient() 函数") | 重复径向渐变。                        |
| [`rgb()`](https://www.w3school.com.cn/cssref/func_rgb.asp "CSS rgb() 函数")                                                                   | 使用红-绿-蓝模型（RGB）定义颜色。            |
| [`rgba()`](https://www.w3school.com.cn/cssref/func_rgba.asp "CSS rgba() 函数")                                                                | 使用红-绿-蓝-阿尔法模型（RGB）定义颜色。        |
| [`var()`](https://www.w3school.com.cn/cssref/func_var.asp "CSS var() 函数")                                                                   | 插入自定义属性的值。                     |

---
#### 动画
