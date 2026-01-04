# Daily Brief 个性化新闻简报系统构建指南

> **用途**: 本文档是构建个性化新闻简报系统的元模板。Claude Code 读取此文档后，可根据用户输入的关键词和需求，自动生成完整的 Daily Brief 系统。

---

## 🚀 快速开始

### 使用方法

1. 进入 Claude Code
2. 告诉 Claude：`读取 daily_brief_builder.md，帮我创建一个关于 [你的主题] 的 Daily Brief 系统`
3. 回答 Claude 的几个问题（主题、关键词、保存位置等）
4. 系统自动生成完整的文件夹结构
5. 以后只需进入该文件夹，运行 `/daily-brief` 即可

### 示例对话

```
用户: 读取 daily_brief_builder.md，帮我创建一个关于"量子计算投资"的 Daily Brief

Claude: 好的，我来帮你创建。请回答几个问题：
1. 保存位置？（默认: ~/Documents/Daily_Brief_量子计算投资）
2. 关注的细分方向？（如：量子硬件、量子软件、投资动态...）
3. 追踪的重点公司/机构？
4. 中文还是英文为主？

用户: 
1. 默认位置
2. 量子硬件、量子算法、融资新闻
3. IBM, Google, IonQ, 本源量子
4. 中英文都要

Claude: [自动生成完整系统]
```

---

## 📁 系统文件结构

每个 Daily Brief 系统包含以下结构：

```
Daily_Brief_[主题名]/
├── CLAUDE.md                    # 核心配置文件（必须）
├── .claude/
│   ├── commands/
│   │   └── daily-brief.md       # 主命令定义（必须）
│   └── subagents/
│       ├── [tracker].md         # 信息追踪子代理（可选，按需添加）
│       └── [analyzer].md        # 分析子代理（可选，按需添加）
└── briefs/                      # 简报存档目录
    └── YYYY-MM-DD.md            # 每日简报
```

---

## 📄 核心文件模板

### 1. CLAUDE.md（核心配置）

```markdown
# Daily Brief | [主题名称]

## 追踪目标

- **主题**: [一句话描述追踪的主题]
- **目的**: [为什么要追踪这个主题]
- **更新频率**: 每日 / 每周 / 按需

---

## 🎯 关注重点

### 核心关键词

| 关键词 | 优先级 | 说明 |
|-------|-------|------|
| [关键词1] | ⭐⭐⭐⭐⭐ | [为什么重要] |
| [关键词2] | ⭐⭐⭐⭐ | [说明] |
| [关键词3] | ⭐⭐⭐ | [说明] |

### 追踪对象（可选）

| 对象 | 类型 | 关注点 |
|-----|------|-------|
| [公司/人物/机构1] | 公司/学者/机构 | [关注什么] |
| [公司/人物/机构2] | ... | ... |

### 信息来源

| 来源类型 | 具体来源 | 优先级 |
|---------|---------|-------|
| 学术论文 | arXiv, bioRxiv, Nature... | ⭐⭐⭐⭐⭐ |
| 行业新闻 | TechCrunch, 36氪... | ⭐⭐⭐⭐ |
| 官方发布 | 公司博客, 政府网站... | ⭐⭐⭐⭐⭐ |
| 社交媒体 | Twitter/X, 微信公众号... | ⭐⭐⭐ |

---

## 🔍 搜索策略

### 主要搜索词

**英文**
```
[keyword1] [keyword2] [year]
[keyword3] news update
site:[domain] [topic]
```

**中文**
```
[关键词1] [关键词2] 最新
[关键词3] 动态 [年份]
```

### 筛选标准

**✅ 保留**
- [条件1]
- [条件2]
- [条件3]

**❌ 过滤**
- [排除条件1]
- [排除条件2]

---

## 📊 输出要求

### 简报结构

1. **今日要点** - 最重要的 1-3 条信息
2. **详细内容** - 按分类展开
3. **行动建议** - 需要关注或采取的行动
4. **链接汇总** - 原文链接

### 优先级标记

- 🔴 **重大** - 需要立即关注
- 🟠 **重要** - 当天了解
- 🟡 **一般** - 有空时看
- ⚪ **参考** - 存档备查

---

## Daily Brief Protocol

`/daily-brief` 命令将执行：

1. 搜索最新信息
2. 按筛选标准过滤
3. 分类整理
4. 生成简报
5. 保存至 `/briefs/YYYY-MM-DD.md`

---

## 文件结构

```
Daily_Brief_[主题]/
├── CLAUDE.md
├── .claude/
│   ├── commands/
│   │   └── daily-brief.md
│   └── subagents/
│       └── [按需添加].md
└── briefs/
    └── YYYY-MM-DD.md
```
```

---

### 2. daily-brief.md（主命令）

