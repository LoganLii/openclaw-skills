# 快速参考卡 (Quick Reference)

_放在手边的能力速查表_

---

## 🔍 搜索

```bash
# 百度搜索 (已配置)
python3 ~/.openclaw/skills/baidu-search/scripts/search.py '{"query":"关键词"}'

# 多引擎免费搜索
npx open-websearch@latest

# 内置 Brave 搜索
web_search query="关键词" count=10
```

---

## 🌤️ 天气

```bash
# 当前天气
curl -s "wttr.in/Beijing?format=3"

# 完整预报
curl -s "wttr.in/Shanghai?T"
```

---

## 🛡️ 安全命令

```bash
# 查看待批准
safe-exec-list

# 批准命令
safe-exec-approve <request_id>

# 查看审计日志
cat ~/.openclaw/safe-exec-audit.log
```

---

## 📝 文本润色

直接说："帮我把这段文字改得更自然/更人性化"

---

## 📈 记录学习

自动记录到 `~/.openclaw/workspace/.learnings/`

- `LEARNINGS.md` - 学习和修正
- `ERRORS.md` - 错误记录
- `FEATURE_REQUESTS.md` - 功能请求

---

## 🎯 发现技能

```bash
npx skills find [关键词]
npx skills add <包名> -g -y
```

浏览：https://skills.sh/

---

## 📊 会话管理

```bash
# 查看会话
sessions_list

# 查看状态
session_status

# spawns 子代理
sessions_spawn task="任务描述"
```

---

## 🧠 记忆检索

```bash
# 搜索记忆
memory_search query="关键词"

# 读取片段
memory_get path="MEMORY.md" from=1 lines=10
```

---

## ⚙️ 环境变量

| 变量 | 用途 | 状态 |
|------|------|------|
| `BAIDU_API_KEY` | 百度搜索 | ✅ 已配置 |
| `TAVILY_API_KEY` | Tavily 搜索 | ⚠️ 需配置 |
| `SAFE_EXEC_DISABLE` | 禁用安全执行 | 默认启用 |

---

## 📁 重要路径

```
~/.openclaw/workspace/          # 工作区
~/.openclaw/workspace/CAPABILITIES.md  # 能力清单
~/.openclaw/workspace/MEMORY.md        # 长期记忆
~/.openclaw/workspace/.learnings/      # 学习记录
~/.openclaw/skills/                    # 已安装技能
~/.openclaw/safe-exec-audit.log        # 安全执行日志
```

---

## 🚀 常用命令速查

| 任务 | 命令 |
|------|------|
| 搜索新闻 | `baidu-search` 脚本 |
| 查天气 | `curl wttr.in/城市` |
| 执行危险命令 | 自动拦截，需批准 |
| 润色文本 | 直接请求 |
| 发现技能 | `npx skills find` |
| 查看日志 | `cat ~/.openclaw/safe-exec-audit.log` |

---

_详细文档：`CAPABILITIES.md`_
