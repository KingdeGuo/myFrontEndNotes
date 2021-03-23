[toc]

# 计算属性

- 遇到负责的逻辑时应该使用计算属性`computed`

  ```js
  var app = new Vue({
      el:'#app',
      data:{
          s:"123,456"
      },
      computed:{
          reverseText:function(){
              return this.s.split('.').reverse().join(',');
          }
      }
  })
  ```

- 计算属性可以依赖多个Vue实例的数据

  ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>Title</title>
  </head>
  <body>
  
  <div id="app">
      {{sum}}
  </div>
  
  <script src="https://unpkg.com/vue@2.1.6/dist/vue.min.js"></script>
  <script>
      var app = new Vue({
          el:'#app',
          data:{
              num1:{
                  val:1
              },
              num2:{
                  val:2
              }
          },
          computed:{
              sum:function () {
                  var temp = 0;
                  return this.num1.val + this.num2.val;
              }
          }
      })
  </script>
  
  </body>
  </html>
  ```

- 当num1或者num2中的val发生变化时，sum的值也会发生变化

- 每一个计算属性都包含一个`getter`和一个`setter`属性。

  ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>Title</title>
  </head>
  <body>
  
  <div id="app">
      {{fullName}}
  </div>
  <script src="https://unpkg.com/vue@2.1.6/dist/vue.min.js"></script>
  <script>
      var app = new Vue({
          el: "app",
          data:{
              firstName: 'Jack',
              lastName: 'Green'
          },
          computed:{
              fullName:{
                  get:function () {
                      return this.firstName + " " + this.lastName;
                  },
                  set: function (newValue) {
                      var names = newValue.splice(' ');
                      this.firstName = names[0];
                      this.lastName = names[names.length - 1];
                  }
              }
          }
      })
  </script>
  </body>
  </html>
  ```

- 计算属性的两个小技巧

  - 计算属性可以依赖其他计算属性
  - 计算属性不仅可以依赖当前Vue实例的数据，还可以依赖其他实例数据

  ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>Title</title>
  </head>
  <body>
  <div id="app1"></div>
  <div id="app2">
      {{showAdd}}
  </div>
  
  <script src="https://unpkg.com/vue@2.1.6/dist/vue.min.js"></script>
  <script>
      var app1 = new Vue({
          el:'#app1',
          data:{
              num:1
          }
      });
      var app2 = new Vue({
          el:"#app2",
          data:{
              num:2,
          },
          computed:{
              showAdd:function () {
                  return app1.num + this.num;
              }
          }
      })
  </script>
  </body>
  </html>
  ```

- 计算属性是依赖于缓存的，当计算属性所依赖的数据发生变化时，它才会重新获取新值。`method`里也可以达到同样的效果，但是它不会缓存。因此，使用计算属性还是`methods`取决于你是否需要缓存，当遍历大数组和做大量计算时，应当使用计算属性，除非你不希望得到缓存。