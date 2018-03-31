# 学习笔记

## app.json配置文件
app.json进行对整个项目的配置,
其中:
- pages是所有页面的路径配置(写在第一个的就是项目的入口文件)(路径+文件名,但是不需要写后缀,因为小程序会自动找.json.wxml.wxss.js四个文件)
```js
"pages":[
    "pages/index/index",
    "pages/logs/index"
]
```
- window字段是用于设置小程序的状态栏,导航栏.标题.窗口背景色
  + navigationBarBackgroundColor: 导航栏背景颜色(色值)
  + navigationBarTextStyle: 导航栏标题颜色(仅i支持white/black)
  + navigationBarTitleText: 导航栏标题文字内容
  + navigationStyle: 导航栏样式
  + backgroundColor: 窗口背景颜色
  + backgroundTextStyle: 下拉loading样式(仅支持dray/light)
  + backgroundColorTop: 顶部窗口颜色值(仅ios支持)
  + backgroundColorBottom: 底部窗口颜色i值(仅ios支持)
  + enablePullDownRefresh: 是否开启下拉刷新
  + onReachBottomDistance: 页面上拉触底事件触发时据页面底边距离(单位px)
```js
"window": {
    "navigationBarBackgroundColor": "#000000",
    "navigationBarTextStyle": "white",
    "navigationBarTitleText": "Demo",
    "navigationStyle": "default",
    "backgroundColor": "#ffffff",
    "backgroundTextStyle": "dark",
    "backgroundColorTop": "#ffffff",
    "backgroundColorBottom": "#ffffff",
    "enablePullDownRefresh": "false",
    "onReachBottomDistance": "50"
  }
```
- tabBar字段配置tab栏列表(包括名字和页面路径)
 + color: tab上的文字颜色
 + selectedColor: tab上的文字选中时的颜色
 + backgroundColor: tab 的背景颜色
 + borderStyle: tabbar上边框的颜色(仅支持black/white)
 + list: tab的列表(最少2个,最多5个)
    - pagePath: 页面路径
    - text: tab上文字
    - iconPath: 图片路径(icon限制40kb,建议81px*81px,当position为top,此参数无效,不支持网络图片)
    - selectedIconPath: 选中图片路径(同上)
 + position: tab的位置(可选top/botoom)
```js
"tabBar": {
    "color": "#123456",
    "selectedColor": "#654321",
    "backgroundColor": "#ffffff",
    "borderStyle": "black",
    "position": "bottom",
    "list": [{
      "pagePath": "pages/index/index",
      "text": "首页",
      "iconPath": "../../sladfjl/jaldksjf.jpg",
      "selectedIconPath": "../../sdajfkl/sdkfjlasdjlk.jpg"
    }, {
      "pagePath": "pages/logs/logs",
      "text": "日志",
      "iconPath": "../../sladfjl/jaldksjf.jpg",
      "selectedIconPath": "../../sdajfkl/sdkfjlasdjlk.jpg"
    }]
  },
```
- networkTime字段设置网络超时时间(单位毫秒,均默认6000ms)
    + request: wx.request的超时i时间
    + connectSocket: wx.connectSocket的超时时间
    + uploadFile: wx.uploadFile的超时时间
    + downloadFile: wx.downloadFile的超时时间
- debug字段配置是否开启debug模式
    + 可以在开发者工具中开启debug模式,其信息有: Page的注册 / 页面路由 / 数据更新 / 事件触发

## 页面加载顺序
每一个页面包含4个页面(.json/.wxml/.wxss/.js);
加载顺序: 
现根据.json文件生成一个页面,配置顶部颜色和文字,
然后加载.wxml结构和.wxss样式
最后加载.js文件

## 构造器

项目构造器:
整个小程序只有有个App实例,是所有页面共享的
```js
App({
    onLoad: funciton (){
        // 小程序启动之后执行函数(钩子函数)
    }
})

```

页面构造器:
```js
Page({
    data: {// 参与页面渲染的数据
        logs:[].
    },

    onLoad: function (){
        // 页面加载完成执行(钩子函数)
    }
})

```

