# Sprint Plan

**NetSentinel AI — Predictive Network Incident Management & Auto-Remediation Platform**

> Covers the eight two-week Agile sprints that made up the ML workstream during Phase 3 — Execution, run in parallel with a Waterfall-style, change-controlled infrastructure/integration workstream. See the [README](./README.md) for full project context, [04-WBS.md](./04-WBS.md) for how this maps to the work breakdown structure, and [07-RAID-Log.md](./07-RAID-Log.md) for the issues and change requests that shaped several sprints mid-flight.

---

## Delivery Model

Execution ran as a genuine hybrid: the infrastructure and integration workstream followed Waterfall-style, change-controlled gates — required for any production network or ServiceNow change under Meridian's change policy — while the ML workstream ran in 2-week Agile sprints, with sprint reviews open to the NOC Lead and Network Architect. The PM sat across both, translating ML sprint outputs into formal change requests wherever they touched production systems, rather than treating the two workstreams as separate programs that happened to share a budget.

---

## Sprint-by-Sprint Breakdown

### Sprint 1–2 (Weeks 2–3) — Data Foundation Kickoff
**Goal:** Provision data source access and finalise scope/RACI so both workstreams can commit to a shared plan.
**Delivered:** Data source access provisioned for SolarWinds and ServiceNow; scope statement and RACI matrix finalised and signed off.
**Carried forward:** Cisco DNA Center access delayed by a pending firewall change request (CR-01), not yet resolved at sprint close.

### Sprint 3–4 (Weeks 4–6, 3-week sprint) — Data Cleansing & Feature Engineering
**Goal:** Standardise historical incident root-cause data and complete feature engineering before any model training begins.
**Delivered:** Dedicated joint data-cleansing sprint with NOC SMEs, standardising free-text root-cause categories into a consistent taxonomy; feature engineering completed (link utilisation, error rates, change proximity).
**Adjustment made:** This sprint was deliberately extended from the originally planned 2 weeks to 3, after discovering the usable historical data volume was larger than estimated (18 months of tickets vs. 12 months planned). Descoped to 18 months as a documented trade-off rather than letting the sprint run indefinitely or silently shrinking data quality.
**Risk link:** Closes out [R1 — Data labelling inconsistency](./08-Risk-Register.md).

### Sprint 5 (Weeks 7–8) — Baseline Model Training
**Goal:** Train and validate a baseline XGBoost classifier on the cleansed dataset.
**Delivered:** Baseline model trained on 18 months of cleansed data — initial precision 64%, recall 58% on the held-out test set.
**Issue surfaced:** Precision came in below the 70% charter target. Raised proactively to the Sponsor and NOC Lead at the Week 8 status review rather than held for a later checkpoint — see [Communication Plan](./06-Communication-Plan.md) for the full account of why this mattered.
**Sprint plan response:** A specific, testable hypothesis was formed (missing change-proximity and utilisation-trend features) with a one-sprint plan to test it, rather than treating the miss as a reason to lower the target.

### Sprint 6 (Week 9) — Model Re-training
**Goal:** Re-train the model with an expanded feature set to close the precision gap identified in Sprint 5.
**Delivered:** Re-trained model reached 73% precision / 67% recall — exceeding the original 70% precision target.
**Parallel work:** ServiceNow integration build began in parallel with re-training, rather than waiting for model sign-off, to protect the overall schedule.

### Sprint 7 (Weeks 10–11) — Platform Integration
**Goal:** Build and unit-test the ServiceNow auto-ticketing workflow and Cisco DNA Center / SolarWinds API integration.
**Delivered:** ServiceNow auto-ticketing workflow built and unit tested; DNA Center/SolarWinds integration completed.
**Issue surfaced:** Resource contention for a data scientist with another internal project — negotiated protected time through UAT with the data scientist's functional manager rather than letting the sprint silently slip.

### Sprint 8 (Week 12) — Dashboard & Pre-UAT Hardening
**Goal:** Deliver the NOC-facing dashboard and surface any integration defects before UAT begins.
**Delivered:** Power BI NOC dashboard delivered for internal review.
**Defect caught:** Auto-created tickets were not inheriting the correct CMDB configuration item links, risking incorrect routing. Fixed pre-UAT, with an explicit ticket-routing validation step added to the UAT script as a direct response — catching this before the pilot rather than during it.

---

## Sprint Cadence Summary

| Sprint | Weeks | Primary Focus | RAG Status at Close |
|---|---|---|---|
| 1–2 | 2–3 | Data access provisioning, scope/RACI finalisation | Amber (DNA Center access pending) |
| 3–4 | 4–6 | Data cleansing & feature engineering | Amber → Green |
| 5 | 7–8 | Baseline model training | Green, with a flagged precision issue |
| 6 | 9 | Model re-training, ServiceNow build begins | Green |
| 7 | 10–11 | Platform integration | Green |
| 8 | 12 | Dashboard delivery, pre-UAT hardening | Green, 3% under planned burn |

Sprints 9 onward moved into UAT and pilot execution rather than further ML build sprints — see [10-Product-Backlog.md](./10-Product-Backlog.md) for how backlog items map to each sprint, and the [README](./README.md) outcome snapshot for pilot and rollout results.

---

## What This Cadence Demonstrates

The two sprint-level deviations from plan — extending Sprint 3–4 by a week, and re-running Sprint 6 to fix a precision miss — were both handled the same way: named explicitly, tied to a specific cause, and resolved with a defined plan rather than absorbed quietly or used to justify lowering a target. Running ServiceNow integration in parallel with model re-training, rather than sequencing strictly, is the clearest example of the hybrid delivery model paying off — the Waterfall-governed integration workstream didn't sit idle waiting on the Agile ML workstream to finish.

---

*Part of the [NetSentinel AI](./README.md) case study by Prachi Sharma.*
