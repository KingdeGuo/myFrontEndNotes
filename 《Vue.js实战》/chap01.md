[toc]

# 初识Vue.js

- 采用MVVM模式

  ![image-20210323160118617](https://raw.githubusercontent.com/KingdeGuo/myPictureBed/main/img_upload202103/23/160119-414914.png)

- 当View变化时，会自动更新到ViewModel，反之亦然。

- MVVM将模式拆分为视图和数据两个部分，并将其分离。

- 使用VUE的方式

  - 采用CDN加载
    - 获取特定版本`<script src="https://unpkg.com/vue@2.1.6/dist/vue.min.js"></script>`
    - 获取最新版`<script src="https://unpkg.com/vue/dist/vue.min.js"></script>`
  - 下载之后给出文件引用

- 代码示例1：点击按钮触发事件

  ```html
  <!DOCTYPE html>
  <head>
      <meta charset="UTF-8">
      <title>Title</title>
  </head>
  <body>
  <div id="app">
      <button v-if="buttonShow" v-on:click="handleClick">Click me</button>
  </div>
  
  
  <script src="https://unpkg.com/vue@2.1.6/dist/vue.min.js"></script>
  <script>
      new Vue({
          el:'#app',
          data:{
              buttonShow:true
          },
          methods:{
              handleClick: function () {
                  alert("You clicked");
              }
          }
      });
  </script>
  </body>
  </html>
  ```

- 代码示例2：

  ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>Vue示例1</title>
      <style>
          .myli{
              background: blanchedalmond;
              font-family: 楷体;
              font-size: larger;
          }
      </style>
  </head>
  
  <body>
      <div id="app" class="myli">
          <ul>
              <li v-for="book in books">{{book.name}}</li>
          </ul>
      </div>
  
      <script src="https://unpkg.com/vue@2.1.6/dist/vue.min.js"></script>
      <script>
          new Vue({
              el: '#app',
              data:{
                  books:[
                      {name:'《Vue.js》'},
                      {name:'《Java核心技术》'},
                      {name:'《Java编程思想》'},
                  ]
              }
          });
      </script>
  </body>
  </html>
  ```

  ![image-20210323162932902](https://raw.githubusercontent.com/KingdeGuo/myPictureBed/main/img_upload202103/23/162933-942431.png)

