#  1.BOM概述

## 1.1什么是BOM

BOM（Browser Object Model）即==浏览器对象模型==，它提供了独立于内容而与==浏览器窗口进行交互的对象==，其核心对象是window。

BOM由一系列相关的对象构成，并且每个对象都提供了很多方法与属性。

BOM缺乏标准，JavaScript语法的标准化组织是ECMA，DOM的标准化组织是W3C，BOM最初是Netscape浏览器标准的一部分。



## 1.2BOM的构成

BOM比DOM更大，它包含DOM。

![image-20210326150409845](https://gitee.com/zhang-xiaoweik/images/raw/master/20210326150416.png)

window对象是浏览器的顶级对象，它具有双重角色。

1.它是JS访问浏览器窗口的一个接口。

2.它是一个全局对象。定义在全局作用域中的变量、函数都会变成window对象的属性和方法。在调用的时候可以省略window，前面学习的对话框都属于window对象方法，如alert()、prompt()等。

==注意：window下的一个特殊属性window.name,声明变量时避开==



# 2.window对象的常见事件

## 2.1窗口加载事件

```
window.onload=function() {}
或者
window.addEventListener("load",function(){});
```

window.onload是窗口（页面）加载事件，当文档内容完全加载完成会触发该事件（包括图像、脚本文件、CSS文件等），就调用的处理函数



注意：

1.有了window.onload就可以把JS代码写到页面元素的上方，因为onload是等页面内容全部加载完毕，再去执行事件处理函数，

2.window.onload传统注册事件方式只能写一次，如果有多个，会以最后一个window.onload为准。





```
document.addEventListener('DOMContentLoaded',function(){})
```

DOMContentLoaded事件触发时，仅当DOM加载完成，不包括样式表，图片、flash等等。

ie9以上支持

如果页面的图片很多的话，从用户访问到onload触发可能需要较长的时间，交互效果就不能实现，必然影响用户的体验，此时用DOMContentLoaded事件比较合适。





## 2.2调整窗口大小事件

```
window.onresize=function(){}
window.addEventListener('resize',function(){})
```

window.onresize是调整窗口大小加载事件，当触发时就调用的处理函数。

注意：

1.只要窗口大小发生变化，就会触发这个事件。

2.我们经常利用这个事件完成响应式布局。window.innerWidth当前窗口宽度。





# 3.定时器

## 3.1两种定时器

- setTimeout()
- setInterval()



## 3.2 setTimeout()定时器

```
window.setTimeout(调用函数,延迟的毫秒数);
```

setTimeout()方法用于设置一个定时器，该定时器在定时器到期后执行调用函数。



注意：

1.window在调用的时候可以省略。

2.延时时间 单位是毫秒，如果不写延时时间，默认为0。

3.定时器可能有很多，所以需要给定时器赋值一个标识符



示例：

```
function callback() {
	console.log('123');
}
var timer1=setTimeout(callback,3000);
var timer2=setTimeout(callback,2000);
```



## 3.3停止setTimeout()  定时器

```
window.clearTimeout(timeoutID)
```

该方法取消了先前通过调用setTimeout()建立的定时器。

window可以省略，里面的参数就是定时器的标识符。



示例：

```html
<html>
<head>
    <title>Document</title>
</head>
<body>
    <button>停止定时器</button>
    <script>
        var btn=document.querySelector('button');
        var timer=setTimeout(function(){
            console.log('123');
        },5000);
        btn.addEventListener('click',function(){
            clearTimeout(timer);
        });
    </script>
</body>
</html>
```



## 3.4setInterval()定时器

```
window.setInterval(回调函数，延迟的毫秒数)
```

该方法重复调用一个函数，每隔这个时间，就去调用一次回调函数。



注意事项与setTimeout相同



**倒计时案例：**

```html
<html>
<head>
    <title>Document</title>
    <style>
        span {
            display: inline-block;
            width: 50px;
            height: 50px;
            background-color: black;
            color:white;
            text-align: center;
            line-height: 50px;
        }
    </style>
</head>
<body>
    <span class="day"></span>
    <span class="hour"></span>
    <span class="minute"></span>
    <span class="second"></span>
    <script>
        var day=document.querySelector('.day');
        var hour=document.querySelector('.hour');
        var minute=document.querySelector('.minute');
        var second=document.querySelector('.second');

        var inputTime=+new Date('2021-3-30 18:00:00');
        countDown();//先调用一次这个函数，防止第一次刷新页面有空白
        //设定定时器
        setInterval(countDown,1000);
        function countDown() {
            var nowTime=+new Date();    //+new返回的就是距离1970.1.1总的毫秒数
            var times=(inputTime-nowTime)/1000;
            var d=parseInt(times/60/60/24);//parseInt取整
            var h=parseInt(times/60/60%24);
            var m=parseInt(times/60%60);
            var s=parseInt(times%60);
            h=h<10?'0'+h:h;
            m=m<10?'0'+m:m;
            s=s<10?'0'+s:s;
            day.innerHTML=d;
            hour.innerHTML=h;
            minute.innerHTML=m;
            second.innerHTML=s;

        }
        
    </script>
</body>
</html>
```



## 3.5停止setInterval()定时器

```
window.clearInterval(intervalID);
```

该方法取消了先前通过调用setInterval()建立的定时器。

注意：

1.window可省略

2.参数就是定时器的标识符





**发送短信按钮案例：**

```html
<html>
<head>
    <title>Document</title>
</head>
<body>
    <button>发送短信</button>
    <script>
        var btn=document.querySelector('button');
        var time=10;
        btn.addEventListener('click',function() {
            btn.disabled=true;
            var timer=setInterval(function(){
                if(time==0){
                    //清除定时器并复原按钮
                    clearInterval(timer);
                    time=10;
                    btn.disabled=false;
                    btn.innerHTML='发送短信';
                }
                else{
                    btn.innerHTML='还剩'+time+'秒';
                    time--;
                }     
            },1000);
        });
    </script>
</body>
</html>
```

