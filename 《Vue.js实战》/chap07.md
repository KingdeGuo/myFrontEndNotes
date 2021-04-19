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
        <my-componet>
        </my-componet>
    </div>
    
    <script>
        var Child = {
            template:"<div>局部注册</div>"
        };
        var app = new Vue({
            el: "#app",
            components:{
                'my-componet': Child
            }
        })
    </script>
    ```

    Vue组件的模板在某些情况下会受到HTML的限制，比如`<table>`内规定只能是`<tr>`，`<td>`，`<th>`等表格元素，所以在`<table>`内直接使用组件是无效的。这种情况下，使用特殊的`is`属性来挂载组件。

    常见的限制元素还有`<ul>`，`<ol>`，`<select>`。

    ```html
    <div id="app">
    	<table>
            <today is="my-componet"></today>
        </table>
    </div>
    
    <script>
        Vue.component('my-componet',{
            template:"<div>something to show</div>"
        });
    
        var app = new Vue({
            el: "#app"
        })
    </script>
    ```

  - 除了template选项外，组件中还可以想Vue实例那样引用其他的选项，比如data，computed，methods等。但是在使用data时，和实例稍有区别，data必须是函数，然后将数据return出去

    代码示例

    ```html
    <div id="app">
    	<my-componet>
        </my-componet>
    </div>
    	
    <script>
        Vue.component('my-componet',{
            template:"<div>something to show</div>",
            data:function(){
                return {
                    message:"组件内容"
                }
            }
        });
    
        var app = new Vue({
            el: "#app"
        })
    </script>
    ```

  - JavaScript对象是引用关系，如果return出的对象引用了外部的一个对象，那么这个对象就是共享的。任何一方的修改都会同步。

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
        <my-component></my-component>
        <my-component></my-component>
        <my-component></my-component>
    </div>
    <script src="https://unpkg.com/vue@2.1.6/dist/vue.min.js"></script>
    <script>
        var data = {
            count: 0
        };
    
        Vue.component('my-component',{
            template:'<button @click="count++">{{count}}</button>',
            data:function () {
                return data;
            }
        });
    
        var app = new Vue({
            el: "#app"
        })
    </script>
    
    </body>
    </html>
    ```

    组件使用了三次，点击任意一个，三个的数字都会加1。这不是我们期望的结果，所以给组件返回一个新的data对象来独立。

    ```html
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <title>Title</title>
    </head>
    <body>
    <div id="app">
        <my-component></my-component>
        <my-component></my-component>
        <my-component></my-component>
    </div>
    <script src="https://unpkg.com/vue@2.1.6/dist/vue.min.js"></script>
    <script>
        Vue.component('my-component',{
            template:'<button @click="count++">{{count}}</button>',
            data:function () {
                return {
                    count: 0
                }
            }
        });
    
        var app = new Vue({
            el: "#app"
        })
    </script>
    
    </body>
    </html>
    ```



## 使用props传递数据

- 模板间的通信。
- 通常父组件的模板中包含子组件，父组件要正向地向子组件传递数据或参数，子组件接收到后根据参数的不同来渲染不同的内容或执行操作。
- 使用选项`props`来声明需要从父级接收的数据，`progs`的值可以是字符串数组或者对象。
- 

