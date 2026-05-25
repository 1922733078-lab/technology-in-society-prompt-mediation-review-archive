# Claim Boundary Notes

This note documents how the public archive supports the manuscript's bounded claims. The repository is an empirical audit archive, not a model leaderboard.

## Supported Claims

| Empirical pathway | Evidence in this archive | Supported claim |
|---|---|---|
| Local ComfyUI direct pathway | Prompt inventory, seeds, generation summaries, visual feature tables, drift tables, contact sheets, and original run reports in `original_main_run/`. | Under a bounded SD1.x-style local workflow, changing only prompt language is associated with measurable visual and structural drift relative to the English-reference pathway. |
| Local two-checkpoint robustness check | Model manifests, hashes, run manifests, image feature tables, drift tables, and reports in `local_two_checkpoint/`. | The direction of non-English drift is not limited to the original checkpoint, although magnitude and language ordering remain model-specific. |
| GPT-image-2 metadata probe | Generation manifests, sidecar-derived coding tables, operation summaries, reports, and contact sheet in `gpt_image2_expanded/`. | In this 60-image mechanism probe, every saved sidecar exposed a non-empty `revised_prompt`, and those strings contain visible mediation operations such as composition specification, relation clarification, detail expansion, clean-background simplification, realism/stylization cueing, and no-text/negative instruction. |
| Qwen-Image API metadata probe | Redacted metadata sidecars, metadata summaries, coding tables, reports, and contact sheet in `qwen_image_api_probe/`. | In this tested endpoint and run, the returned metadata exposed `orig_prompt`, but no non-empty `revised_prompt`, `actual_prompt`, or `prompt_extend` field was observed. |

## Claims Not Supported By This Archive

- A universal ranking of languages.
- A leaderboard comparison of image-generation models.
- A claim that Qwen-Image performs no internal prompt transformation.
- A claim that GPT-image-2 is generally superior to Qwen-Image.
- A formal semantic benchmark of prompt following.
- A measure of artistic quality, creator satisfaction, market access, authorship recognition, cultural value, or lived creative experience.
- A population-level estimate of multilingual user experience.

## Metric-To-Claim Boundary

The local visual metrics in this archive, including SSIM drift, pHash distance, RGB histogram distance, luminance, contrast, entropy, edge density, and colorfulness, are proxies for visual and structural change under controlled prompt conditions. They do not measure semantic correctness, artistic merit, human preference, cultural appropriateness, or user-perceived creative agency.

## Creative Equity Boundary

The manuscript uses "creative equity" in a bounded infrastructural sense: comparable ability to express intent, inspect mediation, revise production briefs, and contest transformations. The archive supports claims about these infrastructural conditions and audit trails. It does not directly measure creative equity as a lived, cultural, market, or artistic outcome.
