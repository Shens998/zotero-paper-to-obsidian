# Zotero Paper to Obsidian

An installable Codex Skill for a research workflow in which **Zotero manages literature**, **Codex reads and drafts structured notes**, and **Obsidian manages the knowledge base**.

The Skill processes one Zotero paper at a time. It reads available metadata, PDF text, and annotations; creates an evidence-aware literature note; and safely writes it into an Obsidian Vault. Existing notes are never overwritten: only empty metadata may be filled, and proposed additions are appended for review.

## Roles

| Tool | Role |
|---|---|
| Zotero | Bibliographic metadata, PDFs, annotations, citation keys, and Word citations |
| Codex | The single operational entry point: reads a paper, drafts the note, and reports uncertainty |
| Obsidian | Markdown knowledge base, project links, and review queues |
| Word | Formal manuscript writing with Zotero-managed citations |

## Install

1. Install a Codex Zotero capability that can access your local Zotero library and attached PDFs.
2. Copy or clone this repository into your local Codex skills directory as `zotero-paper-to-obsidian`.
3. Copy `references/config.example.md` to `references/config.local.md` and set your Zotero source collection, Vault root, and literature folder. `config.local.md` is intentionally ignored by Git.
4. Start Zotero desktop and invoke:

```text
Use $zotero-paper-to-obsidian to read the latest PDF in my configured Zotero collection and create its Obsidian literature note.
```

Codex requests write permission only when a completed note is ready to enter your Vault.

## Safety boundaries

- No PDF text: no fabricated research summary.
- No reliable page, figure, or table location: mark the claim `待核验`.
- Existing note: preserve its body and nonempty fields.
- No edits to Zotero items, `.obsidian`, Word files, or formal citation fields.

## Documentation

For the complete Chinese setup guide—including OneDrive sync, review states, Word handoff, and troubleshooting—see [docs/zh-CN/setup.md](docs/zh-CN/setup.md).

## License

MIT. See [LICENSE](LICENSE).
