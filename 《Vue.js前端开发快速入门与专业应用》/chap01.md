[toc]

# Vue.js简介

- Vue的特点

  - 响应式编程：保持视图和状态的同步
  - 组件化：一切都是组件

- 一个数据绑定是实例

  ```js
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>Title</title>
      <script src="https://cdn.staticfile.org/vue/2.2.2/vue.min.js"></script>
  </head>
  <body>
  
  <div id="app">
      <span>You say: {{message}}</span> <br>
      <input type="text" v-model="message">
  </div>
  
  <script>
      var app = new Vue({
          el: "#app",
          data:{
              message: "hello world"
          }
      });
  </script>
  
  </body>
  
  </html>
  ```

- 一个组件化实例

  我们可以自己定义HTML标签，并在模板中使用它。

  ```js
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>Title</title>
      <script src="https://cdn.staticfile.org/vue/2.2.2/vue.min.js"></script>
  <!--    <script src="http://cdnjs.cloudflare.com/ajax/libs/vue/1.0.26/vue.min.js"></script>-->
  
  </head>
  <body>
  
  <div id="app">
      <message content='Hello, kingdeguo'></message>
  </div>
  
  
  <script>
      var Message = new Vue.extend({
          props:['content'],
          template:'<h1>{{content}}</h1>'
      });
      Vue.component('message', Message);
      var vm = new Vue({
          el: "#app"
      });
  </script>
  
  </body>
  
  </html>
  ```

  