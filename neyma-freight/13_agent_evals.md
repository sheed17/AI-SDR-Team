# Agent Evals

## Purpose

Use this eval layer to keep Neyma Freight disciplined without turning the operator workflow into paperwork.

For v0, the daily eval is three gates:

1. Signal Gate
2. Person Gate
3. Message Gate

If those pass, the row can move forward. If one fails, the row parks, gets enriched, or is disqualified.

The older multi-score eval model is useful later for scale and cost optimization, but it is not the daily operating loop for two people manually reviewing rows.

## Daily Eval Fields

Use these fields in `Neyma Freight Pipeline`:

| Field | Type | Notes |
| --- | --- | --- |
| Signal Gate | Select | PASS, REVIEW, FAIL |
| Person Gate | Select | PASS, REVIEW, FAIL |
| Message Gate | Select | PASS, REVIEW, FAIL |
| Booking Priority | Select | HIGH, MEDIUM, LOW |
| Gate Notes | Text | Short reason for any REVIEW/FAIL or priority choice |
| Estimated Tokens | Number | Optional rough estimate for the row |
| Last Run Tokens | Number | Optional actual tokens if available |
| Tool Calls Used | Number | Optional tool-call count if available |

Use these fields in `Neyma Freight Campaigns`:

| Field | Type | Notes |
| --- | --- | --- |
| Estimated Campaign Tokens | Number | Optional expected total token use |
| Actual Campaign Tokens | Number | Optional actual total token use |
| Gate Pass Count | Number | Rows where all three gates pass |
| Gate Review Count | Number | Rows with at least one REVIEW |
| Gate Fail Count | Number | Rows with at least one FAIL |
| Cost Notes | Text | Optional cost assumptions and anomalies |

## Gate Values

Use:

- `PASS`: good enough to move forward.
- `REVIEW`: potentially useful, but needs human judgment or enrichment.
- `FAIL`: do not move forward.

## Signal Gate

Question:

`Is the pain signal real, cited, and relevant to carrier invoice reconciliation or brokerage back-office work?`

PASS requires:

- Evidence URL exists.
- Evidence quote or job title exists.
- The evidence supports carrier invoice intake, POD collection, lumper/accessorial backup, billing, settlements, carrier payables, AP, load entry, TMS usage, email/fax/portal document workflows, or related brokerage operations paperwork.
- The outreach hook can point to the evidence without exaggerating it.

REVIEW when:

- Evidence is real but weak.
- The evidence is relevant to operations but not clearly tied to billing, carrier payables, PODs, invoices, TMS, or load closeout.
- The evidence URL is broad and needs a better page.
- There is a timing signal but no clear manual workflow signal.

FAIL when:

- No evidence exists.
- Evidence does not support the pain claim.
- The hook would be based on industry assumptions.
- The source is unreliable or not specific to the company.

Routing:

- `PASS`: continue.
- `REVIEW`: enrich or park in `NEEDS_REVIEW`.
- `FAIL`: no draft; use `DISQUALIFIED` or C-tier.

## Person Gate

Question:

`Is this the right person or clearly the best available contact?`

PASS requires:

- Direct person LinkedIn URL when findable.
- Person appears attached to the company.
- Title fits the buying committee:
  - Founder, Owner, President
  - COO, VP Ops, Head of Ops, Operations Manager
  - Accounting Manager, AP Manager, Controller
  - Billing Manager, Carrier Payables, Settlements
  - Senior brokerage operations lead
- Confidence is honest.

REVIEW when:

- Person is plausible but not confirmed.
- Only one person is mapped for a likely A-tier account.
- A general inbox is the only available contact.
- LinkedIn profile is stale or ambiguous.

FAIL when:

- Person works at the wrong company.
- Person field contains a company page or generic search URL.
- Title is clearly irrelevant.
- No credible person or inbox exists for a send-ready row.

Routing:

- `PASS`: continue.
- `REVIEW`: enrich or downgrade from A-tier.
- `FAIL`: do not send; hold, enrich, or disqualify.

