# jquery笔记

### 导入cdn

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.6.0/jquery.min.js"></script>
```

### vscode中没有jquery的提示代码

- 在项目根目录建一个 `jsconfig.json`，并在里面写内容：

```js
{
  "exclude": ["node_modules"],
  "typeAcquisition": {
    "include": [
      "jquery"
    ]
  }
}
```

### jq的入口函数，相当于js中的“windows.onload=function(){}”

```js
$(document).ready(function{
	//内容
});
```

```js
//简写版
$(function(){
     //内容
})
```

### 基本选择器

- 标签选择器

  ```js
  $("div")
  ```

- ID选择器：获取指定id元素

  ```js
  $("#id")
  ```

- 类选择器：获取同一类class元素

  ```js
  $(".dv")
  ```

- 通配符选择器：获取所有元素  很少用

  ```js
  $("*")
  ```

- 并集选择器：使用逗号分隔

  ```js
  $(".dv,.btn")
  ```

- 后代选择器：空格 （子代和后代都选中） $("li p")

  - \>：大于号子代选择器,获取儿子层级的,注意不会获取孙子层级 

    ```js
    $("1i>p")
    ```

  - \+：加号紧邻选抒器选择one卜面的第个邻居  

    ```js
    $(".one+li")
    ```

  - \~：兄弟姐妹选择器选择one下面的所有的邻居

    ```js
    $(".one~li"）
    ```

### 过滤选择器

- :first选择满足条件的第一个元素$("li:first")---选择第一个li

  ```js
  $("li:first")
  ```

- :last选择满足条件的最后一个元素---选择最后一个li

  ```js
  $("li:last")
  ```

- :even偶数获取的是li元素索引值为奇数的元素，因为从e开始的

  ```js
  $("li:even")//获取奇数
  ```

- :odd奇数获取的是li元素索引值为偶数的元素,因为从e开始的

  ```js
  $("li:odd")//获取偶数
  ```

- :eq(index)获取到第几个li元素，索引值index 从e开始

  ```js
  $("li:eq(index)")
  ```

### 获取索引值

```js
$('dv').index();
```

- index()偶尔获取的值全部为-1，那是因为找不到所有兄弟节点的位置

  ```js
  //原来：
  $(" ul li").click(function(){
  alert($(this).index()); 
  });
  //解决办法（也就是将this放到index()里面去,才能找到具体的索引）：
  $(" ul li").click(function(){
  alert($("ul li").index(this));  
  });
  ```

### 筛选选择器

- .eq(index)选择第N个元素index 从e开始$("li").eq(2)

  ```js
  $('div').eq(index)
  ```

-  parent()查找父类$("li").parent()

  ```js
  $('div').parent()
  ```

- .children(o选择孩子$("li").children()

  ```js
  $('div').children()
  ```

- .siblings(）这个强大啊，这个就是典型的排他思想，选抒兄弟，不分上下都是兄弟，这个用的特别多

  ```js
  $('div').siblings()
  ```

### 隐藏，显示，切换，上滑，下滑，切换滑动

- .show(1000)
- .hide(1000)
- .toggle(1000)
- .slideDown(1000)
- .slideUp(1000)
- .slideToggle(1000)

- 执行完后可以执行回调函数
  - hide(1000,function(){});

```html
<!DOCTYPE html>
<html>

<head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width,initial-scale=1.0">
    <title>sailormoon</title>
    <style>
        #hhh {
            display: none;
            width: 305px;
            height: 100px;
            background-color: rgb(8, 78, 110);
        }
    </style>
</head>

<body>
    <button id="xs">显示</button>
    <button id="yc">隐藏</button>
    <button id="qh">切换</button>
    <button id="xh">下滑</button>
    <button id="sh">上滑</button>
    <button id="qhhd">切换滑动</button>
    <div id="hhh"></div>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.6.0/jquery.min.js"></script>
    <script>
        $('#xs').click(function() {
            $('#hhh').show(1000);
        })
        $('#yc').click(function() {
            $('#hhh').hide(1000);
        })
        $('#qh').click(function() {
            $('#hhh').toggle(1000);
        })
        $('#xh').click(function() {
            $('#hhh').slideDown(1000);
        })
        $('#sh').click(function() {
            $('#hhh').slideUp(1000);
        })
        $('#qhhd').click(function() {
            $('#hhh').slideToggle(1000);
        })
    </script>
</body>

</html>
```

### 判断div show的状态

```js
var temp= $("#test").is(":hidden");//是否隐藏 

