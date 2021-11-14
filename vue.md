

# Vue.js笔记

### 导入cdn的包 （版本号：Vue.js v2.5.21）

```html
<script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.min.js"></script>
```

### 导入网络请求库（版本号：axios v0.21.4）---下面“网络应用”才会用到

```html
<script src="https://unpkg.com/axios/dist/axios.min.js"></script>
```

### vue的7种属性

- el属性

- - 用来指示vue编译器从什么地方开始解析 vue的语法，可以说是一个占位符。

- data属性

- - 用来组织从view中抽象出来的属性，可以说将视图的数据抽象出来存放在data中。

- template属性

- - 用来设置模板，会替换页面元素，包括占位符。

- methods属性

- - 放置页面中的业务逻辑，js方法一般都放置在methods中

- render属性

- - 创建真正的Virtual Dom

- computed属性

- - 用来计算

- watch属性

- - watch:function(new,old){}
  - 监听data中数据的变化
  - 两个参数，一个返回新值，一个返回旧值，



### 第一个vue文件

```html
<!DOCTYPE html>
<html>

<head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width,initial-scale=1.0">
    <title>sailormoon</title>
</head>

<body>
     ----------------------------------------------------------------
    <div id="app">
        {{ message }}
    </div>
    <script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.min.js"></script>
    <script>
        var app = new Vue({
            el: "#app",
            data: {
                message: "Hello Vue.js!"
            }
        })
    </script>
     ----------------------------------------------------------------
</body>

</html>
```

### v-text：控制值

- 缩写写法：{{data}}

```html
<div id="app">
     <h1 v-text="message"></h1>
     {{message}}
</div>
<script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.min.js"></script>
<script>
     var app = new Vue({
          el: "#app",
          data: {
               message: "你是煞笔"
          },
     })
</script>
```

### v-bind：动态绑定一个或多个属性attribute

- 缩写：:+属性

```html
<div id="dv">
     <!--绑定title属性-->
     <span v-bind:title="message">你是煞笔吗</span>
     <!--简化版-->
     <span :title="message">你是煞笔吗</span>
</div>
<script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.min.js"></script>
<script>
     var vm = new Vue({
          el: "#dv",
          data: {
               message: "yes",
          },
     })
</script>
```

### v-if，v-else-if，v-else：条件语句

```html
<div id="app">
     <h1 v-if="ok">Yes</h1>
     <h1 v-else>No</h1>
</div>
<script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.min.js"></script>
<script>
     var vm = new Vue({
          el: "#app",
          data: {
               ok: true
          }
     })
</script>
```

```html
<div id="app">
     <h1 v-if="type==='A'">A</h1>
     <!-- cdn2.1.0版本之后才有else-if-->
     <h1 v-else-if="type==='B'">B</h1>
     <h1 v-else-if="type==='C'">C</h1>
     <h1 v-else="type==='D'">D</h1>
</div>
<script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.min.js"></script>
<script>
     var vm = new Vue({
          el: "#app",
          data: {
               type: 'A'
          }
     })
</script>
```

### v-for：循环遍历

```html
<div id="app">
     <li v-for="item in items">
          {{item.message}}
     </li>
</div>
<script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.min.js"></script>
<script>
     var vm = new Vue({
          el: "#app",
          data: {
               items: [
                    {message: "小屁孩日记"}, 
                    {message: "圣经"}, 
                    {message: "山海经"}
               ]
          }
     })
</script>
```

- 可以加index

```html
<div id="app">
     <li v-for="(item,index) in items">
          {{index+1}}{{item.message}}
     </li>
</div>
<script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.min.js"></script>
<script>
     var vm = new Vue({
          el: "#app",
          data: {
               items: [{
                    message: "小屁孩日记"
               }, {
                    message: "圣经"
               }, {
                    message: "山海经"
               }]
          }
     })
</script>
```



### v-on：事件绑定

- 各种事件--https://www.cnblogs.com/torchstar/p/11799394.html

- "v-on:" 可以简化为"@"

| 按键                | 作用                                       |
| ------------------- | ------------------------------------------ |
| keyup.按键          | 表示按下键盘的按键后触发                   |
| `click`             | 在元素上按下并释放任意鼠标按键。           |
| `contextmenu`       | 右键点击（在右键菜单显示前触发）。         |
| `dblclick`          | 在元素上双击鼠标按钮。                     |
| `mousedown`         | 在元素上按下任意鼠标按钮。                 |
| `mouseenter`        | 指针移到有事件监听的元素内。               |
| `mouseleave`        | 指针移出元素范围外（不冒泡）。             |
| `mousemove`         | 指针在元素内移动时持续触发。               |
| `mouseover`         | 指针移到有事件监听的元素或者它的子元素内。 |
| `mouseout`          | 指针移出元素，或者移到它的子元素上。       |
| `mouseup`           | 在元素上释放任意鼠标按键。                 |
| `pointerlockchange` | 鼠标被锁定或者解除锁定发生时。             |
| `pointerlockerror`  | 可能因为一些技术的原因鼠标锁定被禁止时。   |
| `select`            | 有文本被选中。                             |
| `wheel`             | 滚轮向任意方向滚动。                       |

