#### input模糊搜索视图层

```
  <view class='c_disgon'>
        <text class='c_disgon_tit'>诊断:  </text>
        <input class='textarea dig' bindinput='currentbox' value='{{Diagnosis}}' bindfocus='Diagnosisfocus' placeholder='请输入诊断...'></input> 

         <view class='c_voiceBtn iconfont i-yuyin1 ' catchtouchstart="streamRecord" catchtouchend="endStreamRecord"></view>
        <scroll-view scroll-y class="c_disgonbox" wx:if="{{disgonbox==true}}">
          <view class='c_disgontext' bindtap='diagbtn' wx:for="{{disgonlist}}" wx:for-item="item" data-diagid="{{item.diagId}}" data-name="{{item.diagName}}">{{item.diagName}}</view>
        </scroll-view>
      </view>
```
#### 效果详细介绍
```
页面效果:  只要是做到点击input文本框，设置其value值；同时请求接口下拉列表页为true的效果
```
#### js当中的data
```
data:{
disgonbox:false,//在data里面先是默认下拉列表为false
}
```
#### 添加诊断事件js
```
 currentbox:function(e){
    this.setData({
      currentText: e.detail.value// 此处是获取自己设置的input的value值
    })
    console.log(e);
    if (e.detail.value==''){//如果没有诊断，则下面的模糊搜索列表则是空的
      this.setData({
        disgonbox:false
      })
    }else{如果有诊断，//请求接口
      wx.request({
        url: `${app.globalData.residentUrl}/doctor/represcribing/selectAllDiagnose`,
        method: 'post',
        data: `{
          "pageNum":"${this.data.pageNum}",
          "pageSize":"${this.data.pageSize}",
          "diagName":"${e.detail.value}" //诊断名称
        }`,
        success: res => {
          console.log(res)
          if (res.data.data.list.length!=0){ //如果请求的数据是存在的话，就把模糊列表设置为真
            this.setData({
              disgonbox: true,
              disgonlist: res.data.data.list //此处的list在视图层有了一个循环wx:for="{{disgonlist}}"
            })
          }else{
            this.setData({
              disgonbox: false
            })
          }
        }
      })
    }
  },
```
#### 绑定模糊列表事件js

```
diagbtn:function(e){
    console.log(e);
    wx.setStorageSync('diagid', e.currentTarget.dataset.diagid)
    this.setData({
      disgonbox:false,
      currentText: e.currentTarget.dataset.name
    })
  },
```
