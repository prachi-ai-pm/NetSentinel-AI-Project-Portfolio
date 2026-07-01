# Complete Documentation Index

**NetSentinel AI — Predictive Network Incident Management & Auto-Remediation Platform**

> A single navigable index of every artifact in this case study, organised by delivery phase rather than file number. For readers who want to follow the work in the order it actually happened. See the [README](./README.md) for the project overview and outcome snapshot.

---

## How to Use This Index

This repository documents the full lifecycle of an AI/ML program — from a kickoff where the sponsor had already shelved a previous AI initiative, through to a closure where the NOC team went from skepticism to requesting expanded automation. The 15 documents below are listed in delivery order, grouped by the five phases they belong to, with a one-line note on what each one is for.

**If you only have a few minutes:** read the [README](./README.md), then the [Project Closure Report](./14-Project-Closure-Report.md), then [Lessons Learned](./15-Lessons-Learned.md).

**If you're assessing this for a specific role type**, see the Interview Talking-Points section at the end of this document.

---

## Phase 1 — Initiation

| Document | What it captures |
|---|---|
| [01-Project-Charter.md](./01-Project-Charter.md) | The formal scope, success criteria, constraints, and the kickoff questions that had to be answered before sponsorship was secured — including the prior failed AIOps evaluation |
| [02-Business-Case.md](./02-Business-Case.md) | Options considered (do nothing / buy / build), financial justification, and how the case was defended against sponsor skepticism |

## Phase 2 — Planning

| Document | What it captures |
|---|---|
| [03-Scope-Statement.md](./03-Scope-Statement.md) | In/out-of-scope boundaries, the legacy-switch telemetry decision (scope in, not silently exclude), and the phased rollout design |
| [04-WBS.md](./04-WBS.md) | Work breakdown structure across the five major deliverable groups, mapped to the 24-week schedule |
| [05-Stakeholder-Register.md](./05-Stakeholder-Register.md) | Full stakeholder map with RACI matrix, and why the NOC Lead's "R" on UAT sign-off was the single biggest structural adoption decision |
| [06-Communication-Plan.md](./06-Communication-Plan.md) | Communication cadence and the phase-by-phase account of how proactive escalation — especially the Week 8 precision miss — shaped stakeholder confidence |
| [12-Budget.md](./12-Budget.md) | Approved $185K budget breakdown, actual $179,400 closure spend, change-request cost impact, and the discipline of communicating ongoing run cost before closure |

## Phase 3 — Execution

| Document | What it captures |
|---|---|
| [07-RAID-Log.md](./07-RAID-Log.md) | Risks, Assumptions, Issues, Dependencies, and Changes across all five phases — with the four change requests and their outcomes |
| [08-Risk-Register.md](./08-Risk-Register.md) | Risk-specific deep dive with likelihood/impact scoring, full burn-down table, and why data quality and NOC adoption were the two Critical-rated risks |
| [09-Sprint-Plan.md](./09-Sprint-Plan.md) | The eight two-week Agile ML sprints run in parallel with a Waterfall-governed infrastructure track — including the precision miss and the re-training recovery |
| [10-Product-Backlog.md](./10-Product-Backlog.md) | 30 backlog items across five epics, MoSCoW-prioritised and sprint-mapped, including the mid-program escalation of change-proximity features from Should to Must |
| [11-User-Stories.md](./11-User-Stories.md) | 12 detailed stories with acceptance criteria, written from each stakeholder's perspective — NOC analyst, Sponsor, Security Lead, Steering Committee, and more |
| [13-Architecture-Diagram.md](./13-Architecture-Diagram.md) | System architecture from telemetry sources through the prediction pipeline, confidence gate, ServiceNow ticketing, NOC workflow, and human approval gate — with a GitHub-native Mermaid diagram |

## Phase 4 — Monitoring & Control

| Document | What it captures |
|---|---|
| *Pilot KPI results and go/no-go narrative* | Documented in [14-Project-Closure-Report.md](./14-Project-Closure-Report.md) — Pilot Results section |

