# 1.DOM简介

## 1.1什么是DOM

文档对象模型（Document Object Model，简称DOM），是W3C组织推荐的处理可扩展标记语言的标准==编程接口==。

W3C已经定义了一系列的DOM接口，通过这些DOM接口可以改变网页的内容、结构和样式。



## 1.2DOM树

![image-20210222205432818](https://gitee.com/zhang-xiaoweik/images/raw/master/20210323165815.png)

- 文档：一个页面就是一个文档，DOM中使用document表示
- 元素：页面中的所有标签都是元素，DOM中使用element表示
- 节点：网页中的所有内容都是节点（标签、属性、文本、注释等），DOM中使用node表示

==DOM把以上内容都看做是对象==

# 2.获取元素

## 2.1如何获取页面元素

获取页面中的元素可以使用以下几种方式：

- 根据ID获取
- 根据标签名获取
- 通过HTML5新增的方法获取
- 特殊元素获取

## 2.2根据ID获取

getElementById()可以获取带ID的元素对象

```html
<!DOCTYPE html>
<html>
    <head>
        <meta http-equiv="Content-Type" content="text/html;charset=utf-8">
        <title>learn js</title>
    </head>
    <body>
        <div id='time'>2019-9-9</div>
        <script>
            //文档页面从上往下加载，所以得先有标签，把script写到标签下面
            //返回的是一个元素对象
            var timer=document.getElementById('time');
            //console.dir打印返回的元素对象可以更好地查看属性和方法
            console.dir(timer);
        </script>
    </body>

</html>
```

------

## 2.3根据标签名获取一类元素

getElementsByTagName()返回带有指定标签名的对象集合，以伪数组的形式存储。

```html
<ul>
    <li>知否知否，应是绿肥红瘦</li>
    <li>知否知否，应是绿肥红瘦</li>
    <li>知否知否，应是绿肥红瘦</li>
    <li>知否知否，应是绿肥红瘦</li>
    <li>知否知否，应是绿肥红瘦</li>
</ul> 
<script>
    var lis=document.getElementsByTagName('li');
    console.log(lis);
    console.log(lis[0]);

    for(var i=0;i<lis.length;i++){
        console.log(lis[i]);
    }

</script>
```

运行结果

![image-20210205154429879](https://gitee.com/zhang-xiaoweik/images/raw/master/20210323165810.png)



还可以获取某个父元素指定标签名的子元素。

```
element.getElementsByTagName('标签名');
```

注意：父元素必须是==单个对象==，获取的时候不包括父元素自己。

```html
<body>
    <ul>
        <li>知否知否，应是绿肥红瘦</li>
        <li>知否知否，应是绿肥红瘦</li>
        <li>知否知否，应是绿肥红瘦</li>
        <li>知否知否，应是绿肥红瘦</li>
        <li>知否知否，应是绿肥红瘦</li>
    </ul> 
    <script>
        var lis=document.getElementsByTagName('ul');
        //只有一个ul返回的也是伪数组，必须lis[0]指明单个对象
        console.log(lis[0].getElementsByTagName('li'));
    </script>
</body>
```

------

## 2.4通过H5新增方法

##### 1.getElementsByClassName

```html
document.getElementsByClassName('类名');//根据类名返回元素对象集合
```

##### 2.querySelector

```html
document.querySelector('选择器');//根据指定选择器返回第一个元素对象
```

##### 3.querySelectorAll

```html
document.querySelectorAll('选择器');//根据指定选择器返回所有元素对象的集合(伪数组)
```

```html
<body>
    <div class="box">盒子1</div>
    <div class="box">盒子2</div>
    <div id="nav">
        <ul>
            <li>首页</li>
            <li>产品</li>
        </ul>
    </div>
    <script>
        //1.getElementsByClassName 根据类名获得某些元素集合
        var boxes=document.getElementsByClassName('box');
        console.log(boxes);
        //2.querySelector 返回指定选择器的第一个元素对象
        var firstBox=document.querySelector('.box');
        console.log(firstbox);
        var nav=document.querySelector('#nav');
        console.log(nav);
        var li=document.querySelector('li');
        console.log(li);
        //3.querySelectorAll 返回指定选择器的所有元素对象集合
        var allBox=document.querySelectorAll('.box');
        console.log(allBox);
    </script>
</body>
```

------

## 2.5获取body和html元素

```html
document.body  //返回body元素对象
document.documentElement  //返回html元素对象
```

# 3.事件基础

## 3.1事件概述

JavaScript使我们有能力创建动态页面，而事件是可以被JavaScript侦测到的行为。

网页中的每个元素都可以产生某些可以触发JavaScript的事件，例如，我们可以在用户点击某按钮时产生一个事件，然后去执行某些操作。

## 3.2事件三要素

事件是由三部分组成：事件源、事件类型、事件处理程序。

## 3.3执行事件的步骤

1.获取事件源

2.注册事件（绑定事件）

3.添加事件处理程序（采取函数赋值方式）

```html
<body>
    <div>123</div>
    <script>
        // 执行事件步骤
        // 点击div 控制台输出 我被选中了
        // 1.获取事件源
        var div=document.querySelector('div');
        // 2.绑定事件 注册事件
        // div.onclick
        // 3.添加事件处理程序
        div.onclick=function() {
            console.log('我被选中了');
        }
    </script>
</body>
```



常见的鼠标事件

| 鼠标事件    | 触发条件         |
| ----------- | ---------------- |
| onclick     | 鼠标点击左键触发 |
| onmouseover | 鼠标经过触发     |
| onmouseout  | 鼠标离开触发     |
| onfocus     | 获得鼠标焦点触发 |
| onblur      | 失去鼠标焦点触发 |
| onmousemove | 鼠标移动触发     |
| onmouseup   | 鼠标弹起触发     |
| onmousedown | 鼠标按下触发     |



# 4.操作元素

JavaScript的DOM操作可以改变网页内容、结构和样式，我们可以利用DOM操作元素来改变元素里面的内容、属性等。



## 4.1改变元素内容

```
element.innerText
```

从起始位置到终止位置的内容，但去除html标签，同时空格和换行也会去掉

```
element.innerHTML
```

起始位置到终止位置的全部内容，包括html标签，同时保留空格和换行

- 在获取内容时，innerText会把该元素内的html标签、空格、换行去除，innerHTML会保留html标签、空格和换行。
- 在修改元素内容时，给innerText的字符串中如果含有html标签，该标签不会生效，给innerHTML的字符串中的html会生效。

==innerHTML比较常用==



## 4.2常用元素的属性操作

```
1. innerText、innerHTML 改变元素内容
2. src、href
3. id、alt、title
```

操作分两步：

1.获取元素对象

2.通过==元素对象.属性==修改



## 4.3表单元素的属性操作

利用DOM可以操作如下表单元素的属性：

```
type、value、checked、selected、disabled
```

例如：

```html
<body>
    <button>按钮</button>
    <input type="text" value="输入内容">
    <script>
        var btn=document.querySelector('button');
        var input=document.querySelector('input');
        btn.onclick=function() {
            //表单里面的值 文字内容是通过value来修改的
            input.value='点击了';
            //如果想要某个表单被禁用 不能再点击 disabled
            this.disabled=true;
        }
    </script>
</body>
```



## 4.4样式属性操作

可以通过JS修改元素的大小、颜色、位置等样式。

```
1. element.style      行内样式操作
2. element.className  类名样式操作
```



### 行内样式操作

```html
<style>
    div{
        width: 200px;
        height: 100px;
        background-color: pink;
    } 
</style>
<body>
    <div></div>
    <script>
        var div=document.querySelector('div');
        div.onclick=function () {
            this.style.backgroundColor='purple';
        }
    </script>
</body>
```

1. JS里的样式采取驼峰命名法，比如fontSize、backgroundColor
2. JS修改style样式操作，产生的是行内样式，CSS权重比较高



**文本框显示隐藏内容案例**

```html
<style>
    input {
        color: #999;
    }
</style>
<body>
    <input type="text" value="手机">
    <script>
        var text=document.querySelector('input');
        text.onfocus=function () {
            if(this.value==='手机'){
                this.value='';
            }
            this.style.color='black';
        }
        text.onblur=function (){
            if(this.value===''){
                this.value='手机';
            }
            this.style.color='#999';
        }
    </script>
</body>
```



### 类名样式操作

如果需要修改的样式较多，功能比较复杂，可以通过修改该元素的类名className实现。

例如：

```html
<style>
    .first {
        width: 200px;
        height: 100px;
        background-color: pink;
    }

    .change {
        width: 200px;
        height: 100px;
        background-color: purple;
        margin-top: 100px;
    }
</style>

<body>
    <div class="first"></div>
    <script>
        var div = document.querySelector('div');
        div.onclick = function () {
            //给className赋值会覆盖原类名
            this.className = 'change';
            // //如果需要保留原类名，则使用多类名
            // this.className='change first';
        }
    </script>
</body>
```



**密码框位数判断案例：**

```html
<style>
    .register {
        margin: 200px auto;
        width: 600px;
        padding: 10px;

    }

    .message {
        display: inline-block;
        background: url(../images/举报.png) no-repeat left center;
        /*修改背景图片大小，保持纵横比并缩放成适合该区域的最大大小*/
        background-size: contain;
        font-size: 5px;
        color: #999;
        padding-left: 20px;
    }

    .wrong {
        color: red;
        background-image: url(../images/错.png);
    }

    .right {
        background-image: url(../images/对.png);
    }
</style>

<body>
    <div class="register">
        <input type="password" class="ipt">
        <p class="message">请输入6~16位密码</p>
    </div>
    <script>
        var ipt = document.querySelector('.ipt');
        var message = document.querySelector('.message');
        ipt.onblur = function () {
            if (this.value.length < 6 || this.value.length > 16) {
                message.className = 'message wrong';
                message.innerHTML = '您输入的位数不对，请输入6~16位密码';
            }
            else {
                message.className = 'message right';
                //p标签内容如果单打个空格会当作没有内容，需要使用转义字符
                //修改内容时，innerText不会识别转义字符，需要使用innerHTML
                message.innerHTML = '&nbsp';
            }
        }

    </script>
</body>
```



**换肤案例:**

```html
<html>

<head>
    <title>document</title>
    <style>
        * {
            margin: 0;
            padding: 0;
        }

        body {
            background: url('../images/wallhaven-48kldo_1920x1080.png') no-repeat center center;
            /*背景图片保持纵横比并缩放成完全覆盖背景定位区域的最小大小*/
            background-size: cover;
        }

        .change {
            margin: 200px auto;
            /*清除浮动带来的影响*/
            overflow: hidden;
            width: 410px;
            background-color: pink;
            padding: 2px;

        }

        .change li {
            list-style: none;
            float: left;
            margin: 0 1px;

        }

        .change img {
            width: 100px;
            cursor: pointer;
            /*把img行内块元素放置在父元素的中间（垂直居中）*/
            vertical-align: middle;
        }
    </style>
</head>

<body>
    <ul class="change">
        <li><img src="../images/wallhaven-48kldo_1920x1080.png" alt=""></li>
        <li><img src="../images/wallhaven-6kgez6_1920x1080.png" alt=""></li>
        <li><img src="../images/wallhaven-j33eoy_1920x1080.png" alt=""></li>
        <li><img src="../images/wallhaven-j8yxg5_1920x1080.png" alt=""></li>
    </ul>

    <script>
        /*获取.change下的所有img*/
        var imgs = document.querySelector('.change').querySelectorAll('img');
        for (var i = 0; i < imgs.length; i++) {
            imgs[i].onclick = function () {
                document.body.style.backgroundImage = 'url(' + this.src + ')';
            }

        }
    </script>
</body>

</html>
```



**表单全选案例：**

```html
<html>

<head>
    <title>Document</title>
    <style>
        .table {
            /*将表格边框合并为单一边框*/
            border-collapse: collapse;
            margin: 100px auto;
        }

        .table,
        th,
        td {
            border: 1px solid gray;
            padding: 10px;
        }

        thead {
            background-color: skyblue;
            color: white;
        }
    </style>

</head>

<body>
    <table class="table">
        <thead>
            <tr>
                <th><input type="checkbox" id="j_cbAll"></th>
                <th>商品</th>
                <th>价钱</th>
            </tr>
        </thead>
        <tbody id="j_tbs">
            <tr>
                <td><input type="checkbox" name="choose"></td>
                <td>iPhone8</td>
                <td>8000</td>
            </tr>
            <tr>
                <td><input type="checkbox" name="choose"></td>
                <td>iPad Pro</td>
                <td>5000</td>
            </tr>
            <tr>
                <td><input type="checkbox" name="choose"></td>
                <td>iPad Air</td>
                <td>2000</td>
            </tr>
            <tr>
                <td><input type="checkbox" name="choose"></td>
                <td>Apple Watch</td>
                <td>2000</td>
            </tr>
        </tbody>
    </table>

    <script>
        var j_cbAll = document.getElementById('j_cbAll');//获取全选框
        var j_tbs = document.getElementById('j_tbs').getElementsByTagName('input');//获取tbody内的所有复选框
        //1.点击全选则全部选中或全部不选中
        j_cbAll.onclick = function () {
            for (var i = 0; i < j_tbs.length; i++) {
                /*把下面复选框的checked属性与全选框挂钩*/
                j_tbs[i].checked = this.checked;
            }
        }
        //2.下面复选框全部选中时，上面全选自动选中

        for (var i = 0; i < j_tbs.length; i++) {
            j_tbs[i].onclick = function () {
                //flag表示复选框是否全部选中
                var flag = true;
                //每次点击下面的一个复选框都要检查是否下面的复选框全都被选中
                for (var i = 0; i < j_tbs.length; i++) {
                    if (!j_tbs[i].checked) {
                        flag = false;
                        //如果该次点击时已有未选复选框，则没必要判断后续的复选框是否选中
                        break;
                    }
                }
                j_cbAll.checked = flag;
            }
        }

    </script>

</body>

</html>
```



## 4.5操作元素总结

![image-20210306145144356](https://gitee.com/zhang-xiaoweik/images/raw/master/20210323165752.png)



## 4.6自定义属性的操作

**1.获取属性值**

```
element.属性	获取属性值
element.getAttribute(‘属性’);
```



**区别：**

- element.属性	获取内置属性值
- element.getAttribute(‘属性’)    获取自定义属性



**2.设置属性值**

```
element.属性=‘值’	设置内置属性值
element.setAttribute(‘属性’,‘值’);
```



**区别:**

- element.属性	设置内置属性值
- element.setAttribute(‘属性’ , ‘值’);	主要设置自定义的属性



**注意**：

```
element.setAttribute('class','类名')  //class特殊，写的就是class，不是className
```



**3.移除属性**

```
element.removeAttribute(‘属性’);
```

  

## 4.7 H5自定义属性

==自定义属性目的：是为了保存并使用数据。有些数据可以保存到页面中而不用保存到数据库中。==

自定义属性获取是通过getAttribute(‘属性’)获取。

但是有些自定义属性很容易引起歧义，不容易判断是元素的内置属性还是自定义属性.



**1.设置H5自定义属性**

H5规定自定义属性==data-==开头作为属性名并赋值。

比如：

```
<div data-index="1"></div>
或者使用JS设置
element.setAttribute('data-index',2)
```



**2.获取自定义属性**

两种方法：element.getAttribute和element.dataset

具体使用如下：

```html
<html>
<head>
    <title>Document</title>
</head>
<body>
    <div data-index="2" data-list-name="andy"></div>
    <script>
        var div=document.querySelector('div');
        console.log(div.getAttribute('data-index'));
        console.log(div.getAttribute('data-list-name'));

        //dataset是一个集合里面存放了所有以data开头的自定义属性
        console.log(div.dataset);
        console.log(div.dataset['index']);
        //如果自定义属性里面又多个-链接的单词，获取的时候采取驼峰命名法
        console.log(div.dataset.listName);
        console.log(div.dataset['listName']);
    </script>
</body>
</html>
```

建议使用getAttribute，兼容性比较好





# 5.节点操作

## 5.2节点概述

一般地，节点至少拥有nodeType（节点类型）、nodeName（节点名称）和nodeValue（节点值）这三个基本属性。



- 元素节点nodeType为1
- 属性节点nodeType为2
- 文本节点nodeType为3（文本节点包含文字、空格、换行等）

==在实际开发中，节点操作主要操作的是元素节点==



## 5.3节点层级

利用DOM树可以把节点划分为不同的层级关系，常见的是==父子兄层级关系==



### 1.父级节点

```
node.parentNode
```

parentNode属性可返回某节点的父节点，注意是==最近的一个父节点==。

如果指定的节点没有父节点则返回null。

例如：

```
var ul=document.querySelector('ul');
console.log(ul.parentNode);
```



### 2.子节点

```
1.parentNode.childNodes(标准)
```

parentNode.childNodes返回包含指定节点的子节点的集合，该集合为及时更新的集合。

==注意：==

==返回值里面包含了所有的子节点，包括元素节点，文本节点等。==

==如果只想要获得里面的元素节点，则需要专门处理。所以一般不提倡使用childNodes==

```
var ul=document.querySelector('ul');
for(var i=0;i<ul.childNodes.length;i++){
	if(ul.childNodes[i].nodeType==1){
		//ul.childNodes[i]是元素节点
		console.log(ul.childNodes[i]);
	}
}
```



```
2. parentNode.children(非标准)
```

parentNode.children是一个只读属性，返回所有的子元素节点，它只返回子元素节点，其余节点不返回（==这个是重点掌握的==）

虽然children是一个非标准，但是得到了各个浏览器的支持，因此我们可以放心使用。



```
3. parentNode.firstChilld
```

firstChild返回第一个子节点，找不到则返回null。同样，也是包含所有节点。

```
4. parentNode.lastChild
```



```
5. parentNode.firstElementChild
```

firstElementChild返回第一个子元素节点，找不到则返回null。

```
6. parentNode.lastElementChild
```

lastElementChild返回最后一个子元素节点，找不到则返回null。

==注意：这两个方法有兼容性问题，IE9以上才支持。==



实际开发中，想要返回第一个子元素或者最后一个子元素写法如下：

```
parentNode.children[0]
parentNode.children[ul.children.length-1]
```



**下拉菜单案例**

```html
<html>
<head>
    <title>Document</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            font-size: 15px;
        }
        li {
            list-style: none;
        }
        a {
            text-decoration: none;
            color: black;
        }

        .nav {
            width: 400px;
            margin: 0 auto;
            overflow: hidden;
        }
        .nav>li {
            float: left;
            padding: 10px;
        }
        .nav>li>a{
            display: block;
            padding: 10px;
            text-align: center;
        }
        .nav>li>a:hover{
            background-color: #eee;
        }
        .nav ul>li{
            padding: 10px;
            border: 1px solid orange;
            border-top: 0;
        }
    </style>
</head>
<body>
    <ul class="nav">
        <li>
            <a href="#">微博</a>
            <ul>
                <li><a href="#">私信</a></li>
                <li><a href="#">评论</a></li>
                <li><a href="#">@我</a></li>
            </ul>
        </li>
        <li>
            <a href="#">微博</a>
            <ul>
                <li><a href="#">私信</a></li>
                <li><a href="#">评论</a></li>
                <li><a href="#">@我</a></li>
            </ul>
        </li>
        <li>
            <a href="#">微博</a>
            <ul>
                <li><a href="#">私信</a></li>
                <li><a href="#">评论</a></li>
                <li><a href="#">@我</a></li>
            </ul>
        </li>
        <li>
            <a href="#">微博</a>
            <ul>
                <li><a href="#">私信</a></li>
                <li><a href="#">评论</a></li>
                <li><a href="#">@我</a></li>
            </ul>
        </li>
    </ul>
    <script>
        var nav=document.querySelector('.nav');
        var lis=nav.children;//得到四个小li
        for(var i=0;i<lis.length;i++){
            lis[i].onmouseover=function() {
                //四个小li内有两个元素节点，第二个是ul
                this.children[1].style.display='block';
            }
            lis[i].onmouseout=function() {
                this.children[1].style.display='none';
            }
        }
    </script>
</body>
    
</html>
```



### 3.兄弟节点

```
1. node.nextSibling
```

nextSibling返回当前元素的下一个兄弟节点，找不到则返回null。同样，也是包含所有的节点。

```
2. node.previousSibling
```

previousSibling返回当前元素上一个兄弟节点，找不到则返回null。包含所有节点。



```
3. node.nextElementSibling
```

nextElementSibling返回当前元素下一个兄弟元素节点，找不到则返回null。

```
4. node.previousElementSibling
```

previousElementSibling返回当前元素上一个兄弟元素节点，找不到则返回null。

==注意：这两个方法有兼容性问题，IE9以上才支持。==



要解决兼容性问题，可以自己封装一个兼容性的函数。

```
function getNextElementSibling(element) {
	var el = element;
	while(el=el.nextSibling) {
		if(el.nodeType===1){
			return el;
		}
	}
	return null;
}
```





## 5.4创建节点

```
document.createElement('tagName')
```

该方法创建由tagName指定的HTML元素。因为这些元素原先不存在，是根据需求动态生成的，所以也称为==动态创建元素节点==。



### 添加节点

```
1. node.appendChild(child)
```

node.appendChild()方法将一个节点添加到指定父节点的子节点列表==末尾==。类似于css里面的after伪元素。

其中：node是父级，child是子级。



```
2. node.insertBefore(child,指定元素)
```

该方法将一个节点添加到父节点指定子节点前面。



使用案例：

```html
<html>
<head>
    <title>Document</title>
</head>
<body>
    <ul>
        <li>123</li>
    </ul>
    <script>
        //创建元素节点
        var li=document.createElement('li');
        var ul=document.querySelector('ul');
        //添加节点
        ul.appendChild(li);
        //创建一个元素节点并添加到原有的li前面
        var lili=document.createElement('li');
        ul.insertBefore(lili,ul.children[0]);
    </script>
</body>
</html>
```





## 5.5删除节点

```
node.removeChild(child)
```

node.removeChild()方法从DOM中删除一个子节点，返回删除的节点。



比如：

```
var ul=document.querySelector('ul');
ul.removeChild(ul.children[0]);
```



**发布和删除留言案例：**

```html
<html>
<head>
    <title>Document</title>
    <style>
        ul {
            width: 200px;
        }
        ul a {
            float: right;
        }
    </style>
</head>
<body>
    <textarea name="" id="" cols="30" rows="10"></textarea>
    <input type="button" value="发布">
    <ul>
        <li>123</li>
    </ul>
    <script>
        var ul=document.querySelector('ul');
        var text=document.querySelector('textarea');
        var btn=document.querySelector('input');
        btn.onclick=function() {
            if(text.value==''){
                alert('您没有输入内容');
                return false;
            }
            else{
                var lili=document.createElement('li');
                ul.insertBefore(lili,ul.children[0]);
                lili.innerHTML=text.value+"<a href='javascript:;'>删除</a>";
                text.value='';
                var del=document.querySelector('ul').querySelectorAll('a');
                for(var i=0;i<del.length;i++){
                    del[i].onclick=function() {
                        //删除当前a的父元素li
                        ul.removeChild(this.parentNode);
                    }
                }
            }            
        }
    </script>
</body>
</html>
```

阻止链接html跳转需要添加javascript:void(0);或者javascript:;



## 5.6复制节点


