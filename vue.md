

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



### npm初始化 --- Node Package Manager

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
npm install webpack --save-dev
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

### 配置vue

- 配置后就可以实现vue实例化等功能

- 配置vue环境有三种方法
  - 第一种：下载vue的js文件，然后导入
  - 第二种：导入cdn
  - 第三种：通过npm安装vue环境，就是下面这种方法

- 安装vue环境

```bash
#不需要再后面加--dev，因为不只是开发时依赖
npm install vue --save
```

- 安装后试一下使用vue

```html
<!-- index.html -->
<div id="app">
    {{message}}
</div>
```

```js
//main.js
import Vue from 'vue'

new Vue({
    el: '#app',
    data: {
        message: '你牛逼'
    }
})
```

- 运行后发现浏览器console报错

```asciiarmor
You are using the runtime-only build of Vue where the template compiler is not available. Either pre-compile the templates into render functions, or use the compiler-included build.
//在模板编译器不可用的情况下，您使用的是仅运行时版本的Vue。可以将模板预编译为呈现函数，也可以使用编译器附带的构建。
```

- 报错的原因是vue有两个版本
  - 1.runtime-only -> 代码中,不可以有任何的template
  - 2.runtime-compiler -> 代码中,可以有template,因为有compiler可以用于编译template

- 单独安装vue后只是第一个版本runtime-only
- 还需要再webpack.config.js中配置

```js
module.exports = {
     resolve:{
          alias:{
               'vue$':'vue/dist/vue.esm.js'
          }
     }
}
```

- 配置后就相当于安装第二个版本了，运行就没有报错了

### el和template的关系（el和tempalte同时存在的情况）

- 在项目中index.html中body里面只有一个div:app

```html
<div id="app">
</div>
```

- div:app里面内容是从main.js中vue实例template覆盖过来的

![image-20211115141908669](C:\Users\nnf\Desktop\超叼的\img\image-20211115141908669.png)

### Vue文件

- 但是template和data等数据都放在main.js文件中，main.js文件就显得很臃肿，所以就引出了vue文件，把数据都放到vue文件里面

![image-20211116095332392](C:\Users\nnf\AppData\Roaming\Typora\typora-user-images\image-20211116095332392.png)

- 但是想用vue文件需要
- 安装vue-loader和vue-template-compiler

```bash
npm install vue-loader vue-template-compiler --save-dev
```

- 配置webpack.config.js

```js
module: {
  rules: [
    {
      test: /\.vue$/,
      use:['vue-loader']
    }
  ]
}
```

- 但是配置后，npm run build运行还是没成功，查阅资料后发现因为版本太新了，还需要再配置一下webpack.config.js

```js
const VueLoaderPlugin = require('vue-loader/lib/plugin')

module.exports = {
    plugins: [new VueLoaderPlugin()],
}
```

- 然后就可以了

- vue文件中的套娃，一个套一个，无限循环

![image-20211116141803323](C:\Users\nnf\Desktop\超叼的\img\image-20211116141803323.png)

### 省略后缀名

- 直接在resolve->extensions中加入

```js
module.exports = {
    resolve: {
        extensions:['.js','.css','.vue'],
    },
}
```

### Plugin插件

##### 添加版权

- 添加后，打包后的文件头部都会有版权信息

```js
const webpack = require('webpack');

module.exports = {
    plugins: [
        new VueLoaderPlugin(),
        //可以在打包的文件中设定版权
        new webpack.BannerPlugin('最终版权归 why牛腩粉 所有'),
    ],
}
```

##### HtmlWebpackPlugin插件 --- 打包html文件

- 安装HtmlWebpackPlugin插件

```bash
npm install html-webpack-plugin --save-dev
```

- 配置webpack.config.js

```js
//安装后导出HtmlWebpackPlugin插件
const HtmlWebpackPlugin = require('html-webpack-plugin');

module.exports = {
    plugins: [
        new VueLoaderPlugin(),
        new webpack.BannerPlugin('最终版权归 why牛腩粉 所有'),
        //运用这个插件
        new HtmlWebpackPlugin()
    ],
}
```

- 然后npm run build发现打包目录dist中生成index.html文件
- 但是这个文件里有两个错误
  - 第一个：没有div:#app组件
  - 第二个：bundle.js文件路径不对

![image-20211116193442338](C:\Users\nnf\Desktop\超叼的\img\image-20211116193442338.png)

- 解决方法：
- 第一个：在webpack.config.js中配置

```js
plugins: [
    new VueLoaderPlugin(),
    new webpack.BannerPlugin('最终版权归 why牛腩粉 所有'),
     //这里写的会根据没打包之前index.html文件补充到打包后的index.html文件中
    new HtmlWebpackPlugin({
        template: 'index.html'
    })
],
```

