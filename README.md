# YuMou-Pages

个人网站与项目托管平台。

[English](readme/readme_en.md) | [简体中文](readme/readme_zh-cn.md)

## 仓库

- [Codeberg (主仓库)](https://codeberg.org/yumou/yumou114514.github.io)
- [GitHub (镜像)](https://github.com/yumou114514/yumou114514.github.io)

## 功能模块

| 模块 | 路径 | 说明 |
|------|------|------|
| 首页 | `/` | 功能导航入口 |
| 项目 | `/project/` | 项目展示 |
| CB应用商店 | `/app/` | 应用浏览、搜索与下载 |
| 照片 | `/photo/` | 照片画廊，点击查看/下载 |
| 文章 | `/article/` | 技术文档 |
| AI聊天 | `/ai.html` | DeepSeek AI 对话 |
| ACG | `/acg.html` | 随机动漫图片 |

## 技术栈

- 纯静态站点，无框架依赖
- 统一样式系统 (`res/style.css`)，支持暗色模式
- JSON 驱动的应用商店数据
- GitHub Pages 部署

## 目录结构

```
├── app/                  # CB应用商店
│   ├── ProjectList/      # 应用索引 (a-z.json)
│   ├── Timer/            # Timer 应用
│   └── FJE Web Json Editor/
├── article/              # 文章/文档
├── photo/                # 照片画廊
├── project/              # 项目展示
├── res/                  # 公共资源
│   └── style.css         # 统一样式表
├── readme/               # 多语言 README
├── index.html            # 首页
├── ai.html               # AI聊天
└── acg.html              # ACG随机图片
```

## 许可

[LICENSE](LICENSE)
