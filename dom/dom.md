# DOM 编程

js 三部分构成

ECMAScript   表示js语言 版本号

dom  document object model

bow  browser object model

​	window  --->( document/ history/location)  父子关系



## window

### 属性

常用属性

document

/ history

/location

### 常用方法

alert () 警示框

```
window.altert("大家小心啊 。。。。");
```



confirm ()  确认框

```javascript
        var flag =window.confirm("请确定删除吗?");
        console.log("flag " +flag);
        if(flag === true  ) {
               window.alert("已经删除成功");
        }else {
           window.alert("不删除啦，我在考虑考虑");
        }
```



prompt()  输入提示框

```
        //prompt  输入提示框  , 返回值为你输入的值
     var str =   window.prompt("请输入数字：","100");
     console.log(str);


```



open()

```
        window.onload = function () {
            var btnObj = document.getElementById("btn");
            btnObj.onclick = function () {
                window.open("http://www.baidu.com");
            }
        }


```



setTimeout()

定时器的作用 ，可以某一时间后，调用某一个方法

clearTimeout()

```
    <script>
        //setTimeout()
        function  show() {
            document.write("hello wukong");
        }
        window.setTimeout(show,10000);
    </script>


  <!--  <p> 10秒钟后，调用某个方法，方法中输出一句话</p>-->


```



setInterval()

周期性的定时器

clearInterval()

```
    <script>

        function  show() {
            console.log("hello wukong");
        }
        var number = window.setInterval(show,5000);

        function  stop() {
            window.clearInterval(number);
        }


    <p>每5秒，调用一次某个方法，在控制台输出 hello  wukong </p>
    <button onclick="stop()">点击按钮后，周期性定时器停止</button>

```



### 事件

常见事件

onblur

onfocus

ondblclick

onkeydown

onclick 等等



onload  浏览器把页面的的所有内容都加载完毕后，触发该事件。

```
// 页面加载完成后，跳出广告窗口
window.onload = function(){

}


```



onunload 浏览器窗口被关闭是，触发该事件。

（不推荐使用，最新的浏览器一般不支持）

https://www.cnblogs.com/tu-0718/p/11765027.html

```
// 窗口被关闭时，弹出警示框


```



## document

表示网页的实际内容



### 属性

title, links, images,forms 等等

```
//title
<head>
    <meta charset="UTF-8">
    <title>悟空学院</title>
    <script>
        window.onload =  function () {
            var divObj = document.getElementById("display");
            divObj.innerHTML = "当前文档的标题为=>" + document.title + "<br>";
            divObj.innerHTML += "当前文档的最后修改时间：" + document.lastModified + "<br>";
            divObj.innerHTML += "当前文档中包含多少个超链接：" + document.links.length+ "<br>";
            divObj.innerHTML += "当前文档中包含多少个图片：" + document.images.length+ "<br>";
            divObj.innerHTML += "当前文档中包含多少个表单：" + document.forms.length+ "<br>";

        }
    </script>
</head>
<body>
<a href="http://www.baidu.com"> 百度一下</a><br>
<a href="http://www.taobao.com">淘宝</a><br>
<img src="img/1.jpg" alt="未加载"><br>
<img src="img/2.jpg" alt="未加载"><br>
<img src="img/3.jpg" alt="未加载"><br>
<form action="">
    <input type="text"><br>
    <input type="password"><br>
    <input type="button" value="提交"><br>
</form>
<hr>
<div id="display">


</div>

```





### 方法

**getElementById()**

```
  var divObj = document.getElementById("display");
  
  <div id="display">

</div>


```



**getElementsByName()**