- 第二个解决方法：删掉没打包之前index.html文件中引用js文件的script，打包后会自动生成

![image-20211116194722830](C:\Users\nnf\Desktop\超叼的\img\image-20211116194722830.png)

- 按情况应该会自动生成对应引用js文件script的，但是没成功，js文件路径还是没对，先不管了

##### uglifyjs插件 --- 丑化js文件（就是把那些空格和注释删掉，压缩内存）

- 安装uglifyjs

```bash
npm install uglifyjs-webpack-plugin@1.1.1 --save-dev
```

- 配置webpack.config.js

```js
const UglifyJsPlugin = require('uglifyjs-webpack-plugin')

module.exports = {
    plugins: [
        new VueLoaderPlugin(),
        new webpack.BannerPlugin('最终版权归 why牛腩粉 所有'),
        new HtmlWebpackPlugin(),
        new UglifyJsPlugin(),
    ],
}
```

- 但是我发现这个东西被弃用了，所以还是别安装了。。

### 热部署 --- 搭建本地服务器，绑定一个文件夹，每次保存都会热更新，把代码放进内存里，还没放进磁盘里，改代码改好了，再npm run build才会打包代码进磁盘里

- 安装本地服务器

```bash
npm install --save-dev webpack-dev-server
```

- 配置webpack.config.js
- 这里devServe还有几个属性
  - contentBase:为哪一个文件夹提供本地服务，默认是根文件夹，我们这里要填写./dist
  - port :端口号
  - inline :页面实时刷新
  - historyApiFallback:在SPA页面中，依赖HTML5的history模式

```js
//新版本的
module.exports = {
     plugins: {
       new webpack.LoaderOptionsPlugin({
         options: {
           postcss: function () {
             return [precss, autoprefixer];
           },
           devServer: {
             //本地服务器所加载的页面所在的目录
             contentBase: "./public", 
             //实时刷新
             inline: true 
           }
         }
       })
     }
}
```

- 在package.json中配置，下次运行命令行就只要npm run dev

```json
"name": "meetwepack",
    "version": "1.0.0",
    "description": "",
    "main": "index.js",
    "scripts": {
        "test": "echo \"Error: no test specified\" && exit 1",
        "build": "webpack",
         //--open表示自动打开页面
        "dev": "webpack-dev-server --open"
    },
```

- 按道理来说npm run dev就可以了，但是我运行出后是Cannot GET /，单独右键运行就可以，而且改代码也有右上角热更新的标志，但就是没变化，那就先这样先。。



## Vue cli2

### runtime-compiler和runtime-only的区别

- runtime-compiler中注册子组件

```js
//runtime-compiler(v1)
//template -> ast -> render ->vdom ->UI
new Vue({
     el: '#app',
     template:'<App/>',
     components: { App }s
})
```

- runtime-only中注册子组件

```js
//runtime-only(v2)(2比1的性能更多)
//render -> vdom ->UI
new Vue({
     el: '#app',
     render:function(h){
          return h(App)
     }
})

//简写版
new vue({
     el: '#app",
     render: h => h(App)
})
```



## Vue cli3

### 路由器 --- router-link 和 router-view

- 安装vue-router

```bash
npm install vue-router --save
```

- 在src文件夹下建文件夹：router
- 在router文件夹下建js文件：index.js，用来配置路由相关信息

- index.js的内容（这里是旧版vue2的）

```js
//导入插件
import Vue from 'vue'
import VueRouter from 'vue-router'

//1.通过Vue.user(插件)，安装插件
Vue.use(VueRouter)

//2.实例化VueRouter对象
// const router = new VueRouter({
//     routes:[
//     ]
// })
//一般吧routes单独放出来
const routes = [
	
]
const router = new VueRouter({
    //配置路由和组件之间的应用关系
    routes
})

//3.将router对象传入到Vue实例中
export default router
```

- 新版index.js（vue3）

```js
import { createRouter, createWebHistory } from 'vue-router'
//引入
//import Home from '../components/Home.vue'
const routes = [{
    //在这里配置路由配置
     //path:'./home',
     //component: Home
}]
const routerHistory = createWebHistory()
const router = createRouter({
    history: routerHistory,
    routes
})
export default router
```

- 在main.js中接收router

```js
import router from './router'

createApp(App).use(router).mount('#app')
```

- 使用路由
  - router-link：相当于a标签
  - router-view：点击link后渲染组件的位置

```html
<router-link to="/home">home</router-link>
<router-link to="/about">about</router-link>
<router-view></router-view>
```

### 路由默认值

- 每次一打开页面就显示主页，不需要点击再显示

```js
const routes = [{
    path:'/',
    //重定向，也就是将根目录重定向到/home
    redirect:'/home'
}]
```

### router-link的其它属性

- <u>tag</u>：默认渲染a标签，可以通过这个来改成其它的标签

