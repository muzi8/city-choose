### 一个类似通讯录的城市选择demo
这个项目之前是想用同事给的设计稿当做练手项目来做的。
下面是同事给的设计稿

![我是设计稿图片](https://coding.net/u/muzi8/p/Travel/git/raw/master/design.png)

> 2018/05/25

构建项目

### 目录结构
```
│  .babelrc -------------- babel的配置项
│  .editorconfig -------------- 配置编辑器的语法
│  .eslintignore -------------- 不受eslint检测的配置
│  .eslintrc.js -------------- 配置代码规范
│  .gitignore -------------- 上传到仓库的一些忽略配置项
│  .postcssrc.js -------------- 对postcss的配置项
│  index.html -------------- 项目默认的模板文件
│  package-lock.json -------------- 锁文件，确定第三方包的具体版本
│  package.json -------------- 项目的第三方依赖
│  README.md -------------- 项目说明文件
│
├─build -------------- 项目打包的webpack的配置内容(一般不需要修改，webpack自动打包的)
│
├─config -------------- 项目的配置文件夹
│      dev.env.js -------------- 开发环境的配置信息
│      index.js -------------- 基础配置信息
│      prod.env.js -------------- 生产环境的配置信息
├─src -------------- 项目的源代码(业务代码的开发)
│  │  App.vue -------------- 项目最原始的根组件
│  │  main.js -------------- 项目的入口文件
│  │
│  ├─assets -------------- 项目要用到的图片资源
│  │
│  ├─components -------------- 项目要用到的小组件
│  │
│  └─router<
│          index.js -------------- 项目的路由
│
└─static -------------- 静态资源（图片或者模拟的json数据）
```
#### Build Setup

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

---

###### 在webpack.base.config.js中删去了rules里关于scss和css的配置

因为新版的`vue-cli`在`build/util.js`已经配置了这些，如果在`webpack.base.config.js`中再写就是重复配置，会导致在`main.js`中全局引用`css`和`scss`的时候报错。

## 更新自2019/03/29
product组件我删掉跳转，因为详情页当时并没有完成，同事后来删掉了这个项目的设计稿，我没办法去看标注了。。所以项目慢慢作废了，但是对于城市选择这里，还是可以当做一个练手的组件
