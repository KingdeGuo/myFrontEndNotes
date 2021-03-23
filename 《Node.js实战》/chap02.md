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

