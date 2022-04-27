 

# JS笔记

***



### js组成部分

1.ECMAscript：语法规范 定义变量
2.DOM Document Object Model 文档对象模型
3.BOM Browser Object Model 浏览器对象模型

### 注释

```js
*/ 多行 /* 
//alt + shift + a
```

### 变量交换

```js
var w1 = 10;
var w2 = 20;
w1 = w1 + w2;
w2 = w1 - w2;
w1 = w1 - w2;
console.log(w1,w2);
```

### 获取数据变量（返回字符串）

```js
typeof num//推荐
typeof (num)
```

### 五个数据类型（特殊：typeof null检测到的类型市object）

| 数值型（整数+小数） |  number   |
| :-----------------: | :-------: |
|       字符型        |  string   |
|       布尔型        |  boolean  |
|         空          |   null    |
|       未定义        | undefined |

### null的特殊用法

```js
定义一个变量一开始是会一个null，有些人用定时器一开始就var timeId = null;
//工作里面总结的一句话
null：一开始没有，以后会有
undefined：一开始没有，以后也没有
```

### 复合数据类型（复杂数据类型，引用数据类型）（特殊：typeof function返回的市function，其他都是object）

|        对象        |        Object         |
| :----------------: | :-------------------: |
|        函数        |       Function        |
|        日期        |         Date          |
|        数组        |         Array         |
| 扩展：基本包装类型 | String,Number,Boolean |

### 引用类型判断相等==，因为地址不同所以不相等

```js
var str1 = [1, 2, 3];
var str2 = [1, 2, 3];
console.log(str1 == str2);//false
console.log(str1 === str2);//false
```

### null因为历史遗留问题，为特殊数据object

```js
var nll = null;
console.log(typeof nll);
```

### 面试题1：NaN    (not  a  number不是个数字)

```js
var num;
console.log(num);//undefined
console.log(num + 10);//NaN
```

### 面试题2：不要拿小数相加，不要用小数验证小数

```js
var x = 0.1;
var y = 0.2;
var sum = x + y;
console.log(sum);//0.30000000000000004
console.log(sum == 0.3);//false
```

### 面试题3：不要用NaN验证是否是不是NaN

```js
var age;
console.log(age + 10 == NaN);//false
```

### 如何验证NaN   isNaN() ：是不是不是一个数字

```js
var num;
console.log(isNaN(num));//true
```

### 逻辑与  &&  和逻辑或  ||

```js
console.log(0 && 0);//0
console.log(0 && 1);//0
console.log(1 && 0);//0
console.log(1 && 2);//2
console.log(2 && 3);//3
//与：如果表达式1为真，则返回表达式2的值，如果表达式2的值为假，则返回表达式1的值
console.log(0 || 0);//0
console.log(0 || 1);//1
console.log(1 || 0);//1
console.log(1 || 2);//1
console.log(2 || 3);//2
//或：如果表达式1为真，则返回表达式1的值，如果表达式1的值为假，则返回表达式2的值
```

### 复制光标这行到下一行快捷键

```js
alt + shift + 向下键
```

### 比较常用的转义字符 \t ,\n,\\",\\'

```js
\t:tab键
\n:换行
\:想打"或'时
```

### 隐式转换 - * / %

```js
var age1 = 10;
var age2 = "5";
var age3 = 5;
console.log(age1 - age2);//5
console.log(age1 * age2);//50
console.log(age1 / age2);//2
console.log(age1 % age2);//0
console.log(age2 == age3);//true,只比较值，不比较类型
console.log(age2 === age3);//flase,值和类型都比较
```

### 类型的颜色

```js
字符串-黑色  数字和布尔-蓝色  null和undefined-黑色
```

### parseInt()---转换为整数，从左往右转换，如果遇到字母立马停止转换

```js
console.log("fddv10bacfdsv");//fddv10bacfdsv
console.log(parseInt("fddv10bacfdsv"));//NaN
console.log(parseInt("10fddvbacfdsv"));//10
console.log(parseInt("10.98fddvbacfdsv"));//10
```

### parseFloat()---转换为小数

```js
console.log("fddv10bacfdsv");//fddv10bacfdsv
console.log(parseFloat("fddv10bacfdsv"));//NaN
console.log(parseFloat("10fddvbacfdsv"));//10
console.log(parseFloat("10.98fddvbacfdsv"));//10.98
```

### Number()---判断是否为数字，再输出

```js
console.log("fddv10bacfdsv");//fddv10bacfdsv
console.log(Number("fddv10bacfdsv"));//NaN
console.log(Number("10fddvbacfdsv"));//NaN
console.log(Number("10.98fddvbacfdsv"));//NaN
console.log(Number("10.98"));//10.98
```

### .toString---转为字符串

```js
var num = 10;
console.log(num);//蓝色的10
console.log(num.toString);//黑色的10
```



```js
var nll = null;
console.log(num.toString);//报错，无法转换
```



```js
var un;//undefined
console.log(num.toString);//报错，无法转换
```

### String()---转换为字符串，特殊作用为可以转换null和undefined

```js
var nll = null;
console.log(String(num));//null
```



```js
var un;//undefined
console.log(String(num));//undefined
```

### Boolean()---结果就两种，要么true，要么false，为false的只有五种可能：0，null，undefined，“”，NaN

```js
var str = "小明"；
var num = 18;
var nll = null;
var aa;
console.log(Boolean(str));//true
console.log(Boolean(num));//ture
console.log(Boolean(null));//false
console.log(Boolean(aa));//false
console.log(Boolean(1));//ture
console.log(Boolean(0));//false
console.log(Boolean(-1));//ture
```

### 字符类型加上正和负会自动转换为数值类型，如果字符类型中有不是数字的字符，会返回NaN

```js
var str = "18";
console.log(+str);//蓝色的18
console.log(-str);//蓝色的-18

var str1 = "18abc";
console.log(+str);//NaN
console.log(-str);//NaN

console.log(str - 0);//18
console.log(str1 - 0);//NaN
console.log(str + 0);//18abc0
```

### 弹窗输入

```js
var age = prompt("请输入您的年龄");
```

### 三元运算符

```js
var age = 18;
var result = age >= 18 ? "成年了" : "未成年";
console.log(result);//成年了
```

### switch~case（判断一个值的时候用）

```js
var num = parseInt(prompt("输入数字"))
switch (num) {
    case "1":
        console.log("星期一");
        break;
    case "2":
        console.log("星期二");
        break;
    case "3":
        console.log("星期三");
        break;
    case "4":
        console.log("星期四");
        break;
    case "5":
        console.log("星期五");
        break;
    case "6":
        console.log("星期六");
        break;
    case "7":
        console.log("星期日");
        break;
    default:
        console.log("你输入的超出范围了喔");
        break;
}
```

### 输出在界面，用js写入运行后的界面

```js
document.write("我好帅");
```

### break和continue

```js
break;//直接终止循环
continue;//直接跳出此次循环，跳到下一次循环
```

### 反转数组，数组名不能为name，原因是name特殊，在赋值的时候浏览器强制转成了string。

```js
var array = [1, 2, 3, 4, 5, 6, 7, 8, 9];
for (var i = 0; i <= array.length / 2; i++) {
    var temp = array[array.length - 1 - i];
    array[array.length - 1 - i] = array[i];
    array[i] = temp;
}
console.log(array);
```

### 函数

```js
function fun(形参) {
    var sum = x + y;
    return sum;
}
var result = fun(实参);
console.log(result + 39);
```

## 实参和形参个数不一致

### 第一种情况，实参大于形参，多的实参不调用

```js
function Sum(x, y) {
    return x + y;
}
console.log(Sum(10, 20, 30));//30
```

### 第二种情况，形参大于实参，多的形参没有赋值=undifined，数字 + undifined = NaN

```js
function Sum1(x, y, z) {
    return x + y + z;
}
console.log(Sum1(10, 10));//NaN
```

### 如果函数没有返回值，默认返回undifined

```js
function fun1(x, y) {
    var result = x + y;
}
console.log(fun1(1, 2));//undifined
```

### 如果函数有返回值return，默认一样返回undifined

```js
function fun2(x, y) {
    var result = x + y;
    return;
}
console.log(fun2(1, 2));//undifined
```

### return后面的值都不会执行

```js
function getsum(x,y){
     return x + y;
     console.log("我好帅");
}
console.log(getsum(10,20));
```

### 用圆周率PI求圆的面积

```js
function C(r) {
    return Math.PI * r * r;
}
console.log(C(10));
```

### 匿名函数

```js
var f = function (){
     console.log("f相当于一个函数名字");
}
f();
```

### 函数自调用（函数自己调用自己）

```js
(function(){
  console.log("函数自调用")
 })()
```

### 伪元素（不需要形参了，优化代码）伪数组

```js
function fun1() {
    var sum = 0;
    for (let i = 0; i < arguments.length; i++) {
        sum += arguments[i];
    }
    return sum;
}
console.log(fun1(10, 20, 30, 40));
```

### 判断是否是闰年

```js
function fun(){
     return year % 4 == 0 && year % 100 != 0 || year % 400 == 0;
}
```

### 斐波那契数列，一年有多少个兔子

```js
var num1 = 1;
var num2 = 1;
var sum = 0;
for (var i = 3; i <= 12; i++) {
    sum = num1 + num2;
    num1 = num2;
    num2 = sum;
}
console.log(sum);
```

### 全局变量中this指向window

```js
console.log(this);//window
```

### 普通函数里面this指向window

```js
function fun() {
    console.log(this);
}
fun();//window
```

### 变量提升，当网页一打开，首先浏览器会先遍历一遍代码，浏览器会把带var和function 提前声明

```js
//第一，如果是var浏览器会先提前声明 var age；只声明，不去赋值，默认的结果underfined
//第二，变量提升，只提升等号左边的，不会提升等号右面的
//第三，如果是function会声明加定义，会把整个function函数提升到代码前面
```

```js
//变量提升-示例1
console.log(a);//undefined
var a = 123;
console.log(a);//123
function f(){
     console.log(a);undefined
     var a = 456;
     console.log(a);//456
}
f();
console.log(a);

//伪代码
var a;
a = 123;
console.log(a);//123
function f(){
     var a;
     console.log(a);//undefined
     a = 456;
     console.log(a);//456
}
f();
console.log(a);//123

//示例二
var foo = 1;
function fun(){
     if(!foo){
          var foo = 10;
     }
     console.log(foo);//10
}
fun();

//伪函数
var foo = 1;
function fun(){
     var foo;
     if(!foo){
          foo = 10j;
     }
     console.log(foo);//10
}
fun();

//示例三
console.log(a,b,c);//undefined undefined undefined
var a = 10,b = 20, c = 30;
function fun(a){
     console.log(a,b,c);//10 undefined 30
     var b = a = c =100;
     console.log(a,b,c);//100 100 100
}
fun(10,20);
console.log(a,b,c);//10 20 100

//伪代码
var a;
var b;
var c;
console.log(a,b,c);//undefined undefined undefined
var a = 10,b = 20, c = 30;
function fun(a){
     var b;
     console.log(a,b,c);//10 undefined 30
     b = a = c = 100;
     console.log(a,b,c);//100 100 100
}
fun(10,20);
console.log(a,b,c);//10 20 100
```

### 内置对象一

```js
//内置对象（系统自带的），后面会学习浏览器对象BOM，自定义构造函数对象（new一下就会有对象了---面向对象里面会详细讲解）
//内置对象：Math，Date，Arr，String···
Math.PI//派
Math.max()//最大值
Math.min()//最小值
Math.abs()//绝对值
Math.random()//随机获取 0 到 1 之间的随机数，[0,1)
Math.ceil(12.5)//13   向上取整
Math.floor(12.5)//12   向下取整
Math.pow(2,4)//16   求知数次幂
Math.sqrt(16)//4   求平方根
Math.round(10.98)//11   小数四舍五入
```

### 随机点名

```js
var names = ["wyf","zwh","myl","hjh"];
console.log(names[parseInt(Math.random() * names.length)]);
```

### 内置对象二

```js
function da(dt) {
    var y = dt.getFullYear(); //获取年
    var m = dt.getMonth() + 1; //我们的月是从0开始的，所以要加1
    var d = dt.getDate(); //获取日期
    var h = dt.getHours(); //获取小时
    var min = dt.getMinutes(); //获取分钟
    var sec = dt.getSeconds(); //获取秒
    var week = dt.getDay(); //获取星期几
    switch (week) {
        case 1:
            week = "星期一";
            break;
        case 2:
            week = "星期二";
            break;
        case 3:
            week = "星期三";
            break;
        case 4:
            week = "星期四";
            break;
        case 5:
            week = "星期五";
            break;
        case 6:
            week = "星期六";
            break;
        case 0:
            week = "星期天";
            break;
    }
    m = m < 10 ? "0" + m : m;
    d = d < 10 ? "0" + d : d;
    h = h < 10 ? "0" + h : h;
    min = min < 10 ? "0" + min : min;
    sec = sec < 10 ? "0" + sec : sec;
    return y + "年" + m + "月" + d + "日" + h + "小时" +
        min + "分钟" + sec + "秒" + week;
}
var dt = new Date(); //获取系统日期
console.log(da(dt));
```

- 封装一个获取时间的方法

  ```js
  function getTime() {
       var d = new Date();
       var vYear = d.getFullYear()
       var vMon = d.getMonth() + 1
       var vDay = d.getDate();
       var h = d.getHours();
       var m = d.getMinutes();
       var se = d.getSeconds();
       s = vYear + "/" + (vMon < 10 ? "0" + vMon : vMon) + "/" + (vDay < 10 ? "0" + vDay : vDay) + " " + (h < 10 ? "0" + h : h) + ":" + (m < 10 ? "0" + m : m) + ":" + (se < 10 ? "0" + se : se);
       return s;
  }
  ```

  

### 随机取颜色 #xxxxxx

```js
function getColor() {
    var str = "#";
    var arr = ["1", "2", "3", "4", "5", "6", "7", "8", "9", "a", "b", "c", "d", "e", "f", "g"];
    for (let i = 0; i < 6; i++) {
        str += arr[parseInt(Math.random() * arr.length)];
    }
    return str;
}
console.log(getColor());
```

### 当页面加载时运行---入口函数

```js
window.onload = function() {
}
```

```js
//获取id改div的背景颜色
window.onload = function() { document.getElementById("color").style.backgroundColor = getColor();//利用
}
```

```js
document --- 文档
get --- 获取
Element --- 元素
By --- 通过
Id --- 页面的id
```

### 获取数组索引的值  .chatAt()

```js
var str = "wyfhaoshuai";
console.log(str.chatAt(10));
```

### 内置对象二

```js
//.charAt();获取索引所在位置的字符
var str = "fjdksovhwiorfvsioajdfiosghviowjfidopafjpioqafjw"
console.log(str.charAt(11));

//.String.fromCharCode()获取ascll码中对应的值
var word = String.fromCharCode(65, 66, 67);
console.log(word);
var sos = String.fromCharCode(83, 79, 83);
console.log(sos);

//.concat()返回拼接之后的字符串
var str5 = "我们";
var str6 = str5.concat("wyf", "hao", "shuai");
console.log(str6); //我们wyfhaoshuai

//.indexOf("想找的字符串"，从哪里开始找)  返回想找的字符串的索引，获得下标,如果没找到就返回-1
var str10 = "不是吧你别在这里吵了";
var index = str10.indexOf("吵", 8);
console.log(index); //8

//.lastIndexOf("想找的字符串")  返回想找的字符串的最后一个的索引
var str10 = "不是吵吧你别在这里吵了";
var index = str10.lastIndexOf("吵");
console.log(index); //9

//.replace("替换目标"，"替换对象")  替换字符串
var str11 = "wyf好帅，是一个靓仔";
str12 = str11.replace("帅", "靓");
console.log(str12); //wyf好靓，是一个靓仔

//.slice(开始的索引值，结束的索引值（不包括）)提取两个索引之间的字符
var str13 = "你开玩笑是吧不要这样";
var str14 = str13.slice(4, 7);
var str15 = str13.slice(4); //把剩下的所有都提取
console.log(str14);

//.splice(n,m,x,y,z)  把数组从索引n开始删除m个元素，用x,y,z代替删除的m项，返回值是被删的数组，原来的数组已经改变(备注：增删改除)
//.splice(当前的索引值,元素个数,新的元素)
var str22 = [1, 2, 3, 4, 5, 6];
var str23 = str22.splice(2, 2, 7, 8, 9);
console.log(str23);//3,4
console.log(str22);//1,2,7,8,9,5,6
//扩展1，当m是0的时候，他是把x,y,z..添加到索引n的前面
var str24 = [1, 2, 3, 4, 5, 6];
var str25 = str24.splice(2, 0, 7, 8, 9);
console.log(str24);//1,2,7,8,9,3,4,5,6
//扩展2，没有xyz，相当于直接删除m项
var str26 = [1, 2, 3, 4, 5, 6];
var str27 = str26.splice(2, 2);
console.log(str26);//1,2,5,6
//扩展3，当什么都没写，返回空数组
var str30 = [1, 2, 3, 4, 5, 6];
var str31 = str30.splice();
console.log(str31);//[]
console.log(str30);//1,2,3,4,5,6
//扩展3，当.splice(0)是，相当于删除整个数组
var str28 = [1, 2, 3, 4, 5, 6];
var str29 = str28.splice(0);
console.log(str29);//1,2,3,4,5,6
console.log(str28);//[]

//.split("22","拆分后留下的字符串个数")  以规定字符拆分字符串形成数组
var str16 = "w|y|f|h|a|o";
var str17 = str16.split("|");
console.log(str17); //["w", "y", "f", "h", "a", "o"]

//.substr("开始位置","截取个数")   返回截取后的字符，个数可以省略
var str18 = "我们都是靓仔，靓妹";
var str19 = str18.substr(4, 2);
console.log(str19);//靓仔

//.substring("开始位置","结束的位置（不包含）")  返回截取后的字符
var str20 = "我们都是靓仔，靓妹";
var str21 = str20.substring(4, 6);
console.log(str21);//靓仔

//.toLocaleLowerCase()  转换成小写字母
//.toLowerCase()  转换成小写字母
var str1 = "LIVE ME";
console.log(str1.toLocaleLowerCase());
console.log(str1.toLowerCase());

//.toLocaleUpperCase()  转换成大写字母
//.toLowerCase()  转换成大写字母
var str2 = "live me";
console.log(str2.toLocaleUpperCase());
console.log(str2.toUpperCase());

//.trim()  删除两端的空格，中间的空格删不了
var str3 = "   张文瀚  傻逼   "
console.log(str3.trim());
```

### 作业

