# CSS

## CSS语法规范

CSS规则由两个主要的部分构成：选择器以及一条或多条声明。

![image-20210214162847182](https://gitee.com/zhang-xiaoweik/images/raw/master/20210323170034.png)

放在\<style>\</style>标签内。

## CSS属性书写顺序

建议遵循以下顺序：

1. 布局定位属性：display/position/float/clear/visibility/overflow（建议display第一个写）
2. 自身属性：width/height/margin/padding/border/background
3. 文本属性：color/font/text-decoration/text-align/vertical-align/white-space/break-word
4. 其他属性（CSS3）：content/cursor/border-radius/box-shadow/text-shadow/background:linear-gradient...

## 基础选择器

### 标签选择器

用HTML标签名称作为选择器，按标签名称分类，为页面中某一类标签指定统一的CSS样式，比如所有的\<div>标签和所有的\<span>标签。

语法：

```
标签名 {
	属性1: 属性值1;
	...
}
```



### 类选择器

如果想要差异化选择不同的标签，单独选一个或者某几个标签，可以使用类选择器。

语法：

```
.类名 {
	属性1: 属性值1;
	...
}
```

例如：

```
.red {
	color: red;
}
```

后续调用只需要在HTML标签中增加一个属性class='red',如下：

```
<div class="red">变红色</div>
```

注意：

1. 类名自定义（随便），但不能与div,p等等HTML标签重名。
2. 类名比较长的话也可以添加'-'，比如"star-sing"。
3. 不能使用纯数字或中文命名。
4. 类选择器可以多次被调用。

#### 多类名选择器

使用方式：

```
<div class="red font20">亚瑟</div>
```

在标签class属性中写多个类名，中间用空格隔开。

使用场景：

可以把一些标签元素相同的样式放到一个类里面，节省CSS代码。

### id选择器

语法：

```
#id名 {
	属性1: 属性值1；
	...
}
```

例如，将id为nav元素中的内容设置为红色。

```
#nav {
	color: red;
}
```

调用：

```
<div id="nav">迈克尔杰克逊</div>
```

注意：id选择器只能被调用一次。

### 通配符选择器

通配符选择器使用"*"定义，他表示选取页面中所有元素（标签）。

语法：

```
* {
	属性1: 属性值1；
	...
}
```

通配符选择器不需要调用，自动给所有的元素使用样式。

## 字体属性

CSS字体属性用于定义字体系列、大小、粗细和文字样式（如斜体）。

### 字体系列

CSS使用font-family属性定义文本的字体系列。

```
p {font-family:"微软雅黑";}
div {font-family:Arial,"Microsoft Yahei","微软雅黑";}
```

- 各种字体之间使用逗号隔开。
- 如果一个字体由多个单词组成要加引号。
- 如果写多个字体，浏览器会依次查看你的电脑有没有安装该字体，选取第一个安装了的字体显示。

### 字体大小

CSS使用font-size属性定义字体大小。

```
p {
	font-size: 20px;
}
```

可以使用\<body>标签设置整个页面的文字大小，但标题标签文字大小需要另外设置。

### 字体粗细

CSS使用font-weight 属性定义字体粗细。

```
p {
	font-weight: bold;
}
```

| 属性值  | 描述                                                       |
| ------- | ---------------------------------------------------------- |
| normal  | 默认值（不加粗）                                           |
| bold    | 粗体                                                       |
| 100-900 | 400等同于normal，而700等同于bold，注意这个数字后面不跟单位 |

### 文字样式

CSS使用font-style属性设置文本的风格

```
p {
	font-style: normal;
}
```

| 属性值 | 作用   |
| ------ | ------ |
| normal | 默认值 |
| italic | 斜体   |

平时我们很少给文字加斜体，反而要给斜体标签（em,i）改为不倾斜字体。

### 字体复合属性

```
body {
	font: font-style font-weight font-size/line-height font-family;
}
```

- 使用font属性时，必须按上面顺序，各属性空格隔开。
- 不需要设置的属性可以省略（取默认值），但必须保留font-size和font-family属性，否则font属性将不起作用

例如：

```
div {
	font: italic 700 16px 'Microsoft Yahei';
}
```

## 文本属性

CSS文本属性可定义文本的外观，比如文本的颜色、对齐文本、装饰文本、文本缩进、行间距等。

### 文本颜色

color属性定义文本颜色。

```
div {
	color: red;
}
```

| 表示           | 属性值                        |
| -------------- | ----------------------------- |
| 预定义的颜色值 | red,green,blue,pink           |
| 十六进制       | #FF0000,#FF6600,#29D794       |
| RGB代码        | rgb(255,0,0)或rgb(100%,0%,0%) |

### 对齐文本

text-align属性用于设置元素内文本内容的水平对齐方式。

```
div {
	text-align: center;
}
```

| 属性值 | 解释             |
| ------ | ---------------- |
| left   | 左对齐（默认值） |
| right  | 右对齐           |
| center | 居中对齐         |

### 装饰文本

text-decoration属性规定添加到文本的修饰，可以给文本添加下划线、删除线、上划线等。

```
div {
	text-decoration: underline;
}
```

| 属性值       | 描述                            |
| ------------ | ------------------------------- |
| none         | 默认，无装饰线（最常用）        |
| underline    | 下划线，链接a自带下划线（常用） |
| overline     | 上划线（几乎不用）              |
| line-through | 删除线（不常用）                |

### 文本缩进

text-indent属性用来指定文本的第一行的缩进，通常是将段落的首行缩进。

```
div {
	text-indent: 10px;
}
p {
	text-indent: 2em;
}
```

em是一个相对单位，就是当前元素1个文字的大小，如果当前元素没有设置大小，会按照父元素的1个文字大小。

### 行间距

line-height属性设置行间距离（行高）。

```
p {
	line-height: 26px;
}
```

![image-20210215153957190](https://gitee.com/zhang-xiaoweik/images/raw/master/20210323170043.png)

修改行间距改的是上间距和下间距，文字大小不变。

## CSS引入方式

### 内部样式表

内部样式表（内嵌样式表）是写到html页面内部，是将所有CSS代码抽取出来，单独放到一个\<style>标签中。

```
<style>
	div {
		color: red;
		font-size: 12px;
	}
</style>
```

\<style>标签理论上可以放在html文档的任何地方，但是一般放在\<head>标签中。

### 行内样式表

行内样式表（内联样式表）是在元素标签内部的style属性中设定CSS样式，适合于修改简单样式。.

```
<div style="color: red;font-size: 12px;">青春不常在，抓紧谈恋爱</div>
```

### 外部样式表

样式单独写到CSS文件中，之后把CSS文件引入到HTML页面中使用。

引入外部样式表分两步:

1. 新建一个后缀名为.css的样式文件,把所有CSS代码都放入此文件中,且不需要再写\<style>标签。
2. 在HTML页面中，使用\<link>标签引入这个文件。

```
<link rel="stylesheet" href="css文件路径">
```

## 复合选择器

复合选择器是由两个或多个基础选择器，通过不同的方式组合而成的。

常用的复合选择器包括：后代选择器、子选择器、并集选择器、伪类选择器等等。

### 后代选择器

后代选择器又称为包含选择器，可以选择父元素里面子元素，写法就是把外层标签写在前面，内层标签写在后面，中间用空格分隔，当标签发生嵌套时，内层标签就成为外层标签的后代。

```
元素1 元素2 {样式声明}  
```

上述语法表示选择元素1里面的所有元素2（后代元素）。

- 元素2只要是元素1的后代即可
- 元素1和元素2可以是任意基础选择器

### 子选择器

子元素选择器只能选择某元素的最近一级子元素。

语法：

```
元素1>元素2 {样式声明}
```

上述语法表示选择元素1里面的所有直接后代元素2。

- 元素2必须是最近一级

### 并集选择器

并集选择器可以选择多组标签，同时为他们定义相同的样式，通常用于集体声明。

```
元素1,元素2 {样式声明}
```

上述语法表示选择元素1和元素2。

建议打完一个"元素,"就回车，竖着写，如下：

```
div,
p,
span {样式声明}
```

### 伪类选择器

伪类选择器用于向某些选择器添加特殊的效果，比如给链接添加特殊效果，或者选择第1个，第n个元素。

伪类选择器最大的特点是用冒号(:)表示，比如:hover、:first-child。

#### 链接伪类选择器

```
a:link    /*选择所有未被访问的链接*/ 
a:visited /*选择所有已被访问的链接*/  
a:hover   /*选择鼠标指针位于其上的链接*/ 
a:active  /*选择活动链接（鼠标按下未弹起的链接）*/ 
```

1. 为了确保生效，要按照LVHA的顺序声明:link - :visited - :hover - :active。
2. a链接在浏览器中具有默认样式，实际工作中要给链接单独指定样式。

链接伪类选择器实际工作开发中的写法：

```
a {
	color: gray;
}
a:hover {
	color: red;  /*鼠标经过的时候，由原来的灰色变成红色*/
}
```



如果需要在鼠标经过某盒子时修改该盒子子元素属性，写法如下

```
选择器:hover 子元素的选择器 {样式}
```



#### :focus伪类选择器

:focus伪类选择器用于选取获得焦点的表单元素。

焦点就是光标，一般情况\<input>类表单元素才能获取，因此这个选择器也主要针对表单元素来说。

```
input:focus {
	background-color:yellow;
}
```

## CSS元素显示模式

### 块元素

常见的块元素有\<h1>~\<h6>、\<p>、\<div>、\<ul>、\<ol>、\<li>等，其中\<div>标签是最典型的块元素。

块级元素的特点：

1. 独占一行。
2. 高度、宽度、外边距以及内边距都可以控制。
3. 宽度默认是容器（父级宽度）的100%。
4. 是一个容器及盒子，里面可以放行内或者块级元素。

注意：

- 文字类的元素内不能使用块级元素。
- \<p>标签主要用于存放文字，因此\<p>里面不能放块级元素，特别是不能放\<div>。
- 同理，\<h1>~\<h6>等都是文字类块级标签，里面也不能放其他块级元素。

### 行内元素

常见的行内元素有\<a>、\<strong>、\<b>、\<em>、\<i>、\<del>、\<s>、\<ins>、\<u>、\<span>等，其中\<span>标签是最典型的行内元素，行内元素也称内联元素。

行内元素的特点：

1. 一行可以显示多个。
2. 宽高直接设置是无效的。
3. 默认宽度就是它本身内容的宽度。
4. 行内元素只能容纳文本或其他行内元素。

注意：

链接内不能再放链接

特殊情况链接\<a>里面可以放块级元素，但是给\<a>转换一下块级模式最安全。

### 行内块元素

在行内元素中有几个特殊的标签——\<img>、\<input>、\<td>，它们同时具有块元素和行内元素的特点。

行内块元素的特点：

1. 和相邻行内元素（行内块）在一行上，但是他们之间会有空白缝隙，一行可以显示多个（行内元素特点）。
2. 默认宽度就是它本身内容的宽度（行内元素的特点）。
3. 高度，行高、外边距以及内边距都可以控制（块级元素的特点）。

### 显示模式转换

一个模式的元素需要另外一种模式的特性。比如想要增加链接\<a>的触发范围。

做法：在相应选择器内添加相应display属性。

- 转换为块元素：display:block;
- 转换为行内元素：display:inline;
- 转换为行内块：display:inline-block;

### 单行文字垂直居中

让文字的行高（line-height）等于盒子的高度，就可以让文字在当前盒子内垂直居中。

## 背景

背景属性可以设置背景颜色、背景图片、背景平铺、背景图片位置、背景图像固定等。



### 背景颜色

background-color属性定义了元素的背景颜色。一般情况下元素背景颜色默认值是transparent（透明）。



### 背景图片

background-image属性描述了元素的背景图像。实际开发常见于logo或者一些装饰性的小图片或者是超大的背景图片，优点是非常便于控制位置。

```
background-image: none | url(路径)
```



###  背景平铺

background-repeat属性对背景图像进行平铺。

```
background-repeat: repeat | no-repeat | repeat-x |repeat-y
```

默认是repeat



###  背景图片位置

利用background-position属性可以改变图片在背景中的位置。

```
background-position: x y;
```

x坐标和y坐标，可以使用方位名词或者精确单位。

| 参数                                                        |
| ----------------------------------------------------------- |
| 百分数\|由浮点数字和单位标识符组成的长度值                  |
| top \| center \| bottom \| left \| center \| right 方位名词 |

1.参数是方位名词

- 如果指定的两个值都是方位名词，则两个值的前后顺序无关，比如left top和top left效果一致。
- 如果只指定了一个方位名词，另一个值省略，则第二个值默认居中对齐。

2.参数是精确单位

- 如果参数值是精确坐标，那么第一个肯定是x坐标，第二个一定是y坐标。
- 如果只指定一个数值，该数值一定是x坐标，另一个默认垂直居中。

3.参数是混合单位

- 如果指定的两个值是精确单位和方位名词混合使用，则第一个值是x坐标，第二个值是y坐标。



### 背景图像固定（背景附着）

background-attachment属性设置背景图像是否固定或者随着页面的其余部分滚动。

background-attachment后期可以制作视差滚动的效果。

| 参数   | 作用                   |
| ------ | ---------------------- |
| scroll | 背景图像随对象内容滚动 |
| fixed  | 背景图像固定           |



### 背景复合写法

我们可以将这些背景属性合并简写在同一个属性background中。

使用简写属性时，没有特定的书写顺序，一般习惯约定顺序为：

background:背景颜色 背景图片地址 背景平铺 背景图像固定 背景图片位置；



### 背景大小

background-size属性指定背景图片大小。



语法：

```
background-size: length|percentage|cover|contain
```

| 值         | 描述                                                         |
| ---------- | ------------------------------------------------------------ |
| length     | 设置背景图片高度和宽度。第一个值设置宽度，第二个值设置高度。如果只给出一个值，第二个默认为auto |
| percentage | 计算相对于背景定位区域的百分比。第一个值宽度，第二个值高度。如果只给出一个值，第二个默认为auto |
| cover      | 保持图像纵横比并将图片缩放成完全覆盖背景定位区域的最小大小   |
| contain    | 保持图像纵横比并将图片缩放成适合背景定位区域的最大大小       |



### 背景色半透明

CSS3为我们提供了背景颜色半透明的效果。

```
background: rgba(0,0,0,0.3);
```

- 最后一个参数是透明度alpha，取值范围在0~1之间
- 习惯把0.3的0省略掉，写为background:rgba(0,0,0,.3);
- 注意：背景半透明是指盒子背景半透明，盒子里面的内容不受影响



## CSS特性

### 层叠性

相同选择器给设置同一个样式，其中一个样式就会覆盖（层叠）另一个冲突的样式。层叠性主要解决样式冲突的问题。

- 样式冲突，遵循的原则是就近原则，那个样式离结构近，就用哪个样式。

### 继承性

子标签会继承父标签的某些样式，如文本颜色和字号（text-,font-,line-这些元素开头的可以继承，以及color属性）。

行高的继承性

```
body {
	font: 12px/1.5 Microsoft YaHei;
}
```

- 行高可以跟单位也可以不加单位
- 如果子元素没有设置行高，则会继承父元素的行高为当前子元素文字大小*1.5
- 如果子元素没有设置文字大小，则会继承父元素的文字大小，然后计算子元素的行高

### 优先级

当同一个元素指定多个选择器，就会有优先级的产生。

- 选择器相同，执行层叠性。
- 选择器不同，根据选择器权重执行。



选择器权重如下表

| 选择器               | 选择器权重 |
| -------------------- | ---------- |
| 继承或者 *           | 0,0,0,0    |
| 标签选择器           | 0,0,0,1    |
| 类选择器，伪类选择器 | 0,0,1,0    |
| ID选择器             | 0,1,0,0    |
| 行内样式style=""     | 1,0,0,0    |
| !important           | 无穷大     |

权重从上往下递增

权重叠加：如果是复合选择器，会有权重叠加，需要重新计算权重。

- div ul li ----->  0,0,0,3
- .nav ul li ----->  0,0,1,2
- a:hover ----->  0,0,1,1
- .nav a----->  0,0,1,1

## 盒子模型

CSS盒子模型包括：边框、外边距、内边距和实际内容。

### 边框border

边框由三部分组成：边框宽度（粗细） 边框样式 边框颜色

| 属性         | 作用     |
| ------------ | -------- |
| border-width | 边框粗细 |
| border-style | 边框样式 |
| border-color | 边框颜色 |

border-style常用属性值：

| 属性值 | 作用     |
| ------ | -------- |
| solid  | 实线边框 |
| dashed | 虚线边框 |
| dotted | 点线边框 |

边框简写：

```
border: 1px solid pink; /*没有顺序*/
```

边框分开写法：

```
border-top: 1px solid pink; /*上边框*/
```

假如要求上边框红色，其余边框蓝色，根据层叠性，可以先设置border蓝色，然后设置border-top红色。

#### 表格的细线边框

border-collapse属性控制浏览器绘制表格边框的方式，它控制相邻单元格的边框：

```
border-collapse:collapse;
```

上述代码表示将相邻边框合并在一起。

#### 边框会影响盒子实际大小

定义盒子宽高后，增加边框是加在盒子外侧的。

### 内边距padding

padding属性用于设置内边距，即边框与内容之间的距离。

padding分为左右上下四部分：padding-left、padding-right、padding-top、padding-bottom。



简写：

| 值的个数                   | 意思                                                 |
| -------------------------- | ---------------------------------------------------- |
| padding:5px                | 1个值，代表上下左右都有5像素内边距                   |
| padding:5px 10px           | 2个值，代表上下内边距是5像素 ，右内边距是10像素      |
| padding:5px 10px 20px      | 3个值，代表上内边距5px，左右内边距10px，下内边距20px |
| padding:5px 10px 20px 30px | 4个值，上5px，右10px，下20px，左30px                 |

注意：内边距也会影响盒子大小。如果盒子已经有了宽高，再指定内边距，会撑大盒子。



padding应用：

导航栏里面每个盒子（都是a链接，转换为行内块元素）的字数不同，可以不设置宽度，直接给padding，用padding撑开盒子，可以保证每个盒子两边留的空白一样多。

### 外边距margin

margin同样分为上下左右四个部分，margin-top、margin-bottom、margin-left、margin-right。

margin简写与padding一致。

#### 外边距让盒子水平居中

外边距可以让块级盒子水平居中，但需要满足两个条件：

1. ==盒子必须指定宽度==
2. ==盒子左右外边距都设置为auto==

常见写法，以下三种：

- margin-left: auto;   margin-right: auto;
- margin:auto;
- margin:0 auto;

注意：以上是让块级元素水平居中，行内元素或者行内块元素水平居中给其父元素添加text-align:center 即可。

#### 外边距合并

使用margin定义块元素的垂直外边距时，可能会出现外边距的合并。

主要有两种情况：

1. 相邻块元素垂直外边距的合并

2. 嵌套块元素垂直外边距的塌陷



##### 1.相邻块元素垂直外边距的合并

当上下相邻的两个块元素相遇时，如果上面的元素有margin-bottom，下面的元素有margin-top，他们之间的垂直间距不是margin-bottom和margin-top之和，而是取较大值。

![image-20210219135023993](https://gitee.com/zhang-xiaoweik/images/raw/master/20210323170057.png)

##### 2.嵌套块元素垂直外边距的塌陷

对于两个嵌套关系（父子关系）的块元素，父元素有上外边距同时子元素也有上外边距，此时父元素会塌陷较大的外边距值。

![image-20210219150417950](https://gitee.com/zhang-xiaoweik/images/raw/master/20210323170103.png)

解决方案：

1. 为父元素定义边框
2. 为父元素定义内边距padding
3. 为父元素添加overflow:hidden

### 清除内外边距

网页元素很多都带有默认的内外边距，而且不同浏览器默认的也不一致，因此再布局前，要先清除网页元素的内外边距。

```
* {
	padding:0;
	margin:0;
}
```

注意：行内元素为了照顾兼容性，尽量只设置左右内外边距，不要设置上下内外边距。但是转换为块级和行内块元素就可以了。

## 圆角边框（重点）

border-radius属性用于设置元素的外边框圆角。

```
border-radius: length;
```

原理：以length为半径作圆放到直角相切处。

![](https://gitee.com/zhang-xiaoweik/images/raw/master/20210323170108.png)

半径越大，弧度越明显。

- 参数可以是px或百分比，取50%即为圆。
- 如果需要设置圆角矩形，取高度的一半即可。
- border-radius是个简写属性，可以跟四个值，分别代表左上角、右上角、右下角、左下角。
- 分开写：border-top-left-radius、border-top-right-radius、border-bottom-right-radius、border-bottom-left-radius。 

## 盒子阴影（重点）

```
box-shadow: h-shadow v-shadow  blur spread color inset;
```

| 值       | 描述                                   |
| -------- | -------------------------------------- |
| h-shadow | 必需，水平阴影的位置，允许负值         |
| v-shadow | 必需，垂直阴影的位置，允许负值         |
| blur     | 可选，模糊距离，越大越模糊             |
| spread   | 可选，阴影的尺寸，影子大小             |
| color    | 可选，阴影的颜色                       |
| inset    | 可选，将外部阴影（outset）改为内部阴影 |

注意：

1. 默认的是外阴影，省略不写，如果写了outset，会导致阴影无效。
2. 盒子阴影不占用空间，不会影响其他盒子排列。

## 文字阴影

```
text-shadow: h-shadow v-shadow blur color;
```

属性值与上述盒子阴影相同。

## 浮动

### 传统网页布局的三种方式

网页布局的本质---用CSS来摆放盒子，把盒子放到相应位置。

CSS提供了三种传统布局方式：

- 普通流（标准流）
- 浮动
- 定位

### 标准流（普通流）

所谓标准流，就是标签按照规定的默认方式排列。

1.块级元素独占一行，从上向下顺序排列。

- 常用元素：div、hr、p、h1~h6、ul、ol、dl、form、table

2.行内元素从左到右排列，碰到父元素边缘自动换行

- 常用元素：span、a、i、em等

注意：实际开发中，一个页面基本都包含了这三种布局方式。

### 浮动（float）

#### 为什么需要浮动？

提问：用标准流能很方便的实现如下效果吗？

1.如何让多个块级盒子（div）水平排列成一行？

![image-20210220145624664](https://gitee.com/zhang-xiaoweik/images/raw/master/20210323170112.png)

比较难，虽然转换为行内块元素可以实现一行显示，但是他们之间会有空白缝隙，很难控制

2.如何实现两个盒子的左右对齐？

![image-20210220145713081](https://gitee.com/zhang-xiaoweik/images/raw/master/20210323170115.png)

总结：有很多的布局效果，标准流没有办法完成，此时就可以利用浮动完成布局，因为浮动可以改变元素标签默认的排列方式。

浮动最典型的应用：可以让多个块级元素一行内排列显示。

网页布局第一准则：多个块级元素纵向排列找标准流，多各块级元素横向排列找浮动。

#### 什么是浮动

float属性用于创建浮动框，将其移动到一边，直到左边缘或右边缘触及包含块或另一个浮动框的边缘。

语法：

```
选择器 {float: 属性值;}
```

| 属性值 | 描述                 |
| ------ | -------------------- |
| none   | 元素不浮动（默认值） |
| left   | 元素向左浮动         |
| right  | 元素向右浮动         |

#### 浮动特性（重难点）

1.浮动元素会脱离标准流（脱标）

浮动的盒子不再保留原先的位置。

![image-20210220151649648](https://gitee.com/zhang-xiaoweik/images/raw/master/20210323170118.png)

2.浮动的元素会一行内显示并且元素顶部对齐

浮动的元素是互相贴靠在一起的（不会有缝隙），如果父级宽度装不下这些浮动的盒子，多出的盒子会另起一行对齐 。

3.浮动的元素会具有行内块元素的特性

任何元素都可以浮动，不管原先是什么模式的元素，添加浮动之后具有行内块元素相似的特性。

- 如果块级盒子没有设置宽度，默认宽度和父级一样宽，但是添加浮动后，它的大小根据内容来决定

#### 浮动元素经常和标准流父级搭配使用

为了约束浮动元素位置，我们网页布局一般采取的策略是：

先用标准流的父元素排列上下位置，之后内部子元素采取浮动排列左右位置。

![image-20210220153827167](https://gitee.com/zhang-xiaoweik/images/raw/master/20210323170122.png)

#### 浮动布局注意点

一个元素浮动了，理论上其余兄弟元素也要浮动。

浮动的盒子只会影响浮动盒子后面的标准流，不会影响前面的标准流。

#### 清除浮动

由于父级盒子很多情况下，不方便给高度，但是子盒子浮动又不占有位置，导致父级盒子高度为0，也会影响下面的标准流盒子。

![image-20210220162130680](https://gitee.com/zhang-xiaoweik/images/raw/master/20210323170125.png)

- 清除浮动的本质是清除浮动元素脱标造成的影响
- 如果父盒子本身有高度，则不需要清除浮动
- 清除浮动之后，父级就会根据浮动的子盒子自动检测高度。

语法：

```
选择器{clear:属性值;}
```

| 属性值 | 描述                                       |
| ------ | ------------------------------------------ |
| left   | 不允许左侧有浮动元素（清除左侧浮动的影响） |
| right  | 不允许右侧有浮动元素（清除右侧浮动的影响） |
| both   | 同时清除左右两侧浮动的影响                 |

在实际工作种，几乎只用clear:both;

清除浮动的策略是闭合浮动，只让浮动在父盒子内部影响，不影响父盒子外面的其他盒子。



清除浮动的方法：

1. 额外标签法也称为隔墙法，是W3C推荐的做法
2. 父级添加overflow属性
3. 父级添加after伪元素
4. 父级添加双伪元素

##### 额外标签法

额外标签法会在浮动元素末尾添加一个空的标签，例如\<div style="clear:both">\</div>，或者其他标签（如\</br>等）。

- 优点：通俗易懂，书写方便
- 缺点：添加许多无意义的标签，结构化较差

注意：这个新的空标签必须是==块级元素==。

##### 父级添加overflow

可以给父级添加overflow属性，将其属性值设置为hidden、auto或scroll。

- 优点：代码简洁
- 缺点：无法显示溢出的部分

##### :after伪元素法

:after方式是额外标签法的升级版，相当于在浮动元素末尾添加一个带clear:both的空标签，也是给父元素添加，写法固定

```
/*单冒号是为了照顾低版本浏览器，用双冒号也可*/
.clearfix:after {
	content: "";       /*伪元素必写属性*/
	display: block;	   /*插入的元素必须是块级*/	
	height: 0;	       /*不要看见这个元素*/
	clear: both;
	visibility: hidden;/*不要看见这个元素*/
}
.clearfix {   /*为了兼容IE6、7*/
	*zoom: 1;
}
```

同时父元素在原本指定的选择器后面再加上这个clearfix选择器。

- 优点：没有增加标签，结构更加简单。
- 缺点：照顾低版本浏览器
- 代表网站：百度、淘宝、网易等

##### 双伪元素清除浮动

也是给父元素添加，写法固定

```
.clearfix:before,
.clearfix:after {
	content: "";
	display: table; 
}
.clearfix:after {
	clear:both;
}
.clearfix {   /*为了兼容IE6、7*/
	*zoom: 1;
}
```

同样父元素在原本指定的选择器后面再加上clearfix选择器

- 优点：结构更加简单。
- 缺点：照顾低版本浏览器
- 代表网站：小米、腾讯等



## 定位

定位可以让某个元素在一个盒子内自由移动位置，并且压住其他盒子。

定位可以在我们滚动窗口时，让某个盒子固定在屏幕的某个位置。

### 定位组成

定位=定位模式+边偏移。



**1.定位模式**

定位模式决定元素的定位方式，通过CSS的position属性来设置，其值可以分为四个：

| 值       | 语义     |
| -------- | -------- |
| static   | 静态定位 |
| relative | 相对定位 |
| absolute | 绝对定位 |
| fixed    | 固定定位 |

**2.边偏移**

边偏移就是定位的盒子移动到最终位置，有top、bottom、left和right四个属性。

| 边偏移属性 | 示例         | 描述                                           |
| ---------- | ------------ | ---------------------------------------------- |
| top        | top: 80px    | 顶端偏移量，定义元素相对于其父元素上边线的距离 |
| bottom     | bottom: 80px | 底部偏移量，元素相对于其父元素下边线的距离     |
| left       | left: 80px   | 左侧偏移量，元素相对于其父元素左边线的距离     |
| right      | right: 80px  | 右侧偏移量，元素相对于其父元素右边线的距离     |



#### 静态定位static（了解）

静态定位是元素的默认定位方式，无定位的意思。

语法：

```
选择器 {position: static;}
```

- 静态定位按照标准流特性摆放位置，它没有边偏移
- 静态定位在布局时很少用到

#### 相对定位relative（重要）

相对定位是元素在移动位置的时候，相对于它原来的位置来说的。

语法：

```
选择器 {position: relative;}
```

相对定位的特点：

1. 如果给个边偏移是top:100px，会让该元素向下移动到距离原位置100px的地方，同样给个left:100px，会向右移动到距原位置100px的地方。
2. ==原来在标准流的位置继续占有==，后面的盒子仍然以标准流的方式对待该元素（后面盒子完全不被影响，不会像浮动那样后面的盒子向上移动占位）。

#### 绝对定位absolute（重要）

绝对定位是相对于它的祖先元素来说的。

语法：

```
选择器 {position: absolute;}
```

绝对定位的特点：

1. 如果没有祖先元素或者祖先元素没有定位，则以浏览器为准定位。 
2. 如果==祖先元素==有定位（相对、绝对、固定定位），则以==最近一级==的==有定位祖先元素==为参考点移动位置。
3. 绝对定位==不再占有原先的位置==。（脱标）

#### 子绝父相

子级是绝对定位的话，父级如果需要占有位置要用相对定位。

1. 子级绝对定位，不会占有位置，可以放到父盒子里的任何一个地方，不会影响其他兄弟盒子。
2. 父盒子需要加定位限制子盒子在父盒子内显示。
3. 父盒子布局时，需要占有位置，因此父亲只能是相对定位。



如下图中间的盒子：

![image-20210224221017483](https://gitee.com/zhang-xiaoweik/images/raw/master/20210323170133.png)



#### 固定定位fixed（重要）

固定定位是元素固定于浏览器可视区的位置，主要使用场景：可以在浏览器页面滚动时元素的位置不会改变。

语法：

```
选择器 { position: fixed;}
```

固定定位的特点：

1.以浏览器的可视窗口为参照点移动元素。

- 跟父元素没有任何关系
- 不随滚动条滚动

2.固定定位==不占有原先的位置==。

固定定位也是脱标的，可以看作是一种特殊的绝对定位。



==固定定位小技巧：固定在版心右侧位置==。

1. 让固定定位的盒子left:50%，走到浏览器可视区的一半位置。
2. 让固定定位的盒子margin-left:版心宽度的一半距离。多走版心宽度的一半位置，就可以让固定定位的盒子贴着版心右侧对齐了。



#### 粘性定位sticky（了解）

粘性定位可以被认为是相对定位和固定定位的混合。

语法：

```
选择器 { position: sticky;top: 10px;}
```



粘性定位特点：

1. 以浏览器的可视窗口为参照点移动元素（固定定位特点）
2. 粘性定位==占有原先的位置==（相对定位特点）
3. 必须添加top、left、right、bottom其中一个才有效。

跟页面滚动搭配使用。兼容性较差，IE不支持。



### 定位叠放次序z-index

在使用定位布局时，可能会出现盒子重叠的情况，此时，可以使用z-index来控制盒子的前后次序（z轴）

语法：

```
选择器 { z-index: 1;}
```

- 数值可以是正整数、负整数或0，默认是auto，数值越大，盒子越靠上
- 如果属性值相同，则按照书写顺序，后来居上
- 数字后面不能加单位
- 只有定位的盒子才有z-index属性



### 定位的拓展

#### 1.绝对定位的盒子居中

加了绝对定位和固定定位的盒子不能通过margin:0 auto水平居中，但是可以通过以下计算方法实现水平和垂直居中。

1. left:50%;让盒子的左侧移动到父级元素的水平中心位置。
2. margin-left:-100px;让盒子向左移动自身宽度的一半。

垂直居中方法相似。

固定定位也可以使用这种方式居中。



#### 2.定位特殊特性

绝对定位和固定定位也和浮动类似。

1.行内元素添加绝对或者固定定位，可以直接设置高度和宽度。

2.块级元素添加绝对或者固定定位，如果不给宽度或者高度，默认大小是内容的大小。

 

#### 3.脱标的盒子不会触发外边距塌陷

浮动元素、绝对定位（固定定位）元素都不会触发外边距合并的问题



#### 4.绝对定位（固定定位）会完全压住盒子

浮动元素不同，只会压住它下面标准流的盒子，但是不会压住下面标准流盒子里面的文字和图片。

但是绝对定位（固定定位）会压住下面标准流所有的内容。

浮动之所以不会压住文字和图片，是因为浮动最初产生的目的是为了做文字环绕效果，文字会围绕浮动元素。



## 元素的显示与隐藏

类似网站广告，当我们点击关闭就不见了，但是我们重新刷新页面，会重新出现。

本质：让一个元素在页面中隐藏或者显示出来。



1.display显示隐藏

2.visibility显示隐藏

3.overflow溢出显示隐藏



### display属性

- display : none ;隐藏对象
- display : block ;除了转换为块级元素之外，同时还有显示元素的意思

==display隐藏元素后不保留原位置==

后面应用广泛，搭配JS可以做很多网页特效。



### visibility可见性

- visibility : visible; 元素可视
- visibility : hidden; 元素隐藏

==visibility隐藏元素后保留原位置==

如果隐藏元素想要保留位置，就用visibility : hidden

如果隐藏元素不想保留位置，就用display : none（用处更多 重点）



### overflow溢出

  overflow属性制定了如果内容溢出一个元素的框时，会发生什么。

| 属性值  | 描述                                     |
| ------- | ---------------------------------------- |
| visible | 不剪切内容也不添加滚动条                 |
| hidden  | 不显示超过对象尺寸的内容，超出的部分隐藏 |
| scroll  | 不管超出内容否，总是显示滚动条           |
| auto    | 超出框自动显示滚动条，不超出不显示滚动条 |

一般情况下，我们不想让溢出的内容显示出来，因为溢出的部分会影响布局。

但是如果有定位的盒子，请慎用overflow : hidden 因为它会隐藏多余部分。



如下图中HOT就有部分在盒子外面，如果使用overflow : hidden 外面的部分就会被隐藏。

![image-20210226145823429](https://gitee.com/zhang-xiaoweik/images/raw/master/20210323170142.png)





## 精灵图

### 精灵图（sprites）的使用

1. 精灵技术主要针对于==背景图片==使用，就是把多个小背景图片整合到一张大图片中
2. 这个大图片称为sprites精灵图
3. 移动背景图片位置，此时可以使用background-position
4. 移动的距离就是这个目标图片的x和y坐标，x轴向右，y轴向下
5. 一般情况下都是把精灵图往左往上移动，所以数值是负值
6. 使用精灵图的时候需要精确测量，每个小背景图片的大小和位置



## 字体图标

使用场景：主要用于显示网页中通用、常用的一些小图标。

精灵图有很多优点，但是缺点很明显。

1. 图片文件比较大。
2. 图片本身放大和缩小会失真。
3. 一旦图片制作完毕想要更换非常复杂。

字体图标iconfont的出现很好地解决了以上问题。

字体图标提供一种方便高效的图标使用方式，展示的是图标，本质属于字体。



### 字体图标的优点：

- 轻量级：一个字体图标要比一系列的图像要小，一旦字体加载了，图标就会马上渲染出来，减少了服务器请求
- 灵活性：本质其实是文字，可以很随意的改变颜色、产生阴影、透明效果、旋转等
- 兼容性：几乎支持所有的浏览器

注意：字体图标不能替代精灵技术，只是对工作中图标部分技术的提升和优化。

**总结：**

1.如果遇到一些结构和样式比较简单的小图标，就用字体图标。![image-20210228104339638](https://gitee.com/zhang-xiaoweik/images/raw/master/20210323170150.png)

2.如果遇到一些结构和样式复杂一点的小图标，就用精灵图。![image-20210228104407206](https://gitee.com/zhang-xiaoweik/images/raw/master/20210323170152.png)



字体图标是一些网页常见的小图标，直接网上下载即可。因此使用可以分为：

1.字体图标的下载

2.字体图标的引入（引入到html页面中）

3.字体图标的追加（以后添加新的小图标）



### 字体图标的引入

**step 1**:百度iconfont,找到阿里巴巴矢量图标库官网,然后注册登录,或者用github登录也行,此步骤跳过;

**step 2**:找到图标管理->我的项目->然后新建项目:

![img](https://gitee.com/zhang-xiaoweik/images/raw/master/20210323170155.png)

右边点击新建项目,用于保存自己常用的图标;

![img](https://gitee.com/zhang-xiaoweik/images/raw/master/20210323170158.png)

step 3:项目新建完成后,往项目里添加我们要想使用的图标,找到图标库,搜索一个想要的图标,然后添加到购物车;

![img](https://gitee.com/zhang-xiaoweik/images/raw/master/20210323170200.png)

 

 我现在将第一个安卓图标加入我的项目,点击加入购物车

![img](https://gitee.com/zhang-xiaoweik/images/raw/master/20210323170203.png)

step 4:添加到购物车完成后,购物车徽章数字应该显示1了,点击右上角的购物车图标,选择添加至项目,选择我们刚刚创建的项目,确定;

![img](https://gitee.com/zhang-xiaoweik/images/raw/master/20210323170205.png)

自动跳转到对应的项目里了,如图:

![img](https://gitee.com/zhang-xiaoweik/images/raw/master/20210323170208.png)

step 5:接下来一部比较关键,将打包好的字体文件下载到本地添加到你的项目中,在项目中引用文件中的iconfont.css文件;

![img](https://gitee.com/zhang-xiaoweik/images/raw/master/20210323170210.png)

下载下来解压后的文件如下:

![img](https://gitee.com/zhang-xiaoweik/images/raw/master/20210323170213.png)

**强调一次,把上面这些文件都放在一个文件夹内，然后放在你的项目目录中,再在你的项目中引入iconfont.css文件**

![img](https://gitee.com/zhang-xiaoweik/images/raw/master/20210323170240.png)

 

step 6:到了最后一步了,如何在项目中使用字体图标呢,其实很简单,创建一个i标签或者span标签,添加两个类名,一个固定的是iconfont,另一个是你想要的那个图标对应的类名:

![img](https://gitee.com/zhang-xiaoweik/images/raw/master/20210323170243.png)

具体代码如下:

![img](https://gitee.com/zhang-xiaoweik/images/raw/master/20210323170247.png)

### 字体图标的追加

与引入相同，将所需要的图标都添加到项目后，下载至本地，覆盖之前的文件夹。



## 三角

网页中常见一些三角形，使用CSS直接画出来就可以，不必做成图片或者字体图标。

```css
div {
	width: 0;
	height: 0;
	line-height: 0;  /*line-height和font-size是为了照顾低版本浏览器，高版本可以不写*/
	font-size: 0;
	border: 50px solid transparent;
	border-left-color: pink;
}
```

![image-20210228121637554](https://gitee.com/zhang-xiaoweik/images/raw/master/20210323170258.png)

- 宽高必须为0
- border: 50px solid transparent;会产生一个类似上面的图形，只不过是变成透明的，然后想显示这四块中的左边的三角形，就给border-left-color设置一个颜色，就会只显示这一块三角
- 三角的大小是通过边框粗细控制的



## CSS用户界面样式

所谓的界面样式，就是更改一些用户操作样式，以提高更好的用户体验。

- 更改用户的鼠标样式
- 表单轮廓
- 防止表单拖拽



### 鼠标样式cursor

```css
li {cursor: pointer;}
```

设置或检索在对象上移动的鼠标指针采用何种系统预定义的光标形状。

| 属性值      | 描述       |
| ----------- | ---------- |
| default     | 小白  默认 |
| pointer     | 小手       |
| move        | 移动       |
| text        | 文本       |
| not-allowed | 禁止       |



### 轮廓线outline

给表单添加outline: 0; 或者 outline: none;样式之后，就可以去掉默认的蓝色边框。

```css
input {outline: none;}
```



### 防止拖拽文本域resize

实际开发中，问们文本域右下角是不可以拖拽的。

```css
textarea{ resize: none;}
```

另外，使用textarea标签时，最好不要跨行，不然文本域初始就会有大片空白区域。



## vertical-align属性应用

CSS的vertical-align属性使用场景：经常用于设置图片或者表单（行内块元素）和文字垂直对齐。

官方解释：用于设置一个元素的垂直对齐方式，但是它只针对于行内元素或者行内块元素有效。

语法：

```css
vertical-align : baseline | top | middle | bottom
```

| 值       | 描述                                   |
| -------- | -------------------------------------- |
| baseline | 默认，元素放置在父元素的基线上         |
| top      | 把元素的顶端与行中最高元素的顶端对齐   |
| middle   | 把此元素放置在父元素的中部             |
| bottom   | 把元素的顶端与行中最低的元素的顶端对齐 |

![image-20210228194405396](https://gitee.com/zhang-xiaoweik/images/raw/master/20210323170303.png)



图片、表单都属于行内块元素，默认的vertical-align是基线对齐。

![image-20210228194510237](https://gitee.com/zhang-xiaoweik/images/raw/master/20210323170308.png)

此时可以给图片、表单这些行内块元素的vertical-align属性设置为middle就可以让文字和图片垂直居中对齐了。



### 解决图片底部默认空白缝隙问题

bug:图片底侧会有一个空白缝隙，原因是行内块元素会和文字的基线对齐。

主要解决方法有两种：

1.给图片添加vertical-align: middle | top | bottom等。（提倡使用的）

2.vertical-align只针对行内元素或行内块元素，所以可以把图片转换为块级元素display: block;就不会再与基线对齐



## 溢出的文字省略号显示

1.单行文本溢出显示省略号

必须满足三个条件

```css
/*1.先强制一行内显示文本*/
white-space: nowrap;  (默认normal自动换行)
/*2.超出的部分隐藏*/
overflow: hidden;
/*3.文字用省略号替代超出的部分*/
text-overflow: ellipsis;
```



2.多行文本溢出显示省略号

多行文本溢出显示省略号，有较大兼容性问题，适合于webKit浏览器或移动端（移动端大部分是webkit内核）

```css
overflow: hidden;
text-overflow: ellipsis;
/*弹性伸缩盒子模型显示*/
display: -webkit-box;
/*限制在一个块元素显示的文本的行数*/
-webkit-line-clamp: 2;
/*设置或检索伸缩盒对象的子元素的排列方式*/
-webkit-box-orient: vertical;
```

更推荐后台人员来做这个效果，因为后台人员可以设置显示多少个字，操作更简单。





## 常见布局技巧

### margin负值的运用

当多个盒子紧靠时，相邻两个盒子的相邻边框会看起来更宽

![image-20210304200035616](https://gitee.com/zhang-xiaoweik/images/raw/master/20210323170316.png)

通过margin-left设置一个负的边框粗细，可以使每个盒子都向左移动一个边框粗细的长度，从而使得相邻边框层叠。

如果需要鼠标经过某个盒子的时候，边框换个颜色显示，会出现有一条边框被盖住的问题。这时需要提高当前盒子的层级（如果没有定位则加相对定位，如果有定位，则加z-index）

```html
<style>
    ul li {
        position: relative;
        float: left;
        list-style: none;
        
        width: 200px;
        height: 100px;
        border: 1px solid red;
        margin-left: -1px;
    }
    /* ul li:hover {
        如果盒子没有定位，鼠标经过添加相对定位即可
        position: relative;
        border: 1px solid blue;
    } */
    ul li:hover {
        /* 如果盒子有定位，提高z-index即可 */
        z-index: 1;
        border: 1px solid blue;
    }

</style>
<body>
    <ul>
        <li>1</li>
        <li>2</li>
        <li>3</li>
        <li>4</li>
        <li>5</li>
    </ul>
</body>
```



### 文字围绕浮动元素

![image-20210304201849656](https://gitee.com/zhang-xiaoweik/images/raw/master/20210323170319.png)

要制作上面这种效果，利用浮动元素不会压住文字的特性，不需要一个父盒子里左右两个子盒子，只需要父盒子里有一个子盒子放图片，并且让这个盒子浮动即可。



### 行内块运用

![image-20210304203258517](https://gitee.com/zhang-xiaoweik/images/raw/master/20210323170322.png)

运用行内块可以比较方便的制作上面页面切换的盒子的样式。

```html
<style>
    .box {
        /* 想让这些行内块元素在盒子里居中，只需要给父盒子text-align:center */
        text-align: center;  
    }
    .box a {
        display: inline-block;
        padding: 10px 15px;
        text-decoration: none;
        background-color: #f7f7f7;
        color: black;
        border: 1px solid #ccc;
    }
    
</style>
<body>
    <div class="box">
        <a href="#">&lt;&lt;</a>
        <a href="#">1</a>
        <a href="#">2</a>
        <a href="#">3</a>
        <a href="#">4</a>
        <a href="#">5</a>
        <a href="#">6</a>
        <a href="#">&gt;&gt;</a>
    </div>
</body>
```

效果如下：

![image-20210304205528804](F:\Typora\learn\css.assets\image-20210304205528804.png)



### 三角运用

**原理**

```html
<style>
    .box {
        width: 0;
        height: 0;
        border-top: 50px solid pink;
        border-right: 50px solid skyblue;
        border-bottom: 50px solid blue;
        border-left: 50px solid green;
    }
</style>

<body>
    <div class="box"></div>
</body>
```

上述代码会产生一个如下的图形：

![image-20210306204642588](https://gitee.com/zhang-xiaoweik/images/raw/master/20210323170327.png)

当把border-bottom粗细设置为0，会变化成如下图形：

![image-20210306204751487](https://gitee.com/zhang-xiaoweik/images/raw/master/20210323170330.png)

再接着把border-left粗细设置为0，会变成如下图形：

![image-20210306204857458](https://gitee.com/zhang-xiaoweik/images/raw/master/20210323170333.png)

最后把border-top颜色改为transparent，得到如下三角形：

![image-20210306205022776](https://gitee.com/zhang-xiaoweik/images/raw/master/20210323170335.png)

在这个例子中，三角形的高通过border-top粗细控制，底通过border-right粗细控制。



规范书写：

```css
/*1.只保留右边的边框有颜色*/
border-color:transparent skyblue transparent transparent;
/*2.样式都是solid*/
border-style:solid;
/*3.设置所需要三角形的底和高*/
border-width:50px 50px 0 0;
```



商品折扣价格显示框案例：

```html
<style>
    .price {
        width: 200px;
        height: 24px;
        border: 1px solid red;
        margin: 100px auto;
        line-height: 24px;
        font-size: 14px;

    }

    .miaosha {
    	/*子绝父相，否则小三角会以body为标准定位*/
        position: relative;
        /*利用浮动可以使行内元素获得行内块元素的特性*/
        float: left;
        width: 100px;
        height: 100%;
        background-color: red;
        text-align: center;
        font-weight: 700;
        color: white;
    }

    .miaosha i {
    	/*运用绝对定位摆放小三角*/
        position: absolute;
        right: 0;
        top: 0;
        width: 0;
        height: 0;
        border-color: transparent white transparent transparent;
        border-style: solid;
        border-width: 24px 10px 0 0;
    }

    .origin {
        margin-left: 30px;
        text-decoration: line-through;
        color: #999;
    }
</style>

<body>
    <div class="price">
        <span class='miaosha'>
            ¥1600
            <i></i>
        </span>
        <span class="origin">¥2000</span>
    </div>
</body>
```

效果如下：

![image-20210306220119192](https://gitee.com/zhang-xiaoweik/images/raw/master/20210323170340.png)

（显示有点bug，应该是和边框贴合的，但是网页缩放比例不同时，有的时候会显示贴合，有的时候有几条边没有贴合）



# CSS3新特性

## 新增选择器

### 属性选择器

属性选择器可以根据元素特定属性来选择元素。这样就可以不借助于类或者id选择器。

| 选择符        | 简介                                  |
| ------------- | ------------------------------------- |
| E[att]        | 选择具有att属性的E元素                |
| E[att=“val”]  | 选择具有att属性且属性值等于val的E元素 |
| E[att^=“val”] | 匹配具有att属性且值以val开头的E元素   |
| E[att$=“val”] | 匹配具有att属性且值以val结尾的E元素   |
| E[att*=“val”] | 匹配具有att属性且值中含有val的E元素   |

例如：

```html
<html lang="en">
<head>
    <title>document</title>
    <style>
        /*把具有value属性的input选出来*/
        input[value] {
            color: pink;
        }
    </style>
</head>
<body>
    <input type="text" value="请输入用户名">
    <input type="text">
</body>
</html>
```



==注意：类选择器、属性选择器、伪类选择器权重都是10==



### 结构伪类选择器

结构伪类选择器主要根据==文档结构==来选择元素，常用于根据父级选择里面的子元素。

| 选择符           | 简介                        |
| ---------------- | --------------------------- |
| E:first-child    | 匹配父元素中的第一个子元素E |
| E:last-child     | 匹配父元素中最后一个E元素   |
| E:nth-child(n)   | 匹配父元素中的第n个子元素E  |
| E:first-of-type  | 指定类型E的第一个           |
| E:last-of-type   | 指定类型E的最后一个         |
| E:nth-of-type(n) | 指定类型E的第n个            |



**nth-child(n)**选择某个父元素的一个或多个特定的子元素。

- ==n可以是数字，关键字和公式==
- n如果是数字，就是选择第n个子元素，里面数字从1开始
- n可以是关键字：even偶数，odd奇数
- n可以是公式：常见的公式如下（如果填的是字母n，则从0开始，每次加1往后面计算，相当于选择了所有孩子，超出的部分被忽略）

| 公式 | 取值                           |
| ---- | ------------------------------ |
| 2n   | 偶数                           |
| 2n+1 | 奇数                           |
| 5n   | 5    10    15……                |
| n+5  | 从第5个开始（包括第5个）到最后 |
| -n+5 | 前5个（包括第5个）             |



**nth-child和nth-of-type区别：**

1.nth-child对父元素里面==所有孩子==排序选择。（序号是固定的）先找到第n个孩子，然后看看是否和E的类型匹配。

2.nth-of-type对父元素里面==指定子元素==进行排序选择。先去匹配E，然后再根据E找第n个孩子。

示例：

```
<html lang="en">

<head>
    <title>document</title>
    <style>
        /*1.选择ul里面的第一个孩子 li*/
        ul li:first-child {
            background-color: skyblue;
        }

        /*2.选择ul里面的最后一个孩子 li*/
        ul li:last-child {
            background-color: pink;
        }

        /*3.选择ul里面的第3个孩子 li*/
        ul li:nth-child(3) {
            background-color: pink;
        }
    </style>
</head>

<body>
    <ul>
        <li>我是第1个孩子</li>
        <li>我是第2个孩子</li>
        <li>我是第3个孩子</li>
        <li>我是第4个孩子</li>
        <li>我是第5个孩子</li>
        <li>我是第6个孩子</li>
    </ul>
</body>

</html>
```





### 伪元素选择器（重点）

伪元素选择器可以帮助我们利用CSS创建新标签元素，而不需要HTML标签，从而简化HTML结构。

| 选择符   | 简介                     |
| -------- | ------------------------ |
| ::before | 在元素内部的前面插入内容 |
| ::after  | 在元素内部的后面插入内容 |

注意：

- before和after创建一个元素，但是属于==行内元素==
- 新创建的这个元素在文档树（HTML结构）中是找不到的，所以我们称为伪元素
- 语法：element::before {}
- before和after必须有==content属性==，不需要内容可以设置为content:’’;
- before在父元素内容的前面创建元素，after在父元素内容的后面插入元素
- ==伪元素选择器==和==标签选择器==一样，权重为1



**伪元素应用：**

伪元素字体图标

```html
<html>

<head>
    <title>document</title>
    <link rel="stylesheet" href="../iconfont/iconfont.css">
    <style>
        div {
            position: relative;
            margin: auto;
            width: 200px;
            height: 30px;
            border: 1px solid red;
        }
        div::after {
            position: absolute;
            right: 5px;
            content: '\e65b';
            font-family: 'iconfont';
            font-size: 20px;
            line-height: 30px;
        }
    </style>
</head>

<body>
    <div></div>
</body>

</html>
```

在伪元素中使用阿里巴巴iconfont字体图标，在content的基础上还必须有font-family:’iconfont’;这个写法固定。

content的值就是\\加上&#x后面的e65b。

![image-20210311203130830](https://gitee.com/zhang-xiaoweik/images/raw/master/20210323170349.png)





## CSS3盒子模型

CSS3中可以通过==box-sizing==来指定盒子模型，有两个值：即可指定为==content-box==、==border-box==，这样我们计算盒子大小的方式就发生了改变。



两种情况：

1.box-sizing:content-box    盒子大小为width + padding + border（默认方式）

2.box-sizing:border-box    盒子大小为width



如果盒子模型改为了box-sizing:border-box，那padding和border就不会撑大盒子了（前提padding和border不会超过width宽度）



## 滤镜filter

filter  CSS属性将模糊或颜色偏移等图形效果应用于元素。

```
filter: 函数();   
例如：filter: blur(5px);   blur模糊处理，数值越大越模糊
```



## calc函数

calc()函数能让你在声明CSS属性值时进行一些计算。

```
width:calc(100%-80px);
```

括号里可以使用 + - * / 进行计算。



## 过渡（重点）

过渡（transition）是CSS3中具有颠覆性的特征之一，我们可以在不使用Flash动画或JavaScript的情况下，当元素从一种样式变换为另一种样式时为元素添加效果。

过渡动画：是从一个状态渐渐的过渡到另外一个状态

低版本浏览器不支持（ie9以下版本）但是不影响页面布局。

==经常和:hover一起搭配使用==



**语法：**

```
transition:要过渡的属性 花费时间 运动曲线 何时开始;
```

1.属性：想要变化的css属性，宽高、背景颜色、内外边距都可以。如果想要所有属性都变化过渡，写一个all就可。

2.花费时间：单位是秒（必须写单位），比如0.5s

3.运动曲线：默认是ease（可以省略）

4.何时开始：单位是秒（必须写单位），可以设置延迟触发时间，默认是0s（可以省略）



==哪个元素需要变化就给谁加过渡==



如果需要变化多个属性，可以如下写：

```
div {
	width: 200px;
	height:100px;
	background-color: pink;
	/*多个属性逗号隔开*/
	transition: width .5s,height .5s;
}
div:hover {
	width: 400px;
	height: 200px;
}
```

