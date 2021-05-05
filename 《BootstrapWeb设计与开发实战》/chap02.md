[toc]
# Bootstrap开发环境

- Bootstrap的JS效果都是基于Jquery的，所以同时要引入JQuery文件。

  ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>Title</title>
      <link rel="stylesheet" href="../../bootstrap-5.0.0-beta3-dist/css/bootstrap.css">
  </head>
  <body>
  
  <script src="../../js/jquery-3.6.0.min.js"></script>
  <script src="../../bootstrap-5.0.0-beta3-dist/js/bootstrap.js"></script>
  </body>
  </html>
  ```

- 调用bootstrap样式

  ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>Title</title>
      <link rel="stylesheet" href="../../bootstrap-5.0.0-beta3-dist/css/bootstrap.css">
  </head>
  <body>
  
  <table class="table table-striped table-bordered">
      <tr>
          <th>name</th>
          <th>age</th>
          <th>class</th>
      </tr>
      <tr>
          <td>nihao</td>
          <td>18</td>
          <td>One</td>
      </tr>
  </table>
  
  
  <script src="../../js/jquery-3.6.0.min.js"></script>
  <script src="../../bootstrap-5.0.0-beta3-dist/js/bootstrap.js"></script>
  </body>
  </html>
  ```

  ![image-20210505155752436](https://raw.githubusercontent.com/KingdeGuo/myPictureBed/main/img_upload202105/05/155754-878500.png)

- 调用bootstrap组件

  以导航栏为例

  ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>Demo02</title>
  </head>
  <body>
      <div class="navbar">
          <div class="navbar-inner">
              <a class="brand" href="#">Bootstrap</a>
              <ul class="nav">
                  <li class="active"><a href="#">Home</a></li>
                  <li><a href="#">News</a></li>
                  <li><a href="#">BBS</a></li>
                  <li><a href="#">About</a></li>
              </ul>
          </div>
  
      </div>
  </body>
  </html>
  ```

  ![image-20210505161345882](https://raw.githubusercontent.com/KingdeGuo/myPictureBed/main/img_upload202105/05/161347-247378.png)

- 调用bootstrap js效果

  ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>Demo03</title>
      <link rel="stylesheet" href="../../bootstrap-5.0.0-beta3-dist/css/bootstrap.css">
  </head>
  <body>
  
  <ul class="nav nav-tabs" id="myTab">
      <li class="active"><a href="#home" data-toggle="tab">Home</a></li>
      <li><a href="#news" data-toggle="tab">Home</a></li>
      <li><a href="#blog" data-toggle="tab">Blog</a></li>
      <li><a href="#about" data-toggle="tab">About</a></li>
  </ul>
  
  <div class="tab-content">
      <div class="tab-pane active" id="home">Home Page</div>
      <div class="tab-pane" id="news">News Page</div>
      <div class="tab-pane" id="blog">Blog Page</div>
      <div class="tab-pane" id="about">About Page</div>
  </div>
  
  
  
  <script src="../../js/jquery-3.6.0.min.js"></script>
  <script src="../../bootstrap-5.0.0-beta3-dist/js/bootstrap.js"></script>
  
  <script>
      $('#myTab a').click(function (e) {
          e.preventDefault();
          $(this).tab('show');
      })
  </script>
  </body>
  </html>
  ```

  ![image-20210505161555995](https://raw.githubusercontent.com/KingdeGuo/myPictureBed/main/img_upload202105/05/161556-869587.png)

