# Daily Brief Builder

用 Claude Code 快速创建个性化新闻简报系统。

## 使用方法

1. 在 Claude Code 中运行：
   ```
   读取 daily_brief_builder.md，帮我创建一个关于 [你的主题] 的 Daily Brief
   ```

2. 回答几个问题（关键词、追踪对象等）

3. 系统自动生成完整的简报系统

4. 之后只需进入生成的文件夹，运行 `/daily-brief`

## 生成的系统结构

```
Daily_Brief_[主题]/
├── CLAUDE.md              # 配置文件
├── .claude/commands/
│   └── daily-brief.md     # 简报命令
└── briefs/
    └── YYYY-MM-DD.html    # 简报输出
```

## 特性

- HTML 输出，Anthropic 风格设计
- 支持深色/浅色模式
- 可定制关键词、信息源、筛选标准

详细文档见 [daily_brief_builder.md](daily_brief_builder.md)
