# Goal-to-Result Worker

## Purpose

Run Neyma Freight from a single operator goal to a concrete result: a Notion queue of evidence-backed, account-first GTM rows with buying committee mapping and workflow-audit outreach.

This is the v0 worker contract. It is not a backend service. Codex acts as the worker loop until the process proves itself enough to justify deterministic glue.

## Operator Goal Shape

The operator should be able to say:

`Run Neyma Freight for 10 customs brokers in Southern California. Use LinkedIn, company websites, and search. Stop at PENDING_APPROVAL.`

The worker should not ask for handoff instructions between discovery, research, qualification, and drafting.

If a goal is missing region or count, use reasonable defaults:

- Count: 10 prospects
- Region: United States
- Source mix: LinkedIn, search, company websites
- Stop state: `PENDING_APPROVAL`

## Campaign Control Surface

Use the Notion database:

`Neyma Freight Campaigns`

Each campaign defines:

- Campaign Name
- Goal
- Region
- Target Count
- ICP Segment
- Source Mix
- Stop State
- Campaign State
- Prospects Sourced
- Prospects Researched
- Prospects Qualified
- Prospects Drafted
- Prospects Pending Approval
- Prospects Sent
- Notes

The prospect-level source of truth remains:

`Neyma Freight Pipeline`

## Campaign States

Use:

- `REQUESTED`
- `RUNNING`
- `PAUSED`
- `DONE`
- `ERROR`
- `NEEDS_REVIEW`

## Worker Loop

For each campaign in `REQUESTED` or `RUNNING`:

1. Set campaign to `RUNNING`.
2. Source prospects until the campaign has enough candidate rows.
3. For each prospect, advance through deterministic states:
   - `NEW`
   - `SOURCING`
   - `SOURCED`
   - `RESEARCHING`
   - `RESEARCHED`
   - `QUALIFYING`
   - `QUALIFIED` or `DISQUALIFIED`
   - `DRAFTING`
   - `DRAFTED`
   - `PENDING_APPROVAL`
4. Stop at `PENDING_APPROVAL`.
5. Update campaign counters.
6. Mark campaign `DONE` when the target number of prospects has reached `PENDING_APPROVAL`, `DISQUALIFIED`, or `NEEDS_REVIEW` and no actionable rows remain for the campaign.

For enterprise-style runs, a row is not truly ready unless it also has:

- `Account Tier`
- `Primary Persona`
- `Buying Committee` for A-tier accounts
- `Account POV`
- `Workflow Audit Angle`
- `Eval Status`
- `Overall Eval Score`
- `Estimated Tokens`
- `Edge Case Type` when messy
- `Booking Likelihood Score`
- `Booking Hypothesis`
- `Call CTA`

## Autonomous Within-Step Behavior

During sourcing, use:

- Sales Navigator account search when available
- Sales Navigator lead search when available
- LinkedIn company search
- LinkedIn people search
- LinkedIn jobs
- Google/search results
- Company websites
- Quote/contact/intake pages
- Careers pages

During research, inspect whatever pages are needed to verify:

- Company type
- Size fit
- Decision-maker
- Buying committee
- Signal A
- Signal B
- Evidence URL and quote
- Account POV
- Workflow Audit Angle

During outreach, write:

- Email subject
- Email draft
- LinkedIn draft for manual send
- Recommended angle
- Personalization hook
- Persona-specific 5-minute workflow audit CTA
- Sequence step and next-touch plan

After each step, apply `13_agent_evals.md` and write:

- Relevant eval scores
- `Eval Status`
- `Eval Failure Reason` when not passing
- `Eval Notes`
- `Estimated Tokens`
- `Last Run Tokens` when available
- `Tool Calls Used` when available

When messy inputs appear, apply `14_edge_cases.md` and write:

- `Edge Case Type`
- `Risk Flags`
- `Recovery Action`
- `Next Best Action`

Before a row becomes send-ready, apply `15_call_booking_self_eval.md` and write:

- `Booking Likelihood Score`
- `Booking Hypothesis`
- `Call CTA`
- `Next Best Action`

## Deterministic Stop Rules

Stop and park the row when:

- Evidence is missing: `DISQUALIFIED`
- Evidence is ambiguous: `NEEDS_REVIEW`
- Research hits access/tool failure: `ERROR` or `NEEDS_REVIEW`
- Draft is ready: `PENDING_APPROVAL`

Do not ask the operator what to do unless:

- The campaign goal itself is contradictory.
- A tool login is unavailable.
- Sending is requested but a row is missing email, evidence, draft content, or is rejected/held/disqualified/already sent.
- The row is high-risk or ambiguous enough that continuing would fabricate evidence.

## Sending Rule

The goal-to-result worker normally stops at `PENDING_APPROVAL`.

Email sending is a separate operator-commanded action:

- Operator must explicitly ask to send a campaign, row, or exact message.
- The row must be `Account Tier` A or strong B.
- The row must have a credible email address.
- The row must have an evidence-backed draft and evidence URL.
- The row must have a `Workflow Audit Angle`.
- The row must have `Eval Status` of `PASS`.
- The row must have `Deliverability Eval Score` of 4 or higher.
- A-tier rows should have `Booking Likelihood Score` of 4 or higher.
- The row must have a concrete `Booking Hypothesis` and `Call CTA`.
- The row must not be `REJECTED`, `HOLD`, `DISQUALIFIED`, `NEEDS_REVIEW`, `ERROR`, or `SENT`.
- Codex updates successfully sent rows to `SENT`.

LinkedIn remains draft-only.

## Result Shape

At the end of a campaign run, report:

- Campaign URL
- Number sourced
- Number researched
- Number qualified
- Number drafted
- Number pending approval
- Number A-tier
- Number B-tier
- Number with two mapped people
- Number eval-pass
- Number eval-fail
- Number eval-needs-review
- Number booking-priority rows
- Top edge cases
- Estimated campaign tokens
- Actual campaign tokens if available
- Number disqualified
- Number needs review
- Any blockers

Do not provide a long transcript of every browsed page unless the operator asks.

## Default Campaign Command

`Run Neyma Freight campaign: 10 freight forwarders/customs brokers in [region]. Use LinkedIn, websites, and search. Draft only with real evidence. Stop at PENDING_APPROVAL.`
