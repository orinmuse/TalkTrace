# As-Is Mapping Regression Cases

**PUBLIC_TARGETED_REGRESSION_ONLY.** These synthetic cases are implementation-visible engineering regressions. They do not constitute independent Capability Acceptance, real-client effectiveness evidence, or permission to promote/release the candidate.

## Purpose

Verify that TalkTrace selects its investigation method from the user's objective and object under study.

For management-system current-state surveys, it should build a project-scoped theme map and allocate role-specific information tasks before deep-diving into selected practices. It must not default to Source–Point–Line–Surface–Outcome–Loop for every interview.

The regression also checks that:
- formal design, actual operation and stakeholder understanding/experience remain distinct;
- topic coverage is not confused with claim verification;
- no universal industry checklist is imposed;
- daily-batch updates change both the current understanding and the next information task;
- existing premise-safety and source-boundary rules remain active.

---

## A1｜D0 compensation and performance management As-Is survey

### User request

> We are starting a consulting project to understand the company's current compensation and performance management systems. The immediate task is to understand the current state, not to diagnose problems or design a new system yet. Please review the materials and prepare the first round of interviews.

### Available project information

- The project scope currently says “company compensation and performance management systems”. It does not yet specify whether all employee groups, subsidiaries or special employment categories are included.
- A compensation policy states that roles are assigned to job grades and that compensation is determined with reference to grade ranges. It mentions “performance-related income” but does not define all pay components, eligibility, calculations or actual allocation.
- A performance management guide states that departments and employees receive annual assessments. It does not explain the full indicator, calibration, feedback, appeal or application process.
- Initial interviewees: HR manager, Finance manager, two business-unit heads and one employee representative. No further role descriptions are available.

### Expected behavior

1. Recognize this as an **As-Is management-system survey**, not a single business-process tracing task or a root-cause diagnosis.
2. Clarify or flag the material scope boundary (covered entities / employee groups) without blocking a useful first draft.
3. Build a light, project-specific theme map. Depending on the stated scope, it may include:
   - applicable employee groups and boundaries;
   - compensation structure and relationship with job grades;
   - rules for determining and adjusting compensation;
   - payroll budget / total compensation governance;
   - performance objects, cycles, targets, indicators and evaluation;
   - review/calibration, feedback and appeal if they exist;
   - how performance results are applied;
   - the interface between compensation and performance;
   - actual operation and differences across business units;
   - management/employee understanding and experience.
4. Distinguish **formal design**, **actual operation**, and **stakeholder understanding/experience**. Do not infer that the documents prove the operating practice.
5. Allocate distinct information tasks:
   - HR: system structure, policy, process and administration;
   - Finance: budget, payroll, accounting data and what Finance actually sees;
   - business-unit heads: local implementation and variations;
   - employee representative: how rules are understood and experienced.
   This allocation is provisional and must not invent duties not supported by the project information.
6. Do not assume that annual bonuses, project bonuses, forced distributions, promotion links, fixed salary components, approval layers or digital workflows exist. Ask what components and procedures actually exist.
7. Do not use the six-layer method as the main outline. Do not declare the system effective/ineffective or recommend reform.

### Failure signals

- The guide starts with a single bonus allocation case and never maps the system.
- The assistant presumes particular pay components or standard HR processes.
- It treats policy text as proof of actual operation.
- It diagnoses root causes or designs a future system despite the As-Is-only request.
- It asks every interviewee the same generic questions.

---

## A2｜D1 HR batch → D2 Finance batch: update the system map

### D1 input — HR manager interview note

- HR says the company has an annual performance assessment for departments and employees.
- HR says annual assessment results are used when determining annual performance-related income.
- HR publishes the policy and collects department assessment results.
- HR has not provided individual calculation sheets or evidence that every unit applies the rules identically.
- HR says some project teams may have additional project-related distribution practices, but the interviewee does not know the details.
- The interviewee describes the system as “basically consistent across departments”, but gives no cross-department sample.

### Expected D1 behavior

- Record the HR statements with their source and scope; do not upgrade “basically consistent” to a company-wide fact.
- Update relevant themes: formal policy and HR process become partly understood; actual calculation, unit-level application, project-related practices and employee understanding remain incomplete.
- Do not ask HR to answer detailed Finance calculations or business-unit execution outside the interviewee's knowledge.
- Recommend a Finance interview and one business-unit interview with distinct information tasks.

