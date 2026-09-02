# OGT — Master Blueprint

**Version:** 0.2 Proposed Revision  
**Status:** Updated for human review and approval  
**Previous approved baseline:** Version 0.1  
**Scope:** Generic, independent OGT governance-evaluation agent/framework  
**Reference case:** MARGO Phase 0 (first empirical case only)

## 1. Purpose

The OGT receives an **Execution Evidence Record (EER)** produced by a governed agent and evaluates that execution against an explicit governance model. It produces evidence-based reconstruction, governance findings, specification gaps, metrics, and recommendations for **Human Governance Review**.

The OGT is independent of the governed agent. MARGO is the first evaluation case, not a dependency of the generic framework.

> The OGT evaluates evidence; it does not manufacture governance authority.

## 2. Core Architecture

```text
┌─────────────────────────────┐
│       GOVERNED AGENT        │
│  MARGO / Agent X / Agent Y  │
└──────────────┬──────────────┘
               │ Execution Evidence
               ▼
┌─────────────────────────────┐
│             EER             │
│  Execution Evidence Record  │
│   preserved / immutable     │
└──────────────┬──────────────┘
               │ input
               ▼
┌─────────────────────────────┐
│             OGT             │
│ Governance Evaluation Agent │
│                             │
│ S0 Evidence                 │
│ S1 Reconstruction           │
│ S2 Governance Interaction   │
│ S3 Observational Testing    │
│ S4 Findings                 │
│ S5 Assessment               │
│ S6 Human Review              │
│ S7 Improvement              │
│ S8 Closure                  │
│ S9 Re-evaluation            │
└──────────────┬──────────────┘
               ▼
      HUMAN GOVERNANCE REVIEW
```

## 3. OGT Roadmap

The OGT is defined as a **progressive governance capability**, not as a monolithic implementation that must contain all future evaluation domains from its first release.

```text
                         OGT ROADMAP
                              │
               ┌──────────────┴──────────────┐
               │                             │
           OGT CORE                    EXTENSION ARCHITECTURE
               │                             │
               ▼                             ▼
     "Did the execution             Specialist capabilities
      comply with the                that are pluggable,
      specified governance?"         contextual, and decoupled
               │                             │
               └──────────────┬──────────────┘
                              ▼
                            OGT+
                              │
             "Is the execution adequate considering
              governance, security, compliance, cost,
              operational performance, quality,
              and evolution?"
```

### 3.1 Roadmap Timeline

| Stage | Where it is defined / originates | Where it is operationalized | Primary objective |
|---|---|---|---|
| **OGT Core** | P0.1–P0.15, with the Core boundary explicitly controlled through P0.4 | S0–S6 | Evaluate an execution against the governance specified for that execution |
| **OGT Extensions** | Extension architecture in P0.4–P0.10; extension lifecycle introduced in S7 | S7–S8 | Add specialized, governed, plug-in evaluation capabilities without coupling them to the Core |
| **OGT+ Readiness** | Composition and readiness criteria defined through S7 and validated through S8 | S8–S9 | Demonstrate that OGT Core + applicable governed Extensions can operate as a coherent, governed composition |
| **OGT+ Continuous Governance** | Continuous-governance rules established through S9 and subsequent approved framework evolution | Subsequent evaluation cycles | Evolve the composition according to context, evidence, approved requirements, and new governance needs |

### 3.2 Architectural Meaning of the Stages

**OGT Core** is deliberately narrow. Its first governing question is:

> **Did the execution comply with the specified governance?**

The Core must remain domain-agnostic and must not embed process-specific KPIs, department-specific rules, security profiles, regulatory catalogues, or specialist evaluation logic.

**OGT Extensions** provide specialized evaluation capabilities. An Extension is a governed evaluation capability, not merely a software tool. An Extension may use specialist agents, models, APIs, knowledge repositories, databases, external tools, or human specialists.

