[toc]

# 使用图像

- 一般浏览器对`jepg`和`gif`的支持更好。

  - GIF

    GIF是英文单词Graphic Interchange Format的缩写，即图像交换格式，文件最多可使用256种颜色，最适合显示色调不连续或具有大面积单一颜色的图像， 例如导航条、按钮、图标、徽标或其他具有统- - 色彩和色调的图像。
    GIF格式的最大优点就是可制作动态图像，可以将数张静态文件作为动画帧串联起来，转换成一个动画文件。
    GIF格式的另一优点就是可以将图像以交错的方式在网页中呈现。所谓交错显示，就是当图像尚未下载完成时，浏览器会先以马赛克的形式将图像慢慢显示，让浏览者可以大略猜出下载图像的雏形。

  - JEPG

    JPEG格式是一种压缩 的非常紧凑的格式，专门用于不含大色块的图像。JPEG图像有一定的失真度，但是在正常的损失下肉眼分辨不出JPEG和GIF图像的区别，而JPEG文件只有GIF文件的1/4。JPEG对图标之类的含大色块的图像不是很有效，不支持透明图和动态图，但它能够保留全真的色调板格式。如果图像需要全彩模式才能表现效果的话，JPEG 就是最佳的选择。

  - PNG

    PNG图像格式是一-种 非破坏性的网页图像文件格式，它提供了将图像文件以最小的方式压缩却又不造成图像失真的技术。它不仅具备了GIF图像格式的大部分优点，而且还支持48-bit的色彩，更快地交错显示，跨平台的图像亮度控制，更多层的透明度设置。

- 常用属性

  ![image-20210501215135800](https://raw.githubusercontent.com/KingdeGuo/myPictureBed/main/img_upload202105/01/215137-260943.png)

- 图片热区

  - 首先需要在图像文件中设置映射图像名，在图像的属性中使用`<usemap>`标记添加图像要引用的映射图像的名称。

    ```html
    <map name="mymap">
            <area shape="热区形状" coords="热区坐标" href="链接地址">
    </map>
    ```

  - 代码示例

    ```html
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <title>Demo01</title>
    </head>
    <body>
        <map name="mymap">
            <area shape="rect" coords="10,10,30,30" href="#">
        </map>
    
        <img src="../../images/11.jpg" alt="error" usemap="#mymap">
    </body>
    </html>
    ```

    