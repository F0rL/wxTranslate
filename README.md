# 支持多国语言翻译的微信小程序
微信搜索：**简简译**

或扫描二维码：

![](https://ws1.sinaimg.cn/large/90864b23gy1fwa0u103p0j2076086t99.jpg)

- 使用百度翻译api
需要申请 appid 与 key 并在 `api.js` 设置

## 功能
1. 多国语言选择
2. 查看个人翻译历史
3. 清除个人记录

## 技术点
### 微信相关组件使用
#### `view` 等同于 `div`
#### `navigator` 等同于 `a`链接，通过`navigator`跳转到小程序的其他页面
#### 引入外链图标库
- 在 `app.wxss` 公共样式当中 `@import "./assets/iconfont/iconfont.wxss";` 引入 `iconfont.wxss`
- 将 `iconfont.wxss` 内容修改为如下代码(iconfont中css链接使用浏览器打开后得到下列代码)，将 `url` 地址改为 `https` 后缀为 `ttf`：
### 文本是否能够复制
使用 `<text selectable="true">{{item.dst}}</text>` 使翻译结果可选择，可复制

### 翻译api使用
#### 微信发起请求使用 `wx.request()`
需要先到微信小程序设置 `request合法域名`

#### 使用百度的接口
百度api地址为：https://fanyi-api.baidu.com/api/trans/vip/translate
需注意，为了保证调用安全，要使用MD5算法生成的一段字符串，生成的签名长度为 32位，签名中的英文字符均为小写格式

### tabBar导航
必须放置在底部`"position": "bottom",`，才能使用 icon 图标。
用`"iconPath"`和`"selectedIconPath"`设置 tabBar 图标和被选中的图标。