**OGT+** is not a separate monolithic product. It is a **contextual composition of OGT Core and one or more governed Extensions** selected according to the scope, context, risk, and governance requirements of the evaluated execution or process.

### 3.3 Contextual Governance Rule Evolution

Contextual governance rules are supplied by the applicable process or governance specification, but they may also be **identified, challenged, refined, added, or proposed for modification by specialist evaluators** when their domain analysis reveals a relevant governance requirement.

Such evaluator-originated rules are initially **candidate governance requirements/rules**. They do not become normative merely because an evaluator proposes them.

Any addition or modification that changes the applicable governance baseline must preserve provenance, rationale, evidence, scope, versioning, and the required human governance authority. The applicable approval gate is defined by the governance model and must not be bypassed by the evaluator or by OGT automation.

This permits contextual governance to evolve without embedding contextual rules in OGT Core or OGT+.

### 3.4 Separation of KPI Ownership

Process-specific KPIs belong to the **applicable process specification**, not to OGT Core and not to OGT+.

For example, PMO process KPIs may be defined in the governance/process specification for the PMO workflow. Another department may define a different KPI set for its own workflow.

OGT Core provides the generic capability to ingest, evaluate, calculate, and trace applicable metrics according to the governing specification. OGT+ may use specialized evaluation capabilities to assess such metrics, but must not hard-code a department's KPI catalogue.

The same separation applies to security requirements, regulatory requirements, data classifications, and other context-dependent governance rules.

### 3.5 OGT+ Readiness Principle

OGT+ readiness is a **governance condition**, not simply a technical integration milestone.

Readiness requires, at minimum, that:

- the Core boundary is preserved;
- applicable Extensions are specified and qualified;
- Extension evidence requirements are defined;
- Extension governance and decision authority are defined;
- contextual selection criteria are defined;
- Test Vectors cover the relevant capabilities;
- traceability is preserved across Core and Extensions;
- human review authority remains explicit;
- failure, conflict, insufficiency, and unresolved behavior are defined;
- changes to Extensions and their governance remain controlled.

## 3. Governance Improvement Loop

```text
EXECUTION → EER → OGT → HUMAN GOVERNANCE REVIEW
                         │
              ┌──────────┼──────────┐
              ▼          ▼          ▼
           ACCEPT      CHANGE   MORE EVIDENCE
                         │          │
                         ▼          │
                    IMPROVEMENT     │
                         │          │
                         ▼          │
                  NEW EXECUTION     │
                         │          │
                         ▼          │
                        EER ────────┘
                         │
                         ▼
                        OGT
                         │
                         ▼
                 EXIT CONDITION
                         │
                         ▼
               EVALUATION CLOSED
```

A new execution produces a **new EER**. The original EER is never rewritten. The unit that closes is the **evaluation cycle**, not an individual EER.

## 4. Foundational Principles

1. Evidence before conclusion.
2. Preserve the original EER before analysis.
3. Separate observation from assessment.
4. Trace expected behavior to observed behavior.
5. Human intervention is evidence, not automatically failure.
6. Distinguish specification gaps from agent failures.
7. Insufficient evidence is not automatically failure.
8. OGT recommends; human authority decides wherever HITL is required.
9. OGT cannot silently change its own governance model.
10. Authorizations are explicit, scoped, and non-reusable.
11. Improvement is controlled, traceable, and followed by re-evaluation where required.
12. Exit conditions are explicit and governed.
13. OGT Core remains domain-agnostic and independently governed.
14. Specialized evaluation capabilities are implemented as governed Extensions rather than embedded in the Core.
15. OGT+ is a contextual composition of Core and applicable governed Extensions, not a monolithic replacement for the Core.
16. Process-specific KPIs and contextual governance requirements remain external to OGT Core and OGT+.
17. Specialist evaluators may originate candidate contextual governance requirements, but normative changes require the applicable human governance authority.

# PART I — PRE-STEP

## P0.1 — Terminology Consolidation

