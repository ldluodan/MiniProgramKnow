##### 解决苹果手机按钮的圆角问题

```
在使用html5编写移动页面时，总会涉及有关按钮的一些问题，在android手机浏览器中显示正常，但在ios浏览器中按钮会显示为圆角，设置border-radius:0px;也不管用，其实在css中添加  “-webkit-appearance”就能解决问题。
```

```
 .btn{
 height: 300px;
 width: 300px;
line-height: 300px;
 border: 0;
 font-size: 55px;
 color: #fff;
 background: #EA15A0;
 border-radius: 50px;
 -webkit-appearance : none ;  /*解决iphone safari上的圆角问题*/
}
html：
<input type ="button" class ="btn" value="按钮" />
```

```
总结：

     使用css样式 -webkit-appearance: none;  轻松解决iphone上按钮的圆角问题。
```
![image](https://note.youdao.com/yws/res/1497/DD844639030A40649F388AF1250D4CFB)

##### 解决苹果手机textarea的margin和padding问题
![image](https://note.youdao.com/yws/res/1503/FD225BC9EBF04733A46C5FA158AD0D01)
下面写实现过程：

![image](https://note.youdao.com/yws/res/1507/CCBEFD325CE1408494452CC7B1277BF0)

```
wxml文件：
<view class='xingdongDescript'>
  <view class='xingdongNameBox'>
    <view>行动名称</view>
    <input placeholder='请输入' />
  </view>
  <view class='xingdongjieshaoBox'>
    <view class='xingdongjieshao'>行动介绍</view>
    <view class="{{detail ? 'iostextarea'  : 'androidtextarea'}}">
      <textarea placeholder='请输入' />
    </view>
  </view>
</view>
```

```
.iostextarea textarea{
    position: absolute;
    width: 100%;
    height: 100%;
    font-size: 34rpx;
 }
.androidtextarea textarea{
    width: 100%;
    height: 197rpx;
    float: left;
    padding: 22rpx 0 0 0;
    box-sizing: border-box;
    font-size: 34rpx;
 }
```
##### 函数调用的时候，前面加上new关键字所谓构造函数，就是通过这个函数生成一个新对象，这时，this就指向这个对象。

```
function demo(){
    this.testStr='this is a test'
}
let a= new demo();
alert(a.testStr); // 'this is a test'
```