```html
<router-link to="/home" tag="button">home</router-link>
```

- 但是vue3.x版本vue-router4.x中tag已经无效了，需要用v-slot处理

```html
<router-link to="/test" v-slot="{navigate, isActive, isExactActive}">
  <el-button @click="navigate" :class="{active: isActive, exactActive: isExactActive}">测试1</el-button>
</router-link>
```

- <u>replace</u>：replace不会留下history记录，就可以防止用户点击返回按钮返回到上一个页面中

```html
<router-link to="/home" replace>home</router-link>
```

- 被点击的router-link会自动加属性class="router-link-active"
- 然后我们想给点击的router-link添加样式的话，直接在css中.router-link-active{}就行了

```css
.router-link-active{
}
```

- <u>active-class</u>：给活跃的router-link自动添加的class自定义名字

```html
<router-link to="/home" active-class="active">home</router-link>
```

- 如果有很多个router-link一个一个改active-class很麻烦，可以在index.js中加一个属性linkActiveClass，就会全部自动换

```js
const router = createRouter({
    history: routerHistory,
    routes,
     //统一换
    linkActiveClass: 'active'
})
```

### 通过点击事件跳转路径

- html中绑定点击事件

```html
<button @click="homeclick">home</button>
<button @click="aboutclick">about</button>
<router-view></router-view>
```

- js中点击事件

```js
methods: {
  homeclick(){
    //this.$router.push('/home')
    this.$router.replace('/home')//replace没有返回
  },
  aboutclick(){
    //this.$router.push('/about')
    this.$router.replace('/about')//replace没有返回
  }
},
```

### 动态路由器

- index.js配置路由器路径

```js
const routes = [{
    path: '/user/:userId',
    component: User
}]
```

- App.vue配置router-link

```vue
<template>
  <div>
    <!-- 用v-bind绑定data中的数据，并拼接在一起就可以了 -->
    <router-link :to="'/user/' + userId" replace>user</router-link>
    <router-view></router-view>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      //只要动态改变data中的数据，路径值就会对应改变
      userId:'wyfnb'
    }
  },
}
</script>
```

- 如果想在页面中显示路径值

- User.vue中

```vue
<template>
    <div>
        <h1>我是user</h1>
        <h2>我的路径是{{userId}}</h2>
    </div>
</template>

<script>
export default {
    name: '短暂逃离User',
    computed: {
        userId(){
             //$route就是获取到当前处于活跃状态的路由
             //在这里表示获取到处于活跃状态的路由的param(参数)值
            return this.$route.params.userId
        }
    },
};
</script>
```

### 点击事件 => 动态路由

```vue
<template>
    <div>
        <button @click='userClick'></button>
    </div>
</template>
```

```js
methods:{
     userClick(){
          this.$router.push('/user/' + this.userId)
     }
}
```

### 路由懒加载

- 首先,我们知道路由中通常会定义很多不同的页面.
- 这个页面最后被打包在哪里呢?一般情况下，是放在一个js文件中.
- 但是,页面这么多放在一个js文件中,必然会造成这个页面非常的大.如果我们一次性从服务器请求下来这个页面,可能需要花费一定的时间,甚至用户的电脑上还出现了短暂空白的情况.
- 如何避免这种情况呢?使用路由懒加载就可以了,这样就可以每个页面打包时生成一个js文件

```js
const routes = [{
    path: '/',
    //重定向，也就是将根目录重定向到/home
    redirect: '/home'
}, {
    path: '/home',
     //箭头函数导入
    component: () =>
        import ('../components/Home.vue')
}, {
    path: '/about',
    component: () =>
        import ('../components/About.vue')
}, {
    path: '/user/:userId',
    component: () =>
        import ('../components/User.vue')
}]
```

### 路由嵌套使用

- 在index.js中配置

```js
const routes = [{
    path: '/home',
    component: () =>
        import ('../components/Home.vue'),
    //子路由
    children: [{
        //子路由是不用加/的
        path: 'message',
        component: () =>
            import ('../components/Message.vue')
    }, {
        path: 'news',
        component: () =>
            import ('../components/News.vue')
    }]
},]
```

- router-link是在父路由.vue的文件中添加的

```vue
<template>
    <div>
        <h1>我是首页</h1>
        <!-- 路径一定要写父路由 --> 
        <router-link to="/home/message" replace>信息</router-link>
        <router-link to="/home/news" replace>新闻</router-link>
        <router-view></router-view>
    </div>
</template>
```

### 路由传递参数

- 在App.vue中router-link的to属性里面写参数

```html
<router-link :to="{path:'/profile',query:{name:'why',age:21,height:1.88}}" replace>档案</router-link>
```

- 路径就会显示参数
- 协议://主机:端口/路径?查询
- scheme://host : port/ path?query#fragment

