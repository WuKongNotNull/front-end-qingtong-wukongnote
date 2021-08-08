# JavaScript 基本语法

## js的概述

Javascript是基于事件驱动和面向对象的，运行客户端的脚本语言。

**事件**

和计算机的交互行为：单击、双击、鼠标悬浮、键盘输入 等等行为叫做事件

**面向对象**

编程思想： 一切万物就是对象（Object）

对象：由属性和方法（行为）：

学生属性 parameter： 学号 姓名 年龄等

学生行为 method： 学习、写作业、上课等等

**客户端**

js主要运行的客户端：浏览器  ，运行在浏览器的语言：前端语言

通过node.js技术，实现js可以运行在服务器上

**跨平台**

你的平台(操作系统Linux\window\mac\mac ios\ andriod等等 )支持浏览器，就能运行js

## javaScript 语言的组成

**ecmasscript**

**dom**

**bom**



## 使用js

**1  直接使用**

2 **引用使用**





## 数据类型

数值类型  1 0.2 12.333   100

字符串类型 “sss”

逻辑值类型  true  false

空值   var num;



## 变量

声明变量，并且赋值（定义变量）

var ：  js 属于弱类型语言

```
var  num = 100;
var student_name = "高同学";
var flag = true;
var wukong;
```



## 常量

整数常量  100   077  0xof

浮点常量  1.2    3.0e9

布尔常量 true  / false

字符串常量  "我是悟空非空也"





## js的语法结构

```javascript
document.write("我是悟空非空也");
```



## js运算符

算术运算符  + - *  /  %（去余数） ++  --

位运算符  ~  << >> >>> & ^ |

复合赋值运算符  += -= *= /= %= 等等

比较运算符  > <  == != >= >= ?: (E?a:b)



## 逻辑运算符

逻辑与  &&  a&&b

逻辑或 ||

逻辑非 ！



## 运算符的优先级

略



## 表达式

算术表达式  1+1

字符串表达式 “hello”+"world"

逻辑表达式  1>2



## 流程控制

顺序结构

```javascript
document.write("hello");
document.write("悟空");
document.write("猪八戒");
document.write("唐僧");
```



选择结构

if    if-else  if-else-if  switch   if-else 嵌套

```javascript
/* if 结构*/

if (2>1){
    document.write("我是悟空非空也");
}
document.write("<hr>");
/*if -else 结构*/
if (1>2){
    document.write("我是唐僧");
}else{
    document.write("我是唐三藏");
}
document.write("<hr>");
/*if -else if-else 结构*/
var score =99;
if (score>90) {
    document.write("你获得了一等奖学金");
} else if (score>80) {
    document.write("二等奖学金");
} else if(score>70) {
    document.write("三等奖学金");
} else {
    document.write("呵呵，没有。。。");
}
document.write("<hr>");

/*switch 结构*/
var score3 = 100;
var degree = score3/10;
switch (degree) {
    case 10:
        document.write("获得满分，奖励苹果手机一部");
        break;
    case 9:
        document.write("获得90几分,奖励华为手机一部");
        break;
    case 8:
        document.write("获得80几分，奖励山寨手机一部");
        break;
    default:
        document.write("谢谢参与");
        break;
}

document.write("<hr>");
/*if-else 嵌套*/
var score2 = 91;
if(score2>90){
    document.write("恭喜你，获得一等奖学金");
    if(score2>95){
        document.write("获得苹果电脑一台");
    }else{
        document.write("获得华为手机一部");
    }
}else {
    document.write("很抱歉，没有奖学金");
    if(score2>60){
        document.write("本次考试通过");
    }else{
        document.write("欢迎参加补考");
    }
}
document.write("<hr>");
```



循环结构

while

do-while

for

```javascript
/* 循环结构 while :1-100 之和  */
var i =1;
var sum = 0;
while(i<=100){
    sum +=i;
    i++;
}
document.write("1-100和为："+sum);

document.write("<hr>");

/* for 循环*/

var sum2=0;
for (var j=1;j<=1000;j++){
    sum2 +=j;
}
document.write("1-1000和为：",sum2);

document.write("<hr>");

/* do -while*/
var k=1;
var sum3=0;
do{
    sum3 +=k;
    k++;
}while(k<=10);
document.write("1-10之和为",sum3);



```



**转移语法**

break  终止当前循环

```
//  输出1 - 100 ，当遇到50的时候，停止输出
// break ,停止当前循环
/*for(var i=0; i<100;i++){
    if(i == 50){
        break;
    }
    document.write("输出数字"+(i+1)+"<br>");
}*/
```



continue  停止本次循环，进入下

一次循环

```javascipt
for(var i=0; i<100;i++){
    if(i == 49){
       continue;
    }
    document.write("输出数字"+(i+1)+"<br>");
}


```





## 函数

**自定义函数**

在js中直接调用

```javascript
/*js 的函数*/
//定义函数
function show() {
    document.write("我是悟空非空也");
}
show();

document.write("<hr>");

function add( a, b) {
    return a +b;
}
var sum = add(1,2);
document.write("和为",sum);

document.write("<hr>");

function sub(a,b) {
    var result = a-b;
    document.write("减的结果为",result);
}
sub(10,5);
```



**匿名函数**

```
// 定义匿名函数

var show =function () {
    document.write("我是悟空非空也");
}
//调用
show();
```



html

```html
<button id="show">输出一句话</button>
<!--引入 js，一定要放在 id为show的下面 -->
<script src="function.js"></script>
```

js