var temp1= $("#test").is(":visible");//是否可见 
```

###  淡出淡入

- .fadeIn(1000) --- 淡入
- .fadeOut(1000) --- 淡出
- .fadeToggle(1000) --- 切换淡出淡入
- .fadeTo(1000,0.5) --- 第一个参数是时间，第二个参数是透明度，这是固定格式，不能省略透明度

```html
<!DOCTYPE html>
<html>

<head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width,initial-scale=1.0">
    <title>sailormoon</title>
    <style>
        #hhh {
            width: 305px;
            height: 100px;
            background-color: #084e6e;
        }
    </style>
</head>

<body>
    <button id="btn1">淡入</button>
    <button id="btn2">淡出</button>
    <button id="btn3">切换淡出淡入</button>
    <button id="btn4">透明度</button>
    <div id="hhh"></div>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.6.0/jquery.min.js"></script>
    <script>
        $('#btn1').click(function() {
            $('#hhh').fadeIn(500);
        })
        $('#btn2').click(function() {
            $('#hhh').fadeOut(500);
        })
        $('#btn3').click(function() {
            $('#hhh').fadeToggle(500);
        })
        $('#btn4').click(function() {
            $('#hhh').fadeTo(500, 0.5);
        })
    </script>
    <script src="./jq.js"></script>
</body>

</html>
```

### 获取组件中的html内容

- .html() --- 相当于原生js中innerHTML
- 把jQuery对象转换为DOM对象的两个方法
  - [0]
  - .get(0)

```js
$('div').innerHTMl//不可以，因为innerHLML是原生js的
$('div').html()//jq自带的方法
$('div')[0].innerHTML//这样就是把jQuery对象转换为DOM对象
$('div').get(0).innerHTML//这样就是把jQuery对象转换为DOM对象
```

### 获取组件中的text内容

- .text()

```js
$('div').text()
```

### 获取表单的值

- .val()

```js
$('input').val();
//想让input中的值为空
$('input').val('');
```

### 把jQuery对象转换为DOM对象

- $(DOM对象)

```js
var btn = document.getELementGetId('btn');
$(btn).click(function({}));
```

### 鼠标事件方法，点击事件等

- click() --- 单击事件

- dbclick() --- 双击事件

- mousedown() --- 按下事件

- mouseup() --- 弹起事件

- mouseenter(),mouseover() --- 移入事件

- mouseleave(),mouseout() --- 移出事件

- hover() --- mouseenter() 和 mouseleave() 两个连在一起可以用这个来代替

- mousemove() --- 鼠标移动事件

  ```html
  <!DOCTYPE html>
  <html>
  
  <head>
      <meta charset="utf-8">
      <meta name="viewport" content="width=device-width,initial-scale=1.0">
      <title>sailormoon</title>
      <style>
          #hhh {
              width: 305px;
              height: 100px;
              background-color: #084e6e;
          }
      </style>
  </head>
  
  <body>
      <div id="hhh"></div>
      <script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.6.0/jquery.min.js"></script>
      <script>
          $('#hhh').hover(function() {
              $('#hhh').css('backgroundColor', '#555555');
          }, function() {
              $('#hhh').css('backgroundColor', '#084e6e');
          })
      </script>
      <script src="./jq.js"></script>
  </body>
  
  </html>
  ```

### 鼠标移动事件 + 获取鼠标坐标

- mousemove()

```js
$('html').mousemove(function(event) {
    var x = event.pageX;
    var y = event.pageY;
    console.log(x + " " + y);
})
```

### 页面滚动的事件

```js
$(window).scroll(function() {
     //内容
})
```

### <u>bind方法</u>

- 直接绑定事件

```js
$('#dv').bind('click', function() {
     //事件内容
})
```

- 链式绑定

```js
$('#dv').bind('click', function() {
    //点击事件
}).bind('mouseenter', function() {
    //鼠标移入事件
}).bind('mouseleave', function() {
    //鼠标移出事件
})
```

- 用对象的链式绑定

```js
//示例
$('#dv').bind({
    'click': function() {
        //点击事件
    },
    'mouseenter': function() {
        //鼠标移入事件
    },
    'mouseleave': function() {
        //鼠标移出事件
    },
})

//但是当使用的事件方法一样时，只能执行最后一个事件
$('#dv').bind({
    'click': function() {
        console.log('我是第一个事件');
    },
    'click': function() {
        console.log('我是第二个事件');
    },
    'click': function() {
        console.log('我是第三个事件');
    },
})
//只输出第三个事件
```

- 解绑bind方法 --- unbind()

```js
//用法
$('#dv').unbind('click');

