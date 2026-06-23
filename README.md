# 🕐 屏幕保护时钟 (NowScreen)

一个**准单文件**（HTML + sw.js）的全屏时钟 PWA，支持 10 种预设主题、屏幕保护模式和丰富的个性化设置。在浏览器中直接打开即可使用，可安装为独立 App。

## ✨ 功能

### ⏰ 时钟显示
- 全屏时钟，占视口约 80%，每秒刷新
- 支持 **12/24 小时制**切换
- 14 个常见时区可选（Asia/Shanghai、America/New_York 等）

### 🎨 10 种预设主题
| 主题 | 背景 | 文字 | 字体 |
|------|------|------|------|
| 🌙 暗夜模式 | `#000` | `#fff` | system-ui |
| ☀️ 极简白 | `#f0f0f0` | `#1a1a1a` | sans-serif |
| 🔶 复古琥珀 | `#0d0d05` | `#ffb000` | monospace |
| 🌲 森林绿 | `#0a1f0a` | `#7ec87e` | serif |
| 🌊 海洋蓝 | `#0a1628` | `#5b9bd5` | system-ui |
| 💜 霓虹紫 | `#0f0014` | `#e040ff` | monospace |
| 🍊 日落橙 | `#1a0d05` | `#ff8c42` | sans-serif |
| 🌿 薄荷绿 | `#ebf5ee` | `#2d6a4f` | system-ui |
| 🌹 玫瑰粉 | `#1a0a14` | `#ff6b9d` | serif |
| 🌌 极光 | `#050a14` | `#00e5a0` | monospace |

点击即可一键切换主题，手动调整后自动标记为「自定义」。

### ⚙️ 个性化设置
- 字体大小滑块（4vw - 30vw）
- 背景颜色选择器
- 文字颜色选择器
- 字体选择（system-ui / monospace / serif / sans-serif）
- 时区下拉选择
- 12/24 小时制切换开关

### 🖥️ 屏幕保护模式
- 启用后时钟在屏幕上缓慢移动并边界反弹
- 点击页面暂停移动、呼出设置，5 秒后恢复
- 关闭后平滑回到屏幕中央

### 📱 PWA 支持
- 可安装为独立桌面/移动 App（`display: fullscreen`）
- Service Worker 离线缓存，断网也能打开
- 动态 `theme-color`，状态栏跟随背景色
- 首次点击自动请求全屏，隐藏系统导航栏
- Apple iOS Safari "添加到主屏幕" 适配

### 💾 数据持久化
- 所有设置自动保存到 `localStorage`
- 刷新页面或重新打开后完全恢复

## 🚀 使用

### 浏览器直接打开
下载 `index.html` 和 `sw.js`，双击 `index.html` 即可。

### Caddy 部署
```bash
# 上传文件到服务器
scp index.html sw.js user@server:/var/www/nowscreen/

# Caddyfile
nowscreen.yourdomain.com {
  root * /var/www/nowscreen
  file_server
  encode gzip
}
```

### Docker + Caddy
```yaml
services:
  caddy:
    volumes:
      - /path/to/nowscreen:/var/www/nowscreen
```

## 📁 文件结构

```
nowscreen/
├── index.html    # 主页面（内联 manifest）
├── sw.js         # Service Worker（离线缓存）
├── Caddyfile     # Caddy 配置示例
└── README.md
```

## 🛠 技术栈

- 纯原生 HTML + CSS + JavaScript，零外部依赖
- `localStorage` 持久化设置
- `Intl.DateTimeFormat` 时区转换
- `requestAnimationFrame` 屏幕保护动画
- Service Worker API 离线支持
- Web App Manifest（blob URL 内联）

## 📄 License

MIT
