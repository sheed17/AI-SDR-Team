# Cofounder Setup Handoff

## Purpose

This is the setup checklist for handing Neyma Freight to a cofounder on another computer.

The handoff is:

- give him the repo
- connect the same tools
- confirm access
- run a small test campaign
- make sure he can operate the Notion queue without starting from scratch

This is not a backend deployment.

## What He Needs

Required:

- Local copy of this repo
- Codex access
- Notion access to `Neyma Freight`
- LinkedIn account with Sales Navigator
- Browser/Chrome session logged into LinkedIn and Sales Navigator
- Business Gmail/Workspace inbox access for autonomous email sends during `run pipeline`

Recommended:

- Apollo trial or account later, only when email enrichment becomes the bottleneck
- Google Drive access if proof assets, sample docs, or Loom notes are stored there
- Shared calendar link for booked reconciliation audits

Not needed yet:

- Backend server
- Database
- Redis/Celery
- Custom UI
- LinkedIn automation tools
- Bulk email infra

## Repo Handoff

Give him the folder:

`neyma-freight/`

He should understand the key files:

- `01_icp.md`: locked ICP and pain
- `02_discovery.md`: how candidates are found
- `03_research.md`: how evidence and decision-makers are researched
- `04_qualification.md`: how rows are scored
- `05_outreach.md`: how outreach is drafted
- `06_followup.md`: how replies/follow-ups are handled
- `07_quality_rubric.md`: quality bar
- `08_runbook.md`: operating manual
- `09_execution_model.md`: state-machine model
- `10_goal_to_result.md`: campaign worker contract
- `11_worker_checklist.md`: what Codex follows during a run
- `12_enterprise_gtm.md`: account-first GTM model
- `13_agent_evals.md`: three-gate eval and optional token usage
- `14_edge_cases.md`: edge-case routing
- `15_call_booking_self_eval.md`: booked-call optimization
- `16_cofounder_handoff.md`: optional operator queue workflow
- `17_cofounder_setup.md`: this setup handoff

## Tool Connections

### Notion

He needs access to:

- `Neyma Freight` page
- `Neyma Freight Pipeline`
- `Neyma Freight Campaigns`

Confirm he can:

- open the databases
- edit rows
- create new campaign rows
- see views:
  - `A-Tier ABM`
  - `Needs Buying Committee`
  - `Booking Priority`
  - `Edge Cases`
  - `Eval Review`
  - `Booked Call Learning`

### LinkedIn / Sales Navigator

He should log into LinkedIn and Sales Navigator locally before running the pipeline.

Sales Navigator is the main SDR cockpit for:

- account search
- lead search
- decision-maker mapping
- saving leads/accounts
- confirming direct person profiles
- finding similar brokerages
- checking active employees and rough headcount
- mapping founder, ops, accounting/AP, billing, settlements, and carrier-payables contacts

Rules:

- Sales Navigator is for account sourcing, lead sourcing, research, and context.
- LinkedIn is for research and manual human touches only.
- Do not automate LinkedIn messages.
- Do not connect, follow, react, comment, or message from an automation flow.
- The system drafts LinkedIn touches; the human decides whether to send them manually.

### Gmail / Business Email

He needs Gmail or Workspace connected for the fully autonomous version.

Before sending, confirm:

- sending inbox is the intended business inbox
- signature is correct
- reply handling is clear
- unsubscribe/suppression handling is understood
- low weekly send volume is maintained

The system can draft without Gmail. With Gmail connected, `run pipeline` is the explicit instruction to send eligible emails after validation.

### Apollo

Do not require Apollo on day one.

Use Apollo only when:

- A-tier accounts are strong
- direct person is found
- public email is missing
- email enrichment becomes the bottleneck

Apollo should not determine account quality. Account quality comes from ICP, evidence, person fit, and booking priority.

### Google Drive

Use Drive later for:

- sample document proof assets
- workflow teardown docs
- Loom/script notes
- before/after extraction examples

Drive is optional for the first handoff unless proof assets are ready.

## Environment Setup

On his machine:

1. Open Codex.
2. Put the repo/folder in his workspace.
3. Confirm the `neyma-freight/` folder is visible.
4. Connect Notion.
5. Connect Gmail only if he will send.
6. Log into LinkedIn and Sales Navigator in browser.
7. Run a test prompt.

Test prompt:

`Read neyma-freight/08_runbook.md and neyma-freight/11_worker_checklist.md. Confirm you understand the Neyma Freight workflow and list what tools are connected. Do not send anything.`

## First Test Campaign

Use a small test before trusting a full run:

`run pipeline for 3 in NorCal`

That should automatically expand to:

- source 3 small freight brokerage prospects in Northern California
- research carrier-payables/reconciliation evidence
- map decision-makers
- qualify or disqualify rows
- draft email and LinkedIn copy when evidence is real
- send eligible Gmail emails after validation
- park blocked rows
- summarize what happened

Success looks like:

- 3 rows created or updated
- evidence URL captured for qualified rows
- direct decision-maker LinkedIn URL found when possible
- account tier assigned
- booking priority set
- edge cases noted
- LinkedIn opener drafted
- email sent only when validation passes
- weak or blocked rows parked without asking for approval

## Main Operating Command

Once setup is verified:

`run pipeline for 10 in [region]`

Other valid casual commands:

- `run pipeline`
- `run pipeline for 3 in norcal`
- `run pipeline 5 dallas`
- `run freight pipeline in chicago`

## Human Role

His job is not to research from scratch.

His job is to:

- say `run pipeline for [count] in [region]`
- review the end summary
- manually send or edit LinkedIn touches if desired
- record replies, objections, referrals, and booked calls

He should not have to:

- pick sources
- translate prompts into campaign fields
- approve each row
- decide the next pipeline step
- inspect Sales Navigator unless he wants to
- babysit the run

## Troubleshooting

If Notion is not connected:

- use local Markdown and a temporary spreadsheet
- do not run a large campaign
- reconnect Notion before serious work

If LinkedIn is unavailable:

- use public web/search
- mark lower confidence
- do not A-tier rows solely from weak person data

If Sales Navigator is unavailable:

- use regular LinkedIn and public web/search
- mark `Person Gate` as `REVIEW` when buyer mapping is weaker
