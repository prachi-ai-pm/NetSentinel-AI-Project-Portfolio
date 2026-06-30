# Stakeholder Register

**NetSentinel AI — Predictive Network Incident Management & Auto-Remediation Platform**

> Produced during **Phase 1 — Initiation**, alongside the [Project Charter](./01-Project-Charter.md). See the [README](./README.md) for full project context and [06-Communication-Plan.md](./06-Communication-Plan.md) for how each stakeholder group was engaged through delivery.

---

## Register

| Stakeholder | Role | Interest / Influence | Engagement Approach |
|---|---|---|---|
| VP, IT Infrastructure & Ops | Sponsor | High / High | Bi-weekly steering review, escalation point |
| NOC Lead | Operational owner | High / Medium | Weekly working session, early prototype demos to build trust |
| Network Architect | Technical SME | High / Medium | Embedded in planning + execution workstream |
| Data Scientist (x2) | Model build | High / Low | Daily standups during model sprints |
| ServiceNow Developer | Integration build | Medium / Medium | Sprint reviews, API contract sign-off |
| Security & Compliance Lead | Risk gatekeeper | Medium / High | Data governance review at each phase gate |
| Banking Ops Director | Business stakeholder | Medium / Medium | Monthly business impact readout |
| Finance Business Partner | Budget owner | Low / Medium | Monthly budget variance report |

---

## RACI Matrix

| Activity | PM | Network Architect | Data Scientist | NOC Lead | Sponsor |
|---|---|---|---|---|---|
| Business case & charter | R/A | C | C | I | A |
| Data access & governance | A | R | C | I | I |
| Model build & tuning | A | C | R | C | I |
| ServiceNow integration | A | C | I | C | I |
| UAT sign-off | A | C | C | R | I |
| Go-live decision | R | C | C | C | A |
| Benefits realisation report | R/A | I | I | I | A |

*R = Responsible, A = Accountable, C = Consulted, I = Informed*

**The single most consequential RACI decision on this register is the NOC Lead's "R" on UAT sign-off.** The NOC had already pushed back hard on a vendor tool two years earlier, and the team's standing concern was being handed a finished system rather than shaping it. Making UAT sign-off a genuine NOC responsibility — not just an "I" — meant the NOC was testing and approving the system before pilot go-live, not being asked to adopt something already decided for them. Combined with the predict-and-ticket-only design from the charter, this was identified at closure as the single biggest factor in NOC adoption.

---

## Why Each Stakeholder Mattered

- **VP, IT Infrastructure & Ops (Sponsor):** Carried real institutional memory of a shelved AIOps platform evaluation two years prior. Every early conversation with this stakeholder had to address why this program would survive contact with production where the prior one hadn't — not just what it would deliver.
- **NOC Lead:** The operational owner whose team would actually live with the system day to day. Their early concern — "another dashboard nobody uses" — shaped the human-approval-gate design as much as any formal requirement did.
- **Network Architect:** The technical bridge between the ML workstream and the production network, embedded across planning and execution rather than consulted only at integration points — necessary given how much of the program's risk sat at exactly that boundary (API rate limits, legacy telemetry gaps, firmware dependencies).
- **Data Scientists:** High interest, low formal influence on the register, but the program's technical risk concentrated here — data labelling quality and model precision were the two issues that came closest to threatening the charter's success criteria.
- **Security & Compliance Lead:** Medium interest, high influence — a single objection on data residency or cloud ML compute could have stalled the program at any gate. Engaging this stakeholder earlier than originally planned was identified at closure as something to do differently next time.
- **Banking Ops Director:** Medium / Medium, but became the source of the program's most significant scope-pressure moment (the mid-execution ATM network extension request, CR-03) — a reminder that "medium influence" stakeholders can still generate high-stakes scope decisions.
- **Finance Business Partner:** Lower interest day-to-day, but the audience the savings calculation in the business case was deliberately built to satisfy independently, without requiring ongoing persuasion.

---

## Kickoff Narrative — What Actually Got Asked

The kickoff was where the project could have stalled before it started — the sponsor had seen AI pitches before that didn't survive contact with production. These were the real questions that had to be answered directly.

**Q: We evaluated AIOps platforms two years ago and shelved it. Why will this be different?**
A: Because this isn't a generic platform purchase — it's a model trained on Meridian's own three years of incident, change, and telemetry data, scoped to the specific failure patterns actually observed: WAN saturation, switch stack failures, and post-change drift. Narrower, cheaper, and faster to prove value than a platform rollout, with the option to expand later if it works.

**Q: What's the ROI, concretely, not in "efficiency gains"?**
A: Current SLA breaches and reactive response cost roughly $1.2M a year in penalty credits and emergency support. This program costs $185K and targets a 38% MTTR reduction. Even a conservative outcome pays for itself inside six months, with the savings calculation built into the business case so Finance can stress-test it independently.

**Q: Who is accountable if the model recommends a wrong action and causes an outage?**
A: Nobody, in Phase 1, by design. The model only predicts and creates a ServiceNow ticket — no automated change is pushed to production without a human approval gate. This was made a hard constraint in the charter specifically to get Security and the NOC comfortable before any conversation about further automation.

### Issues Surfaced at Kickoff

- Sponsor skepticism rooted in a prior failed AIOps evaluation — addressed by deliberately scoping smaller and proving value before requesting further investment.
- NOC Lead raised concern that "another dashboard nobody uses" would be the outcome — addressed by committing to NOC-led UAT and a no-automation-without-approval design from day one.

### Positive Outcomes

- Charter signed in Week 1 with no scope disputes — the explicit out-of-scope list (endpoints, applications, security incidents) pre-empted the usual "can it also do X" scope creep at this stage.
- Sponsor agreed to a phased automation approach (predict-and-ticket first, auto-remediate later), which became the single most reused argument throughout the program when stakeholders pushed for faster automation.

---

*Document produced as part of Phase 1 — Initiation. Part of the [NetSentinel AI](./README.md) case study by Prachi Sharma.*
