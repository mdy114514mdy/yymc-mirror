# YYMC 网页版 · 静态镜像

Minecraft Java 26.2 内容的网页版（OpusMC，作者 B 站 UP「土豆味小哲」）的静态镜像。

打开首页即玩：横屏壳 → 游戏本体（约 60 MB，首次加载慢一点，之后走缓存）。

## 内容

| 路径 | 说明 |
|---|---|
| `index.html` | 横屏壳（竖屏旋转提示、强制横屏、全屏工具条） |
| `game/OpusMC.v2.html` | 游戏本体，62,735,848 B，区块 worker 与音效事件表都内联 |
| `game/sounds/sfx/**/*.m4a` | 原版音效 4849 个（AAC 96k），按游戏事件名铺平 |
| `favicon.svg` / `favicon.ico` | 图标 |

## 与本地完整版的差别

- **没有 v1**（50 MB 那份区块 worker 缺失、会卡），只保留 v2
- **没有 ogg 兜底**：只放 m4a，Safari / Chrome / Edge / Firefox 都能播
- **没有 `/rooms` 反代**：纯静态托管，房间/联机接口（`xz.honghemc.cn:8443`）需要服务端转发并补 `Origin: https://www.bilibili.com`，GitHub Pages 做不到，所以联机功能在线上是 403
- 仍缺 4 个作者自制文件（`emoji.webp`、`jing.webp`、`skins_data.js`、`vstates_data.js`），表现为：彩色 emoji 退回系统字体、鲸鲸伙伴无贴图、预设皮肤空、用存档开房间会报「方块数据加载失败」

## 本地跑

纯静态，任何静态服务器都行：

```bash
python -m http.server 8099
# 或 npx serve .
```

**别用 file:// 双击**：游戏里有 `new Worker(blob:)`，origin 为 null 时 worker 全废。

## 版权

游戏内容版权归原作者「土豆味小哲」；Minecraft 素材归 Mojang / Microsoft。这里只是把公开可访问的页面抓下来做技术存档。
