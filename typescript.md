#### typescript
    TypeScript是一种由微软开发的自由和开源的编程语言。
    它是JavaScript的一个超集，而且本质上TypeScript扩展了JavaScript的语法
    解决JavaScript的“痛点”：弱类型和没有命名空间，导致很难模块化。
##### 为什么要用TypeScript
    开源

    简单
        TypeScript 是 JavaScript 的超集，这意味着他支持所有的 JavaScript 语法。

    兼容性好
        TScript 是 JS的强类型版本。然后在编译期去掉类型和特有语法，生成纯粹的 JavaScript 代码。
        由于最终在浏览器中运行的仍然是 JS，所以 TScript 并不依赖于浏览器的支持，也并不会带来兼容性问题。
        任何现有的JS程序可以不加改变的在TScript下工作。
##### 与js相比的优势
    TypeScript工具使重构更变的容易、快捷。

    TypeScript 引入了 JavaScript 中没有的“类”概念。

    TypeScript 中引入了模块的概念，可以把声明、数据、函数和类封装在模块中
     
    类型安全功能能在编码期间检测错误，这为开发人员创建了一个更高效的编码和调试过程。
##### 安装
    node 服务器 
    TypeScript解释器npm install -g typescript  -g 全局安装 ，在本机上 哪里都能用
    tsc空格-v命令用来测试是否安装成功
##### 文件声明与使用
    文件后缀 文件名称.ts
    每次修改.ts文件都需要编译, 使用命令: tsc 文件名
    会自动生成xxx.js文件 
    如果想使用必须在HTML文件中使用script标签引用新生成的xxx.js文件
##### 变量
    let/var 变量名称：数据类型 = value

    let(块变量)和const（常量）是JavaScript里相对较新的变量声明方式。	

    注意：let变量不能重复声明

    注意：const它拥有与 let相同的作用域规则，但是不能对它们重新赋值。

    注意:除了下划线 _ 和美元 $ 符号外，不能包含其他特殊字符，包括空格
##### 数据类型
    布尔值 ：boolean

    数字 ：number

    字符串 ：string可以使用双引号（ "）或单引号（'）表示字符串
    
    数组 ：number[]或 ：Array<number>
