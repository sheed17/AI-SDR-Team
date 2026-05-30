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
7. Run relevant evals and write eval scores/status.
8. Route edge cases with `Edge Case Type`, `Risk Flags`, `Recovery Action`, and `Next Best Action`.
9. Write `Account POV` and `Workflow Audit Angle`.
10. Draft outreach for qualified A-tier or strong B-tier rows only.
11. Run outreach, deliverability, and booked-call evals.
12. Stop each drafted row at `PENDING_APPROVAL`.
13. Update campaign counters, token estimates, and eval counts.
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
- `Discovery Eval Score`, `Signal Eval Score`, and `Buying Committee Eval Score` are captured where relevant.
- Any messy condition is captured using `14_edge_cases.md`.

## Qualification Acceptance

Qualify only when:

- Score is 7 or higher.
- Confidence is `MEDIUM` or `HIGH`.
- Signal A or Signal B is real.
- Draft hook can cite evidence.
- `Account Tier` is `A` or `B`.
- `Qualification Eval Score` is 4 or higher for A-tier and at least 3 for B-tier.

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
- `Outreach Eval Score` of 4 or higher, or a clear reason for `NEEDS_EDIT`
- `Deliverability Eval Score` of 4 or higher before any operator-commanded send
- `Booking Likelihood Score` of 4 or higher for A-tier sends
- `Booking Hypothesis`
- Exact `Call CTA`

Then set:

- `State`: `PENDING_APPROVAL`
- `Approval Status`: `PENDING`
- `Sequence Step`: `Not started`
- `Eval Status`: `PASS`, unless the row needs human QA
- `Next Best Action`: review, send, enrich person, improve evidence, or hold

## Eval Routing

After each agent step, apply `13_agent_evals.md`:

- If `Signal Eval Score` is below 3, do not draft.
- If `Buying Committee Eval Score` is below 3 for an A-tier candidate, downgrade to B/C or route to `NEEDS_REVIEW`.
- If `Outreach Eval Score` is below 4, route to `NEEDS_EDIT` or `NEEDS_REVIEW`.
- If `Deliverability Eval Score` is below 4, do not send.
- If `Eval Status` is `FAIL`, route to `DISQUALIFIED` or C-tier.
- If `Eval Status` is `NEEDS_REVIEW`, park the row and explain why in `Eval Failure Reason`.
- If an edge case is detected, write `Edge Case Type`, `Risk Flags`, `Recovery Action`, and `Next Best Action`.

## Booked-Call Routing

Apply `15_call_booking_self_eval.md` before sending:

- If `Booking Likelihood Score` is 4-5, prioritize the row.
- If `Booking Likelihood Score` is 3, enrich trigger, person, proof, or CTA before sending.
- If `Booking Likelihood Score` is 1-2, hold or C-tier the row.
- If the account has no timing trigger, keep the row but lower booking likelihood unless the evidence is unusually strong.
- If the CTA is a demo request, rewrite it as a 5-minute workflow-audit ask.

## Token Logging

For every row, estimate token use:

- C-tier early stop: `15000`
- B-tier researched and drafted: `35000`
- A-tier ABM with buying-committee mapping: `60000`

When actual usage is available, write:

- `Last Run Tokens`
- `Tool Calls Used`
- `Eval Notes` with any expensive or unusual research path

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
- The row has `Eval Status` of `PASS`.
- The row has `Deliverability Eval Score` of 4 or higher.
- The row has `Booking Likelihood Score` of 4 or higher for A-tier.
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
- How many prospects passed eval, failed eval, or need review
- How many A-tier rows have booking likelihood 4+
- Top edge cases blocking sends
- Estimated campaign tokens and actual campaign tokens if available
- Link to the review/send queue
- Clear blockers
