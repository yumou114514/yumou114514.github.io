# Yumou-Pages Personal Website

[Back to README Home](../README.md)

> **Notice**: This repository has moved to [Codeberg](https://codeberg.org/yumou/yumou114514.github.io) as the primary repository. The GitHub repository is automatically synced via workflows.

## Introduction

A personal website built with GitHub Pages, featuring:

- **Home Navigation** - Central hub for all modules
- **Projects** - Personal project showcase
- **CB App Store** - Browse, search, and download apps with alphabetical navigation
- **Photo Gallery** - Image viewing and downloading
- **Articles** - Technical documentation
- **AI Chat** - DeepSeek API-powered chat interface
- **ACG** - Random anime images

## Technical Highlights

- Pure static site, no backend required
- Unified styling system (`res/style.css`) with automatic light/dark mode
- JSON-driven app store with search and alphabetical navigation
- Responsive design for mobile and desktop

## Module Overview

| Module | Path | Description |
|--------|------|-------------|
| Home | `/index.html` | Navigation entry point |
| Projects | `/project/` | Project showcase |
| App Store | `/app/` | CB App Store main page |
| App Detail | `/app/app.html` | App info and downloads |
| Photos | `/photo/` | Photo gallery |
| Articles | `/article/` | Article/documentation list |
| AI Chat | `/ai.html` | DeepSeek AI chat interface |
| ACG | `/acg.html` | Random anime images |

## App Store Data Structure

The app store uses JSON files for data storage:

- `app/ProjectList/a-z.json` - Alphabetically indexed app list (with full app info inline)
- `app/<app-name>/info.json` - Detailed app information

`info.json` fields:

```json
{
  "name": "App Name",
  "description": "App description",
  "version": "Version number",
  "author": "Author",
  "platforms": ["Platform list"],
  "websites": {
    "author": "Author website",
    "project": "Project website"
  },
  "downloads": {
    "Platform": "Download URL"
  }
}
```

## Repository Links

- [Codeberg (Primary)](https://codeberg.org/yumou/yumou114514.github.io)
- [GitHub (Mirror)](https://github.com/yumou114514/yumou114514.github.io)
