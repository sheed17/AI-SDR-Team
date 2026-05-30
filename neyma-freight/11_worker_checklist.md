# Worker Checklist

## Before Running

- Read `01_icp.md`.
- Read `02_discovery.md`.
- Read `03_research.md`.
- Read `04_qualification.md`.
- Read `05_outreach.md`.
- Read `07_quality_rubric.md`.
- Read `10_goal_to_result.md`.
- Read `12_enterprise_gtm.md`.
- Read `13_agent_evals.md`.
- Read `14_edge_cases.md`.
- Read `15_call_booking_self_eval.md`.
- Read `17_cofounder_setup.md` only when setting up another operator machine.
- Confirm Notion access.
- Confirm LinkedIn local Chrome access if LinkedIn is in the source mix.

## Campaign Intake

Create or use a row in `Neyma Freight Campaigns`.

Required:

- Campaign Name
- Goal
- Region
- Target Count
- ICP Segment
- Source Mix
- Stop State: `PENDING_APPROVAL`
- Campaign State: `REQUESTED`

## Processing Order

For each campaign:

1. Set campaign to `RUNNING`.
2. Source enough candidate companies.
3. Create one pipeline row per candidate.
4. Research each row.
5. Map the buying committee for A-tier candidates.
6. Qualify each row and assign `Account Tier`.
7. Apply the three gates: `Signal Gate`, `Person Gate`, and `Message Gate`.
8. Route edge cases with `Edge Case Type`, `Risk Flags`, `Recovery Action`, and `Next Best Action`.
9. Write `Account POV` and `Workflow Audit Angle`.
10. Draft outreach for qualified A-tier or strong B-tier rows only.
11. Run Message Gate and set `Booking Priority`.
12. Stop each drafted row at `PENDING_APPROVAL`.
13. Update campaign counters, token estimates, and gate counts.
14. If the operator command includes sending, validate and send eligible emails.
15. Summarize result.

## Sourcing Acceptance

Only add a candidate when at least one is plausible:

- Freight forwarder or customs broker
- 10-40 staff or likely small operator-led firm
- Manual intake signal may exist
- Hiring signal may exist
- Decision-maker is findable

## Research Acceptance

Research is complete only when:

- Company type is confirmed or uncertainty is noted.
- Region is captured.
- Headcount estimate is captured.
- Signal A or Signal B has been searched for.
- Decision-maker has been searched for.
- A-tier candidates have at least two buying-committee people searched for.
- Evidence URL and quote are captured if a signal exists.
- `Account POV` and `Workflow Audit Angle` are captured for A-tier and send-ready B-tier rows.
- `Signal Gate` and `Person Gate` are captured.
- Any messy condition is captured using `14_edge_cases.md`.

## Qualification Acceptance

Qualify only when:

- Score is 7 or higher.
- Confidence is `MEDIUM` or `HIGH`.
- Signal A or Signal B is real.
- Draft hook can cite evidence.
- `Account Tier` is `A` or `B`.
- `Signal Gate` and `Person Gate` are not `FAIL`.

Otherwise:

- Use `DISQUALIFIED` for no fit/no signal.
- Use `NEEDS_REVIEW` for ambiguity.
- Use `Account Tier = C` for rows worth holding but not sending.

## Draft Acceptance

Draft only when qualified.

Every draft must include:

- Specific signal
- Evidence-grounded hook
- Small automation offer
- Low-pressure 5-minute workflow audit CTA
- `Account POV`
- `Workflow Audit Angle`
- Persona-aware copy for founder, ops, brokerage, import/export, or documentation
- `Message Gate` is `PASS`, or there is a clear reason for `NEEDS_EDIT`
- `Booking Priority` is `HIGH` for A-tier sends
- `Booking Hypothesis`
- Exact `Call CTA`

Then set:

- `State`: `PENDING_APPROVAL`
- `Approval Status`: `PENDING`
- `Sequence Step`: `Not started`
- `Signal Gate`: `PASS`
- `Person Gate`: `PASS`
- `Message Gate`: `PASS`
- `Booking Priority`: `HIGH` or `MEDIUM`
- `Next Best Action`: review, send, enrich person, improve evidence, or hold

## Gate Routing

After each agent step, apply `13_agent_evals.md`:

- If `Signal Gate` is `FAIL`, do not draft.
- If `Signal Gate` is `REVIEW`, enrich or park in `NEEDS_REVIEW`.
- If `Person Gate` is `FAIL`, do not send.
- If `Person Gate` is `REVIEW`, enrich, downgrade from A-tier, or use a general inbox intentionally.
- If `Message Gate` is `FAIL`, do not send.
- If `Message Gate` is `REVIEW`, rewrite before handoff/send.
- If an edge case is detected, write `Edge Case Type`, `Risk Flags`, `Recovery Action`, and `Next Best Action`.

## Booked-Call Routing

Apply `15_call_booking_self_eval.md` before sending:

- If `Booking Priority` is `HIGH`, prioritize the row.
- If `Booking Priority` is `MEDIUM`, enrich trigger, person, proof, or CTA before sending.
- If `Booking Priority` is `LOW`, hold or C-tier the row.
- If the account has no timing trigger, keep the row but lower `Booking Priority` unless the evidence is unusually strong.
- If the CTA is a demo request, rewrite it as a 5-minute workflow-audit ask.

## Token Logging

For every row, estimate token use:

- C-tier early stop: `15000`
- B-tier researched and drafted: `35000`
- A-tier ABM with buying-committee mapping: `60000`

When actual usage is available, write:

- `Last Run Tokens`
- `Tool Calls Used`
- `Gate Notes` with any expensive or unusual research path

## Do Not Do

- Do not ask the operator to approve each transition.
- Do not send email unless the operator's command explicitly includes sending.
- Do not send LinkedIn messages.
- Do not connect, follow, react, comment, endorse, or scrape at high volume.
- Do not fabricate signals.

## Email Send Validation

Before sending a drafted campaign email, verify:

- The row has a credible email address.
- The row has an email subject and email draft.
- The row has a real Signal A or Signal B evidence URL.
- The row is `Account Tier` A or strong B.
- The row has `Workflow Audit Angle`.
- The row has `Signal Gate`, `Person Gate`, and `Message Gate` of `PASS`.
- The row has `Booking Priority` of `HIGH` for A-tier.
- The row has a concrete `Booking Hypothesis` and `Call CTA`.
- The row is not rejected, held, disqualified, needs review, errored, or already sent.

After a successful Gmail send, update:

- `State`: `SENT`
- `Outcome`: sent timestamp or Gmail message ID
- `Sequence Step`: `Email 1`
- `Last Touch Date`
- `Next Touch Date`, normally 3-5 business days later
- Campaign sent counter

## End Report

Report:

- What campaign ran
- How many prospects reached each terminal/parked state
- How many prospects passed all gates, failed a gate, or need review
- How many A-tier rows are `Booking Priority = HIGH`
- Top edge cases blocking sends
- Estimated campaign tokens and actual campaign tokens if available
- Link to the review/send queue
- Clear blockers