**Objective:** establish the generic vocabulary.

**Define/validate:** OGT, EER, Test Vector, Finding, Governance Gap, Specification Gap, Agent Failure, Evidence Insufficiency, HITL, Human Governance Review, Improvement, New Execution, Evaluation Cycle, Exit Condition.

**Output:** terminology baseline and glossary candidate.

**Human decision:** approve normative terminology.

## P0.2 — Lifecycle Consolidation

**Objective:** consolidate S0–S9 as one coherent lifecycle.

**Activities:** validate order, dependencies, convergence points, parallelizable analysis, decision gates, loop and closure behavior.

**Output:** lifecycle baseline.

## P0.3 — Step/Sub-step Consolidation

**Objective:** define every Step and Sub-step sufficiently to execute the methodology without relying on lost conversational context.

**Output:** complete S0–S9 catalogue.

## P0.4 — Step/Sub-step Control Matrix

This is a primary governance artifact.

| Field | Required meaning |
|---|---|
| Step | Lifecycle stage |
| Sub-step | Atomic process unit |
| Activity | What is performed |
| Input | Required input |
| Output | Produced result |
| Evidence | Proof of completion |
| Dependency | Required predecessor |
| Parallelizable | Whether execution may overlap |
| Human Decision | Whether human authority is required |
| HITL | Applicable gate |
| Repository Change | Whether artifacts may change |
| Stop Condition | Condition requiring stop |
| Gate | Transition criterion |
| Responsibility | Accountable actor |
| Capability Stage | Core / Extension / OGT+ Readiness / Continuous Governance |
| Context Dependency | Whether the control depends on process, department, project, sector, geography, risk, or other context |
| Extension Dependency | Applicable specialist capability, if any |
| Rule Origin | Process/governance specification, specialist evaluator proposal, or other approved source |
| Rule Authority | Authority required to make a contextual rule normative |

**Control principle:** parallel execution never creates parallel decision authority.

## P0.5 — Input / Output Model

**Objective:** map all inputs, outputs, persistent artifacts, transient data, mandatory inputs, optional inputs, and dependency chains.

**Output:** lifecycle I/O map, including Core/Extension interfaces and context-dependent inputs.

## P0.6 — Gates, HITLs & Branches

**Objective:** define decision authority.

**Must distinguish:** formal HITL, operational approval, human intervention, Human Governance Review, authorization scope, negative/cancellation events, A/B/C branches.

**Branches:**
- **A — ACCEPT:** current governance state accepted.
- **B — CHANGE:** controlled improvement required.
- **C — MORE EVIDENCE:** evidence insufficient/contradictory.

**Output:** gate and decision-authority model, including Extension approval and contextual-rule approval paths.

## P0.7 — Test Vector Model

**Objective:** define the reusable observational governance test unit.

**Candidate fields:** ID, governance domain, scenario, trigger, preconditions, expected behavior, required evidence, observed behavior, human intervention, classification, finding reference, KPI relevance, decision reference.

**Output:** Test Vector model and register structure, including a mechanism for specialist Extension test semantics without coupling them to the Core.

## P0.8 — KPI & Metrics Model

**Objective:** formally define metrics before they become normative.

Every KPI must specify: ID, name, purpose, scope, numerator, denominator, variables, formula, unit, source, timing, interpretation, threshold, limitations, and human-decision relevance.

**Candidate metrics:** OGT Pass Rate, Explicit Compliance Rate, Implicit Compliance Rate, Partial Rate, Failure Rate, Unresolved Rate, Human Intervention Dependency (HID), Human Course-Correction Success Rate.

**Output:** KPI model, including separation between OGT KPIs and externally supplied process/department KPIs.

## P0.9 — Traceability Model

**Objective:** ensure every material conclusion traces to evidence.

```text
EER → Evidence Event → Reconstruction → Governance Interaction
    → Test Vector → Expected/Observed → Finding → Assessment
    → Human Decision → Improvement/Closure
```

