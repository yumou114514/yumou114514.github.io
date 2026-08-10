# Yumou-Pages 个人网站

[返回 README 首页](../README.md)

> **重要通知**：该仓库已迁移至 [Codeberg](https://codeberg.org/yumou/yumou114514.github.io) 为主仓库，GitHub 仓库通过工作流自动同步。

## 简介

这是一个基于 GitHub Pages 构建的个人网站，包含以下功能：

- **首页导航** - 所有功能模块的统一入口
- **项目展示** - 个人项目概览
- **CB应用商店** - 应用浏览、搜索、按字母导航与下载
- **照片画廊** - 图片展示与下载
- **文章系统** - 技术文档管理
- **AI聊天** - 基于 DeepSeek API 的对话功能
- **ACG** - 随机动漫图片

## 技术特点

- 纯静态站点，无需后端服务
- 统一样式系统 (`res/style.css`)，支持亮色/暗色模式自动切换
- JSON 数据驱动的应用商店，支持搜索与字母导航
- 响应式设计，适配移动端与桌面端

## 模块说明

| 模块 | 路径 | 说明 |
|------|------|------|
| 首页 | `/index.html` | 功能导航入口 |
| 项目 | `/project/` | 项目展示页 |
| 应用商店 | `/app/` | CB应用商店主页 |
| 应用详情 | `/app/app.html` | 单个应用信息与下载 |
| 照片 | `/photo/` | 照片画廊 |
| 文章 | `/article/` | 文章/文档列表 |
| AI聊天 | `/ai.html` | DeepSeek AI 对话界面 |
| ACG | `/acg.html` | 随机动漫图片 |

## 应用商店数据结构

应用商店使用 JSON 文件存储数据：

- `app/ProjectList/a-z.json` - 按字母索引的应用列表（内嵌完整应用信息）
- `app/<应用名>/info.json` - 应用详细信息

`info.json` 字段说明：

```json
{
  "name": "应用名称",
  "description": "应用描述",
  "version": "版本号",
  "author": "作者",
  "platforms": ["平台列表"],
  "websites": {
    "author": "作者网站",
    "project": "项目网站"
  },
  "downloads": {
    "平台名": "下载链接"
  }
}
```

## 仓库地址

- [Codeberg (主仓库)](https://codeberg.org/yumou/yumou114514.github.io)
- [GitHub (镜像)](https://github.com/yumou114514/yumou114514.github.io)
