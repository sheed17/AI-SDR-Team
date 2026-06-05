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
- Confirm LinkedIn and Sales Navigator local browser access for the best SDR workflow.
- Confirm Gmail access if the run is expected to send eligible emails.

## Campaign Intake

When the operator says a casual command such as `run pipeline for 3 in NorCal`, normalize it into a campaign row in `Neyma Freight Campaigns`.

Infer missing values instead of asking:

- Campaign Name: generated from count, region, and date.
- Goal: the original operator prompt plus normalized intent.
- Region: location phrase from the prompt; default `United States`.
- Target Count: number from the prompt; default `10`.
- ICP Segment: small freight brokerages.
- Source Mix: public search, FMCSA/SAFER or authority lookup when available, DAT/Truckstop directories when available, LinkedIn/Sales Navigator, websites, jobs.
- Stop State: `SENT` for eligible Gmail emails; blocked rows park themselves.
- Campaign State: `REQUESTED`.

Ask a question only when the command is impossible to interpret, such as no accessible tools, contradictory region/count, or no sending inbox when the operator clearly expects email sending.

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
12. Send eligible Gmail emails after validation.
13. Update campaign counters, token estimates, and gate counts.
14. Park blocked rows in `NEEDS_REVIEW`, `DISQUALIFIED`, or `ERROR`.
15. Summarize result.

## Sourcing Acceptance

Only add a candidate when at least one is plausible:

- Small freight brokerage
- 5-20 staff, or 10-40 staff for a still-lean operator-led firm
- Carrier invoice, POD, billing, TMS, or reconciliation signal may exist
- Hiring signal may exist
- Decision-maker is findable

Before promoting a sourced candidate to research, make a real account-first pass:

- Sales Navigator was used first for account discovery and buyer mapping when available.
- Universe source is captured: Sales Navigator, LinkedIn, search, FMCSA/SAFER, DAT, Truckstop, jobs, company website, or operator-provided.
- Fit was checked against the ICP, including carrier-only, warehouse-only, software/vendor, and enterprise 3PL exclusions.
- Authority or directory verification was attempted when the company has an MC/DOT or obvious directory presence.
- Signal search was attempted for invoice, POD, billing, settlements, AP, TMS, carrier-payables, lumper, accessorial, and brokerage-ops terms.
- Person mapping is not required until the account has plausible fit and signal.
- `Sales Nav Account URL`, `Sales Nav Lead URLs`, `Sales Nav Search Notes`, `Source Stack Used`, `Authority/Directory Notes`, and `Signal Search Notes` are populated when available.

## Research Acceptance

Research is complete only when:

- Company type is confirmed or uncertainty is noted.
- Region is captured.
- Headcount estimate is captured.
- Sales Navigator account/lead context is captured when available.
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
- Low-pressure 5-minute reconciliation audit CTA
- `Account POV`
- `Workflow Audit Angle`
- Persona-aware copy for founder, ops, accounting/AP, carrier payables, billing, or settlements
- `Message Gate` is `PASS`, or there is a clear reason for `NEEDS_EDIT`
- `Booking Priority` is `HIGH` for A-tier sends
- `Booking Hypothesis`
- Exact `Call CTA`

Then set:

- `State`: `SENDING` then `SENT` when Gmail send validation passes under `run pipeline`
- `State`: `NEEDS_REVIEW` when useful but blocked
- `Approval Status`: optional; do not require it for `run pipeline`
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
- If `Booking