**Output:** traceability model.

## P0.10 — Evidence Rules

**Objective:** define integrity, provenance, sufficiency, conflict, missing evidence, preservation, and retention rules.

**Output:** evidence rules, including provenance and integrity requirements for specialist-evaluator evidence and contextual-rule proposals.

## P0.11 — Control Matrix Validation

**Objective:** validate completeness and consistency of the matrix.

**Checks:** missing I/O, circular dependencies, missing gates, undocumented human decisions, undocumented repository impact, unbounded activities, missing stop conditions.

**Output:** validated matrix and unresolved design questions.

## P0.12 — Documentation Architecture

**Objective:** decide the generic OGT documentation set.

**Candidate artifacts:** `OGT.md`, `OGT_EXECUTION_PLAYBOOK.md`, `GLOSSARY.md`, `GOVERNANCE_MODEL.md`, `EER_SPECIFICATION.md`, `TEST_VECTOR_MODEL.md`, `KPI_MODEL.md`, templates, examples.

**Rule:** generic documents must not embed MARGO assumptions.

The documentation architecture must also preserve the OGT roadmap boundary:
Core specification, Extension specifications, contextual process/governance
specifications, and OGT+ composition/readiness artifacts must remain separately
identifiable and versionable.

## P0.13 — Repository Impact Assessment

**Objective:** decide where OGT lives architecturally.

**Questions:** independent repository, temporary POC, relationship to MARGO repository, versioning, evidence boundaries, release boundaries, repository impact.

**Output:** repository architecture recommendation, including boundaries for Core, Extensions, contextual specifications, and evidence.

## P0.14 — GitHub / OneDrive Structure

**Objective:** define authoritative storage boundaries.

**Questions:** source-controlled artifacts, evidence, working material, persistent governance documentation, collaboration material, immutable evidence references.

**Output:** storage architecture decision, including authoritative locations for Core/Extension specifications and context-specific governance artifacts.

## P0.15 — Baseline / Checkpoint Governance

**Objective:** protect accepted baselines before further work.

**Reference baseline:** MARGO Phase 0 commit `9bc937c — feat: establish Phase 0 repository foundation`, synchronized with `origin/main`.

**Output:** protected-baseline confirmation and checkpoint rules.

**Human decision:** required for changes to an accepted baseline.

# PART II — OGT LIFECYCLE

## STEP 0 — Evidence Intake & Preservation

**Question:** Is the evidentiary foundation valid and sufficient?

### S0.1 — EER Intake
Receive the EER.

### S0.2 — EER Identity & Metadata
Capture execution ID, governed-agent identity/version, timestamps, scope, provenance and available metadata.

### S0.3 — Evidence Integrity Check
Verify that the supplied evidence can be treated as the reference record.

### S0.4 — Evidence Sufficiency Check
Determine whether evaluation can begin.

### S0.5 — Evidence Preservation
Preserve the original EER unchanged.

### S0.6 — Evaluation Scope Definition
Define exactly what execution/governance scope is being evaluated.

**Output:** Evidence Intake Record (candidate name; subject to P0.1).

**Stop:** missing/unidentifiable EER, failed integrity where required, or insufficient evidence without an authorized recovery path.

## STEP 1 — Execution Reconstruction

**Question:** What happened?

### S1.1 Timeline Reconstruction
### S1.2 Agent State Reconstruction
### S1.3 Action Reconstruction
### S1.4 Decision Reconstruction
### S1.5 Human Interaction Reconstruction
### S1.6 Authorization Reconstruction
### S1.7 Intervention & Exception Reconstruction
### S1.8 State Transition Reconstruction
### S1.9 Evidence-to-Event Traceability

**Output:** Execution Reconstruction Record.

No normative judgment is made here unless required to disambiguate the reconstruction.

## STEP 2 — Governance Interaction Analysis

**Question:** How did governance operate?

