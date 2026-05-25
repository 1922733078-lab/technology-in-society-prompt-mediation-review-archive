# Expanded GPT-image-2 Mechanism Probe Report

## Purpose

This supplementary run addresses the methodological risk that a small GPT-image-2 evidence set would be too limited to support even a mechanism-level claim. The completed set is still not a GPT-image-2 capability benchmark. It is used only to examine whether submitted multilingual prompts are mediated by the API/model-side `revised_prompt` layer before image synthesis.

## Inputs and Design

- Project directory: `PROJECT_ROOT`
- Source inventory: `PROJECT_ROOT/实验/多语种_完整_运行_20260520_093932/提示词数据/第1267份_多语种_提示词_清单.json`
- Reference-only prior 12-image probe: `PROJECT_ROOT/实验/图像二号_多语种_探测_20260520_100011_资料/`
- Generation script: `SKILL_ROOT/gpt-image-2-codexcs/scripts/codexcs_gpt_image_2.py`
- Model: `gpt-image-2`
- Size / quality: `1024x1024`, `medium`
- Output directory: `PROJECT_ROOT/experiments_gpt_image2_expanded_20260520_1713/`

The source inventory contains 10 scene IDs and 44 prompt variants. To create a 12-unit representative expansion without wasting repeat calls, the completed design uses all 10 base scene prompts plus two variant prompts that represent quantity shift and explicit negation rephrasing:

`S01_base`, `S02_base`, `S03_base`, `S04_base`, `S05_base`, `S05_quantity_shift`, `S06_base`, `S07_base`, `S08_base`, `S09_base`, `S09_negation_rephrase`, and `S10_base`.

Each prompt unit is generated in five languages: English, Chinese, Hindi, Spanish, and French. This yields a complete 60-image set. The earlier 40-image expansion was reused, and only the missing 20 images were newly generated.

## Completion and Failures

- Complete set size: 60 PNG images + 60 sidecar JSON files
- Previously generated and reused: 40
- Newly generated in this completion pass: 20
- New-generation failures: 0
- New-generation retries: 0
- `generation_status.csv` rows: 60 (`success` = 20, `skipped_existing` = 40, `failed` = 0)
- Longest newly generated request: `S05_quantity_shift_en`, 57.3 seconds
- API key logging: no key was printed or stored in outputs

Every sidecar JSON preserves the submitted prompt, `revised_prompt`, language, scene ID, prompt ID, generation time, output filename, expected object metadata, and request settings.

## Prompt-Rewriting Coding

| Measure | Count | Rate |
| --- | ---: | ---: |
| Revised prompt present | 60/60 | 1.000 |
| Revised prompt English-like | 53/60 | 0.883 |
| Composition specification | 60/60 | 1.000 |
| Clean/background instruction | 36/60 | 0.600 |
| Realism or stylization instruction | 58/60 | 0.967 |
| No-text or negative instruction | 19/60 | 0.317 |
| Object-relation clarification | 60/60 | 1.000 |
| Detail expansion | 60/60 | 1.000 |

The sidecar evidence supports the narrower mediation claim: submitted prompts were not passed through as bare text. They were consistently rewritten into more explicit scene instructions, with relation clarification, detail expansion, and frequent composition/background/style specifications. The rewritten prompts were often English-like, but not always; several Chinese, Hindi, Spanish, and French cases preserved or mixed the submitted language while still adding scene-planning instructions.

## Material Traceability Check

The contact sheet is retained as a material traceability check, not as a formal semantic benchmark. It shows that the sidecar metadata belonged to completed image-generation requests and lets readers inspect representative files. The manuscript does not use this sheet to report an API-side visual conformance rate or to compare GPT-image-2 visually against the tested Qwen-compatible endpoint.

One retained note concerns `S10_base_es`: the file contains the red umbrella, brown bench, and no car, but the umbrella rests against/over the bench rather than forming a clean "above" relation. This observation is retained as a material inspection note only; no aggregate visual score is reported.

## Representative Cases

1. `S01_base_hi`
   - Submitted: Hindi prompt for a red cup to the left of a blue book.
   - Revised prompt remains Hindi and adds a simple scene, clean background, realistic style, and clear object visibility.
   - Interpretation: prompt mediation is not limited to English translation; same-language enrichment also appears.

2. `S05_quantity_shift_zh`
   - Submitted: Chinese prompt for one red apple to the left of one green pear.
   - Revised prompt expands the short quantity relation into a clean still-life instruction.
   - Interpretation: the rewriting layer clarifies both count and object relation.

3. `S09_negation_rephrase_en`
   - Submitted: `Do not draw a bird; keep only the blue ship and the yellow sun.`
   - Revised prompt explicitly removes bird-like elements and keeps only the blue ship and yellow sun.
   - Interpretation: negative constraints are mediated into a more operational exclusion instruction.

4. `S10_base_es`
   - Submitted: Spanish prompt for a red umbrella above a brown bench, with no car.
   - Revised prompt specifies an outdoor realistic scene with no car and clear composition.
   - Visual note: absence is satisfied, but the spatial relation is partial. This illustrates why the contact sheet is not used as a formal semantic benchmark.

## Conservative Manuscript Wording

Suggested paragraph:

> To address the limited scale of the initial GPT-image-2 probe, we expanded the mechanism probe to 60 images: 12 representative prompt units from the original multilingual prompt inventory, each generated in English, Chinese, Hindi, Spanish, and French. The 12 units cover all 10 base scene IDs and add quantity-shift and explicit-negation variants. We do not interpret this as a general GPT-image-2 capability benchmark. Instead, we use the saved sidecar metadata to examine whether submitted prompts are mediated by an API/model-side rewriting layer before image synthesis. All 60 requests had a saved `revised_prompt`; the revised prompts consistently added relation clarification and scene/detail expansion, and frequently added composition, background, and style specifications. The contact sheet is used only as a material traceability check for completed image requests. These findings support the narrower claim that prompt rewriting functions as a mediation layer in this workflow, while broader claims about GPT-image-2 multilingual capability remain outside the scope of this study.

Suggested limitation sentence:

> The expanded GPT-image-2 sample is used only as a mechanism probe for prompt rewriting and should not be interpreted as a model-level performance evaluation or a cross-system benchmark.

## Output Files

- `generation_manifest.json` / `generation_manifest.csv`: complete 60-request design.
- `generation_status.csv`: 20 newly generated successes, 40 reused existing records, and 0 failures.
- `images/*.png`: 60 generated images.
- `images/*.json`: 60 augmented sidecar metadata files.
- `expanded_gpt_image2_coding_table.csv`: row-level revised-prompt coding and light observation fields.
- `expanded_gpt_image2_language_summary.csv`: language-level summary.
- `expanded_gpt_image2_scene_summary.csv`: representative prompt-unit summary.
- `expanded_gpt_image2_operation_summary.csv`: rewriting-operation frequency table.
- `expanded_gpt_image2_contact_sheet.png`: 12-by-5 visual contact sheet.
- `expanded_gpt_image2_summary.md`: short machine-readable summary.
