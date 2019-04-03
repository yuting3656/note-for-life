# 想要讓某 class 的 min-height 和 screen size 一樣高

> link: https://stackoverflow.com/questions/26837493/how-to-set-min-height-and-max-height-equal-to-window-height/26837604#26837604

~~~css
.nav-sm .container.body .right_col {
  padding: 10px 20px;
  margin-left: 70px;
  z-index: 2;
  min-height: 100vh;
}
~~~