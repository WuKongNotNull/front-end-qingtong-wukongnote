# 数组及操作方法

数组就是一组数据的集合，javascript中，数组里面的数据可以是不同类型的。

**定义数组的方法**

```html
//数组对象的创建和赋值
var fruit=new Array(4);
fruit[0]="apple";
fruit[1]="orange";
fruit[2]="peach";
fruit[3]="banana";

//对象的实例创建
var aList = new Array("apple","orange","peach","banana");

//直接量创建
var aList2 = ["apple","orange","peach","banana"];
```

**操作数组中数据的方法**
1、获取数组的长度：aList.length;

```
var aList = [1,2,3,4];
alert(aList.length); // 弹出4
```

2、用下标操作数组的某个数据：aList[0];

```
var aList = [1,2,3,4];
alert(aList[0]); // 弹出1
```

3、join() 将数组成员通过一个分隔符合并成字符串

```
var aList = [1,2,3,4];
alert(aList.join('-')); // 弹出 1-2-3-4
```

4、push() 和 pop() 从数组最后增加成员或删除成员

```
var aList = [1,2,3,4];
aList.push(5);
alert(aList); //弹出1,2,3,4,5
aList.pop();
alert(aList); // 弹出1,2,3,4
```

5、unshift()和 shift() 从数组前面增加成员或删除成员

```
var aList = [1,2,3,4];
aList.unshift(5);
alert(aList); //弹出5,1,2,3,4
aList.shift();
alert(aList); // 弹出1,2,3,4
```

6、reverse() 将数组反转

```
var aList = [1,2,3,4];
aList.reverse();
alert(aList);  // 弹出4,3,2,1
```

7、indexOf() 返回数组中元素第一次出现的索引值

```
var aList = [1,2,3,4,1,3,4];
alert(aList.indexOf(1));
```

8、splice() 在数组中增加或删除成员

```
var aList = [1,2,3,4];
aList.splice(2,1,7,8,9); //从第2个元素开始，删除1个元素，然后在此位置增加'7,8,9'三个元素
alert(aList); //弹出 1,2,7,8,9,4
```

**多维数组**
多维数组指的是数组的成员也是数组的数组。

```
var aList = [[1,2,3],['a','b','c']];

alert(aList[0][1]); //弹出2;
```

**获取元素的第二种方法**
document.getElementsByTagName(''),获取的是一个选择集，不是数组，但是可以用下标的方式操作选择集里面的dom元素。