//可以解绑指定组件
$('#dv').unbind('click','div');//只解除div的事件

//如果unbind()里面什么都不写,相当于把全部事件解绑
$('#dv').unbind();

//示例
$('#btn1').click(function() {
     $('#dv').bind('mouseenter', function() {
          $('#dv').css('background', 'black');
     }).bind('mouseleave', function() {
          $('#dv').css('background', 'pink');
     })
});
$('#btn2').click(function() {
     //unbind()扩展里面还可以写多个参数，中间用空格隔开
     $('#dv').unbind('mouseenter mouseleave');
})

//复合写法
$('#dv').unbind('click mouseenter mouseleave','div');
```

### <u>delegate方法</u>

```js
$('#btn').click(function() {
     //把子元素的事件委托给了父级元素
     $('#dv').delegate('span', 'click', function() {
         //事件
     })
})
```

- 解绑delegate方法

```js
$('#dv').undelegate('click');
```

### <u>on方法</u> --- 当组件是后来用js通过点击或者其他事件主动导进的时候，新增的组件通过click等点击方法进行的事件是无效的，所以要用on方法

- on方法绑定事件

```js
$('dv').on('click','.note',function(){
     //点击新添加组件的事件
})
```

- 解绑on方法

```js
$('#dv').off('click');

//扩展 --- 加个逗号可以指定解除哪个指定组件的事件
$('#dv').off('click','p');
```

### 排队机制，当鼠标事件重复做很多次，jq会把动作排队一个一个实现，可以加  .stop()  来停止排队中的事件

```js
$('btn').click(function(){
     $('dv').stop().slideDown();
})
```

### 修改组件的css

- css("width") --- 返回属性的值
- css("width","300px") --- 改变该属性的值
- css({"width","300px","height","300px"}) --- 改变多组属性的值

### 添加css样式

- hasClass() --- 判断有没有css类
- addClass() --- 添加css类
- removeClass() --- 删除css类
- toggleClass() --- 添加/关闭  类切换

### jq中可以一个对象使用对个方法

```js
$('div').click(function(){}).dblclick(function(){});
```

### 修改组件的属性

```js
$('div').attr('属性','值');
```

- 和css方法相似，也能用对象修改多个属性

```js
$('div').attr({
     '属性':'值',
     '属性':'值'
});
```

### 从前后添加元素

- append() --- 在被选元素的结尾插入内容
- prepend() --- 在被元素的开头插入内容
- a.appendTo(b) --- 把a加到b的里面（后面追加）
- a.prependTo(b) --- 把a加到b的里面（前面追加）
- after() --- 在被选元素之后插入内容
- before() --- 在被选元素之前插入内容

```js
$("p").append("Some appended text.");
$("p"). prepend("Some prepended text.");
$("img").after("Some text after");
$("img"). before("Some text before");
```

### 创建元素

```js
var div = $('<div></div>').text("牛腩粉");
$('#app').append(div);
```

### 删除元素

- remove() --- 删除被选元素（及其子元素）
- empty() --- 从被选元素中删除子元素

```js
$('div').empty();
$('div').remove();
$('div').remove('.app');//可以指定删除class名为app的div
```

### 遍历循环 --- 相当于for循环

- $('dv').each(function(index,ele){})

```js
$('#left li,#right li').each(function(index,ele){
     //index 返回的是索引值---等价于$(this).index()
     //ele 返回的是某个元素---element
     console.log(index);
})
```

### animate动画效果，平移，变大变小，变宽变长

- 平移

```js
$('#dv').animate({'left':'100px'},1000)
```

- 变长

```js
$('#dv').animate({"width": "100px"}, 1000)
```

- 可以复合写法

```js
$('#dv').animate({
     'left':'100px'
},1000).animate({
     "width": "100px"
}, 1000)
```

### 扩展一个find方法，方便处理

- 找到后代中class为note的所有组件

```js
$('#dv').find('.note')
```

### 图片跟随鼠标移动，cursor

```html
<!DOCTYPE html>
<html>

<head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width,initial-scale=1.0">
    <title>sailormoon</title>
    <style>
        * {
            margin: 0;
            padding: 0;
        }
        
        #cursor {
            position: relative;
            width: 50px;
            height: 50px;
            background-color: rgb(255, 155, 177);
        }
    </style>