```markdown
# Daily Brief | [主题名称]

[一句话描述这个简报的目的]

## 执行流程

### 第一步：加载配置

阅读 `CLAUDE.md` 获取：
- 核心关键词
- 追踪对象
- 筛选标准

### 第二步：多源搜索

使用 web search 执行搜索：

**[分类1]**
```
[搜索词1]
[搜索词2]
```

**[分类2]**
```
[搜索词3]
[搜索词4]
```

### 第三步：信息筛选

按 CLAUDE.md 中的筛选标准处理搜索结果：
- 保留符合条件的信息
- 过滤不相关内容
- 按优先级排序

### 第四步：生成简报

使用下方输出模板生成简报

### 第五步：保存

保存至 `/briefs/YYYY-MM-DD.md`

---

## 输出模板

```markdown
# 📰 [主题] 简报 | YYYY-MM-DD

> [一句话 slogan]

---

## 🌟 今日要点

[最重要的 1-3 条信息，用 bullet points]

---

## 📋 详细内容

### [分类1]

**[标题1]**
- **来源**: [来源名称]
- **日期**: YYYY-MM-DD
- **要点**: [简要说明]
- **链接**: [URL]

### [分类2]

...

---

## 💡 行动建议

- [ ] [需要做的事情1]
- [ ] [需要做的事情2]

---

## 🔗 链接汇总

| 标题 | 来源 | 链接 |
|-----|------|------|
| xxx | xxx | [链接] |

---

*生成时间: HH:MM*
```

---

## 重要提醒

- 信息准确性优先
- 标注信息来源
- 区分事实与观点
- 关注时效性
```

---

### 3. 子代理模板（按需添加）

子代理是可选的，用于复杂场景。常见类型：

#### 3.1 Tracker（追踪器）

```markdown
# [名称] Tracker | 追踪器

专门追踪 [具体对象] 的 [具体内容]。

## 追踪范围

| 对象 | 追踪内容 | 频率 |
|-----|---------|------|
| [对象1] | [内容] | 每日 |
| [对象2] | [内容] | 每周 |

## 搜索策略

[具体搜索词和方法]

## 输出格式

[该追踪器的输出格式]
```

#### 3.2 Analyzer（分析器）

```markdown
# [名称] Analyzer | 分析器

对 [具体内容] 进行深度分析。

## 分析维度

| 维度 | 分析方法 | 输出 |
|-----|---------|------|
| [维度1] | [方法] | [格式] |
| [维度2] | [方法] | [格式] |

## 评估标准

[具体的评估框架]

## 输出格式

[分析报告的格式]
```

---

## 🎨 自定义选项

### 按主题类型选择模板

| 主题类型 | 建议的子代理 | 特殊配置 |
|---------|------------|---------|
| **行业动态** | news-tracker, competitor-analyzer | 重点追踪公司/产品 |
| **学术研究** | paper-tracker, method-analyzer | 重点追踪作者/会议 |
| **政策追踪** | policy-tracker, benefit-analyzer | 重点追踪发布机构 |
| **求职/岗位** | job-tracker, opportunity-analyzer | 重点追踪机构/要求 |
| **项目优化** | paper-tracker, code-optimizer, benchmark-analyst | 重点追踪技术/竞品 |
| **投资/市场** | market-tracker, trend-analyzer | 重点追踪数据/趋势 |

### 语言配置

```yaml
language:
  primary: zh-CN / en-US
  search: both / zh-only / en-only
  output: zh-CN / en-US / bilingual
```

### 更新频率

```yaml
frequency:
  type: daily / weekly / on-demand
  best_time: 早晨 / 下午 / 晚间
```

---

## 🔧 构建步骤

当用户请求创建 Daily Brief 系统时，按以下步骤执行：

### Step 1: 收集信息

询问用户：
1. **主题名称**: 简短的主题描述
2. **保存位置**: 文件夹路径（提供默认值）
3. **关注的关键词**: 3-10 个核心关键词
4. **追踪对象**（可选）: 公司/人物/机构
5. **信息来源偏好**: 学术/新闻/官方/社交
6. **语言偏好**: 中文/英文/双语
7. **特殊需求**: 任何其他定制需求

### Step 2: 生成文件结构

```bash
mkdir -p [路径]/.claude/commands
mkdir -p [路径]/.claude/subagents
mkdir -p [路径]/briefs
```

### Step 3: 生成 CLAUDE.md

根据收集的信息，填充 CLAUDE.md 模板

### Step 4: 生成 daily-brief.md

根据主题特点，定制搜索策略和输出格式

### Step 5: 生成子代理（如需要）

根据主题类型，选择并生成合适的子代理

### Step 6: 确认完成

向用户展示：
- 创建的文件结构
- 使用方法
- 首次运行建议

---

## 📝 示例系统

### 已创建的 Daily Brief 系统参考

| 系统 | 主题 | 子代理 |
|-----|------|-------|
| Daily_Brief_EVMarket | 新能源汽车市场 | news-tracker, trend-analyzer |
| Daily_Brief_LLMResearch | 大语言模型研究 | paper-tracker, benchmark-analyst |
| Daily_Brief_QuantumComputing | 量子计算投资 | news-tracker, market-analyzer |
| Daily_Brief_ClimatePolicy | 气候政策追踪 | policy-tracker, trend-analyzer |
| Daily_Brief_SpaceTech | 商业航天动态 | news-tracker, competitor-analyzer |

