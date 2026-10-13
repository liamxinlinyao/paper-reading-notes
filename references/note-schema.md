# Markdown 笔记结构与模板

## 目录

```text
Sources/Papers/
Knowledge/Questions/
Knowledge/Evidence/
Knowledge/Methods/
Knowledge/Connections/
Research-Cards/
```

## 稳定身份与通用字段

创建前，搜索现有 frontmatter 的 `citekey`、规范化 DOI（去掉 DOI URL 前缀并小写）、标题+首作者+年份。匹配同一论文时保留原 ID 和文件名，即使后来补充了 DOI/citekey。多记录冲突或不同版本结论不一致时先保留，报告歧义；不自动合并。

第一次创建时优先 citation key、其次 DOI、最后标题+首作者+年份作为 `paper_key`，ID 使用 `paper-<safe-key>`；路径非法字符替换为连字符，大小写碰撞时追加作者/年份短标识。ID 一旦分配不随阅读日期变化。子卡 ID 使用 `<paper-id>-<type>-01` 等递增序号；同一问题、主张、方法或连接更新原子卡，只有新增实质内容才分配新序号。跨论文卡同样先搜索主题和机制再创建，所有来源都保留。日期型 ID 只用于没有稳定论文身份的跨论文新卡。

使用标准 Markdown 相对链接，如 `[证据卡](../../Knowledge/Evidence/<id>.md)`；`linked_cards` 与 `related_papers` 填稳定 ID。链接指向已创建或本批次计划创建的文件，不留下虚假文件链接。

每份模板都合并下列通用字段，其中 `scope_conditions`、`related_papers` 和 `next_action` 不可省略。未知书目信息用 null 或空列表；模板中日期、ID 和枚举选择在使用时必须替换为具体值。`claim_strength` 按该卡的主张实际证据填写，不继承模板默认值。问题和连接始终为推测；证据强度在正文说明，不能用一个等级掩盖冲突证据。

```yaml
type: paper | question | evidence | method | connection | research-card
id: PRN-YYYYMMDD-slug-NN
title: ""
source: ""
paper_key: ""
source_type: full_paper | preprint | abstract_only | project_note | other
source_anchors: []
citekey: ""
doi: ""
authors: []
year: null
research_type: experimental | observational | qualitative | theory | method | review | other
claim_strength: speculative | observed | supported | strong
status: inbox | screened | deep_read | active | archived
related_papers: []
linked_cards: []
scope_conditions: []
next_action: ""
updated: YYYY-MM-DD
```

## 论文阅读卡：`Sources/Papers/<stable-id>.md`

```markdown
---
type: paper
id: PRN-YYYYMMDD-paper-NN
title: ""
source: ""
citekey: ""
doi: ""
authors: []
year: null
research_type: ""
claim_strength: observed
status: screened
related_papers: []
linked_cards: []
next_action: ""
updated: YYYY-MM-DD
---

## 快速筛选
- 是否精读：yes | maybe | no
- 相关性：
- 材料完整度：
- 主要风险：

## 研究过程
- 已有认识：
- 缺口：
- 研究问题：
- 假设/命题/机制：
- 设计与数据：
- 分析：
- 结论：

## 关键分叉点
| 选择 | 原文理由 | 可行替代 | 可能改变的结论 | 证据位置 |
|---|---|---|---|---|

## 证据地图
| 作者结论 | 图/表/章节 | 实际支持范围 | 条件与限制 | 可信度 |
|---|---|---|---|---|

## 图表解读
### Figure/Table 1
- 为什么做：
- 怎么做：
- 怎么看：
- 发现什么：
- 支持到哪：
- 为什么接下一张图：

## 关联卡片
- 问题卡：
- 证据卡：
- 方法卡：
- 连接卡：

## 未核验与后续
- 未核验：
- 下一步：
```

## 四类卡片

### 问题卡：`Knowledge/Questions/<id>.md`

```markdown
---
type: question
id: PRN-YYYYMMDD-question-NN
title: ""
source: ""
claim_strength: speculative
status: active
next_action: ""
updated: YYYY-MM-DD
---

## 作者回答了什么
## 作者没有回答什么
## 为什么值得继续追
## 最小可回答问题
## 支持条件
## 证伪条件
## 下一步行动与决策
```

### 证据卡：`Knowledge/Evidence/<id>.md`

```markdown
---
type: evidence
id: PRN-YYYYMMDD-evidence-NN
title: ""
source: ""
claim_strength: observed
status: active
updated: YYYY-MM-DD
---

## 作者声称什么
## 证据与位置
## 样本、场景、比较、效应与不确定性
## 实际支持边界
## 反向或缺失证据
## 我信到什么程度
## 禁止使用的更强表述
```

### 方法卡：`Knowledge/Methods/<id>.md`

```markdown
---
type: method
id: PRN-YYYYMMDD-method-NN
title: ""
source: ""
claim_strength: speculative
status: active
updated: YYYY-MM-DD
---

## 适合什么问题
## 识别或解释逻辑
## 优势与常见坑
## 关键参数
## 迁移前提
## 所需资源
## 验证方法
```

### 连接卡：`Knowledge/Connections/<id>.md`

```markdown
---
type: connection
id: PRN-YYYYMMDD-connection-NN
title: ""
source: ""
claim_strength: speculative
status: active
updated: YYYY-MM-DD
---

## 触发连接的原文事实
## A 到 B 的机制映射
## 可检验预测
## 可能失败的条件
## 需要连接的文献
## 下一步检索词
```

连接始终标为推断或假设。

## 研究卡：`Research-Cards/<id>.md`

```markdown
---
type: research-card
id: PRN-YYYYMMDD-research-NN
title: ""
source: ""
claim_strength: speculative
status: active
decision: explore
updated: YYYY-MM-DD
---

## 问题
## 假设或机制
## 最小研究设计
## 关键对照
## 判断标准
## 所需数据与资源
## 可行性与风险
## 支持条件
## 证伪/放弃条件
## 下一步行动
```
