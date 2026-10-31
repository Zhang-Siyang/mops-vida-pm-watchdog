# MOPS·VIDA PM Watchdog

The product is **MOPS·VIDA PM 2.5 Watchdog**

Note: The product Chinese name is
<ruby>
忻 <rp>(</rp><rt>Xīn</rt><rp>)</rp>
风 <rp>(</rp><rt>fēng</rt><rp>)</rp>
随身 <rp>(</rp><rt>suíshēn</rt><rp>)</rp>
PM 2.5 <rt></rt>
检测 <rp>(</rp><rt>Jiǎncè</rt><rp>)</rp>
仪 <rp>(</rp><rt>yí</rt><rp>)</rp>
</ruby>

Product model: `AD520-P001`

Official Website: <https://www.lianluo.com>

Press release: <https://family.pconline.com.cn/1040/10406965.html>

Documentation: [docs](docs)

## 本地运行

需要现代 Node.js（GitHub Actions 使用 Node.js 22）和 Python 3：

```sh
npm ci --ignore-scripts --no-audit --no-fund
npm start
```

用 Chrome 或 Edge 打开 <http://127.0.0.1:8765/>。服务只监听本机；localhost
属于安全上下文，可以使用 Web Bluetooth，无需自签名 HTTPS 证书。
保留 Webpack 4，构建命令仅对当前 Node 进程启用 OpenSSL legacy provider。

## 使用检测仪

1. 打开电脑蓝牙，开启检测仪并放在附近；如其他应用占用检测仪，先断开。
2. 点击 **Connect**，在浏览器的蓝牙选择器中选择设备并连接；按系统提示允许蓝牙权限。
3. **Real-time** 显示 PM2.5、电池、记录时间等读数。
4. **Read history (one-time)** 读取历史记录，**Download** 下载已读取的历史数据。
5. 结束时点击 **Disconnect**。**Shutdown** 会关闭检测仪，不是关闭网页。

设备连接需要浏览器支持 Web Bluetooth；桌面 Chrome/Edge 可用，移动端优先使用
Android Chrome。Safari 和 iPhone/iPad 的常规浏览器不适用。
网页连接的是使用者身边的蓝牙设备，不是通过互联网访问家里的检测仪。

## 公开部署

公开仓库：<https://github.com/Zhang-Siyang/mops-vida-pm-watchdog>

公开网页：<https://pm25.syang.dev/>

在仓库 Settings → Pages 中选择 **GitHub Actions**。
推送 `master` 或手动运行 **Publish** 工作流即可构建并发布 `dist`；
项目独立域名为 `pm25.syang.dev`，Cloudflare 使用 DNS-only CNAME 指向
`zhang-siyang.github.io`，GitHub Pages 为该域名签发证书并启用 Enforce HTTPS。
此绑定仅属于当前项目，不改变个人博客或其他站点。Web Bluetooth 不能在普通公网
HTTP 页面工作。

本分支移除了原作者的 Google Analytics。检测仪读数由浏览器通过蓝牙读取，
应用没有向服务器上传读数的逻辑；GitHub Pages 只托管静态文件。
历史数据仅保存在当前页面内存中，刷新或关闭前请先下载。

原项目及 MIT 许可证保留。原在线地址
<https://nicelabs.github.io/mops-vida-pm-watchdog> 已失效。
