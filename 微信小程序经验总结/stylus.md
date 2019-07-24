#### 强大的css预编译stylus以及在vue中使用stylus

```
//配置背景图片函数
mixin.styl:
bg-image($url)
  background-image: url($url + "2.png")
  @media (-webkit-min-device-pixel-ratio: 3),(min-device-pixel-ratio: 3)
    background-image: url($url + "3.png")
```

```
variable.styl
// 颜色定义规范
$color-theme = #ffcd32

//字体定义规范
$font-size-medium = 14px
```

```
content.vue
<style scoped lang="stylus" rel="stylesheet/stylus">
  @import "~common/stylus/mixin"
  @import "~common/stylus/variable"
    .recommend-list
      .list-title
        height 300px
        width 100%
        font-size $font-size-medium
        color $color-theme
      .item
        padding 0 20px 20px 20px
        background bg-image('../images/bg.png')
        &.active
          color #fff
</style>
```
#### 使用非常简单

```
安装stylus，使用npm安装,stylus和stylus-loader，一个都不能少
npm install stylus stylus-loader --save-dev

使用的话分为两种，一种是直接在vue中的style模块中使用，这时在style模块中规定好就可以了
<style lang="stylus" rel="stylesheet/stylus"></style>
<style>
  @import "content.styl"
</style>
```

