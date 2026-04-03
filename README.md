# Diary Polisher Pro - 英文日记精修助手

> 使用 AI 将你的英文日记从草稿升级为专业写作，同时学习 CEFR 高级表达

![Version](https://img.shields.io/badge/version-1.0.0-blue)
![License](https://img.shields.io/badge/license-MIT-green)
![Platform](https://img.shields.io/badge/platform-Web%20App-9cf)

---

## 目录

- [功能特点](#功能特点)
- [技术栈](#技术栈)
- [快速开始](#快速开始)
- [配置说明](#配置说明)
- [部署指南](#部署指南)
- [项目结构](#项目结构)
- [常见问题](#常见问题)
- [学习资源](#学习资源)

---

## 功能特点

### 核心功能

| 功能 | 说明 |
|------|------|
| **AI 精修** | 将英文日记升级到 B1/B2/C1 等级 |
| **亮点解析** | 自动标记固定搭配、精彩句型、核心词组 |
| **导师评语** | 提供详细的中文写作反馈 |
| **日历打卡** | 可视化追踪学习进度 |
| **PDF 导出** | 一键生成精美的学习报告 |

### CEFR 等级说明

| 等级 | 难度 | 适用人群 |
|------|------|----------|
| B1 | Intermediate | 初中级英语学习者 |
| B2 | Upper-Intermediate | 中高级学习者 |
| C1 | Advanced | 高级英语学习者 |

---

## 技术栈

本项目使用纯前端技术，无需后端服务器：

- **React 18** - 用户界面框架
- **Tailwind CSS** - 样式设计（通过 CDN 引入）
- **Lucide Icons** - 图标库
- **Google Gemini API** - AI 精修服务
- **LocalStorage** - 本地数据存储

### 为什么选择纯前端架构？

- **零服务器成本** - 可免费部署到静态托管平台
- **简单易维护** - 只有一个 HTML 文件
- **运行速度快** - 无需网络请求到后端
- **隐私安全** - 数据存储在用户本地浏览器

---

## 快速开始

### 方法一：直接打开（仅用于测试）

1. 下载 `index.html` 文件
2. 双击在浏览器中打开

> 注意：直接打开无法保存 API Key 配置，适合快速体验。

### 方法二：本地开发服务器

```bash
# 使用 Python（macOS 自带）
cd diary-polisher
python3 -m http.server 8080

# 或使用 Node.js
npx serve .
```

然后访问 http://localhost:8080

---

## 配置说明

### 获取 Google Gemini API Key

1. 访问 [Google AI Studio](https://aistudio.google.com/app/apikey)
2. 登录 Google 账号
3. 点击 "Create API Key"
4. 复制生成的密钥

### 配置 API Key

**⚠️ 重要安全提示：不要将 API Key 直接写在代码中！**

对于正式部署，推荐使用环境变量：

```bash
# 创建 .env 文件（不要提交到 Git！）
VITE_GEMINI_API_KEY=你的API密钥
```

或者使用 URL 参数方式：
```
https://your-app.netlify.app/?api_key=你的API密钥
```

---

## 部署指南

### 方案一：Netlify（推荐）- 5分钟完成

1. **访问 [Netlify](https://www.netlify.com)，注册/登录账号**

2. **创建新站点**
   - 点击 "Add new site" → "Deploy manually"
   - 将 `index.html` 拖入上传区域

3. **配置环境变量（如需）**
   - 进入 Site Settings → Environment Variables
   - 添加 `VITE_GEMINI_API_KEY = 你的密钥`

4. **自定义域名（可选）**
   - Domain Management → Add custom domain

### 方案二：Vercel

1. **访问 [Vercel](https://vercel.com)，使用 GitHub 登录**

2. **创建项目**
   - New Project → Import GitHub Repository
   - 或直接上传文件夹

3. **配置环境变量**
   - Environment Variables 添加 `VITE_GEMINI_API_KEY`

### 方案三：GitHub Pages（免费）

1. **创建 GitHub 仓库**
   ```bash
   cd diary-polisher
   git init
   git add index.html
   git commit -m "Initial commit"
   ```

2. **推送到 GitHub**
   ```bash
   git remote add origin https://github.com/你的用户名/diary-polisher.git
   git push -u origin main
   ```

3. **启用 GitHub Pages**
   - 仓库 Settings → Pages → Source: main branch

### 部署检查清单

- [ ] API Key 已正确配置
- [ ] 网站可以正常访问
- [ ] 功能测试通过（输入日记 → 提交 → 查看结果）
- [ ] PDF 导出功能正常

---

## 项目结构

```
diary-polisher/
├── index.html      # 主应用文件（包含所有代码）
├── README.md       # 项目说明文档
└── .env.example    # 环境变量示例（不包含真实密钥）
```

---

## 工作原理

```
用户输入英文日记
       ↓
前端发送请求到 Google Gemini API
       ↓
AI 分析并返回：
  - 精修后的文章
  - 亮点标记（固定搭配、句型、词组）
  - 中文解释
  - 导师评语
       ↓
前端渲染结果，保存到 LocalStorage
       ↓
用户可导出 PDF 或查看历史
```

---

## 常见问题

### Q: API Key 多少钱？

Google Gemini API 有免费额度：
- 每月 1500 万 token（Gemini 1.5 Flash）
- 足够个人学习使用

### Q: 我的日记数据安全吗？

是的！所有数据都存储在你浏览器的 LocalStorage 中，我们无法访问你的数据。

### Q: 为什么精修结果不如预期？

尝试：
1. 使用更高的 CEFR 等级（如 C1）
2. 输入更长的原始文本
3. 减少文章中的中式英语表达

### Q: 可以离线使用吗？

一旦页面加载完成，即可离线使用（数据仍保存在本地）。

---

## 学习资源

- [CEFR 标准详解](https://www.coe.int/en/web/common-european-framework-reference-languages)
- [Google Gemini 官方文档](https://ai.google.dev/docs)
- [Tailwind CSS 文档](https://tailwindcss.com/docs)
- [React 官方教程](https://react.dev/learn)

---

## 许可证

本项目仅供学习交流使用。

---

## 致谢

- [React](https://react.dev) - UI 框架
- [Tailwind CSS](https://tailwindcss.com) - 样式框架
- [Lucide](https://lucide.dev) - 图标库
- [Google Gemini](https://ai.google.dev) - AI 能力支持
