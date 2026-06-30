# Business Case

**NetSentinel AI — Predictive Network Incident Management & Auto-Remediation Platform**

> Produced during **Phase 1 — Initiation**, alongside the [Project Charter](./01-Project-Charter.md). See the [README](./README.md) for full project context.

---

## The Problem, in Numbers

Meridian Financial Group's branch network runs on a hybrid Cisco infrastructure (routers, switches, WAN links) across 3 regional data centres and 40 branches, monitored via SolarWinds NPM and Cisco DNA Center, with incidents logged and tracked in ServiceNow.

- **18 P1/P2 major incidents per quarter**, on average, over the two quarters preceding this program.
- **Average MTTR: 4.5 hours**, against a contractual SLA target of 95% compliance.
- **SLA compliance: 88%**, below target and triggering financial penalties under the Meridian master services agreement.
- **Recurring root causes** — WAN link saturation, switch stack failures, and configuration drift after changes — were detected only after impact, triggering reactive bridge calls and escalations rather than being caught ahead of breach.

## The Opportunity

Three years of incident, change, and monitoring telemetry already existed in ServiceNow, SolarWinds, and Cisco DNA Center. Rather than continuing to invest only in better dashboards, the program proposed using this historical data to train a predictive model that could flag at-risk network elements 30–45 minutes ahead of failure, paired with automated ServiceNow ticket creation and first-line remediation playbooks — closing the loop between detection, prediction, and action.

## Options Considered

| Option | Description | Verdict |
|---|---|---|
| **Do nothing** | Continue reactive monitoring and bridge-call response | Rejected — SLA penalties and customer churn risk continue to grow |
| **Buy a commercial AIOps platform** | License an off-the-shelf AIOps tool (e.g. Moogsoft, BigPanda) | Rejected for Phase 1 — 12+ month procurement cycle, doesn't use Meridian's own incident history, high licensing cost |
| **Build a targeted predictive model in-house** | Use existing ServiceNow/SolarWinds/DNA Center data to build a focused incident-prediction + auto-ticketing capability | **Selected** — fastest time-to-value, builds internal capability, lower cost, data stays in-house |

## Financial Justification

| | |
|---|---|
| **Estimated annual cost of current SLA breaches and downtime** | ~$1.2M (penalty credits, emergency vendor support, lost productivity) |
| **Program investment** | $185,000 one-time (6-month build + hypercare) |
| **Projected annual savings once stabilised** | $350K–$480K (MTTR reduction + reduced manual triage + avoided penalty credits) |
| **Payback period** | Under 6 months post go-live |
| **Actual annualised savings at closure** | ~$480,000 against a one-time investment of $179,400 — a payback period of approximately 4.5 months from full rollout |

## Strategic Alignment

The program directly supports Meridian's 2026 IT strategy pillar of "resilient, self-healing infrastructure," and gives IT Operations a defensible, data-backed narrative for the next SLA renegotiation with the business.

---

## How This Business Case Was Actually Defended

The financial case alone wasn't what got this funded — the sponsor had already shelved a prior AIOps platform evaluation, which made the conversation as much about trust as about ROI.

**On why this would be different from the shelved platform evaluation:** the case was made that this wasn't a generic platform purchase, but a model trained on Meridian's own three years of incident, change, and telemetry data, scoped specifically to the failure patterns actually observed — WAN saturation, switch stack failures, and post-change drift. Narrower, cheaper, and faster to prove value than a platform rollout, with the option to expand later if it worked.

**On ROI, when pushed for something more concrete than "efficiency gains":** current SLA breaches and reactive response were costing roughly $1.2M a year in penalty credits and emergency support. The program cost $185K and targeted a 38% MTTR reduction — even a conservative outcome paid for itself inside six months, with the savings calculation built into the business case so Finance could stress-test it independently.

**On accountability, when asked who is responsible if the model recommends a wrong action:** nobody, in Phase 1, by design. The model only predicts and creates a ServiceNow ticket — no automated change is pushed to production without a human approval gate. This was made a hard constraint in the charter specifically to get Security and the NOC comfortable before any conversation about further automation.

---

## Notes on Building a Credible Case After a Prior Failure

- **Scoping deliberately smaller than a full AIOps platform** let the program prove value fast and rebuild sponsor trust after the previous failed AI evaluation — a closure-stage lesson that traces directly back to how this business case was framed at the outset.
- **The explicit out-of-scope list (endpoints, applications, security incidents)** was written into the business case and charter together, pre-empting the usual "can it also do X" scope creep before kickoff rather than fielding it reactively during planning.

---

*Document produced as part of Phase 1 — Initiation. Part of the [NetSentinel AI](./README.md) case study by Prachi Sharma.*