```js
//找其中的字符串
var str4 = "张文瀚unglyfulishstupid";
var index = str4.indexOf("张文瀚");
console.log(index);//0
console.log(str4.substr(index, 3));//张文瀚

//找字符串中所有想找到字符的index
var str5 = "jhkgfldsjghdlsjghdlsjghdlslfjkghdksjfhg";
var index1 = 0;
var key = "j";
while ((index1 = str5.indexOf(key, index1)) != -1) {
    console.log(index1);
    index1 += key.length;
}
```

### 数组

```js
//第一种
var arr1 = [1,2,3,4,5];
//第二种--内置构造函数方式new来创建
var arr2 = new Array(1,2,3,4,5);

//第一种和第二种的区别
var arr3 = [6];
console.log(arr1.length);//1
var arr4 = new Array(6);//创建对象，只写一个数字在，就表示有这么多个数字的空字符
console.log(arr4.length);//6
console.log(arr4);//empty*6
```

### 判断数组的方式

```js
// instanceof 判断这个对象是否是数组，如果是为ture，如果不是为false
var arr1 = [];
console.log(arr1 instanceof array);//ture
var arr2 = 10;
console.log(arr2 instanceof array);//false

// isArray
var arr3 = [];
console.log(Array.isArray(arr3));//ture
```

### 内置对象三

```js
//.push(值1，值2...)  给数组后面添加元素，返回值为数组的长度
var arr1 = [1,2,3,4,5];
var result1 = arr1.push(100,200);
console.log(result1,arr1);//1,2,3,4,5,100,200

//.unshift(值1，值2...)  给数组前面添加元素
var arr2 = [1,2,3,4,5];
var result2 = arr2.unshift(100,200);
console.log(result2,arr2);//100,200,1,2,3,4,5

//.pop()  删除数组的最后一项，返回值是删除的那一项
var arr3 = [1,2,3,4,5];
var result3 = arr3.pop();
console.log(result3,arr3);//1,2,3,4

//.shift()  删除数组的第一项，返回值是删除的那一项
var arr4 = [1,2,3,4,5];
var result4 = arr4.shift();
console.log(result4,arr4);//2,3,4,5

//.reverse()  数组反转
var arr5 = [1,2,3,4,5];
var result5 = arr5.reverse();
console.log(result5);//5,4,3,2,1

//.sort()  数组排序，只能排序10以内的数字
var arr6 = [3,6,3,7,8,1,2];
var result6 = arr6.sort();
console.log(result6);//1, 2, 3, 3, 6, 7, 8

//.sort(dunction(a,b){a - b})  数字如果超过10，用“回调函数”，如果是b-a就是从大到小
var arr7 = [1,100,232,45,65,4,87];
var result7 = arr7.sort(function(a,b){
     return a - b;
})//1, 4, 45, 65, 87, 100, 232
```

## DOM Document Object Model 文档对象模型

### 入口函数：<u>单独  js  文件</u>   或   <u>script在body上面</u>    对文档处理需要加载页面

```js
window.onload = function() {
    //文档处理内容
}
```

### 鼠标事件

```js
onclick//单击
ondblclick//双击
onmouseover//经过
onmouseout//离开
```

### 改img的图片 ，动作在控件里面

```html
<img src = "./图片2.jpg" id="i"></img>
<button onclick = "img()"></button>//

```

```js
function img(){
     document.getElementById("i").src("./图片1.jpg");
}
```

### 动作在js里

```html
<button class="d" id="btn"></button>
```

```js
window.onload = function() {
    var btn = document.getElementById("btn");
    btn.onclick = function() {//
        alert("好啊");
    }
}
```

###   获取text的内容

```js
p.innerText = "好啊";
```

### 获取多个相同标签，把这多个标签变成集合（伪数组）（例子为p标签）

```js
var pObjs = document.getElementsByTagName("p");
console.log(pObjs);//p, p, p, p, p, p
for (var i = 0; i < pObjs.length; i++) {
    pObjs[i].innerText = "傻了吧";
}
```

### 修改a标签的href

```js
var aObj = document.getElementById("a");
aObj.href = "https://app.mockplus.cn/team/pwajjstnyc";
```

### 隐藏和显示图片

```html
<div>
     <input type="button" value="隐藏" id="dis1">
     <input type="button" value="显示" id="dis2">
</div>
<div id="i">
     <img src="./pic/光.jpg" alt="" id="img">
</div>
```

```js
var dis1 = document.getElementById("dis1");
var dis2 = document.getElementById("dis2");
var i = document.getElementById("i");
dis1.onclick = function() {
     i.style.display = "none";//隐藏
}
dis2.onclick = function() {
     i.style.display = "block";//显示
}
```

### public公用调用函数--my$()

```js
//独立设一个公用js文件
function my$(id){
    	return document.getElementById(id);
}
```

```js
//在独立js文件中调用
my$("html中的id");
```

### 调用<img>的width和height的数据不用加px

```js
wyf$("img").width = "200";
```

### this的用法1

```html
<img src="./pic/昼夜1.jpg" alt="" id="night">
```

```js
wyf$("night").onmouseover = function() {
     this.src = "./pic/昼夜2.jpg";
}
wyf$("night").onmouseout = function() {
     this.src = "./pic/昼夜1.jpg";
}
```

### 排他思想

```html
<input type="button" value="叼啊">
<input type="button" value="叼啊">
<input type="button" value="叼啊">
<input type="button" value="叼啊">
<input type="button" value="叼啊">
<input type="button" value="叼啊">
<input type="button" value="叼啊">
<input type="button" value="叼啊">
<input type="button" value="叼啊">
<input type="button" value="叼啊">
```

```js
var bObjs = document.getElementsByTagName("input");
var bObjsarray = Array.from(bObjs);//可以把集合转化为真正的数组，这里没用到
    for (var i = 0; i < bObjs.length; i++) {
        bObjs[i].onclick = function() { //获取每个按钮点击事件
            for (let j = 0; j < bObjs.length; j++) { //第一件事情
                bObjs[j].value = "叼啊"; //把每个按钮的值改为相同的值
            }
            this.value = "菜啊"; //第二件事情，把自己变单独的值
        }
    }
```

### 排他思想例子：选项卡

```html
<input class="button" id="but1" type="button" value="1">
<input class="button" id="but2" type="button" value="2">
<input class="button" id="but3" type="button" value="3">
<div id="box">
     <div class="box_box" id="box3">
          <div>3</div>
     </div>
     <div class="box_box" id="box2">
          <div>2</div>
     </div>
     <div class="box_box" id="box1">
          <div>1</div>
     </div>
</div>
```

```css
#box {
    position: relative;
    width: 400px;
    height: 200px;
    background-color: rgb(255, 245, 106);
}

.button {
    font-size: 20px;
    cursor: pointer;
    background-color: rgb(255, 255, 255);
    border: 1px solid #b1b1b1;
    width: 70px;
    height: 30px;
    border-radius: 3px;
    -webkit-border-radius: 3px;
    -moz-border-radius: 3px;
    -ms-border-radius: 3px;
    -o-border-radius: 3px;
}

#but1 {
    color: #fff;
    background-color: #535353;
}

.box_box {
    color: #fff;
    font-size: 100px;
    display: flex;
    align-items: center;
    justify-content: space-around;
    position: absolute;
    width: 100%;
    height: 100%;
}

#box1 {
    background-color: rgb(66, 164, 255);
}

#box2 {
    background-color: rgb(255, 68, 68);
}

#box3 {
    background-color: rgb(66, 255, 82);
}
```

```js
// 获取按钮的集合
var butObjs = document.getElementsByClassName("button");
// 获取下面色块的集合
var box_ele = document.getElementsByClassName("box_box");
// 把色块的集合转化为数组
var box = Array.from(box_ele);
// 把数组倒换过来，因为html中div1，2，3这样排序会让3放在最上面
var boxObjs = box.reverse();
// 排他思想改变按钮和色块的变化
for (let i = 0; i < butObjs.length; i++) {
    // 获取点击的下标
    butObjs[i].index = i;
    //过去点击按钮的事件
    butObjs[i].onclick = function() {
        // 先把所有按钮统一样式
        for (let j = 0; j < butObjs.length; j++) {
            butObjs[j].style.backgroundColor = "#ffffff";
            butObjs[j].style.color = "#535353";
        }
        // 把点击的按钮单独改变样式
        this.style.backgroundColor = "#535353";
        this.style.color = "#ffffff";
        // 先把所有色块统一样式
        for (let j = 0; j < boxObjs.length; j++) {
            boxObjs[j].style.display = "none";
        }
        // 把点击对应的色块单独改变样式
        boxObjs[this.index].style.display = "flex";
    }
}
```

### 改变性别，用checked为true判定

```html
<input type="button" value="女的" id="n">
<input type="radio" name="nex" id="nan">男
<input type="radio" name="nex" id="nv">女
```

```js
wyf$("n").onclick = function() {
     wyf$("nv").checked = "fjdskfjsdko";//true就是被选中
}
```

### 下拉选择菜单，用selected为true判定

```html
<input type="button" value="王译锋喜欢吃的" id="wyf">
<select name="吃的" id="">
     <option value="牛腩粉">牛腩粉</option>
     <option value="海七沙县炒面">海七沙县炒面</option>
     <option value="红茶玛奇朵" id="hong" >红茶玛奇朵</option>
     <option value="培根">培根</option>
     <option value="ei">ei</option>
</select>
```

```js
wyf$("wyf").onclick = function() {
     wyf$("hong").selected = true;
}
```

### 点击改变样式，背景宽度长度。。

```js
this.style.width = "100px";
this.style.backgroundColor = "skyblue";
```

### 同一个按键控制隐藏和显示

- 优化之前

```html
<input type="button" value="隐藏" id="btn3">
<img src="./pic/抠肉肚脐3.jpg" alt="" width="200" id="im1">
```

```js
wyf$("btn3").onclick = function() {
     if (this.value == "隐藏") {
          wyf$("im1").style.display = "none";
          this.value = "显示";
     } else {
          wyf$("im1").style.display = "inline-block";
          this.value = "隐藏";
     }
}
```

- 优化之后

```css
.dis_none {
     display: none;
}
```

```html
<input type="button" value="优化后的隐藏" id="better">
<div id="clss">优化后隐藏显示的内容</div>
```

```js
wyf$("better").onclick = function() {
     if (wyf$("clss").className != "dis_none") {
          wyf$("clss").className = "dis_none";
          this.value = "优化后的显示";
     } else {
          wyf$("clss").className = "";
          this.value = "优化后的隐藏";
     }
}
```

### .className用 js 添加 css 样式

```css
.cls {
     width: 100px;
     height: 100px;
     background-color: rgb(0, 153, 255);
}
```

```html
<div id="sty">.classname</div>
```

```js
wyf$("sty").className = "cls";
```

### 用三元运算开关灯，夜晚模式和白天模式

```html
<input type="button" value="开/关灯" id="light">
```

```js
wyf$("light").onclick = function() {
     document.body.style.backgroundColor = document.body.style.backgroundColor != "black" ? "black" : "";
}
```

### 获取body

```js
document.body.style.backgroundColor;
```

### 按按钮禁止填写文本框

```html
<input type="button" value="禁止你写字" id="stop">
<input type="text" name="" id="text">
```

```js
wyf$("stop").onclick = function() {
     wyf$("text").disabled = "true";
}
```

### 让a标签无法跳转return false

- 第一种方法，行内解决

```html
<a href="https://www.hanjutv2020.com/" id = "a" onclick="alert('哎呀  你电我干嘛'); return false">让a标签无法跳转</a>
```

- 第二种方法，js解决

```js
wyf$("a").onclick = function() {
     return false;
}
```

### 美女相册(头像)

```html
<ul id="l">
     <li>
          <a href="./pic/头像2.jpeg"><img width="100" src="./pic/头像2.jpeg" alt=""></a>
     </li>
     <li>
          <a href="./pic/头像16.jpeg"><img width="100" src="./pic/头像16.jpeg" alt=""></a>
     </li>
     <li>
          <a href="./pic/头像15.jpeg"><img width="100" src="./pic/头像15.jpeg" alt=""></a>
     </li>
     <li>
          <a href="./pic/头像14.jpeg"><img width="100" src="./pic/头像14.jpeg" alt=""></a>
     </li>
</ul>
<img src="./pic/头像20.jpeg" alt="" width="400" id="a1">
```

```js
var aObjs = document.getElementById("l").getElementsByTagName("a");
for (var i = 0; i < aObjs.length; i++) {
     aObjs[i].onclick = function() {
          wyf$("a1").src = this.href;
          return false;
     }
}
```

### 鼠标经过出现，鼠标离开消失（二维码）

```html
<div class="erweima">
     <a href="#"></a>
     <div class="nv hide" id="light">
          <img src="./pic/光.jpg" alt="" width="150">
     </div>
</div>
```

```js
var aObj = document.getElementsByTagName("a")[0];
aObj.onmouseover = function() {
     wyf$("light").className = "nv show";
}
aObj.onmouseout = function() {
     wyf$("light").className = "nv hide";
}
```

### getElementsByName获取相同name值形成集合（伪函数）

```html
<input type="button" value="别点击喔" id="name"><br>
<input type="text" value="不是吧！！！" name="name1"><br>
<input type="text" value="不是吧！！！" name="name2"><br>
<input type="text" value="不是吧！！！" name="name1"><br>
<input type="text" value="不是吧！！！" name="name3"><br>
<input type="text" value="不是吧！！！" name="name1"><br>
<input type="text" value="不是吧！！！" name="name1"><br>
```

```js
wyf$("name").onclick = function() {
     var inputs = document.getElementsByName("name1");
     for (var i = 0; i < inputs.length; i++) {
          inputs[i].value = "你真点啊";
     }
}
```

### querySelector和getElementById相似获取id，但是获取的id前要加#

### querySelectorAll和getElementByClassName相似获取class，但是获取的class前要加.

```html
<input type="button" value="别点击喔" id="name"><br>
<div id="hong"></div>
```

```js
var a = document.querySelector("#name");
a.onclick = function() {
     var d = document.querySelector("#hong");
     d.style.backgroundColor = "black";
}
```

### 获取元素的方式总结

- 根据  "id"  获取元素：document.getElementById("id的值")

- 根据  "标签"  获取元素：document.getElementsByTagNmae("标签的名字")

- 根据  "name的值"  获取元素：document.getElementsByName("name的值")

- 根据  "类样式(class)"  获取元素：document.getElementByClassName("类样式的名字")

- 根据  "选择器的方式"  获取元素：

  1.document.querySelector("#id")

  2.document.querySelector(".class")

- 获取  "body"  标签：document.body

### 获取焦点和失去焦点（锚点）

```html
<input type="text" name="" class="t" id="t" value="你个傻逼">
```

```js
wyf$("t").onfocus = function() {
     if (this.value == "你个傻逼") {
          this.value = "";
          this.style.color = "black";
}
wyf$("t").onblur = function() {
     if (this.value == "") {
          this.value = "你个傻逼";
          this.style.color = "gray";
     }
}
```

### 自己添加属性，随便取名

- 添加属性：setAttribute("属性的名字","属性的值")
- 获取属性：getAttribute("属性的名字")

```html
<ul id="uu">
     <li>好嗨哟</li>
     <li>牛啊牛啊</li>
     <li>绣得天花乱坠</li>
     <li>抱歉</li>
     <li>不是吧</li>
</ul>
```

```js
var list = document.getElementsByTagName("li");
for (var i = 0; i < list.length; i++) {
     list[i].setAttribute("xswl", (i + 1) * 20);
     list[i].onclick = function() {
          alert(this.getAttribute("xswl"));
     }
}
```

###    删除标签的属性（包括系统自带的）

```html
<input type="button" value="删除标签属性" id="btn">
<div id="d" score="30" class="d"></div>
```

```js
wyf$("btn").onclick = function() {
     wyf$("d").removeAttribute("score");
     wyf$("d").removeAttribute("class");//系统自带的class
}
```

### 添加文本  innerText和innerHTML的区别

```html
<input type="button" value="点击增加inner" id="btn">
<div class="inner" id="inner"></div>
```

```js
wyf$("btn").onclick = function() {
     wyf$("inner").innerText = "牛啊牛啊";
     wyf$("inner").innerText = "<p>一碗化州牛腩粉 吃出男人的沉稳</p>"
     wyf$("inner").innerHTML = "牛啊牛啊";
     wyf$("inner").innerHTML = "<p>一碗化州牛腩粉 吃出男人的沉稳</p>";
}
```

### 导航栏，tab栏

```css
#hd {
     font-size: 0;
}

#hd span {
     display: inline-block;
     width: 50px;
     height: 30px;
     font-size: 16px;
     text-align: center;
     line-height: 30px;
}

#bd ul li {
     width: 200px;
     height: 200px;
     background-color: rgb(0, 255, 98);
}

.hide {
     display: none;
}

.show {
     display: inline-block;
}

.sele {
     background-color: rgb(255, 145, 0);
}
```

```html
<div>
     <div id="hd">
          <span class="sele">wyf1</span>
          <span>wyf2</span>
          <span>wyf3</span>
          <span>wyf4</span>
     </div>
     <div id="bd">
          <ul>
               <li class="show">1</li>
               <li>2</li>
               <li>3</li>
               <li>4</li>
          </ul>
     </div>
</div>
```

```js
var sp = document.getElementsByTagName("span");
var li = document.getElementsByTagName("li");
for (var i = 0; i < li.length; i++) {
     if (li[i].className != "show") {
          li[i].className = "hide";
     }
}
for (var i = 0; i < sp.length; i++) {
     sp[i].setAttribute("index", i);
     sp[i].onclick = function() {
          for (var j = 0; j < sp.length; j++) {
               sp[j].removeAttribute("class");
          }
          this.className = "sele";//上面导航栏的排他
          var num = this.getAttribute("index");
          for (var k = 0; k < li.length; k++) {
               li[k].className = "hide";
          }
          li[num].className = "show";//下面界面的排他
     }
}
```

### 出现Cannot set property 'className' of undefined的问题

> for (var i = 0; i < sp.length; i++) {
>      sp[i].setAttribute("index", i);
>      sp[i].onclick = function() {
>      li[i].className = "show";//这行出现问题
>      }
> }
>
> 由于这是事件过程，当鼠标移到元素上触发事件时，i的值早已不是当初声明事件过程时的那个i了，而是等于oLi.length（你用console.log把i的值输出一下就知道了），因此oLi[i]实际上就已经超出oLi的范围了，所以是undefined

## 节点的介绍

### 必须要熟练---倒背如流

> nodeType：节点类型（1代表的标签节点，2代表的是属性节点，3代表的是文本节点）
>
> nodeName：节点名字（如果是标签节点---获取到的是大写的标签名；如果是属性节点--- 获取到的是小写的属性名；文本节点---获取的是#text）
>
> nodeValue：节点的值（如果是标签节点---null，属性节点---属性的值，文本节点---文本内容）
>
> |          | nodeType |   nodeName   | nodeValue |
> | :------: | :------: | :----------: | :-------: |
> | 标签节点 |    1     | 大写的标签名 |   null    |
> | 属性节点 |    2     | 小写的属性名 | 属性的值  |
> | 文本节点 |    3     |    #text     | 文本内容  |
>
> 

