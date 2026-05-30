# Qualification Playbook

## Goal

Score researched prospects consistently and decide whether to draft outreach.

## Required Inputs

A prospect can be qualified only when these fields are populated:

- Company
- Website
- Region
- Headcount Estimate
- Research Summary
- At least one of Signal A or Signal B with evidence URL
- Decision Maker or clear note explaining why one is unavailable
- Account Tier
- Account POV and Workflow Audit Angle for A-tier or send-ready B-tier rows

## Scoring

Use a 0-10 `Qualification Score`.

Score 9-10:

- Strong ICP fit
- Clear Signal A or Signal B
- Decision-maker identified
- Buying committee mapped when possible
- Evidence directly supports manual document work
- Outreach hook is obvious and specific
- Account can be A-tier

Score 7-8:

- Good ICP fit
- At least one real signal
- Some uncertainty on size, decision-maker, or workflow
- Drafting is allowed if confidence is medium or high
- Account is usually B-tier unless buying committee and email quality are strong

Score 5-6:

- Plausible fit
- Evidence exists but is weak, indirect, old, or ambiguous
- Set to `NEEDS_REVIEW` unless operator asks to proceed
- Account is C-tier until enriched

Score 0-4:

- Poor fit or no usable signal
- Disqualify

## Confidence

Use one of:

- `HIGH`: evidence and company fit are clear
- `MEDIUM`: evidence is real but one important detail is uncertain
- `LOW`: evidence is thin or fit is unclear

## Account Tier

Use:

- `A`: strong ICP fit, strong evidence, at least one credible email, account POV, workflow audit angle, and two mapped people when findable.
- `B`: good ICP fit and real evidence but only one mapped person, general inbox, or lighter personalization.
- `C`: weak signal, unclear ICP, missing decision-maker, missing email, or enrichment needed.

Do not send C-tier accounts.

## Disqualifiers

Use `Disqualifier` when relevant:

- Outside ICP
- Too large
- Too small
- Carrier or warehouse-only
- Software/vendor
- No public manual-document signal
- No decision-maker found
- Inactive or low-quality web presence

## State Transitions

Before advancing state, apply the Qualification Eval in `13_agent_evals.md` and write:

- `Qualification Eval Score`
- `Overall Eval Score`
- `Eval Status`
- `Eval Failure Reason` when not passing
- `Eval Notes`

After research:

- `RESEARCHED` when research is complete but qualification not decided.
- `QUALIFIED` when score is 7+ and evidence supports a hook.
- `DISQUALIFIED` when score is 0-4 or a hard disqualifier applies.
- `NEEDS_REVIEW` when score is 5-6 or evidence is ambiguous.

After drafting:

- `DRAFTED` when outreach exists but has not been prepared for approval.
- `PENDING_APPROVAL` when Email Draft or LinkedIn Draft is ready for human review.

## Qualification Note Template

Use this in `Notes` when useful:

`Qualified because [Signal A/B] shows [manual workflow], company appears to be [ICP fit], and [decision-maker] is likely responsible for operations. Uncertainty: [missing/unclear item].`

## Hard Rule

If no real signal exists, do not draft. Set the prospect to `DISQUALIFIED` or `NEEDS_REVIEW`.
