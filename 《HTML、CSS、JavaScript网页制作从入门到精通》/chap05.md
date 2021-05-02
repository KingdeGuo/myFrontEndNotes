[toc]

# 使用列表

- 有三种，分别是有序列表、无序列表、定义列表

- 有序列表

  ```html
  <ol>
      <li>Line One</li>
      <li>Line Two</li>
      <li>Line Three</li>
  </ol>
  ```

  - 可以通过`type`属性改变序号的类型，包括大小写字母、阿拉伯数字、大小写罗马数字。

    ![image-20210502092043544](https://raw.githubusercontent.com/KingdeGuo/myPictureBed/main/img_upload202105/02/092228-700836.png)

  - 可以通过`start`设置列表的起始数值

    ```html
    <ol type="I" start="3">
    	<li>Line One</li>
    	<li>Line Two</li>
    	<li>Line Three</li>
    </ol>
    ```

- 无序列表

  ```html
  <ul type="I" start="3">
      <li>Line One</li>
      <li>Line Two</li>
      <li>Line Three</li>
  </ul>
  ```

  - 可以通过`type`属性改变符号形状

    ![image-20210502092623264](https://raw.githubusercontent.com/KingdeGuo/myPictureBed/main/img_upload202105/02/092625-349738.png)

    ```html
    <ul type="square">
    	<li>Line One</li>
    	<li>Line Two</li>
    	<li>Line Three</li>
    </ul>
    ```

- 目录列表标记`dir`

  ```html
  <dir>
      <li>dir1</li>
      <li>dir2</li>
      <li>dir3</li>
  </dir>
  ```

- 定义列表标记`<dl>`

  