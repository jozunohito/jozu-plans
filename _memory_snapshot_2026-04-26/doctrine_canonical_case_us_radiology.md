---
name: Canonical Case — US Radiology OCR to Revenue Infrastructure ($30K → $1.6M ARR)
description: The reference pattern for converting a commodity technical ask into enterprise revenue optimization infrastructure. Technical symptom to revenue system. Incumbent displacement.
type: reference
originSessionId: b76896f1-74c9-4dc1-9c8f-284044f2d492
---
# CANONICAL CASE: US RADIOLOGY OCR → REVENUE OPTIMIZATION INFRASTRUCTURE

**Classification:** Canonical pattern. The third of three core Jozu cases, encoding the technical-symptom-to-revenue-system reframe and the displacement of an entrenched incumbent through broader workflow ownership. Confirmed mapping to the public "Beyond OCR / Healthcare Services" case on jozuconsultinggroup.com. $1.6M ARR expanding to ~$7M TCV over the multi-year contract.

**Status:** v1.0 from Jeff's verbatim anonymized facts, 2026-04-22.

## Facts on record

- Client: large, venture-backed national radiology organization consolidating imaging centers across the US.
- Operating model: centralized centers of excellence for scheduling and patient intake. 5.5M faxed physician orders per year. Manual processing of handwritten orders.
- Initial ask: OCR for fax ingestion, commodity pricing ~$0.005/page, estimated deal ~$30K annually.
- Underlying problem: revenue leakage from delayed intake and failed patient engagement, compounding against venture-funded imaging equipment (MRI, CT) whose economics depend on utilization.
- Incumbent competitor: handling patient messaging with strong internal presence and board-level relationships.
- Execution: ~40 meetings, ~12 on-site, 6-8 month sales cycle.
- Outcome: ~$1.6M ARR, multi-year contract, incumbent displaced, full intake-to-engagement workflow control.

## 1. PROBLEM DECOMPOSITION

**Stated technical problem:**
OCR for fax ingestion. A pure commodity technical ask at unit pricing. Narrow scope. No strategic positioning. No economic linkage.

**Actual operational problem:**
The radiology organization's centers of excellence received physician orders via fax simultaneously across multiple centers. Centers competed internally to contact and schedule the patient first. Manual intake delayed the outreach. Delays cost the organization the patient.

The operational sequence was:
- Physician order faxed to multiple centers.
- Each center manually processed the order.
- First center to reach the patient won the scheduling.
- Delays = patients drifted, no-showed, or were scheduled by a competing center in the network.

**Underlying economic problem:**
Imaging equipment (MRI, CT) was venture-funded. Each machine's unit economics depended entirely on utilization rate. Idle machines = direct revenue loss. Underutilized technicians = fixed cost against zero variable revenue. Lost patient first-interactions = lost lifetime value (repeat procedures, preventative care referrals, procedural follow-ups).

The economic consequence was:
- Per-machine revenue at risk per day of underutilization.
- First-patient-contact correlation with lifetime patient value.
- No-show and cancellation rates as a function of patient engagement quality.
- Venture-backed growth thesis dependent on proving utilization economics.

**Separation of layers:**

| Layer | Framing | Budget line |
|---|---|---|
| Technical symptom | OCR accuracy on faxed orders | IT budget, ~$30K |
| Operational inefficiency | Intake delay, manual routing, engagement gaps | Operations budget, $200K-$500K range |
| Financial consequence | Idle machine revenue loss, lost patient LTV | CFO/COO budget, $1M+ range tied to revenue optimization |

A seller who accepts the technical framing wins a $30K deal. A seller who reaches the financial layer wins a $1.6M ARR deal.

## 2. DISCOVERY ANALYSIS

**Signals that indicated a larger problem:**

