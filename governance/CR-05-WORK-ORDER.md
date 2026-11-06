# CR-05 Work Order — TalkTrace v0.3.0-candidate

**Authority:** [TalkTrace Issue #12](https://github.com/orinmuse/TalkTrace/issues/12)  
**Base:** `main@f8220d2281bd64209a461115798c3b4fd142c7c2`  
**Branch:** `work/cr05-as-is-method-v0.3.0-candidate`  
**Authorization:** FROZEN / BOUNDED EXECUTION AUTHORIZED  
**Release boundary:** Candidate branch + PR only. No merge, Registry promotion, release, or Drive package replacement.

## 1. Problem statement

TalkTrace v0.2.0-candidate demonstrated useful daily-batch synthesis and evidence discipline in a process-oriented case (cross-professional resource coordination). It did not adequately test management-system As-Is mapping (e.g. compensation/performance, organization, job/grade architecture). Its current references still give Source–Point–Line–Surface–Outcome–Loop too much default influence over investigation planning.

This is a method-selection and coverage problem, not a reason to discard the daily-batch engine or the six-layer practice-tracing method.

## 2. Frozen method contract

### 2.1 Internal purpose routing

Select the investigation strategy from the user's current purpose and the actual object under study. Do not expose a mandatory mode selector.

- **As-Is Mapping:** establish what the current management system contains and how it is designed, operated and experienced.
- **Practice Tracing:** investigate a specific business practice, process, event or capability; use Source–Point–Line–Surface–Outcome–Loop selectively when it fits.
- **Issue Verification:** clarify a specific disputed claim or emerging issue using neutral questions and fit-for-purpose evidence. Do not turn this into a formal diagnosis unless separately requested and adequately supported.

Strategies may be mixed by topic within one project or interview.

### 2.2 As-Is mapping logic

Start from the project scope and available materials. Build a lightweight, project-specific theme map. Depending on relevance, themes may include:

- system boundary, covered populations and applicability;
- modules, components and structure;
- formal policies, rules and calculation/decision criteria;
- roles, responsibilities and decision rights;
- actual operating practices and interfaces;
- data, records and management information;
- differences by department, role, business type or period;
- exceptions, stakeholder understanding and lived experience;
- historical changes, only where relevant to current-state understanding.

Do not force a universal checklist. Do not assume any particular compensation, performance, grading, approval or digital workflow exists.

For management-system surveys, distinguish:
1. **Formal design:** what policies, rules and documents prescribe;
2. **Actual operation:** what people actually do, based on firsthand accounts and records;
3. **Stakeholder understanding/experience:** how different roles interpret and experience the system.

These are complementary views, not a mandatory sequential lifecycle.

### 2.3 Coverage and evidence are separate

Topic coverage describes whether a relevant theme has been explored (e.g. not explored, partly understood, sufficiently mapped, out of scope/not applicable). It is not a confidence score.

For important claims, preserve the existing independent evidence controls:
- Evidence basis;
- Scope;
- Verification status;
- source independence/shared upstream;
- premise safety and risk-proportionate verification.

A topic may be broadly covered while important claims remain unverified. A document may establish formal design while actual operation remains unknown.

### 2.4 Practice tracing

Preserve the exact business meaning of Source–Point–Line–Surface–Outcome–Loop, but make it conditional:
- Source: business origin/purpose;
- Point: real practice/case;
- Line: actual work process and responsibility chain;
- Surface: repeatability and organizational replication conditions;
- Outcome: actual result/value;
- Loop: the organization's feedback, adjustment, re-run and effectiveness review.

Do not use it as a default As-Is checklist. Do not require all six layers for every case.

### 2.5 Daily batch / cross-day update

Preserve existing stateless reload and daily-batch operation. On each batch:
- identify genuine new or revised information;
- update the current theme map and its coverage gaps;
- update important claims and evidence boundaries independently;
- identify contradictions and shared upstream sources;
- remove answered/redundant questions;
- allocate remaining information needs to the most suitable next role, case or record;
- stop when there is no material new information.

No persistent project state, database, evidence graph, RAG, agent, or new daily user-maintenance step.

## 3. Implementation scope

### In scope

- `SKILL.md`: purpose routing, As-Is default for current-state requests, cross-cutting guardrails.
- `references/interview-plan.md`: scope and theme map before interviewee selection; role-specific information jobs.
- `references/interview-guide.md`: As-Is system mapping questions; practice tracing demoted to conditional method; issue verification and premise-safety retained.
- `references/interview-delta.md`: update topic coverage separately from claim evidence; refresh next interview based on both.
- `evals/as-is-mapping.md`: public targeted regression for As-Is mapping and cross-day update.
- `evals/README.md`: explain the new regression boundary and preserve sealed acceptance separation.
- `governance/CR-05-WORK-ORDER.md`: this frozen work order.

### Out of scope

- `references/interview-notes.md` unless implementation review finds a concrete incompatibility;
- changes to runtime manifest or package file count;
- new Skill, Agent, API, connector, database, RAG, or persistent project memory;
- automatic diagnosis, causal claims, redesign recommendations or maturity scoring;
- modification of old test records, v0.2.0 package, main branch, Registry or Drive artifact.

## 4. Regression cases

1. **Compensation/performance As-Is:** identify the project-scoped system themes; distinguish formal rules, actual operation, and stakeholder experience; allocate unique information tasks to HR, Finance, business management and/or employees only where relevant; do not invent modules or diagnose prematurely.
2. **Organization/job/grade As-Is:** demonstrate method transfer beyond a compensation-specific question bank.
3. **As-Is-only boundary:** user requests description of current state, not diagnosis or redesign; do not state root causes or prescribe reform.
4. **Practice-tracing regression:** old cross-professional resource-coordination scenario still supports real case reconstruction and selective six-layer reasoning.
5. **Daily-batch regression:** one-department daily input changes theme coverage, known/unknowns and next interview without demanding multiple departments or real-time input.
6. Existing premise-safety, stateless reload, N1/N2 duplicate/missing-history behavior remains regression baseline.

Public cases are implementation-visible regression only. They do not constitute independent capability acceptance.

## 5. Acceptance gates

- **Purpose fit:** As-Is tasks are not forced into practice tracing or diagnosis.
- **Coverage:** all in-scope core themes are identified without an exhaustive universal checklist.
- **Design/operation/experience separation:** formal provisions, actual practices and stakeholder perceptions are not conflated.
- **Role fit:** each proposed interviewee has a distinct, evidence-grounded information task.
- **Coverage/evidence separation:** a mapped topic is not automatically treated as verified.
- **Premise safety:** no invented roles, rules, approval steps, indicators, causal relationships or organizational facts.
- **Adaptive update:** new department information revises the theme map and next interview plan, not merely appends another case.
- **Regression and burden:** existing daily-batch/evidence behavior remains; no additional daily manual process or runtime dependency.

A failure on any critical gate means REWORK. Passing public regression alone does not authorize release.

## 6. Execution and release controls

- Work only on the named branch from the frozen base.
- Keep changes minimal and reviewable.
- Do not merge the PR.
- Do not modify Registry or Google Drive package.
- Skill Manager reviews implementation and test evidence independently.
- Candidate may be considered for controlled use only after gates pass; Active/Stable requires separate evidence and authorization.