```javascript
var button = document.getElementById("show");
/*匿名函数*/
button.onclick= function () {
    document.write("我是唐僧啊。。。。");
}
```



## 内部函数

isNaN()  判断变量是否是数字

is not a number

```
// isNaN  ?  没有归属对象的函数，就在内部函数

function test() {
    // 输入框的作用
    var result = window.prompt("请输入数字：",""); // 100 字符串，系统转换成 100 数字
    var number = window.parseInt(result);
    if (isNaN(number)){ //true:  is not a number
        window.alert("该结果不是一个数字");
    } else {
        window.alert("该结果是一个数字");
    }
}
```



## 使用Function() 去构造函数

```
var add = new Function("a", "b", "return a+b");
/*var result = add(2,4);
window.alert(result);*/
/*window.alert(add(2,4));*/
document.write(add(2,4));
```



##   事件

略





## 对象

**预定义对象**

​	内置对象

​		  math

​			string 对象

​	浏览器对象

​		document

​		location

​		history

自定义对象

学生对象？



****

### String

```
// 使用string 对象
str = new String("我是悟空非空也ss");
document.write("该对象的长度为:"+ str.length);
document.write("该字符串的第5个字符是："+str.charAt(4));
document.write("sss"+str.substr(2,2));
document.write("<hr>")
document.write("sss"+str.substring(2,3));
```



### Array

```
// 使用Array 对象
var array = new Array();
array[0] = "a";
array[1] = "b";
array[2] = "c";
for ( var x in array.sort()){
    document.write(array[x]+"<br>");
}
```



## Math 内置对象

方法

abs()   absolute  绝对的

floor()  对数进行下舍入   5.4  floor(5.4)---》 5

ceil()   对数进行向上取值  5.4  ceil（5.4）--》6

random()   取0到1 之间的随机值

round()  四舍五入

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>猜数字</title>
    <script src="js.js"></script>
</head>
<body>

    <div>
        <div>
            <input type="text" placeholder="请输入0-10之间的整数" id="myInput">
        </div>
        <div><input type="button" value="点击" id="inputId"></div>
        <!-- 此处的div 容器 用于显示 结果-->
        <div id="display"></div>
    </div>

</body>
</html>
```

```
//  先将整个html加载到浏览器中，之后加载  window.onload = function () {} 代码
window.onload = function () {
    var inputIdObj = document.getElementById("inputId");
    inputIdObj.onclick =  guess;

    // 放js 代码
    function guess() {
        var myInput = document.getElementById("myInput");
        // 调试代码 我们喜欢用console.log（）
        console.log("我猜的数字是："+myInput.value);
        // 生成一个随机数 --》Math 对象  [0,1] *100 --->[0,100]  10.23432
        var number = Math.floor(Math.random()*10);  // [0,10] 之间的整数
        console.log("生成的随机整数为；"+number);
        var displayDiv = document.getElementById("display");
        if(myInput.value > number) {
            displayDiv.innerHTML = "<h2>你猜大了，不好意思啊</h2>";
        }else  if(myInput.value < number){
            displayDiv.innerHTML = "<h2>你猜小了，不好意思啊</h2>";
        }else {
            displayDiv.innerHTML = "<h2>恭喜你，猜中了</h2>";
        }
    }
}
```





## Date 对象

getDate()  返回月中哪一天

getDay() 返回是一个星期中的哪一个天 （0-6）0 表示 星期日

getHours()

....





## 自定义对象

法一： 使用json的方式自定义对象

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>json方式自定义对象</title>
    <script>
        // 黄金三大步：  定义对象（类）  创建对象   使用对象
        // 通过 json格式 方式定义对象 Objcet  面向事物编程
        // 对象包含 属性和方法
        // 定义对象和创建对象
        var student = {
            // 属性名 ：属性值 （数字/字符串/对象）
            studentNo : 100,
            studentName : "悟空",
            contact: {
                home: "025-12345678",
                phone: "15312088395"
            },
            studentAge: 18,
            show: function () {  // function show(){}
                console.log(this.studentNo);
                console.log(this.studentName);
                console.log(this.studentAge);
                console.log(this.contact.home);
                console.log(this.contact.phone);
                document.write("我是一个好学生");
            }
        }

        //使用对象
        student.show();


    </script>
</head>
<body>

</body>
</html>
```



法二： 使用构造函数定义对象

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>使用构造函数定义对象</title>
    <script>
        // 黄金三大步：  定义对象（类）  创建对象   使用对象
        // 该函数就是对象Student的构造函数 ，通过该构造函数可以定义对象
        function Student(studentNo,studentName,studentAge) {
            this.studentNo = studentNo;
            this.studentName = studentName;
            this.studentAge = studentAge;
            this.show = function () {
                document.write(this.studentNo+"<br>");
                document.write(this.studentName+"<br>");
                document.write(this.studentAge + "<br>");

            }

        }

        // 追加一个新的属性或者新方法  prototype
        Student.prototype.study = function () {
            console.log("该学生真正学习中，好用功啊。。。。");
        }
        Student.prototype.studentAddress = "";

        // 创建对象
        var student1 = new Student("001","wukong",18);
        var student2 = new Student("002","tangseng",1000);


        // 使用对象
        student1.show();
        student1.study();
        console.log(student1.studentNo);
        console.log(student1.studentName);
        console.log(student1.studentAge);
        student1.studentAddress = "天竺市";
        console.log(student1.studentAddress);

        student2.show();
        console.log(student2.studentNo);
        console.log(student2.studentName);
        console.log(student2.studentAge);





    </script>
</head>
<body>

</body>
</html>


```