## Message Gate

Question:

`Is the outreach specific enough that it does not feel like spam?`

PASS requires:

- First line references the observed signal.
- Message names the workflow angle.
- CTA is low-friction, usually a 5-minute reconciliation audit.
- No unsupported claims about savings, volume, staffing, variance rates, invoice leakage, or urgency.
- Copy is concise and calm.
- LinkedIn draft is safe for manual use.

REVIEW when:

- Message is directionally good but too generic.
- CTA feels too broad.
- Persona angle could be sharper.
- Proof asset or sample extraction mention would make the touch stronger.

FAIL when:

- Message could go to any freight company.
- Hook is not evidence-backed.
- It sounds like a generic AI automation pitch.
- It asks for a full demo too early.
- It overclaims.

Routing:

- `PASS`: eligible for handoff or send validation.
- `REVIEW`: rewrite before handoff/send.
- `FAIL`: do not send.

## Booking Priority

Use `Booking Priority` to decide what the cofounder should touch first.

HIGH:

- All three gates pass.
- Account is A-tier or strong B-tier.
- There is a real workflow angle.
- Person is a strong buyer/operator.
- There is a reason this may matter now, such as hiring, growth, visible carrier-payables work, TMS usage, billing friction, POD collection, or a sharp reconciliation workflow.

MEDIUM:

- Signal is real but timing/person/proof is weaker.
- Useful account, but not first in the queue.
- Needs one enrichment step or human judgment.

LOW:

- Weak signal, weak person, weak timing, general inbox only, or C-tier.
- Hold, enrich later, or disqualify.

## Gate Notes

Keep `Gate Notes` short.

Good examples:

- `Signal PASS: carrier page routes invoices/PODs to billing inbox. Person PASS: owner direct /in profile. Message PASS: hook references invoice/rate-con reconciliation. Priority HIGH.`
- `Person REVIEW: company fit and billing signal strong, but only general inbox found. Needs Sales Nav person search.`
- `Signal FAIL: homepage only; no carrier-payables, billing, POD, TMS, or reconciliation evidence found.`

## Token Logging

Token tracking is optional in the manual two-person loop.

Use it when it changes behavior:

- high-cost research on weak accounts
- comparing Sales Nav-heavy runs to public-web runs
- deciding when to add deterministic automation
- estimating cost per handoff-ready account

Simple estimates:

- C-tier early stop: `15000`
- B-tier researched and drafted: `35000`
- A-tier with buying committee mapping: `60000`

Leave `Last Run Tokens` blank when actual token usage is unavailable.

## Legacy Advanced Scores

The older fields may remain in Notion as advanced instrumentation:

- `Discovery Eval Score`
- `Signal Eval Score`
- `Buying Committee Eval Score`
- `Qualification Eval Score`
- `Outreach Eval Score`
- `Deliverability Eval Score`
- `Overall Eval Score`
- `Eval Status`
- `Eval Failure Reason`
- `Eval Notes`
- `Booking Likelihood Score`

Do not require these in normal v0 runs.

Use them only when:

- debugging a bad campaign
- doing a weekly QA pass
- comparing channels or costs
- preparing for a more automated worker later

## Output Contract

Every handoff-ready row should have:

```json
{
  "signal_gate": "PASS | REVIEW | FAIL",
  "person_gate": "PASS | REVIEW | FAIL",
  "message_gate": "PASS | REVIEW | FAIL",
  "booking_priority": "HIGH | MEDIUM | LOW",
  "gate_notes": "",
  "estimated_tokens": null,
  "last_run_tokens": null,
  "tool_calls_used": null
}
```

## Weekly Review

Once per week, review:

- HIGH priority rows that did not get replies.
- REVIEW rows that could become HIGH with one enrichment step.
- FAIL rows that reveal a bad sourcing pattern.
- Replies, referrals, objections, and booked calls.

Update `Learning Notes` with:

- best signals
- best titles
- best regions
- best reconciliation audit angles
- objections by persona
- copy patterns to reuse
- copy patterns to ban