### S2.1 Governance Gate Identification
### S2.2 Authorization Identification
### S2.3 Authorization Scope Analysis
### S2.4 Operational Approval Identification
### S2.5 Human Intervention Identification
### S2.6 Negative / Cancellation Event Identification
### S2.7 Human Course-Correction Analysis
### S2.8 Authorization Reuse Analysis
### S2.9 Governance Dependency Identification

**Output:** Governance Interaction Record.

## STEP 3 — Observational Governance Testing

**Question:** Did observed behavior satisfy the applicable governance expectation?

### S3.1 Governance Scenario Identification
### S3.2 Governance Objective Definition
### S3.3 Governance Trigger Identification
### S3.4 Test Vector Extraction
### S3.5 Expected Behavior Definition
### S3.6 Observed Behavior Mapping
### S3.7 Expected-vs-Observed Evaluation
### S3.8 Evidence Mapping
### S3.9 Human Intervention Correlation
### S3.10 Test Classification

**Candidate classifications:** PASS, PARTIAL, AGENT FAILURE, GOVERNANCE GAP, SPECIFICATION GAP, EVIDENCE INSUFFICIENT/UNRESOLVED, OTHER (if approved).

**Outputs:** OGT Catalogue and Test Vector Register.

## STEP 4 — Findings & Traceability

### S4.1 Finding Identification
### S4.2 Finding Classification
### S4.3 Evidence Linkage
### S4.4 Expected-vs-Observed Traceability
### S4.5 Governance Gap Characterization
### S4.6 Specification Gap Characterization
### S4.7 Agent Behavior Failure Characterization
### S4.8 Evidence Insufficiency Characterization
### S4.9 Candidate Requirement Extraction
### S4.10 Candidate Requirement Destination
### S4.11 Finding Severity / Priority
### S4.12 Finding Status

**Output:** Findings & Traceability Register (FTR).

## STEP 5 — Governance Assessment

### S5.1 — Historical Observation
Record observations without prematurely converting them into normative conclusions.

**Output:** Historical Observation Record (HOR).

### S5.2 — Governance Assessment
Assess gate effectiveness, authority, intervention, autonomy, undocumented rules, and prevention of unsafe progression.

**Output:** Governance Assessment Record (GAR).

### S5.3 — Specification Assessment
Assess whether expected behavior, stop conditions, authorization boundaries and edge cases were sufficiently specified.

**Output:** Specification Assessment Record (SAR).

### S5.4 — Improvement Decision
Convert accepted findings into candidate/approved improvement decisions and destinations.

**Output:** Improvement Decision Record (IDR).

### S5.5 — KPI & Metric Definition / Calculation
For every KPI define variables, formula, source, unit, threshold, interpretation and limitations before calculation.

Candidate formulas:

- **OGT Pass Rate:** `N_PASS / N_TV`
- **Explicit Compliance Rate:** `N_EXPLICIT_COMPLIANT / N_RELEVANT`
- **Implicit Compliance Rate:** `N_IMPLICIT_COMPLIANT / N_RELEVANT`
- **Partial Rate:** `N_PARTIAL / N_RELEVANT`
- **Failure Rate:** `N_FAILURE / N_RELEVANT`
- **Unresolved Rate:** `N_UNRESOLVED / N_RELEVANT`
- **Human Intervention Dependency (candidate):** `N_REQUIRED_HUMAN_INTERVENTIONS / N_RELEVANT_EXECUTION_EVENTS`
- **Human Course-Correction Success Rate:** `N_SUCCESSFUL_COURSE_CORRECTIONS / N_COURSE_CORRECTIONS`

These are candidate definitions until P0.8/P0.11 validate their semantics.

**Important:** a KPI threshold is a trigger only if governance explicitly defines it as such. A threshold does not itself constitute authorization.

## STEP 6 — Human Governance Review Gate

This is the formal human decision point after evidence, reconstruction, testing, findings, assessment and metrics are consolidated.

