# Zotero Paper to Obsidian

面向科研写作的可安装 Codex Skill：**Zotero 管理文献**，**Codex 阅读并起草结构化笔记**，**Obsidian 管理知识库**。

[English README](README.md) · [完整搭建指南](docs/zh-CN/setup.md)

## 项目介绍

当你在 Zotero 中下载或收集一篇感兴趣的论文后，可以在 Codex 中调用 `$zotero-paper-to-obsidian`。Skill 会读取条目元数据、可用 PDF 正文和已有批注，提取研究问题、方法、数据、创新点、关键证据和局限，并将 Markdown 文献笔记安全写入你的 Obsidian Vault。

它每次只处理一篇论文。若同一论文的笔记已经存在，Skill 不覆盖正文或已填写字段，只补齐空白元数据，并追加待你确认的建议更新项。

## 工具分工

| 工具 | 职责 |
|---|---|
| Zotero | 题录、PDF、批注、citation key 与 Word 正式引文的权威来源 |
| Codex | 唯一操作入口：读取论文、生成笔记、说明证据与不确定项 |
| Obsidian | 保存文献笔记、关联概念与项目、管理审阅状态 |
| Word | 正式论文写作；引用和参考文献由 Zotero 维护 |

## 核心流程

```text
Zotero 待处理分类
        ↓
Codex 读取条目 + PDF + 批注
        ↓
ai_draft 文献笔记（方法、数据、创新、证据）
        ↓
Obsidian 管理与审阅
        ↓
verified 笔记 → 证据矩阵 / 提纲 / Word 草稿
        ↓
Word + Zotero 正式写作与引文
```

## 安装

1. 安装能够访问本机 Zotero 文献库和 PDF 的 Codex Zotero 能力。
2. 将本仓库复制或克隆到本机 Codex skills 目录，目录名保持为 `zotero-paper-to-obsidian`。
3. 复制 `references/config.example.md` 为 `references/config.local.md`，填写自己的 Zotero 分类、Vault 路径与文献笔记目录。
4. 启动 Zotero 桌面端后，在 Codex 中输入：

```text
使用 $zotero-paper-to-obsidian 读取我配置的 Zotero 分类中最新且有 PDF 的论文，并写入 Obsidian。
```

首次写入时，Codex 只会请求 Obsidian 文献目录的必要权限。

## 安全边界

- 没有可读取的 PDF 时，不生成伪造的研究总结。
- 没有可靠页码、图号或表号的内容，一律标记为 `待核验`。
- 已有笔记不覆盖正文或非空字段。
- 不修改 Zotero 条目、`.obsidian`、Word 文件或正式引文域。
- `config.local.md` 含个人路径，已被 Git 忽略，不应提交。

## 文档

完整的 Zotero—Codex—Obsidian 搭建、OneDrive 同步、审阅状态、Word 衔接与排障说明，见[中文搭建指南](docs/zh-CN/setup.md)。

## 许可证

MIT，详见 [LICENSE](LICENSE)。
