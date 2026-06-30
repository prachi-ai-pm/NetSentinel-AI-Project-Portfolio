# NetSentinel AI

**An End-to-End AI/ML Project Management Case Study**
*Predictive Network Incident Management & Auto-Remediation Platform — Initiation Through Closure*

**Prachi Sharma** · Senior Associate – Change Control Analyst, NTT DATA
*Role simulated in this portfolio: Project Manager*

---

## A Note on This Repository

This document presents NetSentinel AI as a self-directed portfolio simulation, created independently by Prachi Sharma to demonstrate end-to-end project management capability across AI/ML, infrastructure, and IT service delivery domains. It is **not** a project assigned, sponsored, or delivered by any current or former employer, and does not represent actual employer data, client names, financials, or proprietary information.

The client organisation ("Meridian Financial Group"), stakeholders, conversations, metrics, and outcomes referenced throughout are fictional constructs designed to realistically simulate a banking/financial services infrastructure environment. Where real professional experience informs the simulation — ITSM practice (Incident, Problem, Change, and Release Management), network infrastructure delivery, and Cisco hardware deployment exposure — this is explicitly noted.

**Presented honestly as a self-built simulation, not a claimed client engagement.**

---

## Project Overview

Meridian Financial Group, a fictional regional bank operating 40 branches and three regional data centres across APAC, was experiencing recurring P1/P2 network incidents that breached SLA commitments, eroded customer trust, and consumed significant NOC and engineering effort in reactive firefighting.

**NetSentinel AI** was scoped as a 16-week program (plus 8-week hypercare) to predict network incidents before they breach SLA thresholds and to automate first-line remediation and ticket triage through ServiceNow — reducing Mean Time to Resolve (MTTR) and lifting SLA compliance without adding headcount.

As Project Manager, this program was owned end-to-end: business case and charter, stakeholder alignment across IT Ops, NOC, Data Science, Security, and Finance, scope and schedule management, risk and change control, vendor/API integration governance, and final closure and benefits realisation reporting. The program used a **hybrid Waterfall-Agile delivery model** — Waterfall governance for infrastructure and compliance gates, Agile sprints for ML model development — reflecting how AI initiatives actually get delivered inside regulated, infrastructure-heavy environments.

### Project Snapshot

| | |
|---|---|
| **Role** | Project Manager (sole PM, cross-functional lead) |
| **Sponsor** | VP, IT Infrastructure & Operations |
| **Duration** | 16-week build, 8-week hypercare and stabilisation |
| **Budget** | $185,000 (people, Azure ML compute, ServiceNow integration licensing) |
| **Delivery model** | Hybrid — Waterfall gates for infra/compliance, 2-week Agile sprints for the ML workstream |
| **Core technology stack** | Cisco DNA Center API, SolarWinds NPM, Azure Machine Learning, Python/scikit-learn/XGBoost, ServiceNow REST API, Power BI |

---

## Outcome Snapshot

| Metric | Baseline | Target | Achieved at Closure |
|---|---|---|---|
| Mean Time to Resolve (MTTR) | 4.5 hrs | ≤ 2.8 hrs (-38%) | 2.6 hrs (-42%) |
| SLA compliance | 88% | 95% | 96.5% |
| P1/P2 incidents predicted before breach | 0% (no predictive capability) | 60% | 73% |
| Manual NOC triage effort | Baseline | -25% | -38% |
| Estimated annual savings | — | $350K | $480K |
| Program budget | $185,000 | Within ±10% | $179,400 (3% under) |

All charter success criteria were met or exceeded, with the program closing 3% under budget. The headline numbers are the easy story; the real demonstration of judgment is in how a sponsor who had already shelved one failed AIOps evaluation was brought to a confident go-live decision — through deliberate scope narrowing, a hard human-approval-gate design constraint, and transparent handling of a mid-execution model precision miss.

---

## Repository Contents

| Document | Description |
|---|---|
| [`01-Project-Charter.md`](./01-Project-Charter.md) | Problem statement, objectives, success criteria, scope, constraints, and the kickoff questions that had to be answered before sponsorship was secured |
| [`02-Business-Case.md`](./02-Business-Case.md) | Options considered, financial justification, and how the case was defended against sponsor skepticism from a prior failed AI evaluation |
| [`03-Scope-Statement.md`](./03-Scope-Statement.md) | In-scope / out-of-scope boundaries, constraints, success criteria, and the deliberate scope decision around legacy switch telemetry gaps |
| [`04-WBS.md`](./04-WBS.md) | Work breakdown structure across the five major deliverable groups, mapped to the 24-week schedule |
| [`05-Stakeholder-Register.md`](./05-Stakeholder-Register.md) | Full stakeholder map with RACI matrix and the kickoff conversation that secured sponsorship after a prior failed AI evaluation |
| [`06-Communication-Plan.md`](./06-Communication-Plan.md) | Communication cadence by audience, and how proactive escalation (notably the Week 8 precision miss) shaped stakeholder trust |
| [`07-RAID-Log.md`](./07-RAID-Log.md) | Risks, Assumptions, Issues, Dependencies, and Changes tracked from Initiation through Monitoring & Control |
| [`08-Risk-Register.md`](./08-Risk-Register.md) | Risk-specific deep dive with likelihood/impact scoring, mitigations, and the full risk burn-down to pilot close |
| [`09-Sprint-Plan.md`](./09-Sprint-Plan.md) | The eight two-week Agile sprints that built the ML workstream, run in parallel with a Waterfall-governed infrastructure track |
| [`10-Product-Backlog.md`](./10-Product-Backlog.md) | MoSCoW-prioritised, sprint-mapped backlog across five epics, including the mid-program re-prioritisation that closed the precision gap |

---

## Program Structure

- **Sponsor:** VP, IT Infrastructure & Operations (Meridian Financial Group)
- **Project Manager:** Prachi Sharma
- **Duration:** 16-week build, 8-week hypercare and stabilisation
- **Budget:** $185,000
- **Delivery model:** Hybrid — Waterfall gates for infra/compliance, 2-week Agile sprints for the ML workstream
- **Core technology stack:** Cisco DNA Center API, SolarWinds NPM, Azure Machine Learning, Python/scikit-learn/XGBoost, ServiceNow REST API, Power BI

## The Five-Phase Lifecycle

1. **Initiation** — Securing sponsorship after a prior failed AIOps evaluation, with a hard human-approval-gate constraint written into the charter from day one.
2. **Planning** — Reconciling two different ways of working (infrastructure Waterfall, ML Agile) into one executable scope, schedule, and risk register.
3. **Execution** — Building the model and integrations, including a proactively raised precision miss at Week 8 that strengthened rather than weakened stakeholder confidence.
4. **Monitoring & Control** — Pilot evaluation on Region 1 as a deliberate stress test, with full rollout approved a week ahead of schedule on the strength of the pilot evidence.
5. **Closure** — Formal benefits realisation against the original business case, an 8-week hypercare handoff to BAU, and a credible Phase 2 candidate (ATM network extension) left open for the sponsor rather than a closed conversation.

---

## How This Fits Into My Portfolio

This case study sits alongside a **ChangeGuard AI** case study (predictive ML risk-scoring for IT Change Advisory Boards in a regulated bank). Together they're meant to show range across infrastructure-heavy and governance-heavy AI/ML delivery:

- **Lead with NetSentinel AI** for infrastructure/network-heavy, ITSM, or service-delivery-focused roles.
- **Lead with ChangeGuard AI** for model-risk-governance-heavy or fairness/explainability-focused roles.

---

*Prachi Sharma — Senior Associate, Change Control Analyst · Project Manager (simulated role, this portfolio)*