```html
<div id="app">
     <input v-on:click="sanHi" type="button" value="你是煞笔吗？">
     <!--简化版-->
     <input @click="sanHi" type="button" value="你是煞笔吗？">
</div>
<script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.min.js"></script>
<script>
     var vm = new Vue({
          el: "#app",
          data: {
               message: "我是煞笔！"
          },
          methods: {
               sanHi: function() {
                    alert(this.message);
               }
          }
     })
</script>
```

- 事件可以带参数

```html
<div id="app">
     <input type="text" name="" id="" @keyup.enter="action('老铁',666)" v-model:value="message">
</div>
<script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.min.js"></script>
<script>
     var vm = new Vue({
          el: "#app",
          data: {
               message: "我是煞笔",
          },
          methods: {
               action: function(a, b) {
                    alert(this.message + a + b);
               }
          }
     })
</script>
```

### v-model:双向绑定数据

```html
<div id="nnf">
     你是煞笔吗：<input type="text" name="" id="" v-model="message"> {{message}}
</div>
<script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.min.js"></script>
<script>
     var vm = new Vue({
          el: "#nnf",
          data: {
               message: "是呀"
          }
     })
</script>
```

```html
<div id="nnf">
     你是男的女的：
     <input type="radio" name="" id="" value="煞笔：选错了，你选男干嘛" v-model="message">男
     <input type="radio" name="" id="" value="煞笔：选错了，你选女干嘛" v-model="message">女<br> {{message}}
</div>
<script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.min.js"></script>
<script>
     var vm = new Vue({
          el: "#nnf",
          data: {
               message: ""
          }
     })
</script>
```

```html
<div id="nnf">
     <select name="" id="" v-model=selected>
          <option value="">--请选择--</option>
          <option>A</option>
          <option>B</optBion>
     <option>C</option>
     </select> {{selected}}
</div>
<script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.min.js"></script>
<script>
     var vm = new Vue({
          el: "#nnf",
          data: {
               selected: ""
          }
     })
</script>
```

### v-show：控制组件的显示和消失

```html
<div id="app">
     <input type="button" value="煞笔的显示和消失" v-on:click="btnEvent">
     <div v-show="isShow" style="width: 100px;height: 100px;background-color: rgb(102, 27, 27);"></div>
</div>
<script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.min.js"></script>
<script>
     var app = new Vue({
          el: "#app",
          data: {
               isShow: true
          },
          methods: {
               btnEvent: function() {
                    this.isShow = !this.isShow
               }
          }
     })
</script>
```

### v-clock：解决加载页面{{}}布局闪烁问题

```html
<div v-clock></div>
```

```css
[v-clock]{display:none;}
```

### 小项目---教室管理网站

- JSON.parse(JSON.stringify(data))：因为push一个对象到一个数组中传递的是地址，改变这个对象，之前传递的对象也会改变，所以用JSON.parse(JSON.stringify(data))把对象转换为字符串就可以

```html
<div id="nnf">
     <h1 id="title">教室管理网站</h1>
     <div id="head">
          <div>教室名称：<input type="text" v-model="inputValue.name" name="" id="call" class="kuang"> </div>
          <div>机构：<input type="text" v-model="inputValue.mechanism" name="" id="" class="kuang"> </div>
          <div>地址：<input type="text" v-model="inputValue.address" name="" id="" class="kuang"> </div>
          <div>教学楼：<input type="text" v-model="inputValue.place" name="" id="" class="kuang"> </div>
          <div>座位：<input type="text" v-model="inputValue.num" name="" id="" class="kuang"></div>
          <div><input type="button" value="增加" @click="add" id="btn"></div>
     </div>
     <hr>
     <div id="list">
          <div id="attribute">
               <div class="attr">教室名称</div>
               <div class="attr">所在机构</div>
               <div class="attr">详细地址</div>
               <div class="attr">上课地点</div>
               <div class="attr">座位数量</div>
               <div class="attr">操作</div>
          </div>
          <div v-for="(li,index) in list" class="data">
               <div class="attr">{{li.name}}</div>
               <div class="attr">{{li.mechanism}}</div>
               <div class="attr">{{li.address}}</div>
               <div class="attr">{{li.place}}</div>
               <div class="attr">{{li.num}}</div>
               <div class="attr"><input type="button" @click="remove(index)" value="删除"></div>
          </div>
     </div>
</div>
<script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.min.js"></script>
<script>
     var vm = new Vue({
          el: "#nnf",
          data: {
               list: [{
                    name: "lxy",
                    mechanism: "牛腩粉公司",
                    address: "深圳",
                    place: "未知",
                    num: "10",
               }, {
                    name: "zwh",
                    mechanism: "牛腩粉公司",
                    address: "东莞",
                    place: "富人区",
                    num: "0",
               }, {
                    name: "czm",
                    mechanism: "牛腩粉公司",
                    address: "惠州",
                    place: "未知",
                    num: "99",
               }, {
                    name: "lyq",
                    mechanism: "牛腩粉公司",
                    address: "化州",
                    place: "橘洲一号",
                    num: "9",
               }],
               inputValue: {
                    name: "wyf",
                    mechanism: "牛腩粉公司",
                    address: "化州",
                    place: "橘洲一号",
                    num: "1000",
               },
          },
          methods: {
               add: function() {
                    if (this.inputValue.name == "") {
                         var call = document.getElementById("call");
                         call.style.boxShadow = "0 0 0 3px #e79d9d";
                    } else {
                         //因为push一个对象到一个数组中传递的是地址，改变这个对象，之前传递的对象也会改变，所以用JSON.parse(JSON.stringify(data))把对象转换为字符串就可以
                         this.list.push(JSON.parse(JSON.stringify(this.inputValue)));
                         this.inputValue.name = "";
                         this.inputValue.mechanism = "";
                         this.inputValue.address = "";
                         this.inputValue.place = "";
                         this.inputValue.num = "";
                    }
               },
               remove: function(index) {
                    this.list.splice(index, 1);
               }
          }
     });
     var shadowObjs = document.getElementsByClassName("kuang");
     for (let i = 0; i < shadowObjs.length; i++) {
          shadowObjs[i].onfocus = function() {
               this.style.boxShadow = "0 0 0 3px #B3D1F3";
          }
          shadowObjs[i].onblur = function() {
               this.style.boxShadow = "";
          }
     }
</script>
```

