#### webpack中利用require.ensure()实现按需加载
```

require.ensure(dependencies: String[], callback: function(require), chunkName: String)
```
#### vue-infinite-scroll使用笔记

```
安装
npm install vue-infinite-scroll --save
尽管官方也推荐了几种载入方式，但“最vue”的方式肯定是在main.js中加入：
import infiniteScroll from 'vue-infinite-scroll'
Vue.use(infiniteScroll)
```
