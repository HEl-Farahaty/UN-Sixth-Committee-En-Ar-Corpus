# UN6C v1.0 field conventions

The authoritative current correspondence layer is `data/current/`. Each JSONL object records `doc_key`, `doc_id`, `session`, `key`, `display_order_candidate`, `english_text`, `arabic_text`, source-unit arrays `en` and `ar` when known, `visible`, `source`, `correspondence_type`, and `review_status`. Baseline rows have `source=baseline_unmodified` or `baseline_edited`; inserted website rows have `source=added_current`. Fields are sparse when original source anchors or optional metadata are unavailable. A nonempty source-unit array is not guaranteed for added rows. See the release README for limitations and `metadata/REVIEW_STATUS.tsv` for document statuses.

## Translation memory

The TMX 1.4 derivative uses UTF-8, `en` and `ar` language tags, one `tu` per active bilingual website correspondence, and UN6C-specific `<prop>` metadata. Empty, excluded and monolingual records remain accessible in JSONL. Invalid XML 1.0 code points, if any, are replaced with U+FFFD in TMX only; see `metadata/TMX_EXPORT_STATS.json`.
