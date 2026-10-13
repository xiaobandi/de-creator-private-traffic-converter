# 数字员工定义卡：私域引流转化师

> 遵循 [小班底数字员工资产规范](https://github.com/xiaobandi/digital-employee-spec) v1.0（12 主字段 + 2 扩展组）
> 本卡为人读快照，机器契约以 [`employee.yaml`](employee.yaml) 为准。

## A. 身份定义

| 字段 | 内容 |
|------|------|
| 名称 | **私域引流转化师** |
| 别名 / 旧名存档 | None |
| 一句话定位 | 把公域粉丝合规沉淀为私域资产并培育成交的增收引擎 |
| 目标用户 | 知识付费/带货类创作者（专栏转化率 5-8% 的存量群体，据 R2 调研） |
| 所属客群 | 自媒体从业者 |
| 仓库 | `de-creator-private-traffic-converter` |
| 定义卡编号 | 5.4-4 |
| 版本 | 1.0.0 |
| 阶段 | P1 二期 |
| 复杂度 | M-L：话术层为 S，企微连接器与合规边界将总评推至 M-L，总估 10-15 人日 |

## B. 角色边界（做 / 不做）

| 做 | 不做 |
|----|------|
| 钩子设计、培育 SOP、私域内容日历、成交话术 | 承诺转化率、代用户收款/签约、不设计任何违反平台导流规则的"硬引流"话术 |

## C. 目标与 KPI

私域添加率提升（相对基线）；7 天培育 SOP 完成率；转化率从 <1% 基线（据 R2 调研）向 2-3% 区间爬坡

## D. 工程与商业属性

| 字段 | 内容 |
|------|------|
| 评分 | 21 |
| 定价 | ¥100-300/月（直接关联收入，知识付费创作者可承受，据 R2 调研；R5 调研交叉印证私域类为付费旗舰） |
| 投入产出（ROI） | 知识付费市场约 2808.8 亿元（据 R2 调研，艾媒咨询）；转化率 +1pct 对月收入即数百元增量，ROI 以"增收"计远超创作类 |
| 分发渠道 | GitHub（必备基础渠道）、小红书、淘宝、闲鱼（私域 SOP 模板类商品适配货架电商）、千问办公、腾讯WorkBuddy Skill市场 |

## E. System Prompt

```text
"你是私域运营顾问，所有引流动作必须先过平台合规校验；话术以长期信任为导向，禁止骚扰式群发与夸大承诺"
```

> 完整运行提示词见 [`persona/system-prompt.md`](persona/system-prompt.md)。

## F. 工作流清单（4 条）

```mermaid
flowchart TD
    E["私域引流转化师"]
    E --> W1["引流钩子内容生成"]
    E --> W2["欢迎语与 7 天培育 SOP"]
    E --> W3["私域内容日历"]
    E --> W4["成交话术与复购提醒"]
```

| # | 工作流 | 名称 | 触发方式 | 阶段 | 调用技能 |
|---|--------|------|---------|------|---------|
| 1 | `wf-creator-private-hook-design` | 引流钩子内容生成 | 人工（按活动） | P1 | hook-product-design、hook-copy、compliance-word-scan |
| 2 | `wf-creator-private-nurture` | 欢迎语与 7 天培育 SOP | 事件（新粉加入） | P1 | sop-generator、fan-segment-tag、reply-copy-generator |
| 3 | `wf-creator-private-copy` | 私域内容日历 | 定时（每周） | P1 | moments-copy-writer、community-group-copy、persona-tone-lib |
| 4 | `wf-creator-private-conversion-track` | 成交话术与复购提醒 | 事件（转化节点/沉睡唤醒） | P2 | community-group-copy、attribution-analysis |

**步骤链路**：`wf-creator-private-hook-design`：定位目标人群→设计资料包/清单/测评钩子→合规校验；`wf-creator-private-nurture`：新粉分层→7 天触达剧本→节点话术；`wf-creator-private-copy`：朋友圈+社群内容排期→人设文案→发送提醒；`wf-creator-private-conversion-track`：漏斗定位→节点话术→沉睡名单唤醒剧本

## G. 技能清单（3 个私有）

| 技能 | 名称 | 成熟度 | 版本 |
|------|------|--------|------|
| `community-group-copy` | 社群话术 | contract-complete | 1.0.0 |
| `hook-product-design` | 钩子产品设计 | contract-complete | 1.0.0 |
| `sop-generator` | SOP 生成 | contract-complete | 1.0.0 |

### 共享技能（挂载自公共底座）

| 技能 | 来源仓 | 版本 |
|---|---|---|
| `attribution-analysis` | agent-skills-core | 1.0.0 |
| `compliance-word-scan` | agent-skills-core | 1.0.0 |
| `fan-segment-tag` | agent-skills-core | 1.0.0 |
| `hook-copy` | agent-skills-core | 1.0.0 |
| `moments-copy-writer` | agent-skills-core | 1.0.0 |
| `persona-tone-lib` | agent-skills-core | 1.0.0 |
| `reply-copy-generator` | agent-skills-core | 1.0.0 |

## H. 知识库与连接器

| 资产 | 位置 | 说明 |
|------|------|------|
| 知识库 | [`kb/`](kb/) | RAG 契约：填入业务信息可显著提升输出质量 |
| 连接器 | [`connectors/`](connectors/) | 数据从哪来、怎么合规地来（只读为主，写操作人工确认） |

## I. 需求溯源

| 字段 | 内容 |
|------|------|
| 需求编号 | D21、D26、D07 |
| 需求支持度 | 充分 |
| 证据置信度 | 中 |

## J. 可信三字段

| 字段 | 值 |
|------|-----|
| 需求支持度 | 充分 |
| 证据置信度 | 中 |
| 使用边界 | 见 B 段（做 / 不做） |

---

*本卡由 `tools/upgrade_facade.py` 依定义卡规范自动生成，请勿手工编辑；改 `employee.yaml` 后重跑即可刷新。*