### S6.1 Review Package Preparation
### S6.2 Human Governance Review
### S6.3 Decision Recording
### S6.4 Branch Selection
### S6.5 Decision Scope Validation
### S6.6 Exit / Loop Determination

### Branch A — ACCEPT
Accept the current governance state for the applicable evaluation cycle.

### Branch B — CHANGE
Authorize/require controlled improvement.

### Branch C — MORE EVIDENCE
Require additional evidence or analysis before a reliable decision.

## EXIT MODEL

The Exit Model belongs to the lifecycle and is evaluated through S6.6 and subsequent re-evaluation controls.

### Candidate continuation triggers
- Human Governance Review requires change;
- required improvement remains unverified;
- approved KPI threshold triggers re-evaluation;
- governance rule requires re-evaluation;
- material unresolved finding remains;
- additional evidence is required;
- human authority explicitly requests another evaluation.

### Candidate exit conditions
- Human Governance Review accepts the state;
- required improvements are completed and, where required, re-evaluated;
- mandatory KPI conditions are satisfied where applicable;
- no unresolved critical finding remains;
- no mandatory re-evaluation trigger remains;
- evidence and traceability are complete.

These are candidate rules until formally approved.

## STEP 7 — Governance Improvement & Framework Consolidation

### S7.1 Accepted Improvement Identification
### S7.2 Governance Requirement Update
### S7.3 Specification Update
### S7.4 Test Vector Library Update
### S7.5 OGT Methodology Update
### S7.6 KPI Model Update
### S7.7 Lessons Learned Consolidation
### S7.8 Framework Versioning

### S7.9 Extension Need Identification
Identify a governance capability that cannot or should not be embedded in OGT Core and determine whether an Extension is warranted.

### S7.10 Extension Specification
Define the Extension objective, scope, inputs, evidence requirements, outputs, applicable contexts, limitations, dependencies, and governance boundaries.

### S7.11 Specialist Evaluator Qualification
Assess candidate evaluator(s) that may provide the Extension capability, including provenance, scope, evidence quality, limitations, version, and fitness for the intended governance purpose.

### S7.12 Extension Governance & Approval
Define the human authority, HITLs, decision scope, and conditions under which the Extension may be used.

### S7.13 Contextual Governance Rule Proposal
Allow a specialist evaluator to propose additions or modifications to contextual governance requirements when supported by domain evidence. Record the proposal separately from the normative governance baseline until approved.

### S7.14 Extension Integration & Traceability
Integrate the approved Extension through a defined interface while preserving independent provenance, evidence, findings, and traceability.

### S7.15 OGT+ Composition Definition
Define which Core capabilities and approved Extensions compose the target OGT+ configuration for a given context.

**Authority rule:** OGT may observe and recommend; human governance authorizes changes where required. The OGT or an Extension cannot unilaterally alter its own governance model, make a contextual rule normative, or authorize its own deployment.

## STEP 8 — Evaluation Closure & Evidence Package

### S8.1 Findings Closure
### S8.2 Decision Recording
### S8.3 Evidence Package Consolidation
### S8.4 KPI Finalization
### S8.5 Traceability Closure
### S8.6 Evaluation Versioning
### S8.7 Evaluation Completion

### S8.8 OGT+ Readiness Assessment
Assess whether the required Core + Extension composition satisfies the approved readiness criteria for the applicable context.

### S8.9 Readiness Evidence & Decision Package
Consolidate the evidence supporting readiness, unresolved issues, limitations, Extension versions, contextual rules, and applicable human decisions.

**Output:** Governance Evaluation Package (candidate name; subject to P0.1), including OGT+ readiness evidence where applicable.

## STEP 9 — Re-evaluation / Continuous Governance

### S9.1 Re-evaluation Trigger Detection
Possible triggers: approved HITL, approved KPI threshold, mandatory governance rule, material behavioral change, unresolved critical finding, additional evidence, or explicit Human Governance Review decision.