</head>

<body>
    <div id="cursor"></div>
    <script src="jquery-3.6.0.min.js"></script>
    <script>
        $(function() {
            $('html').mousemove(function(event) {
                var x = event.pageX - 25;
                var y = event.pageY - 25;
                $('#cursor').css({
                    "left": x,
                    "top": y
                })
            })
        })
    </script>
</body>

</html>
```

### 获取页面被卷上去的距离

```js
$(window).scrollTop()
```

### 获取组件的高度宽度

- 高度

```js
$('#dv').height();//实际高度
$('#dv').innerHeight();//实际高度+内边距
$('#dv').outerHeight();//实际高度+内边距+边框
$('#dv').outerHeight(true);//实际高度+内边距+边框+外边框
```

- 宽度

```js
$('#dv').width(); //实际宽度
$('#dv').innerWidth(); //实际宽度+内边距
$('#dv').outerWidth(); //实际宽度+内边距+边框
$('#dv').outerWidth(true); //实际宽度+内边距+边框+外边框
```

### 获取盒子div到页面的距离

- 盒子到页面左侧的距离

```js
$('#dv').offset().left
```

- 盒子到页面顶部的距离

```js
$('#dv').offset().top
```

### 冒泡

- 阻止冒泡

```js
//js原生方法
e.stopPropagation();
//jq的方法
return false;
```

```html
<!DOCTYPE html>
<html>

<head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width,initial-scale=1.0">
    <title>sailormoon</title>
    <style>
        * {
            margin: 0;
            padding: 0;
        }
        
        #dv1 {
            position: absolute;
            width: 300px;
            height: 300px;
            background-color: pink;
        }
        
        #dv2 {
            position: absolute;
            width: 200px;
            height: 200px;
            background-color: greenyellow;
        }
        
        #dv3 {
            position: absolute;
            width: 100px;
            height: 100px;
            background-color: red;
        }
    </style>
</head>

<body>
    <div id="dv1">
        <div id="dv2">
            <div id="dv3"></div>
        </div>
    </div>
    <script src="jquery-3.6.0.min.js"></script>
    <script>
        $(function() {
            $('#dv1').click(function() {
                console.log('第一个事件');
            });
            $('#dv2').click(function() {
                console.log('第二个事件');
            });
            $('#dv3').click(function(e) {
                console.log('第三个事件');
                // e.stopPropagation();//js原生写法
                return false;//jq的写法
            });
        })
    </script>
</body>

</html>
```

### 轮播图

- 左右两个切换按键获取轮播图索引值时可用

```js
//原生js
var $key = 0;
$key--;
if(key > 4){
     $key = 0;
}

//jq新的方法
$key = $key % $("li").length;
```

### 音乐播放和暂停

```js
//暂停
$('#radio').pause();
//播放
$('#radio').play();
```

### jQuery的顶级对象是$（如果不小心把这个当作变量来用，下面的jquery就不能用了）

```js
//例子：假设先用$设成对象
var $ = 10;
console.log($);//10，输出正常，但是后面jquery就不能用了

//第一种解决方法：直接把 $ 换成 jQuery
jQuery(function({
     jQuery('#btn').click(function(){
          console.log("大家维续给力,我们要扩展");
     })
})

//第二种解决方法：把 $ 的权利让给 nnf
var nnf = $.noConflict();
var $ = 10;
console.log($);
nnf(function(){
     nnf('#dv').click(function(){
          console.log('傻仔');
     })
})
```



## 扩展

### 合并数组

- .concat(数组,数组,数组)

```js
var arr1 = [10,20];
var arr2 = [30,40];
console.log(arr1.concat(arr2));
```

### 筛选数组

- every筛选

```js
//第一个例子
var arr = [10,20,30];
//有三个参数
// 1 --- a ：元素的值
// 2 --- b ：元素的索引
// 3 --- c ：谁调用了这个方法就是谁
var flag = arr.every(function(a,b,c){
     //console.log(arguments.length);
     //console.log(a + " " + b + " " +c);
     return a > 20;//判断数组中是否有大于20的数，有返回false，没有返回true
})
console.log(flag);//false，因为数组中有大于20的数

//第二个例子
var array = ['jkjkjkjkjk','hshshshshs','dndndndndndn'];
var result = array.every(function(ele,index,tmp){//index和tmp一般不用可以省略
     return ele.length > 5;
})
console.log(result);//true，所有元素的长度都大于5
```

