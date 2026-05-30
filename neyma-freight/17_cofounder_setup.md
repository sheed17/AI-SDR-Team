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
- LinkedIn account with Sales Navigator if available
- Browser/Chrome session logged into LinkedIn
- Business email inbox access if he will send email

Recommended:

- Apollo trial or account later, only when email enrichment becomes the bottleneck
- Google Drive access if proof assets, sample docs, or Loom notes are stored there
- Shared calendar link for booked workflow audits

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
- `13_agent_evals.md`: evals and token usage
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

He should log into LinkedIn locally.

Sales Navigator is preferred for:

- account search
- lead search
- decision-maker mapping
- saving leads/accounts
- confirming direct person profiles

Rules:

- LinkedIn is for research and manual human touches.
- Do not automate LinkedIn messages.
- Do not connect, follow, react, comment, or message from an automation flow.
- The system drafts; the human decides.

### Gmail / Business Email

He needs Gmail or Workspace connected only if he will send email.

Before sending, confirm:

- sending inbox is the intended business inbox
- signature is correct
- reply handling is clear
- unsubscribe/suppression handling is understood
- low weekly send volume is maintained

The system can draft without Gmail. Sending requires explicit human instruction and validation.

### Apollo

Do not require Apollo on day one.

Use Apollo only when:

- A-tier accounts are strong
- direct person is found
- public email is missing
- email enrichment becomes the bottleneck

Apollo should not determine account quality. Account quality comes from ICP, evidence, person fit, and booking likelihood.

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
6. Log into LinkedIn/Sales Navigator in browser.
7. Run a test prompt.

Test prompt:

`Read neyma-freight/08_runbook.md and neyma-freight/11_worker_checklist.md. Confirm you understand the Neyma Freight workflow and list what tools are connected. Do not send anything.`

## First Test Campaign

Use a small test before trusting a full run:

`Run Neyma Freight research for 3 customs brokers in [region]. Use the playbooks, update Notion, map decision-makers, write LinkedIn/email drafts only when evidence is real, score booking likelihood, and stop at PENDING_APPROVAL. Do not send anything.`

Success looks like:

- 3 rows created or updated
- evidence URL captured for qualified rows
- direct decision-maker LinkedIn URL found when possible
- account tier assigned
- booking likelihood scored
- edge cases noted
- LinkedIn opener drafted
- email draft written only when evidence is real
- nothing sent

## Main Operating Command

Once setup is verified:

`Run Neyma Freight campaign for 10 freight forwarders/customs brokers in [region]. Prioritize A-tier accounts with manual-document evidence and a timing trigger. Map 2 decision-makers where possible, update Notion, draft email and LinkedIn outreach, score evals and booking likelihood, and stop at PENDING_APPROVAL. Do not send anything.`

## Human Role

His job is not to research from scratch.

His job is to:

- review `Booking Priority`
- open the decision-maker LinkedIn profile
- sense-check the suggested opener
- manually send or edit the LinkedIn touch
- send email only when intended
- record replies, objections, referrals, and booked calls

## Troubleshooting

If Notion is not connected:

- use local Markdown and a temporary spreadsheet
- do not run a large campaign
- reconnect Notion before serious work

If LinkedIn is unavailable:

- use public web/search
- mark lower confidence
- do not A-tier rows solely from weak person data

If Gmail is unavailable:

- draft only
- leave rows at `PENDING_APPROVAL`

If Apollo is unavailable:

- use public emails and general inboxes only when appropriate
- do not guess emails

If the system starts producing generic drafts:

- stop the run
- review `07_quality_rubric.md`, `13_agent_evals.md`, and `15_call_booking_self_eval.md`
- rerun only on rows with evidence

## Handoff Definition Of Done

The cofounder is ready when:

- repo is available locally
- Notion is connected
- LinkedIn/Sales Navigator is logged in
- Gmail is connected if he will send
- he can run the 3-account test campaign
- he can see rows in `Booking Priority`
- no messages are sent automatically
- he understands that LinkedIn touches are manual
