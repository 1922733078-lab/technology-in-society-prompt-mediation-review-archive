# Revised-Prompt Coding Codebook

This codebook documents the six rule-based categories used to code the exposed `revised_prompt` strings in the GPT-image-2 mechanism probe. The coding is intended for auditability of visible mediation operations. It is not an intercoder-validated content analysis and should not be used as a general benchmark of model capability.

## Unit Of Analysis

- One generated record with a non-empty exposed `revised_prompt`.
- A category is marked present only when the operation is textually observable in the exposed `revised_prompt`.
- Empty, missing, or unavailable fields are not interpreted as hidden rewriting.
- Multiple categories can be marked present for the same record.

## Categories

| Category | Mark present when the revised prompt... | Do not mark present when... |
|---|---|---|
| `composition_specification` | Adds viewpoint, layout, framing, staging, placement, camera angle, or scene arrangement. | It only repeats the submitted object list without any added staging or layout detail. |
| `clean_background` | Adds a plain, clean, uncluttered, studio, tabletop, minimal, or simplified background/environment. | The background is merely implied by the original prompt or appears only in the generated image. |
| `realism_or_stylization` | Adds realism, illustration style, rendering style, lighting, photographic/artistic register, or visual polish. | The revised prompt only restates objects, colors, counts, or relations. |
| `no_text_or_negative` | Adds no-text, no-watermark, no-label, absence, avoidance, or other negative instruction. | The submitted prompt already contains a negation and the revised prompt merely preserves it without adding any new negative/no-text instruction. |
| `object_relation_clarification` | Restates or clarifies spatial relations, count relations, color-object bindings, or object-object relations. | It only lists the objects without preserving or clarifying their relation. |
| `detail_expansion` | Adds visual attributes beyond the submitted prompt, such as material, texture, surface, size, scene detail, or descriptive enrichment. | It only translates or repeats the original wording with no added visual detail. |

## Coding Rule For Metadata Absence

For Qwen-Image records in this archive, `revised_prompt` is present as a field but empty in all 60 tested records, and no `actual_prompt` or `prompt_extend` field was observed in the saved sidecars. These records are coded as `no_exposed_rewrite_observed`. This means only that no non-empty prompt-transformation trace was exposed through the tested endpoint and run. It does not prove that no internal prompt transformation occurred.

## Interpretation Boundary

The coding supports claims about exposed prompt-mediation traces. It does not measure visual semantic accuracy, artistic quality, creator preference, cultural appropriateness, or user-perceived control.
