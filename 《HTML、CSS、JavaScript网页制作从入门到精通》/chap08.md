[toc]

# 添加多媒体

- 滚动标记`marquee`

  ```html
  <marquee>
      <font face="宋体">你好</font>
      <img src="../../images/11.jpg">
  </marquee>
  ```

  - 可以通过`direction`的值设置滚动的方向

    取值有`up`, `down`, `left`, `right`

  ```html
  <marquee direction="up">
      <font face="宋体">你好</font>
      <img src="../../images/11.jpg">
  </marquee>
  ```

  - 可以通过`behavior`来设置滚动方式

    ​	取值有`scroll`, `slide`, `alternate`

  ```html
  <marquee behavior="alternate">
      <font face="宋体">你好</font>
  </marquee>
  ```

  - 可以通过`scrollamount`设置滚动的快慢

    其实就是通过滚的那个时移动的长度来设置的，以像素为单位。

  ```html
  <marquee behavior="scroll" scrollamount="30">
      <font face="宋体">你好</font>
  </marquee>
  ```

  - 可以通过`scrolldelay`设置滚动的时间间隔

    时间间隔为毫秒

  ```HTML
  <marquee direction="up" scrollamount="30" scrolldelay="400">
      <font face="宋体">你好</font>
  </marquee>
  ```

  - 可以通过`loop`设置滚动的次数

  ```html
  <marquee direction="up" loop="3">
      <font face="宋体">你好</font>
  </marquee>
  ```

  - 可以通过`hspace`和`vspace`设置水平范围、垂直范围

- 可以通过`embed`标签插入flash。

- 可以通过`bgsound`标记背景音乐。

- 