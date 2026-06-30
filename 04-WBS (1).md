# Work Breakdown Structure (WBS)

**NetSentinel AI — Predictive Network Incident Management & Auto-Remediation Platform**

> Produced during **Phase 2 — Planning**, translating the [Scope Statement](./03-Scope-Statement.md) into deliverables and owners. See the [README](./README.md) for full project context and the project schedule in [05-Stakeholder-Register.md](./05-Stakeholder-Register.md) for the milestone timeline this WBS maps to.

---

## WBS Hierarchy

**1.0 Data Foundation** — *Owner: Network Architect + Data Scientists*

- 1.1 Data source inventory & access provisioning — *Network Architect*
- 1.2 Historical incident/change data extraction & cleansing — *Data Scientist*
  - Includes a dedicated joint data-cleansing sprint with NOC SMEs to standardize free-text root-cause categories before feature engineering begins
- 1.3 Feature engineering (link utilisation, error rates, change proximity) — *Data Scientist*

**2.0 Model Development** — *Owner: Data Scientists*

- 2.1 Baseline model (XGBoost classifier) training & validation — *Data Scientist*
- 2.2 Threshold tuning for precision/recall trade-off — *Data Scientist*

**3.0 Platform Integration** — *Owner: ServiceNow Developer + Network Architect*

- 3.1 Cisco DNA Center / SolarWinds API integration — *Network Architect*
  - Includes a firmware upgrade workstream for 6 legacy branch switches lacking telemetry export capability
- 3.2 ServiceNow auto-ticketing workflow — *ServiceNow Developer*
- 3.3 Power BI NOC dashboard — *ServiceNow Developer*

**4.0 Validation & Rollout** — *Owner: PM + NOC Lead*

- 4.1 UAT with NOC shift teams — *NOC Lead*
- 4.2 Pilot on Region 1 (10 branches) — *PM*
- 4.3 Phased rollout — Regions 2 & 3 — *PM*

**5.0 Closure & Hypercare** — *Owner: PM*

- 5.1 UAT & cutover plan execution
- 5.2 Hypercare & training delivery (8 weeks)
- 5.3 Project closure report & benefits realisation
- 5.4 Lessons learned / retrospective

---

## WBS Summary Table

| WBS ID | Deliverable | Owner |
|---|---|---|
| 1.0 | Data Foundation | Network Architect + Data Scientists |
| 1.1 | Data source inventory & access provisioning | Network Architect |
| 1.2 | Historical incident/change data extraction & cleansing | Data Scientist |
| 1.3 | Feature engineering (link utilisation, error rates, change proximity) | Data Scientist |
| 2.0 | Model Development | Data Scientists |
| 2.1 | Baseline model (XGBoost classifier) training & validation | Data Scientist |
| 2.2 | Threshold tuning for precision/recall trade-off | Data Scientist |
| 3.0 | Platform Integration | ServiceNow Developer + Network Architect |
| 3.1 | Cisco DNA Center / SolarWinds API integration | Network Architect |
| 3.2 | ServiceNow auto-ticketing workflow | ServiceNow Developer |
| 3.3 | Power BI NOC dashboard | ServiceNow Developer |
| 4.0 | Validation & Rollout | PM + NOC Lead |
| 4.1 | UAT with NOC shift teams | NOC Lead |
| 4.2 | Pilot on Region 1 (10 branches) | PM |
| 4.3 | Phased rollout — Regions 2 & 3 | PM |
| 5.0 | Closure & Hypercare | PM |

---

## Schedule Mapping

| Week | Milestone | WBS Item |
|---|---|---|
| 1 | Charter signed; kickoff complete | — (Phase 1) |
| 2–3 | Data source access provisioned; scope & RACI finalised | 1.1 |
| 4–6 | Data cleansing & feature engineering complete | 1.2, 1.3 |
| 7–9 | Baseline model trained; precision/recall reviewed with stakeholders | 2.1, 2.2 |
| 10–11 | ServiceNow + DNA Center/SolarWinds integration built | 3.1, 3.2 |
| 12 | NOC dashboard delivered; internal demo | 3.3 |
| 13 | UAT with NOC shift teams | 4.1 |
| 14 | Pilot go-live — Region 1 (10 branches) | 4.2 |
| 15–16 | Pilot evaluation; go/no-go for full rollout | 4.2 |
| 17–24 | Phased rollout to Regions 2 & 3; hypercare & stabilisation | 4.3, 5.0 |

---

## Notes on Decomposition

- **WBS 1.2 absorbed more effort than originally estimated.** A mid-execution discovery that usable, well-labelled historical data only reliably extended back 12 months rather than the full 18 months initially assumed required replanning within this work package rather than a scope change — see the [RAID Log](./07-RAID-Log.md) for the full account.
- **WBS 3.1 carries a scope decision, not just a technical task.** The decision to fund a firmware upgrade for 6 legacy branch switches — rather than silently excluding them from the model's coverage — was made explicitly at the planning stage and is documented in the [Scope Statement](./03-Scope-Statement.md).
- **WBS 4.0 is phased by risk exposure**, starting with a single 10-branch region treated as a stress test before expanding to the remaining two regions, with an explicit go/no-go gate between phases.
- **WBS 5.0 extends 8 weeks beyond the nominal 16-week build**, reflecting that hypercare and model-performance monitoring were treated as a deliverable in their own right, not an informal wind-down period.

---

*Document produced as part of Phase 2 — Planning. Part of the [NetSentinel AI](./README.md) case study by Prachi Sharma.*