- The 5.5M annual volume itself. At that volume, any intake latency has operational consequences regardless of per-page OCR accuracy.
- "Centers of excellence" model with multiple simultaneous recipients. This is an operational coordination pattern, not a data-entry pattern.
- Venture backing of the parent. Venture-funded organizations have utilization-driven growth theses, which means utilization-limiting factors are board-visible.
- Imaging equipment (MRI, CT) is capital-intensive. Capital-intensive assets have utilization economics that make every minute of idle time expensive.
- Manual processing at that volume means dozens of FTEs. That is a COO/CFO budget line, not an IT budget line.

**How the seller moved beyond the initial ask:**

Used the Five-Level Deep Discovery framework:
- Level 1 (Surface Symptom): "OCR accuracy on physician order faxes."
- Level 2 (Stated Problem): "We need to reduce manual processing errors and cost."
- Level 3 (Operational Impact): "Intake delays mean centers lose patients to other centers in the network or drop them altogether. Manual exception handling adds hours per order."
- Level 4 (Economic Impact): "Each delay-driven no-show costs the full margin of that patient's visit plus lifetime value. Underutilized imaging machines are direct revenue loss against venture-funded capex."
- Level 5 (Root Constraint + Unconsidered Need): "The organization has no integrated intake-to-engagement system. The board-level growth thesis (utilization economics) depends on fixing this. OCR is one symptom. Patient engagement is another. Center-to-center routing is another. The root constraint is absence of a revenue optimization infrastructure covering the full workflow from physician order to patient procedure."

Each level was buyer-validated before the seller advanced.

**Why most sellers would have stopped at OCR:**

- The buyer introduced the problem as OCR. Most sellers take the buyer's framing as authoritative.
- OCR is a clean, purchasable, vendor-category product. Sellers feel safe selling it.
- IT is the easiest stakeholder to reach and pitch. Sellers default to the easiest-accessible buyer.
- $30K is a fast close. Fast closes feel like wins.
- Expanding scope feels presumptuous. Most sellers do not have the operator credibility to expand scope without looking opportunistic.

Ending at Level 2 produces a $30K commodity deal. The $1.6M ARR outcome required reaching Level 5.

## 3. VALUE WEDGE IDENTIFICATION

**What commodity vendors were selling:**

OCR tools at $0.005 per page. Throughput metrics. Field-accuracy statistics. API integrations. Volume pricing tiers.

**Why that leads to low deal value:**

- Unit pricing caps deal size at the volume × unit price.
- Every OCR vendor competes on the same accuracy/throughput/cost dimensions.
- Procurement treats OCR as a fungible utility.
- No path to stakeholder expansion because IT owns the scope.
- No economic anchor because the conversation is about data entry cost, not revenue.

**The seller's unique capabilities:**

Not one capability but an integrated system:
1. **Intelligent Ingestion:** OCR with confidence scoring, not just extraction.
2. **Automated Exception Handling:** system-generated outbound to physician offices for unreadable fields, with image-based feedback for rapid correction.
3. **Real-Time Routing:** immediate ingestion into backend systems, location-based routing to optimal center, prioritization of speed-to-engagement.
4. **Patient Engagement Layer:** automated outreach to patients, procedure education, confidence-building to reduce no-shows, confirmation workflows.

The differentiation is the integration. Any single layer is replicable by a point-solution vendor. The complete pipeline (order → validation → scheduling → engagement → utilization) is not.

**Why competitors could not match this:**

- OCR vendors lacked patient engagement capability.
- Patient engagement vendors (including the incumbent) lacked upstream ingestion.
- Scheduling systems lacked either side.
- No vendor had built the continuous pipeline from fax ingestion to patient confirmation as a single operating system.

The Value Wedge lived in the full-workflow ownership. A buyer comparing the seller's bid to any other vendor's bid was not comparing equivalent things. The comparison collapsed because no other bid addressed the Root Constraint (revenue optimization infrastructure).

## 4. ECONOMIC REFRAMING

**Move from "cost per page" to "revenue per machine":**

