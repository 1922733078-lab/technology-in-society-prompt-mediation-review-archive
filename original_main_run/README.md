# Original Multilingual Audit Materials

This directory contains the data tables and figure sources needed to reproduce the manuscript's original multilingual local-audit summaries.

- Multilingual prompt manifest and per-language prompt files.
- Local ComfyUI generation records, visual feature tables, and visual-drift tables.
- Token-suffix sensitivity tables that recount submitted prompts before the shared English quality suffix is appended.
- GPT-image-2 probe observation, revised-prompt, and curation-coding tables.
- Figure source files used in the manuscript.

Local machine paths and author-identifying filesystem prefixes have been replaced with `REDACTED_PROJECT_ROOT/`. API credentials and sensitive endpoint metadata are not included.

The token-suffix sensitivity files are tokenizer-only diagnostics. They quantify how much the shared English suffix contributes to the SD1.x CLIP token budget, but they are not image-generation records and should not be interpreted as evidence about without-suffix visual drift.
