# Empirical Support Repository for a Prompt-Mediation Study

This repository provides the empirical materials that support a manuscript on multilingual prompt mediation in text-to-image systems. It is intended as a public evidence package for transparency, reproducibility, and independent inspection of the study's data-processing chain.

The repository is not a manuscript draft and does not include author-identifying files, credentials, raw authorization headers, or private endpoint details. Local machine paths have been replaced with project-relative placeholders where they are not needed for interpretation.

## Repository Structure

- `original_main_run/`: multilingual local-audit tables, prompt inventory, manual observation summaries, visual-feature tables, visual-drift tables, and figure source files.
- `local_two_checkpoint/`: supplementary local robustness check using DreamShaper8 and AbsoluteReality v1.6, including generation summaries, visual features, drift comparisons, and contact sheets.
- `gpt_image2_expanded/`: 60-image GPT-image-2 mechanism probe, including generation manifests, coding tables, language/scene/operation summaries, reports, and contact sheet.
- `qwen_image_api_probe/`: 60-image probe through a tested Qwen-Image-compatible endpoint, including redacted metadata summaries, coding tables, reports, contact sheet, and metadata sidecars with private endpoint details removed.
- `docs/`: codebook, claim-boundary notes, and schema notes that document how the manuscript maps empirical records to bounded claims.

## How the Materials Support the Manuscript

The files document the empirical basis for the manuscript's claims about prompt mediation, multilingual creative control, and metadata observability:

- Prompt inventories and generation manifests record the submitted multilingual prompts, seeds, model settings, and run structure.
- Coding tables document how revised prompts, curation operations, metadata exposure, and visual checks were coded.
- The codebook in `docs/revised_prompt_codebook.md` defines the six GPT-image-2 revised-prompt mediation categories and the rule for not inferring hidden rewriting from empty or absent fields.
- The claim-boundary note in `docs/claim_boundary_notes.md` states which conclusions are supported by each empirical pathway and which stronger interpretations are outside the evidence.
- The schema note in `docs/qwen_redacted_schema_note.md` documents the returned field hierarchy for the tested Qwen-compatible endpoint without publishing credentials or private endpoint details.
- Visual feature and drift tables provide the quantitative summaries used for cross-language comparison.
- Contact sheets allow readers to inspect representative generated images without needing to reconstruct the full local environment.
- Redacted metadata files show which prompt-transformation fields were exposed by the API responses while withholding credentials and private endpoint information.

## Scope and Limits

These materials support a mechanism-oriented sociotechnical audit. They are not a model leaderboard, a comprehensive benchmark of image quality, or a claim that any platform lacks internal prompt transformation. In particular, the tested Qwen-compatible endpoint probe documents what one OpenAI-compatible endpoint exposed in returned metadata during this controlled run.

## Qwen-Image Scope Note

The Qwen-compatible endpoint materials document exposed metadata from one OpenAI-compatible endpoint, one model name (`Qwen-Image`), one image size, and a 60-request controlled prompt set. Empty `revised_prompt` fields are evidence about metadata observability in this endpoint, not proof that no internal prompt transformation occurred in Qwen-Image or in other compatible endpoint implementations.

## Excluded or Redacted Material

API credentials, raw authorization headers, private endpoint URLs, and sensitive request material are excluded or redacted. Public tables may include project-relative placeholders such as `PROJECT_ROOT/...`; these are included only to preserve the structure of the data-processing chain.
