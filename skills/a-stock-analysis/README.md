# A 股分析 Skill / 提示词

把 TradingAgents-Astock 的多 Agent 投研流程，收成一份可分享、可复用的分析模板。

## 文件

| 文件 | 用途 |
|------|------|
| `SKILL.md` | Cursor / Claude Code Skill（Agent 自动加载） |
| `PROMPT.md` | 纯提示词，复制到任何 LLM 即可用 |

## 怎么用

### 1. 在本仓库用 Cursor Agent

把本目录放到 Cursor skills 路径，或对话里说：

```text
按 skills/a-stock-analysis 分析 603203，并给出后续操作
```

Agent 应调用 `tradingagents.dataflows.a_stock` 拉数，再按 `SKILL.md` 输出。

### 2. 分享给别人（无代码）

打开 `PROMPT.md`，复制「提示词正文」，把 `{股票}` 换成代码/名称发给任意对话模型。对方若能上网查行情更好；否则把行情/财报粘贴进去。

### 3. 本机跑完整 TradingAgents（自动出长报告）

```bash
pip install -e .
# 配置 .env 里的 LLM API Key
tradingagents-web
# 输入 6 位代码 + 日期 → 开始分析
```

Skill 是「轻量人工/Agent 版」；Web/CLI 是「全量 LLM 辩论版」。

## 和项目主流程的对应关系

```
Skill 章节          →  项目模块
市场/指标           →  agents/analysts/market_analyst.py
基本面              →  fundamentals_analyst.py
游资资金            →  hot_money_tracker.py
解禁                →  lockup_watcher.py
政策/新闻           →  policy_analyst.py / news_analyst.py
多空+风控+决策      →  researchers / risk_mgmt / portfolio_manager
数据入口            →  dataflows/a_stock.py
```

## 示例问法

- `按 a-stock-analysis 分析 002407，后续怎么操作`
- `603203 今天最佳出货价`
- `广誉远回踩多少适合入手`
- `对比 600771、002241、000021 哪只更适合建仓`
