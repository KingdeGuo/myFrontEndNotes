[toc]

# 使用表格

- 基本表格

  ```html
  <table>
      <tr> <td>(1,1)</td> <td>(1,2)</td> </tr>
      <tr> <td>(2,1)</td> <td>(2,2)</td> </tr>
      <tr> <td>(3,1)</td> <td>(3,2)</td> </tr>
  </table>
  ```

  ![image-20210502094932313](https://raw.githubusercontent.com/KingdeGuo/myPictureBed/main/img_upload202105/02/100404-387738.png)

  - 设置表格标题`caption`

  - 表头`th`

    ```html
    <table>
        <caption>表格的标题</caption>
        <th>row1</th> <th>row2</th>
        <tr> <td>(1,1)</td> <td>(1,2)</td> </tr>
        <tr> <td>(2,1)</td> <td>(2,2)</td> </tr>
        <tr> <td>(3,1)</td> <td>(3,2)</td> </tr>
    </table>
    ```

    ![image-20210502095311531](https://raw.githubusercontent.com/KingdeGuo/myPictureBed/main/img_upload202105/02/100406-467077.png)

- 表格的一些属性

  - `border`表格的宽度
  - `cellspacing`表格的内框宽度属性
  - `cellpadding`表格内文字与边框间距

  - 代码示例

    ```html
    <table border="2px"
    		cellspacing="0" cellpadding="10px"
    		background="../../images/14.jpg">
    	<caption>表格的标题</caption>
    	<th>row1</th> <th>row2</th>
    	<tr background="../../images/11.jpg"> <td>(1,1)</td> <td>(1,2)</td> </tr>
    	<tr> <td>(2,1)</td> <td>(2,2)</td> </tr>
    	<tr> <td>(3,1)</td> <td>(3,2)</td> </tr>
    </table>
    ```

    ![image-20210502100213541](https://raw.githubusercontent.com/KingdeGuo/myPictureBed/main/img_upload202105/02/100408-395677.png)

- `valign`可以设置垂直对齐方式

  - 可取值有`top`, `middle`, `bottom`

- 单元格合并设置

  - `colspan`水平跨度
  - `rowspan`垂直跨度

- 

