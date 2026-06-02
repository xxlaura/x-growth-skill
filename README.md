# x-growth

[English](README.en.md) | **中文**

基于 X (Twitter) For You 推荐算法源码逆向分析的 AI 增长黑客工具箱。

为 AI Agent（Qwen Code、Claude Code、Cursor 等）设计的 skill，通过 13 个子命令帮你生成算法优化的推文、Thread、视频脚本、KOL 回复、抽奖活动，以及每周内容日历。

## 为什么做这个

[X For You 算法已开源](https://github.com/xai-org/x-algorithm)，我们从源码中提取了所有排名信号、权重逻辑和内容过滤规则。这个 skill 把这些算法秘密转化为可操作的内容生成规则：

- **19 种互动信号权重** — DM 分享 > 回复 > 点赞 > 转发
- **80 小时帖子寿命** — 前 2 小时是黄金引爆期
- **作者多样性惩罚** — 每天最多 3 条，否则算法降权
- **Slop Score** — AI 生成内容检测，需要专门的反检测策略
- **VQV 视频信号** — 30s-2min 视频触发多重高权重信号

## 快速开始

### 安装

**方式 1：直接复制**

```bash
# 克隆仓库
git clone https://github.com/xxlaura/x-growth-skill.git

# 复制到你的项目 skills 目录
cp -r x-growth-skill .agents/skills/x-growth
```

**方式 2：Git Submodule**

```bash
git submodule add https://github.com/xxlaura/x-growth-skill.git .agents/skills/x-growth
```

**方式 3：手动下载**

下载本仓库，将文件放入你的项目 `.agents/skills/x-growth/` 目录。

### 第一步：设置账号风格

```
/x-growth voice-setup
```

通过 3 轮问答 + 写作样本分析，生成你的账号声音档案：

- `config/about.md` — 账号身份（你是谁、写给谁看）
- `config/voice.md` — 声音规则（怎么说话 + 绝不怎么说）

所有后续命令都会自动读取这两个文件，确保风格一致。

**4 个快捷预设（跳过问答）：**

| 预设 | 风格 | 参考账号 |
|------|------|---------|
| A) Product-Led Brand | 简洁、产品说话 | @linear, @stripe |
| B) Developer Builder | 技术 + 有趣 + 有态度 | @supabase, @railway |
| C) Technical Educator | 清晰、深度、慷慨 | @swyx, @karpathy |
| D) Founder Voice | 大胆、愿景、透明 | Building in public 风格 |

## 命令参考

### 日常命令（记住这 5 个就够）

| 命令 | 用途 | 示例 |
|------|------|------|
| `write` | 写一条推文 | `/x-growth write Qwen3.7 多模态能力` |
| `rewrite` | 去 AI 味改写 | `/x-growth rewrite [粘贴文案]` |
| `reply` | 写 KOL 回复 | `/x-growth reply [KOL 帖子]` |
| `hook` | 想不出开头 | `/x-growth hook API 降价` |
| `audit` | 发布前检查 | `/x-growth audit [你的帖子]` |

### 进阶命令

| 命令 | 用途 |
|------|------|
| `voice-setup` | 设置/更新账号风格 |
| `thread` | 写 Thread（5-12 条） |
| `video-script` | 写视频脚本（30s-2min） |
| `giveaway` | 设计抽奖活动 |
| `calendar` | 生成一周内容日历 |
| `benchmark` | 写对比测评帖 |
| `meme` | 写行业 Meme |
| `analyze` | 分析帖子数据 |

### 自然语言（不需要记命令名）

```
/x-growth 帮我写一条关于视频理解的推文        → write
/x-growth 这段话太 AI 了帮我改改：[粘贴]      → rewrite
/x-growth 这个人发了这个，帮我回复：[粘贴]    → reply
```

系统会自动识别你的意图。

## 账号类型与 Anti-Slop 策略

不同类型的账号，降低 AI 检测的策略完全不同：

| 类型 | Anti-Slop 方法 | 适合 |
|------|---------------|------|
| **个人账号** | 口语化 + 不完美 + emoji + 个人经历 | 创始人、开发者、创作者 |
| **品牌账号** | 具体数字 + 内部数据 + 技术精确 + 克制 | 公司、产品、团队 |
| **混合账号** | 两者结合 | CEO 代表品牌、团队负责人 |

`voice-setup` 会根据你选择的账号类型自动应用对应策略。

## 架构

```
x-growth-skill/
├── SKILL.md                    # 主入口 + 命令路由
├── config/
│   ├── about.md                # 账号身份（voice-setup 生成）
│   └── voice.md                # 声音规则（voice-setup 生成）
├── reference/
│   ├── voice-setup.md          # 风格设置流程
│   ├── algorithm.md            # X 算法核心知识
│   ├── anti-slop.md            # Anti-slop 规则（个人 + 品牌）
│   ├── content-types.md        # 8 种内容类型模板
│   ├── hooks.md                # 10 种开头 hook 公式
│   ├── cta-patterns.md         # CTA 触发器模板
│   ├── thread-structure.md     # Thread 结构模板
│   ├── video-script.md         # VQV 优化视频脚本
│   ├── reply-craft.md          # KOL 回复写法
│   ├── giveaway-design.md      # 抽奖活动设计
│   ├── cadence.md              # 发帖节奏与时间窗口
│   └── weekly-calendar.md      # 4 周内容日历模板
└── agents/
    └── x-growth-analyst.md     # 数据分析子 Agent
```

### 依赖链

```
voice-setup → about.md + voice.md
                    ↓
          所有下游命令读取
    (write, thread, reply, hook, rewrite...)
```

`voice-setup` 是基础。所有其他命令在生成内容前都会先读取 `config/about.md` 和 `config/voice.md`。

## 算法核心数字

| 参数 | 值 |
|------|-----|
| 帖子最大寿命 | 80 小时（3.3 天） |
| 黄金引爆期 | 前 2 小时 |
| 每天最多发帖 | 3 条（超过被降权） |
| 帖子最小间隔 | 4 小时 |
| 互动信号排名 | DM 分享 > 回复 > 点赞 > 转发 |
| 视频最佳时长 | 30s - 2min |
| 作者第 2 条帖子 | 得分只剩 55% |
| 作者第 3 条帖子 | 得分只剩 32.5% |

## 兼容性

本 skill 兼容以下 AI Agent 平台：

- [Qwen Code](https://github.com/QwenLM/qwen-code) — `.agents/skills/`
- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) — `.claude/skills/`
- [Cursor](https://cursor.sh) — `.cursor/skills/`
- 其他支持 Markdown skill 的 Agent

## 贡献

欢迎 PR 和 Issue。改进方向：

- 更多语言/地区的发帖时间优化
- 新的内容类型模板
- 更多 voice preset
- 数据分析和 A/B 测试框架

## License

MIT
