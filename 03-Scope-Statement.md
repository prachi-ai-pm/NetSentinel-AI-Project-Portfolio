# Scope Statement

**NetSentinel AI — Predictive Network Incident Management & Auto-Remediation Platform**

> Produced during **Phase 2 — Planning**, translating the [Project Charter](./01-Project-Charter.md) into executable scope. See the [README](./README.md) for full project context and [04-WBS.md](./04-WBS.md) for how this scope was broken into deliverables.

---

## In Scope

- Predictive model covering WAN links, core/branch switches, and routers across 3 regional data centres and 40 branches.
- Data pipeline integrating SolarWinds NPM, Cisco DNA Center telemetry, and 3 years of ServiceNow incident/change history.
- Automated ServiceNow ticket creation with predicted root cause and confidence score.
- NOC-facing Power BI dashboard for prediction visibility and model performance tracking.
- Human-approval gate before any automated remediation action.

## Out of Scope

*(Carried from the Charter, reconfirmed at planning.)*

- Endpoint/desktop devices and application-layer monitoring.
- Security incident detection/response — remains with SOC's existing tooling.
- Fully autonomous remediation — deferred to a potential Phase 2 business case.
- Branch hardware refresh.

---

## Key Constraints

- **Banking-grade change control:** no automated changes without a human approval gate in Phase 1.
- **Data residency:** all data and ML compute must remain in-region.
- **NOC shift structure:** the existing NOC shift structure cannot change as a condition of this program.

## Success Criteria

| Criterion | Target |
|---|---|
| Mean Time to Resolve (MTTR) | ≤ 2.8 hrs |
| SLA compliance | ≥ 95% |
| P1/P2 incidents predicted ahead of breach | ≥ 60% |
| Model precision | ≥ 70% |
| Unplanned production network changes from automation | Zero |

---

## How Scope Boundaries Were Defended

The explicit out-of-scope list was written into both the charter and this scope statement together, and was deliberately reconfirmed at every steering review rather than assumed to hold once agreed. This pre-empted the most predictable scope-creep pressure — requests to extend the model to endpoints or applications — by giving the PM a standing reference to point back to rather than relitigating the boundary each time it was raised. Any genuine extension request was required to go through a formal change request rather than be absorbed informally; see [Risk Register](./08-Risk-Register.md) item R7 and change request CR-03 in the [RAID Log](./07-RAID-Log.md).

### A Scope Decision Made Deliberately, Not by Default

Six branch switches were end-of-life and did not export telemetry the way the rest of the fleet did. Rather than silently excluding them — which would have created a monitoring blind spot in exactly the locations most likely to fail — a firmware upgrade for those six branches was scoped into the plan. The explicit fallback was agreed up front: if the upgrade slipped, those branches would be excluded from Phase 1 and the gap flagged explicitly, rather than the scope quietly shrinking without anyone noticing. This decision is tracked as Risk R2 in the [Risk Register](./08-Risk-Register.md).

### Phased Rollout Scope

| Phase | Scope | Timing |
|---|---|---|
| Pilot | Region 1 (10 branches) | Week 14 |
| Pilot evaluation | Go/no-go decision for full rollout | Weeks 15–16 |
| Full rollout | Regions 2 & 3, phased two weeks apart | Weeks 17–24 (alongside hypercare) |

The pilot was deliberately framed as a stress test, not a best-case showcase — addressing steering committee caution about generalizing results from a 10-branch pilot to the full network before committing to full rollout.

---

## Forward-Looking Note

CR-03 (ATM network extension) was raised as a scope-extension request during execution and was not absorbed into this program's scope. It was formally reopened at closure as a Phase 2 business case candidate, giving the sponsor a credible next step rather than a closed conversation — see [Lessons Learned](./README.md) for the closure-stage detail.

---

*Document produced as part of Phase 2 — Planning. Part of the [NetSentinel AI](./README.md) case study by Prachi Sharma.*
