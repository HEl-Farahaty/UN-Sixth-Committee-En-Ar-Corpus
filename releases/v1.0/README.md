# UN6C v1.0 — United Nations Sixth Committee English–Arabic Parallel Corpus

**Version:** 1.0 · **Publication snapshot:** 16 November 2026 · **Coverage:** General Assembly sessions 45–79 (1990–2024)

This is the first stable, review-inclusive dataset release of UN6C. It contains **1,957 bilingual document identities** and **276,838 active correspondence rows** reconstructed from the October 2026 integrated review website and its saved per-document SQLite revisions. Inclusion does not depend on the review-progress status.

## Which files represent the current corpus?

**Use `data/current/` for the released English–Arabic correspondence data.** This layer follows the website's source-text construction, saved row overlays, inserted row ordering, and explicit row exclusions. It is not identical to the original automatic alignment layer.

- `data/current/WEBSITE_VISIBLE_CORRESPONDENCES.jsonl.gz` (or its per-session shards under `data/current/sessions/`) contains the latest effective **visible** website correspondences in the available local snapshot, including corrected text, edited groups, unmatched passages and newly inserted records.
- `metadata/DOCUMENT_INDEX_WITH_REVIEW_STATUS.tsv` lists all documents and their effective review statuses.
- `metadata/REVIEW_STATUS.tsv` and `metadata/SESSION_STATISTICS.tsv` describe per-document and per-session coverage.

## Original source-linked representation (historical frozen layer)

`data/baseline_v16/` holds the **unchanged 12 October 2026** four-file canonical export:

- `DOCUMENT_INDEX.tsv`
- `FROZEN_ORIGINAL_UNITS.jsonl.gz`
- `FROZEN_COMPANION_LINKS.jsonl.gz`
- `PRIMARY_SELECTED_LINKS.jsonl.gz`

This original-unit and primary-link representation preserves source-level identity and provenance. **The historical selected links must not be mistaken for the current reviewer-edited alignment layer.** Updated website-only text may not be bound to frozen unit IDs.

## Scope and review interpretation

- The corpus comprises bilingual documents whose English and Arabic UN symbols and version designations match. Revisions, addenda and corrigenda remain separate document identities. One-language documents outside this admitted frame are excluded; unmatched English/Arabic passages *within* admitted bilingual documents are retained.
- All documents are included whether marked `finished`, `in_progress` or `not_reviewed`. These values describe review progress, not an independent truth or quality rating for individual alignments.
- This is a **versioned final release** (`v1.0`); it does not claim all entries have undergone independent semantic, OCR or bilingual-source adjudication.
- 71,633 visible added rows have no frozen-unit membership. They are intentionally retained as unbound website records; identifiers are not invented.
- 441 visible records have no content or unit membership. They are retained to reproduce the saved website state and must **not** be treated as usable sentence pairs.
- 61,800 explicitly excluded rows are omitted from the active website layer. The historical frozen layer remains unchanged for provenance; superseded entries in it should not be treated as the current selection.
- The latest revision database in this snapshot was saved **23 October 2026**. Changes made later on AIRE or kept only in unsaved browser drafts were not captured in this release.

## Formats and processing

`JSONL.GZ` stores UTF-8 JSON objects, preserving Arabic text and source/review metadata. TSV files are UTF-8 tabular indexes. The released row's `doc_key`, `doc_id`, `session`, `key`, `display_order_candidate`, `en`, `ar`, `english_text`, `arabic_text`, `visible`, `correspondence_type`, `source` and `review_status` fields support document-aware retrieval. Missing unit identifiers are genuinely absent; do not infer them from the text.

`metadata/PUBLICATION_MANIFEST.json` records release provenance, counts, hashes of the source snapshots, and structural QA scope. `SHA256SUMS.txt` enables download integrity verification.

The original official UN documents are the underlying provenance. See the associated corpus paper for the selection and processing methodology; follow the repository's applicable licensing terms for reuse. This release does not add a new licence to UN documents.

## TMX translation memory

The file(s) in `data/tmx/` contain the matching bilingual EN–AR text groups as TMX 1.4, with document, session, group, unit-ID (when present), and review-status properties. Large TMX files are automatically divided into individual session files. It is a **derivative** of `data/current/` and does **not** replace the JSONL release. The TMX export omits English-only, Arabic-only and empty records because they cannot form bilingual translation units; all are retained in current JSONL. Grouped 1:N/N:1 passages remain single TMX translation units. For exact source text and provenance use JSONL. See `metadata/TMX_EXPORT_STATS.json` and `metadata/TMX_SESSION_COUNTS.tsv` for counts and format limitations.
