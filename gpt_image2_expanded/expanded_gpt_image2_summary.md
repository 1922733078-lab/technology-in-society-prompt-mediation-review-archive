# Expanded GPT-image-2 Summary

- Run directory: `PROJECT_ROOT/experiments_gpt_image2_expanded_20260520_1713`
- Design: 12 representative prompt units across five languages: 10 base scene prompts plus one quantity-shift variant and one explicit-negation variant.
- Successful or reused generations in complete set: 60/60.
- Median elapsed seconds per successful request: 29.4.
- Mean elapsed seconds per successful request: 37.9.
- Revised prompts present: 60/60.
- English-like revised prompts: 53/60.

## By Language

| language_name | records | has_revised_prompt | english_like_revised_prompts | mean_char_expansion_ratio | object_relation_clarification | negative_no_text |
| --- | --- | --- | --- | --- | --- | --- |
| English | 12 | 12 | 12 | 3.952 | 12 | 3 |
| Chinese | 12 | 12 | 9 | 11.169 | 12 | 3 |
| Hindi | 12 | 12 | 11 | 3.958 | 12 | 4 |
| Spanish | 12 | 12 | 10 | 2.669 | 12 | 5 |
| French | 12 | 12 | 11 | 2.943 | 12 | 4 |

## By Representative Prompt Unit

| prompt_id | scene_id | category | variant_type | relation | records | has_revised_prompt | english_like_revised_prompts | mean_char_expansion_ratio | object_relation_clarification | negative_no_text |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| S01_base | S01 | spatial_color | base | left_of | 5 | 5 | 4 | 5.204 | 5 | 0 |
| S02_base | S02 | spatial_color | base | right_of | 5 | 5 | 5 | 5.421 | 5 | 1 |
| S03_base | S03 | spatial_color | base | above | 5 | 5 | 4 | 5.638 | 5 | 0 |
| S04_base | S04 | spatial_color | base | below | 5 | 5 | 4 | 3.828 | 5 | 0 |
| S05_base | S05 | quantity_color | base | left_of | 5 | 5 | 5 | 6.401 | 5 | 1 |
| S05_quantity_shift | S05 | quantity_color | quantity_shift | left_of | 5 | 5 | 5 | 4.715 | 5 | 0 |
| S06_base | S06 | quantity_color | base | right_of | 5 | 5 | 5 | 4.893 | 5 | 3 |
| S07_base | S07 | attribute_binding | base | left_of | 5 | 5 | 3 | 3.66 | 5 | 0 |
| S08_base | S08 | attribute_binding | base | above | 5 | 5 | 5 | 7.008 | 5 | 0 |
| S09_base | S09 | negation | base | none | 5 | 5 | 4 | 4.274 | 5 | 5 |
| S09_negation_rephrase | S09 | negation | negation_rephrase | none | 5 | 5 | 5 | 4.836 | 5 | 4 |
| S10_base | S10 | negation | base | above | 5 | 5 | 4 | 3.379 | 5 | 5 |

## Rewriting Operation Totals

| operation | count | rate |
| --- | --- | --- |
| composition_specification | 60 | 1.0 |
| clean_background | 36 | 0.6 |
| realism_or_stylization | 58 | 0.967 |
| negative_no_text | 19 | 0.317 |
| object_relation_clarification | 60 | 1.0 |
| detail_expansion | 60 | 1.0 |
