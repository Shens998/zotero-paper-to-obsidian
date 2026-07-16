# Literature note schema

Use this structure for every new note. When updating an existing note, preserve all nonempty YAML values and all body text.

```yaml
---
type: literature
citekey: ""
title: ""
authors: []
year:
zotero_uri: ""
doi: ""
tags: []
method_tags: []
datasets: []
source_access: "" # fulltext / annotations / abstract / metadata
ai_reading_status: ai_draft # ai_draft / complete / failed
evidence_status: needs_audit # needs_audit / partial / verified
review_status: pending # pending / verified / rejected
ai_confidence: "" # high / medium / low
projects: []
created: YYYY-MM-DD
---
```

```markdown
# 一句话结论

## 研究问题与假设

## 方法

- 研究任务：
- 方法/模型名称：
- 输入 → 输出：
- 核心步骤或机制：
- 对比基线：
- 创新点：
- 证据强度：
- 代码/实现链接：

## 数据

| 数据集 | 作用 | 范围/样本量 | 获取链接 | 版本/许可 | 处理方式 |
|---|---|---:|---|---|---|

- 原始数据来源：
- 数据访问限制：
- 预处理与划分：
- 数据局限：

## 关键证据

- 结论：
  - 证据/原文：
  - 定位：p. __ / Fig. __ / Table. __ / 待核验
  - 可支持的论点：

## Codex 处理记录

- 可读取材料：
- 未能读取或缺失：
- 待人工核验项：
- 生成日期：YYYY-MM-DD

## 局限与可质疑之处

## 我的关联与想法
```

## Safe update

For an existing note, fill only empty metadata values that come directly from Zotero. Append, without replacing existing content:

```markdown
- 建议更新项（YYYY-MM-DD）：
  - [ ] 可补入：<new evidence or empty field>; 来源：<p./Fig./Table or 待核验>
```

Only the user may change `review_status` to `verified`.
