# 一个路由项目的搭建示例！！！
```js
#vue create 名字

#删除components和views下自带的文件，app.vue文件中删除（自带配置）

#创建api和mock文件夹：

    ##mock文件夹下的index.js中配置：

        let Mock = require("mockjs");
        Mock.mock("wode/data","get",require("./data/wode.json"))
    
    ##main.js中配置：

        require("./mock")"
    ##api/api.js利用axios发送数据

        // import axios from "axios";
        // export function jump(){
        //     return new Promise((resolve,reject)=>{
        //         axios({
        //             url:"wode/data",
        //             methods:"get"
        //         }).then(res=>{
        //             resolve(res)
        //         }).catch(rej=>{
        //             reject(rej)
        //         })
        //     })
        // }

    ##如果是  axios 拦截器 发送数据

        ###在src文件夹下创建一个util（工具文件夹）：在util工具文件夹中创建request.js文件用来编写拦截器。
        
                import axios from "axios"
                // 创建axios 赋值给常量service 
                const service = axios.create();

                // 添加请求拦截器（Interceptors）
                service.interceptors.request.use(function (config) {
                    // 发送请求之前做写什么
                    return config;
                }, function (error) {
                    // 请求错误的时候做些什么
                    return Promise.reject(error);
                });

                // 添加响应拦截器
                service.interceptors.response.use(function (response) {
                    // 对响应数据做点什么
                    return response;
                }, function (error) {
                    // 对响应错误做点什么
                    return Promise.reject(error);
                });
                export default service


        ###api文件夹下创建发送axios的文件发送数据

                import server from "@/util/request.js";

                export function top(){
                    return new Promise((resolve,reject)=>{
                        server.request({
                            url:"index/topdata",
                            methods:"get"
                        }).then(res=>{
                            resolve(res)
                        }).catch(rej=>{
                            reject(rej)
                        })
                    })
                }

        ###在接受数据的文件中：


#在app.vue文件中设置全局样式

        *{
        margin: 0;
        padding: 0;
        }
        ul,ol{
        list-style: none;
        }

        html{
        font-size: 26.67vw;
        }

# 在项目的根目录下创建vue.config.js 
    配置自动打开:
        module.exports={
            devServer:{
                open:true,
                port:8888
            }
        }

    配置解析别名：
        configureWebpack:{
            resolve:{
                alias:{
                    //"别名"："对应的文件夹"
                    "com":"@/components"
                }
            }
        }

#在views文件夹下 创建一级路由页面：创建模板
        <template>
            <div>
                购物车
            </div>
        </template>

#在router下的index.js中引进并配置路由规则
        import Vue from 'vue'
        import VueRouter from 'vue-router'

        import Cart from '@/views/cart.vue';

        Vue.use(VueRouter)

        const routes = [
            {
                path: '/cart',
                name: 'Cart',
                component: Cart
            },
            {                //重定向
                path: '/',
                redirect:"/index"
            },
            {                   //404页面
                path: '*',
                name: 'No',
                component: No
            }  
        ]

#main.js中配置路由：
        new Vue({
            router,
            render: h => h(App)
        }).$mount('#app')


#app.vue:写导航

    <router-link to="/index">  index  </router-link>
    <router-link to="/cart">  cart  </router-link>
    <router-link to="/wode">  wode  </router-link>

    <router-view/>  //路由出口

```