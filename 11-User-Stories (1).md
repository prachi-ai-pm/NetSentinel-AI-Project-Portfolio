# User Stories

**NetSentinel AI — Predictive Network Incident Management & Auto-Remediation Platform**

> Detailed stories with acceptance criteria for the highest-priority items in the [Product Backlog](./10-Product-Backlog.md), written from each real stakeholder's perspective. See the [README](./README.md) for full project context.

---

## Epic 1 — Data Foundation

### US-01 — Standardised Root-Cause Taxonomy
**As a** Data Scientist
**I want** historical incident root-cause data standardised into a consistent taxonomy
**So that** I can engineer reliable features instead of training on inconsistent free-text labels

**Acceptance Criteria:**
- Free-text root-cause fields are mapped to a finite, agreed set of categories, jointly validated by NOC SMEs
- Mapping logic and edge cases are documented in a shared reference, not held only in one person's working notes
- At least 95% of the historical incident dataset is successfully categorised; remaining unmapped records are explicitly flagged, not silently dropped

**Linked backlog item:** BL-04 · **Linked risk:** [R1](./08-Risk-Register.md)

---

### US-02 — Change-Proximity Feature
**As a** Data Scientist
**I want** a feature capturing whether an incident occurred within 24 hours of a network change
**So that** the model can learn the relationship between configuration drift and incident likelihood

**Acceptance Criteria:**
- Feature correctly joins ServiceNow change records to incident records on affected configuration item and timestamp
- Feature is validated against a manually checked sample of known change-related incidents
- Feature materially improves model precision when added, confirmed via a re-training comparison against the baseline

**Linked backlog item:** BL-07 · **Linked issue:** [I2](./07-RAID-Log.md)

---

## Epic 2 — Model Development

### US-03 — Transparent Prediction Confidence
**As a** NOC shift engineer
**I want** every prediction to show a clear confidence score, not just a risk label
**So that** I can judge how much weight to give a prediction instead of treating every alert the same

**Acceptance Criteria:**
- Every prediction surfaced to the NOC includes a numeric or visual confidence indicator
- Confidence scoring methodology is documented in plain language the NOC Lead can explain to their shift teams
- Confidence threshold for triggering a ticket is conservative at launch, favouring fewer high-confidence predictions over a higher volume of low-confidence ones

**Linked backlog item:** BL-12 · **Linked risk:** [R4](./08-Risk-Register.md)

---

### US-04 — Precision Re-Training After a Missed Target
**As a** Sponsor
**I want** to be told immediately if the model misses its precision target, with a concrete remediation plan
**So that** I can trust the program is being managed transparently rather than discovering problems only at a scheduled review

**Acceptance Criteria:**
- Any precision result below the 70% charter target is escalated to the Sponsor within the same review cycle it's discovered, not held for the next scheduled checkpoint
- The escalation includes a specific, testable hypothesis for the shortfall and a defined timeline to test it
- A re-training result is reported back against the original target, not against a quietly revised one

**Linked backlog item:** BL-10 · **Linked issue:** [I2](./07-RAID-Log.md)

---

## Epic 3 — Platform Integration

### US-05 — Auto-Created Ticket With Correct Routing
**As a** NOC shift engineer
**I want** auto-created ServiceNow tickets to be correctly linked to the right configuration item
**So that** predicted incidents are routed to the team that actually owns the affected system, without manual correction

**Acceptance Criteria:**
- Auto-created tickets inherit the correct CMDB configuration item link for the predicted network element
- A validation step specifically targeting ticket-routing accuracy is included in UAT, not assumed to be covered by general functional testing
- Zero misrouted tickets occur during the UAT validation pass before pilot go-live

**Linked backlog item:** BL-17 · **Linked issue:** [I3](./07-RAID-Log.md)

---

### US-06 — Batch Scoring Within API Constraints
**As a** Network Architect
**I want** the model to score network elements on a batch cadence that respects Cisco DNA Center's API rate limits
**So that** the prediction pipeline doesn't fail or get throttled in production

**Acceptance Criteria:**
- Scoring cadence is tested against actual DNA Center API rate limits before being committed to the schedule, not assumed from documentation alone
- Initial cadence (5-minute batches) is documented along with the rationale for not pursuing real-time streaming
- Cadence can be tuned (e.g. to 2-minute batches) without a full re-architecture, validated by the post-pilot change (CR-04)