> #### 对比记忆法
>
> DOM节点          HTML文档
>
> 元素节点               标签
>
> 属性节点               属性
>
> 文本节点            文本内容
>
> 注释节点               注释

### 获取父级节点   <重点一>

```js
console.log(uu.parentNode);
```

### 获取父级元素   <重点二>

```js
console.log(uu.parentElement);
```

### 获取子级节点（多个）   <重点三>

```js
console.log(dd.childNodes);
```

### 获取子级元素   <重点四>

```js
console.log(dd.children);
```

- 以上四种所有浏览器都支持

### 获取子级第一个子节点

```js
console.log(dd.firstChild);//IE8中是第一个子元素
```

### 获取子代第一个子元素

```js
console.log(dd.firstElementChild);//IE8不支持
```

### 获取最后一个子节点

```js
console.log(ll.lastChild);//IE8中是最后一个子元素
```

### 获取最后一个子元素

```js
console.log(ll.lastElementChild);//IE8不支持
```

### 获取前一个兄弟节点

```js
console.log(ll.previousSibling);//IE8中是前一个兄弟元素
```

### 获取前一个兄弟元素

```js
console.log(ll.previousElementSibling)//IE8不支持
```

### 获取下一个兄弟节点

```js
console.log(ll.nextSibling);//IE8中是下一个兄弟元素
```

### 获取下一个兄弟元素

```js
console.log(ll.nextElementSibling);//IE8不支持
```

### 筛选节点

```html
<div id="hh">
     <p>一碗化州牛腩粉</p>
     <span>吃出男人的沉稳</span>
     <p>一碗龙江猪脚饭</p>
     <span>吃出男人的浪漫</span>
     <p>经不经典我不管</p>
     <span>我就喜欢这一款</span>
     <p>人不装逼天打雷劈</p>
     <span>装逼装的好容易当领导</span>
     <p>放心吧 在打你之前我嚼了炫迈</p>
     <span>根本停不下来</span>
</div>
```

```js
var pObjs = wyf$("hh").childNodes;
for (var i = 0; i < pObjs.length; i++) {
     if (pObjs[i].nodeType == 1 && pObjs[i].nodeName == "P") {
          pObjs[i].style.backgroundColor = "pink";
     }
}
```

### 相同标签筛选节点

```html
<input type="button" value="不是吧" id="btn">
<ul id="ll">
     <li>一碗化州牛腩粉</li>
     <li>吃出男人的沉稳</li>
     <li>一碗龙江猪脚饭</li>
     <li>吃出男人的浪漫</li>
     <li>经不经典我不管</li>
     <li>我就喜欢这一款</li>
     <li>人不装逼天打雷劈</li>
     <li>装逼装的好容易当领导</li>
</ul>
```

```js
var nodes = wyf$("ll").childNodes;
wyf$("btn").onclick = function() {
     console.log(nodes);
     count = 0;
     for (var i = 0; i < nodes.length; i++) {
          if (nodes[i].nodeType == 1 && nodes[i].nodeName == "LI") {
               nodes[i].style.backgroundColor = count % 2 == 0 ? "skyblue" : "pink";
               count++;//重点：不用i,另外设个count
          }
     }
}
```

### 	美女相册2 (切换背景)

```css
body {
     background: url("pic/咒术1.jpg") no-repeat top/cover;
}

ul {
     background-color: rgba(255, 255, 255, 0);
     list-style: none;
}

#ii {
     padding-top: 20px;
     background-color: rgba(192, 192, 192, 0.192);
     height: 200px;
     text-align: center;
}
```

```html
<div id="ii">
     <img src="./pic/咒术1.jpg" alt="">
     <img src="./pic/咒术2.jpg" alt="">
     <img src="./pic/咒术3.jpg" alt="">
</div>
```

```js
var imgObjs = wyf$("ii").children;
var count = 0;
for (var i = 0; i < imgObjs.length; i++) {
     imgObjs[i].onclick = function() {
          document.body.style.background = 'url("' + this.src + '") no-repeat top/cover';//重点为三重引号
     }
}
//正常
//'url("' + this.src + '") no-repeat top/cover'
//转义
//"url(\"" + this.src + "\") no-repeat top/cover"
//用ES6的写法，先写单撇 后加${}
//`url("${this.src}") no-repeat top/cover`
```

### 全选框，多选框

```css
td,
th {
     text-align: center;
     width: 100px;
}
```

```html
<table>
     <thead>
          <tr>
               <th>
                    <input type="checkbox" name="" id="i_th">
               </th>
               <th>&nbsp;</th>
               <th>nodeType</th>
               <th>nodeName</th>
               <th>nodeValue</th>
          </tr>
     </thead>
     <tbody id="t_td">
          <tr>
               <td>
                    <input type="checkbox" name="" id="">
               </td>
               <td>标签节点</td>
               <td>1</td>
               <td>大写的标签名</td>
               <td>属性的值</td>
          </tr>
          <tr>
               <td>
                    <input type="checkbox" name="" id="">
               </td>
               <td>属性节点</td>
               <td>2</td>
               <td>小写的属性名</td>
               <td>null</td>
          </tr>
          <tr>
               <td>
                    <input type="checkbox" name="" id="">
               </td>
               <td>文本节点</td>
               <td>3</td>
               <td>#text</td>
               <td>文本内容</td>
          </tr>
     </tbody>
</table>
```

```js
var i_th = wyf$("i_th");
var i_s = wyf$("t_td").getElementsByTagName("input");
i_th.onclick = function() {
     for (var i = 0; i < i_s.length; i++) {
          i_s[i].checked = this.checked;
     }
}//实现点击全选
for (var i = 0; i < i_s.length; i++) {
     i_s[i].onclick = function() {
          console.log(i_s[i]);
          var flag = true;//假设被全选了
          for (var j = 0; j < i_s.length; j++) {
               if (!i_s[j].checked) {
                    flag = false;//结果没全选
                    break;
               }
          }
          i_th.checked = flag;
     }
}//下面的全选完，全选框自动打勾
```

## 创建元素

### 第一种：document.write的缺陷bug，当页面加载完之后，在动作（onclick之类）里执行，他会把我们前面的内容覆盖掉

```html
<input type="button" value="document.write的加载" id="ww">fjdisvnfueovejopvnbwj经常发生滴哦
```

```js
wyf$("ww").onclick = function() {
     document.write("<p>不是吧</p>");
}
```

### 第二种：innerHTML

```html
<input type="button" value="来份牛腩粉" id="lfnnf">
<div id="nnf"></div>
```

```js
wyf$("lfnnf").onclick = function() {
     wyf$("nnf").innerHTML = "<p>牛腩粉</p>";
}
```

### 第三种：createElement（创建元素，创建标签）+ appendChild（把创建的元素追加到父元素里，即插入标签）

```html
<input type="button" value="嗲三种创建元素的方式" id="create">
<div id="cc"></div>
```

```js
wyf$("create").onclick = function() {
     var pObj = document.createElement("p");//创建函数
     pObj.innerText = "第三种创建元素的方法";
     wyf$("cc").appendChild(pObj);//追加到父元素
}
```

### 封装一个函数（function），谁需要谁调用--加薪

```js
btn.onclick = 函数名;//直接名字调用，不用括号（），因为没有返回值
//封装的函数
function 函数名(){
     this.style.backgoundColor = "";//假设内容为把背景设为空
}
```

### 创建元素的作业，字典

```html
<input type="button" value="添加table" id="tt">
<div id="table"></div>
```

```js
var arr = [
     { name: "免费海贼王", href: "https://www.letvav.cc/dongman/haizeiwang/1-962.html" },
     { name: "复制颜色块", href: "https://flatuicolors.com/" },
     { name: "github", href: "https://github.com/" },
     { name: "在线画图", href: "https://www.processon.com/" },
     { name: "幼儿成长记", href: "http://baby.bnuz.edu.cn:8081/#/" }
];
wyf$("tt").onclick = function() {
     var tableObj = document.createElement("table");
     wyf$("table").appendChild(tableObj);
     tableObj.border = "1";
     tableObj.cellPadding = "0";
     tableObj.cellSpacing = "0";
     for (var i = 0; i < arr.length; i++) {
          var array = arr[i];
          var trObj = document.createElement("tr");
          tableObj.appendChild(trObj);
          var td1 = document.createElement("td");
          trObj.appendChild(td1);
          var td2 = document.createElement("td");
          trObj.appendChild(td2);
          td1.innerText = array.name;
          td2.innerHTML = `<a href="${array.href}">${array.name}</a>`;
     }
}
```

## 事件的方式

### 第一种

- 带on的事件onclick,onmouseover,onmouseout等等。

### 第二种（可以支持同时多个function事件反应）

- 对象.addEventListener("事件类型"，事件处理函数，false)---谷歌，火狐支持，IE等低版本不支持

  > 第一个参数：事件类型（“事件类型不带on”）
  >
  > 第二个参数：事件处理函数（匿名函数和命名函数）
  >
  > 第三个参数：false---记住事false---会涉及到后面的冒泡和捕获

```html
<input type="button" value="第二种事件方式" id="count">
```

```js
wyf$("count").addEventListener("click", function() {
     console.log("傻仔");
}, false);
wyf$("count").addEventListener("click", function() {
     console.log("好啊");
}, false);
```

### 第三种（也支持多个function事件反应）

- 对象.attachEvent("事件类型",事件处理函数)---只支持IE等地版本

  > 第一个参数：事件类型（“事件类型带on”）
  >
  > 第二个参数：事件处理函数（匿名函数和命名函数）

```html
<input type="button" value="第二种事件方式" id="count">
```

```js
wyf$("count").attachEvent("onclick", function() {
     console.log("傻仔");
});
```

## 解除事件（解绑）

### 第一种

- 事件.onclick = null;

```html
<input type="button" value="绑定事件" id="bt1">
<input type="button" value="解绑事件" id="bt2">
```

```js
wyf$("bt1").onclick = function() {
     console.log("绑定事件");
}
wyf$("bt2").onclick = function() {
     wyf$("bt2").onclick = null;//绑定事件就不起作用了
}
```

### 第二种

- 事件.removeEventListener("click",命名函数,false)

```html
<input type="button" value="绑定事件" id="bt3">
<input type="button" value="解绑事件" id="bt4">
```

```js
wyf$("bt3").addEventListener("click", f3, false);
wyf$("bt3").addEventListener("click", f4, false);
wyf$("bt4").addEventListener("click", function() {
     wyf$("bt3").removeEventListener("click", f3, false);//解除事件3，点击bt3只能实现事件4
})
```

### 第三种

- 事件.detachEvent("onclick",命名函数);

```html
<input type="button" value="绑定事件" id="bt5">
<input type="button" value="解绑事件" id="bt6">
```

```js
wyf$("bt5").attachEvent("click", f5, false);
wyf$("bt5").attachEvent("click", f6, false);
wyf$("bt6").onclick = function() {
     wyf$("bt5").removeEventListener("click", f6, false);//解除事件5，点击bt5只能实现事件6
}
```

###  冒泡事件，即点击里面小的div外面的也作出反应

- 修复这个bug的方法

  > 谷歌和火狐：e.stopPropagation();
  >
  > IE：window.event.cancelBubble = true;

```html
<div id="dv1">
     <div id="dv2">
          <div id="dv3"></div>
     </div>
</div>
```

```js
document.body.onclick = function() {
     console.log("body");//body
}
wyf$("dv1").onclick = function() {
     console.log("粉红色框");//粉红色框 body
}
wyf$("dv2").onclick = function() {
     console.log("蓝色框");//蓝色框 粉红色框 body
}
wyf$("dv3").onclick = function(e) {//事件对象event，默认写e
     console.log("黑灰色框");//黑灰色框
     //谷歌和火狐
     e.stopPropagation();
     //IE
     window.event.cancelBubble = true;
}
```

### 事件冒泡（事件委托，儿子可以委托爸爸爷爷去做，让上级做）不需要for循环tagname一个一个找了，获取所有子级 （考试）

- var target = e.target;

```html
<ul id="id">
    <li>西施</li>
    <li>王昭君</li>
    <li>貂蝉</li>
    <li>杨玉环</li>
</ul>
```

```js
wyf$("id").onclick = function(e) {//叫他爸负责接受点击事件
    var target = e.target;//target就是任意子集
    target.style.backgroundColor = "pink";
}
```

### 第二种for循环

- 数组.forEach(function(){},false)

```css
#dv1 {
    width: 300px;
    height: 300px;
    background-color: #1abc9c;
}
        
#dv2 {
    width: 200px;
    height: 200px;
    background-color: #ecf0f1;
}
        
#dv3 {
    width: 100px;
    height: 100px;
    background-color: #e74c3c;
}
```

```html
<div id="dv1">
     <div id="dv2">
          <div id="dv3"></div>
     </div>
</div>
```

```js
var dObj = [wyf$("dv1"), wyf$("dv2"), wyf$("dv3")];//获取上下几代div
dObj.forEach(function(ele) {//for循环，ele相当于i
    ele.addEventListener("click", function(e) {
        console.log(this.id);
        e.stopPropagation();//修复冒泡行为的bug
    }, false);
})
```

### 事件的三个阶段，（事件捕获，目标阶段，冒泡），后面前面的123

| 事件     | 属性                | function后面的true/false |
| -------- | ------------------- | ------------------------ |
| 事件捕获 | 1，从外往里         | true                     |
| 目标阶段 | 2，执行当前点击元素 |                          |
| 冒泡     | 3，从里到外         | false                    |

- e.evenPhase获取1，2，3

```css
#dv1 {
    width: 300px;
    height: 300px;
    background-color: #1abc9c;
}
        
#dv2 {
    width: 200px;
    height: 200px;
    background-color: #ecf0f1;
}
        
#dv3 {
    width: 100px;
    height: 100px;
    background-color: #e74c3c;
}
```

```html
<div id="dv1">
     <div id="dv2">
          <div id="dv3"></div>
     </div>
</div>
```

```js
var dObj = [wyf$("dv1"), wyf$("dv2"), wyf$("dv3")];
dObj.forEach(function(ele) {
     ele.addEventListener("click", function(e) {
          console.log(this.id + "=====" + e.eventPhase);
     }, false);//2 3 3
     ele.addEventListener("click", function(e) {
          console.log(this.id + "=====" + e.eventPhase);
     }, true);//1 1 2
})
```

### 计时器（单位：毫秒，1000毫秒=1秒）

- 设置计时器：var timeId = setInterval(fun,100);
- 关闭计时器：clearInterval(timeId);

```html
<input type="button" value="停止计时器" id="btn">
```

```js
var timedID = setInterval(fun, 100);//设置计时器
wyf$("btn").addEventListener("mouseover", function() {
    window.clearInterval(timedID);//关闭计时器
    //clearInterval(timedID);//window可以省略
}, false);
wyf$("btn").addEventListener("mouseout", function() {
    timedID = setInterval(fun, 100);//重新开启计时器
}, false);
function fun() {//另设一个func，可以减少开多个func
    console.log("计时器");
}
```

### 燥起来和停下来（抖）

```html
<input type="button" value="燥起来" id="btn1">
<input type="button" value="停起来" id="btn2">
<div id="ig">
    <img src="./pic/咚1.jpg" alt="" srcset="">
</div>
```

```js
var zao = "";//全局变量
wyf$("btn1").addEventListener("click", function() {
    zao = setInterval(dong, 100);//开启计时器
}, false);
wyf$("btn2").addEventListener("click", function() {
    window.clearInterval(zao);//关闭计时器
}, false);
function dong() {
    var x = parseInt(Math.random() * 100 + 1);//取随机数
    var y = parseInt(Math.random() * 100 + 1);
    wyf$("ig").style.left = x + "px";//要加px单位
    wyf$("ig").style.top = y + "px";
}
```

### 连续输出时间

```js
setInterval(function() {
     var dt = new Date();//获取时间
     var hour = dt.getHours();
     var min = dt.getMinutes();
     var sec = dt.getSeconds();
     console.log(hour + ":" + min + ":" + sec);
}, 1000)
```

### 自动换照片，切换照片

```html
<img src="./pic/咚1.jpg" alt="" id="change">
```

```js
function cha() {
    var mem = parseInt(Math.random() * 11 + 1);
    console.log(mem);
    wyf$("change").src = "./pic/咚" + mem + ".jpg";
}
cha();//一开始就执行一次，要不会1000毫秒才开始第一次，上面function独立就是修复这个bug
setInterval(cha, 1000);
```

### 逐渐平移

- 获取左边的left：id.offsetLeft

```html
<input type="button" value="向右移动400px" id="go">
<div id="run"></div>
```

```js
wyf$("go").addEventListener("click", function() {
     var timeId = setInterval(function() {
          var left = wyf$("run").offsetLeft;//获取绝对定位后run的left
          var step = 1;
          left += step;
          if (left <= 100) {//向右移动
               wyf$("run").style.left = left + "px";
          } else {//超过100停止
               clearInterval(timeId);
               wyf$("run").style.left = 0 + "px";
          }
     }, 10);
}, false);
```

### 逐渐平移（升级版，可以回来的）

```html
<input type="button" value="向右平移400px" id="go1">
<input type="button" value="向右平移800px" id="go2">
<input type="button" value="向右平移0px" id="go3">
<div id="dv"></div>
```

```js
function amimate(element, target) {
     clearInterval(element.timeId);//每次执行都清除定时器，以防按多次按钮加速bug
     //把定时器名字设置为element的定时器，防止每次执行func都开一个定时器
     element.timeId = setInterval(function() {
          var current = element.offsetLeft;
          //每步1px
          var step = 1;
          //判断现在位置和目标位置的前后关系
          step = current < target ? step : -step;
          current += step;
          if (Math.abs(current - target) > Math.abs(step)) {
               element.style.left = current + "px";//记住加px
          } else {
               clearInterval(element.timeId);
               element.style.left = target + "px";
          }
     }, 1);
}
```

### 箭头函数()=>{} 与function的区别

#### 1.this的指向：

- 使用**function**定义的函数，this的指向随着调用环境的变化而**变化的**，而**箭头函数**中的this指向是**固定不变的**，一直指向的是定义函数的环境。

```js
//使用function定义的函数中this指向是随着调用环境的变化而变化的
function foo(){
	console.log(this);
}
var obj = { aa: foo };
foo(); //Window
obj.aa() //obj { aa: foo }
```

```js
//明显使用箭头函数的时候，this的指向是没有发生变化的。
var foo = () => { console.log(this) };
var obj = { aa:foo };
foo(); //Window
obj.aa(); //Window
```

#### 2.构造函数：

- function是可以定义构造函数的，而箭头函数是不行的。

