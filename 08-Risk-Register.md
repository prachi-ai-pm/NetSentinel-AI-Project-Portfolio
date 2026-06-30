# Risk Register

**NetSentinel AI — Predictive Network Incident Management & Auto-Remediation Platform**

> A deeper, risk-specific treatment of the items also tracked in the [RAID Log](./07-RAID-Log.md). Scored for likelihood and impact, with mitigation and the actual burn-down outcome. See the [README](./README.md) for full project context.

---

## Risk Scoring Key

**Likelihood / Impact:** Low, Medium, High
**Risk Rating:** Low / Medium / High / Critical, derived from likelihood × impact

---

## Register

| ID | Risk Description | Category | Likelihood | Impact | Rating | Mitigation | Owner | Status |
|---|---|---|---|---|---|---|---|---|
| R1 | Historical incident data inconsistently labelled — free-text root-cause fields with no standard taxonomy | Data Quality | High | High | **Critical** | Dedicated joint data-cleansing sprint with NOC SMEs (Weeks 4–6) to standardise categories before any feature engineering began, rather than discovering the gap mid-build | Data Scientist | Closed — mitigated in Planning/Execution, confirmed closed at pilot |
| R2 | Legacy branch switches (6 of them) lack telemetry export capability, creating monitoring blind spots in exactly the locations most likely to fail | Infrastructure / Data Coverage | Medium | Medium | **Medium** | Firmware upgrade scoped into the plan via CR-02, rather than silently excluding the affected branches; explicit fallback agreed (exclude and flag, don't shrink silently, if the upgrade slipped) | Network Architect | Closed — firmware upgrade completed, branches included in scope |
| R3 | NOC resistance or low trust in automated predictions, given a prior negative experience with a vendor tool | Human-AI Interaction / Adoption | High | High | **Critical** | Predict-and-ticket only design (no auto-remediation); NOC given a genuine "R" on UAT sign-off, not just informed; transparent confidence scores shown on every prediction | NOC Lead | Substantially reduced — UAT sign-off achieved, feedback loop in active use; NOC requesting expansion by closure |
| R4 | Model false-positive rate erodes NOC trust post-launch, even after a successful pilot | Model Risk | Medium | High | **High** | Conservative confidence threshold at launch to limit prediction volume to higher-confidence cases; weekly precision/recall review built into hypercare | Data Scientist | Open and ongoing by design — carried into hypercare with a structured monitoring cadence, not treated as a one-time fix |
| R5 | Cisco DNA Center API rate limits constrain real-time scoring, undermining the prediction-latency assumption in the original plan | Technical / Architecture | Medium | Medium | **Medium** | Switched to 5-minute batch scoring after Week 2 rate-limit testing showed real-time streaming wasn't viable; later tuned to 2-minute batches via CR-04 once pilot feedback called for tighter latency | Network Architect | Closed — batch scoring in production, tuned post-pilot |
| R6 | Data residency or compliance objection to cloud ML compute, given the banking regulatory environment | Regulatory / Compliance | Low | High | **Medium-High** | In-region Azure ML workspace used from the outset; Security & Compliance sign-off obtained at the planning gate, before architecture commitments were locked in | PM | Closed — pre-cleared at planning, no late-stage blocker |
| R7 | Scope creep — pressure to extend the model to endpoints, applications, or adjacent networks (e.g. ATM) | Scope / Governance | Medium | Medium | **Medium** | Out-of-scope list reconfirmed at every steering review; any extension required a formal change request rather than informal absorption | PM | Managed — CR-03 (ATM extension) deferred and logged as a Phase 2 candidate; no uncontrolled scope change occurred |
| R8 | Key data scientist attrition mid-program, given only two data scientists on the build | Resourcing | Low | High | **Medium-High** | Pipeline knowledge documented in a shared runbook; second data scientist cross-trained so no single point of failure existed | PM | Mitigated — no attrition occurred, but mitigation was in place regardless |

---

## Risk Heat Summary

| Rating | Count | Risk IDs |
|---|---|---|
| **Critical** | 2 | R1, R3 |
| **High** | 1 | R4 |
| **Medium-High** | 2 | R6, R8 |
| **Medium** | 3 | R2, R5, R7 |

---

## Risk Burn-Down

| Risk | Status at Mid-Program | Status at Pilot Close |
|---|---|---|
| R1 — Data labelling inconsistency | Mitigated (cleansing sprint completed) | Closed |
| R2 — Legacy switch telemetry gap | In progress (firmware upgrade underway) | Closed (CR-02 implemented) |
| R3 — NOC trust/adoption | Active (monitoring sentiment in weekly sessions) | Substantially reduced — NOC UAT sign-off achieved, feedback loop in use |
| R4 — Model false-positive drift | Active | Open, monitored — carried into hypercare with weekly precision/recall review |
| R5 — API rate limits | Mitigated (batch scoring at 5 min, later 2 min) | Closed |
| R7 — Scope creep | Active (CR-03 deferred) | Managed — no uncontrolled scope changes occurred |

The risk register was treated as a living, reviewed-every-gate document rather than a one-time planning artifact — this burn-down table is the direct evidence of that discipline, and was used to give the Steering Committee an evidence-based rather than anecdotal basis for the rollout go/no-go decision.

---

## What This Register Demonstrates

The two **Critical**-rated risks on this program — **data quality (R1)** and **NOC adoption (R3)** — are not the risks a purely technical view of an AI/ML program would prioritize first; a technical lens tends to weight model architecture and infrastructure risk most heavily. On this program, both were identified early (at Charter and Planning) and treated with mitigation effort proportional to their rating rather than their technical glamour:

- R1 received a dedicated, scheduled sprint rather than being absorbed into general data engineering time — a direct response to the rating, not an afterthought.
- R3 shaped a structural decision (the NOC's genuine "R" on UAT sign-off) rather than being addressed only through communication — see the [Stakeholder Register](./05-Stakeholder-Register.md) for the full reasoning.

R4 (false-positive drift) is the one risk deliberately left **open and ongoing by design** rather than closed at program end — a model's behavior in live production cannot be fully validated before go-live, and the weekly hypercare review exists specifically because this risk doesn't have a one-time fix.

---

*Part of the [NetSentinel AI](./README.md) case study by Prachi Sharma.*