```css
#title {
    display: flex;
    align-items: center;
    justify-content: space-around;
    margin: 50px 0px;
}

#head {
    padding: 0px 40px;
    display: flex;
    justify-content: space-between;
    margin-bottom: 15px;
}

#head>div {
    padding-left: 20px;
    display: flex;
    align-items: center;
    justify-content: space-around;
    width: 16.6%;
}

#call {
    /* box-shadow: 0 0 0 3px #e79d9d; */
}

.kuang {
    font-size: 1.2rem;
    width: 60%;
    height: 30px;
    padding: 0px 7px;
    border-radius: 5px;
    -webkit-border-radius: 5px;
    -moz-border-radius: 5px;
    -ms-border-radius: 5px;
    -o-border-radius: 5px;
    background-color: #FAFBFC;
    box-sizing: border-box;
    outline: none;
    border: 1px solid #E1E4E8;
    transition: 0.4s;
    -webkit-transition: 0.4s;
    -moz-transition: 0.4s;
    -ms-transition: 0.4s;
    -o-transition: 0.4s;
}

#btn {
    width: 55%;
    height: 30px;
    font-size: 16px;
    /* height: 110%; */
    background-color: #94D3A2;
    border: 0px;
    color: #fff;
    border-radius: 5px;
    -webkit-border-radius: 5px;
    -moz-border-radius: 5px;
    -ms-border-radius: 5px;
    -o-border-radius: 5px;
}

#btn:active {
    background-color: #76b884;
}

#attribute {
    font-size: 20px;
    height: 150%;
    /* background-color: #f0f0f0; */
    margin-top: 15px;
    display: flex;
    align-items: center;
    justify-content: space-around;
}

.data {
    margin-top: 15px;
    display: flex;
    align-items: center;
    justify-content: space-around;
}

.attr {
    width: 150px;
    text-align: center;
}
```



## 网络应用

### 导入网络请求库（版本号：axios v0.21.4）

```html
<script src="https://unpkg.com/axios/dist/axios.min.js"></script>
```

### 两种请求方法

#### 1，get方法

```js
axios.get("地址?key=value&key2=values").then(function(response){},function(err){})
```

#### 2，post方法

```js
axios.post("地址",{key:value,key2:values2}).then(function(response){},function(err){})
```

### 接口地址

| 地址信息                                                     |
| ------------------------------------------------------------ |
| 随机获取笑话的接口<br/>https://autumnfish.cn/api/joke/list<br/>请求方法：get<br/>请求参数：num<br/>参数名：num，参数说明：笑话条数，备注：数字<br/>响应内容：随机笑话 |
| 用户注册接口<br/>https://autumnfish.cn/api/user/reg<br/>请求方法：post<br/>请求参数：username<br/>参数名：username，参数说明：用户名，备注：不能为空<br/>响应内容：注册成功或失败 |
| 天气接口<br/>https://wthrcdn.etouch.cn/weather_mini<br/>请求方法：get<br/>请求参数：city（查询的城市名）<br/>响应内容：天气信息 |
| 音乐接口<br/>https://autumnfish.cn/search<br/>请求方法：get<br/>请求参数：keywords（查询的关键字）<br/>响应内容：歌曲搜索结果 |
| 歌曲详细信息接口<br/>https://autumnfish.cn/song/detail<br/>请求方法：get<br/>请求参数：ids（查询的id）<br/>响应内容：歌曲的详细信息 |
| 歌曲url获取接口<br/>https://autumnfish.cn/song/url<br/>请求方法：get<br/>请求参数：id（查询的id）<br/>响应内容：歌曲的url地址 |
| 歌曲评论获取接口<br/>https://autumnfish.cn/comment/hot?type=0<br/>请求方法：get<br/>请求参数：id（歌曲的id，type固定为0）<br/>响应内容：歌曲的热门评论 |
| 歌曲mv获取接口<br/>https://autumnfish.cn/mv/url<br/>请求方法：get<br/>请求参数：id（mv的id，为0说明没有mv）<br/>响应内容：mv的地址 |

