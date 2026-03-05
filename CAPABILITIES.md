# 我的能力清单 (Capabilities)

_最后更新：2026 年 3 月 5 日_

这是我所有可用技能和工具能力的完整清单，用于快速参考和任务规划。

---

## 📋 目录

1. [已安装技能](#已安装技能)
2. [系统内置工具](#系统内置工具)
3. [技能详细说明](#技能详细说明)
4. [快速使用指南](#快速使用指南)

---

## 已安装技能

| 技能名称 | 状态 | 环境要求 | 用途 |
|----------|------|----------|------|
| `baidu-search` | ✅ 已配置 | `BAIDU_API_KEY` | 百度搜索新闻和信息 |
| `find-skills` | ✅ 可用 | 无 | 发现和安装新技能 |
| `humanizer` | ✅ 可用 | 无 | 去除 AI 写作痕迹，让文本更自然 |
| `mcporter` | ⚠️ 需安装 | `mcporter` 命令 | MCP 服务器工具调用 |
| `open-webSearch` | ✅ 可用 | 无 (免费) | 多引擎网页搜索 (MCP 服务器) |
| `safe-exec` | ✅ 可用 | `jq` | 安全命令执行，危险操作拦截 |
| `self-improving-agent` | ✅ 可用 | 无 | 持续学习，记录错误和改进 |
| `tavily-search` | ⚠️ 需配置 | `TAVILY_API_KEY` | AI 优化的网页搜索 |
| `weather` | ✅ 可用 | `curl` | 天气预报 (无需 API 密钥) |

---

## 系统内置工具

这些是 OpenClaw 系统提供的核心工具，无需额外配置：

| 工具 | 用途 | 备注 |
|------|------|------|
| `read` | 读取文件内容 | 支持文本和图片 |
| `write` | 创建/覆盖文件 | 自动创建父目录 |
| `edit` | 精确编辑文件 | 需要完全匹配原文本 |
| `exec` | 执行 shell 命令 | 支持后台运行和 PTY |
| `process` | 管理后台进程 | 查看日志、发送输入等 |
| `web_search` | 网页搜索 (Brave API) | 内置搜索工具 |
| `web_fetch` | 抓取网页内容 | HTML 转 Markdown/文本 |
| `browser` | 浏览器自动化 | 点击、输入、截图等 |
| `canvas` | 节点画布控制 | 呈现/评估/快照 UI |
| `nodes` | 配对节点管理 | 通知/摄像头/屏幕/位置 |
| `message` | 发送消息 | 跨平台消息 (需配置 channel) |
| `agents_list` | 列出可用子代理 | 用于 `sessions_spawn` |
| `sessions_list` | 列出会话 | 包括子代理会话 |
| `sessions_history` | 获取会话历史 | 读取其他会话记录 |
| `sessions_send` | 发送消息到会话 | 跨会话通信 |
| `subagents` | 管理子代理 | 列出/引导/终止 |
| `session_status` | 查看会话状态 | 用量/时间/成本 |
| `memory_search` | 搜索记忆文件 | 语义搜索 MEMORY.md |
| `memory_get` | 读取记忆片段 | 安全读取记忆文件 |
| `sessions_spawn` |  spawns 子代理会话 | 隔离任务执行 |
| `tts` | 文本转语音 | 自动交付音频 |

---

## 技能详细说明

### 🔍 baidu-search

**用途**: 通过百度 AI 搜索引擎搜索新闻和信息

**命令**:
```bash
python3 ~/.openclaw/skills/baidu-search/scripts/search.py '<JSON>'
```

**参数**:
- `query` (必填): 搜索关键词
- `edition`: `standard` (完整) 或 `lite` (轻量)
- `resource_type_filter`: 资源类型过滤 (web/video/image/aladdin)
- `search_recency_filter`: 时间过滤 (`week`/`month`/`semiyear`/`year`)
- `search_filter`: 高级过滤 (站点限制、日期范围)
- `block_websites`: 屏蔽特定网站
- `safe_search`: 严格内容过滤

**示例**:
```bash
# 基本搜索
python3 ~/.openclaw/skills/baidu-search/scripts/search.py '{"query":"人工智能"}'

# 最近一周的新闻
python3 ~/.openclaw/skills/baidu-search/scripts/search.py '{"query":"最新新闻","search_recency_filter":"week"}'

# 限定站点搜索
python3 ~/.openclaw/skills/baidu-search/scripts/search.py '{"query":"科技新闻","search_filter":{"match":{"site":["news.baidu.com"]}}}'
```

**状态**: ✅ 已配置，可正常使用

---

### 🌐 open-webSearch (MCP 服务器)

**用途**: 多引擎免费网页搜索，无需 API 密钥

**支持的搜索引擎**:
- Bing
- Baidu
- DuckDuckGo
- Exa
- Brave
- CSDN
- 掘金

**启动命令**:
```bash
npx open-websearch@latest
```

**环境变量**:
- `DEFAULT_SEARCH_ENGINE`: 默认搜索引擎 (默认 `bing`)
- `USE_PROXY`: 启用 HTTP 代理
- `PROXY_URL`: 代理服务器地址
- `PORT`: 服务端口 (默认 `3000`)

**功能**:
- 免费搜索，无需 API 密钥
- 支持 HTTP 代理配置
- 可获取文章全文 (CSDN/GitHub README/掘金)
- 可配置结果数量

**状态**: ✅ 可用，需通过 MCP 调用

---

### 📰 tavily-search

**用途**: AI 优化的网页搜索，返回简洁相关内容

**命令**:
```bash
node ~/.openclaw/skills/tavily-search/scripts/search.mjs "查询词"
```

**选项**:
- `-n <数量>`: 结果数量 (默认 5，最大 20)
- `--deep`: 深度搜索 (更慢但更全面)
- `--topic news`: 新闻主题搜索
- `--days <n>`: 新闻搜索限制最近 n 天

**提取内容**:
```bash
node ~/.openclaw/skills/tavily-search/scripts/extract.mjs "https://example.com/article"
```

**状态**: ⚠️ 需要配置 `TAVILY_API_KEY` (从 https://tavily.com 获取)

---

### 🌤️ weather

**用途**: 获取天气预报，无需 API 密钥

**命令**:
```bash
curl -s "wttr.in/城市名？format=3"
```

**格式代码**:
- `%c`: 天气状况
- `%t`: 温度
- `%h`: 湿度
- `%w`: 风速
- `%l`: 地点
- `%m`: 月相

**示例**:
```bash
# 简洁格式
curl -s "wttr.in/Beijing?format=3"
# 输出：Beijing: ⛅️ +8°C

# 完整预报
curl -s "wttr.in/Shanghai?T"

# 机场代码
curl -s "wttr.in/JFK"

# PNG 图片
curl -s "wttr.in/Berlin.png" -o /tmp/weather.png
```

**备用服务**: Open-Meteo (返回 JSON 格式)

**状态**: ✅ 可用，无需配置

---

### 🛡️ safe-exec

**用途**: 安全命令执行，自动检测危险操作并请求用户批准

**风险等级**:
- 🔴 **CRITICAL**: 系统破坏性命令 (`rm -rf /`, `dd`, `mkfs`)
- 🟠 **HIGH**: 用户数据删除或重大系统更改 (`chmod 777`, `curl | bash`)
- 🟡 **MEDIUM**: 服务操作或配置更改 (`sudo`, 防火墙修改)
- 🟢 **LOW**: 读取操作和安全的文件操作

**命令**:
```bash
# 启用
safe-exec enable

# 查看待批准请求
safe-exec-list

# 批准请求
safe-exec-approve <request_id>

# 拒绝请求
safe-exec-reject <request_id>

# 查看审计日志
cat ~/.openclaw/safe-exec-audit.log
```

**环境变量**:
- `SAFE_EXEC_DISABLE`: 设置为 `1` 全局禁用
- `SAFE_EXEC_AUTO_CONFIRM`: 自动批准 LOW/MEDIUM 风险命令

**状态**: ✅ 可用，自动拦截危险命令

---

### 📝 humanizer

**用途**: 去除 AI 写作痕迹，让文本更自然

**检测的 AI 写作模式**:
1. 过度强调重要性/象征意义
2.  superficial -ing 结尾分析
3. 推广性语言
4. 模糊归因
5. "Challenges and Future"公式化章节
6. AI 高频词汇 (Additionally, crucial, delve, underscore 等)
7. 避免使用 is/are
8. 否定平行结构 (Not only...but...)
9. 三法则过度使用
10. 同义词循环
11. 虚假范围 (from X to Y)
12. 破折号过度使用
13. 粗体过度使用
14. 内联标题列表
15. 标题大小写
16. Emoji 装饰
17. 花括号引号
18. 协作式交流客套话
19. 知识截止日期免责声明
20. 奉承/奴性语气
21. 填充短语
22. 过度谨慎
23. 通用积极结论

**使用场景**:
- 编辑 AI 生成的文本
- 审查文档使其更自然
- 去除"AI 味"

**状态**: ✅ 可用，无需配置

---

### 🔧 mcporter

**用途**: 直接调用 MCP 服务器/工具

**命令**:
```bash
# 列出服务器
mcporter list

# 查看工具 schema
mcporter list <server> --schema

# 调用工具
mcporter call <server.tool> key=value

# OAuth 认证
mcporter auth <server>

# 配置管理
mcporter config list|get|add|remove
```

**示例**:
```bash
# 选择器语法
mcporter call linear.list_issues team=ENG limit:5

# 函数语法
mcporter call "linear.create_issue(title: \"Bug\")"

# stdio 服务器
mcporter call --stdio "bun run ./server.ts" scrape url=https://example.com
```

**状态**: ⚠️ 需要安装 `mcporter` 命令 (`npm install -g mcporter`)

---

### 🎯 find-skills

**用途**: 发现和安装新技能

**命令**:
```bash
# 搜索技能
npx skills find [关键词]

# 安装技能
npx skills add <owner/repo@skill> -g -y

# 检查更新
npx skills check

# 更新所有技能
npx skills update
```

**常用技能类别**:
- Web 开发：react, nextjs, typescript, css, tailwind
- 测试：testing, jest, playwright, e2e
- DevOps: deploy, docker, kubernetes, ci-cd
- 文档：docs, readme, changelog, api-docs
- 代码质量：review, lint, refactor, best-practices
- 设计：ui, ux, design-system, accessibility
- 生产力：workflow, automation, git

**浏览技能**: https://skills.sh/

**状态**: ✅ 可用

---

### 📈 self-improving-agent

**用途**: 持续学习和改进，记录错误和修正

**文件结构**:
```
~/.openclaw/workspace/.learnings/
├── LEARNINGS.md       # 学习记录
├── ERRORS.md          # 错误记录
├── FEATURE_REQUESTS.md # 功能请求
```

**记录时机**:
1. 命令/操作意外失败
2. 用户纠正我 ("不对，应该是...")
3. 用户请求不存在的能力
4. 外部 API/工具失败
5. 我的知识过时或错误
6. 发现更好的方法

**ID 格式**: `TYPE-YYYYMMDD-XXX`
- `LRN-20260305-001`: 学习记录
- `ERR-20260305-001`: 错误记录
- `FEAT-20260305-001`: 功能请求

**优先级**:
- `critical`: 阻塞核心功能、数据丢失风险、安全问题
- `high`: 重大影响、影响常见工作流、重复问题
- `medium`: 中等影响、有变通方案
- `low`: 小问题、边缘情况

**晋升规则**:
当学习记录具有广泛适用性时，晋升到：
- `SOUL.md`: 行为准则
- `AGENTS.md`: 工作流改进
- `TOOLS.md`: 工具使用技巧
- `MEMORY.md`: 长期记忆

**状态**: ✅ 可用，自动记录

---

## 快速使用指南

### 搜索新闻/信息
```bash
# 百度搜索 (已配置)
python3 ~/.openclaw/skills/baidu-search/scripts/search.py '{"query":"关键词","search_recency_filter":"week"}'

# 多引擎搜索 (免费)
npx open-websearch@latest

# Tavily 搜索 (需 API 密钥)
node ~/.openclaw/skills/tavily-search/scripts/search.mjs "关键词" --topic news
```

### 查看天气
```bash
curl -s "wttr.in/Beijing?format=3"
```

### 安全执行命令
```bash
# 自动启用，危险命令会被拦截
# 查看待批准请求
safe-exec-list

# 批准
safe-exec-approve <request_id>
```

### 文本润色
```bash
# 使用 humanizer 技能
# 直接让我处理文本即可
```

### 发现新技能
```bash
npx skills find [关键词]
```

### 记录学习
```bash
# 自动记录到 .learnings/ 目录
# 重要学习会晋升到 MEMORY.md 等文件
```

---

## 环境配置检查清单

### 已配置 ✅
- [x] `BAIDU_API_KEY` - baidu-search
- [x] `curl` - weather 技能
- [x] `jq` - safe-exec
- [x] `python3` - baidu-search
- [x] `node` - tavily-search, open-webSearch

### 需配置 ⚠️
- [ ] `TAVILY_API_KEY` - tavily-search (从 https://tavily.com 获取)
- [ ] `mcporter` 命令 - mcporter 技能 (`npm install -g mcporter`)

---

## 能力矩阵

| 能力类别 | 可用工具 | 状态 |
|----------|----------|------|
| **网页搜索** | baidu-search, tavily-search, open-webSearch, web_search | ✅ |
| **天气查询** | weather | ✅ |
| **文件操作** | read, write, edit, exec | ✅ |
| **浏览器自动化** | browser | ✅ |
| **消息发送** | message, sessions_send | ⚠️ (需配置 channel) |
| **子代理** | sessions_spawn, subagents | ✅ |
| **记忆管理** | memory_search, memory_get | ✅ |
| **安全执行** | safe-exec | ✅ |
| **文本处理** | humanizer | ✅ |
| **持续学习** | self-improving-agent | ✅ |
| **MCP 工具** | mcporter | ⚠️ (需安装) |
| **技能发现** | find-skills | ✅ |

---

## 使用建议

1. **搜索优先**: 需要实时信息时，先用 `baidu-search` 或 `open-webSearch`
2. **安全第一**: 危险命令会被 `safe-exec` 自动拦截，无需担心
3. **持续学习**: 错误和纠正会自动记录到 `.learnings/` 目录
4. **文本润色**: 需要去除 AI 味时，使用 `humanizer` 技能
5. **天气查询**: 直接用 `curl wttr.in/城市` 快速获取
6. **子代理任务**: 长时间任务用 `sessions_spawn` 隔离执行
7. **记忆检索**: 回答关于历史的问题前，先用 `memory_search`

---

_这份文档会随着新技能的安装和配置自动更新。_