---

## 💡 灵感库：有趣的 Daily Brief 主题创意

不知道追踪什么？这里有一些有趣的灵感：

### 🎮 游戏娱乐

| 主题 | 追踪内容 | 建议子代理 |
|-----|---------|------------|
| Steam/Epic 限时免费 | 每日免费领取的游戏 | deal-tracker |
| 游戏历史低价 | 愿望单游戏降到史低 | price-monitor |
| Xbox Game Pass 新增 | 会员库新游戏 | news-tracker |
| Switch eShop 打折 | 任天堂折扣 | deal-tracker |
| 独立游戏发布 | itch.io / 小众佳作 | release-tracker |

### 📺 影视追番

| 主题 | 追踪内容 | 建议子代理 |
|-----|---------|------------|
| 今日新番更新 | B站/Crunchyroll 番剧 | schedule-tracker |
| Netflix 即将下架 | 快过期的片子 | expiry-monitor |
| 豆瓣高分新片 | 8分以上新上映 | rating-tracker |
| 院线排片 | 想看的电影什么时候上 | release-tracker |

### 💰 省钱薅羊毛

| 主题 | 追踪内容 | 建议子代理 |
|-----|---------|------------|
| 信用卡活动 | 满减、积分兑换 | deal-tracker |
| 外卖红包 | 美团/饿了么神券 | coupon-tracker |
| 机票低价 | 特定航线历史低价 | price-monitor |
| 酒店 Bug 价 | 飞猪/Booking 漏洞价 | deal-tracker |
| 会员充值优惠 | 视频/音乐会员打折 | deal-tracker |

### 🔧 数码科技

| 主题 | 追踪内容 | 建议子代理 |
|-----|---------|------------|
| GitHub Trending | 今日热门开源项目 | repo-tracker |
| Product Hunt 日榜 | 新奇产品/工具 | product-tracker |
| iOS/Mac 限免 App | 付费应用免费领 | deal-tracker |
| 苹果泄露/爆料 | 新品发布前的小道消息 | rumor-tracker |
| AI 工具更新 | ChatGPT/Claude 新功能 | release-tracker |

### 📚 学习成长

| 主题 | 追踪内容 | 建议子代理 |
|-----|---------|------------|
| Udemy 课程 ¥9.9 | 限时低价课程 | deal-tracker |
| 新书发布 | 关注作者的新书 | release-tracker |
| 播客更新 | 订阅的播客新一期 | schedule-tracker |
| Hacker News 精选 | 技术圈热门讨论 | news-tracker |

### 🌟 小众有趣

| 主题 | 追踪内容 | 建议子代理 |
|-----|---------|------------|
| 太空发射日历 | SpaceX/中国航天发射 | schedule-tracker |
| 流星雨/天文事件 | 今晚能看什么 | event-tracker |
| Kickstarter 有趣项目 | 众筹中的新奇玩意 | product-tracker |
| 限量球鞋发售 | 抽签/补货提醒 | release-tracker |
| 黑胶唱片再版 | 经典专辑重新发行 | release-tracker |
| 猫咪领养 | 本地救助站新猫咪 | listing-tracker |
| 二手相机 | 闲鱼/eBay 捡漏 | deal-tracker |
| 威士忌新品 | 限量版发售 | release-tracker |

### 🏃 生活提醒

| 主题 | 追踪内容 | 建议子代理 |
|-----|---------|------------|
| 明日天气+穿搭 | 该穿什么出门 | weather-advisor |
| 限行提醒 | 车牌尾号限行 | schedule-tracker |
| 快递物流 | 包裹到哪了 | logistics-tracker |
| 水电费账单 | 该交费了 | bill-reminder |
| 护照/签证到期 | 证件有效期提醒 | expiry-monitor |

### 💹 投资理财

| 主题 | 追踪内容 | 建议子代理 |
|-----|---------|------------|
| 加密货币异动 | 大涨大跌提醒 | price-monitor |
| 美股盘前 | 持仓股票新闻 | news-tracker |
| 可转债打新 | 今日可申购 | calendar-tracker |
| 分红日历 | REITs/股息股分红日 | calendar-tracker |

---

## ⚡ 一键构建命令

用户可以使用以下格式快速创建：

```
创建 Daily Brief: [主题]
关键词: [词1], [词2], [词3]
追踪: [对象1], [对象2]
位置: [路径]
```

Claude 将自动：
1. 解析用户输入
2. 生成完整系统
3. 提供使用说明

---

## 🔄 系统维护

### 定期更新

- 每月检查关键词是否需要调整
- 根据使用情况优化搜索策略
- 清理过期的 briefs 文件

### 扩展功能

可以随时添加：
- 新的子代理
- 新的搜索源
- 新的输出格式

---

*本文档版本: 1.0 | 最后更新: 2025-01*
