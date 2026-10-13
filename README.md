# Paper Reading Notes

一个面向管理学与社会科学研究者的 Codex Skill：把论文从“读过并总结”转化为可以重新进入科研生产的研究资产。

它帮助你判断一篇论文是否值得精读，重建作者的研究过程，检查结论与证据的对应关系，并把真正有复用价值的内容沉淀为问题卡、证据卡、方法卡、连接卡和研究卡。

## 为什么需要这个 Skill

普通的论文摘要通常只能回答“作者做了什么”。科研阅读还需要回答：

- 作者没有回答什么？这个缺口是否值得继续追？
- 作者的结论由什么证据支持？我应该相信到什么程度？
- 这个研究设计以后还能解决什么问题？迁移需要哪些条件？
- 这篇论文与其他领域、机制或矛盾文献有什么可检验的连接？

这个 Skill 将论文阅读组织成两个阶段：先快速筛选，再对高价值论文进行完整精读。

## 核心工作流

完整阅读包括：

1. 识别论文身份、材料完整度和研究类型。
2. 判断是否值得精读，并记录主要风险。
3. 重建“已有认识 → 缺口 → 问题 → 假设/机制 → 设计 → 分析 → 结论”的研究过程。
4. 找出数据、样本、模型、对照和识别策略上的关键分叉点。
5. 将每条核心结论对应到图、表、附录或其他证据位置。
6. 生成四类科研笔记。
7. 将最有价值的缺口或连接转化为研究卡和下一步行动。

图表解读固定回答六个问题：为什么做、怎么做、怎么看、发现什么、支持到哪、为什么接下一张图。

## 四类科研笔记

| 笔记 | 核心问题 | 典型产出 |
|---|---|---|
| 问题卡 | 还有什么没有解决？ | 缺口、研究问题、支持/证伪条件 |
| 证据卡 | 我应该相信什么？ | 主张、证据位置、边界、可信度 |
| 方法卡 | 以后可以怎么研究？ | 适用问题、设计逻辑、迁移条件、常见坑 |
| 连接卡 | 新的想法从哪里长出来？ | 跨领域机制、可检验预测、下一步检索 |

研究卡进一步记录最小研究设计、关键对照、判断标准、数据需求、可行性和放弃条件。

## 证据原则

- 严格区分原文事实、作者解释、Skill 的推断和研究者的新想法。
- “显著”不自动等于重要、因果、机制成立或可推广。
- 实验、观察研究、质性研究、理论研究和方法论文使用不同的核查标准。
- 摘要、网页占位符和二手转述只能进入待读或发现队列，不能直接支撑持久化结论。
- 无法核验的内容明确标记为“未核验”，不补写缺失信息。

## 生成的 Markdown 目录

```text
Sources/Papers/
Knowledge/Questions/
Knowledge/Evidence/
Knowledge/Methods/
Knowledge/Connections/
Research-Cards/
```

卡片模板和稳定身份、重复更新规则见 [`references/note-schema.md`](references/note-schema.md)。不同研究类型的证据标准见 [`references/evidence-standards.md`](references/evidence-standards.md)。

## 安装

将整个 `paper-reading-notes` 文件夹复制到当前用户的 Codex skills 目录：

```text
Windows: %USERPROFILE%\\.codex\\skills\\paper-reading-notes
macOS/Linux: ~/.codex/skills/paper-reading-notes
```

安装后可在 Codex 中调用：

```text
使用 $paper-reading-notes 阅读这篇论文，先筛选价值，再生成四类科研笔记和研究卡。
```

如果要保存笔记，请同时指定 Markdown 根目录，例如：

```text
将可复用卡片保存到 D:\\Research\\Literature。
```

## 仓库中应提交的文件

建议提交以下文件和目录：

```text
paper-reading-notes/
├── README.md
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    ├── evidence-standards.md
    └── note-schema.md
```

不需要提交：

- `paper-reading-notes.zip`：发布包可作为 Release 附件，通常不必与源文件重复提交。
- `work/`：静态演练和临时文件。
- 用户自己的 PDF、论文全文、个人笔记和生成的 Markdown 知识库。
- Python 缓存、操作系统临时文件和编辑器配置。

## 版本与贡献

修改 `SKILL.md` 的工作流、卡片字段或证据标准时，请同步更新 `metadata.version`，并说明行为变化。新增研究类型的规则时，应同时更新 `references/evidence-standards.md` 和 README 中的说明。

提交前建议运行 Codex skill validator，确认 `SKILL.md` 的 YAML frontmatter 和目录结构有效。

## 限制

这个 Skill 负责组织阅读、证据判断和研究想法沉淀，不替代研究者对问题价值、证据可信度、方法适配性和理论连接的最终判断。它也不会把缺失的全文、图表数据或统计信息补出来。
