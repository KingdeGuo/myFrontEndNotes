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

## v-if, v-else-if, v-else