```js
//使用function方法定义构造函数
function Person(name, age){
	this.name = name;
	this.age = age;
}
var lenhart =  new Person(lenhart, 25);
console.log(lenhart); //{name: 'lenhart', age: 25}
```

```js
//尝试使用箭头函数
var Person = (name, age) =>{
	this.name = name;
	this.age = age;
};
var lenhart = new Person('lenhart', 25); //报错：Uncaught TypeError: Person is not a constructor
```

#### 3.变量提升

- 由于js的内存机制，function的级别最高，而用箭头函数定义函数的时候，需要var(let const定义的时候更不必说)关键词，而var所定义的变量不能得到变量提升，故箭头函数一定要定义于调用之前！

```js
foo(); //123
function foo(){
	console.log('123');
}

arrowFn(); //Uncaught TypeError: arrowFn is not a function
var arrowFn = () => {
	console.log('456');
};
```

### 轮播图（中间的图片切换）

```css
#box {
     position: relative;
     margin: 100px auto;
     width: 500px;
     height: 281px;
     box-shadow: 0px 0px 10px 5px #353b48;
     overflow: hidden;
}

#img {
     position: absolute;
}

#img ul {
     width: 20000px;
     position: absolute;
}

#img ul li {
     overflow: hidden;
     float: left;
}

#img ul li img {
     width: 500px;
}

#box ol {
     position: absolute;
     align-self: center;
     right: 6px;
     top: 90%;
}

#box ol li {
     color: #353b48;
     background-color: #ffffff;
     margin-right: 4px;
     text-align: center;
     border-radius: 10px;
     float: left;
     display: block;
     width: 20px;
     cursor: pointer;
     user-select: none;
     box-shadow: 0 0 10px 1px #ffffff;
}

.current {
     color: white !important;
     background-color: #353b48 !important;
}

.switch {
     font-size: 20px;
     color: white;
     position: absolute;
     top: 42%;
     width: 44px;
     height: 44px;
     cursor: pointer;
     background-color: rgba(0, 0, 0, 0.63);
     display: none;
     align-items: center;
     user-select: none;
}

.switch:active {
     background-color: rgba(71, 71, 71, 0.63);
}

#left {
     left: -16px;
     border-top-right-radius: 22px;
     border-bottom-right-radius: 22px;
}

#left span {
     margin-left: 50%;
}

#right {
     right: -16px;
     border-top-left-radius: 22px;
     border-bottom-left-radius: 22px;
}

#right span {
     margin-left: 22%;
}
```

```html
<div id="box" class="box">
     <div id="img">
          <ul id="ul">
               <li>
                    <a href=""><img src="./pic/咚1.jpg" alt=""></a>
               </li>
               <li>
                    <a href=""><img src="./pic/咚2.jpg" alt=""></a>
               </li>
               <li>
                    <a href=""><img src="./pic/咚3.jpg" alt=""></a>
               </li>
               <li>
                    <a href=""><img src="./pic/咚4.jpg" alt=""></a>
               </li>
          </ul>
     </div>
     <ol>
     </ol>
     <div id="left" class="switch">
          <span>&lt</span>
     </div>
     <div id="right" class="switch">
          <span>&gt</span>
     </div>
</div>
```

```js
window.onload = function() {
        //平移的封装函数
    function animate(element, target) {
        //每次执行都清除定时器，以防按多次按钮加速
        clearInterval(element.timeId);
        //把定时器名字设置为element的定时器，防止每次执行func都开一个定时器
        element.timeId = setInterval(function() {
            var current = element.offsetLeft;
            //控制平移的快慢
            var step = 15;
            //判断当前位置和目标位置的关系从而决定正反方向平移
            step = current < target ? step : -step;
            //每一次走一步
            current += step;
            //正常情况的每次平移
            if (Math.abs(current - target) > Math.abs(step)) {
                element.style.left = current + "px";
            } else {
                //最后一步的平移
                clearInterval(element.timeId);
                element.style.left = target + "px";
            }
        }, 1);
    }
    //获取最外面的框
    var box = wyf$("box");
    //获取相框
    var img = wyf$("img");
    //获取ul
    var ulObj = img.children[0];
    //获取ul下的li
    var list = ulObj.children;
    //获取相框的宽度
    var imgWidth = list[0].offsetWidth;
    //获取ol
    var olObj = box.children[1];
    //获取ol下的li
    var ol_li = olObj.children;
    // 获取right和left切换图片按键
    var swi = document.getElementsByClassName("switch");
    //把索引作为全局变量定义
    var index_this = 0;
    for (var i = 0; i < list.length; i++) {
        // 创建新元素li
        var liObj = document.createElement("li");
        //把li加进ol里
        olObj.appendChild(liObj);
        // 把第一个li设当前class
        ol_li[0].className = "current";
        // 给每个li设属性索引
        liObj.setAttribute("index", i);
        //获取索引
        var index = liObj.getAttribute("index");
        // 添加内容1234，为索引+1
        liObj.innerHTML = parseInt(index) + 1;
        // li的排他思想
        liObj.onclick = function() {
            for (var j = 0; j < ol_li.length; j++) {
                // console.log(ol_li[j].className);
                ol_li[j].removeAttribute("class");
            }
            this.className = "current";
            //获取点击的li的索引，表示第几个
            index_this = this.getAttribute("index");
            animate(img, -index_this * imgWidth);
        }
    }
    //大招，加薪，为了平移循环后面接上前面，在后面克隆上
    ulObj.appendChild(ulObj.children[0].cloneNode(true));
    //left按钮的点击事件
    wyf$("left").onclick = function() {
            // 当图片为第一个的时候点击，会向右平移并出现最后一张图片
            if (index_this == 0) {
                index_this = list.length - 1;
                img.style.left = -index_this * imgWidth + "px";
            }
            index_this--;
            //调用animate函数点击平移
            animate(img, -index_this * imgWidth);
            //下面的数字按钮用排他思想同步
            for (let i = 0; i < ol_li.length; i++) {
                ol_li[i].removeAttribute("class");
            }
            ol_li[index_this].className = "current";
        }
        //right按钮的点击事件
    wyf$("right").onclick = f_right;
    // 封装right点击事件
    function f_right() {
        if (index_this == list.length - 1) {
            index_this = 0;
            img.style.left = 0 + "px";
        }
        index_this++;
        animate(img, -index_this * imgWidth);
        if (index_this == list.length - 1) {
            ol_li[ol_li.length - 1].removeAttribute("class");
            ol_li[0].className = "current";
        } else {
            for (let i = 0; i < ol_li.length; i++) {
                ol_li[i].removeAttribute("class");
            }
            ol_li[index_this].className = "current";
        }
    }
    //给right设每秒点击一次事件，从而达成自动切换效果
    var img_move = setInterval(f_right, 3500);
    //right和left的出现和消失事件
    wyf$("box").onmouseover = function() {
        swi[0].style.display = "flex";
        swi[1].style.display = "flex";
        clearInterval(img_move);
    }
    wyf$("box").onmouseout = function() {
        swi[0].style.display = "none";
        swi[1].style.display = "none";
        img_move = setInterval(f_right, 3500);
    }
}
```

### offset系列

- offsetWidth：自己的宽度+border值
- offsetHeight：自己的高度+border值
- offsetLeft：分是否有定位
- offsetTop

|              |                获取offsetLeft                |
| :----------: | :------------------------------------------: |
| 有定位的时候 |            自己的left值+margin值             |
|   标准流时   | 父级的（margin+border+padding）+自己的margin |

### scroll系列（加overflow:auto后的滚动条是占位置的）

- scrollWidth：1.没有内容的时候，盒子实际的宽度。2.有内容的时候，盒子里面内容的宽度
- scrollHeight
- scrollTop：盒子内容鼠标滚轮向下滚动的距离
- scrollLeft

### client系列（可视区域）

- clientWidth：可视区域的宽度（不包边框）
- clientHeight：可视区域的高度（不包边框）
- clientLeft：左边边框的宽度
- clientTop：上面边框的宽度

### div的滚动事件（div加了overflow:auto出现滚动条后，鼠标滚动的事件）

```js
wyf$("div").onscroll = function(){
     console.log("hh");
}
```

### document获取元素

- document.body====获取body
- document.title====获取title
- document.documentElement====获取整个html

### 鼠标跟随图片，小苍蝇

- e.clientX：获取鼠标X坐标
- e.clientY：获取鼠标Y坐标

```css
#fly {
    position: absolute;
    left: -100px;
    user-select: none;
    z-index: 1;
}
```

```html
<img src="./pic/蓝色苍蝇.gif" alt="" width="60" id="fly">
```

```js
document.onmousemove = function(e) {
     wyf$("fly").style.left = e.clientX + 15 + "px";
     wyf$("fly").style.top = e.clientY + 15 + "px";
}
```

### window的操作

```js
window.closed       // window是否关闭
window.length       // iframe个数
window.name         // 获取和设置window的名字
window.innerHeight  // window的高度
window.innerWidth   // window的宽度
window.screenX      // 鼠标距离window的左边距
window.screenY      // 鼠标距离window的上边距
window.location     // 获取window关于url的对象
window.history      // 获取history对象
window.screen       // 获取screen对象
window.pageXOffset  // 页面向右滚动的距离
window.pageYOffset  // 页面向下滚动的距离
```

### 创建对象

```js
var obj = {
     name:'王译锋',
     age:99,
     num:1901030097
}
```

### 获取页面向右或向下滑动的距离（的方法）

```js
function getScroll() {
     //创建对象并返回
     return {
          left: window.pageYOffset || document.documentElement.scrollLeft || document.body.scrollLeft || 0,
          top: window.pageXOffset || document.documentElement.scrollTop || document.body.scrollTop || 0
     }
}
```

- 调用：getScroll().top

### 发生滚轮滑动事件，鼠标向下滑动

- 第一种

```js
window.onmousewheel = function() {}
```

- 第二种（常用）

```js
document.onscroll = function(){}
```

### class="fixed"的例子

```css
.fixed{
	position:fixed;
     top: 0;
     left: 50%;
     /*盒子的一半宽度*/
     margin-left:711.5px;
}
```

### 栈内存和堆内存

- 内存里面的储存方式有两种（栈内存 和 堆内存）
- 值类型--一般用“栈内存”--用矩形表示
- 引用类型--一般用“堆内存”--用椭圆表示

### 值类型传递的是值，引用类型传递的是地址

```js
var obj1 = {
     name:'wyf',
     age:18,
     sex:'男'
}
var obj2 = obj1;//把obj1的地址传递给obj2
obj2.name = 'yf';//改变obj2就是改变obj1
console.log(obj1.name);//yf
```

### 嵌套对象：对象里面还有一个对象

```js
var obj1 = {
     sex:'男'
}
var obj2 = {
     name:'wyf',
     age:18,
     objM:obj1
}
console.log(obj2.objM.sex);
```

### 访问对象的方法：点语法和中括号语法

```js
obj = {
     name:"wyf",
     age:23
}
obj.name;//点语法
obj["name"];//中括号语法
```

### 对象的增删改查

```js
var obj = {};//创建对象
obj.name = "wyf";
obj.age = 23;//增
delete obj.name;//删
obj.name = lyq;//改
console.log(obj.name);//查
```

### in关键字

#### 判断对象中是否有这个元素 ： "属性名" in 对象名

```js
var obj = {
     name:"lyq",
     age:12
}
console.log("name" in obj);//true
console.log("key" in obj);//false
 
var a = "name";//把属性名单独放出来也可以
console.log(a in obj);//true
```

#### 对象中的遍历

```js
var obj = {
	name:"lyq",
	age:12,
	sex:"女"
}
for(var key in obj){
     console.log(key,obj[key]);
     //name lyq
     //age 12
     //sex 女
}
```

#### 数组的遍历

```js
var arr = [1,2,3,4,5];
for (var key in arr) {
     console.log(key, arr[key]);
}
//0 1
//1 2
//2 3
//3 4
//4 5
```

### 数组中找出是否存在相应的元素，找数组中的字符串

- 第一种 for in 循环

  ```js
  var arr = [1, 2, 3, 4, 5];
  for (var key in arr) {
       if (arr[key] == 3) {
            console.log("存在");
       }
  }
  ```

- 第二种 indexof 找出对应的元素

  ```js
  var arr = [1, 2, 3, 4, 5];
  if (arr.indexOf("3") != 0) {
       console.log("存在");
  }
  ```

- 第三种 扩展 了解即可 推荐上面两种

  ```js
  var arr = [1, 2, 3, 4, 5];
  if (2 in arr) {
       console.log("存在");
  }
  ```

### 面向过程和面向对象  例子：啤酒鸭

- 面向过程：凡事都是要亲历亲为，每件事的具体过程都是要知道的，注重过程。
- 面向对象：根据需求来找对象，面向对象注重的结果。

### 面向对象

```js
//创建对象
var arr = {
     name: "lyq",
     age: 12,
     sex: "女",
     paint: function() {
          console.log("画画");
     },
     eat: function() {
          console.log("吃");
     }
}
```

### 面向对象，封装函数进对象的例子

```html
<p>我是傻逼</p>
<p>我是傻逼</p>
<p>我是傻逼</p>
<div class="dv">你是傻逼</div>
<div class="dv">你是傻逼</div>
<div class="dv">你是傻逼</div>
```

```js
$ = {
    getElementsByClassName: function(ClassName) {
        return document.getElementsByClassName(ClassName);
    },
    getElementsByTagName: function(Tagname) {
        return document.getElementsByTagName(Tagname);
    },
    setStyle: function(eles, color) {
        for (let i = 0; i < eles.length; i++) {
            eles[i].style.backgroundColor = color;
            eles[i].style.border = "2px solid #888";
            eles[i].style.color = "pink";
        }
    }
}
$.setStyle($.getElementsByTagName("p"), "#123456");
$.setStyle($.getElementsByClassName("dv"), "#654321");
```

### 异常捕捉，一般情况下出现错误代码，就不会执行下面的代码，可以利用try catch继续向下执行代码

```js
try{
     //存放可能会出错的代码，如果有错误信息，那么会执行catch中的代码，如果没有错，就不会执行catch中的代码
}catch(e){
     //e 为错误信息
}
```

- 出错例子

  ```js
  var a = 123;
  console.log(a);
  console.log(b);//报错
  
  function later() {
       console.log("后面执行的代码");
  }
  later();
  ```

- 用try catch后

  ```js
  var a = 123;
  console.log(a);
  try {
      console.log(b);//出错，然后执行catch中的代码
  } catch (e) {//e表示错误的信息
      console.log("Error Msg", e);//执行这句后，继续向下执行
  }
  function later() {
      console.log("后面执行的代码");
  }
  later();
  ```

### 完整的try catch finally --- 防止出错

```js
try{
    //存放可能出错的代码
}catch(e){
    //throw可以手动输出错误信息
    //throw "这是一个错误信息，小心检测一下try里面的代码有没有bug";
    //throw "这是一个错误信息，小心检测一下try里面的代码有没有bug"+e;
    throw{
        errorMsg:e,//错误信息
        errorCode:404,//错误编码，假设404错误
    }
}finally{
    //加上这个才是完整的结构
    //不管前面上面代码，都会执行这里的代码
    //存放一些初始化代码（后端）
    //多用于后端开发node.js，用来释放一些资源
}
```

### delete删除关键字

- 能删除对象中的属性
- 能删除未使用var声明的变量
- 不能删除使用var声明的变量
- 能删除直接定义再window上面的属性
- 总结：如果删除成功返回true，如果失败返回false

```js
word1 = "wyf";
console.log(delete word1);//true 能删除没有用var定义的变量，因为未使用var声明的变量，会自动挂载到window上面，浏览器对象---全局的，能使用delete删除
var word2 = "lyq";
console.log(delete word2);//false 不能删除用var来定义的变量
//考题
window.word3 = "demo";
console.log(delete demo);//true 能删除window上的属性
```

### 五个创建对象

#### 1.字面量的方式创建对象

```js
var littleGirl = {
    name: "赖以青",
    age: 12,
    birthday: 20090128,
    sex: 0,
    school: "三中",
    major: "画画",
    action: function() {
        console.log(this.name + "专业是" + this.major);//用this直接调用本对象
    }
}
console.log(littleGirl.name);
console.log(littleGirl.age);
console.log(littleGirl.sex);
console.log(littleGirl.school);
console.log(littleGirl.major);
littleGirl.action();
```

#### 2.内置的构造函数创建对象

```js
var littleGirl = new Object();
littleGirl.name = "赖以青";
littleGirl.age = 12;
littleGirl.birthday = 20090128;
littleGirl.sex = 0;
littleGirl.action = function() {
    console.log(this.name + "专业是" + this.major);
}
console.log(littleGirl.name);
console.log(littleGirl.age);
console.log(littleGirl.birthday);
console.log(littleGirl.sex);
littleGirl.action();
```

#### 3.工厂模式：就是把内置对象构造函数的方式放到函数里面   缺点：找不到父类

```js
function createKid(name, age, birth, sex, school, major) {
    var kid = new Object();
    kid.name = name;
    kid.age = age;
    kid.birth = birth;
    kid.sex = sex;
    kid.school = school;
    kid.major = major;
    kid.action = function() {
        console.log(this.name + "专业是" + this.major);
    }
    return kid;
}
var kid = createKid("赖以青", 12, 20090128, 0, "三中", "画画");
console.log(kid);
console.log(kid instanceof createKid);//false，工厂模式的缺点：找不到父类
```

#### 4.自定义构造函数    优点：1.完美优化代码  2.还可以找到父类，不像工厂模式一样找不到父类

- instanceof  找父类，子类 instanceof 父类，找到返回true，找不到返回false
- constructor  找父类，用点语法调用，直接返回父类函数

```js
function CreateKid(name, age, major) { //自定义构造函数
    this.name = name;
    this.age = age;
    this.major = major;
    this.action = function() {
            console.log(this.name + "专业是" + this.major);
        }
        //会有默认的return this
}
//实例化对象
var kid = new CreateKid("lyq", 12, "画画");
console.log(kid);
console.log(kid instanceof CreateKid);//true
if (kid.constructor == CreateKid) {
    console.log("Kid是CreateKid的孩子")
}//Kid是CreateKid的孩子
//工作中都是用自定义构造函数方式创建对象---优点：1.完美优化代码  2.还可以找到父类，不想工厂模式一样找不到父类
```

#### 5.Object.create()---优势：能创建一个连原型链都没有的对象，这样好处是我们查询数据更快

```js
var kid = Object.create(null);
console.log(kid.name = "lyq");//lyq
console.log(kid);//{name: "lyq"}
```

#### 原型：prototype

- 我们工作里面，一般会把属性放在构造函数身上，方法放在原型上面，目的就是为了实现数据共享
- console.dir(实例化后的对象);//查看原型的方法

