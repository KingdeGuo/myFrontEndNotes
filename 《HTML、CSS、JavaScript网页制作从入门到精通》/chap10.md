[toc]

# 使用表单

- `from`的`action`部分可以是一个邮箱地址。

  ```html
  <form action="mailto:XXX@qq.com">
      <input type="text">
      <input type="submit" value="提交">
  </form>
  ```

- `method`属性

  - get：表单数据被传送到`action`属性指定的URL，然后这个新的URL被送到处理程序上。
  - post：表单数据被包含在表单主体中，然后被送到处理程序上。

- 编码方式`enctype`

  - `application/x-www-form-urencoded`默认的编码方式
  - `multipart/form-data`MIME编码，上传文件的表单必须选择该项。

- `target`用来指定目标窗口打开方式

  表单的目标窗口往往用来显示表单的返回信息。

  取值有`_top`,`_self`,`_parent`,`_blank`四种。

  ```html
  <form action="demo01.html" target="_blank">
      <input type="text">
      <input type="submit" value="提交">
  </form>
  ```

- 可以使用一副图像作为按钮

  ```html
  <form action="demo01.html" target="_blank">
      <input name="input" type="image" src="../../images/11.jpg">
      <input type="submit" value="提交">
  </form>
  ```

- 有时候项传送一些数据，但是又不想让用户看见，可以使用`hidden`属性。

  ```html
  <input type="hidden" value="1">
  ```

- 文件部分

  ```html
  <input name="file_domain_name" type="file" size="控件长度" maxlength="字长字符数">
  ```

  注意文件传送需要使用`enctype=multipart/form-data`