## Phase 5 — Closure

| Document | What it captures |
|---|---|
| [14-Project-Closure-Report.md](./14-Project-Closure-Report.md) | Formal closure against the charter — objectives vs. outcomes, pilot results, budget closure, governance sign-offs, BAU handoff, and what actually got asked at the rollout and closure gates |
| [15-Lessons-Learned.md](./15-Lessons-Learned.md) | What worked, what to do differently, reusable patterns, and the Phase 2 roadmap left open at closure |

---

## Documentation Coverage Map

| Category | Documents |
|---|---|
| **Strategic / Initiation** | Project Charter, Business Case |
| **Planning** | Scope Statement, WBS, Stakeholder Register, Communication Plan, Budget |
| **Risk & Governance** | RAID Log, Risk Register |
| **Agile Delivery** | Sprint Plan, Product Backlog, User Stories |
| **Technical** | Architecture Diagram |
| **Closeout** | Project Closure Report, Lessons Learned |

---

## Key Threads to Follow Across Documents

Some of the most important stories in this case study cross multiple documents. These are the threads worth tracing if you want to see how PM judgment actually plays out across the lifecycle:

**The precision miss (Week 8):**
Raised as risk R4 in the [Risk Register](./08-Risk-Register.md) → discovered in Sprint 5 of the [Sprint Plan](./09-Sprint-Plan.md) → proactively escalated per the [Communication Plan](./06-Communication-Plan.md) → closed in Sprint 6 via change-proximity features escalated from Should to Must in the [Product Backlog](./10-Product-Backlog.md) → cited by the Steering Committee as a confidence builder in the [Closure Report](./14-Project-Closure-Report.md) → reflected on in [Lessons Learned](./15-Lessons-Learned.md).

**The human-approval-gate design:**
Written into the [Project Charter](./01-Project-Charter.md) as a hard constraint → confirmed in the [Scope Statement](./03-Scope-Statement.md) → built as BL-20 in the [Product Backlog](./10-Product-Backlog.md) → written as US-07 in [User Stories](./11-User-Stories.md) → shown as an architectural boundary in the [Architecture Diagram](./13-Architecture-Diagram.md) → confirmed as zero unplanned production changes in the [Closure Report](./14-Project-Closure-Report.md) → named as the single biggest adoption factor in [Lessons Learned](./15-Lessons-Learned.md).

**The NOC trust arc:**
Skepticism at kickoff ("another dashboard nobody uses") in the [Stakeholder Register](./05-Stakeholder-Register.md) → shaped the charter constraint → NOC given genuine "R" on UAT sign-off per the [RACI](./05-Stakeholder-Register.md) → alert-fatigue concern added the feedback mechanism (BL-21) in the [Product Backlog](./10-Product-Backlog.md) → UAT sign-off achieved across all three shifts per [User Stories](./11-User-Stories.md) US-09 → team requesting expansion of feedback mechanism at [Closure](./14-Project-Closure-Report.md) → named a retrospective lesson in [Lessons Learned](./15-Lessons-Learned.md).

---

## Interview Talking-Points Quick Reference

This repository supports three interview role tracks, each with a primary entry point:

| Role Track | Lead With | Supporting Documents |
|---|---|---|
| **AI/ML Project Manager** | Week 8 precision miss → proactive escalation → precision exceeded at closure | Risk Register, Sprint Plan, Communication Plan, Closure Report |
| **Technical / Infrastructure PM** | Hybrid Waterfall/Agile model; Cisco DNA Center API rate-limit discovery; CR-02 firmware scope decision | WBS, Sprint Plan, Architecture Diagram, RAID Log |
| **Service Delivery Manager** | SLA/MTTR metrics; NOC adoption arc; steering committee rollout approval narrative | Charter, Closure Report, Stakeholder Register, Lessons Learned |

---

*Part of the [NetSentinel AI](./README.md) case study by Prachi Sharma.*
