# RAID Log

**NetSentinel AI — Predictive Network Incident Management & Auto-Remediation Platform**

> RAID = Risks, Assumptions, Issues, Dependencies (and Changes, tracked separately below). Entries span Initiation through Monitoring & Control. See the [README](./README.md) for full project context and the [Stakeholder Register](./05-Stakeholder-Register.md) for the RACI behind each owner listed here.

---

## Risks

| ID | Description | Phase Raised | Owner | Status |
|---|---|---|---|---|
| R1 | Historical incident data inconsistently labelled (free-text root cause fields) | Charter / Planning | Data Scientist | Mitigated — joint data-cleansing sprint with NOC SMEs; closed at pilot |
| R2 | Legacy branch switches lack telemetry export capability | Charter / Planning | Network Architect | Closed — firmware upgrade for 6 branches approved via CR-02 |
| R3 | NOC resistance/low trust in automated predictions | Charter | NOC Lead | Substantially reduced — NOC UAT sign-off achieved; feedback loop in active use |
| R4 | Model false-positive rate erodes NOC trust post-launch | Planning | Data Scientist | Open, monitored — carried into hypercare with weekly precision/recall review |
| R5 | Cisco DNA Center API rate limits constrain real-time scoring | Planning | Network Architect | Closed — batch scoring at 5 min, later tuned to 2 min via CR-04 |
| R6 | Data residency/compliance objection to cloud ML compute | Charter | PM | Closed — in-region Azure ML workspace used; Security sign-off obtained at planning gate |
| R7 | Scope creep — requests to extend to endpoints/applications | Charter | PM | Managed — out-of-scope list reconfirmed at every steering review; CR-03 deferred, no uncontrolled scope change occurred |
| R8 | Key data scientist attrition mid-program | Planning | PM | Mitigated — runbook documentation; second data scientist cross-trained on pipeline |

## Assumptions

| ID | Description | Phase Raised | Owner | Status |
|---|---|---|---|---|
| A1 | 18 months of historical ServiceNow data would be sufficient and readily usable for model training | Planning | Data Scientist | Partially false — usable, well-labelled data initially expected to extend further back; descoped to 18 months as a deliberate, documented trade-off rather than a silent gap |
| A2 | Real-time API scoring via Cisco DNA Center would be technically viable | Planning | Network Architect | False — rate-limit testing in Week 2 showed this wasn't viable; plan revised to 5-minute batch scoring before schedule commitment |
| A3 | NOC would engage constructively given a genuine role in UAT sign-off | Charter | PM | Validated — NOC went from explicit skepticism at kickoff to requesting expansion of the feedback mechanism by closure |
| A4 | Existing NOC shift structure would not need to change to support the new workflow | Charter | PM | Validated — held throughout delivery as a hard charter constraint |

## Issues

| ID | Description | Phase Raised | Severity | Resolution |
|---|---|---|---|---|
| I1 | Historical data volume larger than estimated (18 months of tickets vs. 12 planned), slowing cleansing | Execution (Week 4) | Medium | Descoped to 18 months of data, sufficient for model validity; documented as a deliberate trade-off, not a silent gap |
| I2 | Model precision below target (64% vs. 70%) at first training pass | Execution (Week 8) | Medium | Added change-proximity and utilisation-trend features; re-trained to 73% precision, exceeding the original target |
| I3 | Auto-created tickets not inheriting correct CMDB configuration item links, risking incorrect routing | Execution (Week 12) | High | Fixed pre-UAT; explicit routing-validation step added to the UAT script |
| I4 | NOC shift lead raised alert fatigue concern ("will this just be more noise?") | Execution | Medium | Confidence threshold tuned conservatively for launch; snooze/feedback mechanism added so NOC could downrank noisy prediction types |
| I5 | Data scientist resource contention with another internal project in Week 10 | Execution | Low | Negotiated protected time through UAT with the data scientist's functional manager; documented as a recurring resourcing risk |
| I6 | DNA Center access delayed by a pending firewall rule change request | Execution (Week 4) | Medium | Escalated directly to the Security lead rather than waiting in queue; resolved within the week via CR-01 |

## Dependencies

| ID | Description | Phase Raised | Owner | Status |
|---|---|---|---|---|
| D1 | Security & Compliance sign-off on in-region Azure ML approach required before go-live | Planning | Security & Compliance Lead | Closed — pre-cleared at the planning gate, removing a potential late-stage blocker |
| D2 | Firewall rule change required to permit DNA Center API access from the Azure ML workspace | Execution | Security & Compliance Lead | Closed via CR-01 |
| D3 | NOC UAT sign-off required before pilot go-live | Planning → Execution | NOC Lead | Closed — UAT executed across all three shifts; sign-off achieved |
| D4 | Steering Committee go/no-go decision required before full rollout to Regions 2 & 3 | Monitoring & Control | Sponsor | Closed — approved one week ahead of the planned go/no-go date based on pilot evidence |
| D5 | Ongoing model monitoring ownership and runbook handoff required before hypercare exit | Closure | NOC Lead | Closed — runbook handed over covering model monitoring, feedback-loop usage, and escalation path |

## Changes

| ID | Description | Impact | Decision |
|---|---|---|---|
| CR-01 | Firewall rule change to permit DNA Center API access from Azure ML workspace | Schedule (+3 days) | Approved — Security gate |
| CR-02 | Firmware upgrade for 6 legacy branch switches to enable telemetry export | Cost (+$4,200); schedule absorbed in contingency | Approved — Steering Committee |
| CR-03 | Request from Banking Ops Director to extend prediction scope to ATM network | Scope (significant) | Deferred — logged as a Phase 2 business case candidate, kept outside the current charter |
| CR-04 | Switch batch scoring interval from 5 minutes to 2 minutes after pilot feedback | Cost (+$1,800 compute); no schedule impact | Approved — PM authority, within budget threshold |

---

## RAID Summary by Phase

| Phase | Risks | Assumptions | Issues | Dependencies | Changes |
|---|---|---|---|---|---|
| 1 — Initiation | R1, R2, R3, R6, R7 (raised) | A3, A4 | — | — | — |
| 2 — Planning | R1, R5, R8 (formalized) | A1, A2 | — | D1 | — |
| 3 — Execution | R4 (active monitoring) | A1 (tested), A2 (tested) | I1, I2, I3, I4, I5, I6 | D2, D3 | CR-01, CR-02, CR-03, CR-04 |
| 4 — Monitoring & Control | R1–R5, R7 (burn-down reviewed) | — | — | D4 | — |
| 5 — Closure | R4 (carried into hypercare) | — | — | D5 | — |

---

## What This Log Demonstrates

The two items that came closest to threatening the charter's success criteria — **model precision (I2)** and **historical data volume (I1)** — were both surfaced the moment they were identified rather than discovered at a scheduled review, and both were resolved through engineering work rather than by quietly lowering the target. The Week 8 precision flag in particular was later cited by the Steering Committee as a confidence builder going into the pilot go/no-go decision, not a mark against the program — direct evidence that transparent, early escalation strengthened stakeholder trust rather than weakening it.

The scope-related items (**R7, CR-03**) show the other half of the same discipline: holding a boundary under real pressure from a business stakeholder, formally, rather than letting scope drift informally during execution.

---

*Part of the [NetSentinel AI](./README.md) case study by Prachi Sharma.*