### 第一次尝试网络请求过程

```html
<input type="button" id="get" value="get方法">
<input type="button" id="post" value="post方法">
<script src="https://unpkg.com/axios/dist/axios.min.js"></script>
<script>
     // 随机获取笑话的接口
     // https://autumnfish.cn/api/joke/list
     // 请求方法：get
     // 请求参数：num
     // 参数名：num，参数说明：笑话条数，类型：数字
     // 响应内容：随机笑话
     //axios.get("地址?key=value&key2=values"),then(function(response){},function(err){})
     document.querySelector("#get").onclick = function() {
          axios.get("https://autumnfish.cn/api/joke/list?num=6")
               .then(function(response) {
               console.log(response);
          }),
               function(err) {
               console.log(err);
          }
     }

     // 用户注册接口
     // https://autumnfish.cn/api/user/reg
     // 请求方法：post
     // 请求参数：username
     // 参数名：username，参数说明：用户名，类型：不能为空
     // 响应内容：注册成功或失败
     //axios.post("地址",{key:value,key2:values2}).then(function(response){},function(err){})
     document.querySelector("#post").onclick = function() {
          axios.post("https://autumnfish.cn/api/user/reg", {
               username: "wyf"
          }).then(function(response) {
               console.log(response);
          }, function(err) {
               console.log(response);
          })
     }
</script>
```

### “网络请求 + vue” 结合

```html
<div id="nnf">
     <input type="button" id="joke" value="我想看笑话" @click="getJoke">
     <p>{{joke}}</p>
</div>
<script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.min.js"></script>
<script src="https://unpkg.com/axios/dist/axios.min.js"></script>
<script>
     var vm = new Vue({
          el: "#nnf",
          data: {
               joke: "笑死我了",
          },
          methods: {
               getJoke: function() {
                    //请求后的this.无法获取data中的数据，所以提前把this赋值到that身上，方便调用
                    var that = this;
                    axios.get("https://autumnfish.cn/api/joke").then(
                         function(response) {
                              //调用被提前赋值的that
                              that.joke = response.data;
                         },
                         function(err) {}
                    )
               }
          }
     })
</script>
```

### computed：计算机属性

- 和methods类似，但是其中的方法不能和methods重名
- 能够计算结果缓存起来，就是缓存第一个结果！！！

- 如果在方法中的值发生了变化，则缓存会刷新，可以用控制台使用vm.message = "nnf"，改变数据中的值，再次观察结果。

### 定义一个自己的组件（类似于<div></div>）

```html
<div id="nnf">
     <nnf v-for="item in items" v-bind:message="item"></nnf>
</div>
<script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.min.js"></script>
<script>
     //定义一个自己Vue组件：<nnf></nnf>
     Vue.component("nnf", {
          //接收的数据
          props: ['message'],
          // 模板
          template: '<h1>{{message}}</h1>'
     })

     var vm = new Vue({
          el: "#nnf",
          data: {
               items: ["小屁孩", "煞笔", "牛腩粉"]
          }
     }) 
</script>
```

- 第二种写法（全局组件）

```html
<div id="app">
     <my-cpn></my-cpn>
</div>
<script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.min.js"></script>
<script>
     //创建组件构造器对象
     const cpn = Vue.extend({
          template: `
<div>
<h2>夜夜夜夜</h2>
<div>哈哈哈哈哈哈哈哈哈哈哈哈哈</div>
</div>`
     })
//注册组件（全局组件，意味着可以在多个Vue的示例下面使用）
Vue.component('my-cpn', cpn);

let app = new Vue({
     el: '#app'
})
</script>
```

- 第三种写法（局部组件）

```html
<div id="app">
     <mycpn></mycpn>
</div>
<script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.min.js"></script>
<script>
     //创建组件构造器对象
     const cpn = Vue.extend({
          template: `
<div>
<h2>夜夜夜夜</h2>
<div>哈哈哈哈哈哈哈哈哈哈哈哈哈</div>
     </div>`
     })

     let app = new Vue({
          el: '#app',
          //局部注册组件
          components: {
               mycpn: cpn,
          }
     })
</script>
```

### 套娃，父组件和子组件

```html
<div id="app">
     <mycpn2></mycpn2>
</div>
<script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.min.js"></script>
<script>
     //第二个组件构造器（子组件）
     const cpn1 = Vue.extend({
          template: `
<div>
<h2>啦啦啦啦啦啦啦啦啦</h2>
     </div>
