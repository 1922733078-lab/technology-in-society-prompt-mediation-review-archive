# Tested Qwen-Compatible Endpoint Redacted Schema Note

This note documents the schema-level evidence used for the manuscript's Qwen-compatible endpoint metadata claim. It is a field-hierarchy note, not a benchmark of Qwen-Image model capability.

## Scope

- Probe size: 60 requests.
- Prompt design: 12 controlled prompt units x 5 languages.
- Submitted model name: `Qwen-Image`.
- Endpoint type: OpenAI-compatible image-generation endpoint.
- Image size: `1328x1328`.
- `n`: 1.
- Endpoint URL, credentials, authorization headers, cookies, and sensitive request material are redacted or excluded.

## Representative Returned Field Hierarchy

The redacted sidecars preserve the fields needed to audit returned prompt-metadata observability:

| Response component | Observed field | Status in this run | Interpretation |
|---|---|---|---|
| Request configuration | `model`, `size`, `n` | Model name `Qwen-Image`; size `1328x1328`; `n = 1`. | Documents the tested endpoint configuration. |
| Image data entry | `data[0].revised_prompt` | Field present but empty in 60/60 records. | Empty returned field; not evidence of absent internal rewriting. |
| Metadata result entry | `metadata.output.results[0].orig_prompt` | Present in 60/60 records. | Submitted prompt was exposed in returned metadata. |
| Alternative transformation fields | `actual_prompt`, `prompt_extend` | Not observed in saved records. | No additional non-empty transformation trace was available through this schema. |
| Request identifiers and URLs | request IDs, task IDs, temporary URLs | Retained only in redacted or non-secret form where needed for audit structure. | Supports traceability without publishing credentials or private endpoint details. |

## Interpretation Boundary

The saved records support the claim that this tested endpoint and run exposed submitted prompts but did not expose a non-empty prompt-transformation field. They do not prove that Qwen-Image performs no internal prompt transformation, and they do not establish the behavior of other Qwen-compatible providers, gateways, SDKs, or future API versions.

## Related Files

- `qwen_image_api_probe/qwen_image_api_metadata_summary.csv`
- `qwen_image_api_probe/qwen_image_api_coding_table.csv`
- `qwen_image_api_probe/qwen_image_api_probe_report.md`
- `qwen_image_api_probe/metadata_redacted/*.json`