```js
function CreateKid(name, age, major) { //自定义构造函数
     this.name = name;
     this.age = age;
     this.major = major;
     // this.action = function() {
     //     console.log(this.name + "专业是" + this.major);
     // }
}
CreateKid.prototype.action = function() {//把方法放到原型prototype上
     console.log(this.name + "专业是" + this.major);
}
//实例化对象
var kid = new CreateKid("lyq", 12, "画画");
console.dir(Kid);//CreateKid --- 查看原型的方法
console.log(kid);//CreateKid {name: "lyq", age: 12, major: "画画"}
```

### 原型

老师总结的三句话：

1. 每个构造函数都有一个prototype属性，指向他的原型对象
2. 每一个实例化对象都有一个\__proto__属性，指向他所属类的原型对象
3. 每一个原型对象都有一个constructor属性，指向构造函数本身

![image-20210813204624829](C:\Users\nnf\AppData\Roaming\Typora\typora-user-images\image-20210813204624829.png)

#### 完整的原型图

![image-20210816161943213](C:\Users\nnf\AppData\Roaming\Typora\typora-user-images\image-20210816161943213.png)

- 计算机直接给Object.prototype.\__proto__指向null

#### 获取原型对象的方法---小心被面试到

1. 构造函数.prototype
2. 实例化对象.\__proto__
3. Object.getPrototypeof(实例化对象)

#### 出现自定义构造函数里面方法过多的情况，就把原型指向对象，把所有方法都放在一个对象里面

- constructor：把原型强制指向其他的地方

![image-20210814202815457](C:\Users\nnf\AppData\Roaming\Typora\typora-user-images\image-20210814202815457.png)

```js
function CreateKid(name, age, major) { //自定义构造函数
    this.name = name;
    this.age = age;
    this.major = major;
}
CreateKid.prototype = {
        constructor: CreateKid,//如果把原型的指向给了一个对象{}，那千万别忘了在对象里面修改指向给自定义构造函数
        action: function() {//第一个方法
            console.log(this.name + "专业是" + this.major);
        },
        reaction: function() {//第二个方法
            console.log("吓死我了");
        }
    }
    //实例化对象
var kid = new CreateKid("lyq", 12, "画画");
console.log(kid.constructor); //本来应该是原型的对象的，因为改了就指向回自定义构造函数了
```

#### this的指向

```js
console.log(this); //window
function Kid() {
    console.log(this); //window  没有实例化之前指向window
}
Kid();
var Kids = new Kid(); //Kid()  实例化对象后的this指向对象
```

到此：我们分为一下几种情况看this的走向

1. 函数外部，或者说在全局作用域下面this指向window
2. 普通函数，this指向window
3. 用对象去调用函数，this指向对象（也就是点前面是谁this就指向谁

- 在实际开发工作中：call()  和  apply()  还可以改变this指向

#### 检测自定构造函数的属性和方法

1. in关键字
2. 实例化对象.hasOwnProperty("属性或方法");

```js
function CreateKid(name, age, major) { //自定义构造函数
     this.name = name;
     this.age = age;
     this.major = major;
}
CreateKid.prototype = {
     constructor: CreateKid, //如果把原型的指向给了一个对象{}，那千万别忘了在对象里面修改指向给自定义构造函数
     action: function() {
          console.log(this.name + "专业是" + this.major);
     },
     reaction: function() {
          console.log("吓死我了");
     }
}
//实例化对象
var kid = new CreateKid("lyq", 12, "画画");
console.log(kid.constructor); //本来应该是原型的对象的，因为改了就指向回自定义构造函数了
console.log("name" in kid);//ture  
console.log("action" in kid);//true  in语法可以检测出私有和共有两种 在原型中的属性和方法都是公有的
console.log(kid.hasOwnProperty("name"));//true
console.log(kid.hasOwnProperty("action"));//false  hasOwnProperty只能检测出私有的  所以不能检测出原型中公有的属性和方法
```

#### isPrototype 与 instanceOf

- isPrototype ：判断某个对象是否是指定实例对象的原型对象，如果返回true，反之返回false

- instanceOf：判断当前的对象是否是指定的类型

```js
function CreateKid(name, age, sex) {
    this.name = name;
    this.age = age;
    this.sex = sex;
}
CreateKid.prototype = {
    constructor: CreateKid,
    action: function() {
        console.log(this.name + "好傻");
    }
}
var Kid = new CreateKid("lyq", 12, 0);
console.log(Kid);
console.log(CreateKid.prototype.isPrototypeOf(Kid)); //true
console.log(Kid instanceof CreateKid); //true
```

#### 用原型修改底层方法

```js
//总结：如果我们直接改Array.prototype,如果大家都这么改，别人使用这个数组方法的时候，就降低了搜索的效率。
function MyArray() {
}
MyArray.prototype = new Array();//把MyArray指向Array原型，把Array的所有方法继承到自己新建的原型中，就可以单独加自己的原型，不影响到Array原型了
MyArray.prototype.getLength = function() {
    return this.length;
}
var kid1 = new MyArray();//实例化对象
kid1.push(1, 2, 3, 4);
console.log(kid1.getLength());//4
```

#### 大总结：面试会问到的几句话

##### 问：自定义构造函数和工厂模式非常的相似，但是还是有区别的

1. 自定义的构造函数首字母要大写---规范
2. 需要实例化对象，需要new关键字和构造函数一起创建对象
3. 构造函数最后，会自动返回return this

##### 继续扩展底层原理：自定义构造函数如何来构造函数对象

1. 在函数内部会默写的创建一个空对象 var obj = new Object()
2. 会把默认创建好的对象赋值给this  this = obj
3. 通过this来添加属性和方法
4. 默认会把内部创建好的对象返回return this

##### 构造函数返回值问题---小心面试到

- 值是可以修改的

1. 如果修改的是值类型，修改无效
2. 如果修改的是引用类型，修改有效

### 回调函数---就是函数作为参数调用了---可以传递匿名函数也可调用命名函数

```js
function func(fun) {//形参为函数
     console.log("我是调用函数的函数");
     fun();//运行形参中的函数
}

function name() {//命名函数，也可以为匿名函数
     console.log("我是也个命名函数");
}
func(name);//调用命名函数运行func函数
```

### 高阶函数

```js
function func() {
    console.log("我是第一个函数");
    return function() {
        console.log("我是返回的函数");
    }
}
var fun = func();
fun();//因为返回的是函数，直接加（）执行就行
```

### 继承

#### 1.混入式继承：拷贝继承（浅继承 和 深继承）

```js
var kid1 = {
    name: "lyq",
    age: 12,
    sex: 0,
    action: {
        name: "haosha"
    }
};
var kid2 = {};
//将kid1里面的数据拷贝给kid2
for (var key in kid1) {
    kid2[key] = kid1[key];
}
kid2.action.name = "wyf";//可以单独修改继承的数据
console.log(kid1);
console.log(kid2);
```

#### 2.原型式继承

- 跟前面的混入式继承都有一样的缺陷：存在数据共享问题

  ![image-20210815111950193](C:\Users\nnf\AppData\Roaming\Typora\typora-user-images\image-20210815111950193.png)

```js
function Kid1() {}
Kid1.prototype.action = function() {
    console.log("我是Kid1上的方法");
}
function Kid2() {}
Kid2.prototype = Kid1.prototype; //Kid2继承Kid1的prototype
var Kid22 = new Kid2();
Kid22.action();
```

#### 3.原型链继承 --- 缺点：子类无法向父类传递参数 --- 后面就会引出我们的call继承，经典继承和组合继承

```js
//大人的构造函数
function Adult(name, age, sex) {
    this.name = name;
    this.age = age;
    this.sex = sex;
}
//大人原型上添加方法
Adult.prototype.action = function() {
    console.log("ADULT傻逼");
}
//孩子的构造函数
function Kid(score) {
    this.score = score;
}
//原型链继承
Kid.prototype = new Adult("lyq", 12, 0);
//孩子原型上添加方法
Kid.prototype.study = function() {
    console.log("KID傻逼");
}
//实例化对象
var kid1 = new Kid(100);
console.log(kid1.name, kid1.age, kid1.sex, kid1.score);
kid1.action(); //获取Person的原型上面的方法
kid1.study(); //自己身上的原型方法
//实例化对象
var kid2 = new Kid(110);
console.log(kid2.name, kid2.age, kid2.sex, kid2.score);
kid2.action(); //获取Person的原型上面的方法
kid2.study(); //自己身上的原型方法
//实例化对象
var kid3 = new Kid(120);
console.log(kid3.name, kid3.age, kid3.sex, kid3.score);
kid3.action(); //获取Person的原型上面的方法
kid3.study(); //自己身上的原型方法
```

### call() 和 apply() 方法---借用其他对象的方法

- 面试官会经常问到的点

  call() 和 apply() ：借用其他对象的方法，并绑定this指向

- 语法：公式

  第一：对象1.方法.call(对象2);---注意方法一定不能加括号（）

  第二：对象1.方法.apply(对象2);---注意方法一定不能加括号（）

- 特点：

  我们 call() 和 apply() 不仅能借用其他对象的方法，还能改变this指向

  看call(第一个参数)或者apply(第一个)

```js
var kid1 = {
    name: "lyq",
    age: 12,
    action: function() {
        console.log(this.name + "会画画");
    }
}
var kid2 = {
    name: "wyf"
}
kid1.action.call(kid2); //wyf会画画
kid1.action.apply(kid2); //wyf会画画
```

- call() 和 apply() 的区别

```js
var kid1 = {
    name: "lyq",
    age: 12,
    action: function() {
        console.log(this.name + "会画画");
    },
    add: function(a, b) {
        return a + b;
    }
}
var kid2 = {
    name: "wyf"
}
//如果不传递参数，没有区别
//如果传递参数，call()后面的参数可以是任意的数据序列，而apply()必须是数组
console.log(kid1.add.call(kid2, 1, 2)); //3
console.log(kid1.add.apply(kid2, [1, 2])); //3
```

#### 4.原型链解决方法 --- 借用构造函数继承 --- call() --- 缺点：无法获取父类的方法

```js
//大人的构造函数
function Adult(name, age, sex) {
    this.name = name;
    this.age = age;
    this.sex = sex;
}
//大人原型上添加方法
Adult.prototype.action = function() {
    console.log("ADULT傻逼");
}
//孩子的构造函数
function Kid(name, age, sex, score) {
    Adult.call(this, name, age, sex);
    //缺少对象是因为window省略
    //完整版：window.Person.call(this);
    this.score = score;
}
//孩子原型上添加方法
Kid.prototype.study = function() {
    console.log("KID傻逼");
}
//实例化对象
var kid1 = new Kid("lyq", 12, 0, 100);
console.log(kid1.name, kid1.age, kid1.sex, kid1.score);//lyq 12 0 100
//实例化对象
var kid2 = new Kid("wyf", 22, 1, 110);
console.log(kid2.name, kid2.age, kid2.sex, kid2.score);//wyf 22 1 110
//实例化对象
var kid3 = new Kid("jkl", 24, 1, 120);
console.log(kid3.name, kid3.age, kid3.sex, kid3.score);//jkl 24 1 120
```

#### 5.组合式继承法（原型链继承 + 借用构造函数继承）--- 完美的工作用的继承

```js
//大人的构造函数
function Adult(name, age, sex) {
    this.name = name;
    this.age = age;
    this.sex = sex;
}
//大人原型上添加方法
Adult.prototype.action = function() {
    console.log("ADULT傻逼");
}
//孩子的构造函数
function Kid(name, age, sex, score) {
    Adult.call(this, name, age, sex);////////////////////////////////
    this.score = score;
}
//孩子原型链继承
Kid.prototype = new Adult();/////////////////////////////////////////
//孩子原型上添加方法
Kid.prototype.study = function() {
    console.log("KID傻逼");
}
//实例化对象
var kid1 = new Kid("lyq", 12, 0, 100);
console.log(kid1.name, kid1.age, kid1.sex, kid1.score);
kid1.action();
kid1.study();
//实例化对象
var kid2 = new Kid("wyf", 22, 1, 110);
console.log(kid2.name, kid2.age, kid2.sex, kid2.score);
kid2.action();
kid2.study();
//实例化对象
var kid3 = new Kid("jkl", 24, 1, 120);
console.log(kid3.name, kid3.age, kid3.sex, kid3.score);
kid3.action();
kid3.study();
```

### 测试底层

```js
function Kid(name, age, sex) {
    this.name = name;
    this.age = age;
    this.sex = sex;
}
Kid.prototype = {
    action: function() {
        console.log("lyq");
    }
}
var kid1 = new Kid();
console.log(kid1.constructor);
// 测试所有函数都是Function实例化（所有对象都是Object实例化）
console.log(Kid.constructor); //Function() { [native code] }
console.log(Kid.__proto__); // () --- 空函数
console.log(Function.prototype); // () ---空函数
//测试Functiond的父类 Function是上帝 --- 自己造自己
console.log(Function.constructor);//Function() { [native code] }
```

![image-20210821123136770](C:\Users\锋锋的沉默\AppData\Roaming\Typora\typora-user-images\image-20210821123136770.png)

### json格式的数据处理 --- ()圆括号语法

```js
//工作里面真正给我们模拟的数据大多数都是json格式的数据
//json格式的数据跟对象是一样的，就一点区别
//1.html：var Obj = {name:"lyq",age:12}
//2.json：var json = {"name":"lyq","age":12}
//总结：我们拿到json数据要转换成真正的对象来操作 --- ()圆括号语法
Number.prototype.add = function(num) {
    return this + num;
}
var num = 100;
var result = num.add(100);
console.log(result);
// console.log(100. add(100)); //报错
console.log((100).add(100)); //200
//json格式的对象也可以用()圆括号语法拿到数据
var kid = ({
    "name": "lyq",
    "age": 12
})
console.log(kid); //{name: "lyq", age: 12}
//总结：我们以后工作里面，拿到json数据第一件事就是()圆括号方法
```

### Object静态属性

> <u>1.Object.length：长度 形参的个数</u>
>
> <u>2.Object.name：方法的名字</u>
>
> <u>3.Object.assign()：将多个对象合并到一个对象中，并返回 --- 这也是创建对象的一种方式</u>
>
> <u>4.Object.create() 创建对象 --- 特点：创建没有原型链的对象</u>
>
> <u>5.Object.is()：判断两个参数是否相等  等同于 === 注意一下下面两个特殊情况</u>
>
> 6.Object.getOwnPropertyDescriptor()：获取对象指定的属性的描述对象
>
> 7.Object.getOwnPropertyDescriptors()：获取所有属性的描述对象
>
> <u>8.*Object*.defineProperty()：修改对象指定的属性的描述对象</u>
>
> <u>9.*Object*.defineProperties()：修改所有的属性的描述对象</u>
>
> 10.*Object*.keys()：获取除了不可枚举的属性外的所有属性的名称
>
> 11.*Object*.getOwnPropertyNames()：获取当前对象所有属性的名称，包括不可枚举的的属性
>
> 12.*Object*.isExtensible()：检查是否可扩展
>
> 13.*Object*.preventExtensions()：阻止扩展，但是可以删除,修改
>
> 14.*Object*.isSealed()：检查是否被密封，密封即不能添加和删除属性
>
> 15.*Object*.seal：密封当前对象，不可以添加和删除，但是可以修改
>
> 16.*Object*.isFrozen()：检查是否被冻结，冻结即不能添加，也不能删除
>
> 17.*Object*.freeze()：冻结对象，不可删除，添加，删除
>
> <u>18.*Object*.entries()：获取对象，以一对一数组的形式返回</u>

- Object.length：长度 形参的个数
- Object.name：方法的名字

- Object.assign()：将多个对象合并到一个对象中，并返回 --- 这也是创建对象的一种方式

```js
var kid = {
    name: "lyq",
    age: 12,
}
console.log(Object.assign(kid, { info: "信息" }, { action: "画画" }), { name: "wyf" });
```

- Object.create() 创建对象 --- 特点：创建没有原型链的对象

```js
var kid = Object.create(null);
console.log(kid.name = "lyq");//lyq
console.log(kid);//{name: "lyq"}
```

- Object.is()：判断两个参数是否相等  等同于 === 注意一下下面两个特殊情况

```js
//0 和 -0 比较
console.log(0 === -0);//true
console.log(Object.is(0, -0));//false
//NaN 和NaN 比较
console.log(NaN === NaN);//false
console.log(Object.is(NaN, NaN));//true
```

- Object.getOwnPropertyDescriptor()：获取对象指定的属性的描述对象

```js
var kid = {
    name: "lyq",
    age: 12
}
console.log(Object.getOwnPropertyDescriptor(kid, "name"));
//configurable: true 属性可配置型    false：当前属性不能被删除的   默认：true
//enumerable: true 可枚举   默认：ture   可以循环，遍历   如果是false就是不能被遍历循环
//value: "lyq" 当前属性的值
//writable: true 可写型   默认：true  是可以修改和添加   如果设置为false不能被修改了
```

- Object.getOwnPropertyDescriptors()：获取所有属性的描述对象

```js
var kid = {
    name: "lyq",
    age: 12,
    sex:0
}
console.log(Object.getOwnPropertyDescriptors(kid));
//age: {value: 12, writable: true, enumerable: true, configurable: true}
//name: {value: "lyq", writable: true, enumerable: true, configurable: true}
//sex: {value: 0, writable: true, enumerable: true, configurable: true}
```

- *Object*.defineProperty()：修改对象指定的属性的描述对象

```js
var kid = {
    name: "lyq",
    age: 12,
    sex: 0
}
Object.defineProperty(kid, "name", {
    configurable: false//修改为不可删除
})
console.log(delete kid.name);//false --- 删除失败
```

- *Object*.defineProperties()：修改所有的属性的描述对象

```js
var kid = {
    name: "lyq",
    age: 12,
    sex: 0
}
Object.defineProperties(kid, {
    name: {
        configurable: false,//修改为不可删除
        writable: false//修改为不可修改内容
    }
})
console.log(delete kid.name);//false --- 无法删除名字
kid.name = "wyf";//修改名字的内容
console.log(kid.name);//"lyq" --- 无法修改名字的内容
```

- *Object*.keys()：获取除了不可枚举的属性外的所有属性的名称

```js
var kid = {
    name: "lyq",
    age: 12,
    sex: 0
}
Object.defineProperties(kid, {
    name: {
        enumerable: false //把name属性修改为不可枚举类型（即不可循环，遍历）
    }
})
console.log(Object.keys(kid));//["age", "sex"] --- 因为name是不可枚举类型，所以没有输出
```

- *Object*.getOwnPropertyNames()：获取当前对象所有属性的名称，包括不可枚举的的属性

```js
var kid = {
    name: "lyq",
    age: 12,
    sex: 0
}
console.log(Object.getOwnPropertyNames(kid));//["name", "age", "sex"]
```

- *Object*.isExtensible()：检查是否可扩展

```js
var kid = {
    name: "lyq",
    age: 12,
    sex: 0
}
console.log(Object.isExtensible(kid));//true
```

