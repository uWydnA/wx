# 全局配置

小程序根目录下的 `app.json` 文件用来对微信小程序进行全局配置。文件内容为一个 JSON 对象，有以下属性：

## 配置项

| 属性                                                         | 类型     | 必填 | 描述                                                         | 最低版本                                                     |
| :----------------------------------------------------------- | :------- | :--- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| [pages](https://developers.weixin.qq.com/miniprogram/dev/reference/configuration/app.html#pages) | string[] | 是   | 页面路径列表                                                 |                                                              |
| [window](https://developers.weixin.qq.com/miniprogram/dev/reference/configuration/app.html#window) | Object   | 否   | 全局的默认窗口表现                                           |                                                              |
| [tabBar](https://developers.weixin.qq.com/miniprogram/dev/reference/configuration/app.html#tabBar) | Object   | 否   | 底部 `tab` 栏的表现                                          |                                                              |
| [networkTimeout](https://developers.weixin.qq.com/miniprogram/dev/reference/configuration/app.html#networkTimeout) | Object   | 否   | 网络超时时间                                                 |                                                              |
| [debug](https://developers.weixin.qq.com/miniprogram/dev/reference/configuration/app.html#debug) | boolean  | 否   | 是否开启 debug 模式，默认关闭                                |                                                              |
| [functionalPages](https://developers.weixin.qq.com/miniprogram/dev/reference/configuration/app.html#functionalPages) | boolean  | 否   | 是否启用插件功能页，默认关闭                                 | [2.1.0](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| [subpackages](https://developers.weixin.qq.com/miniprogram/dev/reference/configuration/app.html#subpackages) | Object[] | 否   | 分包结构配置                                                 | [1.7.3](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| [workers](https://developers.weixin.qq.com/miniprogram/dev/reference/configuration/app.html#workers) | string   | 否   | `Worker` 代码放置的目录                                      | [1.9.90](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| [requiredBackgroundModes](https://developers.weixin.qq.com/miniprogram/dev/reference/configuration/app.html#requiredBackgroundModes) | string[] | 否   | 需要在后台使用的能力，如「音乐播放」                         |                                                              |
| [plugins](https://developers.weixin.qq.com/miniprogram/dev/reference/configuration/app.html#plugins) | Object   | 否   | 使用到的插件                                                 | [1.9.6](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| [preloadRule](https://developers.weixin.qq.com/miniprogram/dev/reference/configuration/app.html#preloadRule) | Object   | 否   | 分包预下载规则                                               | [2.3.0](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| [resizable](https://developers.weixin.qq.com/miniprogram/dev/reference/configuration/app.html#resizable) | boolean  | 否   | iPad 小程序是否支持屏幕旋转，默认关闭                        | [2.3.0](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| [navigateToMiniProgramAppIdList](https://developers.weixin.qq.com/miniprogram/dev/reference/configuration/app.html#navigateToMiniProgramAppIdList) | string[] | 否   | 需要跳转的小程序列表，详见 [wx.navigateToMiniProgram](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/miniprogram-navigate/wx.navigateToMiniProgram.html) | [2.4.0](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| [usingComponents](https://developers.weixin.qq.com/miniprogram/dev/reference/configuration/app.html#usingComponents) | Object   | 否   | 全局[自定义组件](https://developers.weixin.qq.com/miniprogram/dev/reference/configuration/(custom-component/README))配置 | 开发者工具 1.02.1810190                                      |
| [permission](https://developers.weixin.qq.com/miniprogram/dev/reference/configuration/app.html#permission) | Object   | 否   | 小程序接口权限相关设置                                       | 微信客户端 7.0.0                                             |
| [sitemapLocation](https://developers.weixin.qq.com/miniprogram/dev/reference/configuration/app.html#sitemapLocation) | string   | 是   | 指明 sitemap.json 的位置                                     |                                                              |
| [style](https://developers.weixin.qq.com/miniprogram/dev/reference/configuration/app.html#style) | string   | 否   | 指定使用升级后的weui样式                                     | [2.8.0](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| [useExtendedLib](https://developers.weixin.qq.com/miniprogram/dev/reference/configuration/app.html#useextendedlib) | Object   | 否   | 指定需要引用的扩展库                                         | [2.2.1](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |
| [entranceDeclare](https://developers.weixin.qq.com/miniprogram/dev/reference/configuration/app.html#entranceDeclare) | Object   | 否   | 微信消息用小程序打开                                         | 微信客户端7.0.9                                              |

### pages

用于指定小程序由哪些页面组成，每一项都对应一个页面的 路径（含文件名） 信息。文件名不需要写文件后缀，框架会自动去寻找对于位置的 `.json`, `.js`, `.wxml`, `.wxss` 四个文件进行处理。

**数组的第一项代表小程序的初始页面（首页）。小程序中新增/减少页面，都需要对 pages 数组进行修改。**

如开发目录为：

```text
├── app.js
├── app.json
├── app.wxss
├── pages
│   │── index
│   │   ├── index.wxml
│   │   ├── index.js
│   │   ├── index.json
│   │   └── index.wxss
│   └── logs
│       ├── logs.wxml
│       └── logs.js
└── utils
```

则需要在 app.json 中写

```json
{
  "pages": ["pages/index/index", "pages/logs/logs"]
}
```

### window

用于设置小程序的状态栏、导航条、标题、窗口背景色。

| 属性                         | 类型     | 默认值   | 描述                                                         | 最低版本                                                     |
| :--------------------------- | :------- | :------- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| navigationBarBackgroundColor | HexColor | #000000  | 导航栏背景颜色，如 `#000000`                                 |                                                              |
| navigationBarTextStyle       | string   | white    | 导航栏标题颜色，仅支持 `black` / `white`                     |                                                              |
| navigationBarTitleText       | string   |          | 导航栏标题文字内容                                           |                                                              |
| navigationStyle              | string   | default  | 导航栏样式，仅支持以下值： `default` 默认样式 `custom` 自定义导航栏，只保留右上角胶囊按钮。参见注 2。 | 微信客户端 6.6.0                                             |
| backgroundColor              | HexColor | #ffffff  | 窗口的背景色                                                 |                                                              |
| backgroundTextStyle          | string   | dark     | 下拉 loading 的样式，仅支持 `dark` / `light`                 |                                                              |
| backgroundColorTop           | string   | #ffffff  | 顶部窗口的背景色，仅 iOS 支持                                | 微信客户端 6.5.16                                            |
| backgroundColorBottom        | string   | #ffffff  | 底部窗口的背景色，仅 iOS 支持                                | 微信客户端 6.5.16                                            |
| enablePullDownRefresh        | boolean  | false    | 是否开启全局的下拉刷新。 详见 [Page.onPullDownRefresh](https://developers.weixin.qq.com/miniprogram/dev/reference/api/Page.html#onpulldownrefresh) |                                                              |
| onReachBottomDistance        | number   | 50       | 页面上拉触底事件触发时距页面底部距离，单位为 px。 详见 [Page.onReachBottom](https://developers.weixin.qq.com/miniprogram/dev/reference/api/Page.html#onreachbottom) |                                                              |
| pageOrientation              | string   | portrait | 屏幕旋转设置，支持 `auto` / `portrait` / `landscape` 详见 [响应显示区域变化](https://developers.weixin.qq.com/miniprogram/dev/framework/view/resizable.html) | [2.4.0](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) (auto) / [2.5.0](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) (landscape) |

- 注 1：HexColor（十六进制颜色值），如"#ff00ff"

- 注 2：关于

  ```
  navigationStyle
  ```

  - 客户端 7.0.0 以下版本，`navigationStyle` 只在 `app.json` 中生效。
  - 客户端 6.7.2 版本开始，`navigationStyle: custom` 对 [web-view](https://developers.weixin.qq.com/miniprogram/dev/component/web-view.html) 组件无效
  - 开启 custom 后，低版本客户端需要做好兼容。开发者工具基础库版本切到 1.7.0（不代表最低版本，只供调试用）可方便切到旧视觉

如：

```json
{
  "window": {
    "navigationBarBackgroundColor": "#ffffff",
    "navigationBarTextStyle": "black",
    "navigationBarTitleText": "微信接口功能演示",
    "backgroundColor": "#eeeeee",
    "backgroundTextStyle": "light"
  }
}
```

![img](https://res.wx.qq.com/wxdoc/dist/assets/img/config.344358b1.jpg)

### tabBar

如果小程序是一个多 tab 应用（客户端窗口的底部或顶部有 tab 栏可以切换页面），可以通过 tabBar 配置项指定 tab 栏的表现，以及 tab 切换时显示的对应页面。

| 属性            | 类型     | 必填 | 默认值 | 描述                                                         | 最低版本                                                     |
| :-------------- | :------- | :--- | :----- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| color           | HexColor | 是   |        | tab 上的文字默认颜色，仅支持十六进制颜色                     |                                                              |
| selectedColor   | HexColor | 是   |        | tab 上的文字选中时的颜色，仅支持十六进制颜色                 |                                                              |
| backgroundColor | HexColor | 是   |        | tab 的背景色，仅支持十六进制颜色                             |                                                              |
| borderStyle     | string   | 否   | black  | tabbar 上边框的颜色， 仅支持 `black` / `white`               |                                                              |
| list            | Array    | 是   |        | tab 的列表，详见 `list` 属性说明，最少 2 个、最多 5 个 tab   |                                                              |
| position        | string   | 否   | bottom | tabBar 的位置，仅支持 `bottom` / `top`                       |                                                              |
| custom          | boolean  | 否   | false  | 自定义 tabBar，见[详情](https://developers.weixin.qq.com/miniprogram/dev/framework/ability/custom-tabbar.html) | [2.5.0](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html) |

其中 list 接受一个数组，**只能配置最少 2 个、最多 5 个 tab**。tab 按数组的顺序排序，每个项都是一个对象，其属性值如下：

| 属性             | 类型   | 必填 | 说明                                                         |
| :--------------- | :----- | :--- | :----------------------------------------------------------- |
| pagePath         | string | 是   | 页面路径，必须在 pages 中先定义                              |
| text             | string | 是   | tab 上按钮文字                                               |
| iconPath         | string | 否   | 图片路径，icon 大小限制为 40kb，建议尺寸为 81px * 81px，不支持网络图片。 **当 `position` 为 `top` 时，不显示 icon。** |
| selectedIconPath | string | 否   | 选中时的图片路径，icon 大小限制为 40kb，建议尺寸为 81px * 81px，不支持网络图片。 **当 `position` 为 `top` 时，不显示 icon。** |

![img](https://res.wx.qq.com/wxdoc/dist/assets/img/tabbar.ce1b3c5b.png)

### networkTimeout

各类网络请求的超时时间，单位均为毫秒。

| 属性          | 类型   | 必填 | 默认值 | 说明                                                         |
| :------------ | :----- | :--- | :----- | :----------------------------------------------------------- |
| request       | number | 否   | 60000  | [wx.request](https://developers.weixin.qq.com/miniprogram/dev/api/network/request/wx.request.html) 的超时时间，单位：毫秒。 |
| connectSocket | number | 否   | 60000  | [wx.connectSocket](https://developers.weixin.qq.com/miniprogram/dev/api/network/websocket/wx.connectSocket.html) 的超时时间，单位：毫秒。 |
| uploadFile    | number | 否   | 60000  | [wx.uploadFile](https://developers.weixin.qq.com/miniprogram/dev/api/network/upload/wx.uploadFile.html) 的超时时间，单位：毫秒。 |
| downloadFile  | number | 否   | 60000  | [wx.downloadFile](https://developers.weixin.qq.com/miniprogram/dev/api/network/download/wx.downloadFile.html) 的超时时间，单位：毫秒。 |

### debug

可以在开发者工具中开启 `debug` 模式，在开发者工具的控制台面板，调试信息以 `info` 的形式给出，其信息有 Page 的注册，页面路由，数据更新，事件触发等。可以帮助开发者快速定位一些常见的问题。

### functionalPages

> 基础库 2.1.0 开始支持，低版本需做[兼容处理](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html)。

插件所有者小程序需要设置这一项来启用[插件功能页](https://developers.weixin.qq.com/miniprogram/dev/framework/plugin/functional-pages.html)。

### subpackages

> 微信客户端 6.6.0 ，基础库 1.7.3 及以上版本支持

启用[分包加载](https://developers.weixin.qq.com/miniprogram/dev/framework/subpackages.html)时，声明项目分包结构。

> 写成 subPackages 也支持。

### workers

> 基础库 1.9.90 开始支持，低版本需做[兼容处理](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html)。

使用 [Worker](https://developers.weixin.qq.com/miniprogram/dev/framework/workers.html) 处理多线程任务时，设置 `Worker` 代码放置的目录

### requiredBackgroundModes

> 微信客户端 6.7.2 及以上版本支持

申明需要后台运行的能力，类型为数组。目前支持以下项目：

- `audio`: 后台音乐播放
- `location`: 后台定位

如：

```json
{
  "pages": ["pages/index/index"],
  "requiredBackgroundModes": ["audio", "location"]
}
```

注：在此处申明了后台运行的接口，开发版和体验版上可以直接生效，正式版还需通过审核。

### plugins

> 基础库 1.9.6 开始支持，低版本需做[兼容处理](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html)。

声明小程序需要使用的[插件](https://developers.weixin.qq.com/miniprogram/dev/framework/plugin/using.html)。

### preloadRule

> 基础库 2.3.0 开始支持，低版本需做[兼容处理](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html)。

声明[分包预下载](https://developers.weixin.qq.com/miniprogram/dev/framework/subpackages/preload.html)的规则。

### resizable

> 基础库 2.3.0 开始支持，低版本需做[兼容处理](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html)。

在 iPad 上运行的小程序可以设置支持[屏幕旋转](https://developers.weixin.qq.com/miniprogram/dev/framework/view/resizable.html)。

### navigateToMiniProgramAppIdList

> 基础库 2.4.0 开始支持，低版本需做[兼容处理](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html)。

当小程序需要使用 [wx.navigateToMiniProgram](https://developers.weixin.qq.com/miniprogram/dev/api/open-api/miniprogram-navigate/wx.navigateToMiniProgram.html) 接口跳转到其他小程序时，需要先在配置文件中声明需要跳转的小程序 appId 列表，最多允许填写 10 个。

### usingComponents

> 开发者工具 1.02.1810190 及以上版本支持

在此处声明的自定义组件视为全局自定义组件，在小程序内的页面或自定义组件中可以直接使用而无需再声明。

### permission

> 微信客户端 7.0.0 及以上版本支持

小程序[接口权限](https://developers.weixin.qq.com/miniprogram/dev/framework/open-ability/authorize.html)相关设置。字段类型为 `Object`，结构为：

| 属性               | 类型             | 必填 | 默认值 | 描述             |
| :----------------- | :--------------- | :--- | :----- | :--------------- |
| scope.userLocation | PermissionObject | 否   |        | 位置相关权限声明 |

**PermissionObject 结构**

| 属性 | 类型   | 必填 | 默认值 | 说明                                               |
| :--- | :----- | :--- | :----- | :------------------------------------------------- |
| desc | string | 是   |        | 小程序获取权限时展示的接口用途说明。最长 30 个字符 |

如：

```json
{
  "pages": ["pages/index/index"],
  "permission": {
    "scope.userLocation": {
      "desc": "你的位置信息将用于小程序位置接口的效果展示" // 高速公路行驶持续后台定位
    }
  }
}
```

![img](https://res.wx.qq.com/wxdoc/dist/assets/img/permission-desc.496b775d.jpeg)

### sitemapLocation

指明 [sitemap.json](https://developers.weixin.qq.com/miniprogram/dev/reference/configuration/sitemap.html) 的位置；默认为 'sitemap.json' 即在 app.json 同级目录下名字的 `sitemap.json` 文件

## 配置示例

```json
{
  "pages": ["pages/index/index", "pages/logs/index"],
  "window": {
    "navigationBarTitleText": "Demo"
  },
  "tabBar": {
    "list": [
      {
        "pagePath": "pages/index/index",
        "text": "首页"
      },
      {
        "pagePath": "pages/logs/logs",
        "text": "日志"
      }
    ]
  },
  "networkTimeout": {
    "request": 10000,
    "downloadFile": 10000
  },
  "debug": true,
  "navigateToMiniProgramAppIdList": ["wxe5f52902cf4de896"]
}
```

### style

> 基础库 2.8.0 开始支持，低版本需做[兼容处理](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html)。

微信客户端 7.0 开始，UI 界面进行了大改版。小程序也进行了基础组件的样式升级。app.json 中配置 `"style": "v2"`可表明启用新版的组件样式。

本次改动涉及的组件有 `button icon radio checkbox switch slider`。可前往小程序示例进行体验。

### useExtendedLib

> 基础库 2.2.1 开始支持，低版本需做[兼容处理](https://developers.weixin.qq.com/miniprogram/dev/framework/compatibility.html)。

> 最新的 nightly 版开发者工具开始支持，同时基础库从支持 npm 的版本（2.2.1）起支持

指定需要引用的扩展库。目前支持以下项目：

- `kbone`: [多端开发框架](https://developers.weixin.qq.com/miniprogram/dev/extended/kbone/)
- `weui`: [WeUI 组件库](https://developers.weixin.qq.com/miniprogram/dev/extended/weui/)

指定后，相当于引入了对应扩展库相关的最新版本的 npm 包，同时也不占用小程序的包体积。目前暂不支持在分包中引用。用法如下：

```json
{
  "useExtendedLib": {
    "kbone": true,
    "weui": true
  }
}
```

### entranceDeclare

> 微信客户端 7.0.9 及以上版本支持，iOS 暂不支持

聊天位置消息用打车类小程序打开，[详情参考](https://developers.weixin.qq.com/miniprogram/dev/framework/open-ability/location-message.html)。

```json
"entranceDeclare": {
    "locationMessage": {
        "path": "pages/index/index",
        "query": "foo=bar"
    }
}
```