```
 <script>
        window.onload = function () {
            var inputObjs = document.getElementsByName("hobbies");
            var showDiv = document.getElementById("show");
            showDiv.innerHTML = "元素数组的个数为："+ inputObjs.length +"<br>";
            showDiv.innerHTML += "第一个元素的属性name的值为："+ inputObjs[0].name +"<br>";
            showDiv.innerHTML += "第一个元素的属性type的值为："+ inputObjs[0].type +"<br>";
            showDiv.innerHTML += "第一个元素的属性checked的值为："+ inputObjs[0].checked +"<br>";
            showDiv.innerHTML += "第二个元素为："+ inputObjs[1].value +"<br>";
            showDiv.innerHTML += "第三个元素为："+ inputObjs[2].value +"<br>";
            showDiv.innerHTML += "第四个元素为："+ inputObjs[3].value +"<br>";

        }
    </script>
</head>
<body>
<form action="">
    用户名： <input type="text"><br>
    <input type="checkbox" name="hobbies" value="eat" checked ="checked" >吃
    <input type="checkbox" name="hobbies" value="drink">喝
    <input type="checkbox" name="hobbies" value="play">玩
    <input type="checkbox" name="hobbies" value="fun">乐
</form>
<hr>
<div id="show"></div>

```



**getElementsByTagName()**

```


```



## dom element

### 常用方法



appendChild(node)

```
   <script>
        window.onload = function () {
            // appendChild()
            var ul = document.getElementById("hobbies");
            // 创建 <li></li>
            var ul_li = document.createElement("li");
            // 创建 文本内容节点 computer game
            var li_text = document.createTextNode("computer game");
            ul_li.appendChild(li_text);
            ul.appendChild(ul_li);

        }

    </script>
</head>
<body>
<ul id="hobbies">
    <li>music</li>
    <li>football</li>
    <li>basketball</li>
  <!-- 通过js 实现 添加该元素 <li>computer game</li>-->
</ul>

```



removeChild()

```
   <script>
        window.onload = function () {
            // appendChild()
            var ul = document.getElementById("hobbies");
            var ps = document.getElementsByTagName("li");
            console.log(ps.length);
            var childNode =ps[2];
            console.log(childNode);
            ul.removeChild(childNode);

        }

    </script>
</head>
<body>
<ul id="hobbies">
    <li>music</li>
    <li>football</li>
    <!--想要删除 basketball 节点-->
    <li id="bb">basketball</li>
</ul>

```



cloneNode()

```
  <script>
        window.onload = function () {
            var yourLiNodes = document.getElementById("yourNode").getElementsByTagName("li");
            // 克隆元素对象
            var newNode = yourLiNodes[2].cloneNode(true);

            var myUlNode = document.getElementById("myNode");
            myUlNode.appendChild(newNode);
        }

    </script>
</head>
<body>
<ul id="yourNode">
    你的爱好：
    <li>music</li>
    <li>football</li>
    <li>basketball</li>
</ul>

<ul id="myNode">
    我的爱好：
    <li>music</li>
    <li>football</li>
   <!-- <li>basketball</li>-->
</ul>

```



replaceChild(newChlid, oldChild)

```
  <script>
        window.onload = function () {
            var myNode = document.getElementById("myNode");
          var liNodes = myNode.getElementsByTagName("li");
          // 修改最后一个li元素
         var lastLiNode = liNodes[liNodes.length-1];
         // 创建一个新的节点
          var newLiNode = document.createElement("li");
          var newTextNode = document.createTextNode("basketball");
          newLiNode.appendChild(newTextNode);
          // 使用新的节点替换旧的节点
            myNode.replaceChild(newLiNode,lastLiNode);

        }

    </script>
</head>
<body>
<ul id="myNode">
    我的爱好：
    <li>music</li>
    <!-- football 修改成 basketball -->
    <li>football</li>

</ul>

```



fatherNode.insertBefore(newNode,targetNode)

```
 <script>
        window.onload = function () {
            // 创建 <li>basketball</li> 节点
            var newLiNode = document.createElement("li");
            var textNode = document.createTextNode("basketball");
            newLiNode.appendChild(textNode);

            var myNode = document.getElementById("myNode");
            var liNodes = myNode.getElementsByTagName("li");
            var LastLiNode = liNodes[liNodes.length-1];
            
            // 在目标位置之前插入(myNode 和 newLiNode,LastLiNode 是父子关系)
            myNode.insertBefore(newLiNode,LastLiNode);
        }

    </script>
</head>
<body>
<ul id="myNode">
    我的爱好：
    <li>music</li>
    <!-- 此处插入 <li>basketball</li> -->
    <li>football</li>
</ul>

```



### 属性

childNodes

