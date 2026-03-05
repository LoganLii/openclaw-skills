# OpenClaw Skills Collection

我的 OpenClaw 技能集合和配置文档。

## 📚 内容

- **CAPABILITIES.md** - 完整的能力清单和使用指南
- **QUICK-REFERENCE.md** - 快速参考卡
- **skills/** - 技能配置和脚本

## 🚀 快速开始

### 克隆项目

```bash
git clone https://github.com/LoganLii/openclaw-skills.git
cd openclaw-skills
```

### 查看能力清单

阅读 `CAPABILITIES.md` 了解所有可用技能和使用方法。

### 使用快速参考

`QUICK-REFERENCE.md` 包含常用命令速查。

## 📋 已安装技能

| 技能 | 状态 | 用途 |
|------|------|------|
| baidu-search | ✅ | 百度搜索新闻 |
| open-webSearch | ✅ | 多引擎免费搜索 |
| weather | ✅ | 天气预报 |
| safe-exec | ✅ | 安全命令执行 |
| humanizer | ✅ | 文本润色 |
| self-improving-agent | ✅ | 持续学习 |
| find-skills | ✅ | 发现新技能 |
| tavily-search | ⚠️ | AI 搜索 (需 API 密钥) |
| mcporter | ⚠️ | MCP 工具 (需安装) |

## 🔧 配置

### 环境变量

创建 `.env` 文件（不提交到 Git）：

```bash
# 百度搜索
BAIDU_API_KEY=your_key_here

# Tavily 搜索
TAVILY_API_KEY=your_key_here
```

### Git 配置

```bash
git config user.name "Your Name"
git config user.email "your@email.com"
```

## 📖 文档

- [完整能力清单](./CAPABILITIES.md)
- [快速参考](./QUICK-REFERENCE.md)

## 🔐 安全提示

- **不要** 将密码、Token 提交到 Git
- 使用 `.env` 文件存储敏感信息
- 将 `.env` 添加到 `.gitignore`

## 📝 更新日志

- 2026-03-05: 初始版本，创建项目

---

**GitHub**: [@LoganLii](https://github.com/LoganLii)
