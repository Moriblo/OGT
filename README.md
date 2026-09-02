# OGT — Orchestration for Governance & Testing

## Overview

OGT (Orchestration for Governance & Testing) is an independent governance framework designed to evaluate governed executions against defined governance requirements, coordinate governance evaluation capabilities, and produce evidence-based findings, metrics, and recommendations for human governance review.

> **OGT is an independent governance evaluation framework. MARGO is its first empirical reference case, not an architectural dependency.**

OGT is intentionally decoupled from the implementation details of any governed agent, workflow, project, department, technology stack, or operational environment.

Its purpose is to provide a reusable governance evaluation capability that can be applied to different governed executions while preserving clear separation between:

- the governed agent or operational process being evaluated;
- the execution evidence produced by that execution;
- the governance evaluation performed by OGT;
- specialist evaluation capabilities that may extend OGT;
- contextual governance requirements and rules;
- and human governance authority.

## OGT as a Governance Evaluation and Orchestration Framework

OGT should not be understood as a governance testing engine only.

Testing is an important OGT capability, but the framework also evaluates, consolidates, and—at its extension level—orchestrates specialized governance evaluation capabilities.

The conceptual capability model is:

```text
                  OGT
                   │
        ┌──────────┼──────────┐
        │          │          │
     EVALUATE    TEST       ORCHESTRATE
        │          │          │
        │          │          └── Specialist Evaluators
        │          │              Extensions
        │          │              Context
        │          │              Evidence
        │          │
        │          └── Governance Tests
        │              Compliance Tests
        │              Test Vectors
        │
        └── Evidence
            Findings
            Metrics
            Specification Gaps
            Recommendations
```

This capability model is aligned with the OGT architectural evolution:

```text
OGT
│
├── OGT Core
│   ├── Evaluate
│   └── Test
│
└── OGT+
    ├── Evaluate
    ├── Test
    └── Orchestrate
        ├── Specialist Evaluators
        ├── Extensions
        ├── Context
        └── Evidence
```

The **OGT Core** establishes the foundational governance evaluation capability. It answers the fundamental question:

> **Did the execution comply with the specified governance?**

**OGT+** extends that foundation by coordinating approved specialized evaluation capabilities according to context. Its purpose is not merely to execute more tests, but to compose the capabilities necessary to evaluate whether an execution is adequate considering additional governance dimensions such as security, compliance, cost, operational performance, quality, and evolution.

The OGT+ composition remains contextual and governed; it must not silently redefine OGT Core.

## Core Principle

OGT does not replace human governance authority. It evaluates evidence, coordinates governed evaluation capabilities, and produces findings for human governance review.

The conceptual governance evaluation flow is:

```text
              GOVERNANCE CONTEXT
                     │
                     ▼
EXECUTION → EVIDENCE → OGT
                       │
             ┌─────────┼─────────┐
             ▼         ▼         ▼
          Evaluate   Test     Specialist
                                Evaluators
             │         │         │
             └─────────┼─────────┘
                       ▼
              GOVERNANCE FINDINGS
                       │
                       ▼
             HUMAN GOVERNANCE REVIEW
                       │
             ┌─────────┼─────────┐
             ▼         ▼         ▼
           ACCEPT     CHANGE   MORE EVIDENCE
```

In this flow, **Specialist Evaluators become part of the OGT+ extension capability**, while Evaluate and Test are present in both OGT Core and OGT+. Their scope, specialization, and composition are determined by the applicable governance context and approved extension model.


```text
GOVERNED EXECUTION
        ↓
EXECUTION EVIDENCE RECORD (EER)
        ↓
OGT
        ↓
GOVERNANCE FINDINGS
SPECIFICATION GAPS
METRICS / KPIs
        ↓
HUMAN GOVERNANCE REVIEW
        ↓
ACCEPT / CHANGE / MORE EVIDENCE
```

A subsequent execution produces a new EER. The original EER remains immutable as evidence of its execution cycle.

## OGT Roadmap

The current conceptual roadmap establishes a progressive evolution from OGT Core to OGT+:

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

The roadmap is intentionally incremental:

| Stage | Architectural role | Primary objective |
|---|---|---|
| **OGT Core** | Evaluate + Test | Evaluate execution against specified governance and perform governed testing |
| **OGT Extensions** | Extend evaluation capabilities | Add specialized, pluggable capabilities that can be qualified and governed |
| **OGT+ Readiness** | Evaluate + Test + Orchestrate | Demonstrate that Core and approved Extensions can operate as a governed composition |
| **OGT+ Continuous Governance** | Govern the evolving composition | Evolve the composition based on context, evidence, requirements, and approved changes |

