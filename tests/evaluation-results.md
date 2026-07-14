# Evaluation Results — DORA Technical Implementation Advisor

## Test Configuration

| Parameter | Value |
|---|---|
| Hardware | MacBook Air M3, 16 GB unified memory |
| AnythingLLM version | (fill in) |
| LM Studio version | (fill in) |
| Embedding model | AnythingLLM built-in embedder |
| Vector database | LanceDB |
| Chat mode | Query |
| Top-K | 6 |
| Similarity threshold | 0.25 |
| Documents loaded | (fill in: number of documents and total chunks) |

---

## Models Evaluated

| # | Model | Organization | Parameters | Architecture | Type |
|---|---|---|---|---|---|
| 1 | Ministral 3 3B Reasoning | Mistral AI | 3B | Dense | Reasoning-optimized |
| 2 | Phi-4 Mini Reasoning | Microsoft | 3.8B | Dense | Reasoning-optimized |
| 3 | Gemma 4 E4B | Google | 8B total / 4B active | Mixture of Experts | General |
| 4 | Qwen3 8B | Alibaba | 8B | Dense | General |
| 5 | Gemma 4 12B QAT | Google | 12B | Dense (Quantization-Aware Trained) | General |
| 6 | Ministral 3 14B Reasoning | Mistral AI | 14B | Dense | Reasoning-optimized |

**Model selection rationale**: The 6 models were chosen to provide coverage across four distinct organizational ecosystems (Mistral, Google, Microsoft, Alibaba), three parameter size tiers (3–4B, 8B, 12–14B), two architecture types (dense and MoE), and both general-purpose and reasoning-optimized variants. This enables analysis of how model size, architecture, and training focus affect performance on regulatory/technical content.

---

## Hypothesis

Before testing, the expected ranking was:
1. **Ministral 3 14B Reasoning** — largest model with reasoning optimization, expected to score highest on complex cross-pillar queries
2. **Gemma 4 12B QAT** — large model with quantization-aware training, expected strong factual accuracy
3. **Qwen3 8B** — strong general-purpose model, expected good structured content handling
4. **Gemma 4 E4B** — MoE architecture with only 4B active parameters, interesting to see if MoE efficiency translates to quality
5. **Phi-4 Mini Reasoning** — small but reasoning-optimized, expected to punch above its weight on complex queries
6. **Ministral 3 3B Reasoning** — smallest model, expected baseline performance

---

## Summary Results

| Model | Parameters | R1 Avg (Factual) | R2 Avg (Technical) | R3 Avg (Cross-Pillar) | Overall Avg | Notes |
|---|---|---|---|---|---|---|
| Ministral 3 3B Reasoning | 3B | /5 | /5 | /5 | /5 | |
| Phi-4 Mini Reasoning | 3.8B | /5 | /5 | /5 | /5 | |
| Gemma 4 E4B | 4B active | /5 | /5 | /5 | /5 | |
| Qwen3 8B | 8B | /5 | /5 | /5 | /5 | |
| Gemma 4 12B QAT | 12B | /5 | /5 | /5 | /5 | |
| Ministral 3 14B Reasoning | 14B | /5 | /5 | /5 | /5 | |

---

## Detailed Results — Ministral 3 3B Reasoning

### Round 1 — Basic Factual Retrieval

**Q1: What are the 5 pillars of DORA?**
- Response: (paste response)
- Score: /5
- Notes:

**Q2: How often must the ICT risk management framework be reviewed?**
- Response: (paste response)
- Score: /5
- Notes:

**Q3: What are the 7 criteria for classifying a major incident?**
- Response: (paste response)
- Score: /5
- Notes:

**Q4: What is the deadline for the initial incident notification?**
- Response: (paste response)
- Score: /5
- Notes:

**Q5: What is TLPT and who must perform it?**
- Response: (paste response)
- Score: /5
- Notes:

**Q6: What is the Register of Information?**
- Response: (paste response)
- Score: /5
- Notes:

**Q7: How often must TLPT be performed?**
- Response: (paste response)
- Score: /5
- Notes:

**Q8: What is the minimum active testing duration for TLPT?**
- Response: (paste response)
- Score: /5
- Notes:

**Q9: Must the Blue Team know about a TLPT in advance?**
- Response: (paste response)
- Score: /5
- Notes:

**Q10: Is purple teaming mandatory in TLPT?**
- Response: (paste response)
- Score: /5
- Notes:

### Round 2 — Technical Implementation Queries

**Q11–Q20**: (same structure as above, one entry per query)

### Round 3 — Complex Cross-Pillar Queries

**Q21–Q30**: (same structure as above, one entry per query)

---

## Detailed Results — Phi-4 Mini Reasoning

(Copy the same 30-query structure — fill in after testing)

---

## Detailed Results — Gemma 4 E4B

(Copy the same 30-query structure — fill in after testing)

---

## Detailed Results — Qwen3 8B

(Copy the same 30-query structure — fill in after testing)

---

## Detailed Results — Gemma 4 12B QAT

(Copy the same 30-query structure — fill in after testing)

---

## Detailed Results — Ministral 3 14B Reasoning

(Copy the same 30-query structure — fill in after testing)

---

## Analysis and Conclusions

### Hypothesis vs. Results

(Write here whether the pre-test hypothesis was confirmed or contradicted, and why)

### Performance by Model Size

(Analyze whether larger models consistently outperformed smaller ones, or if reasoning-optimized smaller models competed with larger general-purpose ones)

### Dense vs. MoE Architecture

(Analyze whether Gemma 4 E4B's MoE architecture with only 4B active parameters performed comparably to dense models of similar or larger size)

### Reasoning-Optimized vs. General-Purpose

(Analyze whether reasoning variants — Ministral 3B/14B Reasoning, Phi-4 Mini Reasoning — outperformed general-purpose models on the complex cross-pillar queries in Round 3)

### Strengths and Weaknesses by Model

**Ministral 3 3B Reasoning:**
- Strengths: (fill in)
- Weaknesses: (fill in)

**Phi-4 Mini Reasoning:**
- Strengths: (fill in)
- Weaknesses: (fill in)

**Gemma 4 E4B:**
- Strengths: (fill in)
- Weaknesses: (fill in)

**Qwen3 8B:**
- Strengths: (fill in)
- Weaknesses: (fill in)

**Gemma 4 12B QAT:**
- Strengths: (fill in)
- Weaknesses: (fill in)

**Ministral 3 14B Reasoning:**
- Strengths: (fill in)
- Weaknesses: (fill in)

### Best Model for This Use Case

(Write your recommendation and rationale)

### Improvement Opportunities

(List specific areas where the system could be improved: additional documents, prompt tuning, chunk size adjustments, Top-K changes, etc.)