The OCR unit-price frame locates the deal in IT budget. The revenue-per-machine frame locates the deal in COO/CFO budget. Same company, different budget authority, different decision thresholds, different deal sizes.

| Unit-price frame | Revenue frame |
|---|---|
| $0.005 per page | $X per day of machine utilization |
| $30K annual IT purchase | Seven-figure revenue optimization |
| Data entry cost reduction | Patient lifetime value capture |
| OCR accuracy metrics | Utilization rate and no-show reduction metrics |
| IT buyer | COO / CFO / Ops leadership buyer |

**Financial impact of idle machines:**

- MRI capital cost is significant (often $1M+ per machine). Depreciation and financing costs accrue regardless of utilization.
- Technicians staffed to operate are fixed cost against variable revenue.
- Every hour of idle time is lost revenue at the procedure's full price.
- At multi-center scale, a few percentage points of utilization gain translates to seven-figure annual revenue impact.

**Cost of delayed engagement:**

- First engagement determines long-term patient relationship. A patient reached slowly goes to a competitor's center, or drops the order entirely.
- No-show rates correlate inversely with engagement quality. Well-engaged patients show up. Neglected patients do not.
- Every no-show is lost revenue plus lost downstream LTV (the follow-up procedure, the preventative referral, the family member).

**Value of capturing first patient interaction:**

- The center that reaches the patient first owns the relationship for the procedure.
- In multi-center networks, internal competition for patients makes speed-to-engagement a zero-sum operational game. Faster center wins.
- Repeat imaging is common for many conditions. First-touch patients return.

**Impact of reducing no-shows:**

- No-show reduction of a few percentage points at millions of orders = tens of thousands of additional procedures annually.
- Each procedure has a gross margin measurable in hundreds of dollars.
- Annual revenue impact of no-show reduction easily exceeds the total deal value. The deal funds itself in year one at modest no-show improvements.

This is the economic case presented to the CFO. At the CFO's budget authority, $1.6M ARR for a system that protects multi-million-dollar annual revenue is a straightforward investment decision.

## 5. SOLUTION EXPANSION MODEL

### Three-layer evolution

**Layer 1: OCR Tool ($30K range)**
- Accepts faxed orders.
- Extracts text.
- Delivers to downstream systems.
- Commodity product. Price-competitive. IT procurement.

**Layer 2: Operational System ($200-500K range)**
- OCR with confidence scoring.
- Automated exception handling (outbound to physician offices for unreadable fields).
- Real-time routing to optimal center.
- Reduces manual FTE load. COO budget.

**Layer 3: Revenue Optimization Engine ($1.6M ARR)**
- All of Layer 2, plus:
- Patient engagement layer: outreach, education, confidence-building, confirmation.
- Closed-loop workflow from physician order to patient procedure.
- Measurable utilization lift and no-show reduction.
- CFO/COO budget. Board-visible metric.

### Role of each layer in deal size expansion

- Layer 1 is defensive (solving stated problem). Price is the only variable.
- Layer 2 is operational (saving FTE cost, reducing errors). Cost-savings frame.
- Layer 3 is revenue (capturing previously lost revenue). Economic-value frame.

The deal size is a direct function of which layer the conversation reaches. A seller who presents only Layer 1 earns a Layer 1 deal. A seller who earns access to Layer 3 conversations earns a Layer 3 deal.

## 6. STAKEHOLDER EXPANSION

**Initial stakeholder scope:**
- Director of IT or similar, focused on OCR procurement.
- Possibly a vendor-management procurement contact.

**Expanded stakeholder set:**
- **CIO:** system integration, data infrastructure, IT architecture fit.
- **COO:** operational workflow ownership, FTE impact, center performance.
- **CFO:** revenue implications, capex utilization, LTV economics.
- **Operations leadership:** center directors, scheduling leads, patient intake managers.
- **VC board members (indirect):** utilization economics are a board-level growth thesis component. Board visibility via CFO reporting.