### S9.2 Trigger Validation
Confirm trigger applicability and authorization.

### S9.3 New Execution Initiation
The governed agent performs a new execution under its own authorization model.

### S9.4 New EER Generation
The new execution produces a new immutable EER.

### S9.5 New OGT Evaluation
The new EER re-enters Step 0.

### S9.6 Comparative Assessment
Compare iterations where relevant.

### S9.7 Improvement Effectiveness Assessment
Determine whether an accepted improvement achieved the intended governance effect.

### S9.8 Exit Condition Evaluation
Apply the approved Exit Model.

### S9.9 Cycle Closure or Continuation
Close the evaluation cycle or return to the applicable loop.

### S9.10 Extension Change Detection
Detect material changes in an Extension, specialist evaluator, external source, regulation, tool, or dependency that may affect evaluation validity.

### S9.11 Contextual Governance Change Assessment
Assess whether a proposed or observed contextual governance change affects the applicable OGT+ composition or evaluation baseline.

### S9.12 OGT+ Requalification
Re-evaluate the affected Extension or composition when approved governance rules require it.

### S9.13 Continuous Governance Exit
Apply the approved conditions for continuing, reconfiguring, suspending, or closing the OGT+ composition.

# PART III — OGT SELF-GOVERNANCE

## 23. OGT Governance Principle

The OGT is itself a governed agent/framework. It therefore cannot be the sole authority for determining the adequacy of its own governance model.

## 24. Critical OGT HITL Points

At minimum, the governance model must consider HITL for:

1. approval of the OGT governance model;
2. approval of normative classification rules;
3. approval of KPI definitions that can trigger governance action;
4. approval of KPI thresholds that can trigger re-evaluation;
5. approval of material methodology changes;
6. approval of changes to the EER contract;
7. approval of changes to Test Vector semantics;
8. approval of Exit Model changes;
9. approval of material changes to decision authority;
10. closure when critical/unresolved findings remain.

Exact HITL IDs, scope and gates are to be defined through P0.6/P0.8/P0.10/P0.11 and the corresponding lifecycle gates.

## 25. No Self-Authorization

OGT execution, successful step completion, KPI thresholds, previous approvals, silence, inferred intent, and automated transitions cannot substitute for required human authority.

# PART IV — ANALYTICAL MODELS

## 26. Prompt/Specification Compliance vs Governance Compliance

| | Specification adequate | Specification inadequate |
|---|---|---|
| Agent compliant | PASS / GOOD | Governance or specification gap |
| Agent non-compliant | Agent failure | Ambiguous; requires assessment |
| Evidence insufficient | Unresolved | Unresolved |

## 27. Human Intervention Analysis

Human intervention may indicate expected operation, a formal governance gate, correction of agent failure, specification ambiguity, an undocumented governance rule, evidence insufficiency, or emergency stop/cancellation.

The OGT must classify the intervention from evidence rather than assume its meaning.

## 28. Improvement Governance

```text
Observation → Recommendation → HUMAN DECISION → Implementation
                                      ↓
                                New Execution
                                      ↓
                                     EER
                                      ↓
                                     OGT
                                      ↓
                               Verification
```

## Reference Case — MARGO Phase 0

MARGO Phase 0 is designated as the first empirical reference case
for the validation of the generic OGT framework.

The reference case is not a normative architectural dependency of OGT.

Case-specific evidence, observations, findings, and analysis must be
maintained separately from the generic OGT specification. The reference
case may be used to validate, challenge, or refine the framework, but
must not silently redefine its normative rules.

# PART V — CONTROL & ARCHITECTURE

## 30. Lifecycle Control Summary

