# Goal-to-Result Worker

## Purpose

Run Neyma Freight from a single operator goal to a concrete result: a Notion queue of evidence-backed, account-first GTM rows with buying committee mapping and reconciliation-audit outreach.

This is the v0 worker contract. It is not a backend service. Codex acts as the worker loop until the process proves itself enough to justify deterministic glue.

## Operator Goal Shape

The operator should be able to say:

`Run pipeline.`

That plain command means:

- Use the default region and target count unless the operator gives different values.
- Use Sales Navigator as the primary account and buyer-mapping cockpit through the cofounder's logged-in session.
- Use public web/jobs/authority sources to verify evidence and avoid false positives.
- Source, research, qualify, draft, and send eligible Gmail emails.
- Park weak or blocked rows automatically.
- Draft LinkedIn copy only; do not send LinkedIn messages.
- Summarize the run at the end.

Natural-language variants are valid and should be normalized automatically:

- `run pipeline for 3 in NorCal`
- `run pipeline for 5 in Dallas`
- `run pipeline 10 socal brokerages`
- `find 3 and run the pipeline`
- `run the freight pipeline in Chicago`

The worker should infer:

- Count from the number in the prompt, defaulting to 10.
- Region from the location phrase, defaulting to United States.
- ICP as small freight brokerages unless the operator explicitly changes it.
- Source mix from the default SDR stack: Sales Navigator first, then public web/jobs/authority/directory verification.
- Stop behavior as send eligible Gmail emails, park blocked rows, and draft LinkedIn only.

The worker should not ask for handoff instructions between discovery, research, qualification, and drafting.

If a goal is missing region or count, use reasonable defaults:

- Count: 10 prospects
- Region: United States
- Source mix: Sales Navigator, LinkedIn, public search, FMCSA/SAFER or authority lookup when available, DAT/Truckstop directories when available, company websites, jobs
- Stop state: `SENT` for eligible Gmail emails; `NEEDS_REVIEW`, `DISQUALIFIED`, or `ERROR` for blocked rows

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

## Best SDR Team Standard

When the operator says `run pipeline`, optimize for the best autonomous SDR outcome, not just task completion.

The standard is:

- Sales Navigator first for account discovery, active employee/headcount checks, similar-account expansion, and buyer mapping.
- Public evidence second for the pain claim: company website, jobs, carrier/billing pages, authority lookups, directories, and search results.
- Account-first, not lead-first: qualify the brokerage before investing heavily in a person.
- Evidence-gated: no pain claim, draft, or send without a cited Signal A or Signal B.
- Buyer-mapped: prefer founder/owner/ops plus accounting/AP/carrier-payables coverage for A-tier accounts.
- Autonomous by default: infer count, region, source mix, and next step; do not ask for approval between stages.
- Safe by default: send eligible Gmail only after validation; never automate LinkedIn messages, follows, comments, reactions, or connection requests.
- Learning-oriented: write edge cases, gate notes, booking hypothesis, and reply learning so the first 20-50 runs improve targeting.

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
   - `SENDING`
   - `SENT`
4. Stop sent rows at `SENT`; park blocked rows at `NEEDS_REVIEW`, `DISQUALIFIED`, or `ERROR`.
5. Update campaign counters.
6. Mark campaign `DONE` when the target number of prospects has reached `SENT`, `DISQUALIFIED`, `NEEDS_REVIEW`, or `ERROR` and no actionable rows remain for the campaign.

For enterprise-style runs, a row is not truly ready unless it also has:

- `Account Tier`
- `Primary Persona`
- `Buying Committee` for A-tier accounts
- `Account POV`
- `Workflow Audit Angle`
- `Signal Gate`
- `Person Gate`
- `Message Gate`
- `Booking Priority`
- `Gate Notes`
- `Estimated Tokens`
- `Edge Case Type` when messy
- `Booking Hypothesis`
- `Call CTA`

## Autonomous Within-Step Behavior

During sourcing, use:

- Sales Navigator account search through the cofounder's logged-in session as the primary account-universe builder.
- Sales Navigator lead search through the cofounder's logged-in session as the primary buyer-mapping surface.
- Public search to build the initial account universe.
- FMCSA/SAFER or equivalent authority lookup when available to verify broker/authority status and avoid carrier-only false positives.
- DAT Directory, Truckstop directories, or similar freight-specific directories when available to find and verify brokerages.
- LinkedIn company search
- LinkedIn people search
- LinkedIn jobs
- Google/search results
- Company websites
- Carrier, billing, POD, claims, contact, and accounting pages
- Careers pages

During sourcing, run the account-first passes from `02_discovery.md`:

1. Sales Nav universe pass: collect likely small freight brokerages in the region.
2. Fi