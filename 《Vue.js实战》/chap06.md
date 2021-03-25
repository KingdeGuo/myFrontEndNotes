[toc]

# 表单与v-model

- 完成表单的数据双向绑定

- 假如使用中文输入法，在没有选定词组之前Vue不会更新数据，如果希望实时更新，那么可以使用`@input`代替`v-model`.

  示例

  ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>Title</title>
  </head>
  <body>
  <div id="app">
      <input type="text" @input="myInput">
      <p>
          The message is: {{message}}
      </p>
  </div>
  <script src="https://unpkg.com/vue@2.1.6/dist/vue.min.js"></script>
  <script>
      var app = new Vue({
          el: "#app",
          data:{
              message:'kingdeguo'
          },
          methods:{
              myInput:function (e) {
                  this.message = e.target.value;
              }
          }
      })
  </script>
  </body>
  </html>
  ```

## 单选按钮

- 单独使用时，不需要`v-model`，直接使用`v-bind`绑定一个布尔类型的值，为真时选中，为否时不选。

  

- 如果组合使用来实现互斥选择的效果，就需要`v-model`配合`value`来使用。



