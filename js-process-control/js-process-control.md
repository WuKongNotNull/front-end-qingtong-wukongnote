# 流程控制

## 条件语句

通过条件来控制程序的走向，就需要用到条件语句。

**运算符**
1、算术运算符： +(加)、 -(减)、 *(乘)、 /(除)、 %(求余)
2、赋值运算符：=、 +=、 -=、 *=、 /=、 %=
3、条件运算符：==、===、>、>=、<、<=、!=、&&(而且)、||(或者)、!(否)

**if else**

```
var a = 6;
if(a==1)
{
    alert('语文');
}
else if(a==2)
{
    alert('数学');
}
else if(a==3)
{
    alert('英语');
}
else if(a==4)
{
    alert('美术');
}
else if(a==5)
{
    alert('舞蹈');
}
else
{
    alert('不补习');
}
```

**switch**

```
var a = 6;

switch (a){
    case 1:
        alert('语文');
        break;
    case 2:
        alert('数学');
        break;
    case 3:
        alert('英语');
        break;
    case 4:
        alert('美术');
        break;
    case 5:
        alert('舞蹈');
        break;
    default:
        alert('不补习');
}
```



## 循环语句

程序中进行有规律的重复性操作，需要用到循环语句。

**for循环**

```
for(var i=0;i<len;i++)
{
    ......
}
```

**while循环**

```
var i=0;

while(i<8){

    ......

    i++;

}
```

**数组去重**

```
var aList = [1,2,3,4,4,3,2,1,2,3,4,5,6,5,5,3,3,4,2,1];

var aList2 = [];

for(var i=0;i<aList.length;i++)
{
    if(aList.indexOf(aList[i])==i)
    {
        aList2.push(aList[i]);
    }
}

alert(aList2);
```

## 