- *Object*.preventExtensions()：阻止扩展，但是可以删除,修改

```js
var kid = {
    name: "lyq",
    age: 12,
    sex: 0
}
console.log(Object.preventExtensions(kid));
```

- *Object*.isSealed()：检查是否被密封，密封即不能添加和删除属性

```js
var kid = {
    name: "lyq",
    age: 12,
    sex: 0
}
console.log(Object.isSealed(kid));//false
```

- *Object*.seal：密封当前对象，不可以添加和删除，但是可以修改

```js
var kid = {
    name: "lyq",
    age: 12,
    sex: 0
}
Object.seal(kid);//密封kid
```

- *Object*.isFrozen()：检查是否被冻结，冻结即不能添加，也不能删除

```js
var kid = {
    name: "lyq",
    age: 12,
    sex: 0
}
console.log(Object.isFrozen(kid));//false
```

- *Object*.freeze()：冻结对象，不可删除，添加，删除

```js
var kid = {
    name: "lyq",
    age: 12,
    sex: 0
}
Object.freeze(kid);
```

- *Object*.entries()：获取对象，以一对一数组的形式返回

```js
var kid = {
    name: "lyq",
    age: 12,
    sex: 0
}
console.log(Object.entries(kid));
//["name", "lyq"]
//["age", 12]
//["sex", 0]
```



### 创建函数 --- 函数没有返回值，默认返回undefined

- 创建函数方式一

  ```js
  function kid() {
      console.log("你是不是傻逼");
  }
  kid();//你是不是傻逼
  ```

- 创建函数方式二

  ```js
  var kid = function() {
      console.log("你是傻逼吗");
  }
  kid();//你是傻逼吗
  ```

- 创建函数方式三 --- new方式

  ```js
  var kid = new Function("console.log('你为什么不是傻逼')");
  kid();//你为什么不是傻逼
  ```

  ```js
  var kid = new Function("a,b", "console.log(a + b)");
  kid(1, 2);//3
  ```




### Object原型成员和方法 --- 即Object.prototype

- constructor()：找父类 --- 获取创建的当前实例对象的构造函数

- isOwnProperty()：判断当前实例对象是否存在指定的“公有”属性 --- in可以检测“公有” 和 “私有” 属性

  ```js
  function Kid(name, age) {
      this.name = name;
      this.age = age;
  }
  var kid = new Kid();
  console.log(kid.hasOwnProperty("name")); //true
  ```

- isPrototypeOf()：判断当前对象是否正在指定对象的原型链中 

  ```js
  function Kid(name, age) {
      this.name = name;
      this.age = age;
  }
  var kid = new Kid("lyq",12);
  console.log(Kid.prototype.isPrototypeOf(kid)); //true
  console.log(Object.prototype.isPrototypeOf(kid)); //true
  console.log(Array.prototype.isPrototypeOf(kid)); //true
  ```

- propertyIsEnumerable()：判断属性是否为枚举类型

  ```js
  function Kid(name, age) {
      this.name = name;
      this.age = age;
  }
  var kid = new Kid("lyq", 12);
  console.log(kid.propertyIsEnumerable("name"));//true
  ```

- valueOf()

  > 基本包装类型：返回对应的值
  >
  > 引用类型：返回对象本身
  >
  > 日期类型：返回的是时间戳

  ```js
  var str = new String("lyq");
  console.log(str.valueOf()); //lyq -- 基本包装类型
  var obj = {
      name: "lyq",
      age: 12
  }
  console.log(obj.valueOf()); //{name: "lyq", age: 12} -- 引用类型
  var date = new Date();
  console.log(date.valueOf()); //1629791813589 -- 日期类型
  ```

- tostring()：返回数据格式字符串

  > 基本类型：返回对应值的字符串
  >
  > 数字类型：可以传递一个参数，指定转换为上面进制的数字字符串，二进制，八进制，十六进制
  >
  > 引用类型：返回[object Object]格式的字符串，object是对象的类型，Object为对象的构造函数

  ```js
  function Kid(name, age) {
      this.name = name;
      this.age = age;
  }
  var kid = new Kid("lyq", 12);
  console.log("demo".toString()); //demo -- 基本类型
  console.log((100).toString()); //100 -- 数字类型
  console.log((100).toString(2)); //1100100 -- 数字类型（二进制）
  console.log((100).toString(16)); //64 -- 数字类型（十六进制）
  console.log(kid.toString()); //[object Object] -- 引用类型
  ```

  ##### Object.prototype.toString.call(arr) --- 数组借用对象的toString方法

  ```js
  //面试官来了
  function Kid(name, age) {
       this.name = name;
       this.age = age;
  }
  var kid = new Kid("lyq", 12);
  var arr = [1, 2, "a"];
  console.log(arr.toString()); //1,2,a -- 发现引用类型arr返回的不是[object Array]
  console.dir(arr); //发现Array的原型链中也有toString()方法
  console.log(Object.prototype.toString() == Array.prototype.toString()); //false -- 对象和数组的toString方法是不一样的
  console.log(Object.prototype.toString.call(arr));//[object Array] -- arr借用Object的toString方法就可以了
  ```

  ##### 上面数组借用对象的toString方法引出：Array.isArray()方法是用来判断对象是否是数组类型，因为ES5存在的不兼容的问题，为了所有浏览器兼容封装一个函数

  ```js
  function isArray(arr) {
       if (arr.isArray) {
            return Array.isArray(arr);
       } else {
            return Object.prototype.toString.call(arr) == "[object Array]";
       }
  }
  console.log(isArray({})); //false --- 对象
  console.log(isArray([1, 2, 3, 4]));//true --- 数组
  ```

- toLocaleString()：将日期转换为通俗易懂的数据

  ```js
  var date = new Date();+
  console.log(date.toLocaleString());//2021/8/24 下午6:05:45
  ```




### 扩展：eval() --- 和function一样，他们的共同点都是把字符串转换为js代码

```js
var jsonStr = '({"name":"lyq","age":"12"})';
console.log(jsonStr);
console.log(eval(jsonStr)); //eval()可以把json数据转换为真正的对象格式的数据
console.log("1+3");//1+3
console.log(eval("1+3"));//4
```



### 扩展ES6的语法：构造函数

```js
class CreateKid {//有人把ES6的写法叫做语法糖
    //属性
    constructor(name, age) {
        this.name = name;
        this.age = age;
    }
    //构造函数上的方法，一般工作上不会用到，只要知道
    static action1() {
        console.log("我是在构造函数上的方法");
    }
    //原型链上的方法
    action2() {
        console.log("我是在原型链上的方法");
    }
}
//该怎么调用就怎么调用
var kid = new CreateKid("lyq", 12);
console.log(kid);
console.log(kid.name);
console.log(kid.age);
CreateKid.action1();//如果是构造函数上的方法要用构造函数名来调用
kid.action2();//原型链上的按正常调用
```

### ES6：构造函数的继承

```js
class Kid {
    constructor(name, age) {
        this.name = name;
        this.age = age;
    }
    eat() {
        console.log("吃饭饭");
    }
}
//继承 extends
class Adult extends Kid {//表示Adult继承了Kid
    constructor(name, age, sex) {
        super(name, age);//表示子类向父类传递参数
        this.sex = sex;
    }
    sleep() {
        console.log("睡觉觉");
    }
}
//实例化对象
var adult = new Adult("lyq", 12, 0);
console.log(adult);//Adult {name: "lyq", age: 12, sex: 0}
console.log(adult.name);//lyq
console.log(adult.age);//12
console.log(adult.sex);//0
adult.eat();//吃饭饭
adult.sleep();//睡觉觉
```

### 扩展一个作用域安全问题

- 问题

```js
function Kid(name, age) {
    this.name = name;
    this.age = age;
}
var kid = Kid("wyf", 22); //头昏眼花忘记写new了
console.log(kid); //undefined -- 出错
```

- 第一种方法解决（不够完美）

```js
function Kid(name, age) {
    if (this == window) {
        throw "请检查一边，你下面的代码没写new，如果忘了，记得加上，免得加班"//警示没加new
        return new Kid();//防止影响其他代码
    } else {
        this.name = name;
        this.age = age;
    }
}
var kid = Kid("wyf", 22); //头昏眼花忘记写new了
console.log(kid);
```

- 第二种方法解决

```js
function Kid(name, age) {
     if (!(this instanceof Kid)) {//更完美了
          // throw "请检查一边，你下面的代码没写new，如果忘了，记得加上，免得加班" //警示没加new
          return new Kid(); //防止影响其他代码
     } else {
          this.name = name; 
          this.age = age;
     }
}
var kid = Kid("wyf", 22); //头昏眼花忘记写new了
console.log(kid);
```

- 第三种方法 --- 在ES6里面提供一个方法new.target == undefined，就表示没有new

```js
function Kid(name, age) {
     if (new.target == undefined) {//更加超级完美了
          // throw "请检查一边，你下面的代码没写new，如果忘了，记得加上，免得加班" //警示没加new
          return new Kid(); //防止影响其他代码
     } else {
          this.name = name;
          this.age = age;
     }
}
var kid = Kid("wyf", 22); //头昏眼花忘记写new了
console.log(kid);
```

- 第四种方法 --- 第三种的缩写 undefined取反，就是true

```js
function Kid(name, age) {
     if (!(new.target)) {//最完美的
          // throw "请检查一边，你下面的代码没写new，如果忘了，记得加上，免得加班" //警示没加new
          return new Kid(); //防止影响其他代码
     } else {
          this.name = name;
          this.age = age;
     }
}
var kid = Kid("wyf", 22); //头昏眼花忘记写new了
console.log(kid);
```

### 混入式继承中的  “浅拷贝” 和 “深拷贝”

- 浅拷贝 --- 数据共存缺陷：被继承的对象中的对象和继承的对象的对象是同一个地址，所以改变这个，另外一个也会随之改变

![image-20210826200230435](C:\Users\nnf\AppData\Roaming\Typora\typora-user-images\image-20210826200230435.png)

```js
var kid = {
    name: "lyq",
    age: 12,
    like: {
        name: "wyf",
        age: 22,
    }
}
var adult = {};
for (var key in kid) {
    adult[key] = kid[key];
}
console.log(adult);
adult.like.name = "shabi";
console.log(kid);//kid中like对象的name也会随着adult改变而改变
```

- 深拷贝

![image-20210827104330661](C:\Users\nnf\AppData\Roaming\Typora\typora-user-images\image-20210827104330661.png)

```js
var kid = {
     name: "lyq",
     age: 12,
     like: {
          name: "wyf",
          age: 22,
     }
}
var adult = {};

function deepCopy(sourse, target) {
     for (var key in sourse) {
          //循环私有的属性，排除共有的原型链上的属性
          if (sourse.hasOwnProperty(key)) {
               //判断如果是引用类型另外处理，属性直接target[key] = sourse[key];
               if (typeof sourse[key] == "Object") {
                    //target[key] = {};
                    //target[key] = [];
                    //用三元运算符初始确定target引用类型是数组还是对象
                    target[key] = Array.isArray(sourse[key]) ? [] : {};
                    //引出递归：自己调用自己
                    deepCopy(sourse[key], target[key]);
               } else {
                    target[key] = sourse[key];
               }
          }
     }
}
deepCopy(kid, adult);
console.log(kid);
console.log(adult);
```

### 数组去重

```js
var arr = [1, 1, 1, 2, 3, 3, 4, 5, 5];
function distinctArray(arr) {
    var newArray = [];
    for (var i = 0; i < arr.length; i++) {
        if (newArray.indexOf(arr[i]) == -1) {
            newArray.push(arr[i]);
        }
    }
    return newArray;
}
var newArray = distinctArray(arr);
console.log(newArray);
```

### IIFF立即执行函数：自己调用自己的函数

- 自执行函数，一班用于初始化

```js
//自执行函数，一般用作初始化
//第一种方法
(function() {
    console.log("方法1");
})();
//第二种方法
(function() {
    console.log("方法2");
}());
// 第三种方法
! function() {
    console.log("方法3");
}();
// 第四种方法
+
function() {
    console.log("方法4");
}();
// 第五种方法
-
function() {
    console.log("方法5");
}();
// 第六种方法
~ function() {
    console.log("方法6");
}();
```

### 惰性函数：在函数中会进行一些分支判断或者初始化操作，然后将函数指向修改后的函数，再次执行这个函数的时候，执行的是修改之后的函数指向

```js
function foo() {
    console.log("我是js的初始化");
    foo = function() {
        console.log("真正的业务逻辑业务");
    }
}
//foo.des = "shabi";
//console.log(foo.des);//shabi
//第一次执行
foo();//我是js的初始化
//console.log(foo.des);//undefined
//第一次后面的执行
foo();//真正的业务逻辑业务
foo();//真正的业务逻辑业务
foo();//真正的业务逻辑业务
foo();//真正的业务逻辑业务
```

##### 扩展：如果想一直执行初始化，我们可以定义一个变量来接收，这样每次执行的都是初始化

```js
function foo() {
    console.log("我是js的初始化");
    foo = function() {
        console.log("真正的业务逻辑业务");
    }
}
// 扩展
var f = foo
f();//我是js的初始化
f();//我是js的初始化
f();//我是js的初始化
```

###  严格模式

1. 在严格模式下不允许使用未声明的变量

   ```js
   "use strict" //加上就回进入严格模式
   num = 100
   console.log(num)//num is not defined(num没定义)
   ```

2. 严格模式定义在脚本开头，会对整个js脚本都执行严格模式

   ```js
   "use strict" //加上就回进入严格模式
   function fun() {
        age = 100
   }
   fun()//age is not defined(age没定义)
   ```

3. 如果严格模式是定义在脚本开头，那么只会对当前整个函数起作用，对外面的代码没有影响

   ```js
   num = 100
   console.log(num)//100(正常)
   function fun(){
        "use strict" //加上就回进入严格模式
        age = 200//age is not defined(函数内age没定义)
   }
   fun()
   ```

4. 严格模式下要求函数参数名唯一

   ```js
   function sum(a,a,c){
        "use strict"
        return a + a + c
   }
   sum()//Duplicate parameter name not allowed in this context(有重复参数，报错)
   ```

5. 进制八进制数字语法

   ```js
   "use strict"
   var sum = 015 + 197 + 99
   console.log(sum);//Octal literals are not allowed in strict mode.(015是八进制数字)
   ```

6. 普通函数this指向---我们之前的没有严格模式下面指向window

   - 面试最多，在严格模式下this指向undefined

   ```js
   function fun() {
        "use strict"
        console.log(this);
   }
   fun()
   ```

### 闭包

- 在平时函数里面定义的变量值，在函数外拿不到它的值 --- 有个垃圾回收机制，当js运行的时候在计算机内部有一个“机器人”大约10秒钟（如果发现好长时间不用这个变量了，计算机会把这个标离给销毁掉）

  ```js
  function fun() {
      var num = 10;
      console.log(num);
  }
  fun()//10
  console.log(num);//num is not defined(函数外获取不到)
  ```

- 闭包的作用：为了缓存数据，想办法把数据保存下来就解决了

  - 优势：缓存数据
  - 劣势：内存泄露，溢出，占用内存

- 闭包语法：首先是函数套函数，子函数调用了父函数的变量，并且子函数被外界所引用，此时就形成了闭包。

  ```js
  function fun1() {
      var num = 10;
      function fun2() {
          return num
      }
      return fun2;//这里返回的是一个函数，所以记得加()
  }
  var replace = fun1()
  console.log(replace());//10
  ```

- 优化1

  ```js
  function fun1() {
      var num = 10;
      return function() {
          return num
      };//直接返回一个函数
  }
  var replace = fun1()
  console.log(replace());//10
  ```

- 当闭包需要多个变量时

  ```js
  function fun() {
      var a = 10
      var b = 20
      return [ //数组里面可以放函数
          function() {
              return a
          },
          function() {
              return b
          }
      ]
  }
  var f = fun() //先把fun函数赋给一个变量
  var a = f[0]()
  var b = f[1]()
  console.log(a, b);
  ```

- 优化2

  - 返回数组优化成返回对象

  ```js
  function fun() {
      var a = 10
      var b = 20
      return {//返回对象
          getA: function() {
              return a
          },
          getB: function() {
              return b
          }
      }
  }
  var f = fun()
  var a = f.getA()
  var b = f.getB()
  console.log(a, b);
  ```

- 优化3

  - 把对象中的函数独立到上面，这样可以想加就自己加

  ```js
  function fun() {
      var a = 10
      var b = 20
      function getA() {
          return a
      }
      function getB() {
          return b
      }//独立函数
      return {
          getA: getA,
          getB: getB
      }
  }
  var f = fun()
  var a = f.getA()
  var b = f.getB()
  console.log(a, b);
  ```

- 优化4

  - 想继续简化，不要上面的var f = fun()
  - 要用到 模块化开发 --- 工作中会大量使用模块化思想 -- 自执行函数()()

  ```js
  var modual = (function fun() //自执行函数
      var a = 10
      var b = 20
      function getA() {
          return a
      }
      function getB() {
          return b
      }
      return {
          getA: getA,
          getB: getB
      }
  })()
  var a = modual.getA()
  var b = modual.getB()
  console.log(a, b);
  ```

#### 闭包题目

- 使用闭包和定时器 实现输出 0 1 2 3 4 5 6 7 8 9

  ```js
  //按正常情况不行 会输出10个10
  for (var i = 0; i < 10; i++) { //有的人说for执行的快，定时器需要1秒（真正的原理：同步
      setTimeout(function() {
          console.log(i);//输出10个10  不满足
      }, 1000);
  }
  //第一种解决方法：自执行函数
  for (var i = 0; i < 10; i++) {
      setTimeout((function() {
          console.log(i);//0 1 2 3 4 5 6 7 8 9 但是还没有达到老板要求，没有闭包
      })(), 1000)
  }
  //第二种解决方法：闭包的应用场景，满足了面试官的需求了--缓存数据
  for (var i = 0; i < 10; i++) {
      function fun() {
          return function(i) {//这里的i为形参
              console.log(i);//0 1 2 3 4 5 6 7 8 9 满足老板要求
          }
      }
      setTimeout(fun(), 1000, i);//定时器的时间后面可以传递参数的 这里的i为实参
  }
  //第三种解决方法：直接使用闭包，把参数传递给父函数也是可以实现的
  for (var i = 0; i < 10; i++) {
      function fun(j) {
          return function() { //这里的i为形参
              console.log(j); //0 1 2 3 4 5 6 7 8 9 满足老板要求
          }
      }
      setTimeout(fun(i), 1000); //定时器的时间后面可以传递参数的 这里的i为实参
  }
  ```