`
     })
     //第二个组件构造器（父组件）
     const cpn2 = Vue.extend({
          template: `
<div>
<h2>哇啊哇哇哇哇哇哇哇</h2>
<mycpn1></mycpn1>
     </div>
`,
          components: {
               //给子组件注册
               mycpn1: cpn1
          }
     })
     //实例化vue
     let app = new Vue({
          el: '#app',
          components: {
               mycpn2: cpn2
          }
     })
</script>
```

### 创建组件注册的语法糖（简介，省略extend）

- 构造全局组件

```html
<div id="app">
     <mycpn1></mycpn1>
</div>
<script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.min.js"></script>
<script>
     //省略Vue.extend()，内部默认自动extend
     Vue.component('mycpn1', {
          template: `
<div>
<h2>啦啦啦啦啦啦啦啦啦</h2>
     </div>
`
     })
     let app = new Vue({
          el: '#app',
          components: {}
     })
</script>
```

- 构造局部组件

```html
<div id="app">
     <mycpn1></mycpn1>
</div>
<script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.min.js"></script>
<script>
     let app = new Vue({
          el: '#app',
          components: {
               mycpn1: {
                    template: `
<div>
<h2>啦啦啦啦啦啦啦啦啦</h2>
     </div>
`
               }
          }
     })
</script>
```

### 组件模板抽离，写到上面，方便写代码

- 第一种写法（script type="text/x-template"）[不常用]

```html
<div id="app">
     <mycpn1></mycpn1>
</div>
<!-- script的类型必须是text/x-template -->
<script type="text/x-template" id="cpn1">
        <div>
            <h2>别别别贝贝</h2>
     </div>
</script>
<script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.min.js"></script>
<script>
     Vue.component('mycpn1', {
          //通过id获取
          template: '#cpn1'
     })
     let app = new Vue({
          el: '#app',
          components: {}
     })
</script>
```

- 第二种写法（template）

```html
<div id="app">
    <mycpn1></mycpn1>
</div>
<!-- template标签 -->
<template id="cpn1">
    <div>
        <h2>别别别贝贝</h2>
    </div>
</template>
<script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.min.js"></script>
<script>
    Vue.component('mycpn1', {
        template: '#cpn1'
    })
    let app = new Vue({
        el: '#app',
        components: {}
    })
</script>
```

### 组件内的数据data，必须是一个函数

- data必须是函数的好处，如果有多个组件，这多个组件调用的地址不一样，所以数据不会有连锁反应，同时变化

```html
<div id="app">
    <mycpn1></mycpn1>
</div>
<template id="cpn1">
    <div>
        <h2>{{message}}</h2>
    </div>
</template>
<script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.min.js"></script>
<script>
    Vue.component('mycpn1', {
        template: '#cpn1',
        //组件内的数据必须是个方法，返回data数据
        data() {
            return {
                message: '组件内数据',
            }
        },
    })
    let app = new Vue({
        el: '#app',
        components: {}
    })
</script>
```

### 父传子 --- 父组件给子组件传递数据

- props

```html
<div id="dv">
     <!-- 绑定props属性和父组件的数据，一定要用v-bind绑定属性，如果没有就会直接传递属性种定义的内容 -->
     <nnf :mes='message' :age='myage'></nnf>
</div>
<template id="nnf">
     <!-- 在自定义子组件内调用数据 -->
     <div>
          <h2>{{mes}}</h2>
          <h3>{{age}}</h3>
     </div>
</template>
<script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.min.js"></script>
<script>
     var vm = new Vue({
          el: "#dv",
data: {
    message: "傻仔",
    myage: "21"
},
components: {
    //子组件
    nnf: {
        //绑定template
        template: '#nnf',
        //props获取父级数据
         
        //第一种写法
        props: ['mes', 'age'],
         
        //第二种写法
        // props: {
        //     mes: String,
        //     age: Number
        // }
         
        //第三种写法
        // props:{
        //     mes:{
        //         type:String,
        //         default:'默认的值'
        //     }
        // }
    }
}
     })
</script>
```

### props驼峰标识，命名中间有大写

```html
<div id="dv">
     <!-- 组件中的属性不能用驼峰命名法，可以用‘-’表示 -->
     <nnf :c-mes='message' :c-age='myage'></nnf>
</div>
<template id="nnf">
     <div>
          <h2>{{cMes}}</h2>
          <h3>{{cAge}}</h3>
     </div>
</template>
<script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.min.js"></script>
<script>
     var vm = new Vue({
          el: "#dv",
          data: {
               message: "傻仔",
               myage: "21"
          },
          components: {
               //子组件
               nnf: {
                    template: '#nnf',
                    props: ['cMes', 'cAge'],
               }
          }
     })
</script>
```

### 子传父 --- 子组件给父组件

- $emit('自定义事件',item)

