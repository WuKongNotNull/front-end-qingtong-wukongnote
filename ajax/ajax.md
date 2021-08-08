# Ajax

浏览器中内嵌一个对象 XMLHttpRequest

**常用的属性**

readystate  表示XMLHttpRequest处的状态

0  未初始化

1 准备发送状态

2 已经发送状态

3 正在接收数据  ：客户端（浏览器）已经接收到http响应的头信息，但是消息体还没有完全被接收

4 完全响应状态

responseText  服务器响应过来的文本内容

responseXMl  服务器响应过来的xml格式的内容

status      http的状态码  404  400 500 200

statusText  描述http 状态的代码文本



**常用的事件**

onreadystatechange 事件



**常用的方法**

open（）

```javascript
open("method","url"[,asyncFlag,username,password])
```



send()

setRequestHeader()



**案例一**

example.html

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>example</title>
    <script>
        window.onload = function () {
            var nameObj = document.getElementById("username");
            nameObj.onblur = function () {
                var xmlHttpRequest;
                if(window.XMLHttpRequest){
                    //firefox chrome opera
                    xmlHttpRequest = new XMLHttpRequest();
                    console.log("XMLHttpRequest 对象创建成功");
                }else{
                    // ie
                    xmlHttpRequest = new ActiveXObject("Microsoft.XMlHTTP");
                }

                xmlHttpRequest.open("GET","ajaxServer.jsp",true);
                xmlHttpRequest.send();

                xmlHttpRequest.onreadystatechange = function () {
                    console.log("enter onreadystatechange....");
                    if(xmlHttpRequest.readyState === 4){
                        if(xmlHttpRequest.status === 200){
                            var responseText = xmlHttpRequest.responseText;
                            var displayObj = document.getElementById("display");
                            displayObj.innerHTML = responseText;
                        }
                    }
                }

            }
        }
    </script>
</head>
<body>
<form>
    <input type="text" id="username" name="username">
    <span id="display"></span><br>
    <input type="submit" value="测试">
</form>
</body>
</html>



```



```
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
<head>
    <title>ajaxServer</title>
</head>
<body>
ajax的响应内容
</body>
</html>
```



**案例二**

```
<%--
    在jsp文件中，我们可以在html中嵌套java代码
--%>
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
<head>
    <title>qq注册页面</title>
    <script>
        // 初始化XMLHttpRequest 对象
        window.onload = function () {
            var usernameObj = document.getElementById("username");
            usernameObj.onblur = function () {
                console.log("失去焦点");

                // 创建 XMLHttpRequest 对象
                var xmlHttpRequest;
                if(window.XMLHttpRequest){
                    //firefox chrome opera
                    xmlHttpRequest = new XMLHttpRequest();
                    console.log("XMLHttpRequest 对象创建成功");
                }else{
                    // ie
                    xmlHttpRequest = new ActiveXObject("Microsoft.XMlHTTP");
                }

                // 发送url 和请求参数
                var usernameParam = usernameObj.value;
                console.log("准备设置url 。。。。");
                //  设置url参数
                xmlHttpRequest.open("GET","usernameCheck.jsp?username="+usernameParam,true);
                // 发送请求
                xmlHttpRequest.send();

                // 监听 readystatechange 事件变化
                xmlHttpRequest.onreadystatechange = function () {
                    console.log("进入onreadystatechange ");
                    if(xmlHttpRequest.readyState === 4){
                        if(xmlHttpRequest.status === 200){
                            console.log(" 4  200");
                            // 表示客户端从服务器完全接收数据，并且数据接收成功
                            var message =   xmlHttpRequest.responseText ;
                            var displayObj = document.getElementById("display");
                            displayObj.innerHTML = message;
                        }
                    }
                }





            }


        }

    </script>
</head>
<body>

    <%--注册表单--%>
    <form action="<%=request.getContextPath() %>/MyRegister" method="post" target="_blank">
        <p>用户名：<input type="text" name="username" id="username"></p><span id="display"></span>
        <p>用户密码：<input type="password" name="password"></p>
        <p>邮箱： <input type="email" name="email"></p>
        <p>爱好：
            <input type="checkbox" value="eat" name="hobbies"> 吃
            <input type="checkbox" value="drink" name="hobbies"> 喝
            <input type="checkbox" value="play" name="hobbies"> 玩
            <input type="checkbox" value="game" name="hobbies"> 打游戏
        </p>
        <p><input type="submit" value="注册"></p>


        <p></p>
    </form>

</body>
</html>

```



```
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
<head>
    <title>Title</title>
</head>
<body>
    <%
        // 写java语言
        String username = request.getParameter("username");

        // 和数据库中的用户名进行比较
        // 假设 wukong  存在于数据库中
        if(username.equals("wukong")){
            // 用户名重复，不能使用
            out.println("username is used 用户名已经被使用");
        }else{
            // 用户名不重复，可以使用
            out.println("username can use 用户名没有被使用");
        }

    %>
</body>
</html>
```



**案例三**

