---
name: zotero-paper-to-obsidian
description: Read one Zotero paper and safely create or update its structured Obsidian literature note. Use when a user asks Codex to process a newly downloaded or specified Zotero paper, read its PDF and annotations, extract methods, datasets, innovations and evidence, and place the result in an Obsidian research Vault.
---

# Zotero Paper to Obsidian

Use Codex as the operational entry point. Zotero is authoritative for metadata, PDFs, annotations, citation keys, and Word citations. Obsidian is the Markdown knowledge base.

## Configure and select

1. Read `references/config.local.md`. If it does not exist, read `references/config.example.md`, ask the user for a Zotero source collection and the local Vault root, then ask them to create `config.local.md`. Do not silently use an example value.
2. Use the available Zotero capability and follow its instructions. Check its local API first. If it is unavailable, stop and give recovery steps; do not read or write the Vault.
3. If the user provides a citation key, title, or Zotero URI, resolve exactly that item. Otherwise select the newest item with an attached PDF in the configured source collection.
4. Process one paper only. If multiple items match, list them and ask the user to choose.

## Read and draft

1. Read the item metadata, original PDF text, and existing Zotero annotations. Treat annotations as supplementary evidence.
2. If no PDF is attached or text cannot be read, do not write a research summary. Report the limitation and available metadata.
3. Read [references/note-schema.md](references/note-schema.md). Extract the research question, method/model, baselines, innovation, validation, datasets, data/code links, findings, and limitations.
4. Give every key claim a reliable `p.`, `Fig.`, or `Table` location when available. Mark all other claims `待核验`; never infer a page, data link, DOI, method, or finding.

## Write safely

1. Resolve the configured `<vault>/<literature_folder>/` on this device. Verify the path before writing; do not hard-code an operating-system-specific path.
2. Name a new note `@citekey｜short-title.md`. Sanitize the title for the filesystem.
3. Search the literature folder for a matching `citekey` or `zotero_uri` before writing.
4. If no match exists, request the minimum write permission for the literature folder and create the note with `ai_reading_status: ai_draft`, `evidence_status: needs_audit`, and `review_status: pending`.
5. If a match exists, never overwrite body text or nonempty YAML values. Fill only empty metadata directly supported by Zotero, then append dated proposed additions under `## Codex 处理记录`.
6. Never modify Zotero items, `.obsidian`, Word documents, citation fields, or existing annotations.
7. If write permission is denied, save the completed note to the task output directory and report the intended Vault path. Never claim it was saved to Obsidian.

## Report

Report the selected Zotero item, materials actually read, created/updated/staged path, missing PDF/text/data fields, and every `待核验` item. State that the note is an `ai_draft` unless the user has verified it.
