[toc]

# 内置指令

## v-cloak

- 不需要表达式

- 在Vue实例结束编译时从绑定的HTML元素上移除，经常和CSS的display:none配合使用

- 代码示例

  ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>Title</title>
      <style>
          [v-cloak]{
              display: none;
          }
      </style>
  </head>
  <body>
  
  <div id="app" v-cloak>
      {{message}}
  </div>
  <script src="https://unpkg.com/vue@2.1.6/dist/vue.min.js"></script>
  <script>
      var app = new Vue({
          el:"#app",
          data:{
              message:"this is a text"
          }
      })
  </script>
  
  </body>
  </html>
  ```

  当网速较慢，还没有加载完毕时，页面上会显示{{message}}字样。这样会有闪动。因此在CSS中加入`[v-cloak]{ display: none; }`来解决这个问题。

- 在一般情况下这是一种解决初始化导致页面闪动的最佳实践，但是在具有工程化的项目里，比如`webpack`和`vue-router`时，项目的HTML结构只有一个空的DIV元素，剩余内容都是由路由器去挂载不同组件完成的，所以不再需要`v-cloak`



## v-once

- 不需要表达式

- 作用的定义它的元素或组件只渲染一次

- 包括元素或组件的所有子节点

- 首次渲染后，不再随数据的变化重新渲染，被称为静态内容

- 代码示例

  ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>Title</title>
  </head>
  <body>
  
  <div id="app">
      <span v-once>
          {{message}}
      </span>
      <div v-once>
          <span>
              {{message}}
          </span>
      </div>
  </div>
  <script src="https://unpkg.com/vue@2.1.6/dist/vue.min.js"></script>
  <script>
      var app = new Vue({
          el:"#app",
          data:{
              message: "Hello kingdeguo"
          }
      })
  </script>
  </body>
  </html>
  ```

- 可能在优化性能的时候需要用到该指令

## v-if, v-else-if, v-else

- 代码示例

  ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>Title</title>
  </head>
  <body>
  <div id="app">
      <p v-if="status===1">show 1</p>
      <p v-else-if="status===2">show 2</p>
      <p v-else>show default</p>
  </div>
  <script src="https://unpkg.com/vue@2.1.6/dist/vue.min.js"></script>
  <script>
      var app = new Vue({
          el:"#app",
          data:{
              status: 1
          }
      })
  </script>
  </body>
  </html>
  ```

- 如果一次判断的是多个文本，在使用`template`

  ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>Title</title>
  </head>
  <body>
  <div id="app">
      <template v-if="status===1">
          <p>p1</p>
          <p>p2</p>
          <p>p3</p>
      </template>
  </div>
  <script src="https://unpkg.com/vue@2.1.6/dist/vue.min.js"></script>
  <script>
      var app = new Vue({
          el:"#app",
          data:{
              status: 1
          }
      })
  </script>
  </body>
  </html>
  ```

- Vue在渲染元素时，出于效率考虑，会尽可能复用已有的元素而非重新渲染

  ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>Title</title>
  </head>
  <body>
  
  <div id="app">
      <template v-if="type==='name'">
          <label>用户名：</label>
          <input placeholder="输入姓名">
      </template>
      <template v-else>
          <label>邮箱：</label>
          <input placeholder="请输入邮箱">
      </template>
      <button @click="handleToggleClick">Change</button>
  </div>
  <script src="https://unpkg.com/vue@2.1.6/dist/vue.min.js"></script>
  <script>
      var app = new Vue({
          el: "#app",
          data:{
              type: 'name'
          },
          methods:{
              handleToggleClick: function () {
                  this.type = this.type === "name" ? "mail" : "name";
              }
          }
      })
  </script>
  </body>
  </html>
  ```

  ![image-20210324223238091](https://raw.githubusercontent.com/KingdeGuo/myPictureBed/main/img_upload202103/24/223339-826966.png)

  最开始渲染的是这样的界面

  输入一段内容

  ![image-20210324223334289](https://raw.githubusercontent.com/KingdeGuo/myPictureBed/main/img_upload202103/24/223335-159836.png)

  然后点击切换

  ![image-20210324223401243](https://raw.githubusercontent.com/KingdeGuo/myPictureBed/main/img_upload202103/24/223401-464212.png)

  可以看到DOM虽然改变了，但是输入框中的内容并没有发生改变。这说明`<input>`标签中的内容被复用了。

- 如果不希望这样做，可以使用Vue.js提供的key属性，来决定元素是否复用。

  ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>Title</title>
  </head>
  <body>
  
  <div id="app">
      <template v-if="type==='name'">
          <label>用户名：</label>
          <input placeholder="输入姓名" key='my-name'>
      </template>
      <template v-else>
          <label>邮箱：</label>
          <input placeholder="请输入邮箱" key='my-mail'>
      </template>
      <button @click="handleToggleClick">Change</button>
  </div>
  <script src="https://unpkg.com/vue@2.1.6/dist/vue.min.js"></script>
  <script>
      var app = new Vue({
          el: "#app",
          data:{
              type: 'name'
          },
          methods:{
              handleToggleClick: function () {
                  this.type = this.type === "name" ? "mail" : "name";
              }
          }
      })
  </script>
  </body>
  </html>
  ```

  给`input`元素增加了key属性之后，就不会复用了。此时label仍然是被复用的，因为没有添加key属性。

## v-show

- 当v-show表达式为false时，元素会被隐藏。查看DOM结构元素上加载了内联样式display:none;
- v-if更适合条件不经常改变的场景，因为他的切换开销比较大，而v-show更适合频繁切换
- v-if在条件第一次为真时才开始编译



## v-for

- 代码示例

  ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>Title</title>
  </head>
  <body>
  <div id="app">
      <ul>
          <li v-for="(book, index) in books">
              {{index}}->{{book.name}}
          </li>
      </ul>
  </div>
  <script src="https://unpkg.com/vue@2.1.6/dist/vue.min.js"></script>
  <script>
      var app = new Vue({
          el: "#app",
          data:{
              books:[
                  {name:"Book1"},
                  {name:"Book2"},
                  {name:"Book3"},
              ]
          }
      })
  </script>
  </body>
  </html>
  ```

  ![image-20210324225919401](https://raw.githubusercontent.com/KingdeGuo/myPictureBed/main/img_upload202103/24/225922-934629.png)

- 同样可以使用`template`

  ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>Title</title>
  </head>
  <body>
  <div id="app">
      <ul>
          <template v-for="book in books">
              <li>书名：{{book.name}}</li>
              <li>作者：{{book.author}}</li>
          </template>
      </ul>
  </div>
  <script src="https://unpkg.com/vue@2.1.6/dist/vue.min.js"></script>
  <script>
      var app = new Vue({
          el: "#app",
          data:{
              books:[
                  {name:"Book1",
                      author:'111'},
                  {name:"Book2",
                      author:'222'},
                  {name:"Book3",
                      author:'333'},
              ]
          }
      })
  </script>
  </body>
  </html>
  ```

  ![image-20210324230317978](https://raw.githubusercontent.com/KingdeGuo/myPictureBed/main/img_upload202103/24/230322-956593.png)

- 除了数组之外，对象是属性也可以遍历

  