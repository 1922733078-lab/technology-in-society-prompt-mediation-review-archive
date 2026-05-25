# Claim Boundary Notes

This note documents how the public archive supports the manuscript's bounded claims. The repository is an empirical audit archive, not a model leaderboard.

## Supported Claims

| Empirical pathway | Evidence in this archive | Supported claim |
|---|---|---|
| Local ComfyUI direct pathway | Prompt inventory, seeds, generation summaries, visual feature tables, drift tables, contact sheets, and original run reports in `original_main_run/`. | Under a bounded SD1.x-style local workflow, changing only prompt language is associated with measurable visual and structural drift relative to the English-reference pathway. |
| Local two-checkpoint robustness check | Model manifests, hashes, run manifests, image feature tables, drift tables, and reports in `local_two_checkpoint/`. | The direction of non-English drift is not limited to the original checkpoint, although magnitude and language ordering remain model-specific. |
| GPT-image-2 metadata probe | Generation manifests, sidecar-derived coding tables, operation summaries, reports, and contact sheet in `gpt_image2_expanded/`. | In this 60-image mechanism probe, every saved sidecar exposed a non-empty `revised_prompt`, and those strings contain visible mediation operations such as composition specification, relation clarification, detail expansion, clean-background simplification, realism/stylization cueing, and no-text/negative instruction. |
| Tested Qwen-compatible endpoint metadata probe | Redacted metadata sidecars, metadata summaries, coding tables, reports, schema note, and contact sheet in `qwen_image_api_probe/` and `docs/qwen_redacted_schema_note.md`. | In this tested endpoint and run, the returned metadata exposed `orig_prompt`, but no non-empty `revised_prompt`, `actual_prompt`, or `prompt_extend` field was observed. |

## Claims Not Supported By This Archive

- A universal ranking of languages.
- A leaderboard comparison of image-generation models.
- A claim that Qwen-Image performs no internal prompt transformation.
- A claim that every Qwen-Image-compatible endpoint exposes the same metadata fields.
- A claim that GPT-image-2 is generally superior to Qwen-Image.
- A formal semantic benchmark of prompt following.
- A visual conformance score comparing GPT-image-2 and the tested Qwen-compatible endpoint.
- A measure of artistic quality, creator satisfaction, market access, authorship recognition, cultural value, or lived creative experience.
- A population-level estimate of multilingual user experience.

## Metric-To-Claim Boundary

The local visual metrics in this archive, including SSIM drift, pHash distance, RGB histogram distance, luminance, contrast, entropy, edge density, and colorfulness, are proxies for visual and structural change under controlled prompt conditions. They do not measure semantic correctness, artistic merit, human preference, cultural appropriateness, or user-perceived creative agency.

## Evidence Trace Boundary

| Evidence trace | Directly supports | Does not support |
|---|---|---|
| CLIP token counts | Relative prompt-representation length in the local SD1.x-style text-encoder pathway, including the shared English suffix. | Semantic accuracy, language quality, or a universal explanation of drift. |
| English-reference visual drift metrics | Paired visual and structural differences between each non-English output and its English-reference output under fixed prompt identifiers and seeds. | Absolute prompt correctness, aesthetic quality, cultural appropriateness, or a claim that English is inherently better. |
| Contact sheets | Material traceability that image files were produced and can be visually inspected alongside metadata. | Formal semantic conformance, human preference, or cross-system visual-performance ranking. |
| GPT-image-2 `revised_prompt` sidecars | Exposed non-empty rewritten prompts and rule-coded visible mediation operations in this 60-image probe. | Intercoder-validated content analysis, hidden safety transformations, or general GPT-image-2 superiority. |
| Tested Qwen-compatible endpoint metadata | Returned `orig_prompt`; empty `data[0].revised_prompt`; no observed `actual_prompt` or `prompt_extend` field in this run. | Absence of internal prompt transformation in Qwen-Image or in other compatible endpoints. |
| Public repository artifacts | Prompt inventories, hashes, generation logs, drift tables, sidecar summaries, coding sheets, codebooks, and figure sources. | Independent proof of every hidden production decision or population-level user experience. |

## Creative Equity Boundary

The manuscript uses "creative equity" in a bounded infrastructural sense: comparable ability to express intent, inspect mediation, revise production briefs, and contest transformations. The archive supports claims about these infrastructural conditions and audit trails. It does not directly measure creative equity as a lived, cultural, market, or artistic outcome.

## Endpoint and Model Boundary

The Qwen materials distinguish the model name submitted in the request (`Qwen-Image`), the OpenAI-compatible endpoint implementation that returned the response schema, and the saved redacted sidecar fields. The archive supports claims about returned metadata observability in this tested endpoint and run. It does not establish model-internal prompt processing or the behavior of other providers, gateways, SDKs, or future API versions.
