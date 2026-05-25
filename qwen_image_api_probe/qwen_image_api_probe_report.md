# Tested Qwen-Compatible Endpoint Mechanism Probe Report

## Scope

This is a third-platform/model-ecosystem prompt mediation probe through a tested Qwen-Image-compatible endpoint. It is not a Qwen-Image benchmark.

## Design

- Endpoint: OpenAI-compatible image endpoint. The specific endpoint URL is redacted in this public support repository.
- Model: `Qwen-Image`
- Size: `1328x1328`
- `n`: 1
- Authorization: credentials are not included; logs and sidecars are redacted.
- Prompt design: 12 representative prompt units x 5 languages = 60 requests.

## Completion

- Successful image generations: 60/60
- Failed image generations: 0
- Skipped existing: 0
- Median runtime: 11.5 seconds
- Mean runtime: 11.956 seconds

## Metadata Findings

| field | count | rate |
| --- | --- | --- |
| has_orig_prompt | 60 | 1.0 |
| has_actual_prompt | 0 | 0.0 |
| has_revised_prompt_field | 60 | 1.0 |
| has_nonempty_revised_prompt | 0 | 0.0 |
| has_prompt_extend | 0 | 0.0 |
| no_exposed_rewrite_observed | 60 | 1.0 |

The endpoint consistently returned `metadata.output.results[0].orig_prompt`, and returned a `data[0].revised_prompt` field that was empty in all generated records. No non-empty `revised_prompt`, `actual_prompt`, or `prompt_extend` field was observed in this 60-request run.

This does not imply that Qwen-Image internally lacks prompt rewriting. It means this tested OpenAI-compatible endpoint did not expose a non-empty prompt-transformation layer in the returned metadata.

## By Language

| language_name | records | has_orig_prompt | has_revised_prompt_field | has_nonempty_revised_prompt | has_actual_prompt | has_prompt_extend | no_exposed_rewrite_observed |
| --- | --- | --- | --- | --- | --- | --- | --- |
| English | 12 | 12 | 12 | 0 | 0 | 0 | 12 |
| Chinese | 12 | 12 | 12 | 0 | 0 | 0 | 12 |
| Hindi | 12 | 12 | 12 | 0 | 0 | 0 | 12 |
| Spanish | 12 | 12 | 12 | 0 | 0 | 0 | 12 |
| French | 12 | 12 | 12 | 0 | 0 | 0 | 12 |

## By Representative Prompt Unit

| prompt_id | scene_id | category | variant_type | records | has_orig_prompt | has_nonempty_revised_prompt | no_exposed_rewrite_observed |
| --- | --- | --- | --- | --- | --- | --- | --- |
| S01_base | S01 | spatial_color | base | 5 | 5 | 0 | 5 |
| S02_base | S02 | spatial_color | base | 5 | 5 | 0 | 5 |
| S03_base | S03 | spatial_color | base | 5 | 5 | 0 | 5 |
| S04_base | S04 | spatial_color | base | 5 | 5 | 0 | 5 |
| S05_base | S05 | quantity_color | base | 5 | 5 | 0 | 5 |
| S05_quantity_shift | S05 | quantity_color | quantity_shift | 5 | 5 | 0 | 5 |
| S06_base | S06 | quantity_color | base | 5 | 5 | 0 | 5 |
| S07_base | S07 | attribute_binding | base | 5 | 5 | 0 | 5 |
| S08_base | S08 | attribute_binding | base | 5 | 5 | 0 | 5 |
| S09_base | S09 | negation | base | 5 | 5 | 0 | 5 |
| S09_negation_rephrase | S09 | negation | negation_rephrase | 5 | 5 | 0 | 5 |
| S10_base | S10 | negation | base | 5 | 5 | 0 | 5 |

## Visual Check

A contact sheet was generated at `qwen_image_api_contact_sheet.png`. Light observation fields are included in `qwen_image_api_coding_table.csv`; they should be treated as a coarse contact-sheet check rather than a benchmark evaluation.

## Conservative Paper Wording

> In a third platform probe through a tested OpenAI-compatible image endpoint using model name `Qwen-Image`, we generated the same 60-request multilingual prompt set used for the GPT-image-2 mechanism probe. The tested endpoint returned successful images and exposed the submitted prompt as `orig_prompt` in response metadata, but it did not expose a non-empty rewritten prompt, `actual_prompt`, or `prompt_extend` field in this run. This contrasts with GPT-image-2, where non-empty `revised_prompt` fields were saved for every request. We interpret this only as a difference in exposed metadata and mediation observability, not as evidence that Qwen-Image internally lacks prompt rewriting.
