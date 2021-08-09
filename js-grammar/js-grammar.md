# JavaScript 基本语法

**javascript语句与注释**

1、一条javascript语句应该以“;”结尾

```html
<script type="text/javascript">    
var a = 123;
var b = 'str';
function fn(){
    alert(a);
};
fn();
</script>
```

2、javascript注释

```html
<script type="text/javascript">    

// 单行注释
var a = 123;
/*  
    多行注释
    1、...
    2、...
*/
var b = 'str';
</script>
```

## 7.3变量

JavaScript 是一种弱类型语言，javascript的变量类型由它的值来决定。 定义变量需要用关键字   `var`

```html
 var a = 123;
 var b = 'asd';

 //同时定义多个变量可以用","隔开，公用一个‘var’关键字

 var c = 45,d='qwe',f='68';
```

**变量类型**

5种基本数据类型：
number、string、boolean、undefined、null

1种复合类型：
object

**typeof显示变量类型**

```html
<body>
<script  type="text/javascript">
    <!--
    document.write("<h2>对变量或值调用typeof运算符返回值：</h2>");
    var width,height=10,name="rose";
    var date=new Date();   //获取时间日期对象
    var arr=new Array(4);   //定义数组
    document.write("width: "+typeof(width)+"<br/>");
    document.write("height: "+typeof(height)+"<br/>");
    document.write("name: "+typeof(name)+"<br/>");
    document.write("date: "+typeof(date)+"<br/>");
    document.write("arr: "+typeof(arr)+"<br/>");
    document.write("true: "+typeof(true)+"<br/>");
    document.write("null: "+typeof(null));
    -->
</script>
</body>
```

**parseInt等进行类型转换**

```html
<script type="text/javascript">
    <!--
    var op1=prompt("请输入第一个数:","")
    var op2=prompt("请输入第二个数:","")
    var p1=parseInt(op1);
    var p2=parseInt(op2);
    var result=p1+p2;
    document.write(p1+"+"+p2+"="+result);
    -->
</script>
```

**变量、函数、属性、函数参数命名规范**

1、区分大小写
2、第一个字符必须是字母、下划线（_）或者美元符号（$）
3、其他字符可以是字母、下划线、美元符或数字



## 7.6函数

函数就是重复执行的代码片。

### **函数定义与执行**

```html
<script type="text/javascript">
    // 函数定义
    function aa(){
        alert('hello!');
    }
    // 函数执行
    aa();
</script>
```

### **变量与函数预解析**

JavaScript解析过程分为两个阶段，先是编译阶段，然后执行阶段，在编译阶段会将function定义的函数提前，并且将var定义的变量声明提前，将它赋值为undefined。

```html
<script type="text/javascript">    
    aa();       // 弹出 hello！
    alert(bb);  // 弹出 undefined
    function aa(){
        alert('hello!');
    }
    var bb = 123;
</script>
```

### **提取行间事件**

在html行间调用的事件可以提取到javascript中调用，从而做到结构与行为分离。

```html
<!--行间事件调用函数   -->
<script type="text/javascript">        
    function myalert(){
        alert('ok!');
    }
</script>
......
<input type="button" name="" value="弹出" onclick="myalert()">

<!-- 提取行间事件 -->
<script type="text/javascript">

window.onload = function(){
    var oBtn = document.getElementById('btn1');
    oBtn.onclick = myalert;
    function myalert(){
        alert('ok!');
    }
}    
</script>
......
<input type="button" name="" value="弹出" id="btn1">
```

### **匿名函数**

定义的函数可以不给名称，这个叫做匿名函数，可以将匿名函数直接赋值给元素绑定的事件来完成匿名函数的调用。

```html
<script type="text/javascript">

window.onload = function(){
    var oBtn = document.getElementById('btn1');
    /*
    oBtn.onclick = myalert;
    function myalert(){
        alert('ok!');
    }
    */
    // 直接将匿名函数赋值给绑定的事件

    oBtn.onclick = function (){
        alert('ok!');
    }
}

</script>
```

### **函数传参**

```html
<script type="text/javascript">
    function myalert(a){
        alert(a);
    }
    myalert(12345);
</script>
```

### **函数'return'关键字**

函数中'return'关键字的作用：
1、返回函数执行的结果
2、结束函数的运行
3、阻止默认行为

```html
<script type="text/javascript">
function add(a,b){
    var c = a + b;
    return c;
    alert('here!');
}

var d = add(3,4);
alert(d);  //弹出7
</script>
```

### 无参函数

```html
<html>
<head lang="en">
    <meta charset="UTF-8">
    <title>无参函数的应用</title>
</head>
<body>
<input name="btn" type="button" value="显示5次欢迎学习JavaScript" onclick="study( )" />
<script type="text/javascript">
    <!--
    function study( ){
        for(var i=0;i<5;i++){
            document.write("<h4>欢迎学习JavaScript</h4>");
        }
    }
    -->
</script>
</body>
</html>
```

### 含参函数

```html
<!DOCTYPE html>
<html>
<head lang="en">
    <meta charset="UTF-8">
    <title>有参函数的应用</title>
</head>
<body>
<input name="btn" type="button" value="请输入显示欢迎学习JavaScript的次数" onclick="study(prompt('请输入显示欢迎学习JavaScript的次数:',''))" />
<script type="text/javascript">
    <!--
    function study(count){
        for(var i=0;i<count;i++){
            document.write("<h4>欢迎学习JavaScript</h4>");
        }
    }
    -->
</script>
</body>
```

