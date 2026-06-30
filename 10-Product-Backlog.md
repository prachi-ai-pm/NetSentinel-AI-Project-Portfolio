# Product Backlog

**NetSentinel AI — Predictive Network Incident Management & Auto-Remediation Platform**

> Translates the [Scope Statement](./03-Scope-Statement.md) and [WBS](./04-WBS.md) into prioritised, sprint-ready backlog items for the Agile ML workstream. Mapped to the sprints in [09-Sprint-Plan.md](./09-Sprint-Plan.md). See the [README](./README.md) for full project context.

---

## Prioritisation Method

MoSCoW prioritisation (Must / Should / Could / Won't), applied against the charter's success criteria — items that directly determine whether MTTR, SLA compliance, prediction precision, or the human-approval-gate constraint can be met are Must-have by default.

---

## Epic 1 — Data Foundation

| ID | Item | Priority | Sprint | Status |
|---|---|---|---|---|
| BL-01 | Provision read access to SolarWinds NPM, Cisco DNA Center, and ServiceNow data sources | Must | 1–2 | Done |
| BL-02 | Inventory and document all data source schemas and refresh cadences | Must | 1–2 | Done |
| BL-03 | Extract 3 years of historical incident and change records from ServiceNow | Must | 3–4 | Done — descoped to 18 months of usable data, documented as a deliberate trade-off |
| BL-04 | Standardise free-text root-cause fields into a consistent taxonomy, jointly with NOC SMEs | Must | 3–4 | Done |
| BL-05 | Engineer link-utilisation trend features | Must | 3–4 | Done |
| BL-06 | Engineer error-rate features per network element | Must | 3–4 | Done |
| BL-07 | Engineer change-proximity features (incidents within 24h of a change) | Should | 3–4 → added in Sprint 6 | Done — originally Should, escalated to Must after the Sprint 5 precision miss |

## Epic 2 — Model Development

| ID | Item | Priority | Sprint | Status |
|---|---|---|---|---|
| BL-08 | Train baseline XGBoost classifier on cleansed historical data | Must | 5 | Done — 64% precision, below target |
| BL-09 | Evaluate model on held-out test set (precision/recall) | Must | 5 | Done |
| BL-10 | Re-train model with expanded feature set (change-proximity, utilisation-trend) | Must | 6 | Done — 73% precision, 67% recall, exceeded target |
| BL-11 | Tune confidence threshold for precision/recall trade-off | Must | 6 | Done — set conservatively for launch |
| BL-12 | Build prediction confidence score output for display to NOC | Must | 6 | Done |

## Epic 3 — Platform Integration

| ID | Item | Priority | Sprint | Status |
|---|---|---|---|---|
| BL-13 | Build Cisco DNA Center API integration | Must | 7 | Done |
| BL-14 | Build SolarWinds NPM API integration | Must | 7 | Done |
| BL-15 | Resolve real-time vs. batch scoring approach given API rate limits | Must | 1–2 (decision), 7 (build) | Done — 5-minute batch scoring; later tuned to 2-minute via CR-04 |
| BL-16 | Build ServiceNow auto-ticketing workflow with predicted root cause and confidence score | Must | 7 | Done |
| BL-17 | Map auto-created tickets to correct CMDB configuration items | Must | 8 | Done — defect found and fixed pre-UAT |
| BL-18 | Build Power BI NOC dashboard for prediction visibility and model performance tracking | Must | 8 | Done |
| BL-19 | Firmware upgrade for 6 legacy branch switches to enable telemetry export | Must | Parallel, via CR-02 | Done |

## Epic 4 — Human-in-the-Loop & Trust Design

| ID | Item | Priority | Sprint | Status |
|---|---|---|---|---|
| BL-20 | Enforce human-approval gate — no automated remediation action without explicit human sign-off | Must | Charter constraint, built throughout | Done — zero unplanned production changes from automation, confirmed at closure |
| BL-21 | Build NOC feedback/snooze mechanism to downrank unreliable prediction types | Should | Added in Execution, in response to alert-fatigue concern (I4) | Done — identified at retrospective as something that should have been in the MVP from Sprint 1 |
| BL-22 | Design UAT script with explicit NOC shift-team participation across all three shifts | Must | Pre-UAT, ahead of Sprint 9 | Done |

## Epic 5 — Validation & Rollout

| ID | Item | Priority | Sprint | Status |
|---|---|---|---|---|
| BL-23 | Conduct UAT with NOC shift teams, including ticket-routing validation | Must | 9 (Week 13) | Done |
| BL-24 | Execute parallel-run cutover (predictions visible, not yet triggering ticket creation) | Must | Pre-pilot | Done — 2-week parallel run |
| BL-25 | Pilot deployment — Region 1 (10 branches) | Must | Week 14 | Done — chosen deliberately as a stress test, not a best-case sample |
| BL-26 | Build rollback capability (disable auto-ticketing, revert to manual monitoring within 30 minutes) | Must | Pre-pilot | Done |
| BL-27 | Phased rollout — Regions 2 & 3, two weeks apart | Must | Weeks 17–24 | Done — approved a week ahead of schedule based on pilot evidence |

## Deferred / Won't-Have (This Program)

| ID | Item | Priority | Disposition |
|---|---|---|---|
| BL-28 | Extend prediction scope to ATM network | Won't (this program) | Deferred via CR-03; reopened at closure as a Phase 2 business case candidate |
| BL-29 | Fully autonomous remediation (no human approval gate) | Won't (this program) | Explicitly out of scope per Charter; candidate for a future phase once trust is established |
| BL-30 | Extend monitoring to endpoint/desktop or application-layer incidents | Won't (this program) | Explicitly out of scope per Charter; reconfirmed at every steering review |

---

## Backlog-to-Sprint Mapping Summary

| Sprint | Weeks | Backlog Items Delivered |
|---|---|---|
| 1–2 | 2–3 | BL-01, BL-02, BL-15 (decision) |
| 3–4 | 4–6 | BL-03, BL-04, BL-05, BL-06, BL-07 (started) |
| 5 | 7–8 | BL-08, BL-09 |
| 6 | 9 | BL-07 (escalated), BL-10, BL-11, BL-12 |
| 7 | 10–11 | BL-13, BL-14, BL-15 (build), BL-16, BL-19 (parallel) |
| 8 | 12 | BL-17, BL-18, BL-21 (added in response to I4) |
| 9 (UAT) | 13 | BL-22, BL-23 |
| Pilot | 14–16 | BL-24, BL-25, BL-26 |
| Rollout | 17–24 | BL-27 |

---

## What This Backlog Demonstrates

**BL-07** (change-proximity features) is the clearest example of priority being driven by evidence rather than the original plan: it started as a Should-have, and was escalated to effectively Must-have the moment the Sprint 5 precision miss made clear it was needed to hit the charter target — a backlog re-prioritisation made mid-program, not at a quarterly planning cycle.

**BL-21** (NOC feedback/snooze mechanism) is the clearest retrospective lesson: it was added reactively, in response to the alert-fatigue concern raised during execution, rather than being part of the original MVP scope. The [Lessons Learned](./README.md) reflection on this program names exactly this — building the NOC feedback mechanism into the MVP from sprint one, rather than adding it later, as something to do differently next time.

---

*Part of the [NetSentinel AI](./README.md) case study by Prachi Sharma.*
