## 面向对象

**面向过程与面向对象编程**

1、面向过程：所有的工作都是现写现用。

2、面向对象：是一种编程思想，许多功能事先已经编写好了，在使用时，只需要关注功能的运用，而不需要这个功能的具体实现过程。

**javascript对象**
将相关的变量和函数组合成一个整体，这个整体叫做对象，对象中的变量叫做属性，变量中的函数叫做方法。javascript中的对象类似字典。

**创建对象的方法**
1、单体

```html
<script type="text/javascript">
var Tom = {
    name : 'tom',
    age : 18,
    showname : function(){
        alert('我的名字叫'+this.name);    
    },
    showage : function(){
        alert('我今年'+this.age+'岁');    
    }
}
</script>
```

```html
<!DOCTYPE html>
<html>
<head lang="en">
    <meta charset="UTF-8">
    <title>另一种创建对象的方法</title>
</head>
<body>
<script>
    var flower=new Object();
    flower.name="长春花";
    flower.genera="夹竹桃科 长春花属";
    flower.area="非洲";
    flower.uses="观赏或用药";
    flower.showName=function(){
        alert(this.name);
    }
    flower.showName();
</script>
</body>
</html>
```



2、工厂模式

```
<script type="text/javascript">

function Person(name,age,job){
    var o = new Object();
    o.name = name;
    o.age = age;
    o.job = job;
    o.showname = function(){
        alert('我的名字叫'+this.name);    
    };
    o.showage = function(){
        alert('我今年'+this.age+'岁');    
    };
    o.showjob = function(){
        alert('我的工作是'+this.job);    
    };
    return o;
}
var tom = Person('tom',18,'程序员');
tom.showname();

</script>
```

2、构造函数

```
<script type="text/javascript">
    function Person(name,age,job){            
        this.name = name;
        this.age = age;
        this.job = job;
        this.showname = function(){
            alert('我的名字叫'+this.name);    
        };
        this.showage = function(){
            alert('我今年'+this.age+'岁');    
        };
        this.showjob = function(){
            alert('我的工作是'+this.job);    
        };
    }
    var tom = new Person('tom',18,'程序员');
    var jack = new Person('jack',19,'销售');
    alert(tom.showjob==jack.showjob);
</script>
```

3、原型模式

```
<script type="text/javascript">
    function Person(name,age,job){        
        this.name = name;
        this.age = age;
        this.job = job;
    }
    Person.prototype.showname = function(){
        alert('我的名字叫'+this.name);    
    };
    Person.prototype.showage = function(){
        alert('我今年'+this.age+'岁');    
    };
    Person.prototype.showjob = function(){
        alert('我的工作是'+this.job);    
    };
    var tom = new Person('tom',18,'程序员');
    var jack = new Person('jack',19,'销售');
    alert(tom.showjob==jack.showjob);
</script>
```

4、继承

```html
<script type="text/javascript">

        function fclass(name,age){
            this.name = name;
            this.age = age;
        }
        fclass.prototype.showname = function(){
            alert(this.name);
        }
        fclass.prototype.showage = function(){
            alert(this.age);
        }
        function sclass(name,age,job)
        {
            fclass.call(this,name,age);
            this.job = job;
        }
        sclass.prototype = new fclass();
        sclass.prototype.showjob = function(){
            alert(this.job);
        }
        var tom = new sclass('tom',19,'全栈工程师');
        tom.showname();
        tom.showage();
        tom.showjob();
    </script>
```

### 构造函数

```html
<!DOCTYPE html>
<html>
<head lang="en">
    <meta charset="UTF-8">
    <title>构造函数</title>
</head>
<body>
<script>
    function Flower(name,genera,area,uses){
        this.name=name;
        this.genera=genera;
        this.area=area;
        this.uses=uses;
        this.showName=function(){
            alert(this.name);
        }
    }
    var flower1=new Flower("长春花","长春花属","非洲","观赏或用药");
    flower1.showName();
    var flower2=new Flower("牡丹","芍药科 芍药属","中国","观赏、食用或药用");
    flower2.showName();
    var flower3=new Flower("曼陀罗花","茄科 曼陀罗属","印度、中国北部","观赏或药用");
    flower3.showName();
    //alert(flower1.constructor==Flower);
    //alert(flower2.constructor==Flower);
   // alert(flower2.constructor==Flower);
    alert(flower1 instanceof Object);
    alert(flower1 instanceof Flower);
    alert(flower2 instanceof Object);
    alert(flower2 instanceof Flower);
    alert(flower3 instanceof Object);
    alert(flower3 instanceof Flower);
</script>
</body>
</html>
```



### 构造函数优化

```html
<!DOCTYPE html>
<html>
<head lang="en">
    <meta charset="UTF-8">
    <title>构造函数</title>
</head>
<body>
<script>
    function Flower(name,genera,area,uses){
        this.name=name;
        this.genera=genera;
        this.area=area;
        this.uses=uses;
        this.showName=showName;
    }
    function showName(){
        alert(this.name);
    }
    var flower1=new Flower("长春花","夹竹桃科 长春花属","非洲、亚热带、热带以及中国大陆的华东、西南、中南等地","观赏或用药等");
    var flower2=new Flower("牡丹","芍药科 芍药属","中国","观赏、食用或药用");
    var flower3=new Flower("曼陀罗花","茄科 曼陀罗属","印度、中国北部","观赏或药用");
    flower1.showName();
    flower2.showName();
    flower3.showName();
    alert(flower1 instanceof Object);
    alert(flower1 instanceof Flower);
    alert(flower2 instanceof Object);
    alert(flower2 instanceof Flower);
    alert(flower3 instanceof Object);
    alert(flower3 instanceof Flower);
    alert(flower1.constructor==Flower);
    alert(flower2.constructor==Flower);
    alert(flower3.constructor==Flower);
</script>
</body>
</html>
```