| Step | Purpose | Main output | Human authority |
|---|---|---|---|
| S0 | Evidence | EIR | If required by evidence/scope rules |
| S1 | Reconstruction | Reconstruction Record | As needed for ambiguity |
| S2 | Governance analysis | Governance Interaction Record | As required |
| S3 | Testing | OGT Catalogue / TV Register | As required |
| S4 | Findings | FTR | As required |
| S5 | Assessment | HOR/GAR/SAR/IDR/KPIs | As required |
| S6 | Review | Decision Record | **Yes** |
| S7 | Improvement | Versioned changes | **Yes where governed** |
| S8 | Closure | GEP | **Yes where governed** |
| S9 | Re-evaluation | New evaluation | **Yes where trigger requires** |

## 31. Formal Lifecycle

```text
PRE-STEP P0.1–P0.15
          ↓
S0 Evidence → S1 Reconstruction → S2 Governance
          ↓
S3 Testing → S4 Findings → S5 Assessment
          ↓
S6 HUMAN GOVERNANCE REVIEW
          ├── A ACCEPT ──────────────┐
          ├── B CHANGE → S7 → S9 ────┤
          └── C MORE EVIDENCE ───────┤
                                     ↓
                                    S8
                                     ↓
                              EVALUATION CLOSED
```

## 32. Candidate Artifact Architecture

After blueprint approval and repository-impact decisions, candidate artifacts are:

```text
OGT.md
OGT_EXECUTION_PLAYBOOK.md
GLOSSARY.md
GOVERNANCE_MODEL.md
EER_SPECIFICATION.md
TEST_VECTOR_MODEL.md
KPI_MODEL.md
templates/
examples/
```

No candidate artifact is implied to be created by this blueprint alone.

# PART VI — OPEN DECISIONS

1. Final terminology.
2. Final EER schema.
3. Final Test Vector schema.
4. Final classification taxonomy.
5. Final HID semantics and formula.
6. Definition of a relevant execution event.
7. KPI threshold semantics.
8. Final Exit Model.
9. Exact OGT self-governance HITLs.
10. Repository architecture.
11. GitHub / OneDrive boundaries.
12. Artifact naming/versioning.
13. Evidence retention model.
14. Whether OGT is implemented as agent, framework, or both.
15. Whether multiple implementations may conform to the same OGT specification.
16. Final definition of the OGT Extension contract.
17. Final Extension qualification criteria.
18. Final contextual-rule proposal and approval model.
19. Final Specialist Capability Registry model, if adopted.
20. Final OGT+ composition and readiness criteria.
21. Final separation between process-specific governance specifications and OGT/OGT+ artifacts.

# PART VII — ACCEPTANCE CRITERIA

The blueprint is ready for formal approval when:

- P0.1–P0.15 are defined;
- S0–S9 and their sub-steps are defined;
- the Control Matrix is complete;
- dependencies and parallelization rules are explicit;
- human decision points are explicit;
- Exit Model is explicitly governed;
- OGT self-governance and HITLs are explicit;
- EER is independent of MARGO;
- Test Vector model exists;
- KPI definitions include variables and formulas;
- evidence preservation is explicit;
- A/B/C branches are explicit;
- Improvement → New Execution is explicit;
- new executions create new EERs;
- closure applies to the evaluation cycle, not the historical EER;
- repository impact is assessed;
- implementation is not implied without authorization.

# 33. Governance Invariant

> **Automation may receive, preserve, analyze, evaluate, and recommend based on execution evidence, but it must never infer or manufacture the human governance authority required to approve a governed decision, alter its own governance model, or close a mandatory human decision gate.**

# 34. Current Status

**Version 0.2 — proposed revision, pending human review and approval.**

Version 0.1 remains the previously approved baseline. This revision incorporates
the OGT roadmap (Core → Extensions → OGT+ Readiness → OGT+ Continuous Governance),
the explicit Step/Sub-step placement of those capabilities, the separation of
process-specific KPIs and contextual security/governance rules, and the controlled
ability for specialist evaluators to propose contextual governance changes.

No OGT implementation is authorized by this document. No MARGO Phase 1 activity
is authorized. No repository modification is implied.
