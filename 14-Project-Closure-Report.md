# Project Closure Report

**NetSentinel AI — Predictive Network Incident Management & Auto-Remediation Platform**

> Closes out the 16-week build and 8-week hypercare delivery and formally transitions the program into standing BAU ownership. See the [README](./README.md) for full project context and [15-Lessons-Learned.md](./15-Lessons-Learned.md) for the reflective companion to this report.

---

## Closure Summary

| | |
|---|---|
| **Project** | NetSentinel AI — Predictive Network Incident Management & Auto-Remediation Platform |
| **Sponsor** | VP, IT Infrastructure & Operations |
| **Project Manager** | Prachi Sharma |
| **Delivery Duration** | 16-week build, 8-week hypercare |
| **Closure Status** | **Delivered and transitioned to BAU.** All charter success criteria met or exceeded; program closed 3% under budget; ownership formally transferred to the NOC Lead with a documented runbook before the program closed. |
| **Budget** | $185,000 approved; $179,400 actual |

---

## Objectives vs. Outcomes

| Charter Success Criterion | Target | Actual at Closure | Met? |
|---|---|---|---|
| Mean Time to Resolve (MTTR) | ≤ 2.8 hrs | 2.6 hrs (-42% from baseline 4.5 hrs) | **Yes — exceeded** |
| SLA compliance | ≥ 95% | 96.5% | **Yes — exceeded** |
| P1/P2 incidents predicted ahead of breach | ≥ 60% | 73% | **Yes — exceeded** |
| Model precision | ≥ 70% | 73% | **Yes** |
| Unplanned production changes from automation | Zero | Zero | **Yes** |
| Budget | $185,000 (±10%) | $179,400 | **Yes — 3% under** |
| Estimated annualised savings | $350K–$480K | $480,000 | **Yes — top of range** |

All six charter success criteria met or exceeded. No objective was missed outright, and no objective required a scope reduction to be declared complete.

---

## Pilot Results (Phase 4 — Region 1, Weeks 14–16)

The pilot was deliberately structured as a stress test, not a best-case showcase — Region 1 was selected because it included the highest-incident-volume branches and two of the legacy switches upgraded under CR-02.

| KPI | Pre-Pilot Baseline | Pilot Result | Variance |
|---|---|---|---|
| MTTR | 4.5 hrs | 2.9 hrs | -36% |
| SLA compliance | 88% | 95.8% | +7.8 pts |
| P1/P2 incidents predicted ahead of breach | 0% | 71% | +71 pts |
| False positive rate | N/A | 12% | Within tolerance (target ≤15%) |
| NOC manual triage effort | Baseline | -34% | -34% |

Pilot results were strong enough that the Steering Committee approved full rollout to Regions 2 and 3 **one week ahead of the planned go/no-go date** — directly attributable to how the pilot's sample was justified: an honest stress-test framing, not a request to extrapolate from an easy sample.

---

## Budget Closure

| | |
|---|---|
| **Approved budget** | $185,000 |
| **Actual spend** | $179,400 (3% under) |
| **Contingency drawn** | $6,000 of $13,000 (CR-02 +$4,200; CR-04 +$1,800) |
| **No incremental funding request made** | All cost-impacting change requests absorbed within the original approved budget |
| **Ongoing run cost (communicated before closure)** | ~$3,200/month Azure ML compute — disclosed to Finance at the rollout go/no-go gate, not discovered post-closure |
| **Payback period** | ~4.5 months from full rollout |
| **Annualised savings** | ~$480,000 |

---

## Scope Closure

All in-scope deliverables defined in the [Scope Statement](./03-Scope-Statement.md) were delivered:

- Predictive scoring for WAN links, core/branch switches, and routers across 3 data centres and 40 branches
- Feature pipeline (utilisation, error rate, change proximity) with legacy switch telemetry coverage resolved via CR-02
- XGBoost model at 73% precision, exceeding the 70% charter target
- ServiceNow auto-ticketing with correct CMDB routing (defect caught and fixed pre-UAT)
- Power BI NOC dashboard
- Human-approval gate — zero unplanned production changes from automation
- Phased rollout across all three regions, each clearing its go/no-go gate
- 8-week hypercare with BAU handoff runbook

