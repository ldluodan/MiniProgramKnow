#### 小程序搜索页（bindfocus，bindblur，bindconfirm）

```
1.小程序一般会在首页的顶部做一个假的搜索样式  = =>  点击该样式跳转到有输入框的页面，在页面输入要搜索的文字，①点击空白处input框失去焦点跳转到搜索结果页②也可以点击键盘上的搜索键，触发跳转到搜索结果③点击取消按钮一般不是清除input框内容停留在本页面而是返回到首页 ==> 到搜索结果页，结果页拿到input框页带过来的关键字请求接口即可
```

```
2.在input框页
<view class='searchBar'>  
  <view class='searchBarInputC flex alignC'>
    <view class='searchBarInput'>
      <input type='text' class='searchBarInput_in' placeholder="搜索您爱吃的美食" value='{{valueKeyword}}' confirm-type='search' focus="{{autoFocus}}"  bindconfirm='resignFocus'   bindfocus="activeFocus" bindblur="resignFocus" ></input>
    </view>
    <view class='searchClose' bindtap='goCancel'>取消</view>
  </view>
</view>

```

```
3.在样式页
.searchBarInputC{
  width: 670rpx;
  margin: 0 auto;
}
.searchBarInput{
  position: relative;
  width: 510rpx;
  height: 70rpx;
  margin: 0 auto;
  -webkit-border-radius: 70rpx;
  -moz-border-radius: 70rpx;
  border-radius: 70rpx;
  background: 43rpx center #f6f6f6 url(data:3fmAAAAAElFTkSuQmCC) no-repeat;
  background-size: 28rpx;
  font-size: 28rpx;
  line-height: 62rpx;
  color: #8a8a8a;
  padding: 0 30rpx 0 80rpx;
  box-sizing: border-box;
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
}
.searchBarInput_in{
  background-color: transparent;
  height: 70rpx;
  width: 100%;
}
.searchClose{
  width: 140rpx;
  height: 70rpx;
  background-color: #ff8a00;
  -webkit-border-radius: 70rpx;
  -moz-border-radius: 70rpx;
  border-radius: 70rpx;
  line-height: 70rpx;
  text-align: center;
  color: #fff;
  font-size: 30rpx;
 
}
.flex {
  display: -webkit-box;
  display: -moz-box;
  display: -ms-flexbox;
  display: -webkit-flex;
  display: flex;
  display: box;
  flex-wrap: wrap;
}
.flexC {
  -webkit-box-pack: center;
  justify-content: center;
  -webkit-justify-content: center;
  -moz-justify-content: center;
  -ms-justify-content: center;
  -o-justify-content: center;
}

```

```
3.在事件层
var that;
Page({
  /**
   * 页面的初始数据
   */
  data: {
    autoFocus: true,
    valueKeyword: ''
  },
  /**
   * 生命周期函数--监听页面加载
   */
  onLoad: function(options) {
    that = this;
  },
  //获取焦点
  activeFocus: function(event) {
    that.setData({
      autoFocus: true
    });
  },
  //失去焦点
  resignFocus: function(event) {
    //焦点开关
    that.setData({
      autoFocus: false
    });
    console.log('222' + event.detail.value);
    // 进行搜索
    wx.redirectTo({
      url: '../searchjg/searchjg?valueKeyword=' + event.detail.value
    });
  },
  //取消，返回上一页
  goCancel: function() {
    wx: wx.navigateBack({
      delta: 1,
    });
  },
})

```

