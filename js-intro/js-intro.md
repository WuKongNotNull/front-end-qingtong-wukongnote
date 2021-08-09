# JavaScript 概述

JavaScript是运行在浏览器的一种基于对象和事件驱动的并具有安全性能的脚本语言。

**JavaScript特点**

- 向HTML页面中添加交互行为
- 脚本语言，语法与Java类似
- 解释性语言，边执行边解释

**前端三大块**
1、HTML：页面结构
2、CSS：页面表现：元素大小、颜色、位置、隐藏或显示、部分动画效果
3、JavaScript：页面行为：部分动画效果、页面与用户的交互、页面功能

**标签<script>**

该标签可以包含在文档中的任何地方，只要保证这些代码在被使用前已读取并加载到内存中即可。代码如下

```html
<script type="text/javascript">
	  document.write("hello,JavaScript");
    document.write("<h1>hello ,JavaScript</h1>");
</script>
```



## JavaScript嵌入页面的方式

1、行间事件（主要用于事件）

```html
<input type="button" name="" onclick="javascript:alert('ok！');">
```

2、页面script标签嵌入

```html
<script type="text/javascript">        
    var a = '你好！';
    alert(a);
</script>
```

3、外部引入

```html
<script type="text/javascript" src="js/index.js"></script>
```



