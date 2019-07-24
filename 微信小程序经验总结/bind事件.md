#### bind事件
##### 1.bindfocus事件

```
指当我们的输入框获得焦点时触发，也就是鼠标或者手指点击到输入框时
```
##### 2.bindblur事件

```
指输入框失去焦点时触发，也就是当我们敲击回车或手机上的完成又或者是点击屏幕上的空白处时触发
```
##### 3.bindchange事件

```
它的效果和bindblur一样，至于看名字我们可能觉得bindchange在输入框中的内容不改变时不会触发，但是亲自测即使内容不改变，bindchange事件也一样会触发。 
```
##### 4.bindinput事件

```
每输入一个字符都会进行一次检索，通常用于实时检索。但是这种方法对数据库的要求较高
```
##### 
```
在bindblur或bindchange事件中我们通过event.detail.value获得事件
```
##### 5.医生端单次用量 频率 天数 总量  用法

```
bindSinglDose: function(e) {
    console.log('picker发送选择改变，携带值为', e.detail.value)
    this.setData({
      singlDoseIndex: e.detail.value
    })
  },
  bindFreq: function(e) {
    this.setData({
      freqIdx: e.detail.value
    })
    this.arithmetic();
  },
  bindburConsumption(e) {
    this.setData({
      Consumption: e.detail.value
    })
    this.arithmetic();
  },
  bindburDays(e) {
    this.setData({
      days: e.detail.value
    })
    this.arithmetic();
  },
  bindSingleTotal: function(e) {
    this.setData({
      singleTotalIdx: e.detail.value
    })
  },
  bindUsing: function(e) {
    this.setData({
      usingInx: e.detail.value
    })
  },
```
##### 6.小程序把data转换成formData
```
header: {
    "content-type": "application/x-www-form-urlencoded"     //这里的改,一开始Content-Type可以,现在只能使用content-type
  },
```
##### 7.获取屏幕的宽高

```
//获取屏幕宽度
var screenWidth = wx.getSystemInfo({
  success: function (res) {
    screenWidth = res.windowWidth
  }
})
```

```
//获取屏幕的高度
var screenHeight = wx.getSystemInfo({
  success: function (res) {
    screenHeight = res.windowHeight
  }
})
```

```
Page({
  onLoad:function(){
    console.log('屏幕高度:'+screenHeight)
    console.log('屏幕宽度:'+screenWidth)
  }
})
```


