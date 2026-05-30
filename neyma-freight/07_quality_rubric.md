# Quality Rubric

## Purpose

Use this rubric before moving a prospect to `PENDING_APPROVAL`.

The bar is evidence-backed relevance, not volume.

For score definitions, per-agent evals, and token logging, use `13_agent_evals.md`.

## Pass Criteria

A prospect is ready for approval only if all are true:

- Company matches freight forwarder or customs broker ICP.
- Headcount appears roughly 10-40 staff or uncertainty is explicitly noted.
- A real Signal A or Signal B is recorded.
- Every pain claim has an evidence URL.
- Evidence quote or job title is captured.
- `Account Tier` is `A` or a strong `B`.
- `Account POV` and `Workflow Audit Angle` are complete.
- Decision-maker discovery was attempted with LinkedIn/search.
- Decision-maker confidence is captured in notes when not obvious.
- A-tier accounts have a buying-committee map with two people when findable.
- Relevant eval scores are captured and `Eval Status` is `PASS`.
- `Overall Eval Score` is 4 or higher for A-tier and at least 3 for strong B-tier.
- Outreach hook references the actual signal.
- Email is concise and calm.
- No send action has been taken.

## Fail Criteria

Fail the prospect when any are true:

- No real signal exists.
- The hook is based only on industry assumptions.
- Evidence URL does not support the claim.
- Job posting is unrelated to documentation or operations.
- Company is clearly outside ICP.
- Draft claims the company has a problem without evidence.
- Draft sounds generic enough to send to any forwarder.
- A-tier account has no account POV.
- A-tier account has only one person and no notes explaining why another person could not be found.
- LinkedIn person fields contain company pages or generic search URLs.
- `Eval Status` is `FAIL`.
- A critical-path eval score is below 3.

## Draft Review Checklist

Before setting `State` to `PENDING_APPROVAL`, check:

- Does the first sentence mention the observed signal?
- Can the operator click the evidence URL and verify the hook?
- Is the offer one small automation workflow, not a platform pitch?
- Is the CTA a low-pressure 5-minute workflow audit?
- Is the email under roughly 120 words?
- Is LinkedIn under roughly 300 characters when possible?
- Is the LinkedIn draft addressed to the best named decision-maker when one is findable?
- If the draft says `Hi team`, does the row explain that no strong named decision-maker was found?
- Does `Workflow Audit Angle` name a specific process, such as POA, ISF, invoice, packing list, email/fax intake, or entry prep?
- Does `Primary Persona` match the message angle?
- Is `Outreach Eval Score` 4 or higher?
- Is `Deliverability Eval Score` 4 or higher if the message may be sent?
- Are there no unsupported claims about savings, staffing, or volume?

## Account Tier Decision

Use:

- `A` when the account has strong fit, strong evidence, at least one credible email, an account POV, and buying-committee mapping.
- `B` when the account has good fit and real evidence but only one person, a general inbox, or lighter personalization.
- `C` when evidence, contact data, or ICP fit is weak.

Do not send C-tier accounts.

Eval guardrails:

- A-tier should have `Overall Eval Score` of 4 or higher.
- B-tier should have `Overall Eval Score` of at least 3 and no critical-path failure.
- C-tier can have useful learning notes, but should not receive outreach.

## State Decision

Use:

- `PENDING_APPROVAL` only when a human can approve or reject the exact draft.
- `NEEDS_REVIEW` when evidence or fit is ambiguous.
- `DISQUALIFIED` when evidence is absent or company is outside ICP.

Eval routing:

- `PASS`: continue to the next state.
- `NEEDS_REVIEW`: park the row with `Eval Failure Reason`.
- `FAIL`: disqualify or downgrade to C-tier.

## Golden Set Notes

For the first 20 prospects, capture learnings in `Notes`:

- Which search query found the prospect
- Which signal was strongest
- Which hook felt most natural
- Why the prospect was qualified or disqualified
- Any repeatable pattern for future discovery
- Persona that received the message
- Reply type and objection/referral language
- Whether the 5-minute workflow audit CTA worked

The golden set should teach the system what a good prospect looks like.
