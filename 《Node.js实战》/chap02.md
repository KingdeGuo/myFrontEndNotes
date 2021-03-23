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

- 