### 动态创建navbar
最初的样式---(用ant-design)

<img src="img/1.png" height="150px">
<img src="img/2.png" height="100px">

结构

<img src="img/3.png" height="230px">

创建navbar的动态数据，在js文件中，并将数据暴露出去

<img src="img/4.png" height="230px">


在将渲染的逻辑封装成一个函数，直接在渲染的地方调用函数

<img src="img/5.png" height="210px">

    map()循环遍历接受到的数据,判断每条数据中是否存在children

    如果有代表有嵌套列表，返回\<SubMenu>,然后继续判断嵌套中是否还存在children-----
    (这可以利用递归的原理再次调用renderMenu()函数)

    如果没有代表只有自己，返回一个\<Menu>
<img src="img/6.png" height="250px">

路由跳转

<img src="img/7.png" height="210px">
