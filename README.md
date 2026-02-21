# Afilmory

现代化高性能照片画廊，基于 React + TypeScript + Cloudflare Pages 构建。

## 特性

- 🖼️ 高性能 WebGL 图片查看器
- 📱 响应式瀑布流布局
- 📷 完整 EXIF 信息展示
- 🗺️ GPS 坐标地图展示
- 🌐 多语言支持
- ⚡ 增量同步，只处理新照片

## 快速部署到 Cloudflare Pages

### 1. Fork 项目

点击右上角 Fork 到你的 GitHub 仓库

### 2. 配置

创建 `configs/你的客户名.json`：

```json
{
  "name": "Gallery Name",
  "title": "My Photo Gallery",
  "description": "Capturing beautiful moments",
  "url": "https://your-project.pages.dev/",
  "accentColor": "#fb7185",
  "author": {
    "name": "Your Name",
    "url": "https://example.com",
    "avatar": "https://example.com/avatar.jpg"
  },
  "social": {
    "github": "username"
  },
  "map": ["maplibre"],
  "mapStyle": "builtin",
  "mapProjection": "mercator"
}
```

### 3. Cloudflare Pages 配置

| 配置项 | 值 |
|--------|-----|
| 生产分支 | `main` |
| 构建命令 | `cp configs/你的客户名.json config.json && pnpm install && pnpm --filter web build` |
| 输出目录 | `apps/web/dist` |

### 4. 环境变量

在 Cloudflare Pages 设置以下变量：

| 变量名 | 说明 |
|--------|------|
| `S3_ENDPOINT` | S3 端点 |
| `S3_ACCESS_KEY_ID` | Access Key |
| `S3_SECRET_ACCESS_KEY` | Secret Key |
| `S3_BUCKET` | 存储桶名称 |
| `S3_REGION` | 区域 |
| `S3_PREFIX` | 照片路径前缀 |

## 本地开发

```bash
# 安装依赖
pnpm install

# 复制配置
cp config.example.json config.json

# 修改 config.json 和 builder.config.ts

# 开发模式
pnpm --filter web dev
```

## 多客户部署

同一仓库支持多个客户：

```
configs/
├── muti.json    # muti 客户
├── iu.json      # IU 客户
└── xxx.json     # 新客户
```

每个客户创建独立的 Cloudflare Pages 项目，构建命令指定对应的配置文件即可。

## License

MIT