```html
<!-- 父组件模板 -->
<div id="dv">
     <!--第三步：在父组件模板中的子组件添加子组件发射的自定义事件-->
     <nnf @itemclick='nnfclick'></nnf>
</div>
<!-- 子组件模板 -->
<template id="nnf">
     <div>
          <!--第一步：从这里的点击事件开始-->
          <button v-for='item in categcries' @click='btnclick(item)'>{{item.name}}</button>
     </div>
</template>
<script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.min.js"></script>
<script>
     //根组件
     var vm = new Vue({
          el: "#dv",
          data: {},
          components: {
               //子组件
               nnf: {
                    template: '#nnf',
                    data() {
                         return {
                              categcries: [{
                                   id: '11',
                                   name: 'czm'
                              }, {
                                   id: '22',
                                   name: 'lxy'
                              }, {
                                   id: '33',
                                   name: 'zwh'
                              }, {
                                   id: '44',
                                   name: 'wyf'
                              }]
                         }
                    },
                    methods: {
                         btnclick(item) {
                              //第二步：子组件发射一个自定义事件，包含第二个item数据
                              this.$emit('itemclick', item);
                         }
                    },
               }
          },
          methods: {
               //第四步：事件接收，要包含参数一起传递过来
               nnfclick(item) {
                    console.log(item.id);
               }
          }

     })
```

### watch属性 --- 监控一个值的变换

```html
<div id="dv">
    <input type="text" name="" id="" v-model="mes1">
    <input type="text" name="" id="" v-model="mes2">
</div>
<script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.min.js"></script>
<script>
    //根组件
    var vm = new Vue({
        el: "#dv",
        data: {
            mes1: '1',
            mes2: '2'
        },
         //监控一个值的变换，并获得当前值和改之前的值
        watch: {
            mes1(val, oldVal) {
                console.log(val + " " + oldVal);
            },
            mes2(val, oldVal) {
                console.log(val + " " + oldVal);
            }
        }
    })
</script>
```

### “父” 访问 “子” --- $children 和 $refs

- $children ---（很少用，因为用index找子组件，如果在中间加了其他的子组件，循序就乱了）

```html
<div id="dv">
    <chi></chi><!-- 被访问的子组件 -->
    <chi></chi>
    <chi></chi>
    <button @click='tachchi'>调用孩子萌</button>
</div>
<template id="chi">
    <div>
        <span>你牛逼</span>
    </div>
</template>
<script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.min.js"></script>
<script>
    let app = new Vue({
        el: '#dv',
        data: {},
        methods: {
            tachchi() {
                //调用其中一个子组件的话就用index获取
                console.log(this.$children[0]);
            }
        },
         //子组件
        components: {
            chi: {
                template: '#chi'
            }
        }
    });
</script>
```

- $refs ---（90%都会用这个）

```html
<div id="dv">
    <chi></chi>
    <chi></chi>
    <chi ref="niniubi"></chi>
    <button @click='tachchi'>调用孩子萌</button>
</div>
<template id="chi">
    <div>
        <span>你牛逼</span>
    </div>
</template>
<script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.min.js"></script>
<script>
    let app = new Vue({
        el: '#dv',
        data: {},
        methods: {
            tachchi() {
                //ref没给子组件取名的时候默认是一个空对象
                console.log(this.$refs.niniubi);
            }
        },
        components: {
            chi: {
                template: '#chi'
            }
        }
    });
</script>
```

### “子” 访问 “父” --- $parent 和 $root

- $parent --- （巨少用，比$children还少用）

- $root --- （99%都会用这个）

### slot插槽

- slot基本用法

```html
<div id="dv">
    <chi></chi>
    <!-- 如果在子组件中加了内容，就会把默认值代替 -->
    <chi><span>不是吧</span></chi>
    <chi></chi>
    <button>调用孩子萌</button>
</div>
<template id="chi">
    <div>
        <span>你牛逼</span>
        <!-- 可以在插槽中添加默认值 -->
        <slot><span>我🐂</span></slot>
    </div>
</template>
<script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.min.js"></script>
<script>
    let app = new Vue({
        el: '#dv',
        data: {},
        components: {
            chi: {
                template: '#chi'
            }
        }
    });
</script>
```

- 给插槽取名可以改相对应的插槽内容

```html
<div id="dv">
    <chi></chi>
    <!-- 子组件中添加的内容通过slot的名字来代替相对应的插槽slot -->
    <chi><button slot="center">我代替中间啦</button></chi>
</div>
<template id="chi">
    <div>
        <!-- 给slot取名 -->
        <slot name='left'>左边</slot>
        <slot name='center'>中间</slot>
        <slot name='right'>右边</slot>
    </div>
</template>
<script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.min.js"></script>
<script>
    let app = new Vue({
        el: '#dv',
        data: {},
        components: {
            chi: {
                template: '#chi'
            }
        }
    });
</script>
```

### 插槽的作用域使用

- 

