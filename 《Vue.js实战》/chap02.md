[toc]

# 数据绑定和第一个Vue应用

- 一个应用的代码示例

  ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>Title</title>
  </head>
  <body>
  
  <div id="app">
      <input type="text" v-model="name" placeholder="your name">
      <h1>hello, {{name}}</h1>
  </div>
  
  <script src="https://unpkg.com/vue@2.1.6/dist/vue.min.js"></script>
  <script>
      var app = new Vue({
          el: '#app',
          data:{
              name:''
          }
      })
  </script>
  
  </body>
  </html>
  ```

  ![image-20210323163526095](https://raw.githubusercontent.com/KingdeGuo/myPictureBed/main/img_upload202103/23/163527-870081.png)

- 这段代码实现了数据的双向绑定。在输入框中输入的内容会**实时**显示出来。



## 2.1 Vue示例与数据绑定

- 一个典型的创建如下所示

  ```js
  var app = new Vue(){
  	// something
  }
  ```

- 这个`app`就是Vue的实例

- `something`中，必不可少的就是`el`，`el`用于指定一个页面中已存在的DOM元素来挂载Vue实例，可以是`HTMLElement`，或者`CSS选择器`。

- 挂载成功之后，可以通过`app.$el`来访问这个元素。

- 上述代码中`v-model`指令，它的值对应于我们创建的`Vue`实例的`data`选项中的`name`字段，这就是`Vue`的数据绑定。

- 建议所有数据都预先在data内部声明，这样不至于将数据散落在业务逻辑中。

- Vue实例本身也代理了data对象里的所有属性

  ```js
  var app = new Vue({
  	el:'#app',
  	data:{
  		a:2
  	}
  })
  console.log(app.a);
  ```

## Vue的生命周期钩子

- `created`

  - 实例创建完成之后调用
  - 完成了数据观测，但是尚未挂载，`$el`不可用

- `mounted`

  - `el`挂载到实例上后调用

- `beforeDestory`

  - 实例销毁之前调用，主要解绑一些使用`addEventListener`监听的事件。

- 像`el`, `data`一样可以作为选项写入Vue实例内

  ```js
  var app = new Vue({
      el:'app',
      data:{
          a:2
      },
      created:function(){
          console.log(2);
      },
      mounted:function(){
          console.log(this.$el);
      }
  })
  ```

## 插值与表达式

- 使用`{{}}`插值

- 如果有时候就是想输出HTML，而不是将数据解析后的纯文本，可以使用`v-html`

  ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>Title</title>
  </head>
  <body>
  
  <div id="app">
      <span v-html="link"></span>
  </div>
  
  <script src="https://unpkg.com/vue@2.1.6/dist/vue.min.js"></script>
  <script>
      var app = new Vue({
          el: '#app',
          data:{
              link:"<a href='#'>这是一个超链接</a>"
          }
      })
  </script>
  
  </body>
  </html>
  ```

- 但是要注意，如果将用户产生的内容使用`v-html`输出后，可能产生XSS攻击，所以要在服务器端对用户提交的内容进行处理。一般将尖括号`< >`转义

- 如果要显示`{{}}`标签，那么使用`v-pre`即可跳过这个元素和它的子元素的编译过程。

  ```html
  <span v-pre></span>
  ```

- 在`{{}}`中，还可以使用JS表达式进行简单的计算

  ```html
  <div id="app">
      {{number / 10}}
      {{isOK ? "YES" : "NO"}}
      {{text.split(',').reverse().join(',')}}
      {{}}
  </div>
  
  <script>
  	var app = new Vue({
          el:'#app',
          data:{
              number:100,
              isOK:false,
              text:'123,456'
          }
      })
  </script>
  ```

- 注意，只支持单个表达式，不支持语句和流控制。在表达式中不能使用用户自定义的全局变量。

## 过滤器的使用

- 在`{{}}`中使用管道`|`可以对数据进行过滤

- 一个实例

  ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>Title</title>
  </head>
  <body>
  
  <div id="app">
      {{date | formatDate}}
  </div>
  <script src="https://unpkg.com/vue@2.1.6/dist/vue.min.js"></script>
  <script>
      var padDate = function (value) {
          return value < 10 ? '0' + value : value;
      }
      var app = new Vue({
          el:'#app',
          data:{
              date: new Date()
          },
          filters:{
              formatDate: function (value) {
                  var date = new Date(value);
                  var year = date.getFullYear();
                  var month = padDate(date.getMonth());
                  var day = padDate(date.getDate());
                  var hours = padDate(date.getHours());
                  var minutes = padDate(date.getMinutes());
                  var seconds = padDate(date.getSeconds());
                  return year + "-" + month + "-" + day + " " + hours + ":" + minutes + ":" + seconds;
              }
          },
          mounted: function () {
              var _this = this;
              this.timer = setInterval(function () {
                  _this.date = new Date();
              },1000);
          },
          beforeDestory:function () {
              if (this.timer){
                  clearTimeout(this.timer);
              }
          }
      })
  </script>
  </body>
  </html>
  ```

- 过滤器可以串联，也可以接收参数

  ```html
  {{message | filter1 | filter2}}
  {{message | filter3('arg1', 'arg2')}}
  ```

- 上述代码中传入的分别是第二和第三个参数，第一个参数是数据本身。



## 指令与事件

- 数据驱动DOM是Vue.js核心理念，所有不到万不得已不要主动操作DOM，你只需要维护号数据，DOM的事Vue会帮你优雅的处理

- 一些指令介绍
  - `v-bind`：动态更新HTML元素上的属性
  - `v-on`：用来绑定事件监听器，方便用于交互
  
  ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>Title</title>
  </head>
  <body>
  <div id="app">
      <p v-if="show">look here</p>
      <button v-on:click="handleClose">Hide top</button>
  </div>
  
  <script src="https://unpkg.com/vue@2.1.6/dist/vue.min.js"></script>
  <script>
      var app = new Vue({
          el: '#app',
          data:{
              show: true
          },
          methods:{
              handleClose: function () {
                  this.show = false;
              }
          }
      })
  </script>
  </body>
  </html>
  ```
  
- `v-on:click`, `v-on:dbclick`, `v-on:keyup`, `v-on:mouseover`

- 也可以写成

  ```js
  <script>
      var app = new Vue({
          el: '#app',
          data:{
              show: true
          },
          methods:{
              handleClose: function () {
                  this.show = close();
              },
              close:function(){
                  this.show = false;
              }
          }
      });
  </script>
  ```



## 语法糖

- `v-bind`的语法糖是直接省略`v-bind`，直接写`:`

- `v-on`的语法糖是用`@`来替代。

- 代码示例

  ```html
  <a v-bind:hred="url">Link</a>
  <!-- 缩写为 -->
  <a :href="url">Link</a>
  
  <button v-on:click=:"myFun1"> Button </button>
  <!-- 缩写为 -->
  <button @click="myFun1"> Button </button>
  ```

  

