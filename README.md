# Research Writing Samples

Three short pieces of technical writing on AI systems: a literature review, a deployment risk assessment for an LLM application, and a critical appraisal of an ML paper. Each one takes a single question and argues it with evidence, rather than summarising.

| Document | Question | Length |
|---|---|---|
| [AI-assisted development: literature review](ai-assisted-development-literature-review.pdf) | Do AI coding assistants raise *quality-adjusted* productivity, and who pays for verification? | 6 pages, 21 peer-reviewed papers |
| [RAG assistant: deployment risk assessment](rag-assistant-deployment-risk-assessment.pdf) | What can go wrong when a retrieval-augmented assistant answers over a student-writable corpus, and what actually mitigates it? | 9 pages, 12-risk register |
| [DTINet: critical appraisal](dtinet-critical-appraisal.pdf) | Do the benchmark and the wet-lab validation of a drug-target interaction model support its discovery claim? | 6 pages |

## 1. Faster Code, Deferred Costs

*Quality-adjusted productivity and the verification burden in AI-assisted software development.*

Reviews 21 peer-reviewed papers (2022 to 2026; ICSE, MSR, TOSEM, IEEE S&P, ACM CCS, USENIX Security, OOPSLA, CHI, plus field experiments from economics) and reads them as two halves of one trade: the effort of *generating* a plausible candidate is exchanged for the effort of *verifying* it.

- Productivity effects shrink as the setting becomes more realistic: from 55.8% faster on a single curated task to roughly 21 to 26% in randomised field trials, and to a 19% *slowdown* for experienced maintainers in repositories they know well (a preprint, flagged as such).
- A classification of every study by construct (speed, quality, verification effort, learning) and setting (artefact audit, lab, field) shows the central gap: **no study measures speed, defect rate and verification effort in the same developers doing the same work**, which is exactly what a claim about quality-adjusted productivity needs.
- Links the evidence to automation-complacency theory from human factors, and asks who bears the verification cost: the developers who gain most from assistance are the least equipped to check its output.

## 2. Deployment Risk Assessment and Limits of Mitigation

*An SSO-gated, bilingual (English and te reo Māori) RAG assistant over a university's course-material exports.*

A full pre-deployment analysis of a realistic LLM system:

- **Architecture and trust boundaries**: identity domain, the institution-controlled application layer (ingestion, index, orchestrator, logs) and an offshore model vendor, with a system diagram and a stakeholder map that separates *users* from *decision subjects*.
- **Risk register**: 12 risks across reliability and grounding, misuse, bias and fairness, privacy and memorisation, security, and organisational governance, each with likelihood, severity, affected stakeholders and a concrete technical or design mitigation.
- **Drill-down on indirect prompt injection** (OWASP LLM01) through a student-writable part of the corpus: mechanism, a plausible failure scenario, monitoring signals at ingest and inference, a **provenance-tiered retrieval pipeline** as the mitigation, and the residual risk that remains.
- **Limits**: why three popular alternatives (hardening the system prompt, keyword filtering, a second LLM as a guardrail classifier) are weaker than they look, and why the remaining risk is a governance question: who may write to a retrievable surface, and who signs off on ingestion.

The analysis also covers data sovereignty for Māori-language material and the jurisdictional exposure of an offshore inference endpoint.

## 3. When Does a Prediction Become a Discovery?

*A critical appraisal of DTINet (Luo et al., Nature Communications, 2017), a network-embedding model for drug-target interaction prediction.*

- Credits what is strong: a careful ablation that strips homologous proteins and similar drugs, AUPR reported alongside AUROC, and a prospective rank-order match between predicted scores and measured IC50 values.
- Shows the core problem with the headline benchmark: it was computed against a **1:1 balanced negative set** while true positives are **0.18%** of all drug-target pairs, a 278-fold inflation of prevalence that collapses a real imbalance of about 550:1. This is exactly the setting that precision-recall analysis exists to expose.
- Concludes that DTINet is a competent ranking algorithm, but that neither its benchmark design nor its validation assays can carry the pharmacological "discovery" claim built on them.

---
*Graduate coursework, shared as writing samples. Course and institution details have been removed.*
