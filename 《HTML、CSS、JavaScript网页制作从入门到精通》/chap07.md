[toc]

# 建立超链接

- 基本格式

  ```html
  <a href="" target=""> name </a>
  ```

  ![image-20210502103635163](https://raw.githubusercontent.com/KingdeGuo/myPictureBed/main/img_upload202105/02/103636-773685.png)

- 锚点链接

  - 首先创建锚点

  ```html
  <a name="锚点的名称"></a>
  ```

  - 然后在`href`中使用`#`以及`name`值来进行标记。

  ```html
  <p><a href="#1">come to that place.</a></p>
  ```

  - 代码示例

  ```htmL
  <a name="1"></a>
  <p><a href="#1">this is 啊</a></p>
  ```

  - 链接到其他页面中的锚点

  ```html
  <a href="链接的文件地址#锚点名称"></a>
  ```

- 链接到邮箱

  ```html
  <a href="mailto:邮件地址"></a>
  ```

- 链接到FTP

  ```html
  <a href="ftp://ftp地址"></a>
  ```

- 链接到Telnet

  ```html
  <a href="telnetL//地址"></a>
  ```

- 下载文件

  ```html
  <a href="文件地址"></a>
  ```

  