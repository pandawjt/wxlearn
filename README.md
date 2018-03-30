# 学习笔记

## app.json配置文件
app.json中有两个字段pages,windows
其中pages是所有页面的路径配置(写在第一个的就是项目的入口文件)
windows字段是项目风格颜色配置

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