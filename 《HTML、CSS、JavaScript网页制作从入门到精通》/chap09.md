[toc]

# 使用框架结构

- 框架基本语法

  - 水平分割窗口`rows`
  - 垂直分割窗口`cols`
  - 代码示例

  ```html
  <frameset rows="20%,30%">
      <frame src="demo01.html" scrolling="no">
      <frame src="demo01.html">
  </frameset>
  ```

  - `frameborder`取值为`0`或`1`，或者`yes`, `no`。用来表示边框是否有效。
  - `framespacing`设置边框之间线条的宽度，以像素为单位。默认为1
  - `noresize`使不能拖动边框
  - `marginheight`边框与内容的垂直距离。
  - `noframes`用来提示用户无法显示框架
  - `iframe`是浮动框架。