### 原型对象

```html
<!DOCTYPE html>
<html>
<head lang="en">
    <meta charset="UTF-8">
    <title>原型对象</title>
</head>
<body>
<script>
    function Flower(){

    }
    Flower.prototype.name="曼陀罗花";
    Flower.prototype.genera="茄科 曼陀罗属";
    Flower.prototype.area="印度、中国北部";
    Flower.prototype.uses="观赏或药用";
    Flower.prototype.showName=function() {
        alert(this.name);
    }
    /*var flower1=new Flower();
    flower1.showName();
    var flower2=new Flower();
    flower2.showName();
    alert(flower1.showName==flower2.showName);*/
    var flower1=new Flower();
    var flower2=new Flower();
    flower1.name="长春花";
    alert(flower1.name);
    alert(flower2.name);

</script>
</body>
</html>
```



### 原型链

```html
<!DOCTYPE html>
<html>
<head lang="en">
    <meta charset="UTF-8">
    <title>原型链</title>
</head>
<body>
<script>
    function Humans(){
        this.foot=2;
    }
    Humans.prototype.getFoot=function(){
       return this.foot;
    }
    function Man(){
        this.head=1;
    }
    Man.prototype=new Humans();
    Man.prototype.getHead=function(){
        return this.head;
    }
    var man1=new Man();
    alert(man1.getFoot());
    alert(man1.getHead());
    alert(man1 instanceof Object);
    alert(man1 instanceof Humans);
    alert(man1 instanceof Man);
</script>
</body>
</html>
```



### 给原型添加方法

```html
<!DOCTYPE html>
<html>
<head lang="en">
    <meta charset="UTF-8">
    <title>给原型添加方法</title>
</head>
<body>
<script>
    function Humans(){
        this.foot=2;
    }
    Humans.prototype.getFoot=function(){
        return this.foot;
    }
    function Man(){
        this.head=1;
    }
    //继承了Humans
    Man.prototype=new Humans();
    //添加新方法
    Man.prototype.getHead=function(){
        return this.head;
    }
    //重写父类型中的方法
    Man.prototype.getFoot=function(){
        return false;
    }
    var man1=new Man();
    alert(man1.getFoot());    //false
</script>
</body>
</html>
```



### 原型链的问题

```html
<!DOCTYPE html>
<html>
<head lang="en">
    <meta charset="UTF-8">
    <title>原型链的问题</title>
</head>
<body>
<script>
    function Humans(){
        this.clothing=["trousers","dress","jacket"];
    }
    function Man(){
     }
    //继承了Humans
    Man.prototype=new Humans();
    var man1=new Man();
    man1.clothing.push("coat");
    alert(man1.clothing);
    var man2=new Man();
    alert(man2.clothing);
</script>
</body>
</html>
```



### 借用构造函数

```html
<!DOCTYPE html>
<html>
<head lang="en">
    <meta charset="UTF-8">
    <title>借用构造函数</title>
</head>
<body>
<script>
    function Humans(){
        this.clothing=["trousers","dress","jacket"];
    }
    function Man(){
        Humans.call(this);   //继承了Humans
    }
    var man1=new Man();
    man1.clothing.push("coat");
    alert(man1.clothing);
    var man2=new Man();
    alert(man2.clothing);
</script>
</body>
</html>
```



### 借用构造函数传递参数

```html
<!DOCTYPE html>
<html>
<head lang="en">
    <meta charset="UTF-8">
    <title>借用构造函数传递参数</title>
</head>
<body>
<script>
    function Humans(name){
        this.name=name;
    }
    function Man(){
        Humans.call(this,"mary");   //继承了Humans,同时还传递了参数
        this.age=38;                //实例属性
    }
    var man1=new Man();
    alert(man1.name);
    alert(man1.age);
</script>
</body>
</html>
```





### 组合继承

```html
<!DOCTYPE html>
<html>
<head lang="en">
    <meta charset="UTF-8">
    <title>组合继承</title>
</head>
<body>
<script>
    function Humans(name){
        this.name=name;
        this.clothing=["trousers","dress","jacket"];
    }
    Humans.prototype.sayName=function(){
        alert(this.name);
    };
    function Man(name,age){
        Humans.call(this,name);    //继承属性
        this.age=age;
    }
    Man.prototype=new Humans();    //继承方法
    Man.prototype.sayAge=function(){
        alert(this.age);
    };

    var man1=new Man("mary",38);
    man1.clothing.push("coat");
    alert(man1.clothing);     //输出"trousers,dress,jacket,coat"
    man1.sayName();            //输出mary
    man1.sayAge();            //输出38
    var man2=new Man("tom",26);
    alert(man2.clothing);    //输出"trousers,dress,jacket"
    man2.sayName();            //输出tom
    man2.sayAge();            //输出26
</script>
</body>
</html>
```

### 