```html
<div id="dv">
    <chi>
        <!-- vue2.5版本之前规定要加template标签 -->
        <!-- 通过slot-scope获取从子组件中data传来的数据 -->
        <template slot-scope='slot'>
            <span>{{slot.data.join(' - ')}}</span>
        </template>
    </chi>
</div>
<template id="chi">
    <div>
        <!-- 给父组件传递子组件的data数据，data名字随便起 -->
        <slot :data='languages'>
            <ul>
                <li v-for='item in languages'>{{item}}</li>
            </ul>
        </slot>
    </div>
</template>
<script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.min.js"></script>
<script>
    let app = new Vue({
        el: '#dv',
        data: {},
        components: {
            chi: {
                data() {
                    return {
                        languages: ['JavascriptCH', 'Java', 'ca', 'Python', '6d', 'Swift ']
                    }
                },
                template: '#chi',
            }
        }
    });
</script>
```

## 前端模块化

- CommonJS、AMD、CMD，也有ES6的Modules

### CommonJS

- CommonJS的导出

```js
//main.js中的内容
module.exports = {
     flag: true,test(a, b){
          return a + b
     },
     demo(a, b){
          return a * b
     }
}
```

- CommonJS的导入

```js
//conmon5模块
let { test, demo,flag } = require('./main.js');

//等同于
let _mA = require( "./main.js");
let test = _mA.test;
let demo = _mA.demo;
let flag = _mA.flag;
```

### ES6的modules

- 首先要在html文件中导入js时加入type='module'

```html
<script src='aaa.js' type='module'></script>
```

- ES6的导出

```js
//导出写法一
export{
	mem1, mem2
}

//导出写法二
export var mem3 = 1000;
export var mem4 = 2.88;

//导出写法三：直接导出函数
export function sum(num1,num1){
     return num1 * num2;
}

//导出写法四：直接导出类
export class Person{
     run(){
		console.log('你牛逼');
     }
}
```

- ES6的导入

```js
//正常导入
import {mem1, mem2} from "./aaa.js"

//把所有数据导入
import * as aaa from './aaa.js'
//一次性引用所有数据
console.log(aaa.mem1);
```

### ES6中可以让导入者自己命名 --- export default

- 自己命名的导出

```js
var mem = '你牛逼';
export default mem;
```

- 自己命名的导入

```js
import myName from './aaa.js';
console.log('myName')
```

## webpack --- 开发时候用的工具，用来打包

### webpack的基本使用过程

- 我们创建如下文件和文件夹:
  - ![image-20211113164420112](C:\Users\nnf\Desktop\超叼的\img\image-20211113164420112.png)

- 文件和文件夹解析∶
  - dist文件夹:用于存放之后打包的文件
  - src文件夹∶用于存放我们写的源文件
    -  main.js:项目的入口文件。
    - mathUtils.js:定义了一些数学工具函数，可以在其他地方引用，并且使用。具体内容查看下面的详情。
    - index.html:浏览器打开展示的首页html
    - package.json :通过npm init生成的，npm包管理的文件(暂时没有用上，后面才会用上)



### npm初始化

- 输入这个命令行就会生成package.json文件，这个文件会显示的是当前项目下的信息

```bash
npm init
```

### npm安装依赖

```bash
npm install
```

### webpack.config.js文件（出口入口配置）

- 方便打包，每次打包都要在webpack后面写出打包入口和打包出口，这个文件可以解决，下次就只要输入webpack就可以自动打包了

```js
//从全局的path包中导入赋值给path
const path = require('path');

//为了不用每次webpack打包都要输入打包入口和打包出口的路径
module.exports = {
    //打包入口的路径
    entry: './src/main.js',
    // 打包出口的路径
    output: {
        //动态获取dist的绝对路径
        path: path.resolve(__dirname, 'dist'),
        filename: 'bundle.js'
    }
}
```

### package.json文件（版本号信息）

- 自己配置，“npm run build”指令代替“webpack”指令来打包了
- 这样配置当在终端运行“webpack”，也会优先在本地找依赖

```json
{
    "name": "meetwepack",
    "version": "1.0.0",
    "description": "",
    "main": "index.js",
     //这里表示每次npm run后面加的指令
    "scripts": {
        "test": "echo \"Error: no test specified\" && exit 1",
         //例：在这个文件终端执行npm run build后相当于执行webpack
        "build": "webpack"
    },
    "author": "",
    "license": "ISC"
}
```

### 安装本地webpack --- 要在对应目录下安装

- --save-dev是开发时依赖，项目打包后就不需要继续使用了

```bash
npm install webpack@3.6.0 --save-dev
```

- 安装后package.json文件的变化

```json
//package.json文件
{
    "name": "meetwepack",
    "version": "1.0.0",
    "description": "",
    "main": "index.js",
    "scripts": {
        "test": "echo \"Error: no test specified\" && exit 1",
        "build": "webpack"
    },
    "author": "",
    "license": "ISC",
     //开发时依赖，这里是本地安装webpack后生成的，只有在开发时才会用到
    "devDependencies": {
        "webpack": "^3.6.0"
    }
}
```

### webpack3.6.0好像因为版本太低安装不了css-loader和style-loader，重新卸载安装

- 卸载webpack

