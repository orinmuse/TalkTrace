# Company guide candidate change acceptance

后续决定：Owner 于2026年10月21日明确要求定为 v0.1.1、封装并邮件交付。当前发布决定以 `releases/v0.1.1.md` 为准；下文保留当时的候选验收与 hold 历史，不再作为现行禁止分发的决定。WorkBuddy NOT TESTED 事实继续保留。

Date: 2026-10-21
Work Order: TT-COMPANY-GUIDE-20261021, PR #9.
Decision owner: Skill Manager; engineering implementation and checks returned through technical-execution.

## Scope and provenance

The user supplied six historical interview guides and requested Skill acceptance and company-template extraction, then authorized continuation. Only reusable structure and question-selection methods entered this public candidate. Source documents, original client identities and client-specific claims were not committed or required at runtime.

Baseline: `5ab55f27256eb4d37eaa93936bac0cd172332231`.
First candidate: `71ee8a5a24c594f22a1b5846733b548d1dc20d4a`.
The revision accompanying this record changes only the company profile's application examples, optional-list information boundaries and evidence/verification documentation. The 11-file runtime manifest is unchanged from the first candidate.

Cloud execution used separate fresh agent sessions with the same synthetic task file and only their respective runtime files. Neither runner received expected answers or the author's findings. A third fresh session saw only the task and anonymous A/B outputs; it did not receive source-format rules or version mapping. A = baseline, B = first candidate. This is a single paired forward trial, not a statistically stable benchmark or WorkBuddy test. Reviewer blindness covered version identity, not the existence of visible document differences.

Runtime digest method: SHA-256 of sorted UTF-8 relative path + NUL + file bytes + NUL, over runtime files only.

- Baseline: `12b2ad19ae9189dfee125b5705048861322deceb29819f237d2af9a49e80ceb1`
- First candidate: `7b828235e54f4d9d30cd79fc9817e1445c5e8659de2ee3dc5c0a32d864570636`
- Revised candidate: `33c544c1964f4be5b731b96dbd405f82a84c7c7cbbdc71eab5d640e0ef4a267e`

Raw evidence is retained beside this record: input, baseline-output, candidate-output, independent-review, followup-input, followup-output, followup-review. All task entities are synthetic.

## First review and disposition

The independent reviewer preferred baseline A and requested revision of B. Do not cite this trial as evidence that the candidate is globally better.

Accepted findings: candidate B lightly presupposed performance/incentive arrangements before checking existence; a hypothetical research question reverted to “本次研究”; a question-only incentive draft omitted an explicit notice that information-use/confidentiality arrangements remained unresolved. These are nearest-layer profile application failures, not reasons to change global routing or add a state engine.

The reviewer also treated the invitation's confidentiality placeholder as unfinished. It is indeed not send-ready, but fail-closed draft status is intentional when required arrangements are unknown. Its absence is not permission to invent a confidentiality commitment or a future project-team promise. Keep this limitation explicit. The blind reviewer lacked company-format references and therefore could not certify exact company format; assess that aspect against the profile and supplied-source analysis, not against the blind review alone.

Repair: add concise examples placing existence checks first; preserve hypothetical status across the entire question; carry necessary unresolved information-use/confidentiality notice into question-only drafts without inventing arrangements or commitments.

## Targeted followup

A new clean runner received only the two affected synthetic tasks and revised runtime. The reviewer then inspected that raw output in a targeted followup, not a renewed blinded pair. No material mandatory rework was found. The HR guide now checks existence of positions, performance evaluation and pay rules before followup. The incentive guide preserves the unapproved/discussion status, self-determination, unresolved information arrangements and absence of financial-data collection.

The revised lists have 7 questions/30 minutes and 5 questions/20 minutes. The reviewer found them feasible for overview interviews but noted limited probing time and optional consolidation. This is a controlled-use limitation, not proof of actual field duration. Do not re-run unrelated cases merely to obtain a favorable global score; no performance superiority claim is authorized.

## Engineering evidence

- Skill frontmatter quick validation: PASS.
- Both existing workflow Python checks executed locally: PASS.
- Clean runtime package assembly: PASS, exactly 11 manifest files, no maintainer files.
- Removing either new runtime dependency is detected by dependency-closure check: PASS.
- Diff whitespace checks: PASS.
- First candidate GitHub validate runs `39534625707` and `39534576195`: success.
- First candidate context-reload runs `39534625708` and `39534576152`: success.
- Existing context-reload/premise-safety mechanisms remain present; structural CI does not prove behavioral execution of all historical cases.
- WorkBuddy candidate installation/loading and real colleague field use: NOT TESTED. Follow S8 with the exact candidate commit.

## Capability acceptance and release disposition

ACCEPT WITH CONDITIONS for the scoped company-profile candidate and controlled trial use. Initial material output findings were repaired and targeted independently reviewed. Package integration is checked. This does not certify the entire Skill anew, establish general superiority, or replace target-runtime acceptance.

Prospective version line: minor / v0.2.0 candidate; no formal version assigned by this record. Keep PR in draft/release hold pending WorkBuddy installation/loading evidence and consultant review of a real guide. Released `v0.1.0` and its immutable tag remain unchanged. No merge, release, promotion, production sending or app deployment is performed by this work order.

Stop internal feature expansion here. The next evidence should be exact-candidate installation/load and one real project guide reviewed for usefulness and duration. Engineering implementation/checks are complete for the cloud scope; the target-runtime gate remains open.
