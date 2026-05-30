# Neyma Freight Runbook

## v0 Operating Model

Neyma Freight v0 is a lightweight, operator-led AI SDR workflow.

It uses:

- Markdown playbooks for agent instructions
- Notion as the pipeline, state, and review surface
- Browser/Chrome/Computer Use for research
- LinkedIn operator session for sourcing, profile/company/job research, and personalization only
- Gmail for email sends after explicit operator send instruction
- SendGrid only later, after the same explicit operator send instruction model is proven
- Google Sheets only if Notion is unavailable

Do not build:

- Backend app
- FastAPI service
- Postgres database
- Redis/Celery queue
- Custom frontend
- Vector database
- Unattended sending without an explicit operator command
- Complex agent framework

The execution pattern is defined in `09_execution_model.md`: agents are agentic within one step, while state transitions between steps are deterministic.

The goal-to-result campaign loop is defined in `10_goal_to_result.md` and `11_worker_checklist.md`.

The enterprise-style GTM motion is defined in `12_enterprise_gtm.md`.

The agent eval layer is defined in `13_agent_evals.md`.

Edge-case routing is defined in `14_edge_cases.md`.

Booked-call improvement is defined in `15_call_booking_self_eval.md`.

Optional operator queue guidance is defined in `16_cofounder_handoff.md`.

Cofounder machine/tool setup is defined in `17_cofounder_setup.md`.

## Campaign Database

Create a Notion database named:

`Neyma Freight Campaigns`

This is the operator's goal input surface. A campaign row tells Codex what result to produce without ping-ponging between steps.

Recommended fields:

| Field | Type | Notes |
| --- | --- | --- |
| Campaign Name | Title | Human-readable campaign name |
| Goal | Text | Plain-English campaign goal |
| Region | Text | Target region |
| Target Count | Number | Number of prospects to process |
| ICP Segment | Select/Text | Freight forwarders, customs brokers, or both |
| Source Mix | Text | LinkedIn, websites, search, jobs |
| Stop State | Select | Usually `PENDING_APPROVAL` |
| Campaign State | Select | REQUESTED, RUNNING, PAUSED, DONE, ERROR, NEEDS_REVIEW |
| Prospects Sourced | Number | Counter |
| Prospects Researched | Number | Counter |
| Prospects Qualified | Number | Counter |
| Prospects Drafted | Number | Counter |
| Prospects Pending Approval | Number | Counter |
| Prospects Sent | Number | Counter |
| Estimated Campaign Tokens | Number | Expected total token use |
| Actual Campaign Tokens | Number | Sum of actual tokens when available |
| Gate Pass Count | Number | Rows where all three gates pass |
| Gate Review Count | Number | Rows with at least one REVIEW |
| Gate Fail Count | Number | Rows with at least one FAIL |
| Cost Notes | Text | Cost assumptions and anomalies |
| Notes | Text | Run log and blockers |

## Notion Database

Create a Notion database named:

`Neyma Freight Pipeline`

Recommended fields:

| Field | Type | Notes |
| --- | --- | --- |
| Company | Title | Company name |
| Website | URL | Primary website |
| Region | Text or Select | City, state, country, or market |
| Headcount Estimate | Text | Include source or uncertainty |
| Decision Maker | Text | Name |
| Decision Maker Title | Text or Select | Founder, Managing Director, COO, VP Operations, etc. |
| Decision Maker LinkedIn URL | URL | Direct `/in/...` person profile; leave blank or note LOW confidence if unavailable |
| Decision Maker Confidence | Select | HIGH, MEDIUM, LOW |
| Decision Maker Source | Select | LinkedIn profile, LinkedIn company, website, search, directory, operator-provided |
| Decision Maker Search Notes | Text | Search queries, why selected, and uncertainty |
| LinkedIn URL | URL | Company LinkedIn page or company-level LinkedIn context |
| Account Tier | Select | A, B, C |
| Buying Committee | Text | Account-level map of founder/ops/brokerage contacts |
| Primary Persona | Select | Founder, Ops, Brokerage, Import/Export, Documentation |
| Person 1 Name | Text | Primary target name |
| Person 1 Title | Text | Exact visible title |
| Person 1 LinkedIn URL | URL | Direct `/in/...` profile |
| Person 1 Email | Email | Verified or public email |
| Person 1 Confidence | Select | HIGH, MEDIUM, LOW |
| Person 2 Name | Text | Secondary buying committee contact |
| Person 2 Title | Text | Exact visible title |
| Person 2 LinkedIn URL | URL | Direct `/in/...` profile |
| Person 2 Email | Email | Verified or public email |
| Person 2 Confidence | Select | HIGH, MEDIUM, LOW |
| Account POV | Text | Evidence-grounded account thesis |
| Workflow Audit Angle | Text | Narrow workflow for 5-minute audit CTA |
| Sequence Step | Select | Not started, Email 1, LinkedIn touch, Follow-up 1, Follow-up 2, Breakup, Complete |
| Last Touch Date | Date | Most recent email or manual LinkedIn touch |
| Next Touch Date | Date | Next planned touch |
| Reply Type | Select | positive, referral, objection, not interested, bounce, no reply |
| Learning Notes | Text | Golden-set learnings and reply analysis |
| Signal Gate | Select | PASS, REVIEW, FAIL |
| Person Gate | Select | PASS, REVIEW, FAIL |
| Message Gate | Select | PASS, REVIEW, FAIL |
| Booking Priority | Select | HIGH, MEDIUM, LOW |
| Gate Notes | Text | Short reason for any REVIEW/FAIL or priority choice |
| Estimated Tokens | Number | Expected token usage for the row |
| Last Run Tokens | Number | Actual token usage when available |
| Tool Calls Used | Number | Count of tool calls when available |
| Edge Case Type | Select | Main issue blocking clean progression |
| Risk Flags | Multi-select | Quality, deliverability, LinkedIn, or cost risks |
| Recovery Action | Text | What to do next when a row is parked |
| Next Best Action | Text | Single next operator or agent action |
| Booking Hypothesis | Text | Why this person may care now |
| Call CTA | Text | Exact CTA used in outreach |
| Meeting Outcome | Select | booked, interested, referred, not now, no show, unqualified, lost |
| Objection Category | Select | Main objection when one appears |
| Email | Email | Only credible sourced or approved enrichment |
| Initial Source URL | URL | First place the prospect was found |
| Source Type | Select | Website, search, LinkedIn company, LinkedIn job, LinkedIn profile, directory, operator-provided |
| LinkedIn Profile Notes | Text | Profile-based personalization notes from operator session |
| Personalization Hook | Text | Human-safe hook for main-account outreach |
| Signal A Found | Checkbox | Manual intake signal |
| Signal A Evidence URL | URL | Required when Signal A is true |
| Signal A Evidence Quote | Text | Short exact quote |
| Signal B Found | Checkbox | Hiring signal |
| Signal B Evidence URL | URL | Required when Signal B is true |
| Signal B Job Title | Text | Exact relevant job title |
| Research Summary | Text | 3-5 sentence summary |
| Qualification Score | Number | 0-10 |
| Confidence | Select | HIGH, MEDIUM, LOW |
| Disqualifier | Select or Text | Reason if not qualified |
| Recommended Angle | Text | Signal-grounded outreach angle |
| Email Subject | Text | Draft subject |
| Email Draft | Text | Human-reviewed email draft |
| LinkedIn Draft | Text | Human-reviewed LinkedIn draft |
| State | Select | Pipeline state |
| Approval Status | Select | Optional review state |
| Outcome | Select or Text | Reply, meeting, closed, not interested, etc. |
| Notes | Text | Golden-set learnings and operator notes |

State values:

- `NEW`
- `SOURCING`
- `SOURCED`
- `RESEARCHING`
- `RESEARCHED`
- `QUALIFYING`
- `QUALIFIED`
- `DISQUALIFIED`
- `DRAFTING`
- `DRAFTED`
- `PENDING_APPROVAL`
- `APPROVED`
- `REJECTED`
- `HOLD`
- `SENDING`
- `SENT`
- `FOLLOWING_UP`
- `REPLIED`
- `NO_REPLY`
- `CLOSED`
- `ERROR`
- `NEEDS_REVIEW`

Approval values:

- `PENDING`
- `APPROVED`
- `REJECTED`
- `HOLD`
- `NEEDS_EDIT`

## Standard Workflow

1. Discovery
   - Use `02_discovery.md`.
   - Use `13_agent_evals.md` to apply the Signal Gate when evidence is found.
   - Add candidates to Notion.
   - Set `State` to `NEW`, `SOURCING`, or `SOURCED`.

2. Research
   - Use `03_research.md`.
   - Use `13_agent_evals.md` to apply Signal Gate and Person Gate.
   - Prioritize company website, quote/contact pages, careers pages, LinkedIn, search results.
   - Capture Signal A and Signal B evidence.
   - For A-tier candidates, map at least two buying-committee contacts when possible.

3. Qualification
   - Use `04_qualification.md`.
   - Use `13_agent_evals.md` to decide whether the row can advance, needs review, or should stop.
   - Use `14_edge_cases.md` to route ambiguity, duplicates, weak evidence, and safety issues.
   - Score 0-10.
   - Set `Account Tier` to `A`, `B`, or `C`.
   - Set `QUALIFIED`, `DISQUALIFIED`, or `NEEDS_REVIEW`.

4. Outreach Drafting
   - Use `05_outreach.md`.
   - Use `13_agent_evals.md` to apply Message Gate and Booking Priority.
   - Use `15_call_booking_self_eval.md` to decide `Booking Priority`.
   - Draft only for qualified prospects with evidence.
   - Complete `Account POV` and `Workflow Audit Angle`.
   - Set `State` to `PENDING_APPROVAL`.
   - Set `Approval Status` to `PENDING`.

5. Human Review
   - Operator can review evidence and drafts in Notion.
   - Operator may set approval to `APPROVED`, `REJECTED`, `HOLD`, or `NEEDS_EDIT`, but this is optional in v0.