```http
http://localhost:8080/profile?name=why&age=21&height=1.88
```

- 如果想在profile.vue中显示参数的数据
- 就要在profile.vue中配置

```vue
<template>
    <div>
        <h1>档案</h1>
         <!-- 用$route引用query方法 -->
        <h2>{{$route.query.name}}</h2>
        <h2>{{$route.query.age}}</h2>
        <h2>{{$route.query.height}}</h2>
    </div>
</template>
```

### 点击事件 => 传递参数

```vue
<template>
    <div>
        <button @click='profileClick'></button>
    </div>
</template>
```

```js
methods:{
     profileClick(){
          this.$router.push({
               path:'/profile',
               query:{
                    name:'why',
                    age:21,
                    height:1.88
               }
          })
     }
}
```

### 全局导航守卫（跳转界面的反应）

- 每次点击切换路由，页面title随着改变

- index.js中添加函数

```js
const routes = [{
    path: '/',
    redirect: '/home'
}, {
    path: '/home',
    component: () =>
        import ('../components/Home.vue'),
     //给每个路由加元数据meta.title属性
    meta: {
        title: '首页'
    },
}, {
    path: '/about',
    component: () =>
        import ('../components/About.vue'),
    meta: {
        title: '关于'
    }
}, {
    path: '/user/:userId',
    component: () =>
        import ('../components/User.vue'),
    meta: {
        title: '用户'
    }
}, {
    path: '/profile',
    component: () =>
        import ('../components/Profile.vue'),
    meta: {
        title: '档案'
    }
}]

//前置守卫(guard)：跳转之前的回调函数
//获取每个路由的title
router.beforeEach((to, from, next) => {
     //加matched[0]是为了每次打开页面显示第一个（首页）
    document.title = to.matched[0].meta.title
     //这个next()一定要加，否则点击路由不会跳转，在没有调用beforeEach这个函数的时候，底层会自动调用next()方法
    next()
})
```

- 补充

```js
//后置狗子(hook)：跳转之后的回调函数
router.afterEach((to,from)=> {
	console.log('----');
})
```

- 路由独享的守卫

```js
const routes = [{
    path: '/home',
    component: () =>
        import ('../components/Home.vue'),
    //跳转到这个路由时触发
    beforeEnter: (to, from, next) => {
        console.log('我跳转到这个路由之前干的');
        next()
    },
    //路由改变时触发
    beforeUpdate() {
        console.log('路由更新了喔');
    },
    //离开这个路由时触发
    beforeRouteLeave(to, from, next) {
        console.log('我离开上一个路由后干的');
        next()
    },
}]
```

### 页面缓存 --- keep-alive

- keep-alive是Vue内置的一个组件，可以使被包含的组件保留状态，或避免重新渲染，可以避免组件频繁的创建和销毁。

- 在实现之前先回顾一下几个生命周期函数

```vue
<script>
export default {
      name: 'App',
      data() {
        return {
          userId:'wyfnb'
        }
      },
  	//组件被创建 => 执行
     created(){

     },
     //组件被销毁 => 执行
     destroyed(){

     },
     //下面这两个必须结合keep-alive使用
     //组件被活跃 => 执行
     activated(){

     },
     //组件不活跃 => 执行
     deactivated(){

     }
}
</script>
```

- 开始
- App.vue中的router-view外要加keep-alive

```vue
<keep-alive>
  <router-view/>
</keep-alive>
```

- Home.vue下有两种状态：新闻news 和 信息message

```vue
<template>
    <div>
        <h1>我是首页</h1>
        <router-link to="/home/message" replace>信息</router-link>
        <router-link to="/home/news" replace>新闻</router-link>
        <router-view></router-view>
    </div>
</template>
```

- 首先要把每次加载的默认路径删了

- 然后要给Home.vue添加方法

```vue
<script>
export default {
    name: '短暂逃离Home',

    data() {
        return {
            path:'/home/news'
        };
    },
    //组件被活跃 => 执行
    activated() {
        //把记录状态放进路径里
        this.$router.push(this.path);
    },
    //守卫：离开组件时执行
    beforeRouteLeave (to, from, next) {
        //记录离开时状态
        this.path = this.$route.path;
        next();
    }
};
</script>
```

### keep-alive的属性

- include：这里的组件都会被缓存
- exclude：这里的组件不会被缓存
- 如果想某个组件不被缓存就可以加excludes属性
- 在App.vue中

```vue
<!-- excludes中的组件就不会被缓存 -->
<keep-alive exclude="Profile,User">
	<router-view/>
</keep-alive>
```

- 上面的Profile,User是组件的name属性

```vue
<script>
export default {
    //name属性
    name: 'Profile',
    data() {
        return {
        };
    },
    mounted() {
    },
    methods: {
    },
};
</script>
```

