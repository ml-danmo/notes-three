### 模拟数据json-server
    我们在开发中并不想使用简单的静态数据，而是希望自己起一个本地模拟请求以及请求回来的过程。
    json-server就是用来完成模拟数据的


    下载：cnpm install json-server -g

    查看版本： json-server --version
##### 创建数据
    在项目下创建一个mock的文件夹并且写入相关的数据.json
##### 启动
    json-server默认端口为3000 我们不能直接启动会和react脚手架冲突
    所以我们启动的时候需要修改端口

    1.cd 到mock文件夹路径下 

    2.json-server --watch json的名字 --port 4000

    3.在浏览器中测试一下 http://localhost:4000/数据的key