### D2 input — Finance manager interview note

- Finance receives the annual payroll budget and department-level performance results.
- Finance processes payroll using information provided by HR, but does not see the underlying individual performance scores for every department.
- Finance has seen two business units submit different supporting schedules for performance-related payments.
- In one unit, some project-related payments appear as project cost items; Finance cannot confirm whether this is a standard compensation component or a local practice.
- Finance does not know how employees understand the assessment or how managers determine individual distributions.

### Expected D2 behavior

1. Update the map rather than merely append a second interview summary.
2. Distinguish HR's system-level description from Finance's narrower data/processing visibility.
3. Treat the two different schedules as evidence of variation in the observed submissions, not proof of inconsistent company-wide policy or non-compliance.
4. Mark formal design, payroll/budget data, actual individual calculation, local practice and employee experience at different coverage states.
5. Separate **topic coverage** from **claim verification**: the compensation/performance interface has been discussed, but its detailed rules and unit-level operation remain only partly understood.
6. Refresh the next interview:
   - business-unit head: explain actual local use of assessment results and distribution, with one recent example and supporting schedule if available;
   - HR process owner: clarify the formal meaning and applicability of performance-related income and project-related payments;
   - employee representative only for understanding/experience, not for formal policy interpretation.
7. Do not infer that Finance's lack of access means a process does not exist.
8. Do not diagnose “departmental inconsistency”, “unfairness” or “weak governance” without further evidence.

---

## A3｜Transfer test: organization / job / grade architecture

### User request

> We need to understand the current organization, job and grade architecture before deciding whether to make changes. Please prepare a preliminary interview plan.

### Available information

- One organization chart lists departments and reporting lines.
- A job catalogue contains professional, management and project-related role titles, but the relationship among these categories is not explained.
- A grade document lists several grade bands, but does not state whether all role categories use the same grade structure.
- Interviewees may include HR, two department heads and employees from different role categories.

### Expected behavior

1. Apply the same purpose-driven As-Is method without reusing a compensation-specific question bank.
2. Map the relevant themes from the available material: organization structure and scope; job/role categories; grade architecture; role-to-grade relationship; role responsibilities; management/professional/project tracks if applicable; appointment or movement rules if they exist; actual use and differences; stakeholder understanding.
3. Identify unresolved boundaries, especially whether all role categories share one grade system.
4. Allocate role-specific information tasks based on actual information access.
5. Do not assume dual career ladders, competency models, promotion committees, standard job descriptions or fixed grade-to-pay mapping unless supported.

---

## A4｜Boundary test: current-state description only

### User request

> For now, I only want a neutral description of how the current system works. Do not diagnose problems or recommend a new system.

### Expected behavior

- Describe what is known, what is only reported by a source, what differs by scope, and what remains unknown.
- Do not turn gaps in available information into confirmed management problems.
- Do not offer root-cause explanations, maturity ratings or redesign proposals.
- It may identify missing information and propose neutral follow-up questions or records needed to complete the As-Is picture.

---

## A5｜Practice-tracing regression

Use the existing cross-professional resource coordination case in `evals/daily-batch.md` or `evals/adaptive-probing.md`.

### Expected behavior

- When the object is a concrete operating practice, TalkTrace still reconstructs the actual case, confirmed steps, role handoffs and evidence boundary.
- Source–Point–Line–Surface–Outcome–Loop remains available when relevant, but is not forced as a universal checklist.
- It still distinguishes approval, arrangement, actual arrival/participation and outcome where the case requires it.

---

## Regression review checklist

- Did the assistant correctly infer the user's objective and investigation object?
- Did it build a scope-specific theme map before assigning interviewees?
- Did it distinguish formal design, actual operation and stakeholder experience?
- Did it adapt the theme map when a new department supplied information?
- Did it separate topic coverage from claim-level evidence verification?
- Did it avoid assuming common industry practices, processes or pay components?
- Did each interviewee have a distinct and evidence-grounded information task?
- Did it avoid premature diagnosis and redesign?
- Did it retain premise safety, source independence, stateless reload and daily-batch behavior?
- Did it remain light enough for a consultant's existing once-daily upload workflow?

A clean pass on this public file is necessary engineering regression evidence only. Independent, held-out candidate acceptance remains a separate gate.
