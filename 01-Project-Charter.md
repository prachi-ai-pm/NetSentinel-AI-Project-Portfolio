# Project Charter

**NetSentinel AI — Predictive Network Incident Management & Auto-Remediation Platform**

> Signed off by Sponsor and IT Steering Committee at end of Week 1. Produced during **Phase 1 — Initiation**, alongside the [Business Case](./02-Business-Case.md). See the [README](./README.md) for full project context and [03-Scope-Statement.md](./03-Scope-Statement.md) / [04-WBS.md](./04-WBS.md) for the planning artifacts that follow.

---

## Charter Summary

| Field | Detail |
|---|---|
| **Project Name** | NetSentinel AI — Predictive Network Incident Management & Auto-Remediation Platform |
| **Sponsor** | VP, IT Infrastructure & Operations (Meridian Financial Group) |
| **Project Manager** | Prachi Sharma |
| **Start / End Date** | Week 1 – Week 16 (build); Weeks 17–24 hypercare |
| **Budget** | $185,000 |
| **Objective** | Reduce Mean Time to Resolve (MTTR) by ≥38% and lift SLA compliance from 88% to ≥95% within 6 months of go-live, using a predictive ML model and automated ServiceNow triage. |
| **In Scope** | WAN links, core/branch switches, and routers across 3 regional data centres and 40 branches; integration with ServiceNow, SolarWinds, and Cisco DNA Center; NOC dashboard and alerting. |
| **Out of Scope** | Endpoint/desktop incidents, application-layer incidents, security incident response (handled by SOC), branch hardware refresh. |
| **Success Criteria** | MTTR ≤ 2.8 hrs; SLA ≥ 95%; ≥60% of P1/P2 incidents predicted ahead of breach; model precision ≥70%; zero unplanned production network changes from automation. |
| **Key Constraints** | Banking-grade change control — no automated changes without a human approval gate in Phase 1; data residency must remain in-region; existing NOC shift structure cannot change. |
| **High-Level Risks** | Data quality/labelling gaps; legacy device telemetry gaps; NOC trust/adoption of automation; model drift post-launch. |

---

## How This Charter Came Together

Meridian Financial Group's branch network was logging an average of 18 P1/P2 major incidents per quarter, with MTTR sitting at 4.5 hours and SLA compliance at 88% against a contractual target of 95%. Recurring root causes — WAN link saturation, switch stack failures, and configuration drift after changes — were only detected after impact, triggering reactive bridge calls and escalations.

This was not the first AI conversation at Meridian: the sponsor had evaluated a commercial AIOps platform two years earlier and shelved it. That history shaped the charter as much as the underlying network problem did — the program had to be scoped narrowly enough to prove value quickly, using data Meridian already owned, rather than repeating a platform-buy approach that had already failed to gain traction.

### PM Activities

- Quantified the baseline using two quarters of NOC incident data — average MTTR, SLA compliance, and incident volume — rather than relying on anecdote.
- Evaluated three options (do nothing, buy a commercial AIOps platform, build a targeted predictive model in-house) and built the financial case for the selected option.
- Drafted this charter with an explicit, narrow in-scope/out-of-scope boundary, deliberately pre-empting the most likely scope-creep requests before kickoff.
- Made "predict-and-ticket, not auto-remediate" a hard design constraint in the charter itself, not a later policy decision — directly addressing the accountability question before it could derail sponsor or NOC buy-in.
- Walked the charter through Sponsor and IT Steering Committee sign-off in Week 1, with no scope disputes at signing.

### Key Questions Asked

- **To the Sponsor, at kickoff:** "We evaluated AIOps platforms two years ago and shelved it. Why will this be different?"
- **To the Sponsor, on ROI:** "What's the ROI, concretely, not in 'efficiency gains'?"
- **To the Sponsor and Security, on accountability:** "Who is accountable if the model recommends a wrong action and causes an outage?"
- **To the NOC Lead:** What would make this feel like a tool the NOC actually trusts, rather than "another dashboard nobody uses"?

### Issues Faced & How They Were Resolved

- **Sponsor skepticism rooted in a prior failed AIOps evaluation.** Addressed by deliberately scoping smaller than a full platform — a focused predictive model trained on Meridian's own three years of incident, change, and telemetry data — and committing to prove value before requesting further investment, rather than asking for platform-scale buy-in up front.
- **The NOC Lead raised concern that this would become "another dashboard nobody uses."** Addressed by committing to NOC-led UAT and a no-automation-without-approval design from day one, written directly into the charter rather than left as an execution-phase decision.
- **Who is accountable if a prediction leads to a bad outcome was an open question at kickoff.** Resolved by making the human-approval gate a hard charter constraint: in Phase 1, the model only predicts and creates a ServiceNow ticket — no automated change reaches production without human sign-off. This was framed explicitly as a trust-building step toward further automation, not a permanent ceiling.

---

## Outcome at Closure

All charter success criteria were met or exceeded — see the [Project Closure Report](./README.md#outcome-snapshot) in the README for the full results. The charter's central design decision (predict-and-ticket only, human-approval gate) was identified at closure as the single biggest factor in NOC adoption.

---

*Document produced as part of Phase 1 — Initiation. Part of the [NetSentinel AI](./README.md) case study by Prachi Sharma.*
