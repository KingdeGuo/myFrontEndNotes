[toc]

# 使用CSS样式表

- 使用方式

  - 链接外部样式表

    ```html
    <link rel="stylesheet" type="text/css" href="../../css/1.css" >
    ```

  - 内部样式表

    ```html
    <style type="text/css">
    
    </style>
    ```

  - 外部样式表

    ```html
    @import mystyle.css
    ```

  - 内嵌样式

    ```html
    <p style=""></p>
    ```

- 字体

  小写转化成大写`font-variant`

- 背景

  `background`取值为`scroll`或者`fixed`，是滚动还是静止不动。

- 文本

  `text-decoration`可以对文本进行修饰。

  `underline`表示下划线，`overline`上划线，`line-through`删除线，`blink`文字闪烁.

  `text-transform`用来转化英文字母的大小写.

  `text-indent`设置缩进值

  `line-height`设置行高

- 外边距与内边距

  - 盒子模型

  ![image-20210503185111572](https://raw.githubusercontent.com/KingdeGuo/myPictureBed/main/img_upload202105/03/185113-103966.png)

- 定位属性

  使用`position: static | absolute | fixed | relative`

  