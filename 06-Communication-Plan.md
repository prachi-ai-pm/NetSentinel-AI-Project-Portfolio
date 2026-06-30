# Communication Plan

**NetSentinel AI — Predictive Network Incident Management & Auto-Remediation Platform**

> Produced during **Phase 2 — Planning**, alongside the [Stakeholder Register](./05-Stakeholder-Register.md). See the [README](./README.md) for full project context.

---

## Communication Cadence

| Audience | Format | Frequency | Owner |
|---|---|---|---|
| Steering Committee (Sponsor, Banking Ops Director, Finance) | Status readout + RAG dashboard | Bi-weekly | PM |
| Core delivery team | Stand-up | Daily (execution phase) | PM |
| NOC shift teams | Working session + demo | Weekly | NOC Lead + PM |
| Security & Compliance | Gate review | At each phase gate | PM |
| Finance | Budget variance report | Monthly | PM |

---

## How This Cadence Played Out by Phase

### Initiation
The Steering Committee cadence began immediately with the charter sign-off in Week 1. No formal status reporting existed yet, but the kickoff conversation itself functioned as the first communication checkpoint — directly addressing sponsor skepticism, ROI, and accountability before any technical work began (see [Stakeholder Register](./05-Stakeholder-Register.md) for the full kickoff narrative).

### Planning
NOC working sessions started in planning, not execution, specifically to avoid repeating the prior failure mode where the NOC was handed a finished tool rather than involved in shaping it. Security & Compliance's gate review at planning pre-cleared the in-region Azure ML approach, removing what could otherwise have been a late-stage blocker before go-live — a direct payoff of treating "gate review at each phase gate" as a real commitment rather than a formality.

### Execution
This is where the communication plan was tested hardest, and where deviating from the standard cadence mattered:

- **Week 4 status report (Amber):** DNA Center access delayed by a pending firewall change request; root-cause field cleansing running behind due to a larger-than-estimated historical data volume. Reported transparently rather than smoothed over, with the variance from plan named directly (18 months of tickets vs. 12 planned).
- **Week 8 status report (Green, with a flagged issue):** Model precision came in at 64% against a 70% charter target. This was raised **proactively to the Sponsor and NOC Lead rather than waiting for the scheduled bi-weekly review** — a deliberate departure from the standard cadence, made because the cost of sitting on a model issue grows the longer it goes unaddressed. The Steering Committee later specifically noted this early flag as a confidence builder going into the pilot decision, not a red mark against the program.
- **Week 12 status report (Green):** Re-trained model reached 73% precision; a CMDB ticket-routing defect was caught and fixed pre-UAT rather than during the pilot, with an explicit validation step added to the UAT script in response.

The standing principle applied throughout execution: bring a problem with a plan attached, on the day it's found, rather than wait for the next scheduled checkpoint and risk a status going from green to red without warning.

### Monitoring & Control
The bi-weekly Steering Committee cadence carried the pilot results into the rollout go/no-go decision. Communicating the Region 1 pilot honestly as a deliberately hard stress-test sample — not a best-case showcase — was what let the Steering Committee approve full rollout to Regions 2 and 3 a week ahead of the planned go/no-go date, rather than asking for a second, larger pilot first.

### Closure
The Finance monthly budget variance report and the Steering Committee cadence converged at closure into the formal benefits realisation report, with ownership and ongoing run-cost already communicated and agreed before the program formally closed — removing a common post-go-live friction point where nobody has agreed who owns an AI system in production.

---

## Communication Principles Applied

- **Bad news traveled faster than good news, on purpose.** The Week 8 precision miss and the Week 4 schedule slip were both surfaced the moment they were identified, not held for the next scheduled report.
- **The NOC was treated as a communication audience with influence, not just an information recipient.** Weekly working sessions with early prototype demos were specifically designed to build trust incrementally, given the team's prior negative experience with a vendor tool.
- **Every escalation came with a plan, not just a status.** Status reports during execution consistently paired each issue with a stated mitigation and a next-period focus, rather than reporting problems in isolation.
- **Scope-pressure requests were communicated as decisions, not absorbed silently.** When the Banking Ops Director requested a mid-execution extension to the ATM network, the response was communicated directly and logged formally (CR-03) rather than quietly worked around or quietly agreed to.

---

*Document produced as part of Phase 2 — Planning. Part of the [NetSentinel AI](./README.md) case study by Prachi Sharma.*
