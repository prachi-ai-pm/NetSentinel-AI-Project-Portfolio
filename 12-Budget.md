# Budget

**NetSentinel AI — Predictive Network Incident Management & Auto-Remediation Platform**

> Source figures from the Phase 1 Business Case and Phase 2 Budget & Resource Plan, tracked through to actual closure spend. See the [README](./README.md) for full project context and the [Business Case](./02-Business-Case.md) for the original financial justification.

---

## Budget Summary

| | |
|---|---|
| **Approved program budget** | $185,000 |
| **Actual spend at closure** | $179,400 (3% under budget) |
| **Ongoing monthly run cost (post-closure, full scale)** | ~$3,200/month (Azure ML compute) |
| **Approved by** | VP, IT Infrastructure & Operations (Sponsor), with Security & Compliance sign-off on the in-region Azure ML approach |
| **Estimated annual cost of status quo** | ~$1.2M (penalty credits, emergency vendor support, lost productivity) |
| **Targeted annual savings** | $350K–$480K |
| **Actual annualised savings at closure** | ~$480,000 |
| **Payback period (actual)** | ~4.5 months from full rollout |

---

## Budget & Resource Plan (Approved at Planning Gate)

| Category | Allocation |
|---|---|
| People (PM, Network Architect, 2 Data Scientists, ServiceNow Dev, QA — 6 months blended) | $132,000 |
| Azure ML compute & storage | $22,000 |
| ServiceNow integration licensing/API usage | $18,000 |
| Contingency (10%) | $13,000 |
| **Total** | **$185,000** |

---

## How the Approved Budget Was Actually Spent

| Category | Approved | Notes on Actual Spend |
|---|---|---|
| People | $132,000 | Largest line item; no change requests impacted people cost directly |
| Azure ML compute & storage | $22,000 | Within allocation; ongoing run cost (~$3,200/month) calculated separately and communicated to Finance ahead of closure |
| ServiceNow integration licensing/API usage | $18,000 | Within allocation |
| Contingency (10%, $13,000) | $13,000 | Partially drawn down to absorb CR-02 (firmware upgrade, +$4,200) and CR-04 (scoring interval change, +$1,800 compute); remainder unspent, contributing to the 3% under-budget close |
| **Total spend at closure** | **$179,400** | **3% under the $185,000 approved budget** |

---

## Change Requests with Budget Impact

| CR # | Description | Cost Impact | Disposition |
|---|---|---|---|
| CR-01 | Firewall rule change for DNA Center API access | No direct cost — schedule impact only (+3 days) | Approved — Security gate |
| CR-02 | Firmware upgrade for 6 legacy branch switches | +$4,200 | Approved — Steering Committee; absorbed within contingency |
| CR-03 | ATM network scope extension | Not costed — deferred before reaching a budget estimate | Deferred — logged as Phase 2 candidate |
| CR-04 | Batch scoring interval change (5 min → 2 min) | +$1,800 compute | Approved — PM authority, within budget threshold |

All cost-impacting change requests were absorbed within the original $185,000 approved budget and its built-in 10% contingency — no incremental funding request was required at any point in delivery.

---

## Financial Case

| | |
|---|---|
| **Baseline annual cost of status quo** | ~$1.2M (SLA penalty credits, emergency vendor support, lost productivity) |
| **Program investment** | $185,000 approved; $179,400 actual |
| **Targeted annual savings** | $350K–$480K (MTTR reduction + reduced manual triage + avoided penalty credits) |
| **Targeted payback period** | Under 6 months post go-live |
| **Actual annualised savings at closure** | ~$480,000 — at the top end of the original target range |
| **Actual payback period** | ~4.5 months from full rollout |

### How the Financial Case Was Defended

The ROI conversation at kickoff had to go further than "efficiency gains," given the sponsor's prior experience with a shelved AIOps platform evaluation. The case made was concrete: current SLA breaches and reactive response cost roughly $1.2M a year; the program cost $185K and targeted a 38% MTTR reduction; even a conservative outcome would pay for itself inside six months. The savings calculation was deliberately built into the business case so Finance could stress-test it independently, rather than asking stakeholders to take the projection on faith. See [Business Case](./02-Business-Case.md) for the full framing.

---

## Ongoing Run Cost, Communicated Before Closure

A recurring failure mode in AI/ML programs is that build cost is carefully governed while run cost only surfaces as a surprise after the project team disbands. This was deliberately avoided here: ongoing Azure ML compute cost at full scale (~$3,200/month) was calculated and communicated to the Steering Committee as part of closure planning, alongside a named ownership transition (NOC Lead, with a documented runbook) — not left for Finance to discover three months later.

> "I built a hypercare and ownership transition plan as part of closure: NOC Lead owns day-to-day model monitoring with a documented runbook, and ongoing Azure ML compute cost is roughly $3,200/month at full scale — well inside the savings the model is already generating. I'd rather hand you that number now than have it surprise Finance in three months."

This run cost is well inside the ~$480,000 annualised savings figure, leaving a clear and durable net benefit rather than a marginal one.

---

## Notes on Budget Governance

- **The contingency line was treated as a real, governable budget item, not a buffer to quietly absorb scope drift.** Both cost-impacting change requests (CR-02, CR-04) were formally logged, approved through the appropriate authority (Steering Committee for CR-02, PM authority within threshold for CR-04), and tracked against the contingency explicitly — not informally folded into "people cost" or left unaccounted for.
- **Monthly budget variance reporting to Finance ran throughout execution** (see [Communication Plan](./06-Communication-Plan.md)), meaning the 3% under-budget close was a continuation of a trend that had been visible and reported throughout, not a surprise at the final report.
- **CR-03 (ATM network extension) was deliberately not costed.** Because it was deferred before reaching a serious scoping conversation, no budget estimate was attached — avoiding the trap of implicitly legitimising an out-of-scope request by giving it a price tag.

---

*Part of the [NetSentinel AI](./README.md) case study by Prachi Sharma.*
