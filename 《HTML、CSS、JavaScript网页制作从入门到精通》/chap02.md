[toc]

# HTML基本标记

- 元信息标记`meta`

  ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>Demo01</title>
  <!--    
      将name设置为keywords, 浏览器将根据content的内容进行搜索。
      这个关键词是看不见的，提供给浏览器使用。
  -->
      <meta name="keywords" content="mykeywords">
  <!--
      将name设置为description, 也就是将元信息设置为网页说明。
      用来详细说明网页内容，主要是为了便于搜索引擎的查找。
  -->
      <meta name="description" content="mydescription">
  <!--
      将name设置为generator, 可以设置网页编辑工具的名称。
  -->
      <meta name="generator" content="IDEA">
  <!--
      将name设置为author, 可以设置作者信息
  -->
      <meta name="author" content="kingdeguo">
      
  <!--
      还可以设置语言的编码方式
  -->
      <meta http-equiv="Content-Type" content="text/html;charset=utf-8">
  <!--
      设置网页自动刷新和网页跳转，跳转时间以秒为单位
  -->
      <meta http-equiv="refresh" content="20;url=demo01.html">
      
  </head>
  <body>
      
  </body>
  </html>
  ```

- `body`标签

  ```html
  <body bgcolor="red">设置颜色</body>
  <body background="img_url">设置背景图片</body>
  <!-- 设置全局的文字颜色-->
  <body text="#ff6347">
      I am red.
  </body>
  <!-- 设置全局的超链接的颜色-->
  <!--
  	link设置访问之前的颜色  
  	alink设置正在访问的颜色
  	vlink设置访问之后的颜色
  -->
  <body link="#ff6347">
      I am red.
  </body>
  <!-- 设置页面与浏览器边框上边距和左边距 -->
  <body topmargin="100px" leftmargin="100px">
      I am here
  </body>
  ```

- 

  