```bash
npm uninstall webpack -g
```

- 安装最新版本

```bash
//全局安装
npm install webpack -g

//局部安装
//一定要确定已经有 package.json，没有就通过 npm init 创建
npm install webpack --save-dev
```

- 安装webpack-dev-server

```bash
npm install webpack-dev-server --save-dev
```

- 安装脚手架

```bash
npm install webpack-cli -g
```

### 将css文件打包到bundle.js文件中

- 首先在main.js入口文件中添加依赖

![image-20211114005710545](C:\Users\nnf\Desktop\超叼的\img\image-20211114005710545.png)

- 去webpack官网https://www.webpackjs.com/中找到中文文档 -> loaders -> 样式

- 安装css-loader

```bash
npm install --save-dev css-loader
```

- 安装style-loader

```bash
npm install style-loader --save-dev
```

- 在webpack.config.js中配置

```js
module: {
    rules: [{
        test: /\.css$/,
        //css-loader只负责将css文件进行加较
        //style-loader负责将样式添加到DoM中
        //使用多个loader时，是从右向左
        use: ['style-loader', 'css-loader']
    }]
},
```

![image-20211114012213409](C:\Users\nnf\Desktop\超叼的\img\image-20211114012213409.png)

- 再打包npm run build就可以实现css了

### 将图片打包到bundle.js中

- 如果直接将url放进css中后打包，就会直接在dist目录下通过hash生成一个图片文件

![image-20211114140923207](C:\Users\nnf\Desktop\超叼的\img\image-20211114140923207.png)

- 但是这样不利于管理文件，所以

- 安装url-loader

```bash
npm install --save-dev url-loader
```

- 并配置webpack.config.js

```js
module.exports = {
  module: {
    rules: [
      {
        test: /\.(png|jpg|gif|jpeg)$/,
        use: [
          {
            loader: 'url-loader',
            options: {
              //当加载的图片，小于limit时，会将图片编译成base64字符串形式．
              //当加载的图片，大于limit时，需要使用file-loader模块进行加载.
              limit: 8192
            }
          }
        ]
      }
    ]
  }
}
```

- 但是我发现打包后图片显示不出来，查资料后发现是webpack5后的版本url-loader、file-loader已经弃用，如果想要继续使用则需要
  - ①在use后添加type: '[javascript](https://so.csdn.net/so/search?from=pc_blog_highlight&q=javascript)/auto'
  - ②url-loader默认采用ES模块语法，即import ‘…/aaa.png’；如果在引入css文件时是comandjs语法就会报错，所以需要将esModule设置为false

- 所以最终配置的webpack.config.js文件应该是

```js
module: {
     rules: [{
          test: /\.(png|jpg|gif|jpeg)$/,
          use: [{
               loader: 'url-loader',
               options: {
                    limit: 10000,
                    //comandjs语法就会报错，所以需要将esModule设置为false
                    esModule: false
               }
          }],
          //webpack5后规定加
          type: 'javascript/auto'
     }]
}
```

- 当加载的图片内存大于limit时，会报错Cannot find module 'file-loader'，所以要

- 安装file-loader

```bash
npm install --save-dev file-loader
```

- 并配置webpack.config.js

```js
module.exports = {
  module: {
    rules: [
      {
        test: /\.(png|jpg|gif)$/,
        use: [
          {
            loader: 'file-loader',
            options: {}
          }
        ]
      }
    ]
  }
}
```

- 但是我发现不安装file-loader也可以打包内存大于limit的图片，所以还是不安装了吧。。

- 当加载的图片内存大于limit时，npm run build打包会生成打包后的图片文件
- 这时你想打包你的图片到指定位置时就可以去webpack.confid.js文件中配置

```js
output: {
     path: path.resolve(__dirname, 'dist'),
     filename: 'bundle.js',
     //每次打包url文件都会自动在前面加这里的前缀
     publicPath: 'dist/'
}
```

- 给打包后的图片自定义名字
- 要在webpack.confid.js文件中配置

```js
module: {
     rules: [{
          test: /\.(png|jpg|gif|jpeg)$/,
          use: [{
               loader: 'url-loader',
               options: {
                    limit: 10000,
                    //name：表示原来文件名
                    //hash:8：表示hash值为8位
                    //extL：表示文件名
                    name: 'img/[name].[hash:8].[ext]',
                    esModule: false
               }
          }],
          type: 'javascript/auto'
     }]
},
```

### ES6语法处理

- 因为有些了浏览器还无法适应ES6，所以为了把ES6语法转化位ES5语法（例如在bundle.js中const没有了）
- 安装babel-loader

```bash
npm install -D babel-loader @babel/core @babel/preset-env webpack
```

- 要在webpack.confid.js文件中配置

```js
module: {
  rules: [
    {
      test: /\.js$/,
      //exclude：排除的意思
      exclude: /(node_modules|bower_components)/,
      use: {
        loader: 'babel-loader',
        options: {
          presets: ['@babel/preset-env']
        }
      }
    }
  ]
}
```

