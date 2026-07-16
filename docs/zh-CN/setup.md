# Zotero—Codex—Obsidian 科研个人知识库搭建指南

## 1. 适用场景与工具分工

本工作流适合以 Word 撰写论文、希望让 Codex 初读文献并将知识沉淀到 Obsidian 的研究者。

| 工具 | 职责 |
|---|---|
| Zotero | 题录、PDF、批注、citation key、Word 正式引文 |
| Codex | 唯一操作入口：读论文、生成结构化笔记、列出证据与不确定项 |
| Obsidian | 笔记、概念关联、项目组织、Dataview 审阅索引 |
| Word | 正式论文；引用和参考文献由 Zotero 插件维护 |

## 2. 工作流图

```text
Zotero 待处理分类 → Codex 读取条目、PDF 与批注 → ai_draft 文献笔记
→ Obsidian 管理、关联与审阅 → verified 笔记 → Codex 证据矩阵/提纲
→ Word + Zotero 完成正式写作与引文
```

## 3. 前置条件与隐私边界

准备 Zotero 桌面端、Codex、Obsidian，以及一个本地可访问的 Obsidian Vault。Zotero 需要允许本机应用通信，待处理条目应有可读取 PDF。

不要把 Zotero 数据库、PDF、Vault、个人 API token 或 `config.local.md` 上传到公开仓库。Skill 只在需要写入笔记时请求 Vault 文献目录权限。

## 4. Zotero 准备

1. 建立一个待处理分类，例如“待 Codex 阅读”。
2. 下载或附加每篇论文的 PDF，并核对题录、DOI 与作者信息。
3. 可在 Zotero 中做批注；Codex 将其作为补充证据，仍以原始 PDF 为主。
4. 保持 Zotero 桌面端运行，并确认你安装的 Codex Zotero 能力可以访问本机库和 PDF。

## 5. Obsidian Vault 与 OneDrive 同步

建议在 Vault 建立 `10_Literature/` 作为自动生成文献笔记目录。可用 OneDrive 在 macOS 和 Windows 同步，但不要在两台设备上同时编辑同一笔记；切换前等待同步完成并处理冲突副本。

不要将 Zotero 数据库或 PDF 附件放入 Vault。Zotero 保持文献源，Obsidian 仅保存 Markdown 笔记和可回溯信息。

## 6. 安装并配置 Codex Skill

1. 将本仓库放到本机 Codex skills 目录，目录名保持为 `zotero-paper-to-obsidian`。
2. 将 `references/config.example.md` 复制为 `references/config.local.md`。
3. 写入你自己的 Zotero 分类名、本机 Vault 根目录与文献目录。该文件已被 `.gitignore` 忽略。
4. 在另一台电脑重复上述配置；两台电脑的 Vault 路径可以不同。

## 7. 首次运行与输出字段

打开 Zotero 后，在 Codex 中输入：

```text
使用 $zotero-paper-to-obsidian 读取我配置的 Zotero 分类中最新且有 PDF 的论文，并写入 Obsidian。
```

也可提供 citation key、标题或 Zotero URI 来指定论文。笔记包含研究问题、方法/模型、对比基线、创新点、数据集及数据链接、关键证据、局限和“我的关联与想法”。没有可靠页码、图号或表号的内容必须标为 `待核验`。

## 8. 审阅状态与论文写作衔接

- `ai_draft`：Codex 已完成初读，尚未人工确认。
- `needs_audit`：存在缺页码、缺数据链接、PDF 读取不完整或关键结论待审的情况。
- `verified`：你已审阅，可用于支撑正式论文论断。

只让 Codex 用 `verified` 笔记形成正式论证。Word 中仍通过 Zotero 的 Add/Edit Citation 和 Refresh 管理引文与参考文献；不要让 Obsidian 维护第二套正式引用。

## 9. 常见问题与排障

**Codex 无法读取 Zotero**：确认 Zotero 已启动、允许本机应用通信，且本地 API 没有被防火墙、代理或端口冲突阻断。

**没有生成笔记**：检查条目是否有 PDF、PDF 是否可以提取文字，以及 `config.local.md` 中的 Vault 路径和文献目录是否正确。

**已有笔记被重复处理**：Skill 不应覆盖正文；它只补齐空白题录字段，并在“Codex 处理记录”追加建议更新项。若发现不同表现，停止写入并检查 citekey 与 Zotero URI。

**OneDrive 冲突**：停止在另一设备编辑，等待同步完成后比较冲突副本，再决定保留内容。

## 10. 跨 macOS/Windows 使用

每台电脑都需要安装 Codex Skill、可用的 Zotero 能力和自己的 `config.local.md`。通过 OneDrive 同步 Vault 内容，而不是同步 Zotero 数据库或 Skill 的本机配置。这样可保持文献、知识库和正式写作职责清晰分离。