**Linked backlog item:** BL-15 · **Linked risk:** [R5](./08-Risk-Register.md)

---

## Epic 4 — Human-in-the-Loop & Trust Design

### US-07 — Human Approval Before Any Automated Change
**As a** Security & Compliance Lead
**I want** absolute certainty that no automated change reaches the production network without human approval
**So that** the program meets banking-grade change control requirements and I can sign off on the architecture with confidence

**Acceptance Criteria:**
- The system architecture has no code path by which a prediction can trigger a production network change without an explicit human approval step
- This constraint is documented in the charter and verified at each phase gate, not only checked once at design time
- Zero unplanned production changes from automation occur across pilot and full rollout

**Linked backlog item:** BL-20 · **Linked risk:** [R6](./08-Risk-Register.md)

---

### US-08 — Feedback Mechanism for Noisy Predictions
**As a** NOC shift lead
**I want** a way to flag or downrank prediction types that turn out to be unreliable in practice
**So that** the system improves from our operational experience instead of becoming "just more noise" we have to tolerate

**Acceptance Criteria:**
- NOC shift engineers can mark a prediction type as low-value directly from the working interface, without filing a separate request
- Downranked prediction types are visibly deprioritised in future scoring, with the change reflected within a defined period
- NOC feedback volume and action taken on it is visible to the NOC Lead, not a black box

**Linked backlog item:** BL-21 · **Linked issue:** [I4](./07-RAID-Log.md)

---

## Epic 5 — Validation & Rollout

### US-09 — NOC-Led UAT Sign-Off
**As a** NOC Lead
**I want** genuine sign-off authority over UAT, not just visibility into testing someone else has already decided is complete
**So that** my team trusts the system because they tested and approved it, not because it was handed to them finished

**Acceptance Criteria:**
- UAT is executed by NOC shift teams across all shifts, not a single representative session
- UAT explicitly covers prediction accuracy review, ticket routing validation, and dashboard usability
- Go/no-go for pilot requires NOC Lead sign-off as a named RACI "Responsible" party, not merely "Informed"

**Linked backlog item:** BL-23 · **Linked stakeholder concern:** [R3](./08-Risk-Register.md)

---

### US-10 — Safe Pilot Rollback
**As a** Sponsor
**I want** a fast, well-defined way to roll back to manual monitoring if the model underperforms during pilot
**So that** approving the pilot doesn't carry unacceptable downside risk to live operations

**Acceptance Criteria:**
- Auto-ticketing can be disabled and the system reverted to manual NOC monitoring within 30 minutes
- A clear, documented precision floor (60%) defines the trigger condition for considering rollback
- Rollback procedure is tested before pilot go-live, not assumed to work based on design alone

**Linked backlog item:** BL-26

---

### US-11 — Stress-Test Pilot Region Selection
**As a** Steering Committee member
**I want** the pilot region chosen to genuinely represent the program's hardest conditions
**So that** strong pilot results give me real confidence in full-scale rollout, not a best-case result that won't generalise

**Acceptance Criteria:**
- Pilot region selection criteria are documented and shared with the Steering Committee before pilot go-live, not justified only after results are in
- Selected region includes the highest-incident-volume branches and at least some of the legacy switches addressed via firmware upgrade
- Pilot results are reported alongside the rationale for why the region was a stress test, not a showcase

**Linked backlog item:** BL-25

---

### US-12 — Documented Ownership Handoff at Closure
**As an** incoming BAU owner (NOC Lead)
**I want** a clear runbook and defined ongoing cost before the project formally closes
**So that** I'm not left owning a production AI system with undocumented procedures or an unbudgeted run cost

**Acceptance Criteria:**
- A runbook covering model monitoring, feedback-loop usage, and escalation path for model anomalies is handed to the NOC Lead before hypercare ends
- Ongoing run cost (e.g. Azure ML compute) is calculated and communicated to Finance before closure, not discovered after
- Ownership of each ongoing governance activity (precision review, anomaly escalation) is assigned to a named role, not left ambiguous

**Linked backlog item:** Closure deliverable, see [README](./README.md) outcome snapshot

---

*Part of the [NetSentinel AI](./README.md) case study by Prachi Sharma.*
