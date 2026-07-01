# Lessons Learned

**NetSentinel AI — Predictive Network Incident Management & Auto-Remediation Platform**

> A reflective review produced as part of Phase 5 — Closure, captured while the delivery was still fresh. See the [Project Closure Report](./14-Project-Closure-Report.md) for the formal closure record and the [README](./README.md) for full project context.

---

## The Headline Lesson

The most impactful single decision in this program happened before any technical work started: making "predict-and-ticket, not auto-remediate" a hard design constraint written into the charter, rather than leaving it as a question to resolve later. It pre-empted the accountability argument that would have stalled sponsor sign-off, addressed the NOC's trust concern before it could harden into resistance, and gave every subsequent stakeholder conversation a settled answer to the hardest question about AI in operations. Closures don't usually name one decision as the reason a program succeeded — this one can.

---

## What Worked

### Scoping deliberately smaller than the obvious solution
A commercial AIOps platform was the obvious answer and it had already been tried and shelved. Proposing a narrow, focused model trained on Meridian's own historical data — rather than another platform pitch — rebuilt sponsor confidence where a bigger scope would have repeated the prior failure. The final results ($480K annualised savings, 73% prediction precision) came from a tighter, faster program, not a broader one.

**Carry forward:** When a category of solution has already failed with a sponsor, the response is not to propose it again with more budget or a different vendor — it's to ask what the smallest version of the answer would be that proves value quickly enough to earn further investment.

### The human-approval-gate constraint
Writing "no automated remediation without human sign-off" into the charter, before any technical design began, did three things simultaneously: it answered the accountability question that could have derailed sponsor sign-off, it gave the NOC a design they could live with, and it gave the PM a fixed point to anchor every subsequent conversation about automation. When scope pressure came — and it did — the charter constraint was the reference, not a negotiation.

At closure, the NOC Lead named this as the single biggest factor in team adoption. Not the precision numbers. Not the dashboard. The fact that the system was never going to act without asking them first.

**Carry forward:** For any AI-in-operations program in a regulated or infrastructure-heavy environment, settle the human-in-the-loop design in the charter — not in the architecture document, not in a sprint review. Charter constraints are harder to negotiate away mid-program than design choices.

### Proactive disclosure of the Week 8 precision miss
The model came in at 64% precision against a 70% charter target at the first evaluation. This was raised to the Sponsor and NOC Lead the same week it was found, with a specific hypothesis (missing change-proximity and utilisation-trend features) and a one-sprint plan to test it — not held for the next scheduled steering review.

At the rollout go/no-go gate, the Steering Committee specifically cited this early flag as a reason for confidence going into full-scale deployment, not a mark against the program. The lesson isn't just that transparency works — it's that transparency paired with a concrete plan works better than transparency alone. Raising a problem without a plan attached is an escalation; raising a problem with a plan attached is a managed issue.

**Carry forward:** Define what "immediately escalate" means before a program starts, not after a problem surfaces. On this program it meant: same week, to Sponsor and NOC Lead, with a hypothesis and a plan. That definition should be established at planning, not improvised under pressure.

### Treating the risk register as a living document
Every steering gate included a formal risk burn-down, not just a status update. This meant the Steering Committee's go/no-go decisions at the pilot gate and the rollout gate were based on a documented evidence base — which risks had closed, which were still active, and what monitoring was in place — rather than on assurances from the PM. The difference between an evidence-based go/no-go and an assurance-based one is measurable in stakeholder confidence.

**Carry forward:** A risk register that's only written at planning is a one-time artifact. A risk register that's reviewed at every gate is a governance tool. The extra effort per gate is small; the return in stakeholder confidence is significant.

---

## What to Do Differently

### Size the data-cleansing effort against the full historical volume from day one
The initial plan assumed 12 months of usable ServiceNow data. Actual historical volume was 18 months of tickets, with more data-quality issues at the older end than expected. Discovering this in Sprint 3–4 rather than at planning added time to the data foundation phase — manageable, but avoidable. The fix is straightforward: pull a representative sample of the full historical dataset in Phase 2 — Planning, before committing to a cleansing timeline, rather than after.

**Carry forward:** For any program where historical data is the training foundation, treat a representative data audit as a required planning deliverable, not a sprint 1 discovery task.

### Pull Security & Compliance into the data architecture conversation a week earlier
Security's sign-off on the in-region Azure ML approach came through cleanly, but later in planning than was ideal — a lot of downstream technical design depended on that decision being settled, and it was in limbo longer than it needed to be. The fix isn't more process; it's earlier scheduling of a single conversation that had to happen anyway.

**Carry forward:** Map the regulatory and compliance dependencies at the start of planning, identify the ones where a single sign-off gates a large amount of downstream work, and schedule those conversations first rather than in sequence with everything else.

### Build the NOC feedback mechanism into the MVP from sprint one
The NOC feedback/snooze mechanism — which let shift teams downrank unreliable prediction types — was added in Sprint 8 in response to an alert-fatigue concern raised during execution, rather than built from the start. It became one of the most actively used features post-launch. Adding it reactively rather than proactively meant an extra sprint's worth of work was threaded into an already-full execution phase, and the NOC didn't benefit from it during UAT, only after.

**Carry forward:** For any AI system that surfaces predictions to operational staff, build the feedback and calibration mechanism into the MVP. The people being shown predictions will always find patterns the model misses; the question is whether you give them a way to act on that knowledge from day one, or add it later.

---

## Reusable Patterns

**The phased-automation framing.** "Predict first, automate later, always with a human gate" is a repeatable trust-building structure for AI-in-operations programs. It answers the accountability question up front, gives the human team time to calibrate their trust in the model before any automation runs, and creates a natural evidence base for expanding automation later. The NOC went from skepticism at kickoff to requesting expansion of the feedback mechanism at closure — that trajectory was the direct result of starting with prediction-only, not automation.

**Evidence-based go/no-go gates.** The pilot go/no-go wasn't "we think it worked, let's proceed." It was a documented KPI table covering MTTR, SLA, precision, false-positive rate, and triage effort reduction — paired with an explicit, honest account of why the pilot sample was representative rather than cherry-picked. Steering Committee approval one week ahead of schedule was the outcome. That decision quality came from the documentation, not from confidence in the PM's word.

**The proactive-escalation-with-a-plan pattern.** Bad news early with a plan attached is a better outcome than bad news late without one. This is easy to say and harder to actually do when the news is "the model missed its precision target." The discipline is to hold the standard: same week, concrete hypothesis, concrete next step.

---

## Phase 2 Roadmap (Left Open at Closure)

CR-03 (ATM network extension) was formally reopened as a Phase 2 business case candidate. Two additional items were identified during closure as candidates for a future phase:

- Fully autonomous first-line remediation for well-validated, low-blast-radius incident types — building on the production track record established in Phase 1.
- Extending the NOC feedback mechanism to actively retrain the model on an ongoing basis, closing the loop between operational feedback and model performance.

Both require a new business case and sponsor approval rather than extension of this program's scope — a deliberate closure discipline, not a convenience.

---

*Part of the [NetSentinel AI](./README.md) case study by Prachi Sharma.*
