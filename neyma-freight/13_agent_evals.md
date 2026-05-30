# Agent Evals

## Purpose

Use this eval layer to keep Neyma Freight from becoming a generic lead machine.

Each agent run must produce an operational output and an eval output. The eval output decides whether the prospect advances, parks in `NEEDS_REVIEW`, or is disqualified.

The evals are practical checks for account quality, evidence quality, person quality, outreach quality, deliverability, and learning.

## Eval Principles

- Evaluate the work before advancing state.
- Prefer false negatives over false positives.
- Do not reward volume.
- Do not infer pain from industry alone.
- Every score must be explainable from visible evidence.
- A low eval score should route to `NEEDS_REVIEW`, `DISQUALIFIED`, or `C` tier.
- LinkedIn person quality matters as much as email quality for A-tier accounts.
- Booking likelihood matters more than draft volume.

## Notion Eval Fields

Add these fields to `Neyma Freight Pipeline`:

| Field | Type | Notes |
| --- | --- | --- |
| Discovery Eval Score | Number | 1-5 account discovery quality |
| Signal Eval Score | Number | 1-5 evidence and pain-signal quality |
| Buying Committee Eval Score | Number | 1-5 person mapping quality |
| Qualification Eval Score | Number | 1-5 tiering and reasoning quality |
| Outreach Eval Score | Number | 1-5 draft quality |
| Deliverability Eval Score | Number | 1-5 send-safety quality |
| Overall Eval Score | Number | Lowest critical-path score or overall QA judgment |
| Eval Status | Select | PASS, FAIL, NEEDS_REVIEW |
| Eval Failure Reason | Text | Specific reason when not PASS |
| Eval Notes | Text | Short QA notes and improvement ideas |
| Estimated Tokens | Number | Expected token range midpoint for this row |
| Last Run Tokens | Number | Actual tokens if available |
| Tool Calls Used | Number | Count of browser/search/Notion/Gmail/tool calls if available |
| Booking Likelihood Score | Number | 1-5 likelihood of a useful reply or workflow-audit call |

Add these fields to `Neyma Freight Campaigns`:

| Field | Type | Notes |
| --- | --- | --- |
| Estimated Campaign Tokens | Number | Expected total token use |
| Actual Campaign Tokens | Number | Sum of logged run tokens when available |
| Eval Pass Count | Number | Number of prospects passing eval |
| Eval Needs Review Count | Number | Number of prospects parked for review |
| Eval Fail Count | Number | Number of prospects failing eval |
| Cost Notes | Text | Human-readable cost assumptions and anomalies |

## Score Scale

Use the same 1-5 score scale for all evals:

- `5`: Excellent; strong enough for A-tier or golden-set learning.
- `4`: Good; usable with minor caveats.
- `3`: Acceptable but not strong; usually B-tier or review.
- `2`: Weak; route to `NEEDS_REVIEW` or C-tier.
- `1`: Fail; disqualify or do not advance.

Use `Eval Status`:

- `PASS` when the row can advance.
- `NEEDS_REVIEW` when a human should inspect uncertainty.
- `FAIL` when the row should not advance.

## Discovery Eval

Evaluate whether the company is worth researching.

Pass criteria:

- Company is plausibly a freight forwarder, customs broker, or both.
- Region matches campaign.
- Headcount appears around 10-40 or uncertainty is stated.
- Website exists.
- Company LinkedIn URL or directory source is captured when findable.

Fail examples:

- Trucking-only company with no forwarding/brokerage signal.
- Large enterprise outside the v0 ICP.
- No operating website or credible source.
- Region mismatch.

Score fields:

- `Discovery Eval Score`
- `Eval Notes`

Automatic routing:

- Score 4-5: continue to research.
- Score 3: continue only if target inventory is thin; otherwise hold.
- Score 1-2: `DISQUALIFIED` or `NEEDS_REVIEW`.

## Signal Eval

Evaluate whether there is real public evidence of manual-document pain.

Pass criteria:

- Signal A or Signal B is real.
- Evidence URL is clickable.
- Evidence quote or job title supports the hook.
- Signal relates to documents, intake, entry prep, customs, manifests, invoices, bills of lading, or shipment paperwork.

Fail examples:

- Evidence URL is just the homepage.
- Quote does not support the pain claim.
- Job is unrelated to documentation or ops.
- Agent writes a pain claim from industry assumptions.

Score fields:

- `Signal Eval Score`
- `Signal A Evidence URL`
- `Signal A Evidence Quote`
- `Signal B Evidence URL`
- `Signal B Job Title`

Automatic routing:

- Score 4-5: eligible for A/B tiering.
- Score 3: B-tier or `NEEDS_REVIEW`.
- Score 1-2: do not draft.

## Buying Committee Eval

Evaluate the quality of the person mapping.

Pass criteria:

- Person is likely attached to the target company.
- Title matches founder, owner, president, COO, ops, brokerage, import/export, documentation, or customs leadership.
- Person LinkedIn URL is a direct `/in/...` URL.
- Confidence is set honestly.
- A-tier accounts have two mapped people when findable.

Fail examples:

- Company LinkedIn URL in a person field.
- LinkedIn search URL instead of a profile URL.
- Person works at a different company.
- Title is too junior for primary outreach unless the account is intentionally documentation-led.

Score fields:

- `Buying Committee Eval Score`
- `Person 1 Confidence`
- `Person 2 Confidence`
- `Decision Maker Confidence`
- `Buying Committee`

Automatic routing:

- Score 4-5: eligible for A-tier if other evals pass.
- Score 3: B-tier unless signal is exceptional.
- Score 1-2: `NEEDS_REVIEW` before drafting.

## Qualification Eval

Evaluate whether the tier, score, and reasoning are consistent.

Pass criteria:

- `Account Tier` matches evidence and contact quality.
- `Qualification Score` matches the written rationale.
- `Account POV` and `Workflow Audit Angle` are grounded in evidence.
- Disqualifier is explicit when relevant.

Fail examples:

- A-tier assigned with weak signal.
- B-tier assigned with no named person and no credible inbox.
- C-tier account has a draft.
- Qualification score is high but notes are vague.

Score fields:

- `Qualification Eval Score`
- `Qualification Score`
- `Account Tier`
- `Confidence`
- `Disqualifier`

Automatic routing:

- Score 4-5: advance if signal/person/draft requirements pass.
- Score 3: B-tier or `NEEDS_REVIEW`.
- Score 1-2: `DISQUALIFIED`, C-tier, or `NEEDS_REVIEW`.

## Outreach Eval

Evaluate whether the email and LinkedIn draft are specific enough to send or hand to the operator.

Pass criteria:

- First sentence references a real observed signal.
- Draft is under roughly 120 words.
- CTA asks for a 5-minute workflow audit.
- Persona angle fits the recipient.
- No unsupported ROI, staffing, or volume claims.
- LinkedIn draft is short and safe for manual use.

Fail examples:

- Generic message that could go to any freight company.
- No evidence-backed hook.
- Pushy or aggressive language.
- Full-demo ask too early.
- Unsupported claim about cost savings or document volume.

Score fields:

- `Outreach Eval Score`
- `Email Subject`
- `Email Draft`
- `LinkedIn Draft`
- `Recommended Angle`

Automatic routing:

- Score 4-5: `PENDING_APPROVAL`.
- Score 3: `NEEDS_EDIT` or `NEEDS_REVIEW`.
- Score 1-2: do not send; rewrite or disqualify.

## Deliverability Eval

Evaluate whether a send is safe for the inbox and domain.

Pass criteria:

- Email is public, verified, or intentionally general inbox.
- Account is A-tier or strong B-tier.
- No attachments.
- No spammy formatting.
- No manipulative language.
- Volume remains low.
- Prospect was not already sent.

Fail examples:

- Guessed email.
- C-tier account.
- Missing evidence URL.
- Bulk-like personalization.
- Already sent or marked rejected/hold/disqualified.

Score fields:

- `Deliverability Eval Score`
- `Email`
- `Sequence Step`
- `Outcome`

Automatic routing:

- Score 4-5: eligible for explicit operator-commanded send.
- Score 3: create draft only or review.
- Score 1-2: do not send.

## Overall Eval

`Overall Eval Score` should be the lowest critical-path score, not a vanity average, when a low score creates risk.

Recommended rule:

- If `Signal Eval Score` is below 3, overall cannot exceed 2.
- If `Deliverability Eval Score` is below 3, overall cannot exceed 2 for sending.
- If `Outreach Eval Score` is below 3, overall cannot exceed 3.
- If `Booking Likelihood Score` is below 3 for a planned send, overall cannot exceed 3.
- If A-tier has `Buying Committee Eval Score` below 4, downgrade to B or `NEEDS_REVIEW`.

Use `Eval Status`:

- `PASS`: all relevant critical checks pass.
- `NEEDS_REVIEW`: there is ambiguity or missing contact/evidence quality.
- `FAIL`: do not advance.

## Token Usage Logging

Track expected and actual usage so the operator can understand cost per quality account.

Typical token ranges per prospect:

| Step | Typical Tokens | Notes |
| --- | ---: | --- |
| Discovery | 2,000-6,000 | Search and source review |
| Signal research | 6,000-18,000 | Website, forms, jobs, quotes |
| Buying committee mapping | 5,000-15,000 | LinkedIn/Sales Navigator profile work |
| Qualification | 2,000-5,000 | Scoring and tiering |
| Account POV and angle | 1,000-3,000 | Account thesis and audit angle |
| Outreach drafting | 2,000-5,000 | Email, LinkedIn, follow-up seed |
| Eval pass | 2,000-6,000 | QA checks and routing |
| Notion update/logging | 500-2,000 | Structured writes |

Campaign estimates:

| Campaign Size | Conservative | Heavy Research |
| --- | ---: | ---: |
| 1 account | 20,000-60,000 | 70,000+ |
| 10 accounts | 200,000-600,000 | 800,000+ |
| 20 accounts | 400,000-1,200,000 | 1,500,000+ |

Set `Estimated Tokens` to a rough midpoint:

- C-tier early stop: `15000`
- B-tier researched and drafted: `35000`
- A-tier ABM with committee mapping: `60000`

Set `Last Run Tokens` only when actual usage is available from the model/tool logs. If not available, leave blank and use `Estimated Tokens`.

## Eval Output Contract

Every agent result should include:

```json
{
  "eval_status": "PASS | FAIL | NEEDS_REVIEW",
  "eval_scores": {
    "discovery": 1,
    "signal": 1,
    "buying_committee": 1,
    "qualification": 1,
    "outreach": 1,
    "deliverability": 1,
    "overall": 1
  },
  "eval_failure_reason": "",
  "eval_notes": "",
  "estimated_tokens": 0,
  "last_run_tokens": null,
  "tool_calls_used": null
}
```

Agents only fill scores relevant to their step. The orchestrator preserves earlier scores and updates `Overall Eval Score`.

## Booking Eval Link

Use `15_call_booking_self_eval.md` as the final pre-send eval.

Passing outreach quality is not enough. A send-ready account should also have:

- a clear reason the person may care now
- a concrete workflow-audit CTA
- a strong enough booking hypothesis to justify consuming inbox reputation

## Weekly Eval Review

Once per week, review:

- A-tier accounts with `Overall Eval Score` below 4.
- Sent accounts with no replies.
- Bounces and wrong-person replies.
- Drafts with low specificity.
- Accounts where Sales Navigator found better decision-makers after the first draft.
- Winning signals and hooks to promote into the golden set.

Update `Learning Notes` with:

- best signals
- best titles
- best regions
- best workflow audit angles
- objections by persona
- copy patterns to reuse
- copy patterns to ban
