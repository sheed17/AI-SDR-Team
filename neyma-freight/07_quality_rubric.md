# Quality Rubric

## Purpose

Use this rubric before moving a prospect to `PENDING_APPROVAL`.

The bar is evidence-backed relevance, not volume.

For the daily three-gate eval and optional token logging, use `13_agent_evals.md`.

## Pass Criteria

A prospect is ready for approval only if all are true:

- Company matches small freight brokerage ICP.
- Headcount appears roughly 5-20 staff, or 10-40 for a still-lean brokerage, with uncertainty explicitly noted.
- A real Signal A or Signal B is recorded.
- Every pain claim has an evidence URL.
- Evidence quote or job title is captured.
- `Account Tier` is `A` or a strong `B`.
- `Account POV` and `Workflow Audit Angle` are complete.
- Decision-maker discovery was attempted with LinkedIn/search.
- Decision-maker confidence is captured in notes when not obvious.
- A-tier accounts have a buying-committee map with two people when findable.
- `Signal Gate`, `Person Gate`, and `Message Gate` are `PASS`.
- `Booking Priority` is `HIGH` for A-tier sends.
- Outreach hook references the actual signal.
- Email is concise and calm.
- No send action has been taken.

## Fail Criteria

Fail the prospect when any are true:

- No real signal exists.
- The hook is based only on industry assumptions.
- Evidence URL does not support the claim.
- Job posting is unrelated to brokerage operations, billing, settlements, carrier payables, AP, load entry, PODs, or compliance.
- Company is clearly outside ICP.
- Draft claims the company has a problem without evidence.
- Draft sounds generic enough to send to any freight company.
- A-tier account has no account POV.
- A-tier account has only one person and no notes explaining why another person could not be found.
- LinkedIn person fields contain company pages or generic search URLs.
- Any gate is `FAIL`.

## Draft Review Checklist

Before setting `State` to `PENDING_APPROVAL`, check:

- Does the first sentence mention the observed signal?
- Can the operator click the evidence URL and verify the hook?
- Is the offer one small automation workflow, not a platform pitch?
- Is the CTA a low-pressure 5-minute reconciliation audit?
- Is the email under roughly 120 words?
- Is LinkedIn under roughly 300 characters when possible?
- Is the LinkedIn draft addressed to the best named decision-maker when one is findable?
- If the draft says `Hi team`, does the row explain that no strong named decision-maker was found?
- Does `Workflow Audit Angle` name a specific process, such as carrier invoice vs. rate-con matching, POD intake, lumper/accessorial review, duplicate invoice detection, or carrier-payables exception handling?
- Does `Primary Persona` match the message angle?
- Is `Message Gate` `PASS`?
- Is `Booking Priority` `HIGH` for A-tier, or intentionally `MEDIUM` for a lighter B-tier?
- Are there no unsupported claims about savings, staffing, volume, variance rate, or invoice leakage?

## Account Tier Decision

Use:

- `A` when the account has strong fit, strong evidence, at least one credible email, an account POV, and buying-committee mapping.
- `B` when the account has good fit and real evidence but only one person, a general inbox, or lighter personalization.
- `C` when evidence, contact data, or ICP fit is weak.

Do not send C-tier accounts.

Gate guardrails:

- A-tier should have all three gates at `PASS` and `Booking Priority = HIGH`.
- B-tier should have no gate at `FAIL`.
- C-tier can have useful learning notes, but should not receive outreach.

## State Decision

Use:

- `PENDING_APPROVAL` only when a human can approve or reject the exact draft.
- `NEEDS_REVIEW` when evidence or fit is ambiguous.
- `DISQUALIFIED` when evidence is absent or company is outside ICP.

Gate routing:

- All gates `PASS`: continue to the next state.
- Any gate `REVIEW`: park, enrich, or downgrade with `Gate Notes`.
- Any gate `FAIL`: disqualify, hold, or downgrade to C-tier.

## Golden Set Notes

For the first 20 prospects, capture learnings in `Notes`:

- Which search query found the prospect
- Which signal was strongest
- Which hook felt most natural
- Why the prospect was qualified or disqualified
- Any repeatable pattern for future discovery
- Persona that received the message
- Reply type and objection/referral language
- Whether the 5-minute reconciliation audit CTA worked

The golden set should teach the system what a good prospect looks like.
