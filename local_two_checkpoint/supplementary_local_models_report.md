# Supplementary Local Models Report

Created: 2026-05-20T18:34:32
Run scope: `full_subset`

## Purpose

This completed supplementary experiment addresses the review risk that the original local evidence relied on a single local SD1.x-style checkpoint. It adds two ModelScope checkpoints and reuses the existing five-language prompt inventory, fixed seeds, and evaluation logic. The result should be treated as a bounded local-model robustness check, not as a universal benchmark of text-to-image systems.

## Model Downloads

| Model | ModelScope source | Local checkpoint | Size bytes | SHA256 | Status |
|---|---|---|---:|---|---|
| DreamShaper8 | `Yntec/Dreamshaper8` | `MODEL_DIR/DreamShaper8_modelscope_Yntec_dreamshaper_8.safetensors` | 2132625894 | `879db523c30d3b9017143d56705015e15a2cb5628762c11d086fed9538abd7fd` | already_present_verified |
| AbsoluteReality v1.6 | `Yntec/AbsoluteReality` | `MODEL_DIR/AbsoluteReality_v16_modelscope_Yntec.safetensors` | 2132625432 | `be1d90c4abb7bb0183f267f899f38b44112ad6ef9a757a6723514ea4e9be15dc` | downloaded_verified |

## Scope And Reproducibility

- Prompt source: `实验/多语种_完整_运行_20260520_093932/提示词数据/第1267份_多语种_提示词_清单.json`.
- Design: `12` prompt records x `5` languages x `2` seeds x `2` new local models = `240` requested images.
- Shared settings: `256x256`, `6` steps, Euler sampler, CFG `5.5`, same positive suffix and negative prompt as the original local run.
- Resume behavior: existing successful rows with valid image paths were skipped and marked in the analysis table where applicable; no existing images were deleted or overwritten intentionally.

Run command:

```bash
cd 'PROJECT_ROOT/experiments_supplementary_models_20260520_1717'
'COMFYUI_ROOT/ComfyUI-aki-v1.5/.venv-macos/bin/python' run_supplementary_local_models.py
```

## Completeness

| Model | Expected | Success | Failed or missing |
| --- | --- | --- | --- |
| absolutereality_v16 | 120 | 120 | 0 |
| dreamshaper8 | 120 | 120 | 0 |

Failure rows: `0`. Full audit: `results/full_completeness_audit.csv`; failure log: `results/failure_log.csv`.

## Per-Model / Per-Language Summary

| Model | Language | Requested | Success | Mean CLIP tokens | Mean drift to English | Mean pHash distance |
| --- | --- | --- | --- | --- | --- | --- |
| dreamshaper8 | English | 24 | 24 | 19.833 | 0.000 | 0.000 |
| dreamshaper8 | Chinese | 24 | 24 | 50.500 | 0.743 | 0.418 |
| dreamshaper8 | Hindi | 24 | 24 | 52.417 | 0.790 | 0.410 |
| dreamshaper8 | Spanish | 24 | 24 | 26.833 | 0.548 | 0.379 |
| dreamshaper8 | French | 24 | 24 | 25.583 | 0.536 | 0.354 |
| absolutereality_v16 | English | 24 | 24 | 19.833 | 0.000 | 0.000 |
| absolutereality_v16 | Chinese | 24 | 24 | 50.500 | 0.750 | 0.406 |
| absolutereality_v16 | Hindi | 24 | 24 | 52.417 | 0.788 | 0.452 |
| absolutereality_v16 | Spanish | 24 | 24 | 26.833 | 0.567 | 0.388 |
| absolutereality_v16 | French | 24 | 24 | 25.583 | 0.604 | 0.389 |

## Directional Comparison With Original Anything-v5 Matched Subset

