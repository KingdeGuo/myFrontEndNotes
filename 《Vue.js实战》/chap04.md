[toc]

# v-bind及class与style绑定

# 绑定class的几种方式

- 对象语法

  ```html
  <div id="app">
      <div :class="{'active':isActive}"></div>
  </div>
  <script src="https://unpkg.com/vue@2.1.6/dist/vue.min.js"></script>
  <script>
      var app = new Vue({
          el: '#app',
          data:{
              isActive: true
          }
      })
  </script>
  ```

  上例最终渲染完成的是

  ```html
  <div class="active"></div>
  ```

  也可以传入多个属性，来动态切换class。且`:class`可以与普通的`class`共存

  ```html
  <div id="app">
      <div class="static" :class="{'active':isActive, 'error':isError}"></div>
  </div>
  <script src="https://unpkg.com/vue@2.1.6/dist/vue.min.js"></script>
  <script>
      var app = new Vue({
          el: '#app',
          data:{
              isActive: true,
              isError:false
          }
      })
  </script>
  ```

  上例最终渲染完成的是

  ```html
  <div class="static active"></div>
  ```

  当`:class`的表达式过长或逻辑复杂时，还可以绑定一个计算属性。一般当条件多于两个时，都可以使用`data`或`computed`

  ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>Title</title>
  </head>
  <body>
  
  <div id="app">
      <div :class="classes"></div>
  </div>
  <script src="https://unpkg.com/vue@2.1.6/dist/vue.min.js"></script>
  <script>
      var app = new Vue({
          el: "#app",
          data:{
              isActive:true,
              isError:false
          },
          computed:{
              classes:function () {
                  return{
                      active: this.isActive && !this.error,
                      'text-fail': this.error && this.error.type === 'fail'
                  }
              }
          }
      })
  </script>
  </body>
  </html>
  ```

- 数组语法

  给`:class`绑定一个数组

  ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>Title</title>
  </head>
  <body>
  <div id="app">
      <div :class="[activeCls, errorCls]"></div>
  </div>
  <script src="https://unpkg.com/vue@2.1.6/dist/vue.min.js"></script>
  <script>
      var app = new Vue({
          el: "app",
          data:{
              activeCls:'active',
              errorCls:'error'
          }
      })
  </script>
  
  </body>
  </html>
  ```

  也可以使用三元表达式来根据条件切换class

  ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>Title</title>
  </head>
  <body>
  <div id="app">
      <div :class="[isAvtive? activeCls:'', errorCls]"></div>
  </div>
  <script src="https://unpkg.com/vue@2.1.6/dist/vue.min.js"></script>
  <script>
      var app = new Vue({
          el: "app",
          data:{
              activeCls:'active',
              errorCls:'error'
          }
      })
  </script>
  
  </body>
  </html>
  ```

  可以使用对象语法简化

  ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>Title</title>
  </head>
  <body>
  <div id="app">
      <div :class="[{'active':isActive}, errorCls]"></div>
  </div>
  <script src="https://unpkg.com/vue@2.1.6/dist/vue.min.js"></script>
  <script>
      var app = new Vue({
          el: "app",
          data:{
              activeCls:'active',
              errorCls:'error'
          }
      })
  </script>
  
  </body>
  </html>
  ```

  同样可以使用计算属性

  ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>Title</title>
  </head>
  <body>
  <div id="app">
      <div :class="classes"></div>
  </div>
  <script src="https://unpkg.com/vue@2.1.6/dist/vue.min.js"></script>
  <script>
      var app = new Vue({
          el: "app",
          data:{
              size:'large',
              disabled:true
          },
          computed:{
              classes:function(){
                  return{
                      'btn',
                      {
                    		['btn-' + this.size]:this.size !== '',
                          ['btn-disabled']:this.disabled
                  	}
                  };
              }
          }
      })
  </script>
  
  </body>
  </html>
  ```

  渲染结果为

  ```html
  <button class="btn btn-large bth-disabled"></button>
  ```

- 在组件上使用

  如果直接在自定义组件上使用`class`或`:class`，样式规则会直接应用到这个组件的根元素上。

  ```html
  Vue.componet('my-component',{
  	template:'<p class='article'>一些文本</p>'
  })
  ```

  然后在调用这个组件时，使用对象语法或者数据语法绑定class。例如

  ```html
  <div id='app'>
      <my-component :class="{'active':isActive}"></my-component>
  </div>
  <script>
  	var app = new Vue({
          el:"#app",
          data:{
              isActive:true
          }
      })
  </script>
  ```

  渲染结果为

  ```html
  <p classs='article active'>
      一些文本
  </p>
  ```

  注意，这种用法仅适用于自定义组件的最外层是一个根元素，否则会失效，当不满足这种条件或需要给具体的子元素设置类名时，应该使用组件的props来传递，这些用法同样适用于绑定内联样式style的内容。

## 绑定内联样式