One out-of-scope request (CR-03 — ATM network extension) was held outside the program boundary and formally reopened as a Phase 2 business case candidate at closure. No uncontrolled scope changes occurred.

---

## Governance Sign-Offs on Record

| Gate | Outcome |
|---|---|
| Charter and Business Case approval | Approved by Sponsor and IT Steering Committee, Week 1 |
| Scope/RACI and Data Access | Approved at Planning gate, including Security & Compliance sign-off on in-region Azure ML approach |
| Model Precision Review (Week 8) | Shortfall proactively disclosed; remediation plan approved by Sponsor before sprint re-planning |
| UAT sign-off | Signed off by NOC Lead across all three shifts |
| Pilot go/no-go (Region 1) | Approved by Steering Committee one week ahead of schedule |
| Full rollout go/no-go | Approved — Regions 2 and 3 phased two weeks apart |
| Closure and BAU handoff | Signed off by Sponsor and NOC Lead |

No governance gate was bypassed or waived. The Week 8 precision disclosure was specifically noted by the Steering Committee at the rollout gate as a confidence builder — evidence that proactive disclosure strengthened rather than weakened stakeholder trust.

---

## What Transfers to BAU

| Responsibility | Cadence | Owner |
|---|---|---|
| Day-to-day model performance monitoring | Daily (first 2 weeks post-hypercare), then weekly | NOC Lead |
| Precision/recall review | Weekly | NOC Lead + Data Scientist on call |
| NOC feedback/snooze mechanism oversight | Ongoing | NOC Lead |
| Model drift escalation | Triggered if precision falls below 60% floor | NOC Lead → Data Scientist |
| Azure ML compute cost tracking | Monthly | Finance Business Partner |
| Phase 2 business case (ATM network extension) | To be scoped post-closure | Sponsor |

---

## Steering Committee Rollout Narrative — What Actually Got Asked

**Q: The pilot numbers look good, but it's only 10 branches. Why should we trust this at full scale?**
A: Region 1 was deliberately chosen because it includes the highest-incident-volume branches and two of the legacy switches upgraded under CR-02 — it's not the easiest subset, it's closer to a worst-case sample. The false-positive rate held within tolerance even on that harder mix, which is the strongest signal available that it will hold at scale.

**Q: What's the ongoing cost once this isn't a "project" anymore — who owns it and what does it cost to run?**
A: A hypercare and ownership transition plan was built as part of closure: the NOC Lead owns day-to-day model monitoring with a documented runbook, and ongoing Azure ML compute cost is roughly $3,200/month at full scale — well inside the savings the model is already generating. Handing over that number at this gate rather than leaving it to surface later is the right discipline.

## Closure Narrative — What Actually Got Asked

**Q: Now that this is in production, what happens if the model's accuracy drifts over time?**
A: That's exactly why the weekly precision/recall review was built into hypercare and the NOC Lead received a runbook with a clear escalation path, rather than treating go-live as the finish line. Model drift is a when-not-if risk for any ML system in production, so ownership and a monitoring cadence had to be defined before the program closed, not left as a gap.

**Q: What would you have scoped differently knowing what you know now?**
A: Data-cleansing effort would have been sized against the full historical data volume from day one rather than an estimate, and Security would have been pulled into the data architecture conversation about a week earlier. Neither caused real damage — the team absorbed both — but they are the kind of estimation lessons worth carrying into the next AI-adjacent program rather than relearning.

---

## Positive Outcomes at Closure

- All charter success criteria met or exceeded; program closed 3% under budget.
- The NOC team went from explicit skepticism at kickoff to requesting expansion of the feedback mechanism to more prediction categories — identified at closure as the single most meaningful adoption outcome.
- CR-03 (ATM network extension) was formally reopened as a Phase 2 business case candidate rather than left as a closed or rejected request — giving the Sponsor a credible next step.
- Ongoing run cost and day-to-day ownership were both defined and communicated before closure, not discovered as gaps post-handoff.

---

*Part of the [NetSentinel AI](./README.md) case study by Prachi Sharma.*
