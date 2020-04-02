## 微信js-sdk接入指南

## 微信官方文档阅读

首先，我们要接入微信jssdk，那么第一步就是要阅读微信开发文档：https://mp.weixin.qq.com/wiki?t=resource/res_main&id=mp1445241432

打开这个网页，在左边的菜单栏，依次点击：**微信网页开发 - 微信JS-SDK说明文档**。

## 微信JSSDK使用步骤

### 绑定域名

先登录微信公众平台进入“公众号设置”的“功能设置”里填写“JS接口安全域名”。

备注：登录后可在“开发者中心”查看对应的接口权限。

### 引入JS文件

在需要调用JS接口的页面引入如下JS文件，（支持https）：http://res.wx.qq.com/open/js/jweixin-1.6.0.js

如需进一步提升服务稳定性，当上述资源不可访问时，可改访问：http://res2.wx.qq.com/open/js/jweixin-1.6.0.js （支持https）。

备注：支持使用 AMD/CMD 标准模块加载方法加载

### 通过config接口注入权限验证配置

这个是前端html页面中需要我们处理的，就是通过wx.config()注入欸之信息，要不然就会无法调用其他接口。

```javascript
wx.config({
    debug: true, // 开启调试模式,调用的所有api的返回值会在客户端alert出来，若要查看传入的参数，可以在pc端打开，参数信息会通过log打出，仅在pc端时才会打印。
    appId: '', // 必填，公众号的唯一标识
    timestamp: , // 必填，生成签名的时间戳
    nonceStr: '', // 必填，生成签名的随机串
    signature: '',// 必填，签名
    jsApiList: [] // 必填，需要使用的JS接口列表
});
```

这些东西，除了jsApiList，我们都需要从后端获取，那我们就向后台发起一个请求，然后后台封装一下返回给前端是不是就好了，很简单吧。

appId简单，直接从微信后台拿来用就行。

timestamp，后台直接生成就行，但要注意要以秒为单位。

nonceStr，java后台随便使用个uuid就可以了。

signature，这个有点东西啊，但也别急，微信有文档，我们慢慢看。