# 井字棋小游戏

利用父子组件间传值完成的一个井字棋小游戏。

预览地址：https://chenning02.github.io/git-demo-basics/dist/index.html

## 运行

```
yarn install
```

### Compiles and hot-reloads for development
```
yarn serve
```

### Compiles and minifies for production
```
yarn build
```

生成时注意在 `vue.config.js` 中修改以下路径，将 `/git-demo-basics/dist/` 修改为 `/仓库名/dist/`

```js
module.exports = {
    publicPath: process.env.NODE_ENV === 'production'
      ? '/git-demo-basics/dist/'
      : '/'
}
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).

