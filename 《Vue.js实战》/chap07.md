[toc]

# 组件详解

- 注册组件有两种方式

  - 全局注册，任何Vue实例都可以使用

    ```js
    Vue.component('my-componet',{
    	// 选项
    })
    ```

    一个实例

    ```html
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <title>Title</title>
    </head>
    <body>
    <div id="app">
        <my-componet>
    
        </my-componet>
    </div>
    <script src="https://unpkg.com/vue@2.1.6/dist/vue.min.js"></script>
    <script>
        Vue.component('my-componet',{
            template:"<div>something to show</div>"
        });
    
        var app = new Vue({
            el: "#app"
        })
    </script>
    
    </body>
    </html>
    ```

    渲染结果就是

    ```html
    <div id="app">
        <div>
            something to show
        </div>
    </div>
    ```

    注意：

    - 在组件中添加`template`就可以显示内容了。

    - `template`的DOM结构必须被一个元素包含，如果直接写成`something to show`，不带`<div></div>`是无法渲染的。

  - 局部注册

    使用`componets`注册，注册后只有该实例作用域下有效。

    组件可以嵌套

    ```html
    <div id="app">
        <my-component></my-component>
    </div>
    <script>
    	var Child = {
            template:'<div>局域注册组件的内容</div>'
        }
        
        var app = new Vue({
            el:"#app",
            components:{
                'my-component':Child
            }
        })
    </script>
    ```

    