- 想通过闭包实现点击哪个div显示哪个div

  - 第一种（错误）

    ```js
    var divs = document.getElementsByTagName("div")
    for (var i = 0; i < divs.length; i++) {
        divs[i].onclick = function() {
            console.log("我是第" + i + "个div");//这样无论点击哪个都是输出“我是第十个div”
        }
    }
    ```

  - 第二种（正确）

    ```js
    var divs = document.getElementsByTagName("div")
    for (let i = 0; i < divs.length; i++) {
        divs[i].onclick = (function(i) {//自执行函数 + 闭包
            return function() {
                console.log("我是第" + (i + 1) + "个0div");//点击哪个div显示哪个div
            }
        })(i);
    }
    ```

### 同步和异步

- 单线程和多线程
  - JS是单线程：同一时间只能执行一个任务
  - 操作系统是多线程的：C++
- 同步编程和异步编程
  - 同步编程(sync)---我们的任务会按照顺序一次执行，当前的任务没有完成，后面的任务是不会执行的（同一个时间只能做一个事情）我们的同步任务会放在主任务队列里面
  - 异步编程(async)---我们的JS当遇到异步任务的时候，不会停止任务，会吸纳把异步编程放到等待任务队列里面，程序会继续往下执行，先把主任务队列里面的程序执行完毕之后，并且到了等待时间，在继续去执行异步任务（“机器人去等待任务队列里面去找异步任务，找到异步任务之后要把异步任务放到主任务队列里面去执行"）

- JS里面哪些是同步哪些是异步呢？

  - JS的异步编程

    1. 定时器
    2. 点击事件，普通事件都是异步
    3. Ajax中一般也使用异步编程

    - 其余的都是同步的

  - JS的同步编程

    - 例1

      ```js
      var startTime = new Date()
      for (let i = 0; i < 100000000; i++) {
          if (i == 99999999) {
              console.log("no"); //第一次输出no(先)
          }
      }
      console.log(new Date() - startTime); //222(毫秒)
      console.log("ok"); //第二次输出ok(后)
      ```

    - 例2

      ```js
      while (1 == 1) {
      }
      console.log("ok");//上个任务还没执行完，所以没有输出
      ```

- 同步和异步的核心原理：（主任务队列和等待任务队列）
  - 主任务队列：同步编译
  - 等待任务队列：异步编译

- 便于理解同步和异步的故事
  - 小明：学完前端月薪上万，赚到钱了---开饭店（小时候的梦想）
  - 服务员：gg（必须只能找一个服务员---js是单线程）
  - 10:00 ：gg1来了  点了西红柿番茄炒蛋 --- 30分钟
  - 10:01 ：gg2来了  点了牛腩粉 --- 10分钟
  - 10:03 ：gg3来了  点了免费白开水 --- 1分钟
  - ......
  - 11:00 ：端菜 --- 先来白开水，然后牛腩粉，再西红柿炒蛋

- 例子

  ```js
  //异步
  setTimeout(() => {
      console.log("西红柿炒蛋");
  }, 50);
  setTimeout(() => {
      console.log("牛腩粉");
  }, 30);
  setTimeout(() => {
      console.log("白开水");
  }, 10);
  
  
  //同步
  for (let i = 0; i < 100000000; i++) {}
  console.log("我是同步");
  //我是同步
  //白开水
  //牛腩粉
  //西红柿炒蛋
  //总结：先执行同步，再执行异步
  ```

|                          主任务列表                          |                         等待任务队列                         |
| :----------------------------------------------------------: | :----------------------------------------------------------: |
| for (let i = 0; i < 100000000; i++) {}<br/>console.log("我是同步");<br/>然后一次机器人把等待任务列表的任务按时间放到主任务队列中<br/>setTimeout(() => {<br/>    console.log("白开水");<br/>}, 10);<br/>setTimeout(() => {<br/>    console.log("牛腩粉");<br/>}, 30);<br/>setTimeout(() => {<br/>    console.log("西红柿炒蛋");<br/>}, 50); | setTimeout(() => {<br/>    console.log("西红柿炒蛋");<br/>}, 50);<br/>setTimeout(() => {<br/>    console.log("牛腩粉");<br/>}, 30);<br/>setTimeout(() => {<br/>    console.log("白开水");<br/>}, 10); |

### 引入init对象初始化

- 正常对象

  ```js
  var obj = {
       name: "ff",
       age: "23",
       showName: function() {
       	console.log("姓名是：" + this.name);
       },
       showAge: function() {
       	console.log("年龄是：" + this.age);
       },
  }
  console.log(obj.name);
  console.log(obj.age);
  ```

- 添加init初始化的对象

  ```js
  var obj = {
      name: "默认值",
      age: "默认值",
      showName: function() {
          console.log("姓名是：" + this.name);
      },
      showAge: function() {
          console.log("年龄是：" + this.age);
      },
      init: function(name, age) {
          this.name = name
          this.age = age
      }
  }
  obj.init("ff", "23")//初始化
  console.log(obj.name);
  console.log(obj.age);
  ```

- 继续优化（把console.log省略）

  ```js
  var obj = {
      name: "默认值",
      age: "默认值",
      showName: function() {
          console.log("姓名是：" + this.name);
      },
      showAge: function() {
          console.log("年龄是：" + this.age);
      },
      init: function(name, age) {
          this.name = name
          this.age = age
              //还可以调用方法
          this.showName()
          this.showAge()
      }
  }
  obj.init("ff", "23")
  ```

### 设计模式

- 历史：设计模式是从建筑行业来的（我们叫做搬砖，码农）

- 常见的设计模式：单例模式，发布订阅模式（观察者模式），工厂模式（命名空间模式，代理模式 ...了解即可）

  #### 单例模式例子（一定要会的，经常用的只有这个）

  - 实例化对象

  ```js
  function Person() {
  }
  //实例化对象
  var p1 = new Person()
  var p2 = new Person()
  var p3 = new Person()
  var p4 = new Person()
  var p5 = new Person()
  //单例模式
  //输出全是false，因为每个都是新的实例化对象
  console.log(p1 === p2);//false
  console.log(p1 === p3);//false
  console.log(p2 === p3);//false
  console.log(p1 === p4);//false
  console.log(p2 === p5);//false
  ```

  - 上面先后实例化的对象判断不相同的解决方法

  ```js
  var _instance
  function Person() {
      if (_instance) {
          console.log("之前已经创建了对象，直接返回创建好的对象就可以了");
          return _instance
      }
      // 原理：因为我们这段代码执行了三部曲，所以p1，p2，p3不是同一个对象，每次new都会创建一个对象
      // 第一，默认的创建一个新对象 var obj = new Object()
      // 第二，默认的把这个对象赋值给this  this = obj
      // 第三，默认返回对象 return this
      _instance = this
      console.log("第一次创建对象");
  }
  //实例化对象
  var p1 = new Person()
  var p2 = new Person()
  var p3 = new Person()
  var p4 = new Person()
  var p5 = new Person()
  //单例模式
  console.log(p1 === p2);
  console.log(p1 === p3);
  console.log(p2 === p3);
  console.log(p1 === p4);
  console.log(p2 === p5);
  // 输出结果:
  // 第一次创建对象
  // 之前已经创建了对象，直接返回创建好的对象就可以了
  // 之前已经创建了对象，直接返回创建好的对象就可以了
  // 之前已经创建了对象，直接返回创建好的对象就可以了
  // 之前已经创建了对象，直接返回创建好的对象就可以了
  // true
  // true
  // true
  // true
  // true
  ```

  #### 发布订阅模式（观察者模式）

  - 发布订阅模式（观察者模式）
    举例：销售部的小姐姐---有新的房源了---发布者
    发布者：具有发布信息的能力
    客户1--->联系电话
    客户2--->联系qq
    客户3--->联系微信
    订阅者：--也有人叫做订阅模式（根据发布信息的状态，或者发布的信息，来采取一些的行

  ```js
  // 发布者发布信息：女神：Xinny  男生：Ben
  var Xinny = { //发布者
      eat: function() {
          console.log("我饿了")
          //让Ben和FF有了联系方式
          Ben.Ben_eat()//此时就有了联系方式，也有人叫做注册订阅者
          FF.FF_eat()
      },
  }
  // 订阅者：（观察者）对象 Ben
  var Ben = {
      Ben_eat: function() {
          console.log("邀请女神吃小龙虾！--- Ben")
      }
  }
  //订阅者（观察者）对象 FF
  var FF = {
      FF_eat: function() {
          console.log("邀请女生吃螺蛳粉! --- FF");
      }
  }
  Xinny.eat()
  ```

  #### 工厂模式（有点难，基本被淘汰，现在面试基本不会问到，了解即可）

  1. 提供一个构造函数（工厂模式）
  2. 设置构造函数原型对象（设置共同的属性和方法）
  3. 生产车间（在构造函数身上提供一个静态的工厂方法）
  4. 建立合作关系（定制合作关系 --- 签合同）
  5. 获取产品 --- 生产产品 --- 嗲用工厂模式，传递参数

  #### 命名空间模式

  - 以后我们的项目都会用模块化开发来写项目，我们的命名空间模式一般都是以项目的名字首字母大写来命名的。现在流行是模块化开发。 --- 了解即可

  ```js
  var GG = {}
  GG.a = 10
  GG.b = 20
  GG.obj = {
      name: 'ff',
      age: 23
  }
  GG.fun = function() {
      console.log('函数');
  }
  GG.Person = function() {
      this.name = 'ff'
  }
  console.log(new GG.Person());
  //总结：以上这种写法用大写字幕来命名的 --- 我们都叫做命名空间模式
  ```









# ES6

### 箭头函数

- <u>ES6中的箭头函数</u>

```js
const sum = (num1,num2) => {
     return num1 + num2
}
```

- 一个参数

```js
const power = num => {
     return num * num
}
```

- 只有一行代码

```js
const sum = (num1,num2) => num1 + num2

//等同于
const sum = (num1,num2) => {
     return num1 * num2
}
```

- 实例：计时器

```js
//原版
setTimeout(function(){
})

//箭头函数版
setTimeout(() => {
})
```

- 箭头函数中的this

```js
const obj = {
    aaa() {
         //普通函数
        setTimeout(function(){
            setTimeout(function(){
                console.log(this);//window
            });
            setInterval(() => {
                console.log(this);//window
            });
        })
         //箭头函数
        setInterval(() => {
            setTimeout(function(){
                console.log(this);//window
            });
            setInterval(() => {
                console.log(this);//obj
            });
        })
    }
}
```

### 箭头函数简化过程

- 普通函数

  ```js
  function fun(a) {
      return a + 1
  }
  ```

- 变成箭头函数

  ```js
  var fun = a => {
      return a + 1
  }
  ```

- 最终形态

  ```js
  var fun = a => a + 1
  ```

- 总结：去掉function关键字，小括号和{}之间有一个 =>，如果有一个可以省略小括号，如果函数体里面只有一行代码{}和return 可以同时省略

- 面试题

  ```js
  //把下面的函数变成箭头函数
  var a = b => {
      return c => {
          return b + c
      }
  }
  
  //简化后6
  var a = b => c => b + c
  ```

### 扩展filter方法（筛选）

- 过滤filter（函数）返回的是满足条件的每个元素，组成一个新数组---做过滤用的（有三个参数：第一个参数是每个元素ele，第二个参数是元素的索引，第三个参数是原数组---后面两个参数我们用不到是可以省略的）---应用场景：一般删除某些不符合条件的而用filter

  ```js
  var arr = [10, 20, 30, 40, 50, 60, 70, 80]
  var newArr = arr.filter(function(ele) {
      return ele > 40
  })
  console.log(newArr);//50 60 70 80
  ```

### 扩展forEach方法

- 便利数组用的 --- 相当于我们的for循环（但是forEach不支持return）

- 有三个参数：第一个参数元素，第二个参数索引，第三个参数数组本身，不需要可以省略

  ```js
  var arr = [10, 20, 30, 40, 50]
  arr.forEach(function(ele, index) {
      console.log(ele + "=====" + index);
  })
  //10=====0
  //20=====1
  //30=====2
  //40=====3
  //50=====4
  ```

- 面试官：问forEach和for有什么区别

  1. forEach不支持return
  2. for循环可以看作一步一步地实现 --- 叫做编程式，forEach不考虑内部怎么运行 --- 叫申明式，也不支持return

### 复习for in

- 有什么特点：循环遍历会把key变成字符串类型的，还会把数组的私有的和共有的都遍历循环

  ```js
  var arr = [10, 20, 30, 40, 50]
  for (var key in arr) {
      console.log(arr[key]);
  }
  //10
  //20
  //30
  //40
  //50
  ```

### 扩展for of

- 这个是ES6的，及支持return，又不会把key变成字符串

  ```js
  var arr = [10, 20, 30, 40, 50]
  for (var val of arr) {
      console.log(val);
  }
  //10
  //20
  //30
  //40
  //50
  ```

### 扩展map()

- 映射 --- map函数，回调函数return，返回什么，这一项就是什么，没有return，返回的是undefined（有三个参数，第一个参数是每个元素的值，第二个参数是元素的索引，第三个参数就是原数组 arr）

  ```js
  var arr = [10, 20, 30, 40, 50]
  var newArr = arr.map(function(ele, index) {
      console.log(ele, index)
          //10 0
          //20 1
          //30 2
          //40 3
          //50 4
      return ele *= 3
  })
  console.log(newArr);//[30, 60, 90, 120, 150]  
  ```

### 扩展ES6的方法

#### includes()

- ES6 includes() 判断数组有没有某一项，返回的是布尔类型，有就返回true，反之返回false

  ```js
  var arr = [1, 2, 3, 4, 5, 6]
  var result = arr.includes(5)
  console.log(result);//true
  ```

#### find()

- ES6 find() 返回找到的那一项，回调函数中如果返回true就表示找到了，找到后停止循环，如果找不到返回的是undefined

  ```js
  var arr = [1, 2, 3, 4, 5, 6, 66, 88]
  var result = arr.find(function(ele, index) {
      return ele > 5
  })
  console.log(result);//6
  ```

#### findIndex()

- 先遍历数组，回调函数返回true，停止查找，返回的是当前项的索引

  ```js
  var arr = ["hhhh", "别吧", 1, 2, 3, 4, 5, 6, 66, 88]
  var i = arr.findIndex(function(item) {
      return typeof item === "number"
  })
  console.log(i); //2
  ```


#### reduce()

- reduce有四个参数，返回的是叠加后的结果

  1. 第一个参数，上一个 prev 代表数组的第一项
  2. 第二个参数，下一个 nex嗲表数组的第二项
  3. 第三个参数，索引  index  代表数组的索引
  4. 第四个参数， 原数组  arr  代表的原数组

  ```js
  var arr = [1, 2, 3, 4, 5]
  var result = arr.reduce(function(prev, next, index, arr) {
      console.log(prev, next)
  })
  console.log(result);
  //1 2
  // undefined 3
  // undefined 4
  // undefined 5
  // undefined
  ```

- 总结：第二次循环的时候，prev是 undefined，next是数组的第三项，后面以此类推，因为没有加return，如果加了return返回值就不会是undefined

  ```js
  var arr = [1, 2, 3, 4, 5]
  var result = arr.reduce(function(prev, next, index, arr) {
      console.log(prev, next)
      return 100//加了返回值，prev第二次就不会是undefined（注意：本次的返回值会作为下一次prev）
  })
  console.log(result);
  // 1 2
  // 100 3
  // 100 4
  // 100 5
  // 100
  ```

- 一般我们<u>求合</u>用reduce()

  ```js
  var arr = [1, 2, 3, 4, 5]
  var result = arr.reduce(function(prev, next, index, arr) {
      return prev + next
  })
  console.log(result); //15
  ```
  
- 需求：还可以把两个数组合并成一个数组 --- 典型的二维数组

  ```js
  var flat = [
      [1, 2, 3],
      [4, 5, 6],
      [7, 8, 9]
  ].reduce(function(prev, next) {
      return prev.concat(next)
  })
  console.log(flat);//[1, 2, 3, 4, 5, 6, 7, 8, 9]  下·这就是把二维数组组合成一堆数组 --- 叫做数组的扁平化
  ```

- reduceRight 跟reduce 一样，只是顺序从右侧开始

### ES6新增 let 和 const 定义变量

- 定义变量以前我们用var，es6里面有两个 let 和 const

1. 预解析（变量提升）

   - var

     ```js
     console.log(a);
     var a//undefined  var能通过预解析，或者说变量提升结果是undefined
     ```

   - let

     ```js
     console.log(a);
     let a //报错
     ```

   - const

     ```js
     console.log(a);
     const a //报错
     ```

2. 会不会给window添加属性

   - let和const不会给window添加属性

3. 声明变量次数

   - var

     ```js
     var a = 12
     var a = 13
     console.log(a);//13
     ```

   - let

     ```js
     let a = 12
     let a = 13
     console.log(a); //报错
     ```

   - const

     ```js
     const a = 12
     const a = 13
     console.log(a); //报错
     ```

4. 必须赋值吗

   - var不必须
   - let不必须
   - const必须
   
4. 声明后是否能改

   - var

     ```js
     var a = 12
     a = 13
     console.log(a);//13
     ```

   - let

     ```js
     let a = 12
     a = 13
     console.log(a); //13
     ```

   - const

     ```js
     const a = 12
     a = 13
     console.log(a); //报错
     ```

#### 总结

|       | 预解析 | 是否可以给window添加属性 | 声明变量次数 | 必须赋值 | 声明后是否能重复改值 |
| :---: | :----: | :----------------------: | :----------: | :------: | :------------------: |
|  var  |   Y    |            Y             |     多次     |    F     |          Y           |
|  let  |   F    |            F             |      1       |    F     |          Y           |
| const |   F    |            F             |      1       |    Y     |          F           |

### 数组的解构赋值

- 如果想把数组中的值一个一个赋值给单独声明的变量，非常麻烦

  ```js
  let arr = [1,2,3,4,5]
  let x = arr[0]
  let y = arr[1]
  let z = arr[2]
  let m = arr[3]
  let n = arr[4]
  ```

- 引出解析复制 --- 大招

  ```js
  let arr = [1, 2, 3, 4, 5]
  let [x, y, z, m, n] = arr
  console.log(x, y, z, m, n);//1 2 3 4 5
  ```

- 如果后面的数组值不够，默认的是undefined

  ```js
  let [x, y, z, m, n] = [1, 2, 3]
  console.log(x, y, z, m, n); //1 2 3 undefined undefined
  ```

- 反过来，如果后面的数组值超过了，后面的数据就不接收了，丢掉即可

  ```js
  let [x, y, z, m, n] = [1, 2, 3, 4, 5, 6, 7, 8, 9]
  console.log(x, y, z, m, n); //1 2 3 4 5 
  ```


- 设置默认值，只有后面的解析值是undefined的时候，或者没有写的时候才会走默认值

  ```js
  let [x1,x2 = 10] = [1]
  console.log(x1,x2);//1 10
  ```


### 扩展块级作用域

- var没有块级作用域，而let和const有

