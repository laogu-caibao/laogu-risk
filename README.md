# 财务风险预警

`laogu-risk`

财务风险预警 skill：输入一家 A 股公司（名称或代码），输出中文财务风险体检表。

## 一键安装

```bash
npx skills add laogu-caibao/laogu-risk
```

仓库地址（点击复制）：

`https://github.com/laogu-caibao/laogu-risk`

**方式一：克隆**

```bash
git clone https://github.com/laogu-caibao/laogu-risk.git
```

**方式二：下载 ZIP**

https://github.com/laogu-caibao/laogu-risk/archive/refs/heads/main.zip

**导入使用**

- Claude Code / Muse：把仓库中的 `SKILL.md` 放到 `~/.claude/skills/laogu-risk/` 下即可调用。
- 豆包智能体 / Workbuddy 等：按各平台的 skill 上传流程导入 `SKILL.md`。
- 扣子 Coze：扣子编程 → 技能面板 → 创建技能 → 本地上传，上传本仓库打包的 zip（仓库根目录已有 SKILL.md，直接压缩仓库文件夹即可）；如页面要求 `.skill` 后缀，由扣子导入后自动生成，不要只改扩展名。
- Trae：设置 → 技能 → 上传技能，上传同上 zip；或手动放到 `~/.trae/skills/laogu-risk/`（项目级用 `.trae/skills/laogu-risk/`）。Trae 也支持 MCP：把 `uvx laogu-mcp` 配进 MCP 设置即可获得 16 个工具（skill 负责流程指导、MCP 负责工具调用）。
- 一次装好全部 16 个：用 [laogu-mcp](https://github.com/laogu-caibao/laogu-mcp)，`uvx laogu-mcp` 一键安装。
## 文件结构

- `SKILL.md` — 主流程（平台中立：纯流程描述，可移植到豆包工作 / WorkBuddy 等 Agent 平台）
- `references/sources.md` — 数据源：东财公告列表/正文接口、财务数字搜索模板、红黄绿灯经验阈值

## 体检指标（8 项）

1. 商誉 / 净资产比
2. 存贷双高（货币资金 vs 有息负债）
3. 应收账款 / 营收比
4. 经营现金流 vs 净利润背离
5. 毛利率异常波动
6. 大股东质押比例
7. 连续亏损 / ST 风险
8. 审计意见非标

## 输出结构

- 标题行：公司全称（代码）+ 报告期 + 生成日期
- 体检表：8 项逐项数值 + 灯号🟢/🟡/🔴 + 依据（注明来源）
- 综合灯号：🔴 高风险 / 🟡 有风险信号 / 🟢 未发现明显风险信号
- 一句话结论 + 固定风险提示行

## 原则

- 只做风险信号提示，不做买卖推荐，不预测股价
- 取不到的数字标"未核验"，不编造、不估算
- 红绿灯阈值为经验阈值，非监管标准

---
## English

**laogu-risk — Financial risk screener.** Pulls key figures from the latest annual or interim report, scores each dimension, and outputs a red/yellow/green financial health table. Install: `npx skills add laogu-caibao/laogu-risk`.

## FAQ

**Q：laogu-risk 有什么用？**
适合的场景：买入或跟踪一家公司前，先做一次财务体检，看有没有踩雷信号（红黄绿灯逐项打分）。

**Q：数据可靠吗？会荐股吗？**
数字必须来自可核验的公开来源（上市公司公告、交易所公开数据、公开网页），取不到就标「未核验」，绝不编造；只做结构化整理与解读，不构成投资建议。

**Q：怎么安装？支持哪些 AI 平台？**
```bash
npx skills add laogu-caibao/laogu-risk
```
平台中立 Markdown，Claude Code、Codex、豆包智能体、Workbuddy、扣子 Coze、Trae 等环境均可用；数据能力可用 [laogu-mcp](https://github.com/laogu-caibao/laogu-mcp)（`uvx laogu-mcp`）一次装齐。更多 skill 见[老谷拆财报组织主页](https://github.com/laogu-caibao)。
---

## 出品

**老谷拆财报** —— 以数据为刃，剖市场真相

- 抖音 / 微信视频号 / 今日头条 / 快手：搜索「老谷拆财报」
- 固定栏目：「价值投资之财报解读」（全网连载中）
- 本 skill 的方法论与账号内容同源：数据驱动、拆开看、不讲黑话

### 扫码关注

| 微信视频号 | 抖音 |
|---|---|
| ![视频号二维码](docs/qrcode-shipinhao.jpg) | ![抖音二维码](docs/qrcode-douyin.png) |
| 扫一扫，关注视频号 | 抖音号：gubaobao22 |

> 作者声明：个人观点，仅供参考，不构成投资建议。
