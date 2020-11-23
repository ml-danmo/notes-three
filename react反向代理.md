### 反向代理
https://facebook.github.io/create-react-app/docs/proxying-api-requests-in-development

*********在src/setupProxy.js
```js
//npm install http-proxy-middleware --save

const { createProxyMiddleware } = require('http-proxy-middleware');

module.exports = function(app) {
  app.use(
    '/mobile',                           //一遇到这个路由
    createProxyMiddleware({
      target: 'http://www.ggrsc.com',    //就目标到这个地址
      changeOrigin: true,
    })
  );
};
```