OGT Extensions are evaluation capabilities, not merely tools. An Extension may use specialist agents, models, APIs, knowledge repositories, databases, external tools, or human specialists as evaluators.

## Human Governance

Human governance remains the decision authority.

OGT may identify:

- governance findings;
- specification gaps;
- evidence insufficiency;
- contextual governance concerns;
- metrics and KPI results;
- opportunities for improvement;
- and conditions requiring further evaluation.

These outputs do not, by themselves, constitute human authorization.

In particular, thresholds may trigger a governance action only where the applicable governance model explicitly defines such behavior. A threshold is not itself an authorization.

## Contextual Governance

OGT must support contextual governance without coupling its core to a specific domain.

Contextual governance rules may originate from an applicable process or governance specification. They may also be proposed or modified through analysis performed by qualified specialist evaluators.

Such proposals are not normative merely because an evaluator produced them. They require the applicable human governance approval before becoming authoritative governance rules.

This distinction is central to maintaining the separation between:

- evaluation;
- recommendation;
- governance rule definition;
- and governance authority.

## Separation of Governance and Process KPIs

OGT KPIs measure the performance or behavior of the governance evaluation itself.

Process or operational-flow KPIs belong to the specification of the process being governed, not to OGT's core modeling.

Therefore:

> **Process/flow KPIs must remain external to OGT Core and must not be embedded in OGT source code or OGT modeling artifacts.**

This allows the same OGT framework to evaluate different processes, departments, projects, or operational environments without becoming coupled to their individual performance models.

## Reference Case — MARGO

MARGO (Migration & Resource Governance Operator) is the first empirical reference case for OGT.

MARGO provides a concrete governed execution through which the OGT framework can be tested, challenged, and refined.

The relationship is intentionally one-way at the architectural level:

```text
MARGO execution
      ↓
     EER
      ↓
     OGT
      ↓
 evaluation / testing
      ↓
 governance findings
```

MARGO is therefore evidence for validating the framework, not a component required by the OGT architecture.

Case-specific evidence, observations, findings, and artifacts should remain identifiable as belonging to the reference case rather than being incorporated into the generic OGT specification without explicit governance.

## Current Repository Scope

The repository is intentionally minimal at this stage.

The initial baseline consists of:

```text
OGT/
├── README.md
└── OGT_MASTER_BLUEPRINT.md
```

The repository structure and additional artifacts will evolve incrementally according to the approved OGT Master Blueprint.

No implementation structure is implied by this initial repository layout.

## Master Blueprint

The **OGT Master Blueprint** is the governing planning and architecture baseline for the development of the framework.

It defines the terminology, lifecycle, steps and sub-steps, control model, inputs and outputs, gates and HITLs, evidence rules, test-vector model, KPI/metric model, traceability, documentation architecture, repository impact, and baseline/checkpoint governance.

The Blueprint also reserves the architecture for OGT Core, Extensions, OGT+ readiness, and continuous governance without prematurely imposing an implementation structure.

## Governing Statements

> **Treatment does not mean that OGT transforms governance. OGT orchestrates the capabilities necessary to evaluate and support the treatment of identified governance matters.**

> **OGT evaluates and orchestrates; human governance decides.**

These statements define the intended meaning of **Treatment** and the boundary between OGT capability and human governance authority. Treatment may result in acceptance, change, additional evidence, re-evaluation, or other governed action, but the applicable human authority determines the decision where human governance is required.

## Design Principles

OGT development follows these principles:

1. **Independence** — OGT must remain independent of any single governed agent or operational process.
2. **Evidence-based evaluation** — governance conclusions must be grounded in execution evidence.
3. **Human authority** — OGT evaluates and recommends; human governance retains decision authority.
4. **Decoupling** — Core governance evaluation must not be coupled to process-specific KPIs, security models, or domain-specific implementations.
5. **Incremental evolution** — capabilities are introduced progressively through controlled stages.
6. **Traceability** — findings and decisions must remain traceable to evidence and applicable governance requirements.
7. **Fail-closed governance** — ambiguity, insufficient evidence, or missing authorization must not silently become permission.
8. **Controlled extensibility** — specialist capabilities may extend evaluation without redefining OGT Core implicitly.
9. **Governed contextualization** — contextual rules may evolve, but proposed changes require appropriate governance authority.
10. **Separation of evidence and evaluation** — execution evidence remains distinct from the evaluation performed over it.

## Status

**Repository status:** Initial foundation

**Framework status:** OGT Master Blueprint established; implementation follows the approved roadmap and governance gates.

**Reference case:** MARGO Phase 0

The repository should evolve through explicit checkpoints rather than by treating successful implementation activity as authorization for subsequent stages.