- var

  ```js
  {
      var a = 23
  }
  console.log(a);//23 能访问到块级作用域里定义的值
  ```

- let 和 const

  ```js
  {
      let a = 23
      const b = 24
  }
  console.log(a); //a is not defined 不能访问到块级作用域里的值
  console.log(b); //b is not defined 不能访问到块级作用域里的值
  ```

- for循环例子

  - var

    ```js
    var liObjs = document.getElementsByTagName("li")
    for (var i = 0; i < liObjs.length; i++) {
        liObjs[i].onclick = function() {
            console.log(i); //点击哪个都是输出5
        }
    }
    ```

  - 用let解决问题， 

    ```js
    var liObjs = document.getElementsByTagName("li")
    for (let i = 0; i < liObjs.length; i++) { //用let定义i可以解决问题
        liObjs[i].onclick = function() {
            console.log(i); //点击哪个输出哪个的下标
        }
    }
    ```

  - 或者用自定义属性来解决

    ```js
    var liObjs = document.getElementsByTagName("li")
    for (let i = 0; i < liObjs.length; i++) {
        liObjs[i].index = i//通过自己自定义属性
        liObjs[i].onclick = function() {
            console.log(this.index);
        }
    }
    ```

### 对象解析结构

- 一般情况下调用对象

  ```js
  var obj = {
      name: "gg",
      age: "18"
  }
  console.log(obj.name);//gg
  console.log(obj.age);//18
  ```

- 如果变量名和属性名是一样的可以省略

  ```js
  let {name: name,age: age} = {name: "gg",age: 18}
  let {name,age} = {name:"gg",age:18}//简化版本
  console.log(name, age); //gg 18
  ```

- 对象里面设置默认值，只有后面解构的值是undefined的时候，或者没有的时候才回走默认值

  ```js
  let {name,age = 100} = {name:"gg",age:undefined}
  console.log(name, age);//gg 100
  ```

### 数组的解构赋值

- 类似于数组，工作里面很多人把字符串叫做类数组 -- 因为长得很像

  ```js
  let [a, b, c, d, e] = "hello"
  console.log(a, b, c, d, e);//h e l l o
  ```

- 测试题

  ```js
  let [a, b, c, d, e, length] = "hello world"
  console.log(length) //空  字符串是拿不到这个长度的
  ```

- 用对象的方式就可以拿到了

  ```js
  let {length} = "hello world"
  console.log(length)
  ```

### 扩展字符串方法

- includes() --- 判断字符串当中是否包含了指定的字符，如果有返回true，否则返回false语法格式：includes("指定的字符",开始查找的位置)

  ```js
  console.log("hello world".includes("world")); //true
  console.log("hello world".includes("world", 6)); //true
  console.log("hello world".includes("world", 7)); //false
  ```

- startsWith() --- 判断字符串是否以特定的字符串开始

- endsWith() --- 判断字符串是否以特定的字符串结束

  ```js
  let url = "admin/index.php"
  console.log(url.startsWith("admin"));
  console.log(url.startsWith("i", 3));
  console.log(url.endsWith("php"));
  console.log(url.endsWith("php", 15));//true  这个
  ```

### 扩展两个ES7的方法

- padStart 和 padEnd 按照指定字符补全字符串的指定长度

  - padStart()

    ```js
    var str = "ab"
    console.log(str.padStart(5, "ghkjjjj"));//ghkab
    ```

  - padEnd()

    ```js
    var str = "ab"
    console.log(str.padEnd(5, "ghkjjjj"));//abghk
    ```

### 调试 --- 断点

- 右键检查后，在console旁边的sourses，设置断点，然后刷新页面，就可以debug了

### ES6模板字符串

- 小斜点  `

- 加变量的时候直接加 ${变量}

  ```js
  let obj = {
      name: "gg",
      age: 18,
      sex: "nv"
  }
  // 正常情况
  var tag = "<div><span>" + obj.name + "</span><span>" + obj.age + "</span><span>" + obj.sex + "</span></div>"
  console.log(tag);
  // 小斜点情况
  var tpl = `<div><span>${obj.name}</span><span>${obj.age}</span><span>${obj.sex}</span></div>`
  console.log(tpl);
  ```

### 函数扩展

- 正常情况函数默认值

  ```js
  function fun(x, y) {
      x = x || "牛腩粉"
      y = y || "很好吃"
      console.log(x, y);
  }
  fun(1)//1 很好吃
  ```

- 面试题来了：但是代入值是0时表示空，没有覆盖默认值

  ```js
  function fun(x, y) {
      x = x || "牛腩粉"
      y = y || "很好吃"
      console.log(x, y);
  }
  fun(0)//牛腩粉 很好吃
  ```

- 解决方法：ES6语法

  ```js
  function fun(x = "牛腩粉", y = "很好吃") {
      console.log(x, y);
  }
  fun(0)//0 "很好吃"
  ```

- 继续扩展 --- 参数也是可以使用结构赋值

  - 首先小心这种情况

    ```js
    function fun({
        x = "牛腩粉",
        y = "很好吃"
    }) {
        //报错了  相当于{x = "牛腩粉",y = "很好吃"} = undefined
        console.log(x, y);
    }
    fun()
    ```

  - 改正

    ```js
    function fun({
        x = "牛腩粉",
        y = "很好吃"
    } = {}) {//让他等于一个空对象就可以了，相当于我们前面的解构赋值
        console.log(x, y);
    }
    fun() //牛腩粉 很好吃
    ```

- 函数length属性

  - 即当前的形参的个数

    ```js
    function fun(x, y) {
    }
    fun(1, 2)
    console.log(fun.length);//2
    ```

  - 特点：length属性，如果形参有默认值，length会失真

    ```js
    function fun(x = 3, y = 4) {
    }
    fun(1, 2)
    console.log(fun.length); //0
    ```

- arguments 伪数组 或者类数组 --- 可以拿到用户传递的参数个数

  ```js
  function fun() {
      console.log(arguments);//Arguments(6) [1, 2, 3, 4, 5, 6, callee: ƒ, Symbol(Symbol.iterator): ƒ]
  }
  fun(1, 2, 3, 4, 5, 6)
  ```

### 数组扩展

- Array() --- 数组方法

  ```js
  console.log(Array(1, 2, 3));//[1, 2, 3]
  ```

- 特殊情况 --- Array()的参数只有一个的时候，就会输出空值empty

  ```js
  console.log(Array(7));//[empty × 7]
  ```

- Array.of() --- 如果想输出单元素数组时的解决方法

  ```js
  console.log(Array.of(7));//[7]
  ```

- Array.from(数组/类数组) --- 返回的是一个数组 （类数组就是具备length属性）

  ```js
  console.log(Array.from([1, 2, 3, 4, 5])); //[1, 2, 3, 4, 5]
  console.log(Array.from("123")); //["1", "2", "3"]
  console.log(Array.from(document.getElementsByTagName('li'))); //[li, li, li, li, li]
  ```

- Array.copyWithin() --- 从原数组中读取内容，替换数组中指定位置的内容

  Array.copyWithin(替换的目标起始位置target，查找的起始位置begin，查找的结束位置end)

  ```js
  let arr = [1, 2, 3, 4, 5, 6, 7, 8]
  console.log(arr.copyWithin(4, 2, 4));//[1, 2, 3, 4, 3, 4, 7, 8]
  ```

- fill() --- 按照指定的字符串填充数组，将数组的每一项都变成指定的字符串

  ```js
  let arr1 = [1, 2, 3, 4, 5, 6, 7, 8]
  console.log(arr1.fill("gg"))//["gg", "gg", "gg", "gg", "gg", "gg", "gg", "gg"]
  let arr2 = [1, 2, 3, 4, 5, 6, 7, 8]
  console.log(arr2.fill("gg", 3, 5))//[1, 2, 3, "gg", "gg", 6, 7, 8]
  ```

### 数组的空位问题

- 数组的空位：数组的某个索引位置没有任何值

  ```js
  let arr = [, , , , , , ]
  console.log(arr.length); //6
  ```

- 注意undefined不是空值

  - 用in来测试数组指定索引位置有没有值，如果有就回返回true，如果没有就返回false

  ```js
  let arr = [, , , , , , ]
  console.log(1 in arr);//false
  ```

  ```js
  let arr = [, undefined, , , , , ]
  console.log(1 in arr); //true
  ```

- 继续扩展（例子：循环遍历）

  - ES5中数组方法对空位置处理不一致，一般直接跳过空位

    - filter()

      ```js
      let arr = [1, 2, , , , 3]
      arr.filter(function(item) {
          console.log(item);//1 2 3
      })
      ```

    - for in 循环

      ```js
      let arr = [1, 2, , , , 3]
      for (let key in arr) {
          console.log(arr[key]);//1 2 3
      }
      ```

  - ES6中会空位处理成undefined

    - find()

      ```js
      let arr = [1, 2, , , , 3]
      arr.find(function(item) {
          console.log(item);//1 2 undefined undefined undefined 3
      })
      ```

    - for of

      ```js
      let arr = [1, 2, , , , 3]
      for (const item of arr) {
          console.log(item);//1 2 undefined undefined undefined 3
      }
      ```

### 扩展运算符(点点点...)

- 可以将类数组具有length属性都变成数组

  ```js
  let st r = "123"
  console.log([...str]);//["1", "2", "3"]
  ```

- 可以将html获取到的<u>集合</u>变成数组

  ```js
  console.log([...document.getElementsByTagName("li")]);//[li, li, li, li, li]
  ```

- 可以将arguments类数组  变成数组

  ```js
  function fun() {
      console.log([...arguments]); //[1,2,3,4,5]
  }
  fun(1, 2, 3, 4, 5)
  ```

- 将两个数组合并，相倒concat，但是"点点点”更好用

  ```js
  let arr1 = [1, 2, 3, 4, 5]
  let arr2 = [10, 20, 30, 40, 50]
  console.log(arr1.concat(arr2));//[1, 2, 3, 4, 5, 10, 20, 30, 40, 50]
  console.log([...arr1, ...arr2]);//[1, 2, 3, 4, 5, 10, 20, 30, 40, 50] 点点点
  ```

- 求数组最大值

  ```js
  let arr = [1, 2, 3, 4, 5, 32, 45, 99]
  console.log(Math.max(arr)); //NaN
  
  //普通方法
  console.log(Math.max(1, 2, 3, 4, 5, 32, 45, 99)); //99
  
  //大招(点点点...)
  console.log(Math.max(...arr)); //99 
  
  //apply()方法
  console.log(Math.max.apply(null, arr));//99 不需要this 给null占个位
  
  //eval()方法
  console.log(eval("Math.max(" + arr + ")"));//99
  ```

### 对象扩展

- 键值对相同可以简写

  ```js
  let name = 'gg',
      age = 18
  let peo = {
      name,
      age
  }
  console.log(peo); //{name: "gg", age: 18}
  ```

- 如果对象中的属性是函数也可以简写

  ```js
  let obj = {
      fun1: function() {
          console.log('我是原始对象中的方法');//我是原始对象中的方法
      },
      fun2() {
          console.log('我是ES6对象中的方法');//我是ES6对象中的方法
      }
  }
  obj.fun1()
  obj.fun2()
  ```

### Symbol类型 --- ES6新增的类型，是一个新的基本数据类型，简单数据类型，值类型

- 使用Symbol函数执行得到一个Symbol数据类型，跟字符串类似，使用Symbol函数得到一个数据，<u>每一个都是完全不相同的</u>

  ```js
  let sym1 = Symbol()
  console.log(typeof sym1);
  //Symbol() 可以接受一个参数
  let sym2 = Symbol("foo")
  let sym3 = Symbol("foo")
  console.log(sym2 == sym3);//false 即使传递的参数一样的，值也是一样的，但就是不同
  ```

- Symbol诞生的作用：一般当作对象的属性（对象的属性如果重名了会覆盖，而我们的Symbol绝对不会覆盖的）任意的要给Symbol()得到的值都是不同的

  ```js
  let sym1 = Symbol()
  let sym2 = Symbol()
  let obj = {
      [sym1]: "牛腩粉"
  }
  obj[sym2] = "好好吃"
  console.log(obj)//{Symbol(): "牛腩粉", Symbol(): "好好吃"}
  ```

- Symbol()值是不可以转换为数字的，也是不可以进行字符串拼接的

  ```js
  Number(Symbol(1))//报错
  ```

- Symbol是可以转换为布尔的

  ```js
  console.log(!Symbol("1"));
  ```

- Symbol是可以嗲用toString方法，变成一个字符串

  ```js
  console.log(Symbol("gg").toString());//Symbol(gg)
  ```

- Symbol.for() 如果有相同参数的Symbol值，找到这个值并返回，如果没有就回创建一个新的Symbol

  ```js
  let demo1 = Symbol.for("hahaha")
  let demo2 = Symbol.for("hahaha")
  console.log(demo1 == demo2); //true 使用Symbol.for 如果参数相同，值就相同
  ```

- Symbol.keyFor() 找到Symbol.for创建的值，如果使用是Symbol创建的找不出来，结果是undefined

  ```js
  let sym = Symbol("wowowo")
  let demo = Symbol.for("hahaha")
  console.log(Symbol.keyFor(sym));//undefined
  console.log(Symbol.keyFor(demo));//hahaha
  ```

### Set类型 --- 类似数组，只有value，没有键key（跟我们对象不太一样，我们对象是键值对）

- 通过构造函数的方式创建Set示例 new

- 参数是一个数组（或者说是类数组，书本上还有说类数组是有 iterable 接口）

- 了解即可：那些有iterable接口？数组，arguments，元素集合，Set，字符串这些都有

  ```js
  console.log(new Set([1, 2, 3, 4, 5]));//{1, 2, 3, 4, 5}
  console.log(new Set("12345"));//{"1", "2", "3", "4", "5"}
  //arguments也是可以的
  function fun() {
      console.log(new Set(arguments));//{1, 2, 3, 4, 5}
  }
  fun(1, 2, 3, 4, 5)
  ```

- 会默认去重，如果有重复的项，会自动去掉

  ```js
  console.log(new Set([1, 1, 1, 1, 2, 2, 3, 4, 4, 4, 5]));//{1, 2, 3, 4, 5}
  ```

- 扩展原型方法：add，clear，delete，has，forEach，keys，values，entries

  - add() --- 添加，如果之前没有加上，有则不加，返回增加后的实例

    ```js
    let set = new Set([1, "牛腩粉", null, true])
    console.log(set.add(10)); //{1, "牛腩粉", null, true, 10}
    //可以实现链式操作 add 注意：里面的参数只能有一个，后面多加的不生效
    console.log(set.add(20).add(30, 40)); //{1, "牛腩粉", null, true, 10, 20, 30}
    ```

  - delete() --- 删除返回值：true/false  如果有这一项删除成功返回true，如果没有此项删除失败返回false

    ```js
    let set = new Set([1, "牛腩粉", null, true])
    console.log(set.delete(1));//true
    ```

  - clear() --- 清空 返回值是undefined

    ```js
    let set = new Set([1, "牛腩粉", null, true])
    console.log(set.clear());//undefined
    ```

  - has() --- 判断有没有此项，返回值true/false

    ```js
    let set = new Set([1, "牛腩粉", null, true])
    console.log(set.has(1));//true
    ```

  - forEach，keys，values，entries --- 循环遍历

    ```js
    let set = new Set([1, "牛腩粉", null, true])
    set.forEach((item,index,input) => {
        //Set实例只有value，没有key
        //item，index 都是当前项 value
        console.log((item,index));
    });
    ```

    

  





















## 补充

### 获取键盘的点击事件

```js
//示例为当前页面点击enter键
$(document).keyup(function(event) {
     if (event.keyCode == 13) {
          alert("你按下了enter(回车键)");
     }
});
```

| **字母数字** |      |      |      |      |      |      |      |
| ------------ | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| 按键         | 键码 | 按键 | 键码 | 按键 | 键码 | 按键 | 键码 |
| A            | 65   | J    | 74   | S    | 83   | 1    | 49   |
| B            | 66   | K    | 75   | T    | 84   | 2    | 50   |
| C            | 67   | L    | 76   | U    | 85   | 3    | 51   |
| D            | 68   | M    | 77   | V    | 86   | 4    | 52   |
| E            | 69   | N    | 78   | W    | 87   | 5    | 53   |
| F            | 70   | O    | 79   | X    | 88   | 6    | 54   |
| G            | 71   | P    | 80   | Y    | 89   | 7    | 55   |
| H            | 72   | Q    | 81   | Z    | 90   | 8    | 56   |
| I            | 73   | R    | 82   | 0    | 48   | 9    | 57   |

| **数字** |      |       |      | **功能键** |      |      |      |
| -------- | ---- | ----- | ---- | ---------- | ---- | ---- | ---- |
| 按键     | 键码 | 按键  | 键码 | 按键       | 键码 | 按键 | 键码 |
| 0        | 96   | 8     | 104  | F1         | 112  | F7   | 118  |
| 1        | 97   | 9     | 105  | F2         | 113  | F8   | 119  |
| 2        | 98   | *     | 106  | F3         | 114  | F9   | 120  |
| 3        | 99   | +     | 107  | F4         | 115  | F10  | 121  |
| 4        | 100  | Enter | 108  | F5         | 116  | F11  | 122  |
| 5        | 101  | -     | 109  | F6         | 117  | F12  | 123  |
| 6        | 102  | .     | 110  |            |      |      |      |
| 7        | 103  | /     | 111  |            |      |      |      |

| **控制键** |      |            |      |             |      |      |      |
| ---------- | ---- | ---------- | ---- | ----------- | ---- | ---- | ---- |
| 按键       | 键码 | 按键       | 键码 | 按键        | 键码 | 按键 | 键码 |
| BackSpace  | 8    | Esc        | 27   | Right Arrow | 39   | -_   | 189  |
| Tab        | 9    | Spacebar   | 32   | Dw Arrow    | 40   | .>   | 190  |
| Clear      | 12   | Page Up    | 33   | Insert      | 45   | /?   | 191  |
| Enter      | 13   | Page Down  | 34   | Delete      | 46   | `~   | 192  |
| Shift      | 16   | End        | 35   | Num Lock    | 144  | [{   | 219  |
| Control    | 17   | Home       | 36   | ;:          | 186  | \|   | 220  |
| Alt        | 18   | Left Arrow | 37   | =+          | 187  | ]}   | 221  |
| Cape Lock  | 20   | Up Arrow   | 38   | ,<          | 188  | '"   | 222  |

### 获取本文件的文件名

```js
function loca() {
     var a = location.href.split('/');
     var b = a[a.length - 1];
     var c = b.slice(10, 11);
     return c;
}
```

### joIn函数解决遍历打印最后留下的小尾巴

- join('数组每个元素中间想加的内容')

```js
var arr = ['你牛逼','我牛逼','大家都牛逼'];
console.log(arr.join(' - '));
```