6. Sending
   - Email sending through Gmail is authorized when the operator explicitly asks to send a campaign, row, or exact message.
   - Before sending, Codex must verify the row has a real email address, an evidence-backed draft, and is not rejected, held, disqualified, already sent, or missing evidence.
   - LinkedIn outreach remains draft-only in v0. The operator sends manually from the main account.
   - After send, update `State` to `SENT`.

7. Follow-Up
   - Use `06_followup.md`.
   - Draft follow-ups.
   - Stop for explicit operator send command before any follow-up send.

## Canonical Operator Command

`Run Neyma Freight Discovery for 10 prospects. Use the playbooks, research each company, update Notion, draft outreach only when evidence is real, and stop at PENDING_APPROVAL.`

## Goal-to-Result Operator Command

`Run Neyma Freight campaign: 10 freight forwarders/customs brokers in Southern California. Use LinkedIn, websites, and search. Draft only with real evidence. Stop at PENDING_APPROVAL.`

## Agent Execution Rules

- Never send without an explicit operator send command.
- Campaign runs should move from goal to review/send queue without asking the operator to hand off between sourcing, research, qualification, and drafting.
- LinkedIn browsing through the alt/operator account is allowed for sourcing, research, and personalization only.
- LinkedIn is also allowed for sourcing companies, jobs, and decision-makers.
- Do not connect, follow, react, comment, endorse, or send LinkedIn messages from the alt/operator account.
- Draft LinkedIn copy for the operator to send from the main account.
- Codex may send emails through Gmail when the operator explicitly asks to send a campaign, row, or exact message and the row passes send validation.
- Every pain claim must cite an evidence URL.
- Every hook must be grounded in Signal A or Signal B.
- Every A-tier account must include a buying-committee map or a note explaining why a second person could not be found.
- `Decision Maker LinkedIn URL`, `Person 1 LinkedIn URL`, and `Person 2 LinkedIn URL` must be direct person profile URLs, not company pages.
- Each send-ready row must have `Signal Gate`, `Person Gate`, and `Message Gate`.
- Any gate with `REVIEW` or `FAIL` should route to `NEEDS_REVIEW`, `DISQUALIFIED`, C-tier, or an enrichment action before drafting or sending.
- Every edge case should write `Edge Case Type`, `Risk Flags`, `Recovery Action`, and `Next Best Action`.
- A-tier sends should normally have `Booking Priority` of `HIGH`.
- Each send-ready row should include a `Booking Hypothesis` and exact `Call CTA`.
- Token usage should be estimated per row and logged when actual token counts are available.
- The CTA should ask for a 5-minute workflow audit unless the operator explicitly requests another conversion goal.
- If no real signal exists, do not fabricate.
- Use `DISQUALIFIED` or `NEEDS_REVIEW` when evidence is absent or ambiguous.
- Keep drafts specific, concise, and calm.
- Record golden-set learnings for the first 20 prospects.

## First 20 Prospect Success Criteria

v0 is successful when:

- 20 prospects have gone through research and qualification.
- Every qualified prospect has evidence.
- Every draft has a specific hook.
- Every A-tier prospect has an `Account POV`, `Workflow Audit Angle`, and buying-committee mapping.
- Every drafted prospect passes the three gates or has a clear `NEEDS_REVIEW` reason.
- Every A-tier send has a booking hypothesis, CTA, and next best action.
- Operator can review, approve, reject, or hold rows in Notion.
- No message is sent without an explicit operator send command.

## Optional Notion Views

Create these views if useful:

- `Needs Research`: `State` is `NEW` or `RESEARCHING`
- `Needs Sourcing`: `State` is `NEW` or `SOURCING`
- `Ready to Draft`: `State` is `QUALIFIED`
- `A-Tier ABM`: `Account Tier` is `A`
- `Needs Buying Committee`: `Account Tier` is `A` and `Person 2 LinkedIn URL` is empty
- `Workflow Audit Queue`: `Workflow Audit Angle` is not empty
- `Gate Review`: `Signal Gate` is `REVIEW`
- `Person Gate Review`: `Person Gate` is `REVIEW`
- `Message Gate Review`: `Message Gate` is `REVIEW`
- `Gate Failures`: `Signal Gate` is `FAIL`
- `Person Gate Failures`: `Person Gate` is `FAIL`
- `Message Gate Failures`: `Message Gate` is `FAIL`
- `Edge Cases`: `Edge Case Type` is not empty
- `High Priority Touches`: `Booking Priority` is `HIGH`
- `This Week Touches`: `Next Touch Date` is not empty
- `Reply Learning`: `Reply Type` is not empty
- `Approval Queue`: `State` is `PENDING_APPROVAL`
- `Needs Edit`: `Approval Status` is `NEEDS_EDIT`
- `Disqualified`: `State` is `DISQUALIFIED`
- `Golden Set`: first 20 manually reviewed prospects

## Fallback

If Notion is unavailable, use Google Sheets with the same fields and state values. Treat the sheet as temporary and migrate back to Notion when available.