```
<script>
        window.onload = function () {
            var myNode = document.getElementById("myNode");
            var children = myNode.childNodes;
            console.log(children);
           /* console.log(children[0]);
            console.log(children[1]);
            console.log(children[2]);
            console.log(children[3]);
            console.log(children[4]);
            console.log(children[5]);
            console.log(children[6]);
*/
            for (var i = 0; i <children.length ; i++) {
                console.log(children[i]);
            }

        }

    </script>
</head>
<body>
<!-- 子节点包含 空元素（比如换行、空格等）-->
<ul id="myNode">
    我的爱好：<li>music</li>
    <li>football</li><li>basketball</li>
</ul>

```



innerHTML

```

```



style

```
   <script>
        window.onload = function () {
            var myNode = document.getElementById("myNode");
            myNode.style.backgroundColor = "pink";
        }

    </script>
<!--    <style>
        #myNode {
            background-color: red;
        }
    </style>-->
</head>
<body>
<!-- 通过js 给ul对象添加样式-->
<ul id="myNode">
    我的爱好：<li>music</li>
    <li>football</li><li>basketball</li>
</ul>

```



nodeName

```
    <script>
        window.onload = function () {
            var myNode = document.getElementById("myNode");
            console.log(myNode.nodeName);
        }

    </script>

</head>
<body>
<ul id="myNode">
    我的爱好：<li>music</li>
    <li>football</li><li>basketball</li>
</ul>

```



节点访问属性

firstChild

lastChild

parentNode

nextSibling

previousSibling



```
  <script>
        window.onload = function () {
           var oUl = document.getElementById("action");
           var display = document.getElementById("display");
           console.log(oUl.firstChild);
           display.innerHTML = "ul 的第一个子节点的文本内容是" + oUl.firstChild.innerHTML +"<br>";
           display.innerHTML += "ul 的最后一个子节点的文本内容是" + oUl.lastChild.innerHTML + "<br>";
           display.innerHTML += "ul 的第一个子节点的兄弟元素的文本内容是" + oUl.firstChild.nextSibling.innerHTML + "<br>";
           display.innerHTML += "ul 的最后一个子节点的前一个兄弟元素的文本内容是" + oUl.lastChild.previousSibling.innerHTML + "<br>";
           display.innerHTML += "ul 的父节点的节点名称是" + oUl.parentNode.nodeName + "<br>";
        }
    </script>

</head>
<body>
<div id="main">
    <ul id="action"><li>music</li><li>football</li><li>basketball</li><li>computer game </li></ul>
    <hr>
    <div id="display">

    </div>

</div>

```





## form 对象













## 属性过滤器

```
 <script>
        $(document).ready(function () {
                $("a[title]").css({
                    "color":"red",
                    "font-size":"30px",
                    "text-decoration":"none"

                });
            $("a[title=first]").css({
                "color":"pink",
                "font-size":"50px",
                "text-decoration":"none"

            });
            $("a[title!=first]").css({
                "color":"green",
                "font-size":"50px",
                "text-decoration":"none"

            });
            $("a[title^=s]").css({
                "font-size":"100px",
                "text-decoration":"none"

            });
            $("a[title$=t]").css({
                "background-color":"yellow",
                "text-decoration":"none"

            });
            $("a[title*=se]").css({
                "background-color":"orange",
                "text-decoration":"none"

            });


        })
    </script>
</head>
<body>
<a href="#" title="first">一</a><br>
<a href="#" >二</a><br>
<a href="#" title="second" >三</a><br>
<a href="#">四</a><br>
<a href="#" title="third">五</a><br>
</body>
</html>
```





## 子元素过滤器

```
 <script>
        $(document).ready(function () {
            $("ul li:first-child").css({
                "color":"red"
            });
            $("ul li:last-child").css({
                "color":"green"
            });
            $("ul li:nth-child(2)").css({
                "color":"blue"
            });
            $("ul li:nth-child(odd)").css({
                "font-size":"30px"
            });
            $("ul li:nth-child(even)").css({
                "background-color":"yellow"
            });
            $("ul li:nth-child(3n)").css({
                "text-decoration":"line-through"
            });

        })
    </script>
</head>
<body>
    <div>
        <ul>
            <li>音乐</li>
            <li>体育</li>
            <li>美术</li>
            <li>数学</li>
        </ul>
    </div>
</body>
```