| Model | Language | New drift | Anything-v5 matched subset | Delta | Direction |
| --- | --- | --- | --- | --- | --- |
| dreamshaper8 | English | 0.000 | 0.000 | 0.000 | similar |
| dreamshaper8 | Chinese | 0.743 | 0.726 | 0.017 | similar |
| dreamshaper8 | Hindi | 0.790 | 0.790 | 0.000 | similar |
| dreamshaper8 | Spanish | 0.548 | 0.447 | 0.100 | higher drift |
| dreamshaper8 | French | 0.536 | 0.445 | 0.091 | higher drift |
| absolutereality_v16 | English | 0.000 | 0.000 | 0.000 | similar |
| absolutereality_v16 | Chinese | 0.750 | 0.726 | 0.024 | similar |
| absolutereality_v16 | Hindi | 0.788 | 0.790 | -0.001 | similar |
| absolutereality_v16 | Spanish | 0.567 | 0.447 | 0.120 | higher drift |
| absolutereality_v16 | French | 0.604 | 0.445 | 0.159 | higher drift |

## Directional Comparison With Original Anything-v5 Full Run

This comparison is language-level and directional only because Anything-v5 used the full 44-prompt inventory while the new local-model robustness check uses the preregistered 12-prompt subset.

| Model | Language | New drift | Anything-v5 full mean | Delta | Direction |
| --- | --- | --- | --- | --- | --- |
| dreamshaper8 | English | 0.000 | 0.000 | 0.000 | similar |
| dreamshaper8 | Chinese | 0.743 | 0.732 | 0.011 | similar |
| dreamshaper8 | Hindi | 0.790 | 0.814 | -0.024 | similar |
| dreamshaper8 | Spanish | 0.548 | 0.452 | 0.096 | higher drift |
| dreamshaper8 | French | 0.536 | 0.437 | 0.099 | higher drift |
| absolutereality_v16 | English | 0.000 | 0.000 | 0.000 | similar |
| absolutereality_v16 | Chinese | 0.750 | 0.732 | 0.018 | similar |
| absolutereality_v16 | Hindi | 0.788 | 0.814 | -0.026 | similar |
| absolutereality_v16 | Spanish | 0.567 | 0.452 | 0.115 | higher drift |
| absolutereality_v16 | French | 0.604 | 0.437 | 0.167 | higher drift |

## Contact Sheet

![Full local-model contact sheet](PROJECT_ROOT/experiments_supplementary_models_20260520_1717/figures/contact_sheet_full_240.png)

## Findings

- Both new checkpoints completed without failures and reproduced non-English visual drift relative to English. Mean non-English structural drift was `0.654` for DreamShaper8 and `0.677` for AbsoluteReality.
- Against the matched Anything-v5 subset, Chinese and Hindi were similar across models, while Spanish and French showed higher drift in the two new checkpoints.
- The finding is therefore stronger than the original single-local-model evidence in direction, but model-specific in magnitude and language ranking.
- Wording for the manuscript should remain bounded: language-conditioned visual drift persisted across two additional SD1.x-style local checkpoints under the same prompt inventory and seeds, but this is not evidence for all text-to-image systems.

## Issue List

See `PROJECT_ROOT/experiments_supplementary_models_20260520_1717/FULL_local_models_issue_list.md`. Key residual limitation: this is a two-checkpoint local SD1.x robustness check with low-cost generation settings and proxy visual metrics, not a general model benchmark or human semantic evaluation.

## Key Output Files

- `PROJECT_ROOT/experiments_supplementary_models_20260520_1717/results/all_generation_eval_with_tokens.csv`
- `PROJECT_ROOT/experiments_supplementary_models_20260520_1717/results/image_features.csv`
- `PROJECT_ROOT/experiments_supplementary_models_20260520_1717/results/visual_drift_to_english.csv`
- `PROJECT_ROOT/experiments_supplementary_models_20260520_1717/results/model_language_summary.csv`
- `PROJECT_ROOT/experiments_supplementary_models_20260520_1717/results/directional_comparison_vs_original_anything_subset.csv`
- `PROJECT_ROOT/experiments_supplementary_models_20260520_1717/results/directional_comparison_vs_original_anything_full.csv`
- `PROJECT_ROOT/experiments_supplementary_models_20260520_1717/results/full_completeness_audit.csv`
- `PROJECT_ROOT/experiments_supplementary_models_20260520_1717/results/failure_log.csv`
- `PROJECT_ROOT/experiments_supplementary_models_20260520_1717/figures/contact_sheet_full_240.png`
- `PROJECT_ROOT/experiments_supplementary_models_20260520_1717/FULL_local_models_issue_list.md`
