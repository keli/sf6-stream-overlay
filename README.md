# SF6 Stream Overlay

Street Fighter 6 风格的 bilibili 直播 OBS 侧边栏面板，配合 [blivechat](https://github.com/xfgryujk/blivechat) 使用。

适用于宽屏显示器两侧空白区域，按 240×1080 设计。

## 面板说明

- **sf6-danmaku.html** — 弹幕面板，作为 blivechat 自定义模板加载，接收并渲染弹幕/礼物/醒目留言
- **sf6-panel.html** — 信息面板，独立页面，显示摄像头框、公告、节目单、跑马灯

## 部署

部署到 Cloudflare Pages（或任意静态托管），连接本仓库即可，无需构建步骤。

## OBS 配置

| 源 | 类型 | X | Y | 宽 | 高 |
|---|---|---|---|---|---|
| 摄像头 | 视频采集设备 | 0 | 0 | 240 | 180 |
| 信息面板 | 浏览器源 | 0 | 0 | 240 | 1080 |
| 弹幕面板 | 浏览器源 | 1680 | 0 | 240 | 1080 |

摄像头层叠在信息面板上方，盖住顶部预留的摄像头区域。

弹幕面板的浏览器源 URL 填 blivechat 房间地址（见下方配置方法）。

## blivechat 配置

### 在线使用（推荐）

1. 打开 [blive.chat](https://blive.chat) 或自建 blivechat
2. 输入身份码，进入房间配置
3. 「自定义模板 URL」填入：`https://你的域名/sf6-danmaku.html`
4. 复制房间 URL，在 OBS 浏览器源中使用

### 本地使用

将 `template.json` 放入 blivechat 的 `data/custom_public/templates/sf6/` 目录，同时将 `sf6-danmaku.html` 和 `blcsdk.js` 放入同一目录，模板会出现在模板列表中。

## 更新内容

编辑 `content.json`，信息面板每 30 秒自动刷新：

```json
{
  "announcement": "公告文字",
  "schedule": [
    { "time": "19:00", "title": "节目名称" }
  ],
  "ticker": "跑马灯文字"
}
```
