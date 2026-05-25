# Full Local Models Issue List

- No unrecovered generation failures: `0/240` failed or missing.
- The experiment remains SD1.x-style and local-checkpoint-specific; it reduces but does not eliminate model-generalization risk.
- Outputs use CPU fallback at `256x256`, `6` Euler steps, so image quality is intentionally low-cost and should be framed as robustness evidence rather than production-quality model assessment.
- The visual drift metrics are low-level structural/perceptual proxies; they do not replace semantic object-level scoring or human evaluation.
- Anything-v5 full-run comparison uses the original 44-prompt inventory, while the new local-model comparison uses a 12-prompt preregistered subset; the full-run comparison is directional, not a matched-prompt statistical test.
- Some DreamShaper8 rows were reused from the earlier partial full run via image-path validation; reused rows are marked with `resume_reused_existing` in `results/all_generation_eval_with_tokens.csv`.
