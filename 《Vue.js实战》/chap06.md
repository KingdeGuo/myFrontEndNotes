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

  ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>Title</title>
  </head>
  <body>
  <div id="app">
      <input type="radio" :checked="picked">
      <label>单选按钮</label>
  </div>
  <script src="https://unpkg.com/vue@2.1.6/dist/vue.min.js"></script>
  <script>
      var app = new Vue({
          el:"#app",
          data:{
              paickd: true
          }
      })
  </script>
  </body>
  </html>
  ```

- 如果组合使用来实现互斥选择的效果，就需要`v-model`配合`value`来使用。

  ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>Title</title>
  </head>
  <body>
  <div id="app">
      <input type="radio" v-model="picked" value="html" id="html">
      <label for="html">HTML</label>
      <input type="radio" v-model="picked" value="js" id="js">
      <label for="js">JS</label>
      <input type="radio" v-model="picked" value="css" id="css">
      <label for="css">CSS</label>
      <p>
          You Picked: {{picked}}
      </p>
  </div>
  <script src="https://unpkg.com/vue@2.1.6/dist/vue.min.js"></script>
  <script>
      var app = new Vue({
          el:"#app",
          data:{
              picked: 'js'
          }
      })
  </script>
  </body>
  </html>
  ```



## 复选框

- 单独使用时也需要绑定v-model

  ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>Title</title>
  </head>
  <body>
  <div id="app">
      <input type="checkbox" v-model="checked" id="checked">
      <label for="checked">State {{checked}}</label>
  
  </div>
  <script src="https://unpkg.com/vue@2.1.6/dist/vue.min.js"></script>
  <script>
      var app = new Vue({
          el:"#app",
          data:{
              checked: false
          }
      })
  </script>
  </body>
  </html>
  ```

- 组合使用

  ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>Title</title>
  </head>
  <body>
  <div id="app">
      <input type="checkbox" v-model="picked" value="html" id="html">
      <label for="html">HTML</label>
      <input type="checkbox" v-model="picked" value="js" id="js">
      <label for="js">JS</label>
      <input type="checkbox" v-model="picked" value="css" id="css">
      <label for="css">CSS</label>
      <p>
          You Picked: {{picked}}
      </p>
  </div>
  <script src="https://unpkg.com/vue@2.1.6/dist/vue.min.js"></script>
  <script>
      var app = new Vue({
          el:"#app",
          data:{
              picked: ['js']
          }
      })
  </script>
  </body>
  </html>
  ```



## 选择列表

- 单独使用

  ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>Title</title>
  </head>
  <body>
  <div id="app">
      <select v-model="selected">
          <option>html</option>
          <option value="js">js</option>
          <option>css</option>
      </select>
      <p>
          You Picked: {{selected}}
      </p>
  </div>
  <script src="https://unpkg.com/vue@2.1.6/dist/vue.min.js"></script>
  <script>
      var app = new Vue({
          el:"#app",
          data:{
              selected: 'html'
          }
      })
  </script>
  </body>
  </html>
  ```

- 多选

  ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>Title</title>
  </head>
  <body>
  <div id="app">
      <select v-model="selected" multiple>
          <option>html</option>
          <option value="js">js</option>
          <option>css</option>
      </select>
      <p>
          You Picked: {{selected}}
      </p>
  </div>
  <script src="https://unpkg.com/vue@2.1.6/dist/vue.min.js"></script>
  <script>
      var app = new Vue({
          el:"#app",
          data:{
              selected: 'html'
          }
      })
  </script>
  </body>
  </html>
  ```

- `<option>`经常使用`v-for`动态输出。

  代码示例

  ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>Title</title>
  </head>
  <body>
  <div id="app">
      <select v-model="selected">
          <option v-for="option in options" :value="option.value">
              {{option.text}}
          </option>
      </select>
      <p>
          You Picked: {{selected}}
      </p>
  </div>
  <script src="https://unpkg.com/vue@2.1.6/dist/vue.min.js"></script>
  <script>
      var app = new Vue({
          el: "#app",
          data:{
              selected: 'html',
              options:[
                  {
                      text: "HTML",
                      value: 'html'
                  },
                  {
                      text: "JavaScript",
                      value: "js"
                  },
                  {
                      text: "CSS",
                      value:'css'
                  }
              ]
          }
      })
  </script>
  </body>
  </html>
  ```

## 绑定值



