

# JS笔记

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

### 获取数据变量

```js
typeof num
typeof (num)
```

### 五个数据类型

```js
number,string,boolean,null,underfined
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
console.log(age1 - age2);//5
console.log(age1 * age2);//50
console.log(age1 / age2);//2
console.log(age1 % age2);//0
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

### 输出在界面

```js
document.write("我好帅");
```

### break和continue

```js
break;//直接终止循环
continue;//直接跳出此次循环，跳到下一次循环
```

### 反转数组

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

### 函数自调用

```js
(function(){
  console.log("函数自调用")
 })()
```

### 伪元素（不需要形参了，优化代码）

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
//第二，变量提升，只提升等号左边的，不会提升等号后面的
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

//示例2
var foo = 1;
function fun(){
     if(!foo){
          var foo = 10;
     }
     console.log(foo);
}
fun();

//伪函数
var foo = 1;
function fun(){
     var foo;
     if(!foo){
          foo = 10j;
     }
     console.log(foo);
}
fun();
```

