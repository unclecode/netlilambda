# netlambda

> A Vue.js project using netlify lambda

1. first create a vue project `vue init webpack netlambda`
2. second `yarn add -D netlify-lambda`
3. third `code .`
4. create  folder in `src` call `lambda` or anything else
5. add `hello.js` and create a handler 
6. add labda script to package json `"lambda":"netlify-lambda serve src/lambda"`
7. `yarn run lambda` check the function on 9000
8. add a button to call the function
9. resolve CORS
10. go to `config` folder and add a proxy to `config/index.js` under `dev`
11. ```proxyTable: {
      // proxy all requests starting with /api to jsonplaceholder
      "/.netlify/functions/": {
        target: "http://localhost:9000/",
        changeOrigin: true,
        pathRewrite: {
          "^/\\.netlify/functions/": ""
        }
      }
    }```
12. then in function call 
```javascript
fetch("/.netlify/functions/hello")
                .then(r => r.text())
                .then(d => {
                    this.msg = d;
                });
```




## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report
```

For a detailed explanation on how things work, check out the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).