**Why economic framing required C-level involvement:**

The OCR conversation lives in IT. The workflow conversation lives in Operations. The revenue conversation lives in Finance and at the board. Each stakeholder has a different decision threshold, a different budget size, and a different definition of success. Expanding the stakeholder set from IT to C-suite expanded both the decision authority and the deal economics.

Every stakeholder meeting produced a Plan Letter that validated the relevant framing with that stakeholder's language. CIO saw integration and security language. COO saw workflow and throughput language. CFO saw utilization and revenue language. All three letters pointed at the same underlying system but framed to each stakeholder's economic lens.

## 7. COMPETITIVE DISPLACEMENT

### Why the incumbent had structural advantage

- Strong internal presence through existing engagement work.
- Board-level relationships providing political insulation.
- Known entity with established procurement relationships.
- Point-solution credibility (they did engagement well within their scope).

In most procurement decisions, the incumbent wins unless displaced by clear economic or strategic advantage.

### How the seller overcame that advantage

1. **Expanded upstream.** The incumbent owned the patient engagement layer. The seller built a solution that started at intake (upstream of the incumbent) and extended through engagement (overlapping the incumbent's turf, then exceeding it).
2. **Owned the full workflow.** The incumbent was a component. The seller was the system. A buyer comparing a component to a system is comparing unequal things.
3. **Changed the economic conversation.** The incumbent was billed against the patient engagement budget line. The seller was billed against revenue optimization, a larger budget with a different authority.
4. **Reframed the incumbent as replaceable.** When the seller owned intake, validation, and routing, the engagement layer could be provided internally or by the seller's integrated system. The incumbent's relationship was no longer load-bearing.

### Why broader system ownership defeated point-solution incumbency

Incumbency is defensive. The incumbent's advantage is status-quo inertia. That inertia only applies within the incumbent's defined scope. When the scope expands beyond the incumbent's product, the incumbent's relational capital does not transfer. The seller was not fighting the incumbent for patient engagement. The seller was replacing the category in which patient engagement was one sub-component.

Board-level relationships at the incumbent mattered less once the deal was a revenue-optimization decision at the CFO level, with a scope the incumbent could not bid.

## 7a. INCUMBENT RENEWAL AS FORCING FUNCTION (load-bearing correction)

**The gate truth.** The OCR engagement by itself did not pass either Buying Cycle Alignment gate. No Active Evaluation existed on an OCR RFP in the window that would carry a $1.6M ARR deal. No Quantified Severity was attached to OCR as a line item; $30K does not clear a CFO threshold on its own.

**What actually created both gates.** The incumbent patient-engagement vendor had a contract renewal dated inside the same procurement window. That renewal, not the OCR ask, was the forcing function. Jeff anchored the deal to the renewal:

- **Active Evaluation.** The plan had to decide whether to renew the incumbent. That is an active evaluation by definition. Once Jeff's scope expanded to cover the incumbent's patient-engagement workload plus intake plus routing, the decision became: "renew the incumbent at current scope, or redirect the incumbent's spend into a broader revenue-optimization platform." Both gates now had an anchor.
- **Quantified Severity.** The incumbent's annual run-rate was the majority of the revenue funding the new work. Redirecting that spend into the integrated platform was not "new budget." It was a reallocation. The severity case was built on two numbers: what the incumbent cost annually, and what the integrated platform produced in utilization lift, no-show reduction, and LTV capture. Severity was quantified against dollars already being spent.

**Why this matters as doctrine.** The deal was not won by "finding a buyer who wanted OCR." The deal was won by identifying an existing forcing function inside the account (the incumbent's renewal date) and anchoring the reframe to it. The OCR ask was the door. The incumbent's renewal was the clock. The reframe was the scope. All three are required.

**Widen, not walk.** When discovery reveals that a narrow technical ask has no Active Evaluation and no Quantified Severity at its own scope, the correct move is not to exit. The correct move is to widen: surface the larger use case, follow the economic pain downstream, and tie the solution to an existing forcing function inside the account. Contract renewals, regulatory deadlines, board-level numbers, and budget cycles are the forcing functions most commonly available. The radiology deal is the canonical teaching case.

## 8. DEAL CONTROL MECHANICS

### How sequence of events was established

The seller constructed a Mutual Sequence of Events early in the cycle covering:
- Stakeholder discovery (CIO, COO, CFO, Ops leadership).
- Validation of problem severity with each stakeholder.
- Agreement on success criteria (utilization lift target, no-show reduction target).
- Technical demo scoped to the full workflow, not just OCR.
- Security and compliance review (HIPAA, PHI handling).
- Commercial structuring against the revenue-optimization scope.
- Executive approval at C-suite.
- Contract execution.
- Implementation plan tied to operational go-live milestones.

Each step was buyer-validated in writing through Plan Letters.

### How timeline drove momentum

- Go-live milestones were anchored to operational events (next quarter's center integration, next physician referral cycle).
- Delays in the sales cycle would push go-live past target utilization periods, forfeiting the revenue impact the business case depended on.
- The seller used those anchor dates to create urgency against the buyer's own operational calendar.

### Why the seller had high confidence before close

- Every stakeholder conversation was documented in a Plan Letter validated by that stakeholder.
- Every step of the Sequence of Events was buyer-confirmed in writing.
- Procurement, legal, security, and technical evaluations were sequenced as parallel workstreams, not end-of-cycle gates.
- The economic buyer (CFO) had signed off on the economic case before the contract draft landed.
- The incumbent's counter-position was known and addressed in writing in the Plan Letters.

The final stages were not negotiation on price. They were execution of a pre-validated Sequence.

## 9. EFFORT VS OUTCOME MODEL

### Why this deal required extended engagement

- ~40 meetings, ~12 on-site, 6-8 months.
- The scope expansion from $30K to $1.6M ARR required stakeholder expansion from a single IT contact to C-suite plus ops leadership plus technical teams.
- Each stakeholder required independent discovery, Plan Letter validation, and sequence alignment.
- Incumbent displacement required additional work to reframe the category.
- Complex workflow solution required technical due diligence that simple OCR would not.

### Why high-value deals demand multi-threading and persistence

- Enterprise deals are approved by committees, not individuals. Every committee member has veto power. Each requires engagement.
- Economic consequence at seven figures triggers CFO and risk-management scrutiny that smaller deals avoid.
- Operational change of this scope touches multiple departments. Any unaligned department becomes a blocker.
- Long sales cycles are a feature of enterprise-scale outcomes, not a bug.

### Why most sellers fail in long-cycle environments

- Pipeline-volume compensation incentivizes shallow multi-deal work over deep single-deal work.
- Monthly forecasting encourages closing small deals fast rather than building large deals slowly.
- 6-8 month cycles look bad on monthly dashboards even when the eventual deal is 50× the quick wins.
- Most sellers do not have the process discipline (Plan Letters + Sequence of Events) to maintain deal control across 40 meetings without drift.

Jeff's outsized output (~10× peer) at Ushur is produced by sustaining the discipline through the long cycle. Peers started the same deals and lost control by meeting 15.

## 10. FAILURE MODE COMPARISON

**If seller had accepted OCR framing:**
- Deal size: ~$30K annually.
- Stakeholder: IT only.
- Competitive pressure: high. Every OCR vendor competes.
- Relationship: vendor-to-buyer transactional.
- Future expansion: unlikely. OCR is the ceiling in that stakeholder's budget.

**If seller had priced per page:**
- Deal size: capped at volume × unit price.
- Scope: ingestion only.
- Margin: commodity.
- Incumbent competitors: unbeatable on price alone.

**If seller had not expanded stakeholders:**
- Ceiling: IT-level decision authority, ~$100K max.
- Blind spot: revenue conversation never happens because IT does not own revenue.
- Outcome: small win or loss on price.

**If seller had not tied to revenue:**
- Conversation stays in cost-savings frame.
- Ceiling: FTE-replacement cost, moderate deal size.
- No CFO engagement because no revenue mechanism visible.
- Outcome: Layer 2 deal at best, around $200-500K.

**Contrast with actual outcome:**

| Path | Deal size | Stakeholder | Competitive position |
|---|---|---|---|
| OCR framing | ~$30K | IT | Commodity |
| Per-page pricing | Volume × unit | IT + procurement | Price-only |
| No stakeholder expansion | ~$100K | IT | Narrow |
| No revenue tie | $200-500K | Ops | Cost-savings |
| **Actual: full workflow, revenue frame, C-suite** | **$1.6M ARR** | **CIO/COO/CFO/Ops** | **Alone at full scope** |

## 11. SYSTEM EXTRACTION (Reusable Decision Framework)

### Trigger conditions (seller recognizes when to apply this pattern)

1. Buyer presents a **technical problem** framed at **unit pricing**.
2. The buyer's operation has **high volume** (meaningful scale of the technical problem).
3. There are **revenue-generating assets downstream** of the technical workflow (equipment, patients, transactions, accounts).
4. There are **delays in process flow** (manual steps, exception handling, routing decisions) that create friction between the technical workflow and revenue realization.

### When all four are present, apply:

**Step A: Trace the workflow to revenue impact.** Follow the technical workflow downstream until it reaches a revenue-generating asset or event. That is where the Root Constraint lives.

**Step B: Quantify the revenue leakage.** In the buyer's own numbers: idle-asset revenue loss per unit time, no-show/cancellation revenue impact, first-touch LTV capture, utilization rate economics. These numbers convert the conversation from technical cost to revenue.

**Step C: Expand scope from point to system.** Define the solution as the complete pipeline from technical ingestion to revenue-realization. Single-layer products become components within your system.

**Step D: Engage economic buyers.** Expand from technical stakeholder (IT) to operational (COO), financial (CFO), and strategic (CEO, board) depending on the revenue scale. Each stakeholder gets their own Plan Letter in their own economic language.

**Step E: Reframe from cost to revenue.** Unit pricing never wins enterprise deals. Revenue framing always exceeds cost framing in budget authority and deal size. Move the budget line from IT to revenue optimization.

**Step F: Displace incumbents at the category boundary, not within their turf.** If a competitor is entrenched in a narrow scope, do not fight them on that scope. Expand above or below and reframe the category so their scope is one component of yours.

**Step G: Commit to the long cycle.** 40 meetings and 6-8 months is the cost of enterprise scale. Plan Letters + Sequence of Events are the discipline that sustains control across that cycle.

### Decision framework (condensed)

> When you see a technical problem at unit pricing with high volume and revenue-generating assets downstream with process-flow delays: trace the workflow to revenue, quantify the leakage, expand scope to the full pipeline, engage economic buyers with stakeholder-specific Plan Letters, reframe from cost to revenue, displace incumbents at the category boundary not within their scope, and sustain deal control through Plan Letters and Sequence of Events across the long cycle.

## 12. INTEGRATION INTO JOZU ENTERPRISE REVENUE SYSTEM

**Value Wedge:** the integrated intake-to-engagement workflow. No competitor had assembled the complete pipeline. The Wedge produced scope that could not be price-compared to any point-solution bid.

**Deep Discovery (Five Levels):** walked from OCR (Level 1) to revenue optimization infrastructure (Level 5). The seller's job at Level 5 was to connect physician-order-ingestion latency to venture-backed imaging-equipment utilization economics. That is a cross-domain jump most sellers cannot make.

**Power Messaging (Why This / Why Now):**
- **Why This Solution:** constraint match (addresses intake-to-revenue pipeline as single system), differentiated capability (only vendor with full-workflow ownership), supporting evidence (buyer-validated operational observations and quantified revenue leakage).
- **Why Act Now:** visible cost of inaction (ongoing idle-machine revenue loss), active financial loss (no-show revenue impact occurring every day), delay increasing risk (venture growth thesis timing, board-visible utilization metrics).

**Buying Cycle Alignment (Two Gates):**
- **Gate One:** active evaluation or change cycle? NOT initially on OCR. The OCR ask alone did not clear the gate. Gate One was cleared by anchoring the deal to the incumbent's contract renewal, which was an active evaluation already in motion inside the account.
- **Gate Two:** problem severity quantified? NOT at the OCR layer. Severity was built at Level 5 with utilization economics, no-show revenue numbers, and the incumbent's annual run-rate as the reallocation base.
- **Teaching point.** Both gates were created by widening the scope and tying the solution to the incumbent's renewal as the forcing function, not by finding gates pre-built around the OCR ask.

**Plan Letter:** at least one per stakeholder meeting across ~40 meetings, each reframed for the stakeholder's economic lens. This is the discipline that carried control across a 6-8 month cycle.

**Mutual Sequence of Events (Nine Steps):**
- Evaluation Phase (1-5) spanned the multi-month discovery across stakeholders, including security/compliance review for PHI handling.
- Execution Phase (6-9) compressed once economic approval was secured, since the Sequence had been validated in writing throughout.

**Infrastructure Pillars:** meeting objectives per meeting (distinct per stakeholder). CRM discovery fields populated per stakeholder. Plan Letters after every meeting (especially critical at 40 meeting volume). Mutual Action Plan mandatory and progressively refined.

## Canonical status

This case is now encoded as the reference pattern for:

- Converting technical unit-priced asks into revenue-optimization enterprise deals.
- Expanding scope from point solution to full workflow ownership.
- Displacing entrenched incumbents through category expansion rather than within-scope competition.
- Sustaining deal control through long (6-8 month, 40-meeting) enterprise cycles.
- Multi-stakeholder economic reframing (IT to COO to CFO).

Any future engagement presenting a technical unit-priced ask + high volume + downstream revenue assets + process delays should open with reference to this pattern. Specific variables change. Structural moves do not.

---

## CROSS-CASE PATTERN SUMMARY (across all three canonical cases)

| | California Health Plan (Wildfire Messaging) | CalOptima (Medicaid → Stars) | US Radiology (OCR → Revenue) |
|---|---|---|---|
| Stated ask | Bulk messaging | Redetermination outreach | OCR fax ingestion |
| Initial frame | Per-transaction | Threshold-bounded urgent | Unit pricing technical |
| Land scope | $200K | $249K | $30K |
| Final outcome | $1.4M ARR ($4.2M TCV) | ~$3M ARR (~$10M TCV) | $1.6M ARR (~$7M TCV) |
| Multiplier | 7× | ~40× | 53× |
| Core reframe | Transaction → Standing capability | Narrow use case → Enterprise scope via partners | Technical symptom → Revenue infrastructure |
| New doctrine component | Pre-authorized unlimited capacity offer design | Threshold-Constrained Entry, Partner Orchestration, Internal Resistance, Procurement Discipline | Revenue-per-asset reframe, incumbent displacement via category expansion |
| Stakeholder shift | Procurement → CMO/GC/Gov Affairs | Member Experience → Clinical/Quality/Gov Affairs/CEO | IT → CIO/COO/CFO |
| Cycle length | Multi-quarter | Land fast, RFP 4-6 months | 6-8 months |
| Competitive structure | Commoditized RFP | Multi-partner enterprise bid | Point-solution incumbent displacement |

Three cases, one system. The Jozu Enterprise Revenue System (Deep Discovery Five Levels → Value Wedge → Power Messaging → Plan Letter → Mutual Sequence of Events → Buying Cycle Alignment) operates across all three with different core patterns surfaced by each.
