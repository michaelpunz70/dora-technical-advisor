# Evaluation Results — DORA Technical Implementation Advisor

**Status: NOT RUN / results not supplied.** The submitted repository contained an evaluation template, blank scores, and no raw responses. No comparison, ranking, performance, completed run, or reliability claim is established by this document. Do not replace missing data with estimates.

## Candidate model inventory

The original labels and specifications are retained below for traceability. They are unverified inventory data, not confirmation that each artifact exists under this exact name, has the reported architecture, was downloaded, or can run on the project hardware. Resolve exact publisher IDs and artifact specifications before testing.

| # | Model | Organization | Parameters | Architecture | Type |
|---|---|---|---|---|---|
| 1 | Ministral 3 3B Reasoning | Mistral AI | 3B | Dense | Reasoning-optimized |
| 2 | Phi-4 Mini Reasoning | Microsoft | 3.8B | Dense | Reasoning-optimized |
| 3 | Gemma 4 E4B | Google | 8B total / 4B active | Mixture of Experts | General |
| 4 | Qwen3 8B | Alibaba | 8B | Dense | General |
| 5 | Gemma 4 12B QAT | Google | 12B | Dense (Quantization-Aware Trained) | General |
| 6 | Ministral 3 14B Reasoning | Mistral AI | 14B | Dense | Reasoning-optimized |

These six candidates represent four organisations in the inventory. Differences between models are confounded by training, artifact format, quantisation, prompt templates, and inference settings. A small convenience sample cannot isolate a causal effect of size, architecture, or reasoning training. The earlier predicted ranking was an unsupported pre-test expectation and is not a result or recommendation.

## Baseline configuration — to verify at run time

| Parameter | Documented baseline / required record |
| --- | --- |
| Hardware | MacBook Air M3, 16 GB unified memory |
| OS, AnythingLLM, LM Studio versions | Pending actual run record |
| Embedding | Built-in local embedder; exact ID/version/hash pending |
| Vector database | LanceDB; version pending |
| Mode / retrieval | Query; Top-K 6; similarity threshold 0.25 |
| Corpus | Expected 18 baseline documents; actual files, versions, digests, and chunk counts pending |
| Chunking / overlap | Pending |
| Prompt | Snapshot and digest of config/system-prompt.md used in run |
| Model artifact | Publisher ID, URL, filename, format, quantisation, digest, license |
| Generation settings | Context window, maximum output, temperature, sampling, seed if supported |
| Session policy | Fresh-session/reset policy and treatment of history |
| Reviewer | Name/role, review date, conflicts, and reference-answer review status |

## Protocol

1. Review all 30 reference answers in [test-queries.md](test-queries.md) against the current sources. Record applicability and source gaps.
2. Freeze the corpus, prompt, queries, and configuration. Give each combination a configuration ID.
3. Run all 30 cases for each candidate, retaining exact responses and retrieved context. The full single-run matrix contains **180 planned model-query cases**; none are claimed completed here.
4. Keep settings consistent where technically feasible. Record model-specific differences and failures. If repeated runs are used, declare the repetition policy before comparing results and report variability.
5. Apply the four-dimension 1–5 rubric and retain scoring rationale. Log false citations, unsupported mandates, wrong clocks, unjustified compliance claims, and omitted applicability conditions as material errors.
6. Use a second reviewer for material legal disagreements where feasible and document adjudication. This is a proposed review process, not an independent review already performed.
7. Report scored-case counts, failed/incomplete cases, per-round and per-dimension means, and material error counts. An overall mean must state its denominator and must not conceal missing cases.
8. Draw bounded conclusions for the frozen test set only. Do not infer legal certification, privacy guarantees, or production suitability.

## Summary — no measured results

| Candidate | Completed cases / 30 | Round 1 | Round 2 | Round 3 | Overall | Status |
| --- | --- | --- | --- | --- | --- | --- |
| Ministral 3 3B Reasoning | Not reported | N/A | N/A | N/A | N/A | Pending |
| Phi-4 Mini Reasoning | Not reported | N/A | N/A | N/A | N/A | Pending |
| Gemma 4 E4B | Not reported | N/A | N/A | N/A | N/A | Pending |
| Qwen3 8B | Not reported | N/A | N/A | N/A | N/A | Pending |
| Gemma 4 12B QAT | Not reported | N/A | N/A | N/A | N/A | Pending |
| Ministral 3 14B Reasoning | Not reported | N/A | N/A | N/A | N/A | Pending |

`N/A` means no measured score, not zero performance. No best model has been established.

## Detailed record template — repeat for each model, query, and repetition

- Run ID / date / configuration ID:
- Exact model artifact and prompt/corpus snapshot:
- Query ID and exact query text:
- Raw response and retrieved passages/source identifiers:
- Reference-answer review status and official provisions checked:
- Accuracy / completeness / specificity / unsupported-claim resistance: pending /5 each
- Per-answer mean and scoring rationale:
- Unsupported citations, material errors, omissions, and uncertainty handling:
- Retrieval issue / generation issue / reference-answer issue:
- Loading failures, truncation, latency, memory pressure, or other observations:
- Reviewer / adjudication / final status:

## Analysis — pending evidence

After completing the records, discuss citation support, retrieval coverage, recurring errors, results by query type, and resource constraints. Report limitations before making a use-case recommendation. Preserve failed runs and negative findings. Re-evaluate affected cases after prompt, model, corpus, or retrieval changes; never silently combine results from different configurations.
