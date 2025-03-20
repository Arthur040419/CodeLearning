# JavaWeb知识笔记

参考视频：[05-DDL-操作数据库_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1Qf4y1T7Hx?spm_id_from=333.788.player.switch&vd_source=f3cb3ea986b26c6910b4df6d37acd60d&p=6)

2025年3月7日回来复习JavaWeb，参考视频：[全网首发AI+JavaWeb开发入门，Tlias教学管理系统项目实战全套视频教程，从需求分析、设计、前后端开发、测试、程序优化到项目部署一套搞定_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1yGydYEE3H/?spm_id_from=333.788.video.desc.click&vd_source=f3cb3ea986b26c6910b4df6d37acd60d)

中间换教程了：[Day01-10. HTML-新浪新闻-实现正文-布局_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1m84y1w7Tb?vd_source=f3cb3ea986b26c6910b4df6d37acd60d&spm_id_from=333.788.videopod.episodes&p=11)

前面那个AI+javaweb的感觉不大好，它用AI生成代码，感觉很烦，而且用AI生成也不利于学习，所以换教程了

笔记就在原来的基础上进行修改



# HTML-CSS

## 02.Web前端开发初识

### 什么是Web标准

Web标准也称网页标准，由W3C（World Wide Web 万维网联盟）制定。

Web标准有三个组成部分：

1.HTML，负责页面的结构（页面的元素及内容等）

2.CSS，负责页面的表现（颜色，大小等）

3.Javascript，负责网页的行为（交互效果）





### 什么是HTML

HTML是HyperText Markup Language的缩写，意为超文本标记语言

超文本：意为超越了文本的限制，超文本不仅能够记录文字还能够定义视频，图片，音频等内容

标记语言：标记语言是由标签构成的语言，标签是提前定义好的，需要浏览器进行解析



### 什么是CSS

CSS是Cascading Style Sheet的缩写，意为层叠样式表，用于控制页面的样式





## 03.HTML-CSS-入门程序

### HTML的基本框架

html的标签不区分大小写

```html
<html>
    <head>
        <!--head标签内的内容是给浏览器看的-->
        <!--浏览器会解析head标签的内容，如下面的title标签，会被展示到页面标签的标题上-->
        <title>页面标题</title>
    </head>
    <body>
        <!--body标签的内容是给用户看的，也就是说这部分的内容会被解析到页面主体中，我们期望给用户看的内容就放在这里-->
        <h1>
            hello HTML
        </h1>
        <img src="图片路径">	<!--属性值可以用单引号也可以用双引号-->
    </body>
</html>
```



## 04.HTML-CSS-VsCode开发工具

### VsCode的使用

下载安装就省略了

输入`!`即可快捷编写HTML的统一框架

![image-20250307094826008](./pictures/image-20250307094826008.png)



解释一下这个快速模板的含义

```html
<!-- 下面的代码用于声明文件类型 -->
<!DOCTYPE html>
<html lang="en">
<head>
    <!-- 声明字符集 -->
    <meta charset="UTF-8">
    <!-- 设置当前网页在移动端的缩放比例 -->
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    
</body>
</html>
```



## 05.HTML-CSS-常见标签和样式-央视新闻-标题-排版

### 完成央视新闻页面的标题排版

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>【新思想引领新征程】推进长江十年禁渔 谱写长江大保护新篇章</title>
</head>
<body>
    <!-- 使用一个h1标签定义一个标题 -->
    <h1>【新思想引领新征程】推进长江十年禁渔 谱写长江大保护新篇章</h1>

    <!-- 使用一个a标签定义一个超链接-->
    <!-- 超链接的属性target代表跳转网页的打开方式
         _blank代表在新窗口中打开网页
         _self代表在当前窗口中打开网页
         默认为_self -->
     <a href="https://www.cctv.com/" target="_blank">央视网</a>
</body>
</html>
```



## 06.HTML-CSS-常见标签和样式-央视新闻-标题-样式

### 引入CSS的三种方式

#### 1.行内样式

直接在标签内定义CSS属性就是行内样式

```html
<!--行内样式的示例如下，style后面的就是样式-->
<a style="color:gray">行内样式</a>
```



#### 2.内部样式

将样式定义在`<style>`标签内的样式叫内部样式

```html
<style>
    /*内部样式*/
    a{
        color:gray;				
    }
</style>
```



#### 3.外部样式

将css样式单独写在一个`.css`文件中，页面如果要使用样式需要使用`<link>`标签引入`.css`文件

```css
/*css文件*/
a{
    color:gray
}
```

```html
<!--引入css文件,href后面接文件的路径-->
<link rel="stylesheet" href="css/news.css">
```



### css样式选择器

如果想要限定样式的作用范围，如：只想让样式在a标签起作用，就要用到css样式选择器

css的样式选择器有以下几种，重点关注前三个

![image-20250307134502558](./pictures/image-20250307134502558.png)

如果三个选择器同时匹配到一个标签，那么优先生效的是id选择器，其次是类选择器，最后才是元素选择器

### css颜色的表示方式

#### 1.关键字

直接使用例如：red、green、gray等颜色关键字

#### 2.rgb表示法

rgb表示法如下

```html
rgb(r,g,b)		r代表红色，g代表绿色，b代表蓝色，取值范围0-255
```

#### 3.rgba表示法

在rgb表示法的基础上多引入了一个属性值a，a代表透明度，取值范围0-1，0表示完全透明，1表示完全不透明

#### 4.十六进制表示法

```html
#rrggbb		#开头，rr表示红色，gg表示绿色，bb表示蓝色，和rgb表示法类似，不过是将0-255变成用16进制表示
```



### 完成央视新闻页面的标题样式

```html
<!-- 学会使用css的三种方式 -->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>【新思想引领新征程】推进长江十年禁渔 谱写长江大保护新篇章</title>

    <!-- 方式二，内部样式 -->
     <style>

        span{
            color:gray;
        }
        
        /* 去除超链接的下划线 */
        a{
            text-decoration: none;
        }
     </style>

     <!-- 方式三，外部样式 -->
      <!-- rel="stylesheet"代表引入的是css文件 -->
      <!-- href="css/news.css"代表引入的css文件的路径 -->
     <!-- <link rel="stylesheet",href="css/news.css"> -->
</head>
<body>
    <h1>【新思想引领新征程】推进长江十年禁渔 谱写长江大保护新篇章</h1>
     <a href="https://www.cctv.com/" target="_blank">央视网</a>
    
    
     <!-- span标签是没有语义的，它的作用是为了让文字具有某种样式
     比如让文字加粗，让文字倾斜，让文字变大等等
     比如让文字变成红色，让文字变成蓝色等等 -->
     <!-- 方式一，行内样式 -->
    <!-- <span style="color:gray">2024年05月15日 20:07</span> -->
    
    <span>2024年05月15日 20:07</span>
    
</body>
</html>
```



## 08.HTML-CSS-常见标签和样式-央视新闻-正文-排版

### 在html页面中引入视频、音频

使用`<video>`引入视频，使用`<audio>`引入音频

```html
<!-- 在页面中引入视频、音频等多媒体文件 -->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>【新思想引领新征程】推进长江十年禁渔 谱写长江大保护新篇章</title>

     <style>

        span{
            color:gray;
        }       
        a{
            text-decoration: none;
        }
     </style>

</head>
<body>
    <h1>【新思想引领新征程】推进长江十年禁渔 谱写长江大保护新篇章</h1>
     <a href="https://www.cctv.com/" target="_blank">央视网</a>
    <span> 2024年05月15日 20:07</span>
    <br>
    
    <!-- 使用video标签引入视频文件 -->
     <!--video标签的属性：
        src:视频文件的路径
        controls:显示视频的控制条
        autoplay:自动播放
        width:视频的宽度
        height:视频的高度
          单位：px：像素
                %：百分比 相对于父级元素的百分比
-->
     <video src="video/Overwatch 2 2025.01.08 - 11.46.00.01.mp4" controls width="80%"></video>
</body>
</html>
```



### 实现文本加粗显示

使用`<b>`标签或`<strong>`标签实现文本加粗显示



## 09.HTML-CSS-常见标签和样式-央视新闻-正文-样式

### 设置行高

使用css的`line-height`设置行高

### 实现每段首行缩进

使用css的`text-indent`设置首行缩进





## Day01-10.HTML-新浪新闻-实现正文-布局

### css盒子模型

页面中的所有元素都可以看成是由一个盒子包含在一个矩形区域内的

盒子模型由四个部分组成：内容区域(content)、内边距区域(padding)、边框区域(border)、外边距区域(margin)

一块内容部分指的是:content、padding、border三部分，盒子是不包含margin的

它们的组成如下图所示

![image-20250307154446455](./pictures/image-20250307154446455.png)

盒子部分的css设置如下

```html
<style>
    div{
        width:200px;
        height:200px;		/*默认指的是内容的长宽*/
        box-sizing:border-box;		/*指定height、width为盒子的长宽*/
        
        
        padding:20px 20px 20px 20px;	/*按顺序依次为，上右下左*/
        border:10px solid red;			/*依次为：边框线条宽度，线条类型，线条颜色*/
        margin:30px;					/*设置方式与padding一致，如果只有一个参数代表上下右左都是一样的*/
    }
</style>
```



### div和span标签

![image-20250307154601673](./pictures/image-20250307154601673.png)



## Day01-11.HTML-表格标签

### 表格标签

html有如下表格标签来制作表格

![image-20250307161448199](./pictures/image-20250307161448199.png)

表格制作示例

```html
<!-- 制作一个表格 -->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <table border="1px" cellspacing="0" width="600px">
        <tr>
            <!--表头-->
            <th>序号</th>
            <th>品牌logo</th>
            <th>品牌名称</th>
            <th>企业名称</th>
        </tr>
        <tr>
            <td>1</td>
            <td><img src="picture/呆呆雾子.jpg"></td>
            <td>华为</td>
            <td>华为</td>
        </tr>
        <tr>
            <td>2</td>
            <td><img src="picture/比心雾子.gif"></td>
            <td>阿里</td>
            <td>阿里巴巴</td>
        </tr>
    </table>
</body>
</html>
```



## Day01-12.HTML-表单标签

### 表单标签及其属性

![image-20250307162603678](./pictures/image-20250307162603678.png)

表单定义示例如下

```html
<!-- 创建一个form表单 -->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <!-- 表单的属性
        action表示表单数据的发送目的地址
        method表示表单请求方式是get还是post
        如果请求方式为get，表单数据会放在请求url后面，使用get传输的数据是有大小限制的，表单默认请求方式是get
        如果请求方式为post，表单数据会放在请求体中，使用post传输数据没有大小限制
    -->
    <form action="" method="get">
        用户名:
        <!-- name属性用来标识输入数据 -->
        <input type="text" name="username">
        年龄:
        <input type="text" name="age">
        
        <input type="submit" value="提交">
    </form>
</body>
</html>
```



## Day01-13.HTML-表单项标签

### 表单项标签及其属性

![image-20250307163805377](./pictures/image-20250307163805377.png)

![image-20250307163815922](./pictures/image-20250307163815922.png)



# JS

## Day02-01.JS-介绍

### 什么是JavaScript

JavaScript是一门跨平台、面向对象的脚本语言（脚本语言指的是用js编写的程序不用经过编译即可被浏览器直接运行）。

JavaScript是用来控制网页行为的，用来实现网页的交互。





## Day02-02.JS-引入方式

### JS的引入方式

JS有两种引入方式

#### 1.内部脚本

内部脚本指的是可以在html文件的任意位置定义js代码，js代码要放在`<script>`标签内

```html
<script>
    具体的js代码
</script>
```

一般会把js代码放在body元素的底部，这样可以改善显示速度



#### 2.外部脚本

外部脚本指的是将js代码单独写在一个`.js`文件中，并使用`<script src=""></script>`来引入，注意`<script>`标签不能自闭和。



```html
<!-- JS的两种引入方式 -->
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>JS的两种引入方式</title>
</head>

<body>
    <h1>JS的两种引入方式</h1>
    <!-- 内部脚本 -->
    <script>
        alert('Hello JS');
    </script>

    <!-- 外部脚本 -->
     <script src="JS/JSDemo.js"></script>
</body>

</html>
```



## Day02-03.JS-基础语法-书写语法

### JS的书写语法

1.JS区分大小写

2.JS每行代码的结尾分号`;`可有可无

3.JS的注释方式与Java一致，`//`表是单行注释，`/**/`表示多行注释



### JS的输出语句

JS有以下三种输出语句

#### 1.通过浏览器弹出提示框

```js
window.alert("Hello JS");
//前面的window.可以省略
alert("Hello JS");
```

#### 2.直接输出到html页面

```js
//直接将数据输出到html页面
document.write("Hello JS");
```

#### 3.输出到浏览器控制台

```js
//将数据输出到浏览器控制台
console.log("Hello JS");
```



```html
<!-- JS的三种输出方式 -->
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>JS的三种输出方式</title>
</head>

<body>
    <h1>JS的三种输出方式</h1>
    <!-- 1.通过浏览器弹窗输出 -->
    <script>
        window.alert("Hello JS");
        //也可以省略window.
        alert("Hello JS");
    </script>

    <!-- 2.输出到html页面 -->
    <script>
        document.write("Hello JS");
    </script>

    <!-- 3.输出到浏览器控制台 -->
    <script>
        console.log("Hello JS");
    </script>
</body>

</html>
```



## Day02-04.JS-基础语法-变量

### JS的变量

JS中使用var来声明一个变量。

变量的命名规则和Java一致，不能用数字开头，变量字符只能由字母、数字、下划线(_)、美元符($)组成。

JS是一个弱类型的语言，一个变量可以存放不同类型的数据。

JS中的变量也可以重复定义，重复定义会覆盖原来的定义



ECMAScript6 新增了let和const

let和var类似，也是用来定义变量的，只不过，let定义的变量是局部变量，且let定义的变量不能重复定义

const用来声明一个只读常量，const声明的变量不能被修改。

```html
<!-- JS的变量 -->
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>JS的变量</title>
</head>

<body>
    <script>
        var a = 1;
        //js是弱类型语言，一个变量可以存放不同类型的数据
        a = "张三";
        alert(a);

        {
            //var定义的是全局变量，就算在某个代码块中定义，在代码块外也能够被访问
            var b = 10;
        }
        // 访问其他代码块中定义的变量
        alert(b);

        //var定义的变量也可以重复定义，重复定义会覆盖原来的定义
        var a = "Arthur";
        alert(a);

        {
            let c = 30;

            //不能重复定义let的变量,下面的代码会报错
            // let c = 888;
        }
        // 外部无法访问到局部变量c，下面的代码浏览器运行时会报错
        alert(c);

        const pi = 3.14;
        // const声明的变量不能被修改，下面的代码在运行时浏览器会报错
        pi=3.15;
        alert(pi);
    </script>
</body>

</html>
```



## Day02-05.JS-基础语法-数据类型&运算符

### JS的数据类型

JS虽然是弱类型的语言，但是它还是有数据类型的，JS的数据类型分为原始类型、引用类型。使用`typeof`运算符可以获取变量的类型

原始类型包括

![image-20250308193359111](./pictures/image-20250308193359111.png)

```html
<!-- JS的数据类型 -->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>JS的数据类型</title>
</head>
<body>
    <script>
        // 不管是整数还是小数在JS中都是number类型
        alert(typeof 3);        //number
        alert(typeof 3.14);     //number

        // 不管是字符还是字符串都是String类型,且声明的时候双引号单引号都能用
        alert(typeof "a");          //string
        alert(typeof "abcdefg")     //string

        alert(typeof true);         //boolean
        alert(typeof false);

        // null可以认为是Object的占位符
        alert(typeof null);         //Object

        //如果变量未初始化，那么该变量的类型为undefined
        var a;
        alert(typeof a);            //undefined


    </script>
</body>
</html>
```



### JS的运算符

JS中的运算符基本与Javar一致，如下，唯一不同之处在于JS有一个`===`运算符

![image-20250308194237351](./pictures/image-20250308194237351.png)

`==`与`===`的区别在于：`==`在判断两个数据是否一致时如果发现数据类型不一样会先转换数据类型，而`===`在比较时，如果发现数据类型不一样会直接返回false，不会进行数据转换。

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <script>
        var a = 10;
        alert(a=="10");     //返回true，会先将字符串"10"转换成数字10
        alert(a==="10");    //返回false，发现两个数据类型不一致，直接返回false，不会进行类型转换
        alert(a===10);      //返回true，数据类型一致，且值相同，返回true
    </script>

</body>
</html>
```



### JS的数据类型转换

JS中的数据类型转换分为以下两种情况

使用方法`parseInt`和`parseFloat`来将字符串转换为数字

其中NaN属于number类型，意为not a number

![image-20250308195053380](./pictures/image-20250308195053380.png)

```html
<!-- JS的数据类型转换 -->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <script>
        // 字符串转换为数字
        alert(parseInt("12"));      //12
        alert(parseInt("12A21"));   //12，如果一个字符串中间有非数字，就只会将前面的所有数字转换为数字
        alert(parseInt("A21"));     //NaN，如果第一个字符为非数字，就直接返回NaN，毕竟前面也没数字嘛
        alert(parseFloat("3.14"));      //3.14
        alert(parseFloat("3.14.21"));   //3.14

        //其他类型转换为boolean类型
        //1.number转换为boolean类型，number中只有0和NaN，即使是负数也是转换为true
        if(0){
            //这行代码执行不到
            alert("0转换成false");
        }        
        if(NaN){
            //这行代码执行不到
            alert("NaN转换成false");
        }
        if(1){
            //这行代码会被执行
            alert("除了0和NaN，其他数字都转换为true")
        }
        if(-1){
            //这行代码会被执行
            alert("即使是负数也是转换成true")
        }

        //2.string类型转换为boolean类型,只有空字符串为false，其他均为true，即使字符串全是空格
        if(""){
            //这行代码执行不到
            alert("空字符串为false")
        }
        if(" "){
            //这行代码会被执行
            alert("非空字符串为true")
        }

        //3.Null和undefined均转换为false
        if(null){
            //这行代码执行不到
            alert("null为false")
        }
        if(undefined){
            //这行代码执行不到
            alert("undefined为false")
        }



    </script>

</body>
</html>
```



### JS的流程控制

JS的流程控制语句的语法和Java一致

![image-20250308200515823](./pictures/image-20250308200515823.png)





## Day02-06.JS-函数

### JS中的函数

#### 函数定义方式1

![image-20250308200907257](./pictures/image-20250308200907257.png)

```html
<!-- JS函数 -->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>JS函数</title>
</head>
<body>
    <script>
        // 定义函数
        function add(a,b){
            return a+b;
        }
        //调用函数
        var result = add(10,20);
        alert(result);

    </script>
</body>
</html>
```



#### 函数定义方式2

![image-20250308201314993](./pictures/image-20250308201314993.png)

```html
<!-- JS函数 -->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>JS函数</title>
</head>
<body>
    <script>
        // 定义函数
        var add = function(a,b){
            return a+b;
        }
        //调用函数
        var result = add(10,20);
        alert(result);

    </script>
</body>
</html> 
```





## Day02-07.JS-对象-Array数组

### JS中的数组

Array时JS当中的数组对象

![image-20250308202827654](./pictures/image-20250308202827654.png)



```html
<!-- JS中的数组 -->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <script>
        // 创建数组
        var arr1 = new Array(1,2,3,4);
        //可以简化
        var arr2=[1,2,3,4,5];

        /* JS的数组很像Java的集合,有如下特点
            1.长度可变
            2.类型可变
        */

       /* 长度可变，虽然创建的数组长度为4，但是可以直接访问索引为10的元素,
            其他索引9，8，7这些没被初始化的就为undefined */
       arr1[10]=10;
       console.log(arr1[10]);       //10
       console.log(arr1[9]);        //undefined
       
       /* 类型可变，可以为JS的数组添加任意类型的数据 */
       arr1[1]=3.14;
       arr1[2]="字符串";
       console.log(arr1[1]);        //3.14
       console.log(arr1[2]);        //字符串
       
    </script>
</body>
</html>
```



### JS中Array对象的属性及方法 

![image-20250308203458575](./pictures/image-20250308203458575.png)



```html
<!-- JS中的数组 -->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <script>
        // 创建数组
        var arr1 = new Array(1,2,3,4);
        
       //获取数组的长度
       console.log(arr1.length);
       
       //push，将新元素添加到数组尾部
       arr1.push("aaa");
       

       /* splice，从数组中删除元素
        该方法有两个参数
        第一个参数为要从那个位置开始删
        第二个参数为要删除的元素个数
       */
        arr1.splice(1,2);
        
        /* forEach方法，遍历每一个有值的元素，注意，是有值的元素，undefined啥的不会遍历
        该方法的参数为一个函数，每次遍历一个元素就会执行传入的方法
        */
        //先制造一些没有值的元素
        arr1[8]="bbb";
        arr1.forEach(function(e){
            //e就是遍历到的元素
            console.log(e);
            
        })

        console.log("==================");
        

        //ES6开始，方法的定义可以简写成(参数列表)=>{方法体}这样的箭头函数，如下所示
        arr1.forEach((e)=>{
            console.log(e);
            
        })
       
    </script>
</body>
</html>
```



## Day02-08.JS-对象-String字符串

### JS中String对象的属性及方法

![image-20250308204744233](./pictures/image-20250308204744233.png)

```html
<!-- String字符串对象 -->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <script>
        //创建字符串方式1
        var s1 = new String("Hello JS");
        //创建字符串方式2
        var s2 = "   Hello JS   ";

        //获取字符串的长度
        console.log(s1.length);
        
        //获取字符串指定索引位置的字符，charAt
        console.log(s1.charAt(1));
        
        //查找某字符在字符串中的位置,indexOf,如果没找到就返回-1，找到了就返回索引
        console.log(s1.indexOf("lo"));

        //去除字符串两边的空格，中间的空格不会去除，会返回一个新字符串
        var s3 = s2.trim();
        console.log(s3);
        console.log(s2);    //原字符串不会改变
        
        //获取字符串某个区间的字符,包前不包后
        var s4=s1.substring(0,5);
        console.log(s4);
    </script>
</body>
</html>
```



## Day02-09.JS-对象-JSON

### JS中的自定义对象

在JS中自定义对象的语法格式如下

![image-20250309093705143](./pictures/image-20250309093705143.png)

调用对象的属性和方法的语法格式如下

![image-20250309093737820](./pictures/image-20250309093737820.png)



```html
<!-- JS中的自定义对象 -->
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>

<body>
    <script>
        var user = {
            //定义属性
            name: "Tom",
            age: 20,
            gender: "man",

            //定义方法
            eat:function(){
                alert("正在吃东西");
            }

            //方法定义可以简写
            // eat(){
            //     alert("正在吃东西");
            // }
        }
        
        //调用对象的属性和方法
        alert(user.name);
        user.eat();


    </script>
</body>

</html>
```



### JSON

JSON是JavaScript Object Notation的简写，意为JavaScript对象标记法。

JSON就是用JavaScript对象标记法书写的文本，也就是说JSON就是一个文本，可以认为是一个字符串。

在JSON中书写不同类型的数据的格式如下

![image-20250309095020126](./pictures/image-20250309095020126.png)

由于其结构简单，层次结构鲜明，多作为数据载体在网络中传输数据。

JSON中数据是以键值对的形式书写，所有键必须带双引号。 

#### 1.定义JSON

定义JSON的格式如下，最外面一定要单引号`''`，不能用双引号`""`

![image-20250309100223744](./pictures/image-20250309100223744.png)

#### 2.将JSON字符串转换为JSON对象

使用JSON提供的`JSON.parse`方法

#### 3.将JSON对象转换为JSON字符串

使用JSON提供的`JSON.stringify`方法



```html
<!-- JSON对象 -->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <script>
        // 定义JSON对象
        //这里注意，最外面只能用单引号来包围JSON字符串，不能用双引号，开始我用双引号就报错了
        var strJSON = '{"name":"Arthur","age":20,"addr":["北京","上海","广州","深圳"] }';

        //将JSON字符串转化为JSON对象，使用js提供的JSON.parse
        var JSONObj = JSON.parse(strJSON);
        //转换成JSON对象后就可以访问JSON中的数据
        alert(JSONObj.name);

        //将JSON对象转化JSON字符串，使用js提供的JSON.stringify
        var JSONStr = JSON.stringify(JSONObj);
        alert(JSONStr);

    </script>
</body>
</html>
```



## Day02-10.JS-对象-BOM

### 什么是BOM

BOM是Browser Object Model的缩写，意为：浏览器对象模型。

BOM允许JS与浏览器对话，使用浏览器的一些组件。

BOM将浏览器的组件封装为对象，如下

![image-20250309100832567](./pictures/image-20250309100832567.png)



### Window：浏览器窗口对象

![image-20250309101353305](./pictures/image-20250309101353305.png)

```html
<!-- 浏览器窗口对象 -->
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>

<body>
    <script>
        //弹出提示框
        window.alert("这是一个提示框");
        //window.可以省略
        alert("这是一个提示框2");

        //弹出对话框，该方法会返回boolean值，确定返回true，取消返回false
        var flag = confirm("您确定要删除吗？");
        alert(flag);

        //按指定毫秒周期性调用函数
        var i = 0;
        setInterval(function () {
            i++;
            console.log("函数被执行了"+i+"次");

        },2000) //每2秒执行一次函数

        //在指定毫秒后执行一次函数，只会执行一次
        setTimeout(function(){
            console.log("只执行一次的函数");
            
        },3000)     //3秒后执行一次函数


    </script>

</body>

</html>
```



### Location：地址栏对象

![image-20250309102712296](./pictures/image-20250309102712296.png)

一旦修改了Location的href，浏览器会立即跳转到新的地址

```html
<!-- Location:地址栏对象 -->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <script>
        //通过window.location来获取地址栏对象，不过window.可以省略
        alert(location.href);
        
        //修改地址栏对象的href，会立即跳转
        location.href="https://www.bilibili.com/";

    </script>
</body>
</html>
```



## Day02-11.JS-对象-DOM

### 什么是DOM

![image-20250309104240402](./pictures/image-20250309104240402.png)

### 通过DOM来获取元素对象

![image-20250309104813914](./pictures/image-20250309104813914.png)

```html
<!-- 使用DOM -->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <h1 id="title">你好啊，Arthur</h1>

    <p name="paragraph">这是一个段落1</p>
    <p name="paragraph">这是一个段落2</p>
    
    <div class="className">66666</div>
    <div class="className">77777</div>
    <div class="className">88888</div>
</body>

<script>
    // 使用DOM来获取元素
    //通过id属性值来获取，返回单个元素对象
    var h1=document.getElementById("title");
    
    //通过标签名来获取,返回的是一个数组
    var divs = document.getElementsByTagName("div");
    for (let index = 0; index < divs.length; index++) {
        alert(divs[index])
    }

    //通过name属性获取，返回的是一个数组
    var names=document.getElementsByClassName("paragraph");

    //通过class属性获取，返回的是一个数组
    var classes = document.getElementsByClassName("className");
</script>
</html>
```



## Day02-12.JS-对象-DOM案例

### 自己做了一个切换图片的效果

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <img id="picture" src="picture/呆呆雾子.jpg" >
    <br>
    <button onclick="lastPisture()">上一张</button>
    <button onclick="nextPisture()">下一张</button>
</body>
    <script>
        function nextPisture(){
            //获取图片元素
            var img = document.getElementById("picture");
            img.src="picture/比心雾子.gif";
        }
        function lastPisture(){
            var img = document.getElementById("picture");
            img.src="picture/呆呆雾子.jpg";
        }

    </script>

</html>
```



## Day02-13.JS-事件-事件绑定&常见事件

### 什么是事件监听

![image-20250309114207526](./pictures/image-20250309114207526.png)



### 事件绑定

事件绑定有两种方式

![image-20250309114841010](./pictures/image-20250309114841010.png)



```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <!-- onclick属性表示当按钮被点击时要执行的函数 -->
    <input type="button" onclick="on()" value="按钮1">
    <input type="button" id="btn" value="按钮2">

</body>
<script>
    //事件绑定方式1
    function on(){
        alert("绑定方式1执行了");
    }

    //事件绑定方式2
    //直接获取元素对象
    var btn = document.getElementById("btn");
    btn.onclick=function(){
        alert("绑定方式2执行了");
    }

</script>
</html>
```



### 常见事件

常见事件如下

![image-20250309115009112](./pictures/image-20250309115009112.png)

```html
<!-- DOM常见事件 -->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<!-- 当页面被加载时会触发load函数 -->
<body onload="load()">
    <!-- 当该输入框获得焦点时会触发focus函数，失去焦点时会触发blur函数 -->
     <form  action="" style="text-align: center;">
        <input type="text" onblur="blur()" onfocus="focus()" onkeydown="blur()">
        <input type="submit" value="提交">

     </form>

     <br>

    <!-- 当鼠标移到该图片时会触发over函数，从该图片移开时会除法out函数 -->
    <img src="picture/大眼juno.gif" onmouseover="over()" onmouseout="out()">

</body>
<script>
    function load(){
        console.log("页面已加载");
        
    }
    function blur(){
        console.log("输入框获得焦点");
        
    }
    function focus(){
        console.log("输入框失去焦点");
        
    }
    function over(){
        console.log("鼠标移上图片");
        
    }
    function out(){
        console.log("鼠标移出图片");
        
    }

</script>
</html>
```



# Vue

## Day02-15.Vue-概述

### 什么是Vue

Vue是一套前端框架，免除了原生JavaScript中的DOM操作。

Vue的核心思想是MVVM（Model-View-ViewModel），实现数据的双向绑定。



### Vue快速入门

1.引入vue.js文件

2.在JS代码区域创建vue核心对象，定义数据模型

3.编写视图

```html
<!-- Vue快速入门 -->
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <!-- 1.引入vue.js文件 -->
    <script src="JS/vue.js"></script>
</head>

<body>
    <!-- 3.编写视图 -->
     <div id="app">
        <!-- 输入框会自动将message的数据展示到输入框上，并且如果在输入框中改变，message的数据就会改变，从而也会影响后面后面用到message的地方，这就是vue的双向数据绑定 -->
        <input type="text" v-model="message">
        <!-- 插值表达式 {{表达式}} -->
        {{message}}
     </div>

</body>
<script>
    // 2.在js代码区创建vue核心对象，定义数据模型
    new Vue({
        //代表vue作用的范围是id为app的这块区域
        el: "#app",
        data: {
            message: "Hello Vue!"
        }
    })

</script>

</html>
```

运行结果如下，在输入框中改变数据，后面也会跟着改变

![image-20250309150928594](./pictures/image-20250309150928594.png)

## Day02-16.Vue-指令-v-bind&v-model&v-on

### vue的常见指令

vue的指令就是HTML标签上带有v-前缀的特殊属性。vue的常见指令如下

![image-20250309151331984](./pictures/image-20250309151331984.png)



### v-bind和v-model的使用

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script src="JS/vue.js"></script>
</head>

<body>
    <div id="app">
        <!-- 使用v-bind来绑定标签的href属性 -->
        <a v-bind:href="url">链接1</a>
        <!-- 可以简化写法 -->
        <a :href="url">链接2</a>
        <!-- 使用v-model来为表单元素创建双向数据绑定 -->
         <!-- 此时如果改变输入框中的数据，上面两个链接也会改变 -->
        <input type="text" v-model="url">
		<!--绑定的变量一定要在数据模型当中声明-->
    </div>

</body>
<script>
    new Vue({
        el: "#app",
        data: {
            //在数据模型中声明变量
            url: "https://www.bilibili.com"
        }
    })

</script>

</html>
```



### v-on的使用

v-on用于绑定元素的事件

```html
<!-- vue的v-on指令 -->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script src="JS/vue.js"></script>
</head>
<body>
    <div id="app">
        <!-- 使用v-on来绑定事件 v-on:事件名 -->
        <input type="button" v-on:click="handle()" value="点我一下">
        <!-- v-on的简化写法 -->
        <input type="button" @click="handle()" value="点我一下">
    </div>
</body>
<script>
    new Vue({
        el:"#app",
        data:{

        },
        //定义vue的方法，要与data同级
        methods:{
            handle:function(){
                alert("你点了一下按钮");
            }
        }
    })

</script>
</html>
```



## Day02-17.Vue-指令-v-if&v-show&v-for

### v-if和v-show的使用

```html
<!-- 使用vue的条件语句 -->
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script src="JS/vue.js"></script>
</head>

<body>
    <div id="app">
        <!-- v-if、v-else-if、v-else -->
        <input type="text" v-model:value="age">
        <span v-if="age<=35">年轻人</span>
        <span v-else-if="35<age&&age<60">中年人</span>
        <span v-else>老年人</span>

        <br>
        <!-- v-show -->
         <!-- v-show的作用和v-if差不多，唯一区别在于当判断结果为false是，v-if并不会渲染元素，而v-show会渲染元素，只不过通过css的display属性隐藏起来了 -->
        <span v-show="age<=35">年轻人</span>
        <span v-show="35<age&&age<60">中年人</span>
        <span v-show="age>=60">老年人</span>
    </div>
</body>
<script>
    new Vue({
        el: "#app",
        data: {
            age: 20,
        }
    })

</script>

</html>
```



### v-for：遍历数组

使用v-for来循环遍历数据

```html
<!-- 使用v-for指令 -->
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script src="JS/vue.js"></script>
</head>

<body>
    <div id="app">
        <!-- 使用v-for来遍历数据 -->
        <!-- 语法格式为 元素名（即遍历出来的元素名，可以任意取） in 数组名（要遍历的数组名） -->
        <div v-for="addr in addrs">{{addr}}</div>
        <!-- 还可以带索引遍历 -->
        <div v-for="(addr,index) in addrs">{{index+1}}:{{addr}}</div>

    </div>
</body>
<script>
    new Vue({
        el: "#app",
        data: {
            addrs: ["北京", "上海", "广东", "深圳"],
        }
    })


</script>

</html>
```





## Day02-19.Vue-生命周期

### 什么是Vue的生命周期

Vue的生命周期指的是Vue对象从创建到被销毁经历的8个阶段，如下

![image-20250309160206111](./pictures/image-20250309160206111.png)

每触发一个生命周期事件，都会自动执行一个生命周期方法（称为钩子）

```html
<!-- Vue生命周期的其中一个阶段：挂载完成 -->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script src="JS/vue.js"></script>
</head>
<body>
    <div id="app"></div>
</body>
<script>
    new Vue({
        el:"#app",
        data:{

        },
        methods:{

        },
        // 生命周期触发的函数是唯一的，其定义与methods同级
        mounted() {
            // 当Vue初始化成功，HTML页面渲染成功，就会执行该方法
            console.log("挂载完成~~~");
            
        },
    })
</script>
</html>
```



# Ajax

## Day03--1.Ajax-介绍

### 什么是Ajax

Ajax是Asynchronous JavaScript And XML的缩写，意为：异步的JavaScript和XML

Ajax的作用如下：

1.向服务器发送请求，并获取服务器的消息

2.异步交互：可以在不重新加载页面的情况下与服务器交换数据并更新部分网页的技术。如：搜索联想、用户名校验等功能







# MySQL基础

## Day06-01.MySQL-课程介绍

### 什么是数据库

数据库指的是Data Base（DB），是存储和管理数据的仓库



### 数据库管理系统

数据库管理系统指的是DataBase Management System（DBMS），是操作和管理数据库的大型软件



### 什么是SQL

SQL是Structured Query Language 的缩写，是操作关系数据库的编程语言，定义了一套操作关系型数据库的统一标准。

使用SQL，不管用的是Oracle还是MySQL，只要是关系型数据库就能用SQL语言来操作。



## Day06-02.MySQL-概述-安装配置

MySQL的安装和环境变量配置就不讲了。

### MySQL的启动与关闭

```cmd
net start mysql		//启动mysql服务

net stop mysql		//停止mysql服务
```



## Day06-03.MySQL-概述-数据模型&SQL简介

### SQL语句的通用语法

![image-20250312192404313](./pictures/image-20250312192404313.png)





### SQL分类

SQL语句通常分为四大类

![image-20250312192545883](./pictures/image-20250312192545883.png)





## 05-DDL-操作数据库

### 登录数据库

```mysql
mysql -u root -p			-- 然后输入密码进入mysql操作环境
```

```mysql
mysql -uroot -p1234		-- 这种方式直接-u 与 -p后面不用接空格，-u后直接接登录用户  -p后直接接密码，1234替换成自己的密码
```

使用第一种方法比较安全

![image-20241222101745304](./pictures/image-20241222101745304.png)

### 连接远程服务器上的数据库

```mysql
mysql -h服务器IP地址 -P端口号 -u 登录用户 -p		-- 注意端口号是大写P，用户名密码是小写p
```

例如

```mysql
 mysql -h 120.26.90.87 -P 3306 -u root -p		-- 然后输入密码即可登录
```





### 相关命令

DDL的命令中database可替换为schema

#### 查询数据库命令

```mysql
show databases;
show schemas;				-- 将database替换为schema也可以使用
```

![image-20241222102127280](./pictures/image-20241222102127280.png)



#### 创建数据库命令

```mysql
create database 数据库名称;
create database testdb;
create schema testdb; 
create database if not exists testdb;		-- 创建testdb数据库如果该数据库不存在
```

![image-20241222102306037](./pictures/image-20241222102306037.png)



#### 删除数据库命令

```mysql
drop database 数据库名称;
drop database testdb;
drop database if exists testdb;			-- 删除数据库，如果该数据库存在
```

![image-20241222102643344](./pictures/image-20241222102643344.png)

#### 使用数据库命令

```mysql
select database();			-- 查看当前使用的数据库
use 数据库名称;				-- 使用指定数据库
use eduadmsys-final;
```

![image-20241222102853345](./pictures/image-20241222102853345.png)



## Day06-05.MySQL-DDL-图形化工具

### 操作数据库的图形化工具

可以使用navicat，我在学习这一节之前用的就是navicat，但是这里教的是Oracle公司的DataGrip，也不用下这个软件，因为这个软件集成到了Idea中，可以直接通过idea来使用

下面介绍在idea中使用datagrip

首先在右侧工具栏找到Database选项，再选择添加Mysql数据库，进入后输入数据库地址和密码等连接就行了。

![image-20250312195200703](./pictures/image-20250312195200703.png)

下面会讲一些细节上的操作

点连接到的数据库服务器旁边的那个小数字，可以选择要显示的数据库

![image-20250312195343831](./pictures/image-20250312195343831.png)

如果想要使用SQL语句，可以右键数据库服务器，然后选择Navigation，选择Jump to Quary 。。。可以进入SQL语句的使用界面，并且可以保存历史SQL语句记录

![image-20250312195507282](./pictures/image-20250312195507282.png)





## 06-DDL-操作表-查询表&创建表

#### 查询表命令

查询当前数据库下的表

```mysql
show tables;
```

![image-20241222103401027](./pictures/image-20241222103401027.png)

#### 查询表结构命令

```mysql
desc 表名称;
desc teacher;
```

![image-20241222103524810](./pictures/image-20241222103524810.png)



#### 查询建表语句

```sql
show create table 表名;
show create table test;		-- 查看test表的建表语句
```



#### 创建表命令

```mysql
create table 表名(
	字段名 字段类型 [约束] [comment 字段注释],		-- []括起来的是可选字段
    字段名 字段类型 [约束] [comment 字段注释],
    ....
    字段名 字段类型		--最后一个字段不能加逗号,
)[comment 表注释];

-- 创建简单表
create table tb_user(
	id int,
    username varchar(25),		--括号里面要指定字段的长度
    password varchar(32)
);

-- 为表及表的每个字段带上注释
create table tb_user(
    id int comment 'ID,用户的唯一标识',
    username varchar(20) comment '用户名',
    name varchar(10) comment '姓名',
    age int comment '年龄',
    gender char(1) comment '性别'
) comment '用户信息表'

-- 为字段添加约束
create table tb_user(
    id int primary key auto_increment comment 'ID,用户的唯一标识',-- 主键且自增
    username varchar(20) not null unique comment '用户名', -- 非空且唯一
    name varchar(10) not null comment '姓名', -- 非空
    age int comment '年龄',
    gender char(1) default '男' comment '性别' -- 默认值为男
) comment '用户信息表'

```

约束是作用于字段上的规则，用于限制存储在表中的数据，可以保证数据的正确性，有效性和完整性。常见的有如下几个约束

![image-20250312201834262](./pictures/image-20250312201834262.png)



![image-20241222104048240](./pictures/image-20241222104048240.png)



## 07-DDL-操作表-数据类型

#### mysql的主要数据类型

![image-20241222104319508](./pictures/image-20241222104319508.png)

其中数值类型还分为有符号和无符号类型，默认为有符号类型，如果想指定无符号类型，需要再类型后面加上`unsigned`表示无符号

```sql
tinyint unsigned
```

小数类型的定义也比较特殊

```sql
float(5,2)   -- 5表示整个数字的长度，2表示小数位长度，说明整数位有3位
double(5,2)  -- 与float同理
decimal(5,2) -- 与float同理，decimal是用字符串的方式来处理小数，可以避免小数运算的精度问题
```





熟悉一下mysql的数据类型的使用

创建以下学生表

![image-20241222105038708](./pictures/image-20241222105038708.png)

```mysql
create table student(
	id int,
    name varchar(10),
    gender char(1),
    birthday date,
    score double(5,2),				-- 使用double类型，括号中前一个数字表示最大长度，后一个数字表示保留几位小数
    email varchar(64),
    tel varchar(15),
    status tinyint					-- 学生状态一般也就几个，所以用tinyint即可
);
```



## 08-DDL-操作表-修改&删除

#### 删除表命令

```mysql
drop table 表名;
drop table tb_user;
```

![image-20241222105948530](./pictures/image-20241222105948530.png)

### 修改表的一系列命令

#### 修改表名

```mysql
-- 第一种方法
alter table 表名 rename to 新的表名;
alter table student rename to stu;

-- 第二种方法
rename table 旧表名 to 新表名;
rename table tb_user to user;
```

![image-20241222110503916](./pictures/image-20241222110503916.png)



#### 添加一列（添加字段）

```mysql
alter table 表名 add 字段名 数据类型 [comment 注释] [约束];
alter table stu add class_id int;
```

![image-20241222110635036](./pictures/image-20241222110635036.png)

#### 修改数据类型（修改字段类型）

```mysql
alter table 表名 modify 字段名 新的数据类型;
alter table stu modify status varchar(10);
```

![image-20241222110830896](./pictures/image-20241222110830896.png)

#### 修改字段名和数据类型

```mysql
alter table 表名 change 列名 新的列名 新的数据类型 [comment 注释] [约束];
alter table stu change class_id class_name varchar(10);
```

![image-20241222110943532](./pictures/image-20241222110943532.png)

#### 删除列

```mysql
alter table 表名 drop 列名;
alter table stu drop class_name;
```

![image-20241222111042727](./pictures/image-20241222111042727.png)

## 10-DML-操作数据-添加&修改&删除

### 添加系列命令

#### 给指定列添加数据

```mysql
insert into 表名(列名1,列名2,....) values(值1,值2,...);
insert into stu(id,name) values(1,'张三');
```

![image-20241222115331588](./pictures/image-20241222115331588.png)

#### 给全部列添加数据

```mysql
insert into 表名 values(值1,值2,....);			-- 表名后面的括号里的列名可以省略也可以全写
insert into 表名(列名1,列名2,等全部列名) values(值1,值2,...);
```

![image-20241222115742754](./pictures/image-20241222115742754.png)

#### 批量添加数据

```mysql
insert into 表名 values(值1,值2,...),(值1,值2,...),(值1,值2,...)....;		-- 全部字段
insert into 表名(列名1,列名2,...) values (值1,值2,...),(值1,值2,...),(值1,值2,...)....;	-- 部分字段
```

![image-20241222120035196](./pictures/image-20241222120035196.png)

### 插入数据时的注意事项

![image-20250314082304555](./pictures/image-20250314082304555.png)



### 修改数据命令

```mysql
update 表名 set 列名1=值1,列名2=值2,.....;			-- 如果不添加where条件，该命令会对所有行执行修改操作
update 表名 set 列名1=值1,列名2=值2,..... where 某个列=某个值;
```

![image-20241222120234138](./pictures/image-20241222120234138.png)

### 删除数据命令

```mysql
delete from 表名 where 条件;					-- 如果不添加where条件，该命令会删除所有的行
delete from 表名;								 -- 删除所有行
```

![image-20241222120725492](./pictures/image-20241222120725492.png)

![image-20241222120742410](./pictures/image-20241222120742410.png)

### 删除命令的注意事项

![image-20250314083704868](./pictures/image-20250314083704868.png)





## 11-DQL-基础查询

#### DQL查询语句的语法

![image-20250314125412682](./pictures/image-20250314125412682.png)





#### 查询多个字段

```mysql
select 字段1,字段2,..... from 表名;
select * from 表名;					-- 实际业务中不建议使用，因为这样不直观且性能低，若要查询全部，仍然要写出全部字段
```

![image-20241222141421234](./pictures/image-20241222141421234.png)

#### 去除重复记录

```mysql
select distinct 字段1,字段2,.... from 表名; 		-- 只需加上distinct关键字
```

![image-20241222141544119](./pictures/image-20241222141544119.png)

#### 为查询字段起别名

```mysql
select 字段1 as 别名1,字段2 as 别名2,...... from 表名;			-- as可省略
select 字段1 别名1,字段2 别名2,..... from 表名;
```

![image-20241222141719298](./pictures/image-20241222141719298.png)

## 12-DQL-条件查询

```mysql
select * from 表名 where 条件;
```

### 常见的条件运算符

![image-20250314090850202](./pictures/image-20250314090850202.png)



### 几个条件查询的例子

#### 查询年龄大于20岁的学员信息

```mysql
select * from stu where age >20;
```

![image-20241222143907059](./pictures/image-20241222143907059.png)

#### 查询年龄大于等于20岁的学员信息

```mysql
select * from stu where age >=20;
```

![image-20241222144331639](./pictures/image-20241222144331639.png)

#### 查询年龄大于等于20岁并且小于30岁的学员信息

```mysql
select * from stu where age >=20 and age < 30;
select * from stu where age >=20 && age <30;			-- 不推荐使用&&
select * from stu where age between 20 and 30;
```

![image-20241222144514157](./pictures/image-20241222144514157.png)

![image-20241222144536371](./pictures/image-20241222144536371.png)

#### 查询入学日期在‘1998-09-01’到‘1999-09-01’之间的学员信息

```mysql
select * from stu where hire_date between '1998-09-01' and '1999-09-01' ;  -- date类型数据也支持比较
```

![image-20241222144734348](./pictures/image-20241222144734348.png)

#### 查询年龄等于18岁的学院信息

```mysql
select * from stu where age = 18;
```

![image-20241222144811168](./pictures/image-20241222144811168.png)

#### 查询年龄不等于18岁的学员信息

```mysql
select * from stu where age != 18;
```

![image-20241222144850640](./pictures/image-20241222144850640.png)

#### 查询年龄等于18岁或20岁或22岁的学员信息

```mysql
select * from stu where age=18 or age=20 or age=22;
select * from stu where age=18||age=20||age=22;				-- 不推荐使用||
select * from stu where age in 一个集合;
select * from stu where age in (18,20,22);
```

![image-20241222145103109](./pictures/image-20241222145103109.png)

#### 查询英语成绩为null的学员信息

要注意的是查询为null的数据不能使用 = 与 !=来比较，要使用 is null 或 is not null

```mysql
select * from stu where english is null;
select * from stu where english is not null;
```

![image-20241222145311916](./pictures/image-20241222145311916.png)

![image-20241222145325651](./pictures/image-20241222145325651.png)

### 模糊查询

`_`代表单个字符，`%`代表任意字符

#### 查询姓‘马‘的学员信息

```mysql
select * from stu where name like '马%';
```

![image-20241222145557450](./pictures/image-20241222145557450.png)

#### 查询第二个字是’花‘的学员信息

```mysql
select * from stu where name like '_花%';
```

![image-20241222145643621](./pictures/image-20241222145643621.png)

#### 查询名字中包含’德‘的学员信息

```mysql
select * from stu where name like '%德%';
```

![image-20241222145718899](./pictures/image-20241222145718899.png)

## 13-DQL-排序查询

排序方式主要有升序排序`asc`，这是默认的；还有一个降序排序`desc`

```mysql
select 字段1,字段2,.... from 表名 order by 排序字段名1 排序方式1 ,排序字段名2 排序方式2,....;
```

#### 按照年龄升序排列

```mysql
select * from stu order by age asc;				-- asc 也可以不写，默认升序排列
```

![image-20241222150936796](./pictures/image-20241222150936796.png)

#### 按照数学成绩降序排列

```mysql
select * from stu order by math desc;
```

![image-20241222151016004](./pictures/image-20241222151016004.png)

#### 按照数学成绩降序排列，如果数学成绩一样，再按照英语成绩升序排列

```mysql
select * from stu order by math desc , english asc;
```

![image-20241222151132519](./pictures/image-20241222151132519.png)

## 14-DQL-聚合函数

聚合函数是将一列数据作为整体，进行纵向计算。

主要有以下5个聚合函数

```mysql
/*
	count		统计数量，如果有值为null，则null不参与统计
	max			求某一列的最大值
	min			求某一列的最小值
	sum			求某一列值的总和
	avg			求某一列的平均值
	需要注意，null也不参与计算比较
*/
select 聚合函数名(列名) from 表名;
```

#### 统计班级一共有多少个学生

```mysql
-- 有三种方式
-- 1. count(字段名)，这种方式的字段一般用非空字段，如id
select count(name) from stu;

-- 2. count(常量),常量可以为数字0、1、2.。。。或者字符，只要非空就行
select count(1) from stu;

-- 3. count(*),推荐使用这种方式，因为mysql底层专门对这种方式进行了优化处理
select count(*) from stu;
```

![image-20241222152306993](./pictures/image-20241222152306993.png)

#### 查询数学成绩的最高分

```mysql
select max(math) from stu;
```

![image-20241222152359781](./pictures/image-20241222152359781.png)

#### 查询数学成绩的最低分

```mysql
select min(math) from stu;
```

![image-20241222152455727](./pictures/image-20241222152455727.png)

#### 查询数学成绩的总分

```mysql
select sum(math) from stu;
```

![image-20241222152527490](./pictures/image-20241222152527490.png)

#### 查询数学成绩的平均分

```mysql
select avg(math) from stu;
```

![image-20241222152555153](./pictures/image-20241222152555153.png)

#### 查询英语成绩的最低分

英语成绩中的null值不会参与比较

```mysql
select min(english) from stu;
```

![image-20241222152632782](./pictures/image-20241222152632782.png)

#### 使用聚合函数的注意事项

![image-20250314094043174](./pictures/image-20250314094043174.png)



## 15-DQL-分组查询

```mysql
select 字段列表 from 表名 [where 条件语句] group by 分组字段名 [having 分组后的过滤条件]
```

要注意的是**分组查询只能查询被分组的字段和聚合函数**，查询其他字段是没有意义的

举个例子，假如我要按性别来分组查询，即此时查询结果以及按性别分为男女两组了，那么此时如果我查询姓名字段，那男女两组都有那么多人，又该返回哪个人的姓名呢？所以说除了被分组的字段和聚合函数，查询其他字段是没有意义的。

#### 分组查询的注意事项

![image-20250314095845416](./pictures/image-20250314095845416.png)

#### where与having的区别

##### 1.执行时机不同

where是分组之前过滤，不满足where条件的不会参与分组，而having是分组后对分组结果进行过滤

##### 2.判断条件不同

where不能对聚合函数进行判断，having可以。



#### 查询男同学和女同学各自的数学平均分

```mysql
select sex,avg(math) from stu group by sex;			-- sex是分组字段 avg(math)是聚合函数
```

![image-20241222153731514](./pictures/image-20241222153731514.png)

#### 查询男同学和女同学各自的数学平均分，以及各自的人数

```mysql
select sex,avg(math),count(*) from stu group by sex;
```

![image-20241222153838605](./pictures/image-20241222153838605.png)

#### 查询男同学和女同学各自的数学平均分，以及各自的人数，并且要求分数低于70分的不参与分组

```mysql
select sex,avg(math),count(*) from stu where math >=70 group by sex;
```

![image-20241222153959757](./pictures/image-20241222153959757.png)

#### 查询男同学和女同学各自的数学平均分，以及各自的人数，并且要求分数低于70分的不参与分组、分组后人数大于2的才显示



```mysql
select sex,avg(math),count(*) from stu where math >=70 group by sex having count(*)>2;
```

![image-20241222154126639](./pictures/image-20241222154126639.png)

## 16-DQL-分页查询

```mysql
select 字段列表 from 表名 limit 起始索引, 查询条目数;
```

起始索引的计算公式：

起始索引=(当前查询的页码-1)*查询条目数

#### 从0开始查询，查询3条数据

```mysql
select * from stu limit 0,3;
```

![image-20241222161407573](./pictures/image-20241222161407573.png)

#### 每页显示3条数据，查询第1页数据

```mysql
select * from stu limit 0,3;
```

#### 每页显示3条数据，查询第2页数据

```mysql
select * from stu limit 3,3;
```

![image-20241222161456363](./pictures/image-20241222161456363.png)

#### 每页显示3条数据，查询第3页数据

```mysql
select * from stu limit 6,3;
```

![image-20241222161528680](./pictures/image-20241222161528680.png)



#### 分页查询的注意事项

![image-20250314130715984](./pictures/image-20250314130715984.png)



## Day07-07.MySQL-DQL-案例

### MySQL的流程控制

MySQL提供了两种流程控制的方法

#### 1.MySQL-if

if的语法如下

```mysql
if(表达式,值1,值2) [as 别名]
```

if的作用为：当表达式的值为true时，取值1，值为false时，取值2。可以为该if语句起个别名，一般也会这么做，否则名字会很长

使用示例：

```mysql
-- 统计男性员工数量和女性员工数量
select if(gender=1,'男','女') '性别',count(*) from tb_emp group by gender;
```

该例子将gender字段取出放在表达式`gender=1`中来判断，并根据取出的gender的值不同来取不同值。这里就是gender为1，就代表男性，gender为2就代表女

运行结果

![image-20250314142647147](./pictures/image-20250314142647147.png)



#### 2.MySQL-case

case的语法如下

```mysql
case 表达式 when 值1 then 结果1 when 值2 then 结果2 ...when 值n then 结果n else 结果 end
```

case的作用为：根据表达式的值来取不同的值，如果表达式的值为值1，那么就取结果1，如果表达式的值为值2，那么就取结果2，如果表达式结果都不符合列出来的值，就取else的结果。

使用示例：

```mysql
select (case job
            when 1 then '班主任'
            when 2 then '讲师'
            when 3 then '学工主管'
            when 4 then '教研主管'
            else '未分配职位' end) 职位
     , count(*)
from tb_emp
group by job
```

该例子判断job的值，如果job为1，就取值为“班主任”，如果job为2，就取值为“讲师”，以此类推。

运行结果

![image-20250314143428979](./pictures/image-20250314143428979.png)



## Day07-09.MySQL-多表设计-一对多-外键

### 外键约束

#### 1.什么是外键约束

如下图所示，有两张表，一张员工表，和一张部门表，部门和员工的关系是一对多的关系，即：一个部门有多个员工，一个员工只属于一个部门。

![image-20250314162501861](./pictures/image-20250314162501861.png)

但是，如果此时我删除一个部门，如下图所示，我删除了部门id为1的部门

![image-20250314162740576](./pictures/image-20250314162740576.png)

可以看见，虽然部门成功删除了，但是员工里面还存在刚刚删除的部门数据，即所属部门id为1的员工，这就导致了数据的不完整、不一致的问题。

造成这个问题的原因在于这两个表只是在我们逻辑上建立了连接，但是在实际的数据库里面，它们并没有建立联系。

要解决这个问题就要用到外键约束，外键约束就是用来解决多表之间的数据完整性、一致性问题的

#### 2.创建外键约束的语法

创建外键约束有两种方式

```mysql
-- 1.在创建表时指定外键约束
create table 表名(
  字段名 数据类型,
  ......
    
    
  [constraint] [外键名称] foreign key(外键字段名) references 主表(要关联的主表字段名)-- 在定义好表的所有字段后再定义外键
);


-- 2.在表创建好后指定外键约束
alter table 表名 add constraint 外键名称 foreign key(外键字段名) references 主表(要关联的主表字段名);
```

示例如下

```mysql
alter table tb_emp
    add constraint 所属部门
        foreign key (dept_id) references tb_dept (id);
```

此时我们就无法直接删除部门数据

![image-20250314164501757](./pictures/image-20250314164501757.png)

但是假如员工中没有相关部门的数据，就可以删除，比如现在员工里面没有人的所属部门是id为4的部门，此时我就可以在部门表中删除id为4的记录

![image-20250314164655561](./pictures/image-20250314164655561.png)



#### 3.物理外键和逻辑外键

上面通过sql语句创建的外键约束属于物理外键，而在`1.什么是外键约束`里面讲的没有用外键约束前的关系就是逻辑外键。

这两种外键，业务上大多数用的是逻辑外键，原因如下图

![image-20250314164952992](./pictures/image-20250314164952992.png)



## Day07-10.MySQL-多表设计-一对一&多对多

### 表的一对一关系

假如我有下图中的一个用户信息表，这个用户信息表包括用户的基本信息和用户的身份证信息。但是在实际业务中，对用户基本信息的查询比较多，对用户身份信息的查询比较少，此时如果仍然用下面的表，每次查询用户基本信息时也会连着查询用户的身份信息，这样会影响查询效率

![image-20250314165423882](./pictures/image-20250314165423882.png)

要解决上面这个问题，可以将上面的表一分为二，将一个大表分为一个用户基本信息表和一个用户身份信息表，然后让这两个表通过外键相互联系，从而实现一对一的关系

![image-20250314165750545](./pictures/image-20250314165750545.png)

### 表的多对多关系

假如有下面这样一个场景

学生与课程的关系是：一个学生可以选择多门课程，一门课程可以被多个学生选择。

那要描述这种关系，在这两个表之间用外键肯定是不合适的，外键适合用在一对多（多对一）的关系。

我们可以创建第三张中间表来表述这种多对多的关系，第三张表至少包含关联到学生和课程两个表的外键，分别关联两方主键。

第三张表的作用实际上就是记录所有的关联关系，如下图，看第三张表就可以发现，学号为1的学生选择了课程号为1、2、3的课程。

![image-20250314170646546](./pictures/image-20250314170646546.png)









# MySQL高级

## Day08-01.MySQL-多表查询-概述

### 什么是多表查询

多表查询很简单，语法如下

```mysql
select 字段1,字段2,....字段n from 表1,表2....表n;
```

例如：

```mysql
-- 多表查询
select * from tb_emp,tb_dept;
```

但是这样查询出来的结果是两个表的笛卡尔积，如下图所示，会有很多无用数据，比如金庸的所属部门id为2，那么其后面跟上的部门信息就应该是部门id为2的部门信息，而不是全部显示出来

![image-20250314173341448](./pictures/image-20250314173341448.png)

为多表查询添加条件以删除无用数据

```mysql
-- 多表条件查询
select * from tb_emp,tb_dept where dept_id=tb_dept.id;
```

删除无用数据后的结果如下

![image-20250314173553773](./pictures/image-20250314173553773.png)



### 多表查询的分类

多表查询分为以下几种

![image-20250314173741107](./pictures/image-20250314173741107.png)





## 08-多表查询-内连接&外连接

### 内连接

```mysql
select 字段列表 from 表1,表2.... where 条件;			-- 这是隐式内连接
select 字段列表 from 表1 [inner] join 表2 on 条件;		-- 这是显式内连接，其中inner可以省略

-- 如果嫌表的名字太长不想写，可以为表起别名
select 字段列表 from 表1 [as] 别名1,表2 [as] 别名2.... where 条件;

-- 例子如下，要注意的是，如果为表起了别名那么不管是在字段列表还是在条件位置，要用表名只能用别名
select 员工.name 员工姓名,部门.name 部门姓名 from tb_emp 员工,tb_dept 部门 where 员工.dept_id=部门.id;
```

内连接是查询 表1 与 表2相交的数据

![image-20241222211732864](./pictures/image-20241222211732864.png)

#### 隐式内连接查询emp和dept的数据

```mysql
select * from emp,dept where emp.dep_id=dept.did;			-- 隐式内连接
```

![image-20241222212933054](./pictures/image-20241222212933054.png)

#### 隐式内连接查询emp的name,gender,和dept表的dname

```mysql
select emp.name,emp.gender,dept.dname from emp,dept where emp.dep_id=dept.did;
```

![image-20241222213013685](./pictures/image-20241222213013685.png)

#### 显示内连接查询数据

```mysql
select * from emp inner join dept on emp.dep_id=dept.did;
select * from emp join dept on emp.dep_id=dept.did;				-- 省略inner
```

![image-20241222213247760](./pictures/image-20241222213247760.png)

### 外连接

#### 左外连接

```mysql
select 字段列表 from 表1 left [outer] join 表2 on 条件;				-- outer可省略

```

查询emp表的所有数据及对应的部门信息

```mysql
select * from emp left join dept on emp.dep_id=dept.did;
```

![image-20241222213900157](./pictures/image-20241222213900157.png)

#### 右外连接

```mysql
select 字段列表 from 表1 right [outer] join 表2 on 条件;			-- outer可省略 
```

查询dept表的所有数据及其对应的员工信息

```mysql
select * from emp right join dept on emp.dep_id = dept.did;
```

![image-20241222214033673](./pictures/image-20241222214033673.png)

## 09-多表查询-子查询

SQL语句中嵌套select语句的查询被称为子查询，也叫嵌套查询

子查询根据查询结果的不同，其作用也不同，主要有四种分类，如下：

![image-20250316085937325](./pictures/image-20250316085937325.png)

#### 标量子查询

标量子查询指的是子查询结果为单个值

可以作为条件值来进行条件判断

```mysql
select 字段列表 from 表1 where 表1.某个字段 {=,>,<,...} (子查询);
select * from emp where emp.salary > (
	select salary from emp where emp.name = '猪八戒'					--子查询不能带分号;
);		-- 查询工资大于猪八戒的所有员工信息，子查询先查出猪八戒的工资.
```

![image-20241222215923811](./pictures/image-20241222215923811.png)

#### 列子查询

子查询返回结果为一列的子查询就是列子查询，这种子查询常用操作符有：`in`,`not in`

可以作为一个集合条件，查询在这个集合内的数据，使用in关键字进行条件判断

```mysql
select 字段列表 from 表1 where 表1.某个字段 in (子查询);
-- 查询财务部和市场部所有员工信息
select * from emp where emp.dep_id in (
	select did from dept where dname in ('财务部','市场部')
);
```

![image-20241222220343617](./pictures/image-20241222220343617.png)

#### 行子查询

子查询返回结果为一行，就是行子查询

这里先学一个小知识点

```mysql
select * from tb_emp where entrydate='2007-01-01'and job=2;

-- 下面的查询语句与上面的查询语句等效
select * from tb_emp where (entrydate,job)=('2007-01-01',2);
```

这个小知识点用在行子查询非常有用，因为行子查询返回的就是类似于`('2007-01-01',2)`这种单行多列的数据。

```mysql
-- 查询与'韦一笑'的入职日期及职位都相同的员工
select * from tb_emp where (entrydate,job)=(select entrydate,job from tb_emp where name = '韦一笑');
```

查询结果

![image-20250316092238400](./pictures/image-20250316092238400.png)





#### 表子查询

可以作为一个虚拟表来与其他表进行连接

```mysql
select 字段列表 from 表1 left join (
	select 字段列表 from 表2 where 条件
) on 连接条件;

-- 查询入职日期是'2011-11-11'之后的员工信息和部门信息
select * from (
	select * from emp where emp.join_date > '2011-11-11'
) as t1 left join dept on t1.dep_id=dept.did;
```

![image-20241222220939097](./pictures/image-20241222220939097.png)

## 10-多表查询-案例

相关数据表的模型如下：

![image-20241222222712326](./pictures/image-20241222222712326.png)

```mysql
-- 1.查询所有员工信息。查询员工编号，员工姓名，工资，职务名称，职务描述
SELECT
  emp.id,
  emp.ename,
  emp.salary,
  job.jname,
  job.description 
FROM
  emp
  JOIN job ON emp.job_id = job.id;
-- 2.查询员工编号，员工姓名，工资，职务名称，职务描述，部门名称，部门位置
SELECT
  emp.id,
  emp.ename,
  emp.salary,
  job.jname,
  job.description,
  dept.dname,
  dept.loc 
FROM
  emp,
  job,
  dept 
WHERE
  emp.job_id = job.id 
  AND emp.dept_id = dept.id;-- 隐式内连接
SELECT
  emp.id,
  emp.ename,
  emp.salary,
  job.jname,
  job.description,
  dept.dname,
  dept.loc 
FROM
  emp
  JOIN job ON emp.job_id = job.id
  JOIN dept ON emp.dept_id = dept.id;-- 显式内连接
-- 3.查询员工姓名，工资，工资等级
SELECT
  emp.ename,
  emp.salary,
  t1.grade 
FROM
  emp
  LEFT JOIN salarygrade t1 ON emp.salary BETWEEN t1.losalary 
  AND t1.hisalary;		-- 外连接方法
  
SELECT
  emp.ename,
  emp.salary,
  t1.grade 
FROM
  emp,
  salarygrade t1 
WHERE
  emp.salary BETWEEN t1.losalary 
  AND t1.hisalary;-- 内连接方法
-- 4.查询员工姓名，工资，职务名称，职务描述，部门名称，部门位置，工资等级
SELECT
  emp.id,
  emp.ename,
  emp.salary,
  job.jname,
  job.description,
  dept.dname,
  dept.loc,
  t1.grade 
FROM
  emp
  JOIN job ON emp.job_id = job.id
  JOIN dept ON emp.dept_id = dept.id
  JOIN salarygrade t1 ON emp.salary BETWEEN t1.losalary 
  AND t1.hisalary;-- 显式内连接
-- 5.查询出部门编号、部门名称、部门位置、部门人数
SELECT
  dept.id,
  dept.dname,
  dept.loc,
  count 
FROM
  dept,
  (SELECT dept_id, count(*) count FROM emp GROUP BY dept_id) t1 
WHERE
  dept.id = t1.dept_id;
```



## Day08-08.MySQL-事务-介绍与操作

### 什么是事务

事务指的是一组操作的集合，它是一个不可分割的工作单位，事务会把所有操作作为一个整体一起向系统提交或撤销操作请求，因此事务中的操作要么全部完成，要么全部失败。



### 为什么要引入事务这个机制

如下图，我有两个表，一个部门信息表，一个员工信息表

![image-20250316110017330](./pictures/image-20250316110017330.png)

现在我需要删除一个部门及其部门下的所有员工信息，使用下面的SQL语句

```mysql
-- 删除部门信息
delete from tb_dept where id=1;

-- 删除部门下的所有员工信息
delete from tb_emp where dept_id=1;
```

这个SQL语句是没有问题的，执行后数据肯定能够正常删除，但是，如果其中一条语句出现了异常，如下图，第二条语句是异常的

![image-20250316110226209](./pictures/image-20250316110226209.png)

此时再执行会出现下面的结果，可以看到部门表的数据成功删除了，但是员工表的数据并没有删除，这就导致了数据不一致性。

![image-20250316110326891](./pictures/image-20250316110326891.png)

实际上，MySQL默认会自动提交事务，所以MySQL将我们的两条删除语句当成了两个事务，第一条删除部门的语句为一个事务，执行成功，第二条删除员工的语句为一个事务，执行失败。要解决这个问题我们同样也要用到事务这个机制，不过我们需要将这两条语句当作一次事务来提交，这样这两条语句要么全部成功，要么全部失败，就不会导致数据的不一致。

下面介绍如何手动操作事务

### 事务的操作

操作MySQL事务有三条指令：开启事务`start transaction`/`begin`，提交事务`commit`，回滚事务`rollback`

```mysql
-- 开启事务，执行这条语句时表示下面执行的命令都属于同一个事务
start transaction;


-- 当执行完开启事务命令后，下面的删除语句执行完不会立即提交到数据库中
-- 删除部门信息
delete from tb_dept where id=2;

-- 删除部门下的所有员工信息
delete from tb_emp where dept_id ==2;


-- 提交事务，只有执行了这条语句，对数据库的修改才会真正保存到数据库里面
commit;


-- 回滚事务，但sql语句执行出现异常，执行这条语句以回滚到事务开启前的状态
rollback;
```

执行 start transaction 命令可以理解为，让系统修改数据库时先把修改的信息写在一个“草稿本”上，而不是直接在数据库这个“答题纸”上直接写。

待确认修改结果没有异常时，再把“草稿纸”上的修改写到“答题纸”上去。



### 事务的四大特性

事务的四大特性也是经常出现的面试题

事务的四大特性包括：

#### 1.原子性(Atomicity)

事务是不可分割的最小单位，事务的操作要么全部成功，要么全部失败

#### 2.一致性(Consistency)

事务完成时，必须使所有数据保持一致状态。

例如上面讲到的员工信息与部门信息的关系，如果只删除部门信息而没有删除对应的员工信息，那就是数据不一致状态。只有部门信息和员工信息一起删或部门信息和员工信息都不删，才能保持数据的一致性。

#### 3.隔离性(Isolation)

隔离性指的是多个并发事务在执行时互不干扰，每个事务都像是在独立运行。隔离性确保事务提交前的修改对其他事务不可见，从而保证了数据一致性。

下面的内容来自deepseek AI

数据库系统通常提供以下四种隔离级别，控制事务之间的可见性：

1. **读未提交（Read Uncommitted）**
   - 最低级别，事务可以读取其他未提交事务的修改。
   - 可能导致**脏读**。
2. **读已提交（Read Committed）**
   - 事务只能读取已提交的数据。
   - 避免了脏读，但可能出现**不可重复读**。
3. **可重复读（Repeatable Read）**
   - 事务执行期间多次读取同一数据，结果一致。
   - 避免了脏读和不可重复读，但可能出现**幻读**。
4. **串行化（Serializable）**
   - 最高级别，事务完全串行执行。
   - 避免了脏读、不可重复读和幻读，但性能开销最大。

隔离性旨在解决以下并发问题：

1. **脏读（Dirty Read）**
   - 读取到未提交的数据，可能导致回滚后数据不一致。
2. **不可重复读（Non-repeatable Read）**
   - 同一事务内多次读取同一数据，结果不同。
3. **幻读（Phantom Read）**
   - 同一事务内多次查询，结果集不一致，通常因其他事务插入或删除数据引起。

#### 4.持久性(Durability)

事务一旦提交或回滚，它对数据库的修改就是永久的





## Day08-10.MySQL-索引-介绍

### 什么是索引

索引(index)是帮助数据库高效获取数据的数据结构。

没有使用索引时，数据库查找是通过全表扫描来进行查找的，也就是一条一条往下找。

使用索引后，数据库会建立一个搜索二叉树，使用搜索二叉树会使查找更高效。

全表扫描

![image-20250316115953818](./pictures/image-20250316115953818.png)

搜索二叉树

![image-20250316120017410](./pictures/image-20250316120017410.png)

### 索引的优缺点

#### 1.索引的优点

a.索引可以提高数据查询效率，降低数据库的IO成本

b.通过索引列对数据库进行排序，降低数据排序成本，降低CPU消耗



#### 2.索引的缺点

a.索引会占用存储空间

b.索引虽然大大提高了查询效率，但它也降低了对数据库增删改的效率，因为每次对数据库的修改都要同时维护二叉树，从而降低了数据库增删改的效率。

![image-20250316120637368](./pictures/image-20250316120637368.png)



### 索引的结构

前面讲索引虽然提到了二叉树，但是实际上MySQL的索引结构并没有用二叉树，也没有用红黑树啥的，而是B+Tree。

不使用二叉树的原因有下面几点：

1.二叉树每一个根节点只能存储两个子节点，如果数据库数据量很大，就会加深树的深度，影响查询效率

2.如果在存储数据时是按照降序或升序来存储的，此时二叉树就会变成一个单向链表，查询效率自然也不会太高。

如下图，右边就是一个单向链表

![image-20250316121551550](./pictures/image-20250316121551550.png)

MySQL支持的索引结构有很多，比如：Hash索引、B+Tree索引、Full-Text索引。如果没有特别指明，默认使用B+Tree索引。



B+Tree（多路平衡搜索树）索引的结构如下

![image-20250316121733519](./pictures/image-20250316121733519.png)

B+Tree索引结构的特点有：

1.每一个节点可以存储多个Key，有n个key就有n个指针指向其他节点

2.所有数据都是存储在叶子节点中，非叶子节点只用于索引数据

3.叶子节点间形成了一条双向链表，便于数据的排序及区间范围查询。



下面举一个查询例子：

假如我需要查询索引为53的数据。

首先查看根节点，53大于38，但小于67，所以查找索引38下指针指向的节点。

继续查询下一个节点，53大于47，但小于55，所以查找索引47下指针指向的节点。

继续查询下一个节点，找到53这个索引，其下对应的就是要找的数据。查询完毕。



### 操作索引

#### 1.创建索引

创建索引的语法如下

```mysql
create [unique] index 索引名 on 表名(字段名,.....); 

-- 创建索引
create index idx_emp_name on tb_emp(name);
```

索引名`idx_emp_name`是一种索引的命名规范，idx表示这是一个索引，emp表示索引所属的表，name表示索引的字段。



#### 2.查看索引

查看索引的语法如下

```mysql
show index from 表名;

-- 查看索引
show index from tb_emp;
```

结果如下，可以看到有三个索引。但是我们刚刚只创建了一个索引，为什么有3个呢？第一个id字段的索引是主键，MySQL会自动为主键创建索引，主键索引的查询效率是最高的；第二个username字段，是由于该字段有一个unique，约束，表示该字段唯一，被unique约束的字段也会创建一个索引；第三个name字段才是我们刚刚创建的索引。

![image-20250316142344485](./pictures/image-20250316142344485.png)



#### 3.删除索引

删除索引的语法如下

```mysql
drop index 索引名 on 表名;

-- 删除索引
drop index idx_emp_name on tb_emp;
```



#### 4.索引的注意事项





# JDBC

## 01-JDBC简介 快速入门

### 什么是JDBC

JDBC是Java DataBase Connectivity 的缩写，是使用Java操作数据库的一套API。

实际上JDBC仅仅是Java提供的用于操作数据库的接口，是一套操作数据库的规范，它并没有具体实现如何操作数据库。因为市面上有很多种数据库，操作不同数据库的方法也会有所不同，因此Java不能为每一个数据库都提供一个操作类。而市面上的所有数据库都实现了JDBC这个操作数据库的接口，因此通过使用JDBC接口，我们就可以方便地操作所有数据库。而实现JDBC这个接口的类就是每次操作数据库时需要导入的数据库驱动。

![image-20250316155619044](./pictures/image-20250316155619044.png)





### JDBC的使用

使用jdbc的步骤如下

#### 0.首先创建工程，导入数据库驱动jar包

创建一个空工程，进入project structure设置jdk和language level

![image-20241223132000098](./pictures/image-20241223132000098.png)

然后创建一个模块，在模块里面创建一个lib文件夹，将驱动jar包放入lib文件夹并将该文件夹设置为library文件夹

![image-20241223125910477](./pictures/image-20241223125910477.png)

设置该文件夹的有效范围

![image-20241223130024971](./pictures/image-20241223130024971.png)

#### 1.注册驱动

```java
Class.forName("com.mysql.jdbc.Driver");
```

#### 2.获取连接

```java
String url = "jdbc:mysql://127.0.0.1:3306/testdb";
String username = "root";
String password = "对应的数据库密码";
Connection conn = DriverManager.getConnection(url,username,password);
```

#### 3.定义sql语句

```java
String sql = "update account set money = 2000 where id =1 ";
```

#### 4.获取执行sql对象

```java
Statement stmt = conn.createStatement();
```

#### 5.执行sql

有多种执行sql语句的方法：`executeQuery(String sql)`用于执行查询语句，返回结果为`ResultSet`结果集对象，`executeUpdate(String sql)`用于执行修改语句，返回结果为受影响行数

```java
int count = stmt.executeUpdate(sql);			//返回结果为受影响的行数
```

#### 6.处理返回结果

```java
System.out.println(count);
```

如果处理的是结果集，就需要一个字段一个字段地来处理

例如

```java
List<User> userList = new ArrayList<>();
    while (resultSet.next()){
        int id = resultSet.getInt("id");
        String name = resultSet.getString("name");
        short age = resultSet.getShort("age");
        short gender = resultSet.getShort("gender");
        String phone = resultSet.getString("phone");

        User user = new User(id,name,age,gender,phone);
        userList.add(user);
    }
```

#### 7.释放资源

```java
stmt.close();
conn.close();		//释放数据库连接
```

![image-20241223134341400](./pictures/image-20241223134341400.png)

修改成功

![image-20241223134357995](./pictures/image-20241223134357995.png)

## 02-JDBC-API详解-DriverManager

DriverManager是驱动管理类，其主要有以下两个作用：

1.注册驱动

2.获取sql连接对象

DriverManager是一个工具类，其函数都是静态函数，因此可以直接通过类名来访问成员函数

```java
Connection conn = DriverManager.getConnection(url,username,password);
```

url的定义详解如下

```java
//设置url的完整语法
String url = "数据库协议://数据库ip地址:数据库端口号/要访问的数据库名?参数键值对1&参数键值对2....";
//后面的键值对可以进行某些设置，比如配置useSSL=false参数，禁用安全连接方式，解决警告提醒
//如果是访问本地数据库并且端口为3306，ip地址还可以省略
String url = "jdbc:mysql:///testdb?useSSL=false";
```

警告提醒：

![image-20241223140302587](./pictures/image-20241223140302587.png)

禁用安全连接方式，解决警告提醒

![image-20241223140741243](./pictures/image-20241223140741243.png)

## 03-JDBC-API详解-Connection

Connection是数据库连接对象，其主要作用如下：

1.获取执行sql的对象

2.管理事务

这里先讲管理事务，第一个后面讲

```java
//connection提供了三个管理事务的函数
//1.setAutoCommit(boolean autoCommit);	true为自动提交事务，false为手动提交事务
//2.commit()							提交事务
//3.roolback()							回滚事务
```

修改前面快速入门代码，使其要么修改两个数据，要么一个也不修改

```java
//1.注册驱动
Class.forName("com.mysql.jdbc.Driver");
//2.获取连接
String url ="jdbc:mysql:///testdb?useSSL=false";
String username="root";
String password="gt1303190518";
Connection conn = DriverManager.getConnection(url,username,password);
//3.定义sql语句
String sql1="update account set money=2000 where id = 1";
String sql2="update account set money=3000 where id = 2";
//4.获取执行sql对象
Statement stmt = conn.createStatement();
conn.setAutoCommit(false);                  //设置手动提交事务
        try {

            //5.执行sql语句
            int count1 = stmt.executeUpdate(sql1);
            int i=3/0;							//这里会抛出异常，使得第一个sql成功执行，第二个sql不能执行
            
            int count2 = stmt.executeUpdate(sql2);
            //6.处理执行结果
            System.out.println(count1);
            System.out.println(count2);
            conn.commit();                      //提交事务
        } catch (SQLException e) {
            conn.rollback();                    //捕获到错误就回滚
            throw new RuntimeException(e);
        }
//7.释放资源
stmt.close();
conn.close();
```

如果没有报错，数据会被正常修改，但如果让int i = 3/0;这行代码生效的话，结果如下

![image-20241223153651936](./pictures/image-20241223153651936.png)

![image-20241223153703910](./pictures/image-20241223153703910.png)

控制台第一行打印出来的1就是第一个sql执行的结果，sql1成功修改了一行数据，但数据库里面并没有看到sql1的修改，因为事务被回滚了，此时如果我们再把回滚、提交、设置自动提交的代码去掉，就会发现sql1的修改成功了，但sql2没有执行

![image-20241223154001917](./pictures/image-20241223154001917.png)

## 04-JDBC-API详解-Statement

Statement的作用是执行sql语句，其提供两种执行函数

1.执行DML、DDL语句，即对数据库的修改语句

```java
int executeUpdate(sql);					//返回受影响的行数
```

前面快速入门里的代码就是这个

2.执行DQL语句，即查询语句

```java
ResultSet executeQuery(sql);			//返回ResultSet结果集对象
```

## 05-JDBC-API详解-ResultSet

ResultSet是查询语句的结果的集合，如果要取出里面的数据，就要通过一个抽象的“光标”一行一行去访问里面的数据，其提供了以下用于访问里面数据的函数

#### 1.next()函数

```java
boolean next();					//将访问光标向下移动一行，并判断该行是否是有效行，有效行就返回true
```

#### 2.getxxx函数

```java
xxx getxxx(索引或字段名);			//xxx代表数据类型，索引是指要获取的数据在第几列，从1开始
int getInt("id");
String getString(2);
```

总获取数据方式是通过一个while循环来遍历所有行

```java
		//1.注册驱动
        Class.forName("com.mysql.jdbc.Driver");
        //2.获取连接
        String url ="jdbc:mysql:///testdb?useSSL=false";
        String username="root";
        String password="gt1303190518";
        Connection conn = DriverManager.getConnection(url,username,password);
        //3.定义sql语句
        String sql1="select * from account";
        //4.获取执行sql对象
        Statement stmt = conn.createStatement();
        //5.执行sql语句
        ResultSet res=stmt.executeQuery(sql1);
        //6.获取查询的数据
        while(res.next()){
            System.out.println(res.getInt(1));          //通过索引来获取数据
            System.out.println(res.getString("name"));  //通过字段名来获取数据
            System.out.println(res.getDouble(3));
            System.out.println("---------------");
        }
        //7.释放资源
        res.close();
        stmt.close();
        conn.close();
```

![image-20241223160816926](./pictures/image-20241223160816926.png)

#### 案例

查询account账户表数据，将其封装为Account对象中，并且存储到ArrayList集合中

首先建立一个Account的实体类

![image-20241223161651156](./pictures/image-20241223161651156.png)

然后将数据封装成Account对象并打印出来

```java
public static void main(String[] args) throws ClassNotFoundException, SQLException {
        //1.注册驱动
        Class.forName("com.mysql.jdbc.Driver");
        //2.获取连接
        String url ="jdbc:mysql:///testdb?useSSL=false";
        String username="root";
        String password="gt1303190518";
        Connection conn = DriverManager.getConnection(url,username,password);
        //3.定义sql语句
        String sql1="select * from account";
        //4.获取执行sql对象
        Statement stmt = conn.createStatement();
        //5.执行sql语句
        ResultSet res=stmt.executeQuery(sql1);
        //6.获取查询的数据
        //建立list集合
        ArrayList<Account> list = new ArrayList<>();
        while(res.next()){
            //创建实体
            Account account=new Account();

            account.setId(res.getInt(1));          //通过索引来获取数据
            account.setName(res.getString("name"));  //通过字段名来获取数据
            account.setMoney(res.getDouble(3));
            list.add(account);
        }
        System.out.println(list);
        //7.释放资源
        res.close();
        stmt.close();
        conn.close();
    }
```

![image-20241223162623352](./pictures/image-20241223162623352.png)

 

## 06-JDBC-API详解-PreparedStatement-SQL注入

PreparedStatement是预编译sql语句执行类，是Statement的一个继承类，同样是用来执行sql语句的，但是它可以防止SQL注入。

#### 什么是SQL注入

SQL注入是通过操作输入的数据来修改事先定义好的SQL语句，以达到执行代码对服务器进行攻击的方法。

```java
//通常我们用于查询的sql语句是这样定义的
String name="username";
String pwd="123";				//这是一验证用户登录的查询语句
//sql语句是通过字符串拼接出来的
String sql="select * from tb_user where username= '"+name+"'and password='"+pwd+"'";

//然后根据查询结果，如果查询结果大于0，则表示存在用户且密码正确，则允许登录，否则不允许登录
```

而sql注入就是通过输入相关字符来达到修改sql语句的目的

```java
//举个例子
//这里不管用户名输什么
//只要对password输入
String pwd = "0' or '1' = '1'";
//此时sql语句就变成了 select * from tb_user where username = 'username' and password='0' or '1'= '1'
//而这个sql语句由于后面的or ‘1’=’1‘,不管怎样都能查出所有的数据，也就是会导致最终判断结果>0成立，从而使得可以登录成功

```

输入正确的账号密码登录

![image-20241223165421504](./pictures/image-20241223165421504.png)

sql注入方式登录成功

![image-20241223165831338](./pictures/image-20241223165831338.png)

## 06-JDBC-API详解-PreparedStatement

如何解决sql注入，这就要用到PreparedStatement。

### 使用PreparedStatement的步骤

#### 1.获取PreparedStatement对象

```java
//要使用PreparedStatement的话就要先定义sql语句，且语句中的参数值要用?替代
//定义sql语句
String sql="select * from tb_user where username=? and password = ?";
//获取对象,将sql语句传入构造函数来获取PreparedStatement对象
Connection conn = DriverManager.getConnection(url,username,password);			//先获取连接
PreparedStatement pstmt=conn.preparedStatement(sql);
```



#### 2.设置参数值

```java
//PreparedStatement有 setxxx(参数1,参数2)函数
//xxx代表数据类型
//参数1代表?的位置,从1开始
//参数2代表要替换的值
pstmt.setString(1,name);
pstmt.setString(2,pwd);
```

#### 3.执行sql

```java
//通过PreparedStatement执行sql语句不需要再传递sql语句
//直接使用函数executeUpdate()或executeQuery()来执行
pstmt.executeQuery();
```

```java
public static void main(String[] args) throws ClassNotFoundException, SQLException {
        //1.注册驱动
        Class.forName("com.mysql.jdbc.Driver");
        //2.获取连接
        String url ="jdbc:mysql:///testdb?useSSL=false";
        String username="root";
        String password="gt1303190518";
        Connection conn = DriverManager.getConnection(url,username,password);
        //3.定义sql语句
        String name="fjdaklfjla";
        String pwd="0' or '1' = '1";
        String sql1="select * from tb_user where username=?and password=?";
        System.out.println(sql1);
        //4.获取执行sql对象
        PreparedStatement pstmt = conn.prepareStatement(sql1);
        //设置参数值
        pstmt.setString(1,name);
        pstmt.setString(2,pwd);
        //5.执行sql语句
        ResultSet res=pstmt.executeQuery();
        //6.处理执行结果
        if(res.next()){
            System.out.println("登录成功");
        }else{
            System.out.println("登录失败");
        }
        //7.释放资源
        res.close();
        pstmt.close();
        conn.close();
    }
```





通过这样修改sql注入便不再生效

![image-20241223171655268](./pictures/image-20241223171655268.png)

#### 注意事项

使用预编译性能会更好，但mysql默认是没有开启这个功能的，所以我们要在获取与数据库连接的时候去将它打开

```java
String url = "jdbc:mysql:///testdb?useSSL=false&useServerPrepStmts=true";
String username = "root";
String password = "对应的数据库密码";
Connection conn = DriverManager.getConnection(url,username,password);
```

## 09-数据库连接池-简介&Druid使用

### 什么是数据库连接池

Java提供了一个接口`DataSource`，所有连接池都要实现这个接口。

连接池有如下几个优点：

1.资源重用

2.提升系统响应速度

3.避免数据库连接遗漏



数据库连接池是一个容器，负责分配、管理数据库连接（Connection）。

连接池允许应用程序重复使用一个现有的数据库连接，而不是重新创建一个新连接

如果一个应用程序获取了连接但一直没有使用，那么过了一定的时间，连接池会自动回收空闲的连接，从而避免后面的应用程序没有连接可用的情况。



### 如何切换springboot项目的连接池

下面介绍目前常用的两个连接池

1.Druid（德鲁伊），这是阿里巴巴开源的连接池

2.Hikari（日语中是“光”的意思），这个连接池是springboot项目的默认连接池

如下图所示，这是一个springboot项目的查询输出结果，看到结果的最后两行，可以发现Hikari这个词，这说明springboot默认用的是Hikari连接池。

![image-20250316162834369](./pictures/image-20250316162834369.png)



如果想要切换springboot的连接池，可以采取以下步骤：

这里以切换成Durid连接池为例子

1.导入Durid连接池的依赖

```xml
<dependency>
   <groupId>com.alibaba</groupId>
   <artifactId>druid-spring-boot-starter</artifactId>
   <version>1.2.8</version>
</dependency>
```

如果springboot版本为3.x.x，还需要再添加下面这个依赖

```xml
<dependency>
   <groupId>com.alibaba</groupId>
   <artifactId>druid-spring-boot-3-starter</artifactId>
   <version>1.2.21</version>
</dependency>
```



2.编写数据库连接的配置文件

配置文件为resources文件夹下的`application.properties`文件

```properties
#驱动类名称
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
#数据库连接的url
spring.datasource.url=jdbc:mysql://localhost:3306/mybatis
#连接数据库的用户名
spring.datasource.username=root
#连接数据库的密码
spring.datasource.password=1234
```



此时可以发现springboot项目使用的连接池变成了Durid

![image-20250316163731933](./pictures/image-20250316163731933.png)







### Druid的使用

Druid（德鲁伊）使用步骤

#### 1.导入jar包

#### 2.定义配置文件

```properties
driverClassName=com.mysql.jdbc.Driver
url=jdbc:mysql:///testdb?useSSL=false&useServerPrepStmts=true
username=root
password=gt1303190518
#最小连接数
initialSize=5
#最大连接数
maxActive=10
#最大等待时间
maxWait=3000
```



#### 3.加载配置文件

```java
Properties prop = new Properties();				
prop.load(new FileInputStream("src/druid.properties"));			//记得做异常处理
```

#### 4.获取数据库连接池对象

```java
DataSource datasource=DuridDataSourceFactory.createDataSource(prop);		
```

#### 5.获取连接

```java
Connection connection = datasource.getConnection();
```

```java
public class JDBCDemo {
    public static void main(String[] args) throws Exception {
        //1.导入Durid jar包
        //2.定义配置文件
        //3.加载配置文件
        Properties prop = new Properties();
        prop.load(new FileInputStream("src/druid.properties"));
        //4.获取数据库连接池对象
        DataSource dataSource= DruidDataSourceFactory.createDataSource(prop);       //根据配置文件建立连接池
        //5.获取连接
        Connection connection= dataSource.getConnection();
        System.out.println(connection);
    }
}
```

![image-20241223215514571](./pictures/image-20241223215514571.png)



# Maven&MyBatis

## Day04-01.maven-课程介绍

### 什么是maven

maven是apache旗下的一个开源项目，是一款用于管理和构建Java项目的工具。

maven的主要作用有以下三点

#### 1.依赖管理

在一个Java项目中，可能会使用到很多其他的技术，比如junit、logback等。此时如果没有maven，就需要手动下载导入很多jar包，会非常繁琐。但是有了maven，我们只需要在maven项目的`pom.xml`文件中写入要用的依赖及其版本，maven就会自动帮我们导入jar包，并更新版本，这样既方便，同时也解决了jar包间的版本冲突问题

#### 2.统一项目结构

开发Java项目有很多平台，如：idea、eclipse，这些平台的项目文件都会有所不同，这就会导致一个问题：一个平台的创建的项目文件在另一个平台打开会出现问题。而使用maven后，maven会统一项目结构，这样就算是不同的平台，打开同一个项目文件也不会出现问题

#### 3.项目构建

一个Java项目一般会经历编译、测试、打包、发布这些流程，maven将这些流程进行了统一管理，提供了统一的命令来执行这些操作，且这些操作是跨平台的，不管是windows系统还是linux系统，都可以使用maven的命令来构建项目



## Day04-03.maven-idea集成-配置及创建maven项目

### 在idea中配置maven

为全局配置maven，这样创建的每一个项目都可以使用maven，就不用一个一个去配置了

1.首先来到idea的主界面，找到Customize

![image-20250310173001076](./pictures/image-20250310173001076.png)

2.进入All settings，找到Build Tools(构建工具)下的maven设置，配置maven的安装目录以及maven配置文件和本地仓库

![image-20250310173048702](./pictures/image-20250310173048702.png)

3.进入Complier，找到Java Compiler，设置Java的字节码版本，字节码版本要和使用的jdk版本对上

![image-20250310173308373](./pictures/image-20250310173308373.png)





### 在Idea中创建maven项目

在创建项目时选择maven项目，配置GroupId（组织名）、ArtifactId（模块名）、项目路径等

![image-20250310174626698](./pictures/image-20250310174626698.png)



### 在Idea中导入maven项目

方法一：

点击右侧的maven工具条，点＋号，添加maven项目

![image-20250310190413205](./pictures/image-20250310190413205.png)

选择要添加项目的pom文件

![image-20250310190453887](./pictures/image-20250310190453887.png)



方法二：

选择左上角的File，选择project modules

![image-20250310190623967](./pictures/image-20250310190623967.png)

进入后选择modules标签，再点+号，选择import Module

![image-20250310190710881](./pictures/image-20250310190710881.png)

选择要导入项目的pom文件即可导入

![image-20250310190739139](./pictures/image-20250310190739139.png)





## Day04-07.maven-依赖管理-依赖范围

### 依赖范围

![image-20250310192718517](./pictures/image-20250310192718517.png)

依赖范围有下面四个

![image-20250310192734741](./pictures/image-20250310192734741.png)



## Day04-08.maven-依赖管理-生命周期

### maven生命周期

maven的生命周期就是为了对所有maven项目的构建过程进行抽象和统一。可以把它理解为对项目的一种操作

maven有3套独立的生命周期

1.clean：清理工作

2.default：核心工作，如：编译、测试、打包、部署等

3.site：生成报告、发布站点等（用的比较少）

maven的每套生命周期包含很多阶段，如下图所示

![image-20250310193331957](./pictures/image-20250310193331957.png)

重点关注5个阶段：clean、compile、test、package、install

在同一套生命周期中，每个阶段的执行都会依赖于前面的阶段，如要执行package，前面compile、test会先执行，然后才执行package。要注意clean不会执行，因为clean属于claen生命周期，与package不属于同一生命周期

这5个阶段的作用如下图所示

![image-20250310193538456](./pictures/image-20250310193538456.png)

也可以选择要跳过某个阶段，比如要执行install，想跳过test阶段，可以在maven工具栏中选择test然后点那个像禁止符号一样的图标，这样就可以跳过该阶段，可以看到test阶段被划了一条横线，表示跳过该阶段

![image-20250310194215211](./pictures/image-20250310194215211.png)





### 如何执行生命周期

方式一：

使用maven工具栏，直接选择要执行的生命周期。

![image-20250310194455126](./pictures/image-20250310194455126.png)

图中还有一个Plugins栏，它下面有很多插件，实际上当我们执行生命周期某个阶段时，就是靠下面这些插件来执行的



方式二：

直接使用命令行

```cmd
mvn 要执行的阶段名
```

比如

```cmd
mvn package
```



## Day08-13.MyBatis-入门-课程介绍

### 什么是MyBatis

MyBatis是一款持久层的框架，用于简化JDBC的开发。





## 02-MyBatis快速入门

下面的MyBatis快速入门是基于springboot框架下的

## 准备工作

### 1.准备工作

#### 1).创建一个springboot项目并整合mybatis

如下图所示，在创建springboot项目的时候要勾选mybatis的依赖，以及mysql的驱动，如果数据库不是mysql就不选mysql驱动而选其他数据库的驱动

![image-20250316145548987](./pictures/image-20250316145548987.png)

项目创建好后可以在pom文件中看到以下依赖

![image-20250316150040405](./pictures/image-20250316150040405.png)



#### 2).创建数据表和实体类

这一步在下面的编码部分会有，mybatis会将从数据库获取到的数据封装成一个实体类对象。

实体类对象的数据类型推荐使用包装类，实体类的变量名要与数据库表的字段名保持一致。



### 2.创建工程模块，导入MyBatis依赖坐标

如果是通过springboot项目创建mybatis，会自动导入相关依赖。所以这一步看情况使用，如果没有用springboot来创建mybatis框架，就可以自己导入依赖坐标。

mybatis依赖坐标可以在mybatis官网找到 [入门_MyBatis中文网](https://mybatis.net.cn/getting-started.html)

```xml
<dependency>
  <groupId>org.mybatis</groupId>
  <artifactId>mybatis</artifactId>
  <version>x.x.x</version>
</dependency>
```

![image-20241224085200417](./pictures/image-20241224085200417.png)

### 3.编写mybatis核心配置文件

在学这个部分的知识时我看的是两个视频，这两个视频一个是在springboot框架下的，另一个是没有的，因此这里记录两种编写配置文件的方法



#### 1).springboot框架下

在springboot框架下，resources文件夹下有一个application.properties文件，在这里编写mybatis相关配置

配置编写内容如下

```properties
#驱动类名称
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
#数据库连接的url
spring.datasource.url=jdbc:mysql://localhost:3306/mybatis
#连接数据库的用户名
spring.datasource.username=root
#连接数据库的密码
spring.datasource.password=122333
```

如下图

![image-20250316151429424](./pictures/image-20250316151429424.png)



#### 2).非springboot框架下

mybatis配置文件可以替换连接信息，解决硬编码问题

在mybatis官方入门案例中找到示例的配置文件，在resources文件夹中创建配置文件

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE configuration
        PUBLIC "-//mybatis.org//DTD Config 3.0//EN"
        "http://mybatis.org/dtd/mybatis-3-config.dtd">
<configuration>
    <environments default="development">
        <environment id="development">
            <transactionManager type="JDBC"/>
            <dataSource type="POOLED">
                <!--连接信息-->
                <property name="driver" value="com.mysql.jdbc.Driver"/>	<!--配置驱动-->
                <property name="url" value="jdbc:mysql:///mybatis?useSSL=false"/>	<!--配置数据库地址-->
                <property name="username" value="root"/>
                <property name="password" value=""/>			<!--配置密码-->
            </dataSource>
        </environment>
    </environments>
    <mappers>
        <mapper resource="org/mybatis/example/BlogMapper.xml"/>
    </mappers>
</configuration>
```

![image-20241224090614325](./pictures/image-20241224090614325.png)



接下来的步骤也分为springboot框架下的使用，和非springboot框架下的使用



## 编码使用

## 一、使用mapper

创建一个mapper包用于存放mapper接口

![image-20250316154103149](./pictures/image-20250316154103149.png)

UserMapper的代码如下

```java
import com.example.pojo.User;
import org.apache.ibatis.annotations.Mapper;
import org.apache.ibatis.annotations.Select;

import java.util.List;

//这个注解表示这个接口是mybatis的一个mapper接口
//在运行时，带有Mapper注解的接口会自动生成一个该接口的实现类对象(这里涉及到的知识是Java的动态代理),并将该对象交给IOC容器管理，这个对象实际上就是一个代理对象
@Mapper
public interface UserMapper {
    //查询所有用户信息
    //使用Select注解表示是查询语句，执行该方法的时候会自动执行注解中写的sql语句，并将返回该方法的的结果
    @Select("select * from user")
    public List<User> list();
}
```

单元测试的代码

```java
import com.example.mapper.UserMapper;
import com.example.pojo.User;
import org.junit.jupiter.api.Test;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.test.context.SpringBootTest;

import java.util.List;

@SpringBootTest     //springboot整合单元测试的注解
class SpringbootMybatisQuickstartApplicationTests {

    @Autowired      //该接口运行时会自动创建一个实现类对象，并将该对象交给IOC容器，因此可以通过依赖注入来使用该对象
    private UserMapper userMapper;

    @Test
    public void testList(){
        List<User> users = userMapper.list();
        users.stream().forEach(e->{
            System.out.println(e);
        });
    }

}
```

运行结果，可以看到查询出来的用户信息

![image-20250316154247185](./pictures/image-20250316154247185.png)



## 二、使用xml映射文件

xml映射文件的规范如下

![image-20250317190241436](./pictures/image-20250317190241436.png)

xml映射文件可以统一管理sql语句，解决硬编码问题

xml映射文件统一命名为xxxMapper.xml  xxx代表实体类

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE mapper
        PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
        "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
<!--上面三行是mybatis的约束代码，可以通过搜索mybatis官网找到-->
<mapper namespace="com.example.mapper.EmpMapper">       <!--namespace填写该xml文件对应的mapper接口的全类名-->
    <!--在mapper标签内部写诸如select、delete等sql语句-->
    <!--id表示该sql语句对应的方法名，resultType表示sql语句执行结果的单挑记录所封装的类型，如查询员工信息，可能返回多条员工信息，那么单条记录所封装的类型就是实体类Emp-->
    <select id="select3" resultType="com.example.pojo.Emp">
        <!--在select标签内部填写具体的查询语句-->
        select * from emp where name like '%${name}%' and gender = #{gender} and entrydate between #{begin} and #{end};
    </select>
</mapper>
```

此时mapper接口中的方法就不需要使用`@Select`这些注解了

```java
import com.example.pojo.Emp;
import org.apache.ibatis.annotations.*;

import java.time.LocalDate;
import java.util.List;

@Mapper
public interface EmpMapper {
    //直接声明一个和xml文件中的sql语句对应的上的抽象方法即可
    public List<Emp> select3(String name, Integer gender, LocalDate begin,LocalDate end);

}
```





## 三、比较原始的使用方法

#### a.定义实体类

```java
public class User {
    private Integer id;
    private String username;
    private String password;
    private String gender;
    private String addr;

    @Override
    public String toString() {
        return "User{" +
                "id=" + id +
                ", username='" + username + '\'' +
                ", password='" + password + '\'' +
                ", gender='" + gender + '\'' +
                ", addr='" + addr + '\'' +
                '}';
    }

    public Integer getId() {
        return id;
    }

    public void setId(Integer id) {
        this.id = id;
    }

    public String getUsername() {
        return username;
    }

    public void setUsername(String username) {
        this.username = username;
    }

    public String getPassword() {
        return password;
    }

    public void setPassword(String password) {
        this.password = password;
    }

    public String getGender() {
        return gender;
    }

    public void setGender(String gender) {
        this.gender = gender;
    }

    public String getAddr() {
        return addr;
    }

    public void setAddr(String addr) {
        this.addr = addr;
    }
}
```



#### b.加载核心配置文件，获取SqlSessionFactory对象

```java
String resource = "配置文件的路径";
InputStream inputStream = Resources.getResourceAsStream(resource);
SqlSessionFactory sqlSessionFactory = new SqlSessionFactoryBuilder().build(inputStream);
```



#### c.获取SqlSession对象，执行sql语句

```java
SqlSession sqlSession=sqlSessionFactory.openSession();
//这里是通过使用xml文件的命名空间来定位sql语句的，User.selectAll即使用命名空间为User下的selectAll语句
List<User> users = sqlSession.selectList("User.selectAll");		
System.out.println(users);
```

#### d.释放资源

```java
sqlSession.close();
```

```java
public static void main(String[] args) throws Exception {
        //1.加载配置文件
        String resource = "mybatis-config.xml";
        InputStream inputStream = Resources.getResourceAsStream(resource);
        SqlSessionFactory sqlSessionFactory = new SqlSessionFactoryBuilder().build(inputStream);
        //2.获取SqlSession对象
        SqlSession sqlSession=sqlSessionFactory.openSession();
        List<User> users = sqlSession.selectList("User.selectAll");
        System.out.println(users);
        //3.释放资源
        sqlSession.close();

    }
```

![image-20241224092801548](./pictures/image-20241224092801548.png)

非springboot框架下的使用方式可以通过使用mapper代理来优化，接着看下面

## 04-Mapper代理开发

不使用Mapper代理的方法

```java
List<User> users = sqlSession.selectList("User.selectAll");			//是"命名空间.id"的形式
```

我们需要去写对应映射文件里面定义好的命名空间和sql语句的id，不是很方便

而使用Mapper代理开发，我们可以将对应的映射文件里面的sql语句像使用类的成员函数一样去使用，这样使用起来会很方便

```java
SqlSession sqlSession=sqlSessionFactory.openSession();
//执行sql语句改为用Mapper代理的方式
//获取代理接口对象
UserMapper userMapper=sqlSession.getMapper(UserMapper.class);
//执行语句
List<User> users=userMapper.selectAll();
```

为什么会很方便，看下图，当我要使用映射文件里面的sql语句时，它自动弹出来了，就像一个成员函数一样

![image-20241224102821505](./pictures/image-20241224102821505.png)

### 使用步骤

#### 1.定义与sql映射文件同名的Mapper接口，并将Mapper接口和sql映射文件放在同一目录文件下

这里的放在同一目录文件下指的是Mapper接口所在的目录层次结构和映射文件所在的目录层次结构一致，如下所示

这里看起来好像没在同一目录下，因为Mapper在java目录中，而映射文件在resources中，但其实，只要它们的目录层次结构一样就没问题，比如说这里的Mapper在com.example.Mapper下，而映射文件也在com.example.Mapper下，只要是这样放的，在编译的时候，他们就会放到一起去。

![image-20241224103140184](./pictures/image-20241224103140184.png)

下图是编译后的文件结构，可以发现接口和映射文件已经放到同一文件夹下了

![image-20241224103448386](./pictures/image-20241224103448386.png)

#### 2.设置sql映射文件的namespace属性为Mapper接口全限定名

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE mapper
        PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
        "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
<mapper namespace="com.example.Mapper.UserMapper">			<!--Mapper接口的全限定名-->
    <select id="selectAll" resultType="com.example.entity.User">
        select * from tb_user;
    </select>
</mapper>
```

#### 3.在Mapper接口中定义方法（不用实现）

定义的方法名就是映射文件中sql语句的id，返回类型对应位sql语句执行完的返回类型

```java
public interface UserMapper {
    List<User> selectAll();				//selectAll语句是查询所有
}
```

#### 4.编码

```java
//1.首先通过SqlSession的getMapper方法获取Mapper接口的代理对象
UserMapper userMapper=sqlSession.getMapper(UserMapper.class);
//2.调用对应方法来执行
List<User> users=userMapper.selectAll();
```

```java
public class mybatisDemo {
    public static void main(String[] args) throws Exception {
        //1.加载配置文件
        String resource = "mybatis-config.xml";
        InputStream inputStream = Resources.getResourceAsStream(resource);
        SqlSessionFactory sqlSessionFactory = new SqlSessionFactoryBuilder().build(inputStream);
        //2.获取SqlSession对象
        SqlSession sqlSession=sqlSessionFactory.openSession();
        //执行sql语句改为用Mapper代理的方式
        //获取代理接口对象
        UserMapper userMapper=sqlSession.getMapper(UserMapper.class);
        //执行语句
        List<User> users=userMapper.selectAll();
        System.out.println(users);
        //3.释放资源
        sqlSession.close();

    }
}
```

![image-20241224104050169](./pictures/image-20241224104050169.png)

### 注意事项

如果Mapper接口名称和sql映射文件名称相同，并在同一目录下，则可以使用包扫描的方式简写mybatis配置文件里面的sql映射文件的加载

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE configuration
        PUBLIC "-//mybatis.org//DTD Config 3.0//EN"
        "http://mybatis.org/dtd/mybatis-3-config.dtd">
<configuration>
    <environments default="development">
        <environment id="development">
            <transactionManager type="JDBC"/>
            <dataSource type="POOLED">
                <!--连接信息-->
                <property name="driver" value="com.mysql.jdbc.Driver"/>
                <property name="url" value="jdbc:mysql:///mybatis"/>
                <property name="username" value="root"/>
                <property name="password" value="gt1303190518"/>
            </dataSource>
        </environment>
    </environments>
    <mappers>
<!--        <mapper resource="UserMapper.xml"/>-->
        <package name="com.example.Mapper"/>			<!--包扫描方式-->
    </mappers>
</configuration>
```



## **05-MyBatis核心配置文件**

所有配置属性详解可见官方文档：[配置_MyBatis中文网](https://mybatis.net.cn/configuration.html)

#### environments

环境配置是用来配置数据库连接的，可以配置多个数据库连接

```xml
<environments default="development">            <!--使用default属性来更改当前使用的数据库，现在是开发环境的数据库，可以改成对应要使用数据库环境的id-->
        <!--第一个数据库连接配置，开发环境的数据库-->
        <environment id="development">
            <transactionManager type="JDBC"/>
            <dataSource type="POOLED">
                <!--连接信息-->
                <property name="driver" value="com.mysql.jdbc.Driver"/>
                <property name="url" value="jdbc:mysql:///mybatis"/>
                <property name="username" value="root"/>
                <property name="password" value="gt1303190518"/>
            </dataSource>
        </environment>
        <!--第二个数据库连接配置，测试环境的数据库-->
        <environment id="test">
            <transactionManager type="JDBC"/>
            <dataSource type="POOLED">
                <!--连接信息-->
                <property name="driver" value="com.mysql.jdbc.Driver"/>
                <property name="url" value="jdbc:mysql:///mybatis"/>
                <property name="username" value="root"/>
                <property name="password" value="gt1303190518"/>
            </dataSource>
        </environment>
    </environments>
```

#### typeAliases

类型别名可为 Java 类型设置一个缩写名字。 它仅用于 XML 配置，意在降低冗余的全限定类名书写。

```xml
<typeAliases>
    <typeAlias alias="User" type="com.example.entity.User"></typeAlias>
    <!--使用包扫描方式配置别名-->
    <package name="com.example.entity"/>                <!--使用包扫描方式配置别名，自动将类名作为别名-->
</typeAliases>
```

在配置文件中设置了别名后，映射文件中使用类就可以直接使用别名而不用全限定类名书写

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE mapper
        PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
        "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
<mapper namespace="com.example.Mapper.UserMapper">
    <select id="selectAll" resultType="User">		<!--使用User别名-->
        select * from tb_user;
    </select>
</mapper>
```

 

## MyBatis使用案例

有下面一张员工信息表，要求通过MyBatis对这张表进行增删改查操作

![image-20250317085507903](./pictures/image-20250317085507903.png)

### 1.删除

根据id删除员工信息

```java
import org.apache.ibatis.annotations.Delete;
import org.apache.ibatis.annotations.Mapper;

@Mapper
public interface EmpMapper {

    //使用delete注解表示删除操作
    @Delete("delete from emp where id = #{id}")
    /*根据id来删除数据，不能直接在sql语句中将id写死了，如delete from emp where id = 17
    * 可以使用MyBatis提供的参数占位符#{}来表示该mapper方法接收的参数，#{id}就表示接收delete的id参数
    * 如果mapper接口方法形参只有一个，那么#{}里面的属性名可以随便写，#{value} #{a}啥的都行，反正只有一个，咋传都对。
    */
    public void delete(Integer id);
    //删除操作是有返回值的，会返回影响的行数，使用下面的方法可以得到删除操作的返回值
    //public int delete(Integer id);
}
```



### 2.预编译SQL

我们可以打开MyBatis的日志，查看MyBatis的底层到底执行了什么样的SQL语句

在配置文件中添加下面代码

```properties
#打开MyBatis的日志，将其输出到控制台
mybatis.configuration.log-impl=org.apache.ibatis.logging.stdout.StdOutImpl
```

此时我们再次执行，就可以在控制台中看到MyBatis的日志

![image-20250317091044621](./pictures/image-20250317091044621.png)



日志中有下面这三行代码

```
==>  Preparing: delete from emp where id = ?
==> Parameters: 17(Integer)
<==    Updates: 0
```

第一行是执行的SQL语句，可以返现id后面有一个`?`，这个就是我们使用`#{}`参数占位符的结果。

第二行是mapper接口方法的形参，在执行sql语句的时候，会将这个形参和sql语句中的`?`替换。

以上这种形式的SQL被称为预编译SQL



使用预编译SQL有下面两点优势：

1.性能更高

MySQL执行sql语句的时候并不是马上执行的，而是要执行下图中的几个步骤。1.sql语法检查 2.优化sql 3.编译sql ，这3步完成后，mysql会将编译好的sql语句进行缓存，如果下次有同样的sql就直接从缓存中取出。

而由于这个机制，如果采用普通的sql语句，如：每次删除员工信息都带上id值，那么每次都会因为id值不同导致sql语句不同，而sql语句不同就不能从缓存中取出，所以每次删除操作都要重新编译。

但是如果使用的是预编译sql，使用`?`来代替id值，此时不管id值是多少，sql语句都还是`delete from emp where id=?`，那么就只用编译一次这个sql语句，后面再次进行删除操作时只需要从缓存中取出该sql语句，然后用id值替换`?`即可，这种方式只用编译一次sql语句。

因此预编译sql的性能更高

![image-20250317091855756](./pictures/image-20250317091855756.png)

2.更安全，可以防止SQL注入（SQL注入是啥？直接在本笔记中搜SQL注入，就可以找到对应的笔记）



Mybatis提供了两种参数占位符

#{}和${}

![image-20250317093455155](./pictures/image-20250317093455155.png)

### 3.新增

新增员工信息

mapper接口代码

```java
import com.example.pojo.Emp;
import org.apache.ibatis.annotations.Insert;
import org.apache.ibatis.annotations.Mapper;

@Mapper
public interface EmpMapper {
    //使用Insert注解来表示插入操作
    @Insert("insert into emp(username, name, gender, image, job, entrydate, dept_id, create_time, update_time)" +
            " values(#{username},#{name},#{gender},#{image},#{job},#{entryDate},#{deptId},#{createTime},#{updateTime})")
    //参数占位符填实体类对象的属性，属性名一定要对的上，注意驼峰命令
    //参数传入一个实体类对象，不用传入一大堆例如：username、password、name等等形参，因为这些数据已经包含在Emp实体类对象里面了
    public void insert(Emp emp);
}
```

但是在测试时出现了找不到符号错误，如下图所示

![image-20250317161208640](./pictures/image-20250317161208640.png)

原因在实体类上，实体类使用了lombok注解，但是并没有生效，可以查看编译后的实体类，如下图，可以看到编译后的实体类并没有getter、setter等方法，说明lombok的注解没有生效。

![image-20250317161518782](./pictures/image-20250317161518782.png)

我上网搜了一下原因，发现可能是手动配置了插件路径的问题，如下图，我将配置插件路径的代码注释掉

![image-20250317161707607](./pictures/image-20250317161707607.png)

重新刷新maven依赖，再使用maven的clean操作清除前面的编译文件，再重新启动测试，此时测试成功了，可以看到mybatis的日志。

![image-20250317161850353](./pictures/image-20250317161850353.png)

这时我们再看看编译后的实体类文件，可以看到成功生成了getter、setter等方法，但是我现在暂时也不知道这个解决原理是什么

![image-20250317161944911](./pictures/image-20250317161944911.png)





### 4.主键返回

主键返回指的是在数据添加成功后，需要获取新添加数据的主键，如刚刚插入的员工信息，在插入后需要获取新插入的员工id用于回显数据。

实现主键返回需要用到`@Options`注解，其用法如下：

mapper接口代码

```java
import com.example.pojo.Emp;
import org.apache.ibatis.annotations.Insert;
import org.apache.ibatis.annotations.Mapper;
import org.apache.ibatis.annotations.Options;

@Mapper
public interface EmpMapper {
    //useGeneratedKeys代表开启主键返回，keyProperty代表要将返回的值封装到哪个属性
    @Options(useGeneratedKeys = true,keyProperty = "id")
    //使用Insert注解来表示插入操作
    @Insert("insert into emp(username, name, gender, image, job, entrydate, dept_id, create_time, update_time)" +
            " values(#{username},#{name},#{gender},#{image},#{job},#{entryDate},#{deptId},#{createTime},#{updateTime})")
    //参数占位符填实体类对象的属性，属性名一定要对的上，注意驼峰命令
    //参数传入一个实体类对象，不用传入一大堆例如：username、password、name等等形参，因为这些数据已经包含在Emp实体类对象里面了
    public void insert(Emp emp);
}
```

测试代码

```java
@Test
public void testInsert(){
   Emp emp = new Emp();
   emp.setUsername("Arthur2");
   emp.setName("亚瑟2");
   emp.setGender(1);
   emp.setImage("/img/picture.jpg");
   emp.setJob(1);
   emp.setEntryDate(LocalDate.of(2025,7,1));
   emp.setDeptId(2);
   emp.setCreateTime(LocalDateTime.now());
   emp.setUpdateTime(LocalDateTime.now());

   empMapper.insert(emp);
   //输出返回的主键
   System.out.println("主键返回的值为："+emp.getId());
}
```

在输出结果中可以看到新增数据的id

![image-20250317164452011](./pictures/image-20250317164452011.png)



### 5.更新（修改）

根据id来修改信息

mapper接口代码

```java
import com.example.pojo.Emp;
import org.apache.ibatis.annotations.*;

@Mapper
public interface EmpMapper {
	//使用Update注解来表示更新操作
    @Update("update emp set username=#{username},name=#{name},gender=#{gender}," +
            "image=#{image},job=#{job},entrydate=#{entryDate},dept_id=#{deptId},update_time=#{updateTime} where id=#{id}")
    public void update(Emp emp);
}
```

测试代码

```java
@Test
public void testUpdate(){
   Emp emp = new Emp();
   //根据id来修改
   emp.setId(29);
   emp.setUsername("Arthur1");
   emp.setName("亚瑟1");
   emp.setGender(1);
   emp.setImage("/img/picture.jpg");
   emp.setJob(1);
   emp.setEntryDate(LocalDate.of(2025,7,1));
   emp.setDeptId(2);
   emp.setCreateTime(LocalDateTime.now());
   emp.setUpdateTime(LocalDateTime.now());

   empMapper.update(emp);

}
```



### 6.查询（根据id查询）

根据id查询

mapper接口代码

```java
import com.example.pojo.Emp;
import org.apache.ibatis.annotations.*;

@Mapper
public interface EmpMapper {
    //使用Select注解表示查询操作
    @Select("select * from emp where id=#{id}")
    public Emp select(Integer id);
}
```

测试代码

```java
@Test
public void testSelect(){
   Emp emp = empMapper.select(29);
   System.out.println(emp);
}
```

结果如下

![image-20250317170758926](./pictures/image-20250317170758926.png)

但是仔细看图中的结果可以发现，后面三个字段的结果为null，这是因为数据库表的字段名和实体类的属性名对不上，如数据库表中字段名是dept_id，而实体类中的属性名是deptId。要解决这个问题有三种解决方案。

1.为字段名起别名，让别名与属性名对上

```java
//方案一，手动设置别名，让别名与属性名相同
@Select("select id, username, password, name, " +
        "gender, image, job, entrydate, " +
        "dept_id deptId, create_time createTime, update_time updateTime from emp where id=#{id}")
public Emp select1(Integer id);
```



2.使用@Results，@Result注解手动映射封装

```java
//方案二，使用@Results，@Result注解手动映射封装
@Results({
        //column代表字段名，property代表要映射到的属性名
        @Result(column = "dept_id",property = "deptId"),
        @Result(column = "create_time",property = "createTime"),
        @Result(column = "update_time",property = "updateTime")
})
@Select("select * from emp where id=#{id}")
public Emp select2(Integer id);
```



3.开启mybatis驼峰命名自动映射开关，开启后mybatis会自动将诸如:dept_id的名字自动映射到deptId这种驼峰命名

在配置文件中打开这个功能

```properties
#打开mybatis驼峰命名自动映射开关
mybatis.configuration.map-underscore-to-camel-case=true
```



通过上面三种方案，就能解决字段名与属性名对不上的问题，推荐使用第三种方案。

![image-20250317172450379](./pictures/image-20250317172450379.png)



### 7.查询（条件查询）

```java
//条件查询
@Select("select * from emp where name like '%${name}%' and gender = #{gender} " +
        "and entrydate between #{begin} and #{end} ")
public List<Emp> select3(String name, Integer gender, LocalDate begin,LocalDate end);
```

![image-20250317174904319](./pictures/image-20250317174904319.png)

这里要注意的是模糊匹配问题，由于#{}参数占位符不能放在单引号内，所以使用${}，因为${}是拼接sql。

但是使用${}拼接sql会影响性能，还会导致sql注入，为了解决这个问题，可以使用mysql提供的`concat`函数来拼接sql语句，如下

```java
//使用concat来拼接sql语句
@Select("select * from emp where name like concat('%',#{name},'%') and gender = #{gender} " +
        "and entrydate between #{begin} and #{end} ")
public List<Emp> select4(String name, Integer gender, LocalDate begin,LocalDate end);
```

结果如下，可以发现#{name}被`?`替代了，也就是成功使用了预编译sql

![image-20250317174738162](./pictures/image-20250317174738162.png)



### 8.参数名说明

早期的springboot使用mybatis时，需要额外使用`@Param`来指定形参名字，如下图

![image-20250317175138396](./pictures/image-20250317175138396.png)

这是由于早期版本编译后不会保留形参原本的名字，而是将其全变成var1,var2...这种名字，所以如果不使用`@Param`，就无法得知形参究竟是哪个值。

而较新版本的springboot在编译后会保留形参名，所以可以不使用`@Param`注解。





## MyBatis与JDBC的对比

MyBatis与JDBC的对比如下图所示

![image-20250316160753890](./pictures/image-20250316160753890.png)

### JDBC的缺点

1.每次使用JDBC需要进行注册驱动，配置数据库url等信息，但这部分信息可能会发生变动，直接写在代码里面不利于代码的修改和维护，这就是所谓的硬编码

2.使用JDBC来处理查询结果会非常繁琐

3.使用JDBC需要频繁与数据库建立连接，这会导致资源的浪费和性能的消耗



### MyBatis的优点

1.MyBatis的数据库配置是单独地写在一个配置文件中的，如果数据库配置发生变化直接修改配置文件即可，而代码不会改变

2.MyBatis会自动将查询结果封装成一个对象，不需要我们手动地一个一个处理

3.MyBatis与数据库建立连接时会用到连接池技术，这大大提高了资源地利用率和性能。





## Day08-18.Mybatis-入门-lombok工具包介绍

### lombok工具包

lombok是一个Java类库，能通过注解的形式自动生成类的构造器、getter、setter等代码。

lombok提供的注解如下

![image-20250316164819739](./pictures/image-20250316164819739.png)



### 如何使用lombok

1.导入lombok依赖

lombok的依赖如下

```xml
<!--不需要版本号，因为springboot的父工程已经规定了lombok的版本-->
<dependency>
	<groupId>org.projectlombok</groupId>
	<artifactId>lombok</artifactId>
</dependency>
```



2.为类添加注解

```java
import lombok.AllArgsConstructor;
import lombok.Data;
import lombok.NoArgsConstructor;

@Data
@NoArgsConstructor
@AllArgsConstructor
public class User {
    private Integer id;
    private String name;
    private Integer age;
    private Integer gender;
    private String phone;
    
}
```



### lombok的原理

lombok实际上就是在编译的时候根据注解为类添加相应的代码，比如如果该类被`@Data`标记，那么在编译时就会为该类加上getter、setter、toString、equals和hashCode方法。

查看上面使用了lombok的User类编译后的字节码，如下图，可以发现User的getter、setter等相关方法。

![image-20250316165508566](./pictures/image-20250316165508566.png)



此外还要注意的是，如果要使用lombok，还需要安装一个lombok插件，如下图所示，不过这个插件现在idea会自动安装，所以可以不用管。

![image-20250316165844963](./pictures/image-20250316165844963.png)



## 06-MyBatis案例

## 07-查询-查询所有&结果映射

查询所有时会遇到一个问题，当我们实体类里面存在驼峰命名时，可能会出现以下的查询问题

brandName和companyName的查询结果为null

![image-20241224115942952](./pictures/image-20241224115942952.png)

这是因为在数据库字段中没有使用驼峰命名而是brand_name的形式，因为mysql数据库不区分大小写，导致实体类和字段对不上

### 如何解决驼峰命名与字段对不上的问题

有三种解决方法

#### 1.给字段名取别名

```xml
<select id="selectAll" resultType="Brand">
        select id, brand_name brandName, company_name companyName, ordered, description, status from tb_brand;  <!--给字段取别名-->
    </select>
```

#### 2.使用sql片段

```xml
<sql id="Base_Column">
        id, brand_name brandName, company_name companyName, ordered, description, status <!--先定义sql片段-->
    </sql>

    <select id="selectAll" resultType="Brand">
        select 
        <include refid="Base_Column"/>
        from tb_brand;
    </select>
```

#### 3.使用resultMap

resultMap是字段映射，可以把数据库的字段映射为其他别名

##### a.定义resultMap

```xml
<resultMap id="brandResultMap" type="Brand">
        <!--
        id标签用于替换主键字段
        result标签用于替换一般字段
        column是要替换的字段
        property是要替换成对应实体类的属性
        -->
        <result column="brand_name" property="brandName"/>
        <result column="company_name" property="companyName"/>
    </resultMap>
```



##### b.使用resultMap替换resultType

```xml
<select id="selectAll" resultMap="brandResultMap">        <!--将resultType替换成resultMap-->
        select 
        id, brand_name, company_name, ordered, description, status              <!--使用了resultMap后这里写原来的字段就没问题了-->
        from tb_brand;
    </select>
```

```xml
<resultMap id="brandResultMap" type="Brand">
        <!--
        id标签用于替换主键字段
        result标签用于替换一般字段
        column是要替换的字段
        property是要替换成对应实体类的属性
        -->
        <result column="brand_name" property="brandName"/>
        <result column="company_name" property="companyName"/>
    </resultMap>
    <select id="selectAll" resultMap="brandResultMap">        <!--将resultType替换成resultMap-->
        select 
        id, brand_name, company_name, ordered, description, status              <!--使用了resultMap后这里写原来的字段就没问题了-->
        from tb_brand;
    </select>
```

#### 4.开启mybatis驼峰命名自动映射开关

在配置文件中打开这个功能

```properties
#打开mybatis驼峰命名自动映射开关
mybatis.configuration.map-underscore-to-camel-case=true
```





## 08-查询-查看详情

查看详情就是通过id来将某一行的详细信息查询出来

```xml
<select id="selectById" resultMap="brandResultMap">
        select
            id, brand_name, company_name, ordered, description, status
        from tb_brand where id=#{id};
    </select>
```

主要关注的点是如何使用参数占位符

#### 参数占位符

```xml
<!--MyBatis里面有两种参数占位符-->
<!--第一种 #{}-->
<!--第二种 ${}-->
```

使用第一种得到的sql语句的参数是用?替代的

![image-20241224185328764](./pictures/image-20241224185328764.png)

使用第二种得到的sql语句的参数是直接显示出来的

![image-20241224185424768](./pictures/image-20241224185424768.png)

这样一来它两的区别就明了了

```xml
<!--使用 #{} 可以避免sql注入问题-->
#{}
<!--使用 ${} 会有sql注入的风险-->
${}
```

#### 在MyBatis映射文件中不能直接使用`<`符号

由于`<`符号与xml文件中的<>标签符号有冲突，所以如果要使用`<`，就要通过以下两种方法

##### 1.使用转义字符

```xml
HTML的 &lt; &gt; &amp; &quot; &copy; 分别是 < > & " © 的转义字符

<select id="selectById" resultMap="brandResultMap">
        select
            id, brand_name, company_name, ordered, description, status
        from tb_brand where id &lt; ${id};			<!--id<#{id}-->
    </select>
```



##### 2.使用CDATA区

直接在CDATA区里面输入特殊字符即可

```xml
<select id="selectById" resultMap="brandResultMap">
        select
            id, brand_name, company_name, ordered, description, status
        from tb_brand where id
         <![CDATA[						<!--CDATA区-->
         <
         ]]>
         #{id};
    </select>
```

## 09-查询-条件查询

条件查询必然涉及到多个参数，所以如何处理替换多个参数是重点

### 三种处理参数的方法

#### 1.使用Param注解

形象的说是用来处理”散装“数据

在定义Mapper的成员函数时通过Param注解来指定那个参数该去替换哪个参数占位符

```java
//@Param("要替换的占位符") 参数类型 参数名
//接收到的status参数去替换#{status},companyName去替换#{companyName},brandName去替换#{brandName}
Brand selectByCondition(@Param("status") int status,@Param("companyName") String companyName,@Param("brandName") String brandName);
```

#### 2.使用实体类对象

这种方式需要严格定义参数占位符的名字，要让参数占位符的名字与实体类对象里面的属性名字一致

```java
//接收参数
int status=1;
String companyName="华为";
String brandName="华为";
//处理接收的数据
companyName="%"+companyName+"%";
brandName="%"+brandName+"%";
//封装成对象
Brand brand=new Brand();
brand.setStatus(status);
brand.setCompanyName(companyName);
brand.setBrandName(brandName);
//在传递对象前要先封装对象
Brand  brand1=selectByCondition(Brand brand);			//传递一个实体类对象
```

#### 3.使用Map键值对

这种方式要先定义一个Map键值对，在调用函数时直接传入键值对，这样就能知道用哪个数据去替换哪个参数占位符了，需要注意键值对的键要严格定义成与参数占位符的名字一致

```java
//接收参数
int status=1;
String companyName="华为";
String brandName="华为";
//处理接收的数据
companyName="%"+companyName+"%";
brandName="%"+brandName+"%";
//封装成键值对
Map map=new HashMap();
map.put("status",status);
map.put("companyName",companyName);
map.put("brandName",brandName);

Brand brand1=brandMapper.selectByCondition(map);		//传递一个键值对
```



## 10-查询-动态条件查询

### 动态SQL

MyBatis对动态条件查询的支持非常强大，提供了多种方式来实现动态查询

#### 使用if（动态SQL-if和where）

使用if标签来判断当前字段是否要加入查询语句中

if标签里面有test属性，test属性里面写逻辑表达式，用于完成条件判断

如果逻辑表达式结果为true，则拼接if标签内的语句

```xml
<!--动态条件查询-->
    <select id="selectByCondition" resultMap="brandResultMap">
        select * from tb_brand where
            <if test="status!=null">
                status = #{status}
            </if>
            <if test="companyName !=null and companyName!=''">
                and company_name like #{companyName}
            </if>
            <if test="brandName !=null and brandName!=''">
                and brand_name like #{brandName};
            </if>
	</select>
```

但是这种方法有一个问题，比如说这里status为空，这时候status字段就不会写入sql语句中，此时就会出差错，见下图

这个时候sql语句变成了 

```xml
....where and ....  		<!--sql语法错误-->
```

![image-20241224202249656](./pictures/image-20241224202249656.png)

##### 解决错误

要解决这个问题有两种方法

###### 1.在where后面加上恒等式

```xml
    <!--动态条件查询-->
    <select id="selectByCondition" resultMap="brandResultMap">
        select * from tb_brand where 1=1			<!--加上恒等式1=1-->
            <if test="status!=null">
               and status = #{status}
            </if>
            <if test="companyName !=null and companyName!=''">
                and company_name like #{companyName}
            </if>
            <if test="brandName !=null and brandName!=''">
                and brand_name like #{brandName};
            </if>

    </select>
```

###### 2.使用MyBatis提供的`<where>`标签替换where关键字

where标签有两个作用：

a).根据where标签内部的条件语句判断需不需要为sql语句添加where关键字，即：如果所有查询条件都为null，那就不需要where关键字，如果至少存在一个查询条件，那就需要where关键字

b).自动去除不合法的 and 关键字

```xml
    <!--动态条件查询-->
    <select id="selectByCondition" resultMap="brandResultMap">
        select * from tb_brand <where>			<!--将字段判断放在where标签里面-->
        <if test="status!=null">
             status = #{status}
        </if>
        <if test="companyName !=null and companyName!=''">
            and company_name like #{companyName}
        </if>
        <if test="brandName !=null and brandName!=''">
            and brand_name like #{brandName};
        </if>

    </where>
    </select>
```

#### 单条件-动态条件查询

使用`<choose>`和`<when> <otherwise>`标签

```xml
    <!--单条件动态条件查询-->
    <select id="selectByConditionSingle" resultMap="brandResultMap">
        select * from tb_brand
        <where>
            <choose>            <!--相当于switch-->
                <when test="status!=null">
                    status = #{status}
                </when>
                <when test="companyName !=null and companyName!=''">
                    company_name like #{companyName}
                </when>
                <when test="brandName !=null and brandName!=''">
                    brand_name like #{brandName}
                </when>
                <otherwise>                <!--相当于default-->
                    1=1;
                </otherwise>
            </choose>
        </where>
    </select>
```

## 11-添加&修改功能

添加功能需要注意的是事务的提交，在使用openSession()来创建SqlSession对象时是默认关闭自动提交事务的，需要加上true参数来打开自动提交事务功能，否则需要手动提交

#### 事务提交

```java
    @Test
    public  void add() throws Exception {
        //接收参数
        int status=1;
        String companyName="8848";
        String brandName="8848";
        int ordered=100;
        String description="不是所有手机都叫8848";

//        //处理接收的数据
//        companyName="%"+companyName+"%";
//        brandName="%"+brandName+"%";
//        //封装成对象
        Brand brand=new Brand();
        brand.setStatus(status);
        brand.setCompanyName(companyName);
        brand.setBrandName(brandName);
        brand.setOrdered(ordered);
        brand.setDescription(description);

        //封装成键值对
        Map map=new HashMap();
        //map.put("status",status);
        map.put("companyName",companyName);
        // map.put("brandName",brandName);
        //1.加载配置文件
        String resource = "mybatis-config.xml";
        InputStream inputStream = Resources.getResourceAsStream(resource);                   //异常未处理
        SqlSessionFactory sqlSessionFactory = new SqlSessionFactoryBuilder().build(inputStream);
        //2.获取SqlSession对象
        SqlSession sqlSession=sqlSessionFactory.openSession(); //默认开启手动提交事务，使用openSession(true)来开启自动提交事务
        //3.获取代理接口对象
        BrandMapper brandMapper=sqlSession.getMapper(BrandMapper.class);
        //4.执行语句
        brandMapper.add(brand);
        //提交事务
        sqlSession.commit();
        //5.释放资源
        sqlSession.close();
    }
}
```

#### 主键返回

在添加数据后，尝试把id打印出来，发现id为null

![image-20241224222116394](./pictures/image-20241224222116394.png)

这就需要通过主键返回才能正确打印id

主键返回主要是在映射文件的sql语句中添加两个属性`useGeneratedKeys``keyProperty`

```xml
<insert id="add" useGeneratedKeys="true" keyProperty="id">
	insert into tb_brand(brand_name, company_name, ordered, description, status) values (#{brandName},#			{companyName},#{ordered},#{description},#{status});
</insert>
```

这样执行后就能成功打印出刚刚添加数据的主键

![image-20241224222439220](./pictures/image-20241224222439220.png)

#### 修改动态字段（动态SQL-if和set）

和动态查询差不多，都要用到`<if test="">`标签，同时再使用`<set>`标签，`<set>`作用和动态查询时用的`<where>`作用差不多

```xml
    <!--修改动态字段-->
    <update id="update">
        update tb_brand
        <set>
            <if test="brandName !=null and brandName!=''">
                brand_name = #{brandName},
            </if>
            <if test="companyName !=null and companyName!=''">
                company_name = #{companyName},
            </if>
            <if test="ordered !=null">
                ordered = #{ordered},
            </if>
            <if test="description !=null and description!=''">
                description = #{description},
            </if>
            <if test="status !=null">
                status = #{status}
            </if>
        </set>
        where id=#{id};
    </update>
```

## 12-删除功能

#### 批量删除（动态SQL-foreach）

假如我要批量删除几个员工信息，那么删除的原sql语句是

```mysql
delete from emp where id in(13,14,15);
```

实际上，foreach就是用于遍历数组然后将数组拼接成in关键字后面的(13,14,15)这种形式。

foreach标签的属性如下

![image-20250318121901926](./pictures/image-20250318121901926.png)

批量删除根据传过来的id数组来删除数据，由于每次传来的id数组的数据个数不能确定，所以要用到动态sql，这里使用foreach来遍历

```xml
<!--collection属性表示要遍历的集合,item为遍历出来的每一个元素，separator表示分隔符，open表示在开始添加的符号，close表示在结尾添加的符号-->    
<delete id="deleteByIds">
        delete from tb_brand where id in
        <foreach collection="array" item="id" open="(" close=")" separator=",">
            #{id}
        </foreach>
        ;				<!--这个分号不要忘了-->
</delete>
```

array是MyBatis默认的集合名，如果想要指定为其他，就要在Mapper中定义函数时添加@Param注解

```java
int deleteByIds(@Param("ids") int[] ids);
```

后面来复习的时候，发现上面的代码可能是老版本才要这么做，新版本可以直接写集合名，集合名是啥，collection属性就填啥

```java
public int deleteByIds(List<Integer> ids);	//collection属性可以直接填ids
```





#### sql片段（动态SQL-sql和include）

假如在xml映射文件中有多个sql语句需要查询所有字段，如下图所示，可以发现sql语句就会变得非常长，但是我们不能使用select * 来解决这个问题，select * 存在性能问题，企业开发中不推荐使用。那如果想要解决这个问题就要用到sql片段了。

![image-20250318163517264](./pictures/image-20250318163517264.png)

sql片段涉及到两个标签，这两个标签一般同时使用。

1.`<sql>`标签，用来定义可重复的sql片段，可以把上图中的`select 所有字段`这个sql片段定义在sql标签中。该标签有一个id属性用于唯一标识sql片段

2.`<include>`标签，通过指定include标签的refid属性，来指定要使用的sql片段，refid属性的值就是`<sql>`标签的id属性

使用示例如下：

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE mapper
        PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
        "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
<mapper namespace="com.example.mapper.EmpMapper">
    <!--使用sql标签定义sql片段-->
    <sql id="selectAll">
        select id,username,password,name,gender,image,job,entrydate,dept_id,create_time,update_time from emp
    </sql>
    <select id="select3" resultType="com.example.pojo.Emp">
        <!--引入sql片段，include标签可以自闭合-->
        <include refid="selectAll"/>
        <where>
            <if test="name!=null">
                name
                like concat('%',
                #{name},
                '%'
                )
            </if>
            <if test="gender!=null">
                and gender =
                #{gender}
            </if>
            <if test="begin!=null and end!=null">
                and entrydate between
                #{begin}
                and
                #{end};
            </if>
        </where>
    </select>
</mapper>
```





## 13-参数传递

了解MyBatis底层是如何封装传递过来的数据的

#### 多个参数

```java
/*
    * MyBatis在接收多个参数时会将每个参数封装为两个键值对
    * 比如这里,如果没有使用注解,就会有以下键值对
    * arg0->status
    * param1->status
    * arg1->companyName
    * param2->companyName
    * arg2->brandName
    * param3->brandName
    *
    *arg是从0开始
    *param是从1开始
    * */
 Brand selectByCondition(int status,String companyName,tring brandName);
```

此时如果还是按自己定义的方式去查询

![image-20241224232518794](./pictures/image-20241224232518794.png)

就会出现以下错误，通过看报错信息可以知道，能够使用的只有arg0，arg1，arg2，param1......

![image-20241224232418842](./pictures/image-20241224232418842.png)

所以我们换种方式，把自己定义的参数占位符改成MyBatis默认的,arg和param是等效的

![image-20241224233458055](./pictures/image-20241224233458055.png)

这时候就成功查询

![image-20241224233522007](./pictures/image-20241224233522007.png)

我们再尝试使用一个注解的情况

```java
List<Brand> selectByCondition(@Param("status")int status,String companyName,String brandName);
//此时键值对arg0会被替换成status
/*
*	status->status
*	param0->status
*	arg1->companyName
*	param1.....后面的一样，没有被替换
*/
```

这时我们再看，键值对arg0已经被替换成status了，如果第二个参数继续使用注解，那么arg2也会被替换，但param不受影响

![image-20241224233816542](./pictures/image-20241224233816542.png)

## 14-注解开发

注解开发适合完成简单功能

```java
    /*
    * 注解开发有以下三种
    * 1.@Select
    * 2.@Update
    * 3.@Delete
    * 4.@Insert
    * */
	//如下是简单的示例
    @Select("select * from tb_brand where id = #{id}")
    Brand selectById(int id);
```

如果sql语句很复杂还是用定义映射文件方式更好









# Web入门 HTTP&Tomcat&Servlet

## Day04-10.Web入门-springBootWeb-快速入门

### springBootWeb快速入门

#### 1.创建一个springboot模块

![image-20250311104656499](./pictures/image-20250311104656499.png)

#### 2.勾选web相关依赖

选择springboot版本，并勾选web相关依赖

![image-20250311104721000](./pictures/image-20250311104721000.png)

创建好工程后，项目的工程目录如下

![image-20250311110025198](./pictures/image-20250311110025198.png)

其中以Application结尾的文件是springboot项目的启动类，用于启动springboot工程



#### 3.定义Controller类

```java
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

//定义Controller类，用于处理浏览器的请求
//使用RestController注解来标记Controller类
@RestController
public class HelloController {
    //使用RequestMapping注解，并指定要处理的路径
    //当请求路径为/hello时，使用该方法来处理请求
    @RequestMapping("/hello")
    public String hello(){
        System.out.println("Hello World");
        return "Hello World";
    }

}
```

#### 4.启动springWeb项目

直接通过启动类，该项目中是`SpringbootWebQuickstartApplication`这个类，来启动项目

![image-20250311110710212](./pictures/image-20250311110710212.png)

启动成功后控制台的输出如下

![image-20250311110742193](./pictures/image-20250311110742193.png)

在浏览器中输入访问路径`localhost:8080/hello`

访问结果如下

![image-20250311110915145](./pictures/image-20250311110915145.png)

包括控制台输出

![image-20250311110934985](./pictures/image-20250311110934985.png)

以上结果说明项目创建并启动成功



### springboot项目的起步依赖

起步依赖是在创建springboot项目时会自动导入的依赖，其名字一般带有starter。起步依赖包含了项目开发的必要依赖，通过依赖传递作用到我们的项目中。

我们在创建springboot项目时会选择项目的相关功能，springboot就会根据这些来导入相关依赖，比如构建web项目时，我们选择了spring web，那么该项目就会自动导入`spring-boot-starter-web`依赖，该依赖就内嵌了tomcat服务器，是我们开发web需要用到的工具。

起步依赖不用写版本号，因为在父工程中会定义所有起步依赖的版本，其会根据当前使用的springboot版本来决定起步依赖的版本，从而避免了版本冲突

下面是一个springboot项目的pom.xml文件

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>
    <!--该项目的父工程-->
    <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>3.4.3</version>
        <relativePath/> <!-- lookup parent from repository -->
    </parent>

    <!--当前项目的坐标-->
    <groupId>com.example</groupId>
    <artifactId>springboot-web-quickstart</artifactId>
    <version>0.0.1-SNAPSHOT</version>
    <name>springboot-web-quickstart</name>
    <description>springboot-web-quickstart</description>
    <url/>
    <licenses>
        <license/>
    </licenses>
    <developers>
        <developer/>
    </developers>
    <scm>
        <connection/>
        <developerConnection/>
        <tag/>
        <url/>
    </scm>
    <properties>
        <java.version>17</java.version>
    </properties>
    <dependencies>
        <!--起步依赖，起步依赖的名字中都带有starter-->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>

        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-test</artifactId>
            <scope>test</scope>
        </dependency>
    </dependencies>

    <build>
        <plugins>
            <plugin>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>
            </plugin>
        </plugins>
    </build>

</project>
```





## Day04-11.Web入门-HTTP协议-概述

### 什么是HTTP协议

HTTP是Hyper Text Transfer Protocol的缩写，即：超文本传输协议。HTTP协议规定了浏览器与服务器的数据传输规则。



### HTTP协议的特点

HTTP协议主要有下面3个特点

#### 1.基于TCP协议

HTTP协议是基于TCP协议的，因此HTTP协议是面向连接，安全的可靠传输协议

#### 2.基于请求-响应模型

HTTP协议基于请求-响应模型，即：一次请求对应一次响应。

#### 3.无状态协议

HTTP协议是一种无状态协议，即：对事务处理没有记忆能力，每一次的请求与响应都是独立，没有联系的。

基于这点原因，HTTP协议就有一个速度快的有点，但是也有多次请求之间不能共享数据这一缺点。



## 03-HTTP-请求数据格式

下面是HTTP的一个请求，可以发现HTTP的请求实际上就是一个字符串

```http
GET /hello HTTP/1.1
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Accept-Encoding: gzip, deflate, br, zstd
Accept-Language: zh-CN,zh;q=0.9,en;q=0.8,en-GB;q=0.7,en-US;q=0.6
Cache-Control: max-age=0
Connection: keep-alive
Cookie: Idea-e250bc6e=23e75080-6801-4801-bf7d-eea3a329b834
Host: localhost:8080
Sec-Fetch-Dest: document
Sec-Fetch-Mode: navigate
Sec-Fetch-Site: none
Sec-Fetch-User: ?1
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/134.0.0.0 Safari/537.36 Edg/134.0.0.0
sec-ch-ua: "Chromium";v="134", "Not:A-Brand";v="24", "Microsoft Edge";v="134"
sec-ch-ua-mobile: ?0
sec-ch-ua-platform: "Windows"
```



### HTTP数据分为三部分

#### 1.请求行

请求数据的第一行是请求行

示例

```http
GET /hello HTTP/1.1

/hello 表示请求路径
GET表示请求方法 
HTTP/1.1表示协议版本
```

#### 2.请求头

请求数据的第二行开始是请求头，格式为key:value格式

示例

```http
Host: www.bilibili.com
Connection: keep-alive
```

需要知道下面几个常见的请求头的含义

```http
Host: 表示请求的主机名
User-Agent: 表示浏览器版本，可以用来做浏览器适配
Accept: 表示浏览器能够接受的资源类型 如 text/*,image/*,*/*表示所有类型
Accept-Language: 表示浏览器偏好语言，服务器可以根据不同的偏好语言提供不同的页面
Accept-Encoding: 表示浏览器支持的压缩类型
Content-Type: 表示请求主体的数据类型
Content-Length: 表示请求主体的大小（单位：字节）
```



#### 3.请求体

只有当请求方式为POST的时候才会有请求体，请求体用于存放POST请求的参数

#### GET与POST请求的区别

GET请求的参数放在请求数据的第一行，且有参数大小限制

POST请求的参数放在请求体里面，即请求数据的最后，并且参数大小没有限制

## 04-HTTP-响应数据格式

### HTTP响应数据分为三部分

#### 1.响应行

响应数据的第一行

```http
HTTP/1.1 200 OK
```

HTTP/1.1代表协议及版本，200代表服务器返回的状态码，ok是对返回结果状态码的具体描述

#### 2.响应头

第二行开始

响应头的数据格式是  键:值  `key`:`value`  形式的

```http
Server: Tengin
Content-Type: text/html
Transfer-Encoding: chunked....
```

常见的响应头含义

Content-Type:表示响应的数据类型 如：text/html，image/jpeg

Content-Length:表示响应内容的长度

Content-Encoding:表示该响应压缩算法，如gzip

Cache-Control:表示客户端该如何缓存，如：max-age=300 表示最多缓存300秒

Set-Cookie:告诉浏览器为当前页面所在域设置cookie

#### 3.响应体

最后一部分，存放响应数据，响应正文 

### 常见的响应状态码

#### 一、状态码大类



| 状态码分类 | 说明                                                         |
| ---------- | ------------------------------------------------------------ |
| 1xx        | **响应中**——临时状态码，表示请求已经接受，告诉客户端应该继续请求或者如果它已经完成则忽略它 |
| 2xx        | **成功**——表示请求已经被成功接收，处理已完成                 |
| 3xx        | **重定向**——重定向到其它地方：它让客户端再发起一个请求以完成整个处理。 |
| 4xx        | **客户端错误**——处理发生错误，责任在客户端，如：客户端的请求一个不存在的资源，客户端未被授权，禁止访问等 |
| 5xx        | **服务器端错误**——处理发生错误，责任在服务端，如：服务端抛出异常，路由出错，HTTP版本不支持等 |

状态码大全：https://cloud.tencent.com/developer/chapter/13553 



#### 二、常见的响应状态码

| 状态码 | 英文描述                               | 解释                                                         |
| ------ | -------------------------------------- | ------------------------------------------------------------ |
| 200    | **`OK`**                               | 客户端请求成功，即**处理成功**，这是我们最想看到的状态码     |
| 302    | **`Found`**                            | 指示所请求的资源已移动到由`Location`响应头给定的 URL，浏览器会自动重新访问到这个页面 |
| 304    | **`Not Modified`**                     | 告诉客户端，你请求的资源至上次取得后，服务端并未更改，你直接用你本地缓存吧。隐式重定向 |
| 400    | **`Bad Request`**                      | 客户端请求有**语法错误**，不能被服务器所理解                 |
| 403    | **`Forbidden`**                        | 服务器收到请求，但是**拒绝提供服务**，比如：没有权限访问相关资源 |
| 404    | **`Not Found`**                        | **请求资源不存在**，一般是URL输入有误，或者网站资源被删除了  |
| 428    | **`Precondition Required`**            | **服务器要求有条件的请求**，告诉客户端要想访问该资源，必须携带特定的请求头 |
| 429    | **`Too Many Requests`**                | **太多请求**，可以限制客户端请求某个资源的数量，配合 Retry-After(多长时间后可以请求)响应头一起使用 |
| 431    | **` Request Header Fields Too Large`** | **请求头太大**，服务器不愿意处理请求，因为它的头部字段太大。请求可以在减少请求头域的大小后重新提交。 |
| 405    | **`Method Not Allowed`**               | 请求方式有误，比如应该用GET请求方式的资源，用了POST          |
| 500    | **`Internal Server Error`**            | **服务器发生不可预期的错误**。服务器出异常了，赶紧看日志去吧 |
| 503    | **`Service Unavailable`**              | **服务器尚未准备好处理请求**，服务器刚刚启动，还未初始化好   |
| 511    | **`Network Authentication Required`**  | **客户端需要进行身份验证才能获得网络访问权限**               |





## Day04-14.Web入门-HTTP协议-协议解析

### HTTP协议解析

HTTP的协议解析实际上就是对浏览器发送过来的字符串进行解析，很多Web服务器软件提供了解析HTTP协议的功能，因此可以直接使用Web服务器软件来解析HTTP协议，如：Tomcat



## 05-Tomcat-简介&基本使用

在做web开发的时候，后端接收到了浏览器发送的请求后要如何处理呢，这当然要写很多代码来负责处理浏览器的发送信息，是一项很繁琐的动作。但是正好这项动作具有很多通用性，也就是说一个人写好了处理请求的代码，另一个人说不定也能直接使用，于是Tomcat应运而生，Tomcat就是别人写好的用于处理浏览器请求的代码，这样我们就能专心在处理业务逻辑上了。

Tomcat也被称为Web容器、Servlet容器。Servlet程序的运行需要依赖Tomcat。

### Tomcat软件的使用

Tomcat是绿色版软件，直接下载解压包解压即用

下面简单介绍一下Tomcat安装后的文件目录

![image-20250311163509963](./pictures/image-20250311163509963.png)



bin是tomcat的可执行文件

conf是tomcat的配置文件

lib是tomcat依赖的jar包

logs是tomcat的日志文件

temp是tomcat的临时文件

webapps是应用发布目录，要部署的应用就放在这个文件夹下

work是tomcat的工作目录



#### Tomcat的启动

找到bin(bin是binary即二进制的缩写，即存放二进制可执行文件的地方，里面的文件都是可以直接执行的)文件夹下的启动脚本

windows系统找startup.bat

linux系统找startup.sh

##### 启动后发现有乱码

![image-20241227160608830](./pictures/image-20241227160608830.png)

原因是windows控制台是GBK编码，而Tomcat输出的是UTF-8编码

解决方法

进入conf文件夹，找到logging.properties文件

![image-20241227160812022](./pictures/image-20241227160812022.png)

打开后进行如下图的修改

![image-20241227160929879](./pictures/image-20241227160929879.png)

再次启动就正常了

![image-20241227160953939](./pictures/image-20241227160953939.png)

此时我们用浏览器访问`localhost:8080`就能看到对应的页面

![image-20241227161055467](./pictures/image-20241227161055467.png)

### 部署自己的项目

只需将自己的项目资源放在webapps目录下，然后输入正确链接访问即可



## 06-Tomcat配置和部署项目

### Tomcat配置

如果想对Tomcat进行一些配置，如配置端口号，可以进到conf目录下，找到server.xml文件，使用文本编辑器或vscode等工具打开

找到如下代码修改即可

![image-20241227162038979](./pictures/image-20241227162038979.png)

### 可能遇到的启动异常

如果在启动Tomcat时出现控制台闪了一下就消失或者没有出现控制台的情况，可能时jdk环境没有配置好，修改一下系统变量的jdk环境即可

### Tomcat项目部署

对于javaWeb项目的部署，直接将项目打包成一个war包，然后将war包放入webapps文件夹下即可





## 09-Tomcat-Idea集成本地Tomcat

### 集成步骤

#### 编辑一个运行Configuration

![image-20241227165751937](./pictures/image-20241227165751937.png)

#### 找到Tomcat本地选项

![image-20241227165822346](./pictures/image-20241227165822346.png)

#### 选择本地Tomcat安装目录

![image-20241227165916762](./pictures/image-20241227165916762.png)

#### 选择要部署的项目

![image-20241227170018204](./pictures/image-20241227170018204.png)

![image-20241227170038930](./pictures/image-20241227170038930.png)

![image-20241227170053376](./pictures/image-20241227170053376.png)

### 相关配置

#### 配置端口

![image-20241227170208496](./pictures/image-20241227170208496.png)

## 10-Tomcat-Tomcat的Maven插件

### 使用Tomcat插件

可以使用快捷键 `alt`+`insert`来快速导入插件

![image-20241227170821778](./pictures/image-20241227170821778.png)

```xml
      <plugin>
        <groupId>org.apache.tomcat.maven</groupId>
        <artifactId>tomcat7-maven-plugin</artifactId>
        <version>2.2</version>
      </plugin>
```

还可以使用configuration标签来进行相关配置

```xml
      <plugin>
        <groupId>org.apache.tomcat.maven</groupId>
        <artifactId>tomcat7-maven-plugin</artifactId>
        <version>2.2</version>
        <configuration>
          <port>8081</port>				<!--配置默认端口号-->
          <path>/</path>				<!--配置默认启动路径-->
        </configuration>
      </plugin>
```

然后再maven里面通过插件启动

![image-20241227171625800](./pictures/image-20241227171625800.png)



### springboot框架下配置tomcat端口

在application.properties配置文件中配置tomcat端口号

输入`server.port=端口号`

![image-20250319082411366](./pictures/image-20250319082411366.png)





## Day05-01.请求响应-概述

### Tomcat的工作原理

Tomcat是一个Servlet容器，它只能识别实现Servlet接口的类。所以我们在springboot框架下编写的Controller类，Tomcat是识别不了的，那咱用springboot写的web到的是怎么运行起来的呢？实际上springboot还提供了一个类：`DispatcherServlet`，这个类就实现了Servlet接口，能够被Tomcat识别。而当服务器收到请求时，就先由DispatcherServlet来进行处理，DispatcherServlet再将请求转给Controller类处理，Controller类处理完后再将结果交给DispatcherSerlvet，DispatcherServlet最后将结果返回给浏览器。

DispatcherServlet也被称为核心控制器或者前端控制器

Tomcat服务器在收到HTTP请求时会解析请求，并将请求信息封装成一个`HttpServletRequest`请求对象。

后端处理完请求后会将处理结果封装成一个`HttpServletResponse`响应对象





## 11-Servlet简介&快速入门

### Servlet快速入门

#### 1.导入Servlet依赖

注意这里要配置该依赖的作用范围，因为Tomcat里面也有这个包，如果配置作用范围就会和Tomcat里面的这个包发生冲突，产生报错

```xml
    <dependency>
      <groupId>javax.servlet</groupId>
      <artifactId>javax.servlet-api</artifactId>
      <version>3.1.0</version>
      <scope>provided</scope>     <!--运行和编译时生效，打包不生效-->
    </dependency>
```

如果不配置依赖范围的话在访问时就会产生如下错误

![image-20241227174431109](./pictures/image-20241227174431109.png)

![image-20241227174401501](./pictures/image-20241227174401501.png)

#### 2.创建一个实现Servlet接口的类

```java
import javax.servlet.*;
import java.io.IOException;

public class servlet implements Servlet {


    //访问时运行service函数
    @Override
    public void service(ServletRequest servletRequest, ServletResponse servletResponse) throws ServletException, IOException {
        System.out.println("servlet hello world~~");
    }

    @Override
    public String getServletInfo() {
        return null;
    }

    @Override
    public void destroy() {

    }
    @Override
    public void init(ServletConfig servletConfig) throws ServletException {

    }

    @Override
    public ServletConfig getServletConfig() {
        return null;
    }
}
```



#### 3.使用注解配置访问路径

使用`@WebServlet`注解来配置访问路径

![image-20241227173907612](./pictures/image-20241227173907612.png)

#### 4.启动Tomcat

启动Tomcat，访问对对应路径后可以看到控制台的输出

![image-20241227174050984](./pictures/image-20241227174050984.png)





## 12-Servlet执行流程&生命周期

### Servlet执行流程

Servlet类由Tomcat创建，并且Servlet中的service函数也是由Tomcat服务器调用的

### Servlet生命周期

Servlet运行在Servlet容器中(web服务器)，其生命周期由容器来管理，主要有以下四个阶段

#### 1.加载和实例化

这个阶段会创建Servlet实例，可以设置实例的创建时期，默认在访问这个Servlet的时候才会创建。

可以在`@WebServlet`注解中添加loadOnstartup属性，该属性表示优先级，服务器在启动时就会根据优先级提前创建Servlet实例

```java
@WebServlet(value = "/demo1",loadOnStartup = 1)			
```

如下图所示，当我设置了`loadOnStartup`属性后，Servlet类就会在服务器启动时创建实例

![image-20241227213333311](./pictures/image-20241227213333311.png)

#### 2.初始化

这个阶段用于加载Servlet类所需的资源，需要自己定义，这个函数只会执行一次

```java
    //Servlet类一旦创建就会执行init函数
    @Override
    public void init(ServletConfig servletConfig) throws ServletException {
        System.out.println("Servlet实例创建成功");
    }
```

如下图，当我第一访问demo1的时候Servlet实例创建，并且调用了init函数，随后我刷新网页多次访问demo1，后面调用的都是service函数，init函数并没有被调用

![image-20241227213035268](./pictures/image-20241227213035268.png)

#### 3.调用service

当每次访问Servlet的时候都会调用service函数，service函数可以被多次调用

#### 4.服务终止

当服务器关闭或者服务停止时会调用destroy函数，该函数用于销毁init函数申请的资源

```java
    //当服务停止时调用destroy函数
    @Override
    public void destroy() {
        System.out.println("调用destroy函数，释放资源");
    }
```

如下图所示，我通过控制台启动Tomcat服务，并通过控制台终止服务，可以看到服务器调用了destroy函数，但这里是乱码，因为编码问题，不过确实看到destroy函数运行了

![image-20241227213849862](./pictures/image-20241227213849862.png)



## 13-Servlet方法介绍&体系结构

### 如何使用HttpServlet

HttpServlet是继承GenericServlet类的一个对HTTP协议封装的Servlet类，而GenericServlet类实现了Servlet接口

#### 1.创建一个自己的Servlet类并且继承HttpServlet

```java
@WebServlet("/demo2")
public class servlet2 extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        System.out.println("Get....");
    }

    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        System.out.println("Post...");
    }
}
```



#### 2.覆写HttpServlet里面的相关方法

```java
    //覆写get方法
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        System.out.println("Get....");
    }

    
    //覆写post方法
    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        System.out.println("Post...");
    }
```



之所有要使用HttpServlet，是因为不同的请求方式，服务器发出的请求信息是不同的，如get请求的请求参数在请求头中，而post的请求参数或数据在请求体中。因此如果每次接收这些请求时都要写代码去处理识别这些请求是什么方法就很麻烦，于是HttpServlet就帮我们封装好了，我们只需要提供每一种请求方法的具体执行函数就行，所以我们使用HttpServlet时需要覆写这些实现函数



## 14-urlPattern配置

### 一个Servlet服务可以配置多个路径可以

使用`urlPatterns`或`value`属性

```java
@WebServlet(urlPatterns = {"/demo2","/demo3"})
```

### 路径的几种匹配方式

#### 1.精确匹配

前面的所有路径配置用的都是精确匹配

#### 2.目录匹配

```java
@WebServlet(value = "/demo3/*")
```

后面*的地方不管写什么都能访问到demo3的路径

![image-20241227222107198](./pictures/image-20241227222107198.png)

访问成功

![image-20241227222417529](./pictures/image-20241227222417529.png)

#### 3.扩展名匹配

注意扩展名匹配的路径前面不能有`/`不然会报错

```java
@WebServlet(value = "*.do")
@WebServlet(value = "/demo4/*.do")			//错误写法

```

错误写法报错

![image-20241227222341114](./pictures/image-20241227222341114.png)

正确写法访问成功

访问路径示例:

```http
http://localhost:8081/sfjkaslf.do
```

![image-20241227222637870](./pictures/image-20241227222637870.png)

#### 4.任意匹配

```java
@WebServlet(value = "/")
@WebServlet(value = "/*")			//这种也可以
```

任意匹配下，不管输入什么都会访问到任意匹配的Servlet

访问路径示例:

```http
http://localhost:8081/sfjkafdasfa
```

##### 注意事项

Tomcat自己自带一个默认的任意匹配，如果再定义任意匹配就会覆盖掉Tomcat的任意匹配，而覆盖掉这个的后果就是无法访问静态资源，所以一般不使用任意匹配





## 15-XML配置Servlet

前面配置Servlet的访问路径使用的都是注解配置，但是在还不支持注解配置的时候用的是XML配置，要在web.xml文件里面配置

使用`<servlet>`和`servlet-mapping`标签来配置

```xml
<web-app>
  <display-name>Archetype Created Web Application</display-name>

  <servlet>
    <servlet-name>xmlServlet</servlet-name>                   <!--这里配置名字-->
    <servlet-class>com.example.servlet6</servlet-class>       <!--这里配置对应Servlet服务的全限定名-->
  </servlet>


  <servlet-mapping>
    <servlet-name>xmlServlet</servlet-name>               <!--这里配置的名字要与前面配置servlet标签起的名字的一致-->
    <url-pattern>/demo6</url-pattern>                     <!--这里配置路径-->
  </servlet-mapping>
</web-app>
```



# Request&Response

## 01-Request和Request介绍&Request继承体系

#### Request继承体系如下

java提供了Request的接口，然后由服务器程序（如：Tomcat）去创建实现类

java提供了Request根接口，ServletRequest

同时提供了继承自ServletRequest的对Http协议封装的请求对象接口HttpServletRequest

Tomcat提供了实现类RequestFacade

![image-20241229102529555](./pictures/image-20241229102529555.png)





## 02-Request获取请求数据-请求行&请求头&请求体

#### 1.请求行

```java
@WebServlet("/req1")
public class req1 extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        //Tomcat的实现的请求对象
        System.out.println("请求对象"+req);
        //Tomcat实现的响应对象
        System.out.println("响应对象"+resp);

        //获取请求方式
        String method=req.getMethod();
        System.out.println(method);

        //获取虚拟目录
        String contextPath=req.getContextPath();
        System.out.println(contextPath);

        //获取URL,返回的是stringBuffer
        StringBuffer url = req.getRequestURL();
        System.out.println(url.toString());

        //获取URI（统一资源标识符）
        String uri = req.getRequestURI();
        System.out.println(uri);

        //获取请求参数
        String query = req.getQueryString();
        System.out.println(query);
    }
}
```

输入请求路径

```http
http://localhost:8081/req-demo/req1?username=zhangsan
```

得到结果如下

![image-20241229111306736](./pictures/image-20241229111306736.png)



#### 2.请求头

请求头的获取通过`getHeader`函数来获取，输入对应键值，就能获取对应的信息

```java
        //获取请求头
        //获取浏览器信息
        String UserAgent = req.getHeader("User-Agent");
        System.out.println(UserAgent);
```

![image-20241229112253348](./pictures/image-20241229112253348.png)



#### 3.请求体

请求体的获取要先获取对应的输入流

如果获取的是文本就用字符输入流，`BufferedReader`

如果获取的是文件（如图片），就用字节输入流,`ServletInputStream`

注意要写在dopost函数里面

```java
    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        //获取请求体
        //如果要获取文本信息就使用字符输入流BufferedReader
        BufferedReader bufferedReader = req.getReader();
        String line = bufferedReader.readLine();
        System.out.println(line);
//        //如果要获取文件，就是用字节输入流
//        ServletInputStream inputStream = req.getInputStream();
    }
```

在表单中输入数据

![image-20241229113611732](./pictures/image-20241229113611732.png)

提交后的结果如下：

![image-20241229113640908](./pictures/image-20241229113640908.png)



## 03-Request通用方式获取请求参数

在前面学的请求方式中，对于不同的请求方式get和post，所用的获取方法也不同，而这样就会使得代码重复量变多，为了解决这个问题，我们可以使用一个通用的方式来获取请求参数，这些通用的方法底层用的其实也是前面学的方法，只不过相当于把它们整合起来。

### 通用请求方式有以下三种

#### 1.`getParameterMap()`

getParameterMap方式，得到的是所有参数的键值对集合

```java
        //1.getParameterMap方式，得到的是所有参数的键值对集合
        Map<String, String[]> parameterMap = req.getParameterMap();
        System.out.println("第一种方法");
        for(String key : parameterMap.keySet()){
            System.out.print(key+":");
            for(String value : parameterMap.get(key)){
                System.out.print(value+" ");
            }
            System.out.println();
        }
```

#### 2.`getParameterValues()`

getParameterValues方式，得到的是对应键值的参数数组

```java
        //2.getParameterValues方式，得到的是对应键值的参数数组
        System.out.println("第二种方法");
        String[] hobbies = req.getParameterValues("hobby");
        System.out.print("hobby");
        for(String value : hobbies){
            System.out.print(value+" ");
        }
```



#### 3.`getParameter`

getParameter方式，得到的是对应键值的值，该键对应的值只能有一个

```java
        //3.getParameter方式，得到的是对应键值的值，该键对应的值只能有一个
        System.out.println("第三种方法");
        String username = req.getParameter("username");
        String password = req.getParameter("password");
        System.out.println("username:"+username);
        System.out.println("password:"+password);
```

使用以上通用方式后，我们可以只在一个方法里面写获取参数的代码，然后其他方法直接调用这个方法即可，例如，在doGet里面写获取参数的方法，在doPost里面直接调用doGet方法

```java
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        //在doGet方法里面写获取参数的代码
        //1.getParameterMap方式，得到的是所有参数的键值对集合
        Map<String, String[]> parameterMap = req.getParameterMap();
        System.out.println("第一种方法");
        for(String key : parameterMap.keySet()){
            System.out.print(key+":");
            for(String value : parameterMap.get(key)){
                System.out.print(value+" ");
            }
            System.out.println();
        }

        //2.getParameterValues方式，得到的是对应键值的参数数组
        System.out.println("第二种方法");
        String[] hobbies = req.getParameterValues("hobby");
        System.out.print("hobby");
        for(String value : hobbies){
            System.out.print(value+" ");
        }
        System.out.println();

        //3.getParameter方式，得到的是对应键值的值，该键对应的值只能有一个
        System.out.println("第三种方法");
        String username = req.getParameter("username");
        String password = req.getParameter("password");
        System.out.println("username:"+username);
        System.out.println("password:"+password);

    }

    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        //调用doGet方法获取参数
        this.doGet(req,resp);
    }
```





提交如下表单

![image-20241229151650614](./pictures/image-20241229151650614.png)

结果如下

![image-20241229151712546](./pictures/image-20241229151712546.png)





## 05-请求参数中文乱码-POST解决方案

对于中文参数

![image-20241229154205237](./pictures/image-20241229154205237.png)

会产出以下乱码结果

![image-20241229154228619](./pictures/image-20241229154228619.png)



### 解决方法

使用`setCharacterEncoding`函数设置字符输入流的编码，这样就正常了

![image-20241229154438763](./pictures/image-20241229154438763.png)

 

## 06-Request请求参数中文乱码-GET解决方案

GET方法参数的获取方式是通过`getQueryString`函数来获取的，而这个函数的编码方式是在Tomcat中写死的，所以不能像解决POST方法那样去修改编码方式。

浏览器处理中文时是将中文转换为URL编码，采用的字符集是`ISO-8859-1`，所以Tomcat在处理请求参数时就是以`ISO-8859-1`的编码方式来处理的

### 解决方法

#### 1.将Tomcat用`ISO-8859-1`编码方式得到的乱码结果转化为字节数组

```java
        //1.先将乱码结果转化未字节数组
        byte[] bytes = username.getBytes("ISO_8859_1");
```



#### 2.再将字节数组用`UTF-8`的方式进行编码

```java
        //2.再将字节数组使用UTF-8的编码方式进行编码
        username = new String(bytes,"UTF-8");
        System.out.println("未解决乱码后 username:"+username);
```



#### 综合为一行代码

上面两个步骤可以合并为一行代码

```java
        //合并为一行代码
        username = new String(username.getBytes("ISO_8859_1"),"UTF-8");
```

结果如下

![image-20241229164931962](./pictures/image-20241229164931962.png)





## 07-Request请求转发

请求转发(forward)就是浏览器请求的时资源A，然后资源A在处理的时候可能需要另一个资源B的处理，于是对资源B发出请求，并将数据一起传过去

#### 实现方式

使用`getRequestDispatcher`和`forward`函数

```java
req.getRequestDispatcher("/reqB").forward(req,resp);
```

如图所示，请求的是A资源

![image-20241229171114016](./pictures/image-20241229171114016.png)

结果如下

![image-20241229171133520](./pictures/image-20241229171133520.png)



#### 参数的传递

参数的传递要用到`setAttribute`和`getAttribute`

##### 1.资源A设置要传递的参数

```java
        System.out.println("资源A的处理");
        String username = "被资源A处理的部分";
        //setAttribute用于设置要传递的参数，设置为键值对
        req.setAttribute("username",username);
        req.getRequestDispatcher("/reqB").forward(req,resp);
```



##### 2.资源B从资源A传递过来的参数里面取出要处理的参数

```java
        System.out.println("资源B的处理");
        //获取资源A传递的参数
        Object username = req.getAttribute("username");
        //对传递的参数进行处理
        username = username +"+资源B对参数的处理";
        System.out.println(username);
```



结果如下

![image-20241229171835147](./pictures/image-20241229171835147.png)

## 08-Response设置响应数据功能介绍&完成重定向

### 如何设置响应数据

#### 1.设置响应行

设置响应行可以使用函数`setStatus`设置状态码

```java
resp.setStatus(200);
```



#### 2.设置响应头

设置响应头使用函数`setHeader`，设置键值对

```java
resp.setHeader("Content-Encoding","gzip");
```



#### 3.设置响应体

设置响应体要使用输出流

获取字符输出流使用函数`getWriter`

获取字节输出流使用函数`getOutputStream`

```java
        //获取字符输出流
        PrintWriter writer = resp.getWriter();
        //获取字节输出流
        ServletOutputStream outputStream = resp.getOutputStream();
```



### 重定向

重定向也是一种资源跳转方式，与前面学的请求转发不同，请求转发只有一次请求与响应，而重定向是浏览器先请求资源A，然后资源A返回一个响应，这个响应是为了告诉浏览器要重新请求哪个资源，所以浏览器又会向服务器发出一个请求用于请求另一个资源B，资源B对请求做出处理后又会返回一个响应

#### 重定向的步骤

##### 1.设置状态码为302

重定向的状态码固定为302

```java
//设置状态码
resp.setStatus(302);
```



##### 2.设置响应头

响应头要固定设置为location:具体重定向的路径这样的键值对形式

```java
//设置响应头
resp.setHeader("location","/req-demo/response2");
```



##### 以上步骤可以简写

HttpServletResponse提供了一个重定向函数`sendRedirect`

```java
//简写以上步骤
resp.sendRedirect("/req-demo/response2");
```



如图所示，输入的路径原本为

```http
http://localhost:8081/req-demo/response1
```

自动重定向到了response2

```http
http://localhost:8081/req-demo/response2
```

![image-20241229174753347](./pictures/image-20241229174753347.png)

### 重定向的特点

重定向可以重定向到任意位置，包括其他服务器的资源

```java
resp.sendRedirect("https://www.bilibili.com/");
```

而请求转发只能转发都本地服务器的资源，不能转发到其他服务器





## 09-资源路径问题

### 如何判断设置路径是否要带上虚拟路径

先说结论：如果这个路径是给浏览器的，就要带上虚拟路径；如果这个路径是给服务器的，就可以不带上虚拟路径

在请求转发或者重定向时，转到的路径设定会有所不同。

请求转发的路径是给服务器使用的，所以可以不带虚拟路径，如下
```java
req.getRequestDispatcher("/reqB").forward(req,resp);
```

而重定向的路径是给浏览器使用的，应该带上虚拟路径，如下

```java
resp.sendRedirect("/req-demo/response2");
```

否则在重定向时会发生以下情况，找不到页面

![image-20250102225845363](./pictures/image-20250102225845363.png)



### 如何动态获取当前的虚拟路径

使用`getContentPath`函数

```java
String contextPath = req.getContextPath();
```

### 如何获取当前项目的工作路径

使用`getProperty`函数

```java
String contextPath = System.getProperty("user.dir");
System.out.println(contextPath);
```

![image-20250113225926621](./pictures/image-20250113225926621.png)



## 10-Response响应字符&字节数据

### 响应字符

使用`PrintWriter`字符输出类来输出响应字符

#### 输出普通字符串

```java
//首先获取字符输出流
PrintWriter printWriter = resp.getWriter();
//使用字符输出流输出字符
printWriter.write("aaa");
```



#### 输出html类型

```java
//可以输出html信息，不过要先设置响应类型才能正确解析html
resp.setHeader("Content-Type","text/html");
printWriter.write("<h1>aaa</h1>");
```

如下图所示，标签会被浏览器解析为输出为html

![image-20250113224221697](./pictures/image-20250113224221697.png)

#### 输出中文类型

如果不进行处理，输出中文字符时会出现乱码，因为Response获取的字符输出流的默认编码为ISO-8859-1

```java
//首先获取字符输出流
PrintWriter printWriter = resp.getWriter();
//使用字符输出流输出字符
printWriter.write("你好");
```

如图所示，中文输出为乱码

![image-20250113224346685](./pictures/image-20250113224346685.png)

##### 解决中文乱码问题

需要在获取字符输出流前设置响应头，设置响应类型和字符编码

```java
        //在获取字符输出流之前设置响应类型和字符编码
        resp.setContentType("text/html;charset=utf-8");
		//获取字符输出流
        PrintWriter printWriter = resp.getWriter();
        //使用字符输出流输出字符
        printWriter.write("你好");
        //可以输出html信息，不过要先设置响应类型才能正确解析html
        printWriter.write("<h1>你好</h1>");
```

![image-20250113224908355](./pictures/image-20250113224908355.png)



### 响应图片等文件

响应图像、视频等文件需要用到字节输出流

```java
//首先读取文件
FileInputStream fileInputStream = new FileInputStream("D:\\code\\Idea_project\\java-web\\src\\main\\resources\\images\\test1.jpg");
//获取字节输出流
ServletOutputStream servletOutputStream = resp.getOutputStream();
//完成流的copy
byte[] buff = new byte[1024];
int len = 0;
while((len = fileInputStream.read(buff))!=-1){
    servletOutputStream.write(buff,0,len);
}
//关闭文件输入流
fileInputStream.close();
```

响应结果为一张图片

![image-20250113231715482](./pictures/image-20250113231715482.png)

可以添加依赖，来简写流的copy

依赖

```xml
    <dependency>
      <groupId>commons-io</groupId>
      <artifactId>commons-io</artifactId>
      <version>2.6</version>
    </dependency>
```



简写

```java
        //完成流的copy
//        byte[] buff = new byte[1024];
//        int len = 0;
//        while((len = fileInputStream.read(buff))!=-1){
//            servletOutputStream.write(buff,0,len);
//        }

        //使用工具，简化流的copy
        IOUtils.copy(fileInputStream,servletOutputStream);
```



## 13-SqlSessionFactory工具类抽取

我们每次在使用mybatis的时候，都要创建SqlSessionFactory对象，这样会有两个问题

1.代码重复量增多

2.每次创建SqlSessionFactory都会消耗资源池资源，浪费资源

为了解决这个问题，可以创建一个工具类

```java
import org.apache.ibatis.io.Resources;
import org.apache.ibatis.session.SqlSessionFactory;
import org.apache.ibatis.session.SqlSessionFactoryBuilder;

import java.io.IOException;
import java.io.InputStream;

public class SqlSessionFactoryUtils {
    private static SqlSessionFactory sqlSessionFactory;

    //静态代码块会随着类的加载而执行，且只会执行一次
    static {
        try {
            //1.加载核心配置文件，获取SqlSessionFactory对象
            String resource = "mybatis-config.xml";
            InputStream inputStream = Resources.getResourceAsStream(resource);
            sqlSessionFactory = new SqlSessionFactoryBuilder().build(inputStream);
        } catch (IOException e) {
            e.printStackTrace();
        }
    }

    public static SqlSessionFactory getSqlSessionFactory(){
        return sqlSessionFactory;
    }
}
```

这样创建SqlSessionFactory的代码就可以改成如下

```java
        //1.加载核心配置文件，获取SqlSessionFactory对象
//        String resource = "mybatis-config.xml";
//        InputStream inputStream = Resources.getResourceAsStream(resource);
//        SqlSessionFactory sqlSessionFactory = new SqlSessionFactoryBuilder().build(inputStream);

		//修改后的代码
        SqlSessionFactory sqlSessionFactory = SqlSessionFactoryUtils.getSqlSessionFactory();
```



# 基于springboot框架的请求与响应

## Day05-03.请求响应-请求-简单参数&实体参数

### 获取请求参数（简单参数）

获取请求参数有两种方式

一种是原始的获取方式，这种方式参考前面讲Request&Response部分时涉及到的获取请求参数的内容。

第二种方式是基于springboot框架的方式，下面只会讲第二种方式

获取请求参数时，只需要直接将方法的形参变量名定义成与请求参数名相同就行，然后定义的形参就会自动接收到对应的请求参数，而且还会自动进行类型转换

例如我创建了下面的Controller类

```java
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class GetParamController {

    @RequestMapping("/getParam")
    //要获取的参数就是name和age，所以方法的形参也定义为name和age
    public void getParam(String name,Integer age){
        //形参就是获取到的参数，直接拿来用就行
        System.out.println(name+" "+age);
    }
}
```

此时我的请求路径为

```
localhost:8080/getParam?name=tom&age=20
```

请求结果为，可以发现，形参的值就是请求的参数

![image-20250311174421272](./pictures/image-20250311174421272.png)

上面是get方式的请求，换成post的请求方式也是一样的，下图是我post的请求方式，参数放在请求体中



![image-20250311174701975](./pictures/image-20250311174701975.png)

请求结果也是一样的，图中上面是get请求结果，下面是post请求结果，可以发现使用post时，形参的值也和post的参数的值一样

![image-20250311174717104](./pictures/image-20250311174717104.png)

#### @RequestParam注解

此外，如果形参名和请求参数名对不上时，请求也不会出错，只不过名字对不上的那个参数无法被获取到。

但是Springboot提供了这种情况的获取参数的方式，那就是`RequestParam`注解，被这个注解修饰的形参会接收指定的请求参数

```java
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RequestParam;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class GetParamController {

    @RequestMapping("/getParam")
    //第一个RequestParam注解指的是将请求参数名为name的参数映射到形参a上，第二个指的是将请求参数名为age的参数映射到形参b上
    //这样即使形参名与请求参数名对不上也能获取到正确的请求参数
    public void getParam(@RequestParam(name = "name") String a, @RequestParam(name = "age") Integer b){
        System.out.println(a+" "+b);
    }

}
```

要注意的是,`RequestParam`注解有第二个属性：`required`，这个属性的默认值为true，表示请求必须带上这个参数，否则请求会出错

```java
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RequestParam;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class GetParamController {

    @RequestMapping("/getParam")
    //可以设置required为false，这样该参数可有可无
    //这里就是指请求时name参数是必须的，age参数可有可无
    public void getParam(@RequestParam(name = "name") String a, @RequestParam(name = "age",required = false) Integer b){
        System.out.println(a+" "+b);
    }

}
```

`@RequestParam`还有一个属性：`defaultValue`，该属性指定如果没有传递该参数，就取设定的默认值

下面是实现分页查询的Controller层的代码

```java
/**
 * 分页查询员工信息
 * @param page
 * @param pageSize
 * @return
 */
@GetMapping("/emps")			//如果没有传入page参数，page就取默认值为1，如果没有传入pageSize，pageSize就取默认值10
public Result page(@RequestParam(defaultValue = "1") Integer page,@RequestParam(defaultValue = "10") Integer pageSize){
    PageBean pageBean =  empService.page(page,pageSize);
    return Result.success(pageBean);
}
```





### 获取请求参数（实体参数）

上面获取参数的方式在请求参数没那么多的时候没什么问题，可是一旦请求参数多起来，比如10个、20个，那我们不可能在方法上定义几十个形参吧，所以就得换另一种方式，这种方式是用来接收实体参数的，我们只要将要接收的10个、20个，管他多少个，反正全封装到一个实体类对象中，接着在接收参数的方法上用这个实体类的变量来接收就可以一次性接收全部参数啦。当然实体类里面定义的属性名肯定要和请求参数名对的上哈。

下面举一个简单的例子，比如我们还是要接收和上面一样的两个参数：`name`、`age`，此时我们可以将这两个参数封装成一个`User`实体类

代码如下

User实体类

```java
public class User {
    private String name;
    private int age;

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    @Override
    public String toString() {
        return "User{" +
                "name='" + name + '\'' +
                ", age=" + age +
                '}';
    }
}
```

Controller类

```java
import com.example.pojo.User;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RequestParam;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class GetParamController {

    @RequestMapping("/getParam")
    //获取简单参数
    public void getParam(@RequestParam(name = "name") String a, @RequestParam(name = "age",required = false) Integer b){
        System.out.println(a+" "+b);
    }
	
    //获取实体参数
    @RequestMapping("/getPojo")
    public void getPojo(User user){
        System.out.println(user);
    }
}
```

我的请求路径还是

```
localhost:8080/getPojo?name=tom&age=20
```

运行结果如下，可以看到，请求参数name和age都被成功获取了

![image-20250311181003505](./pictures/image-20250311181003505.png)

这还仅仅是简单实体，那万一是一个复杂实体，请求参数该怎么填呢？

比如下面这个复杂实体，User类里面还包含了一个Addr类，Addr类里面又有两个成员变量

```java
public class User {
    private String name;
    private int age;
    private Addr addr;

    @Override
    public String toString() {
        return "User{" +
                "name='" + name + '\'' +
                ", age=" + age +
                ", addr=" + addr +
                '}';
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public Addr getAddr() {
        return addr;
    }

    public void setAddr(Addr addr) {
        this.addr = addr;
    }
}
```

Addr类

```java
public class Addr {
    private String addr1;
    private String addr2;

    public String getAddr1() {
        return addr1;
    }

    public void setAddr1(String addr1) {
        this.addr1 = addr1;
    }

    public String getAddr2() {
        return addr2;
    }

    public void setAddr2(String addr2) {
        this.addr2 = addr2;
    }

    @Override
    public String toString() {
        return "Addr{" +
                "addr1='" + addr1 + '\'' +
                ", addr2='" + addr2 + '\'' +
                '}';
    }
}
```

这种情况下的请求参数要这样写，这样请求就不会有问题

```
localhost:8080/getPojo?name=tom&age=20&addr.addr1=上海&addr.addr2=深圳
```

![image-20250311181452141](./pictures/image-20250311181452141.png)

返回结果

![image-20250311181514248](./pictures/image-20250311181514248.png)



### 获取请求参数（数组集合参数）

有时候请求参数里面有多个相同的参数名，比如下面这个请求。要处理这个请求有两种方式

```
localhost:8080/getArray?hobby=game&hobby=java&hobby=c++
```

#### 1.定义一个数组形参

此时如果我们要接收该请求的全部参数，就需要定义一个名字与参数名相同的数组来作为形参

```java
import com.example.pojo.User;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RequestParam;
import org.springframework.web.bind.annotation.RestController;

import java.util.Arrays;

@RestController
public class GetParamController {
    @RequestMapping("/getArray")
    //定义一个数组名与请求参数名相同的数组，用于接收请求中多个名字相同的参数
    public void getArray(String[] hobby){
        System.out.println(Arrays.toString(hobby));
    }
}
```

运行结果如下，这里注意一点：为什么请求参数是c++，结果却是c再带上两个空格呢？因为+在url中是特殊字符，应该对其特殊处理一下才能的到正确的结果

![image-20250311194128064](./pictures/image-20250311194128064.png)

使用下面这个请求才能得到正确的c++

```
localhost:8080/getArray?hobby=game&hobby=java&hobby=c%2B%2B
```

获取用post方式，将参数放在请求体中

![image-20250311194501224](./pictures/image-20250311194501224.png)

正确的结果

![image-20250311194513836](./pictures/image-20250311194513836.png)



#### 2.定义一个集合形参

与上一个方式基本一样，只不过这里用的是集合来接收请求参数，如下

```java
import com.example.pojo.User;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RequestParam;
import org.springframework.web.bind.annotation.RestController;

import java.util.Arrays;
import java.util.List;

@RestController
public class GetParamController {
    @RequestMapping("/getList")
    //使用集合来接收时需要用@RequestParam注解来绑定参数关系
    public void getList(@RequestParam List<String> hobby){
        System.out.println(hobby);
    }
}
```

如果参数是在路径里面的，此时就需要用`@PathVariable`注解，然后用了这个注解，即使不使用`@RequestParam`注解，集合也能够正常获得参数

例如下面的例子

```java
/**
 * 批量删除员工信息
 * @param ids
 * @return
 */
@DeleteMapping("/{ids}")
public Result delete(@PathVariable List<Integer> ids){
    empService.delete(ids);
    return Result.success();
}
```



### 获取请求参数（日期时间类参数）

当请求参数为日期时间时，我们又需要做特殊的处理。比如下面这个请求

```
localhost:8080/getTime?time=2025年03月11日 19:59:30
```

需要将接收到的时间封装成时间类对象，比如LocalDateTime，时间类对象的形参名也应和请求参数名一致，并且需要用`@DateTimeFormat`注解来定义请求参数的时间格式

如下

```java
import com.example.pojo.User;
import org.springframework.format.annotation.DateTimeFormat;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RequestParam;
import org.springframework.web.bind.annotation.RestController;

import java.time.LocalDateTime;
import java.util.Arrays;
import java.util.List;

@RestController
public class GetParamController {
    //获取时间参数
    @RequestMapping("/getTime")
    //使用@DateTimeFormat注解来定义要接收的时间格式
    public void getTime(@DateTimeFormat(pattern = "yyyy年MM月dd日 HH:mm:ss") LocalDateTime time){
        System.out.println(time);
    }
}
```

运行结果

![image-20250311200356384](./pictures/image-20250311200356384.png)



### 获取请求参数（JSON参数）

#### 1.如何使用postman发送JSON参数

如下图所示，要发送JSON参数需要使用post方法，然后在body中选择请求体的格式

![image-20250311200938349](./pictures/image-20250311200938349.png)



#### 2.获取请求中的JSON参数

需要定义一个实体类来封装JSON数据，如果JSON数据里面还包有其他对象，那么实体类的属性也要有对应的其他实体类

对于下面这个JSON参数，我们需要设计两个实体类，一个User类，用来接收name、age、addrs属性。还有一个Addr类，用来接收addr1、addr2属性

```json
{
    "name":"Arthur",
    "age":20,
    "addrs":{
        "addr1":"深圳",
        "addr2":"上海"
    }
}
```

User类

```java
public class User {
    private String name;
    private int age;
    private Addr addrs;

    @Override
    public String toString() {
        return "User{" +
                "name='" + name + '\'' +
                ", age=" + age +
                ", addrs=" + addrs +
                '}';
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public Addr getAddrs() {
        return addrs;
    }

    public void setAddrs(Addr addrs) {
        this.addrs = addrs;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }
}
```

Addr类

```java
public class Addr {
    private String addr1;
    private String addr2;

    public String getAddr1() {
        return addr1;
    }

    public void setAddr1(String addr1) {
        this.addr1 = addr1;
    }

    public String getAddr2() {
        return addr2;
    }

    public void setAddr2(String addr2) {
        this.addr2 = addr2;
    }

    @Override
    public String toString() {
        return "Addr{" +
                "addr1='" + addr1 + '\'' +
                ", addr2='" + addr2 + '\'' +
                '}';
    }
}
```



获取JSON参数还需要用到一个`@RequestBody`注解

```java
import com.example.pojo.User;
import org.springframework.web.bind.annotation.RequestBody;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;


@RestController
public class GetParamController {

    //获取JSON参数
    @RequestMapping("/getJSON")
    //需要使用@RequestBody注解
    public void getJSON(@RequestBody User user){
        System.out.println(user);
    }
}
```

运行结果，要注意，实体类中的属性名每一个都一定要和JSON数据中的键名对的上，不然可能会解析不到。

![image-20250311202500485](./pictures/image-20250311202500485.png)



### 获取请求参数（路径参数）

#### 1.获取单个路径参数

路径参数是在URL中直接传递参数，和get方式传递参数不同，get方式如下，参数是放在`?`后面的

```
localhost:8080/getPojo?name=tom&age=20
```

但路径参数不同，如下，参数并没有放在`?`后面，而是直接融入到URL里面了

```
localhost:8080/getPath/1
```

要取出这种路径参数，需要在定义请求路径的时候指出参数的位置，用`{...}`来标识路径参数

```java
import org.springframework.web.bind.annotation.*;

@RestController
public class GetParamController {
    //获取路径参数
    //在定义访问路径的时候就要指明参数位置，本次例子的参数位置就在/getpath/后面，参数名为id
    @RequestMapping("/getPath/{id}")
    //需要使用@PathVariable来获取路径参数，并将其与形参进行绑定
    public void getPath(@PathVariable Integer id){
        System.out.println(id);
    }
}
```

此时我的请求路径可以多样变化

```
localhost:8080/getPath/1	  	这样可以
localhost:8080/getPath/100		这样也可以
```

运行结果

![image-20250311203755108](./pictures/image-20250311203755108.png)



#### 2.获取多个路径参数

那我们要获取多个路径参数该怎么办呢？也简单，只要在定义路径时多用`{}`标记几个参数就好了。这里我们以接收2个路径参数为例子

```java
import org.springframework.web.bind.annotation.*;

@RestController
public class GetParamController {
    //获取多个路径参数
    //在定义路径时多用{}标记几个参数
    @RequestMapping("/getPath/{id}/{name}")
    //形参也多定义几个
    public void getPath2(@PathVariable Integer id,@PathVariable String name){
        System.out.println(id);
        System.out.println(name);
    }
}
```

此时我的请求路径可以这样来

```
localhost:8080/getPath/100/Sky			这样可以	
localhost:8080/getPath/300/Arthur		这样也可以
```

运行结果

![image-20250311204503922](./pictures/image-20250311204503922.png)



## Day05-07.请求响应-响应-@ResponseBody&统一响应结果

### 如何返回响应数据

当后端收到HTTP请求后会进行相应处理，然后需要返回响应数据，那这个响应数据要怎么返回呢？

这就要用到`@ResponseBody`注解，该注解是方法注解、类注解，被该注解标记的类的所有方法的返回值都会作为响应数据，如果响应数据是一个对象，则会先将对象转化为JSON格式，再进行响应。用该注解标记方法也是同理。

在Controller类中，我们不需要再额外使用`@ResponseBody`注解来进行标记，因为用于标记Controller类的`@RestController`注解已经被`@ResponseBody`注解标记，所以`ResponseBody`会被继承到Controller类来，就不需要再用`@ResponseBody`来标记了，也因此Controller类中所有方法的返回值都会自动作为响应数据返回

下面是`@RestController`注解的源码，从这可以看到`@ResponseBody`注解

![image-20250311230757780](./pictures/image-20250311230757780.png)

示例代码

```java
import com.example.pojo.User;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

import java.util.ArrayList;
import java.util.List;

@RestController
public class ResponseController {

    //返回字符串
    @RequestMapping("/getString")
    public String getString(){
        return "Hello SpringBoot";
    }

    //返回对象
    @RequestMapping("/getResponseUser")
    public User getUser(){
        User user = new User();
        user.setName("Arthur");
        user.setAge(20);
        return user;
    }

    //返回集合
    @RequestMapping("/getResponseList")
    public List<User> getList(){
        List<User> list = new ArrayList<>();
        list.add(new User("Arthur",20));
        list.add(new User("Sky",18));
        return list;
    }

}
```

请求结果依次为

返回字符串

![image-20250311232256624](./pictures/image-20250311232256624.png)

返回对象

![image-20250311232225865](./pictures/image-20250311232225865.png)

返回集合

![image-20250311232213277](./pictures/image-20250311232213277.png)

在开发中一般把处理每一个请求路径的方法叫做接口，所谓接口文档描述的就是这些方法的参数、返回值类型等等信息



### 统一响应结果(Result类)

如果在开发中我们的项目是像上面那样，一会儿返回字符串，一会儿返回对象，一会儿又返回结果，会非常不好处理。因为这样的返回结果没有一种统一的格式，前端需要对这些结果分别处理，这使得项目的沟通成本变高，开发效率降低。

为了解决这一个问题，项目规定了响应结果的统一格式，统一格式如下图

![image-20250311233050545](./pictures/image-20250311233050545.png)

其实就是将要返回的结果封装成了一个统一的对象，code表示响应码、msg表示响应的相关提示信息、data表示真正要返回的数据。

不管要返回的是什么数据，反正都将要返回的数据放到data对象中，这样前端就能用一种统一的方式来处理后端的响应结果，这大大提高了开发效率。

Result类如下

```java
public class Result {
    //返回状态码
    private Integer code;
    //返回提示信息
    private String msg;
    //返回响应数据
    private Object data;

    //提供静态方法，用于快速封装响应结果
    public static Result success(Object data){
        return new Result(1,"success",data);
    }

    public static Result success(){
        return new Result(1,"success",null);
    }

    public static Result error(String msg){
        return new Result(0,msg,null);
    }
    
    public Result(Integer code, String msg, Object data) {
        this.code = code;
        this.msg = msg;
        this.data = data;
    }

    public Integer getCode() {
        return code;
    }

    public void setCode(Integer code) {
        this.code = code;
    }

    public String getMsg() {
        return msg;
    }

    public void setMsg(String msg) {
        this.msg = msg;
    }

    public Object getData() {
        return data;
    }

    public void setData(Object data) {
        this.data = data;
    }

    @Override
    public String toString() {
        return "Result{" +
                "code=" + code +
                ", msg='" + msg + '\'' +
                ", data=" + data +
                '}';
    }
}
```

使用Result类来封装响应数据

```java
import com.example.pojo.Result;
import com.example.pojo.User;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

import java.util.ArrayList;
import java.util.List;

@RestController
public class ResponseController {

    //返回字符串
    @RequestMapping("/getString")
    public Result getString(){
        return Result.success("Hello SpringBoot");
    }

    //返回对象
    @RequestMapping("/getResponseUser")
    public Result getUser(){
        User user = new User();
        user.setName("Arthur");
        user.setAge(20);
        //使用Result的静态方法来快速封装结果
        return Result.success(user);
    }

    //返回集合
    @RequestMapping("/getResponseList")
    public Result getList(){
        List<User> list = new ArrayList<>();
        list.add(new User("Arthur",20));
        list.add(new User("Sky",18));
        //使用Result的静态方法来快速封装结果
        return Result.success(list);
    }

}
```

此时返回结果分别为

返回字符串

![image-20250312084437594](./pictures/image-20250312084437594.png)

返回对象

![image-20250312084505756](./pictures/image-20250312084505756.png)

返回集合

![image-20250312084537354](./pictures/image-20250312084537354.png)

可以发现最终结果都是统一的JSON格式。



## Day05-08.请求响应-响应-案例

### 请求响应案例

案例需要获取员工数据，返回统一结果，并在页面渲染展示。

员工数据xml文件

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<emps>
    <emp>
        <name>雾子</name>
        <age>20</age>
        <image>img/比心雾子.gif</image>
        <!-- 1: 男, 2: 女 -->
        <gender>2</gender>
        <!-- 1: 讲师, 2: 班主任 , 3: 就业指导 -->
        <job>1</job>
    </emp>

    <emp>
        <name>Juno</name>
        <age>18</age>
        <image>img/大眼juno.gif</image>
        <gender>2</gender>
        <job>1</job>
    </emp>

    <emp>
        <name>Mercy</name>
        <age>30</age>
        <image>img/黑猫摩西.gif</image>
        <gender>2</gender>
        <job>2</job>
    </emp>
</emps>
```

要解析xml文件需要用到dom4j，在pom文件中导入dom4j的依赖

dom4j的坐标为

```xml
<dependency>
    <groupId>org.dom4j</groupId>
    <artifactId>dom4j</artifactId>
    <version>2.1.3</version>
</dependency>
```

在dom4j框架下创建一个解析员工信息xml文件的工具类

```java
import org.dom4j.Document;
import org.dom4j.Element;
import org.dom4j.io.SAXReader;

import java.lang.reflect.Constructor;
import java.util.ArrayList;
import java.util.List;

//xml解析工具类
public class XmlParseUtils {
    //泛型方法

    /**
     * 该方法用于将xml解析成目标类的对象集合
     *
     * @param file        xml文件路径
     * @param targetClass 目标类
     * @param <T>         泛型
     * @return 返回目标类对象集合
     */
    public static <T> List<T> parse(String file, Class<T> targetClass) {
        List<T> list = new ArrayList<>();
        //需要先导入dom4j依赖，在pom文件中导入
        //使用dom4j提供的解析器对象
        SAXReader saxReader = new SAXReader();
        try {
            //读取xml文件，将xml文件解析为Document对象
            Document dom = saxReader.read(file);
            //获取根标签
            Element root = dom.getRootElement();
            //elements返回当前标签下的所有子标签，而user就是根标签下的所有子标签
            List<Element> elements = root.elements();

            //遍历每一个user标签，来获取每一个user对象的具体数据，并将其封装成目标对象
            for (Element element : elements) {
                //使用反射来获取对象数据并将其封装成对象
                String name = element.element("name").getText();
                String age = element.element("age").getText();
                String image = element.element("image").getText();
                String gender = element.element("gender").getText();
                String job = element.element("job").getText();

                //获取目标类的构造器
                Constructor<T> constructor = targetClass.getDeclaredConstructor(String.class, Integer.class, String.class, String.class, String.class);
                //使用获取到的构造器来新建对象
                constructor.setAccessible(true);
                T object = constructor.newInstance(name,Integer.parseInt(age),image,gender,job);
                list.add(object);
            }

        } catch (Exception e) {
            throw new RuntimeException(e);
        }
        return list;
    }
}
```

创建Controller类

```java
import com.example.pojo.Result;
import com.example.pojo.User2;
import com.example.utils.XmlParseUtils;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

import java.util.List;

@RestController
public class EmpController {
    @RequestMapping("/listEmp")
    public Result listEmp(){
        String file = this.getClass().getClassLoader().getResource("emp.xml").getFile();
        List<User2> emp = XmlParseUtils.parse(file, User2.class);
        for (User2 user : emp) {
            //处理user的性别
            if(user.getGender().equals("1")){
                user.setGender("男");
            }else{
                user.setGender("女");
            }

            //处理user的职责
            if(user.getJob().equals("1")){
                user.setJob("治疗");
            }else {
                user.setJob("支援");
            }
        }
        return Result.success(emp);
    }

}
```

前端页面emp.html如下

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>员工信息</title>
</head>

<link rel="stylesheet" href="element-ui/index.css">
<script src="./js/vue.js"></script>
<script src="./element-ui/index.js"></script>
<script src="./js/axios-0.18.0.js"></script>

<body>
    <h1 align="center">员工信息列表展示</h1>
    <div id="app">
        <el-table :data="tableData" style="width: 100%"  stripe border >
            <el-table-column prop="name" label="姓名" align="center" min-width="20%"></el-table-column>
            <el-table-column prop="age" label="年龄" align="center" min-width="20%"></el-table-column>
            <el-table-column label="图像" align="center"  min-width="20%">
                <template slot-scope="scope">
                    <el-image :src="scope.row.image" style="width: 80px; height: 50px;"></el-image>
                </template>
            </el-table-column>
            <el-table-column prop="gender" label="性别" align="center"  min-width="20%"></el-table-column>
            <el-table-column prop="job" label="职位" align="center"  min-width="20%"></el-table-column>
        </el-table>
    </div>
</body>

<style>
    .el-table .warning-row {
        background: oldlace;
    }
    .el-table .success-row {
        background: #f0f9eb;
    }
</style>

<script>
    new Vue({
        el: "#app",
        data() {
            return {
                tableData: []
            }
        },
        mounted(){
            axios.get('/listEmp').then(res=>{
                if(res.data.code){
                    this.tableData = res.data.data;
                }
            });
        },
        methods: {
        }
    });
</script>
</html>
```

运行结果如下

![image-20250312094814598](./pictures/image-20250312094814598.png)

要注意一个路径问题，springboot提供了静态资源的访问路径，在resource下的static文件夹，将图片资源放在这，如下图

![image-20250312094954817](./pictures/image-20250312094954817.png)

就能直接通过路径·`img/图片文件名`来访问到图片，但如果是放在resources文件夹下而没有放在static文件夹下就不行，上图中两种放法我都试了，没有放在static下的图片访问会失败。



# JSP

## 01-JSP概述&快速入门&原理

JSP是Java Server Pages的简写，叫做java服务端页面，是html和java的结合

### 使用JSP的步骤

#### 1.导入JSP依赖

注意导入JSP依赖时要设置生效范围为provided，因为tomcat里面也存在JSP依赖，如果不设置生效范围会发生冲突

```xml
    <dependency>
      <groupId>javax.servlet.jsp</groupId>
      <artifactId>jsp-api</artifactId>
      <version>2.2</version>
      <scope>provided</scope>
    </dependency>
```



#### 2.编写jsp文件

```jsp
<%--
  Created by IntelliJ IDEA.
  User: Aurora
  Date: 2025/1/14
  Time: 15:20
  To change this template use File | Settings | File Templates.
--%>
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
<head>
    <title>Hello JSP</title>
</head>
<body>
    <h1>
        hello jsp
    </h1>
    <%
        System.out.println("hello JSP");
    %>
</body>
</html>
```



#### 3.无法编译jsp的问题

在运行时出现了如下问题

![image-20250114164436337](./pictures/image-20250114164436337.png)

![image-20250114164447733](./pictures/image-20250114164447733.png)

上网找解决方法，发现可能是以下问题导致的

1.最新版的jdk17自带servlet和jsp等jar包，而运行tomcat7会导致jar包冲突

解决办法是

1.仍然使用tomcat7，但是要将jdk版本降到1.7

2.将tomcat7升级为tomcat10

我这里采用的是第二种方法，升级tomcat7为tomcat10

如下图所示，运行成功了

![image-20250114164826201](./pictures/image-20250114164826201.png)

![image-20250114164834182](./pictures/image-20250114164834182.png)



## 2025年2月6日补充

#### 解决无法编译jsp问题

今天又遇到了jsp无法编译的问题，用上面的方法还是没法解决，搞了半天最后也不知道怎么就解决了，这里把用的jdk版本、tomcat版本和pom.xml文件放在这给出一个参考，反正我今天这样设置就能运行了，先参考参考吧

##### jdk版本

![image-20250206184615014](./pictures/image-20250206184615014.png)

![image-20250206184635605](./pictures/image-20250206184635605.png)

![image-20250206184653717](./pictures/image-20250206184653717.png)

![image-20250206184704465](./pictures/image-20250206184704465.png)



##### tomcat版本

tomcat用的是插件，tomcat7

```xml
  <build>
    <plugins>
      <plugin>
        <groupId>org.apache.tomcat.maven</groupId>
        <artifactId>tomcat7-maven-plugin</artifactId>
        <version>2.2</version>
        <configuration>
          <port>80</port>
        </configuration>
      </plugin>
    </plugins>
  </build>
```



##### pom.xml文件

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>

  <groupId>org.example</groupId>
  <artifactId>filter-demo</artifactId>
  <version>1.0-SNAPSHOT</version>

  <packaging>war</packaging>

  <properties>
    <maven.compiler.source>8</maven.compiler.source>
    <maven.compiler.target>8</maven.compiler.target>
  </properties>


  <dependencies>

    <dependency>
      <groupId>javax.servlet</groupId>
      <artifactId>javax.servlet-api</artifactId>
      <version>3.1.0</version>
      <scope>provided</scope>
    </dependency>


  </dependencies>

  <build>
    <plugins>
      <plugin>
        <groupId>org.apache.tomcat.maven</groupId>
        <artifactId>tomcat7-maven-plugin</artifactId>
        <version>2.2</version>
        <configuration>
          <port>80</port>
        </configuration>
      </plugin>
    </plugins>
  </build>

</project>
```



#### 解决jsp输出中文乱码问题

只需要在jsp文件中添加一行代码

```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
```

![image-20250206185109421](./pictures/image-20250206185109421.png)



### 总结

JSP实际上是一个Servlet，因为服务器在调用JSP的时候会自动将JSP转换成servlet，然后再将servlet编译成字节码来提供服务

通过查看target文件夹，可以找到由JSP转换来的servlet类文件

![image-20250114165742590](./pictures/image-20250114165742590.png)



查看这个类文件

![image-20250114165852210](./pictures/image-20250114165852210.png)

可以找到一个叫`_jspService`的函数，刚刚在JSP文件里面写的java代码就在这里，运行JSP文件，实际上就是运行这个函数

![image-20250114170014058](./pictures/image-20250114170014058.png)



## 02-JSP脚本

### JSP有三种脚本

#### 1.`<%....%>`

这种脚本会放在_jspService函数中

例如

![image-20250114170249204](./pictures/image-20250114170249204.png)

会放在_jspService函数中

![image-20250114170341326](./pictures/image-20250114170341326.png)



#### 2.`<%=.....%>`

这种脚本会将对应的代码放在`out.print()`中

例如

![image-20250114172350163](./pictures/image-20250114172350163.png)

会放在

![image-20250114172401785](./pictures/image-20250114172401785.png)



#### 3.`<%!....%>`

这种脚本会把写在这里面的代码放在_jspService函数外边，适合用于创建成员变量和成员函数

例如

![image-20250114172623134](./pictures/image-20250114172623134.png)



会放在

![image-20250114172637167](./pictures/image-20250114172637167.png)





## 04-EL表达式

EL表达式的主要功能是获取数据，其简化了JSP的数据获取

语法如下

获取expression的数据，expression放在request域中，通过转发传给JSP文件

```jsp
${expression}		
```

### 使用步骤

1.在Servlet中获取数据

2.将数据放入request域中

3.将请求转发给JSP

```java
package com.example.response;

import com.example.pojo.Brand;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.io.IOException;
import java.util.ArrayList;
import java.util.List;

@WebServlet("/EL")
public class ELService extends HttpServlet {

    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        //1.先获取数据
        List<Brand> brands = new ArrayList<Brand>();
        brands.add(new Brand(1,"三只松鼠","三只松鼠",100,"三只松鼠，好吃不上火",1));
        brands.add(new Brand(2,"优衣库","优衣库",200,"优衣库，服适人生",0));
        brands.add(new Brand(3,"小米","小米科技有限公司",1000,"为发烧而生",1));

        //2.然后将数据放入request域中
        req.setAttribute("Brands",brands);

        //3.将请求转发给JSP
        req.getRequestDispatcher("/EL.jsp").forward(req,resp);

    }
}

```

4.在JSP文件中通过EL表达式获取数据

```jsp
<%--
  Created by IntelliJ IDEA.
  User: Aurora
  Date: 2025/1/14
  Time: 19:29
  To change this template use File | Settings | File Templates.
--%>
<%@ page contentType="text/html;charset=UTF-8" language="java" isELIgnored="false" %>
<html>
<head>
    <title>Title</title>
</head>
<body>
    ${Brands}
</body>
</html>

```

### 解决JSP不识别EL表达式的问题

在page标签中再加上isELIgnored="false"

```jsp
<%@ page contentType="text/html;charset=UTF-8" language="java" isELIgnored="false" %>
```



## 05-JSTL-if&foreach

JSTL 是JSP Standar Tag Library 的缩写，表示JSP标准标签库，其通过定义标签库来简化了JSP 中java代码的书写

### 使用步骤

#### 1.导入依赖

要导入两个依赖，一个`jstl`，另一个`standard`

```xml
    <dependency>
      <groupId>jstl</groupId>
      <artifactId>jstl</artifactId>
      <version>1.2</version>
    </dependency>
    <dependency>
      <groupId>taglibs</groupId>
      <artifactId>standard</artifactId>
      <version>1.1.2</version>
    </dependency>
```



#### 2.为JSTL标签定义前缀

前缀名可以自定义，一般为c

```jsp
<%@taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
```



### `c:if`

注意判断条件要一起写在大括号内`{}`

```jsp
<%--
  Created by IntelliJ IDEA.
  User: Aurora
  Date: 2025/1/14
  Time: 20:26
  To change this template use File | Settings | File Templates.
--%>
<%@ page contentType="text/html;charset=UTF-8" language="java" isELIgnored="false" %>
<%@taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
<html>
<head>
    <title>Title</title>
</head>
<body>
    <c:if test="${b==1}">
        true
    </c:if>

    <c:if test="${b==0}">
        false
    </c:if>

</body>
</html>

```



### `c:foreach`

foreach的基本用法

```jsp
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<%@ page import="com.example.pojo.Brand" %>
<%@ page import="java.util.ArrayList" %>
<%@ page import="java.util.List" isELIgnored="false" %>
<%@taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Title</title>
</head>
<body>
<input type="button" value="新增"><br>
<hr>
<table border="1" cellspacing="0" width="800">
  <tr>
    <th>序号</th>
    <th>品牌名称</th>
    <th>企业名称</th>
    <th>排序</th>
    <th>品牌介绍</th>
    <th>状态</th>
    <th>操作</th>

  </tr>
    <c:forEach items="${Brands}" var="brand">
     <tr align="center">
       <td>${brand.id}</td>
  <td>${brand.brandName}</td>
  <td>${brand.companyName}</td>
  <td>${brand.ordered}</td>
  <td>${brand.description}</td>
       <c:if test="${brand.status==1}">
         <td>启用</td>
       </c:if>
       <c:if test="${brand.status==0}">
         <td>禁用</td>
       </c:if>

  <td><a href="#">修改</a> <a href="#">删除</a></td>
     </tr>

    </c:forEach>

</table>

</body>
</html>
```



还可以编成for循环的用法

```jsp
  <c:forEach begin="1" end="10" step="1" var="i">
    ${i}
  </c:forEach>
```



![image-20250114211140826](./pictures/image-20250114211140826.png)



# 分层解耦

下面的代码是基于springboot框架的一个获取员工信息的一个功能代码，具体案例步骤请在本笔记的大纲中搜索`基于springboot框架的请求与响应`

```java
import java.util.List;

@RestController
public class EmpController {
    @RequestMapping("/listEmp")
    public Result listEmp(){
        //该功能代码大致可分为3部分
        //1.访问数据文件，读取数据
        String file = this.getClass().getClassLoader().getResource("emp.xml").getFile();
        List<User2> emp = XmlParseUtils.parse(file, User2.class);
        //2.处理获取的数据
        for (User2 user : emp) {
            //处理user的性别
            if(user.getGender().equals("1")){
                user.setGender("男");
            }else{
                user.setGender("女");
            }

            //处理user的职责
            if(user.getJob().equals("1")){
                user.setJob("治疗");
            }else {
                user.setJob("支援");
            }
        }
        //3.返回数据
        return Result.success(emp);
    }

}
```

看一下这段代码，可以发现，这段代码将读取数据，以及对数据的处理全放在一个方法中了。但在开发中，我们要尽量遵循单一职责原则，也就说，每一个类或者方法都尽量只实现一个功能，这样代码就不会显得那么臃肿。下面要讲的内容，就是要学会对项目代码进行分层解耦，以达到这个目的。

## 06-MVC模式和三层架构

### MVC模式

MVC是一种开发模式，其中

M：Model，业务模型，负责业务处理

V：View，视图，负责页面展示

C：Controller，控制器，负责调用Model和View

在下图示例中，浏览器将请求发给Controller，Controller收到请求后对请求进行处理，然后调用Model来对请求进行业务处理，接着将业务处理后的数据传给View，使其显示在页面上，并返回给浏览器

![image-20250114222724274](./pictures/image-20250114222724274.png)





### 三层架构

三层架构包括：

数据访问层：负责对数据库进行基本的增删改查操作，常见的是开发中的Mapper/dao部分的代码

业务逻辑层：对业务逻辑进行封装，可以通过调用数据访问层的基本操作来形成复杂的逻辑处理操作，常见的是开发中的Service部分

表现层：接收请求，封装数据，调用业务逻辑层，常见的是开发中的Controller/web部分的代码

![image-20250114223305006](./pictures/image-20250114223305006.png)

### 基于springboot框架下的三层架构

上面的三层架构在springboot架构下的具体实现如下：

Controller层：控制层，用于接收前端发送的请求，对请求进行处理，并响应数据。对应上面三层架构的表现层

Service层：业务逻辑层，处理具体的业务逻辑。对应上面三层架构的业务逻辑层

Dao层：数据访问层（Data Access Object  也叫做持久层），负责访问数据库，对数据进行增删改查，将从数据库拿到的数据交给Service层处理。对应上面三层架构的数据访问层

基于这种三层架构，项目的整个业务流程大致为：浏览器发送请求给到Controller层，Controller层调用Service层来进行业务处理，Service层再去调用Dao层去获取相关数据，Dao层与数据库进行交互，并返回数据给Service层，Service层再对获取到的数据进行处理，处理好后将处理结果返回给Controller层，Controller层再对结果进行转发，将结果返回给浏览器。



基于这种三层架构，我们来修改上面获取员工信息的代码，此时项目结构会变成下面这样，每一层都有一个单独的包文件

![image-20250312143221233](./pictures/image-20250312143221233.png)

dao层接口

```java
import com.example.pojo.User2;

import java.util.List;

public interface EmpDao {
    //由于访问数据库的方式有很多，所以可以创建一个接口，不管用啥方法反正先实现接口即可，这样程序的灵活性会更好
    //创建一个获取员工数据的Dao层接口，方便面向接口编程
    public List<User2> listEmp();
}
```

dao层实现

```java
import com.example.dao.EmpDao;
import com.example.pojo.User2;
import com.example.utils.XmlParseUtils;

import java.util.List;

public class EmpDaoA implements EmpDao {
    //实现接口
    //实现Dao层
    @Override
    public List<User2> listEmp() {
        String file = this.getClass().getClassLoader().getResource("emp.xml").getFile();
        List<User2> list = XmlParseUtils.parse(file, User2.class);
        return list;
    }
}
```



service层接口

```java
import com.example.pojo.User2;

import java.util.List;

public interface EmpService {
    public List<User2> listEmp();
}
```

service层实现

```java
import com.example.dao.EmpDao;
import com.example.dao.impl.EmpDaoA;
import com.example.pojo.User2;
import com.example.service.EmpService;

import java.util.List;

public class EmpServiceA implements EmpService {
    //创建一个Dao层的对象以获取数据
    //面向接口编程
    private EmpDao dao = new EmpDaoA();

    //实现service层，进行业务逻辑处理
    @Override
    public List<User2> listEmp() {
        //使用Dao层的对象来获取数据
        List<User2> emp = dao.listEmp();
        //然后对数据进行业务处理
        for (User2 user : emp) {
            //处理user的性别
            if(user.getGender().equals("1")){
                user.setGender("男");
            }else{
                user.setGender("女");
            }

            //处理user的职责
            if(user.getJob().equals("1")){
                user.setJob("治疗");
            }else {
                user.setJob("支援");
            }
        }
        //最后将处理结果返回给Controller层
        return emp;
    }
}
```



controller层实现

```java
import com.example.pojo.Result;
import com.example.pojo.User2;
import com.example.service.EmpService;
import com.example.service.impl.EmpServiceA;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

import java.util.List;

@RestController
public class EmpController {
    //Controller层只需要通过Service层的对象来获取业务处理的结果
    private EmpService service= new EmpServiceA();
    @RequestMapping("/listEmp")
    public Result listEmp(){
        //通过Service层来进行业务处理
        List<User2> emp = service.listEmp();
        //将处理结果封装成Result并返回给浏览器
        return Result.success(emp);
    }

}
```

可以发现，相比原来的Controller层的代码，基于三层架构下的代码更加简洁，代码复用性较高。





## Day05-10.分层解耦-分层解耦（IOC-DI引入）

### 什么是分层解耦

在理解分层解耦之前首先要明白两个概念：

#### 1.内聚

内聚指的是软件中各个功能模块内部的功能联系，用于度量一个模块内部各个元素彼此结合的精密程度。

比如我有一个获取员工信息的功能模块，在这个模块里面，几乎所有元素都是和员工有关的，而不存在什么飞机、大炮啥的与员工信息一点关系也没有的代码，这就说明这个功能模块是高内聚的。



#### 2.耦合

耦合是用来衡量软件中各个层/模块之间的依赖、关联程度。

比如上面我们用三层架构来修改的获取员工信息的代码，如果Service要获取数据就要调用Dao层的代码，即：需要通过`private EmpDao dao = new EmpDaoA();`这行代码来创建一个Dao层的对象，此时如果Dao层的代码发生了变化，即：获取数据的类名变成了EmpDaoB，那么我们Service层的代码也要跟着变化，这就说明这两层的代码是耦合的。



在开发中我们要遵循高内聚、低耦合的原则。

springboot提供了方法来帮助我们实现软件的高内聚、低耦合。

一个是IOC，另一个是DI



### 实现分层解耦的三个思想

springboot实现分层解耦是基于IOC、DI、Bean这三个思想。

#### 什么是IOC

IOC是Inversion Of Control 的缩写，即：控制反转。IOC思想是springboot的一大核心思想。IOC思想是将对象的创建控制权由程序自生转移到外部。比如这行代码`private EmpDao dao = new EmpDaoA();`，就改成`private EmpDao dao;`，也就是说不需要程序自己来创建要用的对象，那交给谁来创建呢？交给外部。外部是啥？springboot专门提供了一个“外部”来实现这个思想，这个“外部”就是一个容器，IOC容器。IOC容器专门用于创建和管理对象。由IOC容器来创建对象，也就不需要程序自己创建了。



#### 什么是DI

DI是Dependency Injection 的缩写，即：依赖注入。容器为应用程序提供运行时所依赖的资源，称为依赖注入。

springboot也就是靠IOC容器和DI这两一起来，实现了我们程序的高内聚、低耦合。IOC容器负责创建程序需要的对象资源，再通过依赖注入将这些对象资源给到程序使用。



#### 什么是Bean对象

IOC容器中创建、管理的对象被称为Bean





## Day05-11.分层解耦-IOC&DI-入门

### 使用IOC&DI思想实现分层解耦

1.使用`@Component`注解实现控制反转，即：将实现类交给IOC容器管理。

如图所示，Service层和Dao层的实现类都加上了`@Component`注解

![image-20250312151015832](./pictures/image-20250312151015832.png)



2.使用`@Autowired`注解实现依赖注入。

在获取资源对象的代码上面使用`@Autowired`注解

如下图所示，Contorller要使用Service对象，因此在创建Service对象的那行代码上使用了`@Autowired`注解；Service也要使用Dao对象，因此在创建Dao对象的那行代码上也使用了`@Autowired`注解

![image-20250312151333036](./pictures/image-20250312151333036.png)

通过上面两步即可实现分层解耦

此时如果业务层的代码发生了变化，实现业务的实现类从EmpServiceA变成了EmpServiceB，我们只需要将EmpServiceA中的`@Component`注解注释掉，然后为EmpServiceB添加`@Component`注解，这样，业务就能很方便的切换，Controller层的代码也就不需要改动。

也别想着为EmpServiceA和EmpServiceB都加上`@Component`注解，因为这样会报错😂

你看嘛

![image-20250312152244840](./pictures/image-20250312152244840.png)



## Day05-12.分层解耦-IOC&DI-IOC详解

### Bean的声明

要将某个对象交给IOC容器管理，可以使用的注解不止有`@Component`一个，还有一些`@Component`的衍生注解，如下图

![image-20250312152941647](./pictures/image-20250312152941647.png)

我们随便查看一个衍生注解的源代码

![image-20250312153039811](./pictures/image-20250312153039811.png)

可以看到，衍生注解实际上也被`@Component`注解标记了，并且衍生注解还有一个value属性，该属性用于设置Bean对象的名字，如果不指定的话，Bean对象的名字默认为首字母小写的类名

下面用`@Component`的衍生注解来标记每一层的实现类，控制台中还可以查看到IOC容器中每一个Bean的名字。

Controller类使用的`@Controller`注解

![image-20250312153704815](./pictures/image-20250312153704815.png)



几点注意事项

![image-20250312155030116](./pictures/image-20250312155030116.png)



### Bean组件扫描

 前面声明Bean的四大注解，如果要想生效还需要被组件扫描注解`@ComponentScan`扫描。那为什么前面讲的时候都没提过这个注解呢？因为这个注解以及包含在了启动类声明注解`@SpringBootApplication`中，其默认扫描范围是启动类所在的包及其子包。因此，只要我们的实现类都放在与启动类相同的一个包或其子包下，就会自动被扫描，也就不需要我们去显式地声明`@ComponentScan`注解了。

我们来验证一下，讲dao包放到外面去，此时启动程序会报如下错误

![image-20250312160109070](./pictures/image-20250312160109070.png)

要想解决，也不是没有办法，可以在启动类中显示地用`@ComponentScan`注解来声明扫描范围，如下图所示

![image-20250312160406496](./pictures/image-20250312160406496.png)

但是不建议这样干，毕竟也没有必要硬要把包放在启动类所在的包外面，这也没啥特别的效果，还徒增配置代码，所以建议就将包放在与启动了同级的包下就好了



## Day05-13.分层解耦-IOC&DI-DI详解

### Bean注入

使用`@Autowired`注解，默认是按照类型进行的，也就是说根据被注解的变量的类型来决定要注入那个类型的依赖，再去IOC容器中找对应的依赖。但是当同一个类型的Bean存在两个时，这种依赖注入方法就会报错，如下

![image-20250312152244840](./pictures/image-20250312152244840.png)

要想解决这个问题，有三种方式

#### 1.`@Primary`

被这个注解标记的实现类会被优先选择用来进行依赖注入，如下图，此时如果有这样一段代码

```java
@Autowired
private EmpService service;
```

会优先使用EmpServiceA

![image-20250312161834279](./pictures/image-20250312161834279.png)

#### 2.`@Qualifier`

使用这个注解来声明Bean的名字，声明Bean的名字后，IOC容器会用指定名字的Bean来进行依赖注入，如下图

此时Controller中的service所接收的对象就是EmpServiceB的对象，因为Bean的默认名为首字母为小写的类名，也就是`@Qualifier`声明的empServiceB

![image-20250312162235614](./pictures/image-20250312162235614.png)

#### 3.`@Resource`

这个注解和`@Qualifier`注解一样，也是用来声明一个Bean的名字，与`@Qualifier`注解的不同点在于：`@Qualifier`注解要配合`@Autowired`注解一起使用，而`@Qualifier`是单独使用的。还有一小点不同的是`@Resource`注解声明Bean名字时需要用name属性来指定，而`@Qualifierr`不需要

![image-20250312162723144](./pictures/image-20250312162723144.png)



#### 4.`@Autowired`和`@Resource`的区别

1).`Autowired`默认是按照类型注入，而`@Resource`默认是按照名称注入

2).`Autowired`是spring框架提供的注解，而`Resource`是JDK提供的注解



### 三大框架

三层架构中，每一层都有一个重要的框架，合起来有三大框架，如下：

表现层：SpringMVC

业务逻辑层：Spring

数据访问层：MyBatis





# 会话跟踪技术

什么是会话？

当打开浏览器向服务器发送第一条请求时会话就建立了，直到其中一方断开连接，会话才会结束。所以可以把会话理解为浏览器与服务器的联系。一次会话存在多次请求，而由于HTTP协议是无状态协议，因此同一个会话中，每个请求之间是没有任何联系的，而会话跟踪技术就是用来判断多个请求是否来自同一个浏览器，也就是说是否属于同一个会话，因为在实际中，会有很多浏览器与服务器建立连接，也就会产生很多会话。会话跟踪技术判断请求来自同一次会话时，就能够实现在多次请求之间共享数据。

当前主流的会话跟踪技术有：

1.客户端会话技术：Cookie

2.服务端会话技术：Session

3.令牌技术



## 02-Cookie-基本使用

Cookie是HTTP协议支持的技术，提供了一个请求头:`Cookie`用于携带Cookie信息给服务器，和一个响应头:`Set-Cookie`用于给浏览器发送Cookie。浏览器收到Cookie时，会自动将Cookie存储到本地，然后在每次发送请求时自动将本地的Cookie信息发送给服务器



Cookie的使用对于后端来说，主要关注点有两个

一个是如何发送cookie

另一个是如何接收cookie

### 如何发送cookie

#### 1.建立Cookie对象

Cookie对象接收的是一个键值对

```java
//创建Cookie对象
Cookie cookie = new Cookie("username","zs");
//创建了一个键值对为username:zs的Cookie
```



#### 2.在响应中添加对应的cookie

将cookie添加到响应中需要用到响应的addCookie函数

```java
//将上面创建的cookie添加到响应中
resp.addCookie(cookie);
```



下面是完整的代码

```java
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        //1.创建cookie对象
        Cookie cookie = new Cookie("username","zs");

        //2.发送cookie，将cookie放入响应中
        resp.addCookie(cookie);

    }

```

在访问对应的站点后，就可以从浏览器中找到对应的Cookie信息

![image-20250120191707892](./pictures/image-20250120191707892.png)



### 如何接收cookie

#### 1.接收cookie数组

接收cookie数组需要用到request的函数`getCookies`

```java
//接收cookie数组
Cookie[] cookies = req.getCookies();
```



#### 2.遍历cookie数组，找出需要的cookie信息

获取cookie信息需要用到`getName`函数和`getValue`函数

```java
//遍历上面获取的cookie数组，找出需要的cookie信息
for(Cookie cookie : cookies){
    String name = cookie.getName();
    if(name.equals("username")){
        System.out.println("username:" + cookie.getValue());
    }  
}
```



完整代码如下：

```java
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        //1.首先接收cookie数组
        Cookie[] cookies = req.getCookies();

        //2.然后遍历cookie数组，取出需要的cookie信息
        for(Cookie cookie :cookies){
            String name = cookie.getName();
            if(name.equals("username")){
                System.out.println("username:" + cookie.getValue());
            }
        }

    }
```



访问对应的网站后，可以得到下图结果，下图成功获取到了username的cookie信息

![image-20250120193347007](./pictures/image-20250120193347007.png)



## 03-Cookie原理&细节

### Cookie原理

cookie是基于HTTP协议的

后端发送Cookie时会在响应标头里面给出`Set-Cookie`,用于告知浏览器要保存的Cookie

![image-20250120194907504](./pictures/image-20250120194907504.png)



浏览器发送Cookie信息给后端时，会在请求标头里添加`Cookie`，用于告知后端浏览器所具有的Cookie信息

![image-20250120195054809](./pictures/image-20250120195054809.png)



### Cookie使用细节

#### Cookie存活时间

Cookie是存储在浏览器的内存中的，默认情况下，Cookie的存活时间是一直到浏览器关闭为止，可以通过在后端使用`setMaxAge`这个函数来修改默认情况，自定义cookie存活时间

#### `setMaxAge`的使用

可以设置三种参数：

##### 1.设置为正数

将cookie存储在硬盘中，进行持久化存储，在规定时间后删除

```java
//设置cookie存活时间，存活时间为7天
cookie.setMaxAge(60*60*24*7);
```

这样获取到的cookie的信息就可以保存7天，如下图所示到期时间刚好是7天后

![image-20250120201033667](./pictures/image-20250120201033667.png)



##### 2.设置为负数

这是Cookie的默认情况，即cookie会一直存活到浏览器关闭为止

##### 3.设置为0

这种情况用于删除对应的cookie



### Cookie存储中文

默认情况下Cookie不能存储中文

如果后端强制发送中文的Cookie信息，那么浏览器就会报错

![image-20250120203015476](./pictures/image-20250120203015476.png)

所以为了满足存储中文的需求，需要按以下方法来存储中文

#### 1.首先在发送Cookie时先对中文进行编码

使用URL编码来进行编码和解码操纵

使用`URLEncode.encode("要编码的中文","编码所用的字符集")`

```java
String value = "张三";
value = URLEncode.encode(value,"UTF-8");
//在编码后创建Cookie对象
Cookie cookie = new Cookie("username",value);
```

如图所示，在编码后，浏览器所存储的cookie信息就变成了对应的编码信息而不是中文

![image-20250120202825509](./pictures/image-20250120202825509.png)





#### 2.在接收Cookie时再进行解码

使用`URLDecoder.decode("要解码的字符","解码用的字符集")`

```java
//对获取到的cookie信息进行解码
String name = URLDecoder.decode(cookie.getName(),"UTF-8");
```

如下图所示，解码后仍然可以正常显示中文

![image-20250120202852574](./pictures/image-20250120202852574.png)



### Cookie的优缺点

#### 1.优点

Cookie是HTTP协议支持的技术，因此很多平台都能够支持Cookie

#### 2.缺点

移动端APP无法使用Cookie

由于数据是存储在浏览器本地，因此Cookie不安全，且用户可以自己禁用Cookie

Cookie不能跨域



### 这里顺便讲一讲什么是跨域

在实际业务中，最常用的开发模式是前后端分离开发，等到业务上线时，前后端一般部署在不同的服务器上。

跨域分为三个维度：协议、IP/域名、端口，只要两个请求链接中这三个维度有任意一个维度不一样就属于跨域。

而由于前端和后端部署在两台不同的服务器上，因此访问前端页面的请求链接与访问后端服务器的请求链接会不一致，也就是会出现跨域现象。

而Cookie不允许跨域。





## 04-Session-基本使用

Session是服务器会话跟踪技术，前面使用的Cookie是将需要共享的信息存在浏览器端，而这个Session是存在服务器端，相比于Cookie更加安全

Session的使用也会用到Cookie技术，当浏览器第一次发送请求到服务器时，如果请求中没有Session，服务器会自动创建一个Session，这个Session有一个SessionID，服务器会将这个SessionID通过`Set-Cookie`响应头发送给浏览器，浏览器得到SessionID的Cookie后会将这个Cookie存储在本地，下一次发送请求时就会通过Cookie将SessionID发送给服务器。

### 将信息存储到Session中

#### 1.获取Session对象

使用`request.getSession()`函数来获取Session对象

```java
//获取Session对象
HttpSession session = req.getSession();
```



#### 2.存储数据

使用Session对象的`setAttribute("要存储的键","要存储的值")`函数来存储数据

```java
//存储数据
sessiono.setAttribute("username","zs");
```



### 获取Session中的信息

#### 1.获取Session对象

```java
//获取Session对象
HttpSession session = req.getSession();
```



#### 2.获取信息

使用`getAttribute("要获取信息的键")`

```java
//获取信息
Object username = session.getAttribute("username");

```



### Session对象的所有函数

1.`setAttribute`

用于存储键值对信息

```java
session.setAttribute("key","value")
```



2.`getAttribute`

根据key获取信息

```java
session.getAttribute("key");
```



3.`removeAttribute`

根据key删除键值对

```java
session.removeAttribute("key");
```



## 05-Session原理&细节

### Session原理

Session是基于Cookie的，服务器是如何保证每次获取的Session对象都是同一个呢？

#### 第一次创建Session对象时

实际上，在服务器中，每次创建一个Session对象的时候，服务器就会给这个Session对象指定一个id，并通过在响应中添加set-cookie响应头来告知这个id

如下图所示

![image-20250120214051929](./pictures/image-20250120214051929.png)



#### 后面再次创建对象时

浏览器在知道服务器发来的Session对象的id后，就会在请求标头中添加`cookie`属性，用于告知服务器应该访问那个Session对象，如果服务器找不到这个对象就会创建一个，然后将id赋给这个新创建的对象

如下图所示，浏览器的请求头中有`cookie`属性

![image-20250120214419013](./pictures/image-20250120214419013.png)

通过上面所说的这个机制，服务器就能准确知道究竟要访问哪个Session对象



### Session细节

#### Session钝化和活化

Session在服务器正常关闭重启时不会消失，原因如下

##### 1.Session钝化

当服务器正常关闭的时候，tomcat会将Session文件自动存入服务器的硬盘中

如下图所示，`SESSIONS.ser`文件就是tomcat存储的Session文件

![image-20250121204226721](./pictures/image-20250121204226721.png)



##### 2.Session活化

当服务器重新启动时，会中文件中加载Session文件，并将前面存储的`SESSIONS.ser`文件删除



通过这样一个机制，服务器中的Session信息就不会因为服务器的重启而消失

##### 3.浏览器关闭对Session的影响

浏览器关闭再启动访问服务器时，其产生的是两个会话，因此生成的Session不是同一个

如下图所示，第二次访问是在关闭浏览器重启后进行的访问，两个Session的地址不一样，所以不是同一个Session

![image-20250121205309459](./pictures/image-20250121205309459.png)



####  Session的销毁

Session销毁有两种方式

##### 1.通过配置销毁时间销毁

默认情况下Session会在30分钟后自动销毁，这是tomcat服务器自己的配置

我们也可以在`web.xml`文件中自己配置销毁时间

```xml
<session-config>
	<session-timeout>40</session-timeout>
</session-config>
```

如下图所示，这样配置Session将在40分钟后销毁

![image-20250121205751247](./pictures/image-20250121205751247.png)



##### 2.使用Session的`invalidate()`函数来销毁

```java
//使用Session的函数invalidate来销毁
session.invalidate();
```

如下图所示示例

![image-20250121205941080](./pictures/image-20250121205941080.png)



此时我们访问服务器会发生如下报错，因为Session已经被销毁了

![image-20250121210018410](./pictures/image-20250121210018410.png)



### Session的优缺点

#### 1.优点

Session是存储在服务器的，因此更加安全



#### 2.缺点

由于Session的实现依赖于Cookie技术，因此Cookie有的缺点Session也有

服务器集群环境下无法使用Session

在如今的业务中，后端程序是部署在服务器集群上的，也就是说后端程序会被同时部署到多台服务器上，所有用户请求会首先到达一台负载均衡服务器，由这台负载均衡服务器来将请求转发给真正的后端程序部署的服务器。而正是因为这样，我们多次请求访问的服务器可能会不一样，所有Session技术就没有意义了，因为Session如果存了这一次请求的信息到这台服务器，那下一次请求可能就访问不到这台服务器了。

![image-20250320165650151](./pictures/image-20250320165650151.png)





## 令牌技术

### 什么是令牌技术

可以把令牌理解成一个身份凭证，当浏览器访问服务器时，服务器会生成一个令牌，并将其发送给浏览器，浏览器可以将令牌存储在Cookie中，也可以存储在其他地方。当浏览器再次发送请求时，会将令牌一起发送给服务器，服务器收到请求后，首先会校验令牌的合法性，如果合法才允许进行接下来的操作。

目前流行的会话跟踪技术就是令牌技术





### JWT令牌

JWT是JSON Web Token的缩写。

JWT定义了一种简洁的、自包含的格式，用于通信双方以JSON的数据格式安全地传输信息。由于数字签名的存在，这些信息是可靠的。

JWT由3部分组成：

1.header（头），记录令牌类型、签名算法等

2.Payload（有效载荷），携带一些自定义数据等

3.Signature（签名），防止Token被篡改，确保安全性。

前两个部分其实就是JSON格式的数据经过Base64编码得来的。

![image-20250320171157117](./pictures/image-20250320171157117.png)





### 生成JWT令牌

使用JWT令牌首先要导入JWT令牌的依赖

```xml
<!--JWT令牌-->
<dependency>
	<groupId>io.jsonwebtoken</groupId>
	<artifactId>jjwt</artifactId>
	<version>0.9.1</version>
</dependency>
```

编写测试程序

```java
	@Test
	void testJWT(){
		Map<String,Object> map = new HashMap<>();
		map.put("id",1);
		map.put("username","Arthur");
		
		//使用链式编程来生成jwt令牌
		String jwt = Jwts.builder().signWith(SignatureAlgorithm.HS256, "ArthurSkyLoveCoding")        //signWith用于指定签名算法和密钥
				.setClaims(map)            //setClaims用于自定义内容（有效载荷）,内容为键值对，注意Map的第一个泛型为String，第二个泛型为Object
				.setExpiration(new Date(System.currentTimeMillis() + 3600 * 1000))		//setExpiration用于指定令牌过期时间，参数为Date类型的时间
				.compact();					//compact以字符串的形式返回生成的JWT令牌
		System.out.println(jwt);

	}
```

生成的JWT令牌

```
eyJhbGciOiJIUzI1NiJ9.eyJpZCI6MSwiZXhwIjoxNzQyNDY2NTgwLCJ1c2VybmFtZSI6IkFydGh1ciJ9.8UsPr7KnmAt6kzZRGasfZoCgkX-DlqTl6Odeu2dy-fU
```

![image-20250320173145887](./pictures/image-20250320173145887.png)

我们可以将这个令牌放到官网去解析一下看看结果是什么，可以发现解析出来的信息就是我们定义的信息

![image-20250320173234370](./pictures/image-20250320173234370.png)



### 解析JWT令牌

```java
@Test
void testParserJWT(){
   //解析JWT令牌
   Claims claims = Jwts.parser()
         .setSigningKey("ArthurSkyLoveCoding")        //setSigningKey用于给出解析密钥
         //parseClaimsJws用于传入要解析的JWT令牌，注意这个方法是parseClaimsJws，不是parseClaimsJwt，注意最后一个字母
         .parseClaimsJws("eyJhbGciOiJIUzI1NiJ9.eyJpZCI6MSwiZXhwIjoxNzQyNDY2NTgwLCJ1c2VybmFtZSI6IkFydGh1ciJ9.8UsPr7KnmAt6kzZRGasfZoCgkX-DlqTl6Odeu2dy-fU")
         .getBody();//getBody用于获取解析后的结果，会返回一个Claims类型的数据

   System.out.println(claims);
}
```

解析结果

![image-20250320174044491](./pictures/image-20250320174044491.png)

如果我们随便修改一下令牌，解析就会报错

![image-20250320174134699](./pictures/image-20250320174134699.png)

如果令牌过期，会出现以下错误，可以看到令牌的过期时间以及现在的时间

![image-20250320174243386](./pictures/image-20250320174243386.png)





### 令牌技术的优缺点

#### 1.优点

令牌不强制存储在Cookie中，所以它支持PC端、移动端

解决集群环境下的认证问题

可以减轻服务器端的存储压力



#### 2.缺点

需要自己实现



### 其他会话跟踪技术

这部分内容是后续补充内容

除了上面讲的cookie和session技术以外，还有其他会话跟踪技术

#### 1.地址重写

地址重写也叫URL重写，该方法是将会话标识作为URL参数的一部分。

但这种方法会导致URL较长，且需要对所有链接进行重写

#### 2.隐藏域

在表单中使用hidden类型的input字段保存数据，然后随表单提交传递会话信息。

这种方式实现简单，用户无感知。

但仅适用于表单交互场景





## 11-案例-验证码-展示&校验

### 如何实现验证码功能

使用工具类`CheckCodeUtil`

工具类如下

```java
package com.example.util;

import javax.imageio.ImageIO;
import java.awt.*;
import java.awt.geom.AffineTransform;
import java.awt.image.BufferedImage;
import java.io.*;
import java.util.Arrays;
import java.util.Random;

/**
 * 生成验证码工具类
 */
public class CheckCodeUtil {

    public static final String VERIFY_CODES = "123456789ABCDEFGHIJKLMNOPQRSTUVWXYZ";
    private static Random random = new Random();

//    public static void main (String[] args) throws IOException {
//        OutputStream fos = new FileOutputStream("D:\\code\\Idea_project\\JSPExample\\src\\main\\webapp\\imgs\\a.jpg");
//        String checkCode = CheckCodeUtil.outputVerifyImage(100,50,fos,4);
//        System.out.println(checkCode);
//
//    }

    /**
     * 输出随机验证码图片流,并返回验证码值（一般传入输出流，响应response页面端，Web项目用的较多）
     *
     * @param width
     * @param height
     * @param os
     * @param verifySize
     * @return
     * @throws IOException
     */
    public static String outputVerifyImage(int width, int height, OutputStream os, int verifySize) throws IOException {
        String verifyCode = generateVerifyCode(verifySize);
        outputImage(width, height, os, verifyCode);
        return verifyCode;
    }

    /**
     * 使用系统默认字符源生成验证码
     *
     * @param verifySize 验证码长度
     * @return
     */
    public static String generateVerifyCode(int verifySize) {
        return generateVerifyCode(verifySize, VERIFY_CODES);
    }

    /**
     * 使用指定源生成验证码
     *
     * @param verifySize 验证码长度
     * @param sources    验证码字符源
     * @return
     */
    public static String generateVerifyCode(int verifySize, String sources) {
        // 未设定展示源的字码，赋默认值大写字母+数字
        if (sources == null || sources.length() == 0) {
            sources = VERIFY_CODES;
        }
        int codesLen = sources.length();
        Random rand = new Random(System.currentTimeMillis());
        StringBuilder verifyCode = new StringBuilder(verifySize);
        for (int i = 0; i < verifySize; i++) {
            verifyCode.append(sources.charAt(rand.nextInt(codesLen - 1)));
        }
        return verifyCode.toString();
    }

    /**
     * 生成随机验证码文件,并返回验证码值 (生成图片形式，用的较少)
     *
     * @param w
     * @param h
     * @param outputFile
     * @param verifySize
     * @return
     * @throws IOException
     */
    public static String outputVerifyImage(int w, int h, File outputFile, int verifySize) throws IOException {
        String verifyCode = generateVerifyCode(verifySize);
        outputImage(w, h, outputFile, verifyCode);
        return verifyCode;
    }



    /**
     * 生成指定验证码图像文件
     *
     * @param w
     * @param h
     * @param outputFile
     * @param code
     * @throws IOException
     */
    public static void outputImage(int w, int h, File outputFile, String code) throws IOException {
        if (outputFile == null) {
            return;
        }
        File dir = outputFile.getParentFile();
        //文件不存在
        if (!dir.exists()) {
            //创建
            dir.mkdirs();
        }
        try {
            outputFile.createNewFile();
            FileOutputStream fos = new FileOutputStream(outputFile);
            outputImage(w, h, fos, code);
            fos.close();
        } catch (IOException e) {
            throw e;
        }
    }

    /**
     * 输出指定验证码图片流
     *
     * @param w
     * @param h
     * @param os
     * @param code
     * @throws IOException
     */
    public static void outputImage(int w, int h, OutputStream os, String code) throws IOException {
        int verifySize = code.length();
        BufferedImage image = new BufferedImage(w, h, BufferedImage.TYPE_INT_RGB);
        Random rand = new Random();
        Graphics2D g2 = image.createGraphics();
        g2.setRenderingHint(RenderingHints.KEY_ANTIALIASING, RenderingHints.VALUE_ANTIALIAS_ON);

        // 创建颜色集合，使用java.awt包下的类
        Color[] colors = new Color[5];
        Color[] colorSpaces = new Color[]{Color.WHITE, Color.CYAN,
                Color.GRAY, Color.LIGHT_GRAY, Color.MAGENTA, Color.ORANGE,
                Color.PINK, Color.YELLOW};
        float[] fractions = new float[colors.length];
        for (int i = 0; i < colors.length; i++) {
            colors[i] = colorSpaces[rand.nextInt(colorSpaces.length)];
            fractions[i] = rand.nextFloat();
        }
        Arrays.sort(fractions);
        // 设置边框色
        g2.setColor(Color.GRAY);
        g2.fillRect(0, 0, w, h);

        Color c = getRandColor(200, 250);
        // 设置背景色
        g2.setColor(c);
        g2.fillRect(0, 2, w, h - 4);

        // 绘制干扰线
        Random random = new Random();
        // 设置线条的颜色
        g2.setColor(getRandColor(160, 200));
        for (int i = 0; i < 20; i++) {
            int x = random.nextInt(w - 1);
            int y = random.nextInt(h - 1);
            int xl = random.nextInt(6) + 1;
            int yl = random.nextInt(12) + 1;
            g2.drawLine(x, y, x + xl + 40, y + yl + 20);
        }

        // 添加噪点
        // 噪声率
        float yawpRate = 0.05f;
        int area = (int) (yawpRate * w * h);
        for (int i = 0; i < area; i++) {
            int x = random.nextInt(w);
            int y = random.nextInt(h);
            // 获取随机颜色
            int rgb = getRandomIntColor();
            image.setRGB(x, y, rgb);
        }
        // 添加图片扭曲
        shear(g2, w, h, c);

        g2.setColor(getRandColor(100, 160));
        int fontSize = h - 4;
        Font font = new Font("Algerian", Font.ITALIC, fontSize);
        g2.setFont(font);
        char[] chars = code.toCharArray();
        for (int i = 0; i < verifySize; i++) {
            AffineTransform affine = new AffineTransform();
            affine.setToRotation(Math.PI / 4 * rand.nextDouble() * (rand.nextBoolean() ? 1 : -1), (w / verifySize) * i + fontSize / 2, h / 2);
            g2.setTransform(affine);
            g2.drawChars(chars, i, 1, ((w - 10) / verifySize) * i + 5, h / 2 + fontSize / 2 - 10);
        }

        g2.dispose();
        ImageIO.write(image, "jpg", os);
    }

    /**
     * 随机颜色
     *
     * @param fc
     * @param bc
     * @return
     */
    private static Color getRandColor(int fc, int bc) {
        if (fc > 255) {
            fc = 255;
        }
        if (bc > 255) {
            bc = 255;
        }
        int r = fc + random.nextInt(bc - fc);
        int g = fc + random.nextInt(bc - fc);
        int b = fc + random.nextInt(bc - fc);
        return new Color(r, g, b);
    }

    private static int getRandomIntColor() {
        int[] rgb = getRandomRgb();
        int color = 0;
        for (int c : rgb) {
            color = color << 8;
            color = color | c;
        }
        return color;
    }

    private static int[] getRandomRgb() {
        int[] rgb = new int[3];
        for (int i = 0; i < 3; i++) {
            rgb[i] = random.nextInt(255);
        }
        return rgb;
    }

    private static void shear(Graphics g, int w1, int h1, Color color) {
        shearX(g, w1, h1, color);
        shearY(g, w1, h1, color);
    }

    private static void shearX(Graphics g, int w1, int h1, Color color) {

        int period = random.nextInt(2);

        boolean borderGap = true;
        int frames = 1;
        int phase = random.nextInt(2);

        for (int i = 0; i < h1; i++) {
            double d = (double) (period >> 1)
                    * Math.sin((double) i / (double) period
                    + (6.2831853071795862D * (double) phase)
                    / (double) frames);
            g.copyArea(0, i, w1, 1, (int) d, 0);
            if (borderGap) {
                g.setColor(color);
                g.drawLine((int) d, i, 0, i);
                g.drawLine((int) d + w1, i, w1, i);
            }
        }

    }

    private static void shearY(Graphics g, int w1, int h1, Color color) {

        int period = random.nextInt(40) + 10; // 50;

        boolean borderGap = true;
        int frames = 20;
        int phase = 7;
        for (int i = 0; i < w1; i++) {
            double d = (double) (period >> 1)
                    * Math.sin((double) i / (double) period
                    + (6.2831853071795862D * (double) phase)
                    / (double) frames);
            g.copyArea(i, 0, 1, h1, 0, (int) d);
            if (borderGap) {
                g.setColor(color);
                g.drawLine(i, (int) d, i, 0);
                g.drawLine(i, (int) d + h1, i, h1);
            }

        }

    }
}


```

使用该工具类直接调用其中的`outputVerifyImage`函数，参数定义为，`width`图片长度，`height`图片高度，`os`图片文件输出流，`verifySize`验证码长度

使用示例如下

```java
//创建文件输出流
OutputStream os = new FileOutputStream("图片输出的路径");
//调用工具类的函数
String checkCode = CheckCodeUtil.outputVerifyImage(100,50,fos,4);
System.out.println(checkCode);
```

执行后会得到如下结果

![image-20250206140121253](./pictures/image-20250206140121253.png)

生成的图片如下

![a](./pictures/a.jpg)



### 如何在Web服务中使用验证码

只需要在调用工具类函数生成验证码的时候修改以下输出流就行，改成ServletOutputStream

如下示例

```java
//创建ServletOutputStream
ServletOutputStream os = resp.getOutputStream();
//调用生成验证码的工具类函数
CheckCodeUtil.outputVerifyImage(100,50,os,4);
```

此外，还需要在前端页面中设置图片的路径

如下是案例中前端验证码部分的代码，设置的图片路径是调用工具类函数的Servlet，输出流会将图片直接输出到页面上

```jsp
      <tr>
        <td>验证码</td>
        <td class="inputs">
          <input name="checkCode" type="text" id="checkCode">
          <img id="checkCodeImg" src="/JSPExample_war/checkCodeServlet">
          <a href="#" id="changeImg">看不清？</a>
        </td>
      </tr>
```

### 如何实现点击更换验证码图片

只需要在点击时重新设置一下图片路径即可

```jsp
<script>
document.getElementById("changeImg").onclick = function (){
    document.getElementById("checkCodeImg").src = "/JSPExample_war/checkCodeServlet?"+ new Date().getMilliseconds();
  }
</script>  
```

注意，路径不能修改成和原来一样,如下所示

因为浏览器会缓存图片，如果路径一样，就算重新设置，图片也不会改变，因此要在路径后面加上时间，这样一来路径就是唯一的，每次设置路径浏览器都会发出请求然后修改图片

```jsp
<script>
document.getElementById("changeImg").onclick = function (){
    document.getElementById("checkCodeImg").src = "/JSPExample_war/checkCodeServlet?"+ new Date().getMilliseconds();
  }
</script>  
```



### 如何校验验证码

校验验证码，即对比生成的验证码和用户输入的验证码

利用Session来校验验证码，首先在生成验证码的时候将生成的验证码存放在Session中

如下所示

```java
        ServletOutputStream os = resp.getOutputStream();
        String checkCode = CheckCodeUtil.outputVerifyImage(100,50,os,4);
        System.out.println(checkCode);

        HttpSession session = req.getSession();
        session.setAttribute("checkCode",checkCode);
```



然后在校验验证码的时候从Session中取出验证码，再从请求中取出用户输入的验证码，将两者进行对比

```java
		//校验验证码
        HttpSession session = req.getSession();
        String checkCode = (String) session.getAttribute("checkCode");
        System.out.println(checkCode);

        //获取用户填写的验证码
        String checkCode1 = req.getParameter("checkCode");

        //对比验证码,这里忽略大小写比较
        if(!checkCode.equalsIgnoreCase(checkCode1)){
            //验证码不一致时不允许注册
            req.setAttribute("register_msg","验证码错误");
            req.getRequestDispatcher("/register.jsp").forward(req,resp);
            return;
        }
		/..验证码通过时的后续代码../
	
```



# 过滤技术（Fileter&Interceptor）

## 01-Filter-概述&快速入门&执行流程

### Filter概述

Filter过滤器是JavaWeb三大组件（Servlet，Filter，Listener）之一

Filter可以将对资源的请求拦截下来，进行统一的处理

利用Filter可以完成一些通用的操作，比如权限控制、统一编码处理

### Filter过滤器快速入门

#### 1.定义一个类，实现Filter接口，重写接口函数

使用过滤器要实现Filter接口并重写函数

Filter接口主要有三个函数

1).init初始化函数

初始化方法，当Web服务器启动，创建该过滤器对象时会调用，只会调用一次

2).doFilter

拦截到请求时，会调用该方法，可以执行多次

3).destroy销毁函数

销毁方法，当服务器关闭时调用，只会调用一次



这里补充一点，在Filter接口中，init和destroy方法都是默认方法，也就是说可以不重写这两个方法

Filter接口的源码如下图所示

![image-20250320195907411](./pictures/image-20250320195907411.png)

#### 2.配置Filter要拦截的资源的路径

使用`@WebFilter`注解来配置要拦截的路径，要注意的是，由于Filter组件是JavaEE的三大组件，而不是Springboot提供的组件，因此如果要在springboot的项目中使用Filter组件，还需要在springboot类中使用`@ServletComponentScan`注解，表示开启支持Servlet组件功能

如下图所示，与Servlet不同，Servlet配置路径配置的是资源访问路径，而Filter配置的是要拦截的路径，下图中`/*`这个路径表示拦截所有资源

![image-20250206161731160](./pictures/image-20250206161731160.png)

在未设置拦截器之前访问index.jsp时可以直接访问

![image-20250206162029003](./pictures/image-20250206162029003.png)

而设置了拦截路径后，访问index.jsp会出现空白页面，即访问被拦截了

![image-20250206162116703](./pictures/image-20250206162116703.png)



利用这个功能可以控制资源访问，如只允许登录后才能访问资源，如果没有登录则拦截并跳回登录页面



下面是一个Filter类的具体示例，这部分是后续补充的，与上面的例子是两个不同的例子，补充的这个例子使用的是springboot框架

```java
import jakarta.servlet.*;
import jakarta.servlet.annotation.WebFilter;

import java.io.IOException;

//使用@WebFilter注解来配置拦截路径
@WebFilter("/*")
//Filter接口不要导错包了，如果是springboot 2.x.x版本就选择javax的包，如果是3.x.x就选择jakarta的包
public class FilterDemo implements Filter {

    @Override
    public void init(FilterConfig filterConfig) throws ServletException {
        System.out.println("init,初始化方法执行了");
    }

    @Override
    public void doFilter(ServletRequest servletRequest, ServletResponse servletResponse, FilterChain filterChain) throws IOException, ServletException {
        System.out.println("拦截到了请求");
    }

    @Override
    public void destroy() {
        System.out.println("destroy,销毁方法执行了");
    }
}
```

不要忘了在springboot的启动类中开启对Servlet组件的支持

![image-20250320194806133](./pictures/image-20250320194806133.png)

```java
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.boot.web.servlet.ServletComponentScan;

@ServletComponentScan     //开启Servlet组件支持功能
@SpringBootApplication
public class TliasWebManagementApplication {

   public static void main(String[] args) {
      SpringApplication.run(TliasWebManagementApplication.class, args);
   }

}
```

创建好过滤器后，可以启动服务尝试访问一下，可以发现访问页面没有加载任何数据，但是可以看到过滤器的doFilter方法执行了，这是正常的，因为请求被过滤器拦截后还需要放行，然后请求才能继续执行，才能成功获得数据

![image-20250320194943041](./pictures/image-20250320194943041.png)





#### 3.在doFilter函数中输出拦截信息并放行

既然拦截了下来，要是不放行，就无法访问执行的资源

通过在doFilter函数中调用`filterChain.doFilter(request,response)`来放行，以前是使用`chain.doFilter(request,response)`,现在改成了`filterChain.doFilter`

如下示例

```java
    @Override
    public void doFilter(ServletRequest servletRequest, ServletResponse servletResponse, FilterChain filterChain) throws IOException, ServletException {
        System.out.println("Filter被执行了");
        filterChain.doFilter(servletRequest, servletResponse);
    }
```

放行后就能正常访问资源，并可以在控制台中看到，Filter正常执行了

![image-20250206162842266](./pictures/image-20250206162842266.png)





下面的内容是后续补充的，例子与上面的例子不同，补充的例子使用的是springboot框架

放行

```java
@Override
public void doFilter(ServletRequest servletRequest, ServletResponse servletResponse, FilterChain filterChain) throws IOException, ServletException {
    System.out.println("拦截到了请求");
    //放行
    filterChain.doFilter(servletRequest,servletResponse);
}
```

这是再用浏览器重新发送请求就能正常看到数据了

![image-20250320195733103](./pictures/image-20250320195733103.png)



### Filter的执行流程

在doFilter函数中，除了上面提到的放行代码`filterChain.doFilter(request,response)`外，还有放行前的逻辑代码和放行后的逻辑代码

而Filter的执行流程为，先执行放行前的逻辑代码，然后被放行后接着执行对应访问资源的代码，当访问资源的代码执行完毕后，程序会回到Filter中，最后再执行放行后的逻辑代码

如下图所示

![image-20250206164738768](./pictures/image-20250206164738768.png)

![image-20250206164750239](./pictures/image-20250206164750239.png)

在doFilter函数中添加测试代码

```java
    @Override
    public void doFilter(ServletRequest servletRequest, ServletResponse servletResponse, FilterChain filterChain) throws IOException, ServletException {
        System.out.println("1.放行前的逻辑代码");
        filterChain.doFilter(servletRequest, servletResponse);
        System.out.println("3.放行后的逻辑代码");
    }
```

执行结果如下

![image-20250206185153954](./pictures/image-20250206185153954.png)





## 02-Filter-拦截路径配置&过滤器链

### Filter拦截路径配置

配置Filter拦截路径有四种方式

#### 1.拦截具体的资源

```java
@WebFilter("/index.jsp")			//资源名为index.jsp的资源会被拦截
```



#### 2.目录拦截

```java
@WebFilter("/user/*")				//user目录下的资源会被全部拦截
```



#### 3.后缀名拦截

```java
@WebFilter("/*.jsp")				//jsp文件会被拦截
```



#### 4.全部拦截

```java
@WebFilter("/*")					//所有文件会被拦截
```



### 过滤器链

一个Web应用可以配置多个过滤器，这多个过滤器被称为过滤器链

其执行流程如下图所示，先执行过滤器1的放行前的逻辑，然后放行，放行后来到过滤器2，就执行过滤器2的放行前逻辑，如果后面还有过滤器就接着执行放行前逻辑，如果没有，就直接执行资源代码，执行完资源代码后，从后往前执行放行后的逻辑，即先执行过滤器2的放行后逻辑再执行过滤器1的放行后逻辑

过滤器的执行顺序默认是按照过滤器的全限定名称来排序的

![image-20250206190343955](./pictures/image-20250206190343955.png)



## 03-Filter-案例-登录验证

### 1.验证用户是否登录

实现验证用户是否登录，如果没有登录，则不允许访问资源，并自动跳转到登录页面，如果登录了，则放行，允许访问资源

在前面jsp的案例中，已经实现了用户登录功能，代码如下

```java
package com.example.web;

import com.example.pojo.User;
import com.example.service.UserService;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.*;
import java.io.IOException;

@WebServlet("/loginServlet")
public class LoginServlet extends HttpServlet {
    private UserService userService = new UserService();
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        String username = req.getParameter("username");
        String password = req.getParameter("password");

        //获取用户信息
        User user = userService.login(username,password);

        if(user != null){
            //登录成功

            //判断用户是否勾选记住用户
            String if_remember = req.getParameter("remember");

            //如果用户勾选了记住用户，则发送cookie
            if("1".equals(if_remember)){
                Cookie usernameCookie = new Cookie("username",username);
                Cookie passwordCookie = new Cookie("password",password);

                usernameCookie.setMaxAge(60*60*24*7);
                passwordCookie.setMaxAge(60*60*24*7);
                resp.addCookie(usernameCookie);
                resp.addCookie(passwordCookie);


            }

            //将用户信息保存到Session中
            HttpSession session = req.getSession();
            session.setAttribute("user",user);

            String contextPath = req.getContextPath();
            System.out.println(contextPath);
            resp.sendRedirect(contextPath+"/selectAllServlet");
        }else {
            //登录失败
            //存储信息到request域中
            req.setAttribute("login_msg","用户名或密码错误");

            //将请求转发到login.jsp
            req.getRequestDispatcher("/login.jsp").forward(req,resp);
        }
    }

    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        this.doGet(req, resp);
    }
}

```

用户登录时会将用户登录信息放入Session中，所以接下来要实现的登录验证功能就要从Session中取出用户登录信息，以此来判断用户是否已经登录

登录验证过滤器代码如下

```java
package com.example.web.Filter;


import javax.servlet.*;
import javax.servlet.annotation.*;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpSession;
import java.io.IOException;

/**
 * 登录过滤器
 * */
@WebFilter("/*")
public class LoginFilter implements Filter {
    public void init(FilterConfig config) throws ServletException {
    }

    public void destroy() {
    }

    @Override
    public void doFilter(ServletRequest request, ServletResponse response, FilterChain chain) throws ServletException, IOException {
        //1.首先将ServletRequest强转为HttpServletRequest
        HttpServletRequest req = (HttpServletRequest) request;

        //2.然后从请求中获取Session
        HttpSession session = req.getSession();

        //3.获取用户登录信息
        Object user = session.getAttribute("user");

        //4.判断用户是否已经登录
        if(user!=null){
            //用户已经登录，放行
            chain.doFilter(request,response);
        }else {
            //非法请求，跳转到登录页面
            req.setAttribute("login_msg","请登陆后再访问");
            req.getRequestDispatcher("/login.jsp").forward(request,response);
        }
    }
}

```



这样实现后还没完，因为单单这样会出现下面的问题

登录页面的样式不见了，这是因为过滤器也将登录页面的图片、css等资源也拦截了，因此我们要将与登录注册相关的资源全部放行

![image-20250207114524041](./pictures/image-20250207114524041.png)



### 2.放行所有登录注册相关资源

在登录过滤器中添加判断登录注册资源路径的代码

```java
        //首先定义所有登录注册资源的访问路径
        String[] urls = {"/login.jsp","/register.jsp","/loginServlet","/registerServlet","/css/","/imgs/"};

        //获取请求路径
        String requestURL = req.getRequestURL().toString();

        //判断访问的路径是否包含登录注册资源的访问路径
        //循环判断
        for(String u :urls){
            if(requestURL.contains(u)){
                //如果访问路径包含登录注册相关资源的路径，则放行
                chain.doFilter(request,response);
                return;
            }
        }
```

这样一来，跳转到登录页面就能正常显示了

![image-20250207115356359](./pictures/image-20250207115356359.png)



## Interceptor拦截器

### 什么是Interceptor

Interceptor是一种动态拦截方法调用的机制，类似于过滤器。

Interceptor是Spring框架提供的，用于动态拦截控制器方法的执行。

其作用是拦截请求，在指定的方法调用前后，根据业务需要执行预先设定的代码





### Interceptor快速入门

使用Interceptor拦截器有以下步骤

1.定义一个拦截器类，实现HandlerInterceptor接口，并重写方法

```java
import jakarta.servlet.http.HttpServletRequest;
import jakarta.servlet.http.HttpServletResponse;
import org.springframework.stereotype.Component;
import org.springframework.web.servlet.HandlerInterceptor;
import org.springframework.web.servlet.ModelAndView;

//将拦截器交给IOC容器管理，方便注册拦截器时使用
@Component
public class InterceptorDemo implements HandlerInterceptor {
    @Override
    public boolean preHandle(HttpServletRequest request, HttpServletResponse response, Object handler) throws Exception {
        //preHandle方法是在目标资源执行之前执行的。如果本方法返回true，则放行请求；如果本方法返回false，则不放行。
        System.out.println("preHandle...");
        return true;        //放行
    }

    @Override
    public void postHandle(HttpServletRequest request, HttpServletResponse response, Object handler, ModelAndView modelAndView) throws Exception {
        //postHandle方法是在目标资源执行完毕后执行的。
        System.out.println("postHandle...");
    }

    @Override
    public void afterCompletion(HttpServletRequest request, HttpServletResponse response, Object handler, Exception ex) throws Exception {
        //afterCompletion方法是在视图渲染完毕后执行的，最后执行
        System.out.println("afterCompletion...");
    }
}
```



2.注册拦截器。需要在一个配置类中注册拦截器，使用`@Configuration`注解将该类声明为配置类，该配置类需要实现WebMvcConfigurer接口，并重写addInterceptors方法，该方法用于注册拦截器

```java
import com.tlias.interceptor.InterceptorDemo;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.context.annotation.Configuration;
import org.springframework.web.servlet.config.annotation.InterceptorRegistry;
import org.springframework.web.servlet.config.annotation.WebMvcConfigurer;

//声明此类为配置类
@Configuration
public class WebConfig implements WebMvcConfigurer {

    //通过依赖注入快速使用拦截器对象
    @Autowired
    private InterceptorDemo interceptorDemo;

    @Override
    public void addInterceptors(InterceptorRegistry registry) {
        /*addInterceptor方法用于注册拦截器，addPathPatterns用于配置拦截路径
        注意拦截器拦截所有的路径与过滤器不同，过滤器是"/*"，而拦截器是"/**"    */
        registry.addInterceptor(interceptorDemo).addPathPatterns("/**");
    }
}
```

此时我们发送一个请求，可以清除地看到拦截器中三个方法的运行情况

![image-20250320213452349](./pictures/image-20250320213452349.png)



### 配置拦截路径

使用`addPathPatterns`来配置要拦截的路径，使用`excludePathPatterns`来配置不需要拦截的路径，这两个方法的参数是String类型的可变数据类型，也就是说可以传入多个String参数。

Interceptor拦截器的拦截路径有下面几种写法

![image-20250320214147700](./pictures/image-20250320214147700.png)

下面的配置表示拦截所有路径，除了登录请求/login。

```java
@Override
public void addInterceptors(InterceptorRegistry registry) {
    /*addInterceptor方法用于注册拦截器，addPathPatterns用于配置拦截路径
    注意拦截器拦截所有的路径与过滤器不同，过滤器是"/*"，而拦截器是"/**"    */
    registry.addInterceptor(interceptorDemo).addPathPatterns("/**").excludePathPatterns("/login");
}
```



### 拦截器的执行流程

拦截器是spring提供的，所以它只会拦截访问spring环境下资源的路径。而过滤器会拦截所有资源

当过滤器Filter和拦截器Interceptor同时存在时，过滤器会先拦截请求，然后执行过滤器放行前的逻辑，接着请求会经过`DispatcherServlet`，由于Tomcat服务器是支持Servlet的轻量级服务器，因此Tomcat无法直接识别spring的Controller类，所以需要`DespatcherServlet`来转发请求请求。请求经过`DispatcherServlet`后，会被拦截器Interceptor拦截，前面讲了，拦截器只会拦截访问spring环境下资源的请求，经过拦截器时，拦截器会执行preHandle方法，最后请求才会来到Controller类，执行Controller的逻辑，待访问资源的执行完毕后，请求会再按原路返回。

执行流程如下图所示

![image-20250320215415307](./pictures/image-20250320215415307.png)

### 拦截器（Interceptor）与过滤器（Filter）的区别

![image-20250320215506209](./pictures/image-20250320215506209.png)





# Listener

## 04-Listener

### Listener概述

Listener是JavaWeb的三大组件之一

Listener是用来监听application、session、request三个对象的创建、销毁以及往其中添加或修改删除属性时自动执行代码的组件

JavaWeb提供了8个监听器，如下图所示

![image-20250207120711069](./pictures/image-20250207120711069.png)

### Listener快速入门

这里以使用ServletContext监听器为例

#### 1.首先创建一个类并实现相关接口

这里要实现ServletContextListener接口



#### 2.为Listener类添加WebListener注解

完整的代码如下

```java
package com.example.web.Listener;

import javax.servlet.ServletContextEvent;
import javax.servlet.ServletContextListener;
import javax.servlet.annotation.WebListener;

@WebListener
public class ListenerDemo implements ServletContextListener {
    @Override
    public void contextInitialized(ServletContextEvent servletContextEvent) {
        //一般用于加载相关资源
        System.out.println("监听器的初始化函数执行了");
    }

    @Override
    public void contextDestroyed(ServletContextEvent servletContextEvent) {

    }
}

```

如下图所示，web应用加载时，监听器就监听到了，并成功执行了初始化函数

![image-20250207121324496](./pictures/image-20250207121324496.png)



# AJAX

## 01-AJAX-概述

AJAX的全称是Asynchronous JavaScript And Xml，意为异步JavaScript和Xml

### AJAX作用

#### 1.与服务器进行数据交换，实现前后端分离

通过AJAX可以向服务器发送请求获取服务器响应的数据，以前不使用AJAX的方式的时候是用JSP来实现的，将数据放在请求域中，再通过JSP的EL表达式来获取数据，但使用JSP方式无法实现前后端分离，因为JSP是服务器管理，需要后端统一编写。而使用AJAX可以解决这个问题

#### 2.实现异步交互

异步交互是指可以在不重新加载整个页面的情况下，与服务器交换数据并更行部分页面。例如：搜索联想，用户名校验等

搜索联想

![image-20250207133241215](./pictures/image-20250207133241215.png)



 

## 02-AJAX-快速入门

实现一个AJAX应用分为前端部分和后端部分

### 后端部分编写

后端部分只需要实现一个AjaxServlet类（实际上还是一个继承自HttpServlet的类），并使用response输出字符串

代码如下所示

```java
package com.example.web;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebListener;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.io.IOException;

@WebServlet("/ajaxServlet")
public class AjaxDemo extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {

        //响应数据
        resp.getWriter().write("hello Ajax~~");
    }

    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        this.doGet(req, resp);
    }
}

```



### 前端部分编写

前端部分编写有三步

#### 1.创建XMLHttpRequest核心对象

XMLHttpRequest是AJAX的核心

```html
<!--创建一个核心对象-->
var xhttp = new XMLHttpRequest;
```



#### 2.向服务器发送请求

向服务器发送数据要使用函数`open`和`send`函数

其中open函数的参数含义如下图所示

![image-20250207212627820](./pictures/image-20250207212627820.png)

```html
xhttp.open("请求方法","请求路径","异步还是同步");
xhttp.send();
```





#### 3.获取服务器响应的数据

获取服务器响应的数据是通过`XMLHttpRequest`的`onreadystatechange`属性

`onreadystatechange`属性是根据readyState来判断执行时机的，每当readyState发生变化时，就会执行一次`onreadystatechange`属性定义的函数

会涉及到三个属性

`readyState` 属性存留 XMLHttpRequest 的状态。

`onreadystatechange` 属性定义当 readyState 发生变化时执行的函数。

`status` 属性和 `statusText` 属性存有 XMLHttpRequest 对象的状态。

这些属性的状态代码以及含义如下图所示

![image-20250207213930621](./pictures/image-20250207213930621.png)

其中当readyState为4，status为200时代表请求已经完成，响应就绪

```html
    xhttp.onreadystatechange = function () {
        if(xhttp.readyState == 4 && xhttp.status == 200){
            alert(xhttp.responseText);
        }
    }
```

前端部分总代码如下

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>

</body>
<script>
    //1.创建核心对象
    var xhttp = new XMLHttpRequest();

    //2.向服务器发送请求，第三个参数默认为true，代表异步
    xhttp.open("GET","http://localhost/Ajax_Demo/ajaxServlet");
    xhttp.send();

    //3.获取服务器的数据
    xhttp.onreadystatechange = function () {
        if(xhttp.readyState == 4 && xhttp.status == 200){
            alert(xhttp.responseText);
        }
    }
</script>
</html>
```



## 03-案例-验证用户是否存在

验证注册时用户名是否已经存在，在光标移出输入框时进行验证，如果存在则给出提示，不存在则清除提示消息，这是一个异步请求的案例

实现逻辑为，通过请求将用户名发送给后端服务器，服务器验证完成后将结果通过response给出，前端再使用AJAX来获取后端结果，根据结果来给出不同的提示

### 后端部分

```java
package com.example.web;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.io.IOException;

@WebServlet("/selectUserServlet")
public class SelectUserServlet extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        //1.获取用户名
        String username = req.getParameter("username");

        //2.校验用户名是否存在，这里模拟验证，直接返回假数据
        String flag = "false";

        //3.响应结果
        resp.getWriter().write(flag);
    }

    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        this.doGet(req, resp);
    }
}
```



### 前端部分

```html
<script>

    //1.获取对象,一旦光标移出输入框就执行函数
    document.getElementById("username").onblur = function (){
        //2.发送ajax请求
        var xhttp = new XMLHttpRequest();

        xhttp.open("GET","http://localhost/Ajax_Demo/selectUserServlet",true);
        xhttp.send();

        xhttp.onreadystatechange = function () {
            if(this.readyState == 4 && this.status == 200){
                if(xhttp.responseText == "true"){
                    //说明用户名存在，给出提示信息
                    document.getElementById("username_err").style.display = "";
                }else{
                    //说明用户名不存在，允许创建，清除提示信息
                    document.getElementById("username_err").style.display = "none";

                }
            }
        }
    }


</script>
```





## 04-Axios-基本使用&请求方式别名

### Axios的使用

Axios是对AJAX的封装，通过使用Axios就不必写过多的代码就可以简单地使用AJAX

#### 1.引入Axios的js文件

在webapp下新建一个`js`文件夹用于存放js文件

将Axios的js文件放如`js`文件夹

然后引入，引入js文件用如下代码

```html
<script src="js/axios-0.18.0.js"></script>
```

![image-20250209111705865](./pictures/image-20250209111705865.png)



#### 2.通过Axios使用get方法

通过Axios使用get方法的代码示例如下

其中`method`属性就是指请求方法，`url`指请求的地址

```html
<script>
  axios({
    method:"get",
    url:"http://localhost/Ajax_Demo/ajaxServlet?username=zhangsan"
  }).then(function (resp){
    alert(resp.data);
  })
</script>
```



#### 3.通过Axios使用post方法

与get方法基本相同，不同的地方是get方法的参数放在请求路径的后面，而post方法的参数放在`data`属性中

```html
<script>
  axios({
    method:"post",
    url:"http://localhost/Ajax_Demo/ajaxServlet",
    data:"username=zhangsan"  
  }).then(function (resp){
    alert(resp.data);
  })
</script>
```



### Axios请求方式别名

Axios提供了请求方式的别名，通过使用别名可以用更少的代码来发送请求

#### 1.get方法别名

简化的get方法中只需要填写要请求的url地址作为参数即可

```html
<script>
	axios.get("http://localhost/Ajax_Demo/axiosServlet?username=zhangsan").then(function (resp){
      alert(resp.data);
  })
</script>  
```



#### 2.post方法别名

简化的post方法中除了要填写url地址，还要填写请求参数

```html
<script>
  axios.post("http://localhost/Ajax_Demo/axiosServlet","username=zhangsan").then(function (resp){
      alert(resp.data);
  })
</script>
```



## 05-JSON-概述和基本语法

### JSON概述

JSON是JavaScript Object Notation的缩写，以为JavaScript对象表示法

其格式与JavaScript的对象格式非常像，如下图所示

JavaScript对象的键可以不加双引号，但JSON必须要加双引号

![image-20250209115410417](./pictures/image-20250209115410417.png)



### JSON基础语法

语法定义

```html
<script>
   var 变量名={
	"key1":value1,
	"key2":value2,
	....
	}
</script>
```

其中value的值可以是数字、字符串、逻辑值、数组（放在中括号中）、对象（放在花括号中）、null

示例如下

```html
<script>
var json={
	"name":"zhangsan",
	"age":23,
	"addr":["北京","上海","深圳"]
}
</script>
```

可通过`json.key`的形式来访问json对象里的数据

示例如下

```html
json.name			
```



## 06-JSON数据和Java对象转换

JSON数据和java对象的转换可以直接使用fastjson

使用fastjson提供的函数即可完成转换

### 1.导入fastjson包

fastjson包的坐标如下

```xml
    <dependency>
      <groupId>com.alibaba</groupId>
      <artifactId>fastjson</artifactId>
      <version>1.2.62</version>
    </dependency>
```



### 2.Java对象转JSON对象

使用函数`JSON.toJSONString`

示例如下

```java
        //1.Java对象转JSON
        User user = new User();
        user.setId("1");
        user.setUsername("zhangsan");
        user.setPassword("123");
        String json =JSON.toJSONString(user);
        System.out.println(json);
```

转换结果如下

![image-20250209121628158](./pictures/image-20250209121628158.png)

### 3.JSON对象转Java对象

使用函数`JSON.parseObject("JSON字符串",要转换成的对象.class)`

示例如下

```java
        //2.JSON对象转Java对象
        User u = JSON.parseObject(json,User.class);
        System.out.println(u);
```

结果如下，这里注意一下，要先在User对象中定义toString方法，不然打印出来的是User对象的地址，而不是图中的结果

![image-20250209122515603](./pictures/image-20250209122515603.png)





# 前端工程化

## Day03-04.前端工程化-环境准备

### Vue-cli：Vue脚手架

Vue-cli是Vue官方提供的一个脚手架，用于快速生成一个Vue的项目模板。

使用Vue脚手架有下面几个功能：

![image-20250310084607305](./pictures/image-20250310084607305.png)





### 如何使用Vue脚手架

#### 1.安装nodejs

浏览器搜索nodejs下载安装包

![image-20250310085012559](./pictures/image-20250310085012559.png)

安装好后，使用命令行检查nodejs是否安装成功

![image-20250310085136378](./pictures/image-20250310085136378.png)





#### 2.配置npm的全局安装路径

将npm的全局安装路径改为nodejs的安装路径，使用如下命令

```cmd
npm config set prefix "nodejs安装路径"
```



![image-20250310085457128](./pictures/image-20250310085457128.png)

#### 3.切换npm的淘宝镜像

切换npm的镜像用于加速文件下载，使用下面的命令切换华为云的镜像

```cmd
npm config set registry https://mirrors.huaweicloud.com/repository/npm/
```

使用下面的指令查看当前镜像源，可以检查是否切换成功

```cmd
npm get registry
```



#### 4.安装Vue-cli

使用以下命令来安装Vue-cli

```cmd
 npm install -g @vue/cli
```

![image-20250310090704546](./pictures/image-20250310090704546.png)

使用以下命令来检查vue脚手架是否安装成功

```cmd
vue --version
```

![image-20250310091208989](./pictures/image-20250310091208989.png)





## Day03-05.前端工程化-Vue项目

### 创建Vue项目

有两种方式创建vue项目

1.命令行方式

在命令行中直接输入

```cmd
vue create vue-project01
```



2.图形化界面创建

从希望vue项目安装到的路径进入命令行，输入以下命令

```cmd
vue ui
```

![image-20250310091749797](./pictures/image-20250310091749797.png)

选择创建新项目

![image-20250310091828361](./pictures/image-20250310091828361.png)

输入项目名，选择包管理器

![image-20250310091943673](./pictures/image-20250310091943673.png)



选择项目要用到的功能，比如：Router

![image-20250310092030973](./pictures/image-20250310092030973.png)

选择vue版本以及语法校验模式

![image-20250310092120519](./pictures/image-20250310092120519.png)

创建完成，如果创建失败可能是没有用管理员权限启动命令行

![image-20250310092506406](./pictures/image-20250310092506406.png)

可以看到文件目录的情况

![image-20250310092537541](./pictures/image-20250310092537541.png)





### Vue项目的目录结构

![image-20250310092835339](./pictures/image-20250310092835339.png)

node_modules存放的是整个项目的依赖包

public存放的是项目的静态文件

src是项目的源代码

还有两个比较重要的文件：package.json、vue.config.js

package.json里面是项目开发所需的模块，版本信息等

vue.config.js里面是vue配置的文件，如：代理、端口的配置等



src下的文件目录

![image-20250310093211618](./pictures/image-20250310093211618.png)

assets存放的是静态资源

components存放的是可重用组件

router存放的是路由配置

views存放的是视图组件，也就是页面

App.vue是入口组件（根组件）

main.js是入口js文件



### Vue项目-启动

启动Vue项目有两种方式

1.使用vscode提供的图像化界面

直接运行serve脚本

![image-20250310093905166](./pictures/image-20250310093905166.png)

如果没看到脚本要先在资源管理器中打开

![image-20250310093829846](./pictures/image-20250310093829846.png)





2.直接在项目文件夹中打开命令行，使用如下命令

```cmd
npm run serve
```





###  修改vue项目的端口号

在vue.config.js文件中添加如下代码

```js
devServer:{
    //配置端口号
    port:9090,
  }
```

![image-20250310094242271](./pictures/image-20250310094242271.png)





## Day03-06.前端工程化-Vue项目开发流程

### Vue页面是如何显示出来的

当我们创建好一个Vue项目后，可以启动该项目，然后可以看到这样一个界面，接下来我们就解析一下这个界面是如何来的，以此来认识Vue是如何运作的

![image-20250310142546682](./pictures/image-20250310142546682.png)

这个页面实际上是vue工程创建时的一个默认页面`index.html`，可以在创建的工程文件中找到，在public文件夹下，其代码如下

```java
<!DOCTYPE html>
<html lang="">
  <head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width,initial-scale=1.0">
    <link rel="icon" href="<%= BASE_URL %>favicon.ico">
    <title><%= htmlWebpackPlugin.options.title %></title>
  </head>
  <body>
    <noscript>
      <strong>We're sorry but <%= htmlWebpackPlugin.options.title %> doesn't work properly without JavaScript enabled. Please enable it to continue.</strong>
    </noscript>
    <!--这里用于挂载Vue的对象-->
    <div id="app"></div>
    <!-- built files will be auto injected -->
  </body>
</html>

```

这个`index.html`默认引入了一个`.js`文件`main.js`，也就是Vue项目的入口JS文件，其代码及代码解释如下

```js
//import表示引入，与其对应的是export，只有先被export的组件才能被import
import Vue from 'vue'
//引入了App.vue这个组件，并命名为App，后面要使用这个组件就可以直接用App这个名字
import App from './App.vue'
import router from './router'

Vue.config.productionTip = false

//创建了一个vue对象
/*实际上等同于如下创建对象的写法
new Vue({
	el:"app",
	......
})
*/
new Vue({
  router,
  //下面这行代码表示会用render这个函数来创建一个虚拟DOM对象，这个DOM对象最终什么样由引入的App.vue这个组件决定，也就是说是在App.vue这个组件中定义的
  render: h => h(App)
}).$mount('#app')		//mount表示会将这个vue对象挂载到id为app的元素上，可以在index.html找到这个元素

```

接下来再看看`main.js`引入的`App.vue`组件。以`.vue`结尾的文件被称为组件，组件由三个部分组成：

1.`<template>`，模板部分，用于定义HTML代码

2.`<script>`，js代码，用于控制模板部分的数据来源和行为，模板部分引入了什么数据或者函数都要在这里先定义

3.`<style>`，负责css样式部分

项目自动生成的`App.vue`的代码如下，挂载到`index.html`中id为app的元素上的就是下面这些东西。

```vue
<template>
  <div id="app">
    <nav>
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </nav>
    <router-view/>
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}
</style>

```

修改这些代码，就可以修改页面，可以尝试一下修改`App.vue`代码

```vue
<template>
  <div>
    <!-- 在模板部分定义HTML代码 -->
     <!-- 通过插值表达式来使用js中定义的数据 -->
    <h1>{{ message }}</h1>
  </div>
</template>

<script>
//组件的js部分先按下面的模板来写，视频这部分讲的依托，啥都没听懂，完全不知道为什么要这样写

//只有先用export导出，才能在其他地方被import引入
export default{
  data(){
    return{
      //在这里面定义数据
      message:"Hello Vue"
    }
  },
  methods:{
    //在这里面定义方法
  }
}

</script>

<style>
/* 将所有样式删除 */
</style>

```



# Element

## Day03-07.Element-快速入门

### 如何使用Element

#### 1.为项目安装ElementUI组件库

直接在vscode终端控制台中输入下面的命令

```cmd
npm i element-ui -S
```

如果报错，可能是权限问题，可以将vscode的启动设置为以管理员的身份启动，如下图，在vscode启动程序的属性里找到兼容性设置

![image-20250310151107565](./pictures/image-20250310151107565.png)

执行完命令后，在node_modules文件夹中找到如下文件就说明安装成功

![image-20250310151148551](./pictures/image-20250310151148551.png)



#### 2.在`main.js`文件中引入ElementUI组件库

```js
import Vue from 'vue'
import App from './App.vue'
import router from './router'

//以下是ElementUI的引入代码
import ElementUI from 'element-ui';
import 'element-ui/lib/theme-chalk/index.css';

//以下是ElementUI的引入代码
Vue.use(ElementUI);

Vue.config.productionTip = false


new Vue({
  router,
  render: h => h(App)
}).$mount('#app')

```



#### 3.访问官网寻找组件

在官网中找到要用的组件，然后复制代码到项目中，接着进行相应的调整

定义ElementView组件

```vue
<template>
    <el-row>
        <el-button>默认按钮</el-button>
        <el-button type="primary">主要按钮</el-button>
        <el-button type="success">成功按钮</el-button>
        <el-button type="info">信息按钮</el-button>
        <el-button type="warning">警告按钮</el-button>
        <el-button type="danger">危险按钮</el-button>
    </el-row>

</template>

<script>
export default {

}
</script>

<style></style>
```

在App.vue中使用ElementView组件

```vue
<template>
  <div>   
    <h1>{{ message }}</h1>
    <!-- 使用ElementView组件 -->
    <ElementView></ElementView>    
  </div>
</template>

<script>
//导入ElementView组件
import ElementView from './views/element/ElementView.vue';
export default{
  //要导出引入的组件，才能在template中使用
  components:{ElementView},
  data(){
    return{
      message:"Hello Vue"
    }
  },
  methods:{
  }
}

</script>

<style>

</style>

```





## Day03-15.vue路由

### vue路由

vue路由是URL中hash(#号)与组件之间的对应关系。如下图，URL中有一个`#`号，当`#`号后面发生变化时，就会去找到对应的页面显示出来

![image-20250310155117962](./pictures/image-20250310155117962.png)



vue官方提供了一个路由插件：Vue Router，其由以下三部分组成

#### 1.VueRouter

路由器类，根据路由请求在路由视图中动态渲染组件。比如有下面的路由表

![image-20250310155617621](./pictures/image-20250310155617621.png)

当URL`#`号后面的路径为/user时，路由器就会渲染UserView组件，其他组件同理



#### 2.`<router-link>`

请求链接组件，浏览器会将其解析为超链接，使用如下

```vue
<template>
	<div>
        <router-link to="/emp">员工管理</router-link>
    </div>
</template>
```





#### 3.`router-view`

动态视图组件，用于渲染展示请求路径对应的组件

比如当浏览器请求的路径为`/user`时，UserView组件就会被渲染到这个标签所在的位置





### 如何使用vue路由

#### 1.在项目中引入vue路由

在控制台输入如下命令

```cmd
npm install vue-router@3.5.1
```

在创建项目是也可以选择路由功能，如果选择了就不需要安装了



#### 2.定义路由表

在项目文件夹中找到router文件夹，在这个文件夹下有一个index.js文件，在该文件中定义路由表



#### 3.引入路由表

在`main.js`文件中引入路由表

```js
import Vue from 'vue'
import App from './App.vue'
//创建项目时已经自动引入了，如果没有自动引入自己添加以下也行
import router from './router'

//以下是ElementUI的引入代码
import ElementUI from 'element-ui';
import 'element-ui/lib/theme-chalk/index.css';

//以下是ElementUI的引入代码
Vue.use(ElementUI);

Vue.config.productionTip = false


new Vue({
  //使用引入的路由表
  router,
  render: h => h(App)
}).$mount('#app')
```



#### 4.定义`<router-link>`和`<router-view>`

```vue
<template>
  <div>
    <!-- router-link会被解析成超链接 -->
    <router-link to="/element1">路径1</router-link>   
    <router-link to="/element2">路径2</router-link>
    <!--路径请求的组件会被渲染到下面标签的位置-->
    <router-view></router-view>
  </div>
</template>

<script>
export default{
  data(){
    return{
      message:"Hello Vue"
    }
  },
  methods:{
  }
}

</script>

<style>

</style>
```





## Day03-16.打包部署

### vue项目打包

使用build脚本即可将vue项目打包

![image-20250310162517228](./pictures/image-20250310162517228.png)

打包完成后会在项目文件夹下生成一个dist文件夹，该文件夹部署到服务器上即可完成项目部署

![image-20250310162637552](./pictures/image-20250310162637552.png)





### vue项目部署

部署vue项目需要使用到Nginx，Nginx是一款轻量级Web服务器。

#### 1.下载安装Nginx

如何下载安装就不说了，直接讲一下安装后的文件目录，安装后的Nginx有如下文件

![image-20250310163049261](./pictures/image-20250310163049261.png)

conf用于存放Nginx的配置文件

html用于存放静态资源文件

logs是日志文件目录

temp是临时文件目录



#### 2.将打包文件放入html文件夹下

![image-20250310163453759](./pictures/image-20250310163453759.png)

注意了，上图中那样放是错的，那样放的话访问时会显示403 forbid错误

要把dist文件夹下的具体文件放在html下

![image-20250310164037113](./pictures/image-20250310164037113.png)

#### 3.双击`nginx.exe`启动服务器

默认端口号为80。

双击后发现没有页面跳出来，可以查看任务管理器，看看有没有nginx进程

![image-20250310163708625](./pictures/image-20250310163708625.png)



#### 4.输入地址访问前端页面

输入localhost:80

![image-20250310164051702](./pictures/image-20250310164051702.png)



#### 5.nginx启动失败

如果双击`nginx.exe`后没有在任务管理器中看到nginx进程，可以查看日志文件，日志文件在nginx安装目录下的log文件夹里面

我这里通过查看error日志文件，发现最后面几行有乱码问题，这是因为我当前这个nginx放在了包含中文的目录下了，乱码就是中文路径的乱码，所以启动失败就是因为nginx放在中文路径下了，将nginx的路径改到全英文路径即可启动成功

![image-20250319084102182](./pictures/image-20250319084102182.png)





## Day10-01.案例-准备工作

### 开发规范-Restful

Restful是一种开发规范，在传统开发风格中，每一种url对应的都是一种操作，而使用Restful，同一个url根据请求的不同，操作也会不同，如图中的例子，对于localhost:8080/users/1这个url，有两种请求结果，一种是get方式：查询id为1的用户，另一种是delete方式：删除id为1的用户信息

![image-20250318225010178](./pictures/image-20250318225010178.png)



## springboot+mybatis开发案例

### 部门管理-查询

这里新知识点是@xxxMapping注解，如@GetMapping，这个注解是@RequestMapping的衍生注解。

还有一个使用logback的知识点

以下代码并不是该业务功能的正确实现，而是为了演示新知识点

```java
import com.tlias.pojo.Result;
import lombok.extern.slf4j.Slf4j;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RequestMethod;
import org.springframework.web.bind.annotation.RestController;


//lombok提供了@Slf4j注解，使用了这个注解后，就不需要自己定义Logger常量对象了，可以直接使用logback的方法来打印日志
@Slf4j
@RestController
public class DeptController {

    //获取所有部门信息
    //使用RequestMapping来指定访问路径，同时可以使用method属性来限定访问方式
    //@RequestMapping(value = "/depts",method = RequestMethod.GET)
    //使用RequestMapping来限定访问方法可能会比较繁琐，因此RequestMapping提供了衍生注解xxxMapping,xxx代表访问方式
    //如：GetMapping  在该注解中指定访问路径，则该访问路径只允许get请求方式
    @GetMapping("/depts")
    public Result list(){
        log.info("查询部门信息");
        return Result.success();
    }
}
```



下面才是业务的正确实现

Controller层

```java
import com.tlias.pojo.Dept;
import com.tlias.pojo.Result;
import com.tlias.service.DeptService;
import lombok.extern.slf4j.Slf4j;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

import java.util.List;


//lombok提供了@Slf4j注解，使用了这个注解后，就不需要自己定义Logger常量对象了，可以直接使用logback的方法来打印日志
@Slf4j
@RestController
public class DeptController {

    @Autowired
    private DeptService deptService;

    //获取所有部门信息
    @GetMapping("/depts")
    public Result list(){
        log.info("查询部门信息");
        List<Dept> list = deptService.list();
        return Result.success(list);
    }
}
```

Service接口

```java
import com.tlias.pojo.Dept;
import java.util.List;

public interface DeptService {

    /**
     * 查询所有部门信息
     * @return
     */
    public List<Dept> list();
}
```

Service层实现

```java
import com.tlias.mapper.DeptMapper;
import com.tlias.pojo.Dept;
import com.tlias.service.DeptService;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Service;

import java.util.List;


@Service
public class DeptServiceImp implements DeptService {

    @Autowired
    private DeptMapper deptMapper;

    @Override
    public List<Dept> list() {

        return deptMapper.list();
    }
}
```

Mapper层

```java
import com.tlias.pojo.Dept;
import org.apache.ibatis.annotations.Mapper;
import org.apache.ibatis.annotations.Select;

import java.util.List;

@Mapper
public interface DeptMapper {


    /**
     * 查询所有部门信息
     * @return
     */
    @Select("select * from dept;")
    List<Dept> list();
}
```





### 部门管理-删除

Controller层

```java
import com.tlias.pojo.Dept;
import com.tlias.pojo.Result;
import com.tlias.service.DeptService;
import lombok.extern.slf4j.Slf4j;
import org.apache.ibatis.annotations.Delete;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.web.bind.annotation.DeleteMapping;
import org.springframework.web.bind.annotation.PathVariable;
import org.springframework.web.bind.annotation.RestController;

@Slf4j
@RestController
public class DeptController {
    
    @Autowired
    private DeptService deptService;


    /**
     * 根据id删除部门
     */
    @DeleteMapping("/depts/{id}")		//路径参数，使用@PathVariable注解
    public Result deleteById(@PathVariable int id){
        log.info("根据id删除部门"+id);
        deptService.deleteById(id);
        return Result.success();
    }
}
```

Service接口

```java
import com.tlias.pojo.Dept;
import java.util.List;

public interface DeptService {

    /**
     * 根据id删除部门
     */
    void deleteById(int id);
}
```

Service层实现

```java
import com.tlias.mapper.DeptMapper;
import com.tlias.pojo.Dept;
import com.tlias.service.DeptService;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Service;

import java.util.List;


@Service
public class DeptServiceImp implements DeptService {

    @Autowired
    private DeptMapper deptMapper;

    @Override
    public void deleteById(int id) {
        deptMapper.deleteById(id);
    }
}
```

Mapper层接口

```java
import com.tlias.pojo.Dept;
import org.apache.ibatis.annotations.Delete;
import org.apache.ibatis.annotations.Mapper;
import org.apache.ibatis.annotations.Select;

import java.util.List;

@Mapper
public interface DeptMapper {

    /**
     * 根据id删除部门
     */
    @Delete("delete from dept where id = #{id}")
    void deleteById(int id);
}
```





### 部门管理-新增

Contorller层

```java
import com.tlias.pojo.Dept;
import com.tlias.pojo.Result;
import com.tlias.service.DeptService;
import lombok.extern.slf4j.Slf4j;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.web.bind.annotation.*;

import java.util.List;

@Slf4j
@RestController
public class DeptController {

    @Autowired
    private DeptService deptService;

    /**
     * 新增部门
     * @param dept
     * @return
     */
    @PostMapping("/depts")
    public Result insert(@RequestBody Dept dept){
        //{}是占位符，运行时第二个参数会替换{}
        log.info("新增部门{}",dept.getName());
        deptService.insert(dept);
        return Result.success();
    }
}
```

Service接口

```java
import com.tlias.pojo.Dept;
import java.util.List;

public interface DeptService {

    /**
     * 新增部门
     * @param dept
     */
    void insert(Dept dept);
}
```

Service实现类

```java
import com.tlias.mapper.DeptMapper;
import com.tlias.pojo.Dept;
import com.tlias.service.DeptService;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Service;

import java.time.LocalDateTime;
import java.util.List;


@Service
public class DeptServiceImp implements DeptService {

    @Autowired
    private DeptMapper deptMapper;

    @Override
    public void insert(Dept dept) {
        //完善插入数据
        dept.setCreateTime(LocalDateTime.now());
        dept.setUpdateTime(LocalDateTime.now());
        deptMapper.insert(dept);
    }
}
```

Mapper接口

```java
import com.tlias.pojo.Dept;
import org.apache.ibatis.annotations.Delete;
import org.apache.ibatis.annotations.Insert;
import org.apache.ibatis.annotations.Mapper;
import org.apache.ibatis.annotations.Select;

import java.util.List;

@Mapper
public interface DeptMapper {
    /**
     * 添加部门
     * @param dept
     */
    @Insert("insert into dept(name, create_time, update_time) values(#{name},#{createTime},#{updateTime}) ")
    void insert(Dept dept);
}
```



### 部门管理-增删改整合

下面代码是部门管理的增删改三个功能整合起来的Controller类

```java
import com.tlias.pojo.Dept;
import com.tlias.pojo.Result;
import com.tlias.service.DeptService;
import lombok.extern.slf4j.Slf4j;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.web.bind.annotation.*;

import java.util.List;


//lombok提供了@Slf4j注解，使用了这个注解后，就不需要自己定义Logger常量对象了，可以直接使用logback的方法来打印日志
@Slf4j
@RestController
public class DeptController {

    @Autowired
    private DeptService deptService;

    //获取所有部门信息
    @GetMapping("/depts")
    public Result list(){
        log.info("查询部门信息");
        List<Dept> list = deptService.list();
        return Result.success(list);
    }


    /**
     * 根据id删除部门
     */
    @DeleteMapping("/depts/{id}")
    public Result deleteById(@PathVariable int id){
        log.info("根据id删除部门"+id);
        deptService.deleteById(id);
        return Result.success();
    }

    /**
     * 新增部门
     * @param dept
     * @return
     */
    @PostMapping("/depts")
    public Result insert(@RequestBody Dept dept){
        log.info("新增部门{}",dept.getName());
        deptService.insert(dept);
        return Result.success();
    }
}
```

可以发现上面的请求路径中有重复的部分：`/depts`，可以将这重复的部分提取出来放在`@RequestMapping`注解上，此时请求的真正路径是`@RequestMapping`注解的value属性+各个方法上的`@xxxMapping`注解的value属性，提取后如下

```java
import com.tlias.pojo.Dept;
import com.tlias.pojo.Result;
import com.tlias.service.DeptService;
import lombok.extern.slf4j.Slf4j;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.web.bind.annotation.*;

import java.util.List;


//lombok提供了@Slf4j注解，使用了这个注解后，就不需要自己定义Logger常量对象了，可以直接使用logback的方法来打印日志
@Slf4j
@RestController
//将重复路径提取到@RequestMapping注解上
@RequestMapping("/depts")
public class DeptController {

    @Autowired
    private DeptService deptService;

    //获取所有部门信息
    @GetMapping
    public Result list(){
        log.info("查询部门信息");
        List<Dept> list = deptService.list();
        return Result.success(list);
    }


    /**
     * 根据id删除部门
     */
    @DeleteMapping("/{id}")
    public Result deleteById(@PathVariable int id){
        log.info("根据id删除部门"+id);
        deptService.deleteById(id);
        return Result.success();
    }

    /**
     * 新增部门
     * @param dept
     * @return
     */
    @PostMapping
    public Result insert(@RequestBody Dept dept){
        log.info("新增部门{}",dept.getName());
        deptService.insert(dept);
        return Result.success();
    }
}
```



### 部门管理-修改

修改部门信息需要实现两个接口，一个是修改部门信息，另一个是根据id查询部门信息(用于数据回显)。

Controller层

```java
import com.tlias.pojo.Dept;
import com.tlias.pojo.Result;
import com.tlias.service.DeptService;
import lombok.extern.slf4j.Slf4j;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.web.bind.annotation.*;

import java.util.List;

@Slf4j
@RestController
//将重复路径提取到@RequestMapping注解上
@RequestMapping("/depts")
public class DeptController {

    @Autowired
    private DeptService deptService;

    /**
     * 修改部门信息
     * @param dept
     * @return
     */
    @PutMapping
    public Result update(@RequestBody Dept dept){
        log.info("修改部门,id为{}",dept.getId());
        deptService.update(dept);
        return Result.success();
    }


    /**
     * 根据id查询部门信息,用于数据回显
     * @return
     */
    @GetMapping("/{id}")		//这里注意{}不要写成了#{}
    public Result selectById(@PathVariable int id){
        return Result.success(deptService.selectById(id));
    }

}
```

Service接口

```java
import com.tlias.pojo.Dept;
import java.util.List;

public interface DeptService {

    /**
     * 修改部门信息
     * @param dept
     */
    void update(Dept dept);


    /**
     * 根据id查询部门信息
     * @param id
     * @return
     */
    Dept selectById(int id);
}
```

Service实现类

```java
import com.tlias.mapper.DeptMapper;
import com.tlias.pojo.Dept;
import com.tlias.service.DeptService;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Service;

import java.time.LocalDateTime;
import java.util.List;


@Service
public class DeptServiceImp implements DeptService {

    @Autowired
    private DeptMapper deptMapper;
    
    /**
     * 修改部门信息
     * @param dept
     */
    @Override
    public void update(Dept dept) {
        //处理修改信息
        dept.setUpdateTime(LocalDateTime.now());
        deptMapper.update(dept);

    }

    /**
     * 根据id查询部门信息
     * @param id
     * @return
     */
    @Override
    public Dept selectById(int id) {
        return deptMapper.selectById(id);
    }
}
```

Mapper接口

```java
import com.tlias.pojo.Dept;
import org.apache.ibatis.annotations.Delete;
import org.apache.ibatis.annotations.Insert;
import org.apache.ibatis.annotations.Mapper;
import org.apache.ibatis.annotations.Select;

import java.util.List;

@Mapper
public interface DeptMapper {


    /**
     * 修改部门,这个功能用了动态sql
     * @param dept
     */
    void update(Dept dept);


    /**
     * 根据id查询部门
     * @param id
     * @return
     */
    @Select("select * from dept where id = #{id}")
    Dept selectById(int id);
}
```

xml映射文件

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE mapper
        PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
        "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
<mapper namespace="com.tlias.mapper.DeptMapper">
    <update id="update">
        <!--修改部门信息-->
        update dept
        <set>
            <if test="name!=null">
                name=#{name},
            </if>
            <if test="updateTime!=null">
                update_time=#{updateTime}
            </if>
        </set>
        where id=#{id}
    </update>
</mapper>
```





### 员工管理-分页查询 

#### 分页查询的思路

前端传递的参数有page页码，pageSize每页数据条数。

后端返回的数据要有total总记录数，rows当前页查询到的所有信息

所以后端返回的数据需要用一个实体类来封装，实体类属性包括total、rows

```java
import lombok.AllArgsConstructor;
import lombok.Data;
import lombok.NoArgsConstructor;

import java.util.List;

@Data
@AllArgsConstructor
@NoArgsConstructor
public class PageBean {
    long total;
    List rows; 
}
```



#### 实现分页查询（原始方法）

Controller层

```java
import com.tlias.pojo.PageBean;
import com.tlias.pojo.Result;
import com.tlias.service.EmpService;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestParam;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class EmpController {

    @Autowired
    private EmpService empService;

    /**
     * 分页查询员工信息
     * @param page
     * @param pageSize
     * @return
     */
    @GetMapping("/emps")
    public Result page(@RequestParam(defaultValue = "1") Integer page,@RequestParam(defaultValue = "10") Integer pageSize){
        PageBean pageBean =  empService.page(page,pageSize);
        return Result.success(pageBean);
    }
}
```

Service接口

```java
import com.tlias.pojo.PageBean;

public interface EmpService {
    /**
     * 分页查询员工信息
     * @param page
     * @param pageSize
     * @return
     */
    PageBean page(Integer page,Integer pageSize);

}
```

Service层实现

```java
import com.tlias.mapper.EmpMapper;
import com.tlias.pojo.Emp;
import com.tlias.pojo.PageBean;
import com.tlias.service.EmpService;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Service;

import java.util.List;

@Service
public class EmpServiceImp implements EmpService {

    @Autowired
    private EmpMapper empMapper;

    @Override
    public PageBean page(Integer page, Integer pageSize) {
        //1.查询员工信息总条数
        Integer total = empMapper.count();
        //2.分页查询员工信息
        Integer start = (page - 1) * pageSize;
        List<Emp> rows = empMapper.page(start,pageSize);
        //3.封装结果
        return new PageBean(total,rows);
    }
}
```

Mapper层接口

```java
import com.tlias.pojo.Emp;
import org.apache.ibatis.annotations.Mapper;
import org.apache.ibatis.annotations.Select;

import java.util.List;

@Mapper
public interface EmpMapper {

    /**
     * 查询员工信息的总条数
     * @return
     */
    @Select("select count(*) from emp")
    Integer count();

    /**
     * 分页查询员工信息
     * @param start
     * @param pageSize
     * @return
     */
    @Select("select * from emp limit #{start},#{pageSize}")
    List<Emp> page(Integer start,Integer pageSize);
}
```



#### 实现分页查询（pageHelper插件）

使用pageHelper会自动完成分页查询的操作，使用pageHelper后我们不需要再手动获取总条数和每页的信息，而是直接执行`select * from 表名`，剩下的pageHelper会帮我们自动执行。

使用pageHelper插件来优化上面的代码

首先要导入pageHelper的依赖

```xml
<dependency>
	<groupId>com.github.pagehelper</groupId>
	<artifactId>pagehelper-spring-boot-starter</artifactId>
	<version>1.4.6</version>
</dependency>
```

Controller层不变，只需修改Service层和Mapper层

Service层实现类

```java
import com.github.pagehelper.Page;
import com.github.pagehelper.PageHelper;
import com.tlias.mapper.EmpMapper;
import com.tlias.pojo.Emp;
import com.tlias.pojo.PageBean;
import com.tlias.service.EmpService;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Service;

import java.util.List;

@Service
public class EmpServiceImp implements EmpService {

    @Autowired
    private EmpMapper empMapper;

    @Override
    public PageBean page(Integer page, Integer pageSize) {
        //使用pageHelper实现分页查询
        //1.设置分页参数
        PageHelper.startPage(page,pageSize);

        //2.直接执行查询语句，pageHelper会自动修改sql语句完成查询所有条数，以及分页查询的任务
        List<Emp> list = empMapper.list();

        //3.将List类型强制转换为Page类型，Page类型是pageHelper定义的类型，它继承了ArrayList类，里面封装了分页查询的结果
        Page<Emp> p= (Page<Emp>) list;

        //4.从Page集合中取出分页查询结果，Page提供了getTotal方法用于获取总条数，getResult方法用于获取分页查询结果
        return new PageBean(p.getTotal(),p.getResult());
    }
}
```

Mapper层接口

```java
import com.tlias.pojo.Emp;
import org.apache.ibatis.annotations.Mapper;
import org.apache.ibatis.annotations.Select;

import java.util.List;

@Mapper
public interface EmpMapper {

    /**
     * 查询所有员工信息，使用了pageHelper后，只需要执行查询所有操作就能够实现分页查询的功能
     * @return
     */
    @Select("select * from emp")
    List<Emp> list();
}
```

通过输出mybatis日志，我们可以看到pageHelper具体执行了哪些sql语句，可以发现pageHelper实际上也是执行了原始方法中的sql语句，只是使用pageHelper后不需要我们自己去操作了，方便了很多

![image-20250319152647336](./pictures/image-20250319152647336.png)



### 员工管理-条件分页查询

这个功能是在分页查询的基础上加上条件判断，自己在实现的时候报了很多错，有很多细节需要注意。

Controller层

Controller报错的点有两个：一个是short类型的参数，最好定义成Short包装类，因为如果使用short基本数据类型，该参数就不能为空，如果该参数为空，程序就会出现异常。

另一个是LocalDateTime和LocalDate要注意区分，浏览器传进来的参数只有年月日，就要用LocalDate，并且要用`@DateTimeFormat`注解指定时间格式，我自己实现的时候错用了LocalDateTime，一直找不到报错原因，看了弹幕才发现。

```java
import com.tlias.pojo.PageBean;
import com.tlias.pojo.Result;
import com.tlias.service.EmpService;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.format.annotation.DateTimeFormat;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestParam;
import org.springframework.web.bind.annotation.RestController;

import java.time.LocalDate;

@RestController
public class EmpController {

    @Autowired
    private EmpService empService;

    /**
     * 分页查询员工信息
     *
     * @param page
     * @param pageSize
     * @return
     */
    @GetMapping("/emps")
    public Result page(@RequestParam(defaultValue = "1") Integer page,
                       @RequestParam(defaultValue = "10") Integer pageSize,
                       String name, Short gender,
                       @DateTimeFormat(pattern = "yyyy-MM-dd") LocalDate begin,
                       @DateTimeFormat(pattern = "yyyy-MM-dd") LocalDate end) {
        PageBean pageBean = empService.page(page, pageSize, name, gender, begin, end);
        return Result.success(pageBean);
    }
}
```

Service层接口

```java
import com.tlias.pojo.PageBean;

import java.time.LocalDate;

public interface EmpService {
    /**
     * 分页查询员工信息
     * @param page
     * @param pageSize
     * @return
     */
    PageBean page(Integer page, Integer pageSize, String name,
                  Short gender, LocalDate begin, LocalDate end);
}
```

Service层实现类

```java
import com.github.pagehelper.Page;
import com.github.pagehelper.PageHelper;
import com.tlias.mapper.EmpMapper;
import com.tlias.pojo.Emp;
import com.tlias.pojo.PageBean;
import com.tlias.service.EmpService;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Service;

import java.time.LocalDate;
import java.util.List;

@Service
public class EmpServiceImp implements EmpService {

    @Autowired
    private EmpMapper empMapper;

    @Override
    public PageBean page(Integer page,Integer pageSize, String name,
                         Short gender, LocalDate begin, LocalDate end) {
        PageHelper.startPage(page,pageSize);

        List<Emp> list = empMapper.list(name, gender, begin, end);
        Page<Emp> p = (Page<Emp>) list;
        return new PageBean(p.getTotal(),p.getResult());
    }
}
```

Mapper层接口

```java
import com.tlias.pojo.Emp;
import org.apache.ibatis.annotations.Mapper;
import org.apache.ibatis.annotations.Select;

import java.time.LocalDate;
import java.util.List;

@Mapper
public interface EmpMapper {

    /**
     * 条件查询所有员工信息，使用动态sql
     * @return
     */
    List<Emp> list(String name, Short gender, LocalDate begin, LocalDate end);
}
```

xml映射文件

这里要注意的点是每个条件后面不要加上`,`符号，因为多个条件之间使用and来分割的，而不是用逗号`,`

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE mapper
        PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
        "http://mybatis.org/dtd/mybatis-3-mapper.dtd">

<mapper namespace="com.tlias.mapper.EmpMapper">
    <select id="list" resultType="com.tlias.pojo.Emp">
        select * from emp
        <where>
            <if test="name!=null">
                name like concat('%',#{name},'%')
            </if>
            <if test="gender!=null">
                and gender=#{gender}
            </if>
            <if test="begin!=null and end!=null">
                and entrydate between #{begin} and #{end}
            </if>
        </where>
    </select>
</mapper>
```



### 员工管理-新增员工

Controller层

```java
import com.tlias.pojo.Emp;
import com.tlias.pojo.PageBean;
import com.tlias.pojo.Result;
import com.tlias.service.EmpService;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.format.annotation.DateTimeFormat;
import org.springframework.web.bind.annotation.*;

import java.time.LocalDate;
import java.util.List;

@RestController
@RequestMapping("/emps")
public class EmpController {

    @Autowired
    private EmpService empService;

    @PostMapping
    public Result save(@RequestBody Emp emp){
        empService.save(emp);
        return Result.success();
    }
}
```

Service层接口

```java
import com.tlias.pojo.Emp;
import com.tlias.pojo.PageBean;

import java.time.LocalDate;
import java.util.List;

public interface EmpService {

    /**
     * 添加员工信息
     * @param emp
     */
    void save(Emp emp);
}
```

Service实现类

```java
import com.github.pagehelper.Page;
import com.github.pagehelper.PageHelper;
import com.tlias.mapper.EmpMapper;
import com.tlias.pojo.Emp;
import com.tlias.pojo.PageBean;
import com.tlias.service.EmpService;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Service;

import java.time.LocalDate;
import java.time.LocalDateTime;
import java.util.List;

@Service
public class EmpServiceImp implements EmpService {

    @Autowired
    private EmpMapper empMapper;

    @Override
    public void save(Emp emp) {
        //添加基本信息
        emp.setCreateTime(LocalDateTime.now());
        emp.setUpdateTime(LocalDateTime.now());
        empMapper.insert(emp);
    }
}
```

Mapper层接口

```java
import com.tlias.pojo.Emp;
import org.apache.ibatis.annotations.Insert;
import org.apache.ibatis.annotations.Mapper;
import org.apache.ibatis.annotations.Select;

import java.time.LocalDate;
import java.util.List;

@Mapper
public interface EmpMapper {
    /**
     * 新增员工
     * @param emp
     */
    @Insert("insert into emp(username, name, gender, image, job, entrydate, dept_id, create_time, update_time) " +
            "values( #{username},#{name},#{gender},#{image},#{job},#{entrydate},#{deptId},#{createTime},#{updateTime}) ")
    void insert(Emp emp);
}
```





## 文件上传

文件上传指的是将文件上传至服务器，以供他人进行访问下载等操作。



### 实现文件上传的前端操作

下面是一个实现文件上传的前端例子

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>上传文件</title>
</head>
<body>

    <form action="/upload" method="post" enctype="multipart/form-data">
        姓名: <input type="text" name="username"><br>
        年龄: <input type="text" name="age"><br>
        头像: <input type="file" name="image"><br>
        <input type="submit" value="提交">
    </form>

</body>
</html>
```

实现文件上传前端必须要注意的三个点:

1.方法必须为post

2.enctype必须为"multipart/form-data"

3.有一个file类型的input元素

我们查看请求头可以看到一个类似`boundary=----xxxxxxxx`的东西，这个东西代表分割符，如果将表单的enctype属性设置为`multipart/form-data`，那么表单数据在提交的时候是分为多个部分提交的，每一个表单项就是单独的部分

![image-20250319175831535](./pictures/image-20250319175831535.png)

在查看请求体，可以发现请求体被`boundary=----xxxxxxxx`这个东西分成了3部分，每一个部分都是一个表单项，其中最后一个部分就是上传的文件内容，其中文件内容浏览器进行了包装，因此我们看不到具体文件内容

![image-20250319175944435](./pictures/image-20250319175944435.png)



### 实现文件上传的后端操作

创建一个Controller类来接收文件

```java
import com.tlias.pojo.Result;
import lombok.extern.slf4j.Slf4j;
import org.springframework.web.bind.annotation.PostMapping;
import org.springframework.web.bind.annotation.RestController;
import org.springframework.web.multipart.MultipartFile;

@Slf4j
@RestController
public class UploadController {

    //Springboot提供了MultipartFile类型用于接收文件
    @PostMapping("/upload")
    public Result upload(String username, Integer age, MultipartFile image){
      log.info("参数为:{},{},{}",username,age,image);
      return Result.success();
    }
}
```

通过打断点调试的方式启动服务器，并访问html页面上传文件，此时我们可以看见一个路径

![image-20250319191921598](./pictures/image-20250319191921598.png)

打开路径，可以看见里面有几个文件，这个路径实际上是存放临时文件的路径

![image-20250319192035615](./pictures/image-20250319192035615.png)

我们将这三个文件修改后缀名为txt，可以发现，文件内容就是前端发过来的表单信息，其中有一个是上传的文件，如下图所示

![image-20250319192241158](./pictures/image-20250319192241158.png)

此时我们让程序正常执行完毕，可以发现临时文件夹中的文件消失了，只要本次上传文件的请求响应完毕后，临时文件就会自动被删除。

![image-20250319192349052](./pictures/image-20250319192349052.png)



### 保存上传的文件

上面我们写后端并没有对上传的文件进行存储，接下来我们要实现存储上传文件的功能。

存储上传文件有两种方式：

#### 1.本地存储

##### MultipartFile提供的常用方法

![image-20250319201551189](./pictures/image-20250319201551189.png)

本地存储是将上传的文件直接存储到服务器的磁盘中。

使用MultipartFile提供的`transferTo`方法。

`transferTo`有两种参数，可以用File类型作为参数，也可以直接传入Path路径类型作为参数

我们在存储文件的时候要先获取文件的名字，使用`getOriginalFilename`方法来获取上传文件的文件名，注意不是`getName`方法，`getName`方法是获取表单项名称的。

```java
import com.tlias.pojo.Result;
import lombok.extern.slf4j.Slf4j;
import org.springframework.web.bind.annotation.PostMapping;
import org.springframework.web.bind.annotation.RestController;
import org.springframework.web.multipart.MultipartFile;

import java.io.File;
import java.io.IOException;

@Slf4j
@RestController
public class UploadController {

    //Springboot提供了MultipartFile类型用于接收文件
    @PostMapping("/upload")
    public Result upload(String username, Integer age, MultipartFile image) throws IOException {
        log.info("参数为:{},{},{}", username, age, image);
        //先获取上传文件的名字
        String filename = image.getOriginalFilename();
        //将文件保存到本地磁盘中
        image.transferTo(new File("D:\\pictures\\zzz\\"+filename));

        return Result.success();
    }
}
```



##### 处理重复文件名（UUID）

上面的存储文件方法会带来一个问题，当多个用户上传的文件名一样时，后面上传的文件会覆盖前面上传的文件，为了解决这个问题，我们需要对用户上传的文件的文件名进行处理，有一个方法是使用时间戳，在原本文件名后面加上时间毫秒值。但这里推荐另一种方法，使用UUID（通用唯一识别码），这种识别码的重复概率极低。

我们可以生成几个UUID来看一看，Java工具包提供了生成UUID的工具类`UUID`

```java
@Test
void testUUID(){
   //生成1000个UUID
   for (int i = 0; i < 1000; i++) {
      System.out.println(UUID.randomUUID());
   }
}
```

生成结果如下图，UUID就长这样

![image-20250319195434683](./pictures/image-20250319195434683.png)



下面用UUID来优化上面的保存文件的代码

```java
import com.tlias.pojo.Result;
import lombok.extern.slf4j.Slf4j;
import org.springframework.web.bind.annotation.PostMapping;
import org.springframework.web.bind.annotation.RestController;
import org.springframework.web.multipart.MultipartFile;

import java.io.File;
import java.io.IOException;
import java.util.UUID;

@Slf4j
@RestController
public class UploadController {

    //Springboot提供了MultipartFile类型用于接收文件
    @PostMapping("/upload")
    public Result upload(String username, Integer age, MultipartFile image) throws IOException {
        log.info("参数为:{},{},{}", username, age, image);
        //先获取上传文件的名字
        String originalFilename = image.getOriginalFilename();
        //获取文件的后缀名，用了UUID可不能忘了后缀名哈
        int index = originalFilename.lastIndexOf(".");
        //将UUID与后缀名拼接成新的文件名
        String filename = UUID.randomUUID().toString()+originalFilename.substring(index);
        //使用新文件名将文件保存到本地磁盘中
        image.transferTo(new File("D:\\pictures\\zzz\\"+filename));

        return Result.success();
    }
}
```

此时我们就可以看见上传的文件了，如图，第二个文件就是用新文件名来保存的文件

![image-20250319200005192](./pictures/image-20250319200005192.png)



##### 设置上传文件的大小限制

springboot中，文件上传时，单个文件默认允许最大大小为1M。

如果此时我们上传的文件超过最大大小，浏览器或者后端服务器会报错，视频中演示的是服务器报错，而我这里是浏览器报错，如下图

![image-20250319200834310](./pictures/image-20250319200834310.png)

我们可以在springboot的配置文件中修改上传文件大小限制

```properties
#设置单个上传文件最大为10MB
spring.servlet.multipart.max-file-size=10MB

#设置单次请求的最大上传大小为100MB（一次请求可以上传多个文件）
spring.servlet.multipart.max-request-size=100MB
```

修改完后，重启服务器，我们就能上传大小超过1MB的文件啦，如下图所示，我上传的文件大小是2.41MB

![image-20250319201240962](./pictures/image-20250319201240962.png)



使用本地存储上传文件其实并不是一个很好的选择，本地存储上传文件有下面几个缺点：

1).存储在服务器磁盘中，浏览器无法直接访问

2).占用本地服务器的磁盘空间

3).如果磁盘损毁，文件也会全部丢失。

基于以上几个原因，在实际业务开发中，一般使用下面讲的云服务器（oss-对象存储服务）来存储文件



#### 2.云服务器（OSS-对象存储服务）

##### 开启阿里云oss服务

要使用oss服务，需要先创建Bucket

![image-20250319203754209](./pictures/image-20250319203754209.png)

创建好后，点击右上角头像，获取AccessKey

![image-20250319203928371](./pictures/image-20250319203928371.png)

如果没有AccessKey，就创建一个

![image-20250319204056305](./pictures/image-20250319204056305.png)

接下来就是根据官方提供的SDK，来将项目与oss集成





##### 使用oss服务

找到官方的SDK文档，根据文档来编写代码

![image-20250319205111248](./pictures/image-20250319205111248.png)

使用前要先把AccessKey配置到系统环境变量中，操作如下图所示

![image-20250320112840624](./pictures/image-20250320112840624.png)

我们复制官方的代码，然后进行适当修改

![image-20250319210812934](./pictures/image-20250319210812934.png)

运行后就能在bucket中看到上传的文件

![image-20250319210846922](./pictures/image-20250319210846922.png)

同时oss会为我们上传的每一个文件提供一个url，可以通过这个url来下载文件，也可以将它放在数据库中，然后浏览器就可以通过这个url去找到对应的图片

如下面，我将第一行的头像地址在数据库中改成了oss提供的地址，这样浏览器就根据这个地址成功访问到了bucket中的图片

![image-20250319211059265](./pictures/image-20250319211059265.png)

但是，注意，这个链接是有时间限制的，也就是说过一段时间我们再用这个链接就访问不到了。

要解决这个问题需要将桶的访问权限设置为公共读

![image-20250319213357105](./pictures/image-20250319213357105.png)

这样生成的链接才是可以一直使用的

![image-20250319213421908](./pictures/image-20250319213421908.png)







### 完善新增员工功能（图片上传）

使用oss来存储员工的图片，并将图片访问路径返回

创建一个工具类，专门用来实现将文件上传到oss服务器上的功能，这部分代码是修改自官方SDK提供的示例

```java
import com.aliyun.oss.*;
import com.aliyun.oss.common.auth.CredentialsProviderFactory;
import com.aliyun.oss.common.auth.EnvironmentVariableCredentialsProvider;
import com.aliyun.oss.common.comm.SignVersion;
import com.aliyun.oss.model.PutObjectRequest;
import com.aliyun.oss.model.PutObjectResult;
import org.springframework.stereotype.Component;
import org.springframework.web.multipart.MultipartFile;

import java.io.InputStream;
import java.util.UUID;

@Component
public class AliOSSUtil {

    public String upload(MultipartFile file) throws Exception{
        // Endpoint以华东1（杭州）为例，其它Region请按实际情况填写。
        String endpoint = "https://oss-cn-beijing.aliyuncs.com";
        // 从环境变量中获取访问凭证。运行本代码示例之前，请确保已设置环境变量OSS_ACCESS_KEY_ID和OSS_ACCESS_KEY_SECRET。
        EnvironmentVariableCredentialsProvider credentialsProvider = CredentialsProviderFactory.newEnvironmentVariableCredentialsProvider();
        // 填写Bucket名称，例如examplebucket。
        String bucketName = "javaweb-tlias-case-sky";
        // 填写Object完整路径，完整路径中不能包含Bucket名称，例如exampledir/exampleobject.txt。
        String originalFileName = file.getOriginalFilename();
        int index = originalFileName.lastIndexOf(".");

        String objectName = "pictures/"+ UUID.randomUUID()+originalFileName.substring(index);
        // 填写Bucket所在地域。以华东1（杭州）为例，Region填写为cn-hangzhou。
        String region = "cn-beijing";

        // 创建OSSClient实例。
        ClientBuilderConfiguration clientBuilderConfiguration = new ClientBuilderConfiguration();
        clientBuilderConfiguration.setSignatureVersion(SignVersion.V4);
        OSS ossClient = OSSClientBuilder.create()
                .endpoint(endpoint)
                .credentialsProvider(credentialsProvider)
                .clientConfiguration(clientBuilderConfiguration)
                .region(region)
                .build();

        try {
            InputStream inputStream = file.getInputStream();
            // 创建PutObjectRequest对象。
            PutObjectRequest putObjectRequest = new PutObjectRequest(bucketName, objectName, inputStream);
            // 创建PutObject请求。
            PutObjectResult result = ossClient.putObject(putObjectRequest);
        } catch (OSSException oe) {
            System.out.println("Caught an OSSException, which means your request made it to OSS, "
                    + "but was rejected with an error response for some reason.");
            System.out.println("Error Message:" + oe.getErrorMessage());
            System.out.println("Error Code:" + oe.getErrorCode());
            System.out.println("Request ID:" + oe.getRequestId());
            System.out.println("Host ID:" + oe.getHostId());
        } catch (ClientException ce) {
            System.out.println("Caught an ClientException, which means the client encountered "
                    + "a serious internal problem while trying to communicate with OSS, "
                    + "such as not being able to access the network.");
            System.out.println("Error Message:" + ce.getMessage());
        } finally {
            if (ossClient != null) {
                ossClient.shutdown();
            }
        }
        //拼接文件访问路径
        String url = endpoint.split("//")[0] + "//" + bucketName + "." + endpoint.split("//")[1] + "/" + objectName;
        return url;
    }
}
```

Controller层

```java
import com.tlias.pojo.Result;
import com.tlias.utils.AliOSSUtil;
import lombok.extern.slf4j.Slf4j;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.web.bind.annotation.PostMapping;
import org.springframework.web.bind.annotation.RestController;
import org.springframework.web.multipart.MultipartFile;

@Slf4j
@RestController
public class UploadController {

    @Autowired
    private AliOSSUtil aliOSSUtil;

    @PostMapping("/upload")
    public Result upload(String username, Integer age, MultipartFile image) throws Exception {
        log.info("参数为:{},{},{}", username, age, image);
        //使用oss来保存数据
        String url = aliOSSUtil.upload(image);
        return Result.success(url);
    }
}
```

这个时候我们就能在添加员工时上传头像，也能在bucket中看到上传的图片

![image-20250319214840274](./pictures/image-20250319214840274.png)

![image-20250319214858394](./pictures/image-20250319214858394.png)





### 员工管理-修改员工信息

实现该功能需要实现两个小功能，一个是根据id查询员工信息用于数据回显，另一个就是根据id修改员工信息

Controller层

```java
import com.tlias.pojo.Emp;
import com.tlias.pojo.PageBean;
import com.tlias.pojo.Result;
import com.tlias.service.EmpService;
import lombok.extern.slf4j.Slf4j;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.format.annotation.DateTimeFormat;
import org.springframework.web.bind.annotation.*;

import java.time.LocalDate;
import java.util.List;

@Slf4j
@RestController
@RequestMapping("/emps")
public class EmpController {

    @Autowired
    private EmpService empService;

    /**
     * 根据id查询员工信息
     * @param id
     * @return
     */
    @GetMapping("/{id}")
    public Result getById(@PathVariable Integer id){
        Emp emp = empService.getById(id);
        return Result.success(emp);
    }

    /**
     * 修改员工信息
     * @param emp
     * @return
     */
    @PutMapping
    public Result update(@RequestBody Emp emp){
        log.info("修改员工信息,id为{}",emp.getId());
        empService.update(emp);
        return Result.success();
    }
}
```

Service层接口

```java
import com.tlias.pojo.Emp;
import com.tlias.pojo.PageBean;

import java.time.LocalDate;
import java.util.List;

public interface EmpService {
    /**
     * 根据id查询员工信息
     * @param id
     * @return
     */
    Emp getById(Integer id);

    /**
     * 修改员工信息
     * @param emp
     */
    void update(Emp emp);
}
```

Service层实现

```java
import com.github.pagehelper.Page;
import com.github.pagehelper.PageHelper;
import com.tlias.mapper.EmpMapper;
import com.tlias.pojo.Emp;
import com.tlias.pojo.PageBean;
import com.tlias.service.EmpService;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Service;

import java.time.LocalDate;
import java.time.LocalDateTime;
import java.util.List;

@Service
public class EmpServiceImp implements EmpService {

    @Autowired
    private EmpMapper empMapper;

    @Override
    public Emp getById(Integer id) {
        Emp emp = empMapper.getById(id);
        return emp;
    }

    @Override
    public void update(Emp emp) {
        empMapper.update(emp);
    }


}
```

Mapper层接口

```java
import com.tlias.pojo.Emp;
import org.apache.ibatis.annotations.Insert;
import org.apache.ibatis.annotations.Mapper;
import org.apache.ibatis.annotations.Select;

import java.time.LocalDate;
import java.util.List;

@Mapper
public interface EmpMapper {
    /**
     * 根据id查询员工信息
     * @param id
     * @return
     */
    @Select("select * from emp where id = #{id}")
    Emp getById(Integer id);

    /**
     * 更新员工信息
     * @param emp
     */
    void update(Emp emp);
}
```

xml映射文件

```java
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE mapper
        PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
        "http://mybatis.org/dtd/mybatis-3-mapper.dtd">

<mapper namespace="com.tlias.mapper.EmpMapper">
    <update id="update">
        update emp
        <set>
            <if test="username!=null and username!=''">
                username=#{username},
            </if>
            <if test="name!=null and name!=''">
                name=#{name},
            </if>
            <if test="gender!=null">
                gender=#{gender},
            </if>
            <if test="image!=null and image!=''">
                image=#{image},
            </if>
            <if test="job!=null">
                job=#{job},
            </if>
            <if test="entrydate!=null">
                entrydate=#{entrydate},
            </if>
            <if test="deptId!=null">
                dept_id=#{deptId},
            </if>
            <if test="updateTime!=null">
                update_time=#{updateTime},
            </if>
        </set>
        where id = #{id}
    </update>

</mapper>
```



### springboot的配置文件

常见的配置文件有xml、properties、yml(yaml)三种，它们三个区别如下图

![image-20250320120445285](./pictures/image-20250320120445285.png)

springboot中使用的是properties和yml



#### 1.springboot自带的application.properties

在上面实现图片上传的功能中，我们上传文件用到的AliOSSUtil工具类中，有下面这段代码

```java
// Endpoint以华东1（杭州）为例，其它Region请按实际情况填写。
String endpoint = "https://oss-cn-beijing.aliyuncs.com";
// 从环境变量中获取访问凭证。运行本代码示例之前，请确保已设置环境变量OSS_ACCESS_KEY_ID和OSS_ACCESS_KEY_SECRET。
EnvironmentVariableCredentialsProvider credentialsProvider = CredentialsProviderFactory.newEnvironmentVariableCredentialsProvider();
// 填写Bucket名称，例如examplebucket。
String bucketName = "javaweb-tlias-case-sky";
// 填写Object完整路径，完整路径中不能包含Bucket名称，例如exampledir/exampleobject.txt。
String originalFileName = file.getOriginalFilename();
int index = originalFileName.lastIndexOf(".");

String objectName = "pictures/"+ UUID.randomUUID()+originalFileName.substring(index);
// 填写Bucket所在地域。以华东1（杭州）为例，Region填写为cn-hangzhou。
String region = "cn-beijing";
```

不难发现，其中的endpoint、bucketName、region等变量的值都是固定要写的，但是这些值可能会随着使用的oss服务器的变化而跟着变化，此时如果想要修改这些变量就要在代码中一个一个修改，这非常不利于项目管理。

为了解决这个问题，我们可以将这些变量放在一个配置文件中，如果服务器发生变化，只需要修改配置文件中的对应值即可。

一般来说，如果把数据放在配置文件中，如果要获取这些数据，我们需要先在代码中加载配置文件，然后根据加载的内容来获取对应的数据。但是，在springboot项目中，存在一个默认的配置文件，那就是位于resources文件夹下的`application.properties`文件，并且springboot提供了`@Value`注解，使用这个注解来注入属性值，能直接将配置文件中的数据赋给变量，不要我们自己去加载配置文件，再去找想要的数据了。

`@Value`的使用语法如下

```java
@Value("${键名}")		//该注解会将配置文件中键所对应的值赋给下面的变量s
private String s;
```

要注意的是，`@Value`注解只能将值赋给成员变量，不能赋给方法中定义的局部变量

配置文件如下

可以自定义名字

```properties
#aliyun-oss
aliyun.oss.endpoint=https://oss-cn-beijing.aliyuncs.com
aliyun.oss.bucketName=javaweb-tlias-case-sky
aliyun.oss.region=cn-beijing
```

这里中文乱码问题暂时还没解决，将就看一下

![image-20250320114738705](./pictures/image-20250320114738705.png)

配置好后修改AliOSSUtil

```java
import com.aliyun.oss.*;
import com.aliyun.oss.common.auth.CredentialsProviderFactory;
import com.aliyun.oss.common.auth.EnvironmentVariableCredentialsProvider;
import com.aliyun.oss.common.comm.SignVersion;
import com.aliyun.oss.model.PutObjectRequest;
import com.aliyun.oss.model.PutObjectResult;
import org.springframework.beans.factory.annotation.Value;
import org.springframework.stereotype.Component;
import org.springframework.web.multipart.MultipartFile;

import java.io.InputStream;
import java.util.UUID;

@Component
public class AliOSSUtil {
    //@Value只能将值赋给类的成员变量
    
    // Endpoint以华东1（杭州）为例，其它Region请按实际情况填写。
    //使用@Value注解来获取配置文件中的数据
    @Value("${aliyun.oss.endpoint}")
    private String endpoint;
    // 填写Bucket名称，例如examplebucket。
    @Value("${aliyun.oss.bucketName}")
    private String bucketName;
    // 填写Bucket所在地域。以华东1（杭州）为例，Region填写为cn-hangzhou。
    @Value("${aliyun.oss.region}")
    private String region;

    public String upload(MultipartFile file) throws Exception {
        // 从环境变量中获取访问凭证。运行本代码示例之前，请确保已设置环境变量OSS_ACCESS_KEY_ID和OSS_ACCESS_KEY_SECRET。
        EnvironmentVariableCredentialsProvider credentialsProvider = CredentialsProviderFactory.newEnvironmentVariableCredentialsProvider();
        // 填写Object完整路径，完整路径中不能包含Bucket名称，例如exampledir/exampleobject.txt。
        String originalFileName = file.getOriginalFilename();
        int index = originalFileName.lastIndexOf(".");

        String objectName = "pictures/" + UUID.randomUUID() + originalFileName.substring(index);

        // 创建OSSClient实例。
        ClientBuilderConfiguration clientBuilderConfiguration = new ClientBuilderConfiguration();
        clientBuilderConfiguration.setSignatureVersion(SignVersion.V4);
        OSS ossClient = OSSClientBuilder.create()
                .endpoint(endpoint)
                .credentialsProvider(credentialsProvider)
                .clientConfiguration(clientBuilderConfiguration)
                .region(region)
                .build();

        try {
            InputStream inputStream = file.getInputStream();
            // 创建PutObjectRequest对象。
            PutObjectRequest putObjectRequest = new PutObjectRequest(bucketName, objectName, inputStream);
            // 创建PutObject请求。
            PutObjectResult result = ossClient.putObject(putObjectRequest);
        } catch (OSSException oe) {
            System.out.println("Caught an OSSException, which means your request made it to OSS, "
                    + "but was rejected with an error response for some reason.");
            System.out.println("Error Message:" + oe.getErrorMessage());
            System.out.println("Error Code:" + oe.getErrorCode());
            System.out.println("Request ID:" + oe.getRequestId());
            System.out.println("Host ID:" + oe.getHostId());
        } catch (ClientException ce) {
            System.out.println("Caught an ClientException, which means the client encountered "
                    + "a serious internal problem while trying to communicate with OSS, "
                    + "such as not being able to access the network.");
            System.out.println("Error Message:" + ce.getMessage());
        } finally {
            if (ossClient != null) {
                ossClient.shutdown();
            }
        }
        //拼接文件访问路径
        String url = endpoint.split("//")[0] + "//" + bucketName + "." + endpoint.split("//")[1] + "/" + objectName;
        return url;
    }
}
```





#### 2.yml配置文件

yml配置文件的基本语法如下

![image-20250320120828008](./pictures/image-20250320120828008.png)

要注意，使用yml定义对象、map和定义数组、集合的语法格式是不一样的



下面是一个示例

```yaml
#配置服务器端口号
server:
  port: 9090

#定义对象、map集合
user:
  name: Arthur
  age: 20
  address: shenzhen

#定义数组、集合，横杠-后面就是数组或集合的元素内容
hobby:
  - Java
  - C++
  - Game
  - Sport
```

重新启动服务器，可以发现服务器的端口号变为了9090

![image-20250320121331742](./pictures/image-20250320121331742.png)



使用yml配置文件来替换properties文件

![image-20250320143243748](./pictures/image-20250320143243748.png)

yml配置文件的编写如下

```yaml
#使用yml文件替换properties
spring:
  application:
    name: tlias-web-management

#配置数据库
  datasource:
    driver-class-name: com.mysql.cj.jdbc.Driver
    url: jdbc:mysql://localhost:3306/tlias
    username: root
    password: gt1303190518
#配置文件上传大小
  servlet:
    multipart:
      max-request-size: 100MB
      max-file-size: 10MB
#配置mybatis
mybatis:
  configuration:
    log-impl: org.apache.ibatis.logging.stdout.StdOutImpl
    map-underscore-to-camel-case: true

#阿里云oss
aliyun:
  oss:
    endpoint: https://oss-cn-beijing.aliyuncs.com
    bucketName: javaweb-tlias-case-sky
    region: cn-beijing
```





#### 3.`@ConfigurationProperties`注解

前面我们讲到，要将配置文件中的值赋给变量，可以使用`@Value`注解，但是使用`@Value`注解需要指定要注入的值的键，此时如果我们有很多值需要注入，那么使用`@Value`注解也会变得非常繁琐。而springboot还给我们提供了一个非常好用的注解，那就是`@ConfigurationProperties`，这个注解需要配合实体类来使用，将我们要注入的变量全放在一个实体类中，然后对实体类使用`@ConfigurationProperties`注解，此时实体类中的所有变量都会得到配置文件里的对应的值，然后我们再通过getter、setter方法来访问这些值就可以了

接下来我们就用`@ConfigurationProperties`注解来继续优化AliOSSUtil类

首先将需要配置的变量全放在一个实体类中

```java
import lombok.Data;
import org.springframework.boot.context.properties.ConfigurationProperties;
import org.springframework.stereotype.Component;

//配置getter、setter方法
@Data
//将该实体类交给IOC容器管理，方便要用这些配置信息的时候通过依赖注入来获得
@Component
//使用@ConfigurationProperties注解来注入所需的值，但是需要指定该值的前缀
@ConfigurationProperties(prefix = "aliyun.oss")
public class AliOSSProperties {

    //变量名需要与配置文件中的键名一致
    private String endpoint;
    private String bucketName;
    private String region;

}
```

有了配置信息的实体类我们再接着修改AliOSSUtil类

```java
import com.aliyun.oss.*;
import com.aliyun.oss.common.auth.CredentialsProviderFactory;
import com.aliyun.oss.common.auth.EnvironmentVariableCredentialsProvider;
import com.aliyun.oss.common.comm.SignVersion;
import com.aliyun.oss.model.PutObjectRequest;
import com.aliyun.oss.model.PutObjectResult;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.beans.factory.annotation.Value;
import org.springframework.stereotype.Component;
import org.springframework.web.multipart.MultipartFile;

import java.io.InputStream;
import java.util.UUID;

@Component
public class AliOSSUtil {

    //通过依赖注入来获取配制信息的实体类
    @Autowired
    private AliOSSProperties aliOSSProperties;

    public String upload(MultipartFile file) throws Exception {
        //使用实体类来获取配置信息
        String endpoint = aliOSSProperties.getEndpoint();
        String bucketName = aliOSSProperties.getBucketName();
        String region = aliOSSProperties.getRegion();


        // 从环境变量中获取访问凭证。运行本代码示例之前，请确保已设置环境变量OSS_ACCESS_KEY_ID和OSS_ACCESS_KEY_SECRET。
        EnvironmentVariableCredentialsProvider credentialsProvider = CredentialsProviderFactory.newEnvironmentVariableCredentialsProvider();
        // 填写Object完整路径，完整路径中不能包含Bucket名称，例如exampledir/exampleobject.txt。
        String originalFileName = file.getOriginalFilename();
        int index = originalFileName.lastIndexOf(".");

        String objectName = "pictures/" + UUID.randomUUID() + originalFileName.substring(index);

        // 创建OSSClient实例。
        ClientBuilderConfiguration clientBuilderConfiguration = new ClientBuilderConfiguration();
        clientBuilderConfiguration.setSignatureVersion(SignVersion.V4);
        OSS ossClient = OSSClientBuilder.create()
                .endpoint(endpoint)
                .credentialsProvider(credentialsProvider)
                .clientConfiguration(clientBuilderConfiguration)
                .region(region)
                .build();

        try {
            InputStream inputStream = file.getInputStream();
            // 创建PutObjectRequest对象。
            PutObjectRequest putObjectRequest = new PutObjectRequest(bucketName, objectName, inputStream);
            // 创建PutObject请求。
            PutObjectResult result = ossClient.putObject(putObjectRequest);
        } catch (OSSException oe) {
            System.out.println("Caught an OSSException, which means your request made it to OSS, "
                    + "but was rejected with an error response for some reason.");
            System.out.println("Error Message:" + oe.getErrorMessage());
            System.out.println("Error Code:" + oe.getErrorCode());
            System.out.println("Request ID:" + oe.getRequestId());
            System.out.println("Host ID:" + oe.getHostId());
        } catch (ClientException ce) {
            System.out.println("Caught an ClientException, which means the client encountered "
                    + "a serious internal problem while trying to communicate with OSS, "
                    + "such as not being able to access the network.");
            System.out.println("Error Message:" + ce.getMessage());
        } finally {
            if (ossClient != null) {
                ossClient.shutdown();
            }
        }
        //拼接文件访问路径
        String url = endpoint.split("//")[0] + "//" + bucketName + "." + endpoint.split("//")[1] + "/" + objectName;
        return url;
    }
}
```

通过打断点我们可以发现，执行该程序时，实体类中的变量成功获取到了配置文件中的信息

![image-20250320145336076](./pictures/image-20250320145336076.png)



如果配置信息实体类上有红色警告怎么办

![image-20250320145756980](./pictures/image-20250320145756980.png)

我们只需要导入一个依赖

```xml
<dependency>
   <groupId>org.springframework.boot</groupId>
   <artifactId>spring-boot-configuration-processor</artifactId>
</dependency>
```

这个依赖的作用是会根据我们写的配置信息的实体类，在yml文件中给我们提示。添加了这个依赖红色警告就消失了

![image-20250320150039831](./pictures/image-20250320150039831.png)



#### 4.`@ConfigurationProperties`与`@Value`的异同

![image-20250320150333972](./pictures/image-20250320150333972.png)



### 登录功能

完成开发案例的登录功能。

该功能的实现思路为：根据用户输入的用户名和密码来查询用户信息，如果查询到用户信息说明用户名和密码正确，如果查询不到用户信息说明用户名或密码错误

Controller层

```java
import com.tlias.pojo.Emp;
import com.tlias.pojo.Result;
import com.tlias.service.EmpService;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.web.bind.annotation.PostMapping;
import org.springframework.web.bind.annotation.RequestBody;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class LoginController {

    @Autowired
    private EmpService empService;

    /**
     * 实现用户登录功能
     * @param emp
     * @return
     */
    @PostMapping("/login")
    public Result login(@RequestBody Emp emp){
        //根据用户名和密码查询用户信息
        Emp user = empService.selectByUsernameAndPassword(emp);
        //如果查询到用户信息则允许登录，否则登录失败
        return user!=null?Result.success():Result.error("用户名或密码错误");
    }
}
```



Service层接口

```java
import com.tlias.pojo.Emp;
import com.tlias.pojo.PageBean;

import java.time.LocalDate;
import java.util.List;

public interface EmpService {
    /**
     * 根据用户名和密码查询用户信息
     * @param emp
     * @return
     */
    Emp selectByUsernameAndPassword(Emp emp);
}
```

Service层实现

```java
import com.github.pagehelper.Page;
import com.github.pagehelper.PageHelper;
import com.tlias.mapper.EmpMapper;
import com.tlias.pojo.Emp;
import com.tlias.pojo.PageBean;
import com.tlias.service.EmpService;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Service;

import java.time.LocalDate;
import java.time.LocalDateTime;
import java.util.List;

@Service
public class EmpServiceImp implements EmpService {

    @Autowired
    private EmpMapper empMapper;

    @Override
    public Emp selectByUsernameAndPassword(Emp emp) {
        return empMapper.selectByUsernameAndPassword(emp);
    }


}
```



Mapper层接口

```java
import com.tlias.pojo.Emp;
import org.apache.ibatis.annotations.Insert;
import org.apache.ibatis.annotations.Mapper;
import org.apache.ibatis.annotations.Select;

import java.time.LocalDate;
import java.util.List;

@Mapper
public interface EmpMapper {
    /**
     * 根据用户名和密码查询用户信息
     * @param emp
     * @return
     */
    @Select("select * from emp where username=#{username} and password=#{password}")
    Emp selectByUsernameAndPassword(Emp emp);
}

```



### 登录校验-实现思路

登录校验指的是服务端接收到一个请求时要先判断用户是否已经登录，如果登录了才允许用户访问资源，如果没有登录就跳转到登录页面让用户登录。

要实现这个功能我们需要解决两个问题：

1.如何记住用户的登录信息？

2.如何在访问所有资源前先判断用户是否登录？



第一个问题，需要用到会话跟踪技术。

第二个问题，需要用到过滤器（filter）、拦截器（Interceptor）技术来进行统一拦截。如果不用这两个技术，貌似也能够实现，只需要在每次访问资源前手动判断进行登录校验，但是这样就很繁琐了，一个项目中有那么多资源，每一个资源都手动校验一次那可太享受了。

下面时登录校验的实现思路图

![image-20250320160445039](./pictures/image-20250320160445039.png)





### 登录校验-下发JWT令牌

我们这里的会话跟踪技术使用的是jwt令牌，详细使用方法可在本笔记搜索`JWT`。



创建JWT工具类

```java
import io.jsonwebtoken.Claims;
import io.jsonwebtoken.Jwts;
import io.jsonwebtoken.SignatureAlgorithm;

import java.util.Date;
import java.util.Map;

public class JwtUtil {

    //JWT令牌密钥
    private static String key = "ArthurSky";
    //设置令牌过期时间为1小时
    private static long expiration = 3600*1000;


    /**
     * 生成jwt令牌
     * @param claims
     * @return
     */
    public static String generateJwt(Map<String,Object> claims){
        String jwt = Jwts.builder().signWith(SignatureAlgorithm.HS256, key)
                .setClaims(claims)
                .setExpiration(new Date(System.currentTimeMillis() + expiration))
                .compact();

        return jwt;
    }


    /**
     * 解析jwt令牌
     * @param jwt
     * @return
     */
    public static Claims parserJwt(String jwt){
        Claims claims = Jwts.parser().setSigningKey(key)
                .parseClaimsJws(jwt)
                .getBody();
        return claims;
    }
}
```

修改登录功能的Controller类

```java
import com.tlias.pojo.Emp;
import com.tlias.pojo.Result;
import com.tlias.service.EmpService;
import com.tlias.utils.JwtUtil;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.web.bind.annotation.PostMapping;
import org.springframework.web.bind.annotation.RequestBody;
import org.springframework.web.bind.annotation.RestController;

import java.util.HashMap;
import java.util.Map;

@RestController
public class LoginController {

    @Autowired
    private EmpService empService;

    /**
     * 实现用户登录功能
     * @param emp
     * @return
     */
    @PostMapping("/login")
    public Result login(@RequestBody Emp emp){
        //根据用户名和密码查询用户信息
        Emp user = empService.selectByUsernameAndPassword(emp);
        //如果查询到用户信息则允许登录，并下发令牌
        if(user!=null){
            Map<String,Object> claims = new HashMap<>();
            claims.put("id",user.getId());
            claims.put("username",user.getUsername());
            claims.put("name",user.getName());
            String jwt = JwtUtil.generateJwt(claims);
            return Result.success(jwt);
        }
        //如果登录失败就返回失败信息
        return Result.error("用户名或密码错误");
    }
}
```



### 登录校验-校验JWT令牌-使用过滤器

要使用过滤器来拦截所有请求，当然，如果请求是登录请求就要直接放行。

首先获取请求路径，判断请求是否为login请求，如果为login请求就直接放行

如果不是login请求，就判断jwt令牌是否为空

如果令牌为空，直接返回错误信息

如果令牌不为空，再使用JWT工具类解析令牌，如果令牌解析出现异常，返回错误信息

如果令牌解析未出现异常，则放行



代码如下

```java
import com.alibaba.fastjson.JSON;
import com.tlias.pojo.Result;
import com.tlias.utils.JwtUtil;
import jakarta.servlet.*;
import jakarta.servlet.annotation.WebFilter;
import jakarta.servlet.http.HttpServletRequest;
import jakarta.servlet.http.HttpServletResponse;
import org.springframework.util.StringUtils;

import java.io.IOException;

@WebFilter(urlPatterns = "/*")
public class LoginCheckFilter implements Filter {
    //使用过滤器来进行登录校验
    @Override
    public void doFilter(ServletRequest servletRequest, ServletResponse servletResponse, FilterChain filterChain) throws IOException, ServletException {
        //判断请求是否为登录请求，如果是登录请求就直接放行
        //先将ServletRequest和ServletResponse强制转换成HttpServletRequest和HttpServletResponse
        HttpServletRequest httpServletRequest = (HttpServletRequest) servletRequest;
        HttpServletResponse httpServletResponse = (HttpServletResponse) servletResponse;
        //获取请求路径
        String url = httpServletRequest.getRequestURL().toString();
        //判断请求路径是否包含登录的请求路径
        if (url.contains("login")) {
            //如果是登录请求，则直接放行
            filterChain.doFilter(servletRequest, servletResponse);
            return;
        }

        //如果不是登录请求，则判断令牌是否为空
        String jwt = httpServletRequest.getHeader("token");
        //使用springboot提供的StringUtils工具类，判断jwt是否为空串，这个hasLength返回字符串长度，如果字符串为空串或为null都会返回false
        if (StringUtils.hasLength(jwt)) {
            //如果令牌不为空，则校验令牌
            try {
                JwtUtil.parserJwt(jwt);
            } catch (Exception e) {
                e.printStackTrace();
                //如果捕获到异常说明令牌非法，直接返回错误信息
                Result result = Result.error("NOT_LOGIN");
                //使用fastJSON将Result转换成JSON格式的数据放在响应体中
                String json = JSON.toJSONString(result);
                httpServletResponse.getWriter().write(json);
                return;
            }
            //如果没有捕获到异常，说明令牌合法，直接放行
            filterChain.doFilter(servletRequest, servletResponse);
        } else {
            //如果令牌为空，返回错误信息
            Result result = Result.error("NOT_LOGIN");
            //使用fastJSON将Result转换成JSON格式的数据放在响应体中
            String json = JSON.toJSONString(result);
            httpServletResponse.getWriter().write(json);
            return;
        }
    }

}
```



### 登录校验-校验JWT令牌-使用拦截器

校验的逻辑和使用过滤器逻辑一致，只需要把过滤器的代码复制过来稍加修改即可

```java
import com.alibaba.fastjson.JSON;
import com.tlias.pojo.Result;
import com.tlias.utils.JwtUtil;
import jakarta.servlet.http.HttpServletRequest;
import jakarta.servlet.http.HttpServletResponse;
import org.springframework.stereotype.Component;
import org.springframework.util.StringUtils;
import org.springframework.web.servlet.HandlerInterceptor;
import org.springframework.web.servlet.ModelAndView;

//将拦截器交给IOC容器管理，方便注册拦截器时使用
@Component
public class LoginCheckedInterceptor implements HandlerInterceptor {
    @Override
    public boolean preHandle(HttpServletRequest request, HttpServletResponse response, Object handler) throws Exception {
        //判断请求是否为登录请求，如果是登录请求就直接放行
        //获取请求路径
        String url = request.getRequestURL().toString();
        //判断请求路径是否包含登录的请求路径
        if (url.contains("login")) {
            //如果是登录请求，则直接放行
            return true;
        }

        //如果不是登录请求，则判断令牌是否为空
        String jwt = request.getHeader("token");
        //使用springboot提供的StringUtils工具类，判断jwt是否为空串，这个hasLength返回字符串长度，如果字符串为空串或为null都会返回false
        if (StringUtils.hasLength(jwt)) {
            //如果令牌不为空，则校验令牌
            try {
                JwtUtil.parserJwt(jwt);
            } catch (Exception e) {
                e.printStackTrace();
                //如果捕获到异常说明令牌非法，直接返回错误信息
                Result result = Result.error("NOT_LOGIN");
                //使用fastJSON将Result转换成JSON格式的数据放在响应体中
                String json = JSON.toJSONString(result);
                response.getWriter().write(json);
                //不允许放行
                return false;
            }
            //如果没有捕获到异常，说明令牌合法，直接放行
            return true;
        } else {
            //如果令牌为空，返回错误信息
            Result result = Result.error("NOT_LOGIN");
            //使用fastJSON将Result转换成JSON格式的数据放在响应体中
            String json = JSON.toJSONString(result);
            response.getWriter().write(json);
            return false;
        }
    }

    @Override
    public void postHandle(HttpServletRequest request, HttpServletResponse response, Object handler, ModelAndView modelAndView) throws Exception {
        //postHandle方法是在目标资源执行完毕后执行的。
        System.out.println("postHandle...");
    }

    @Override
    public void afterCompletion(HttpServletRequest request, HttpServletResponse response, Object handler, Exception ex) throws Exception {
        //afterCompletion方法是在视图渲染完毕后执行的，最后执行
        System.out.println("afterCompletion...");
    }
}
```

但是注意别忘了在配置类中注册拦截器

```java
import com.tlias.interceptor.LoginCheckedInterceptor;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.context.annotation.Configuration;
import org.springframework.web.servlet.config.annotation.InterceptorRegistry;
import org.springframework.web.servlet.config.annotation.WebMvcConfigurer;

//声明此类为配置类
@Configuration
public class WebConfig implements WebMvcConfigurer {

    //通过依赖注入快速使用拦截器对象
    @Autowired
    private LoginCheckedInterceptor interceptorDemo;

    @Override
    public void addInterceptors(InterceptorRegistry registry) {
        /*addInterceptor方法用于注册拦截器，addPathPatterns用于配置拦截路径
        注意拦截器拦截所有的路径与过滤器不同，过滤器是"/*"，而拦截器是"/**"    */
        registry.addInterceptor(interceptorDemo).addPathPatterns("/**").excludePathPatterns("/login");
    }
}
```





### 异常处理

目前我们的项目并没有对异常进行任何处理。假如此时的请求是一个异常请求，如：新增部门时，部门名是重复的

![image-20250320234801764](./pictures/image-20250320234801764.png)

此时我们点击确定，页面不会有任何变化，但是可以打开开发者工具，可以发现此时浏览器收到的结果是500，说明服务器出现了异常，那既然服务器收到了异常的响应，为什么没有对这个响应做出一些处理呢？实际上本来前端是有对异常进行处理的，但是由于服务端没有对异常进行处理，发送给浏览器的异常信息没有按照开发文档规范来，下面有前端收到的异常响应信息，所以前端没法正确处理异常。因此，需要我们后端对异常进行处理，将异常信息按照开发规范封装好发给前端。

![image-20250320234927073](./pictures/image-20250320234927073.png)

响应数据

![image-20250320235045438](./pictures/image-20250320235045438.png)



后端的架构是三层架构，如果没有对异常进行处理，不管哪一层出现的异常，最终都会一直向上抛出，最后会抛给框架来处理，上面的异常响应信息就是框架自动返回的。

![image-20250320235331652](./pictures/image-20250320235331652.png)

因此我们处理异常，只需要在Controller层进行处理，因为最终异常都会被抛到这一层来。



异常处理有两种方法

1.对Controller的所有方法使用try-catch来捕获异常。这种方法实现过于繁琐，不推荐

2.使用全局异常处理器。这种方式会更加简单、优雅。

使用全局异常处理器后，项目的结构会变成这样

![image-20250320235716997](./pictures/image-20250320235716997.png)

此时如果出现异常，异常最终会抛给全局异常处理器处理，如果没有异常，就会正常执行，不会经过全局异常处理器。

定义全局异常处理器需要用到`@RestControllerAdvice`注解，这个注解相当于`@ControllerAdvice`+`@ResponseBody`，而`@ResponseBody`注解会自动将对象转换成json数据，因此全局异常处理器会自动返回json数据。

全局异常处理器还需要用`@ExceptionHandler`注解来指定要捕获的异常类型

接下来我们使用全局异常处理器来处理异常

```java
import com.tlias.pojo.Result;
import org.springframework.web.bind.annotation.ExceptionHandler;
import org.springframework.web.bind.annotation.RestControllerAdvice;

//使用@RestControllerAdvic来定义一个全局异常处理器
@RestControllerAdvice
public class GlobalExceptionHandler {

    //使用@ExceptionHandler来指定该异常处理器要捕获的异常类型，这里是捕获所有异常
    @ExceptionHandler(Exception.class)
    public Result exceptionHandler(Exception e){
        e.printStackTrace();
        return Result.error("操作失败，系统异常");
    }
}
```

此时我们就可以看到浏览器对异常请求做出了提示。

![Screenshot 2025-03-21 000629](./pictures/Screenshot 2025-03-21 000629.png)
