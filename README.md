# Paper Reading Notes

English | [CHN](README.zh-CN.md)

An OpenAI Codex Skill for management and social-science researchers. It turns academic papers from “read and summarize” tasks into reusable research assets.

The skill helps you decide whether a paper deserves deep reading, reconstruct the author’s research process, audit claims against evidence, and preserve reusable content as question, evidence, method, connection, and research cards.

## Why use this skill?

A conventional summary usually answers only “What did the authors do?” Research reading also needs to answer:

- What did the paper leave unresolved, and is the gap worth pursuing?
- What evidence supports each claim, and how strongly should I believe it?
- What can I reuse from the research design, and what would transfer require?
- What testable connection does this paper create with another field, mechanism, or conflicting finding?

The skill uses two stages: screen first, then deep-read papers that have clear research value.

## Core workflow

A full reading includes:

1. Identify the paper, source completeness, and research type.
2. Decide whether the paper deserves deep reading and record the main risks.
3. Reconstruct the chain: prior knowledge → gap → question → hypothesis/mechanism → design → analysis → conclusion.
4. Identify decision points involving data, samples, models, controls, and identification strategies.
5. Map each core claim to the relevant figure, table, appendix, or other evidence.
6. Generate four types of research notes.
7. Turn the most valuable gap or connection into a research card and next action.

For every important figure or table, answer six questions: Why was it created? How was it created? How should it be read? What does it find? What does it support? Why does the next figure follow?

## Four research-note types

| Note            | Core question                     | Typical output                                                 |
| --------------- | --------------------------------- | -------------------------------------------------------------- |
| Question card   | What remains unresolved?          | Gap, research question, support/falsification conditions       |
| Evidence card   | What should I believe?            | Claim, evidence location, scope, confidence                    |
| Method card     | How could I study this later?     | Suitable problems, design logic, transfer conditions, pitfalls |
| Connection card | Where could a new idea come from? | Cross-field mechanism, testable prediction, search terms       |

A research card adds the minimum design, key comparison, decision rule, data needs, feasibility, and stopping conditions.

## Evidence principles

- Keep original facts, author interpretations, skill inferences, and researcher ideas separate.
- Statistical significance does not automatically imply practical importance, causality, mechanism, or generalizability.
- Use different checks for experiments, observational studies, qualitative studies, theory papers, and methods papers.
- Abstracts, webpage placeholders, and second-hand summaries may enter a reading queue, but cannot directly support durable knowledge claims.
- Mark unavailable or unchecked information as `unverified`; never fill in missing evidence.

## Markdown knowledge structure

```text
Sources/Papers/
Knowledge/Questions/
Knowledge/Evidence/
Knowledge/Methods/
Knowledge/Connections/
Research-Cards/
```

See [`references/note-schema.md`](references/note-schema.md) for card templates, stable identities, and update rules. See [`references/evidence-standards.md`](references/evidence-standards.md) for research-type-specific evidence standards.

## Installation

Copy the entire `paper-reading-notes` directory into the current user’s Codex skills directory:

```text
Windows: %USERPROFILE%\\.codex\\skills\\paper-reading-notes
macOS/Linux: ~/.codex/skills/paper-reading-notes
```

Then invoke it in Codex:

```text
Use $paper-reading-notes to read this paper. Screen it first, then generate the four research-note types and a research card.
```

If you want files saved, provide a Markdown root directory:

```text
Save reusable cards under D:\\Research\\Literature.
```

## Files to publish

Recommended repository layout:

```text
paper-reading-notes/
├── README.md
├── README.en.md
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    ├── evidence-standards.md
    └── note-schema.md
```

Do not commit user PDFs, private notes, generated knowledge bases, temporary work files, Python caches, or editor settings. The ZIP archive can be attached to a GitHub Release, but does not need to be duplicated in the source tree.

## Versioning and contributions

When changing the workflow, card fields, or evidence standards, update `metadata.version` in `SKILL.md` and describe the behavior change. When adding a research type, update both `references/evidence-standards.md` and this README.

Before publishing, run the Codex skill validator to verify the frontmatter and directory structure.

## Limitations

This skill organizes reading, evidence judgment, and idea development. It does not replace the researcher’s final judgment about problem value, evidence quality, method fit, or theoretical connections. It also does not invent missing full text, figures, data, or statistics.
