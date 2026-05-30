# Edge Cases and Recovery

## Purpose

This playbook defines what Neyma should do when a prospect does not fit the clean path.

The rule is simple: uncertainty parks the row. It does not push through.

Edge cases should be recorded so the system learns which messes are common and which ones matter.

## Notion Edge-Case Fields

Add these fields to `Neyma Freight Pipeline`:

| Field | Type | Notes |
| --- | --- | --- |
| Edge Case Type | Select | Main issue blocking clean progression |
| Risk Flags | Multi-select | Multiple risks that affect quality or send safety |
| Recovery Action | Text | What to do next |
| Next Best Action | Text | Single next operator or agent action |

Suggested `Edge Case Type` values:

- `No evidence`
- `Weak evidence`
- `Wrong person risk`
- `No direct person URL`
- `General inbox only`
- `Duplicate company`
- `Already contacted`
- `Bounce`
- `Out of office`
- `Referral`
- `Negative reply`
- `Signal disappeared`
- `Sales Nav unavailable`
- `Email unverified`
- `High token burn`
- `Generic draft`
- `LinkedIn risk`
- `Domain safety risk`
- `Other`

Suggested `Risk Flags`:

- `Missing evidence`
- `Weak signal`
- `Ambiguous company fit`
- `Ambiguous person`
- `No email`
- `Unverified email`
- `Duplicate`
- `Already sent`
- `Low personalization`
- `Deliverability risk`
- `LinkedIn safety risk`
- `High cost`

## Universal Routing

Use these rules before advancing state:

- If evidence is missing, do not draft.
- If evidence is weak, downgrade to B/C or route to `NEEDS_REVIEW`.
- If the person match is ambiguous, mark confidence `LOW` and do not A-tier.
- If the draft is generic, fail outreach eval and rewrite.
- If email is unverified, draft only and do not send.
- If domain safety is uncertain, do not send.
- If the row is already contacted, do not send Email 1 again.

## Edge-Case Table

| Edge Case | Detection | State/Tier Action | Recovery Action |
| --- | --- | --- | --- |
| No evidence | No Signal A/B evidence URL or quote | `DISQUALIFIED` or `NEEDS_REVIEW`; C-tier | Search one more targeted query, then stop |
| Weak evidence | Signal exists but does not clearly support manual-document pain | B/C-tier or `NEEDS_REVIEW` | Look for forms, careers, quote/intake pages |
| Wrong person risk | Person may not work at company or title is irrelevant | `NEEDS_REVIEW`; lower confidence | Verify with Sales Nav, website, or search |
| No direct person URL | Only company page or search result found | B/C-tier unless account is exceptional | Run Sales Nav people search |
| General inbox only | No named email found | B-tier at best | Use general inbox only if signal is strong |
| Duplicate company | Same company already active | Hold duplicate | Merge notes or keep best contact |
| Already contacted | Existing sent sequence exists | Do not resend Email 1 | Continue sequence only if timing is valid |
| Bounce | Email bounced | `FOLLOWING_UP` stops or row parks | Find verified email or new contact |
| Out of office | Auto-reply with return date | Keep account open | Set `Next Touch Date` after return |
| Referral | Prospect points to another person | `REPLIED`; update committee | Create/update new primary contact |
| Negative reply | Not interested or asks to stop | `CLOSED` | Do not follow up |
| Signal disappeared | Evidence URL breaks or page changed | `NEEDS_REVIEW` | Re-verify or replace evidence |
| Sales Nav unavailable | LinkedIn/Sales Nav cannot be accessed | Lower person confidence | Use public web/search; note limitation |
| Email unverified | Email is guessed or enrichment uncertain | Draft only | Verify through public source or enrichment |
| High token burn | Too much research on low-fit account | C-tier or stop | Cap research and move on |
| Generic draft | Hook could apply to anyone | `NEEDS_EDIT` | Rewrite from evidence quote and persona |
| LinkedIn risk | Action would message/connect/react from alt account | Stop | Draft only for manual send |
| Domain safety risk | Volume, bounce, or email quality is risky | Do not send | Reduce volume or improve verification |

## Duplicate and Account Lock Rules

Only one active outreach thread should exist per company unless multi-threading is intentional.

When a duplicate appears:

- Keep the row with better evidence and better person mapping.
- Move useful notes into the stronger row.
- Mark weaker row `HOLD`, `DISQUALIFIED`, or C-tier.
- Set `Edge Case Type` to `Duplicate company`.
- Explain the decision in `Recovery Action`.

Release the account lock when:

- The account is `CLOSED`, `DISQUALIFIED`, `REJECTED`, or `NO_REPLY`.
- The operator intentionally selects a better decision-maker.
- A referral names the correct person.

## Reply Edge Cases

### Positive Reply

Set:

- `State`: `REPLIED`
- `Reply Type`: `positive`
- `Next Best Action`: book or prepare the 5-minute workflow audit response

Do not auto-reply unless the operator explicitly asks.

### Referral

Set:

- `Reply Type`: `referral`
- `Edge Case Type`: `Referral`
- `Buying Committee`: update with referred person
- `Next Best Action`: draft a referred-person reply

### Objection

Set:

- `Reply Type`: `objection`
- `Learning Notes`: capture exact objection language
- `Next Best Action`: draft a concise answer or close if not relevant

Common objection categories:

- already have software
- not a priority
- too busy
- wrong person
- security/compliance concern
- no budget
- send information

### Not Interested

Set:

- `State`: `CLOSED`
- `Reply Type`: `not interested`
- `Edge Case Type`: `Negative reply`
- `Next Best Action`: none

Do not follow up.

### Bounce

Set:

- `Reply Type`: `bounce`
- `Edge Case Type`: `Bounce`
- `Deliverability Eval Score`: 1 or 2
- `Next Best Action`: find verified email or alternate contact

## Token-Burn Edge Cases

Stop research early when:

- The company is outside ICP.
- No manual-document signal appears after website, quote/contact, careers, and two targeted searches.
- Person mapping is impossible and the account has only weak signal.
- The account is likely C-tier.

Set:

- `Edge Case Type`: `High token burn`
- `Risk Flags`: `High cost`
- `Estimated Tokens`: current estimate
- `Recovery Action`: explain why the row was stopped

## LinkedIn Safety Edge Cases

LinkedIn is a research and drafting surface only.

If any step would require:

- sending a message
- connecting
- reacting
- commenting
- following
- automated scraping

Stop and set:

- `Edge Case Type`: `LinkedIn risk`
- `Risk Flags`: `LinkedIn safety risk`
- `Next Best Action`: draft manual message for operator

## Send-Safety Edge Cases

Do not send when:

- `Deliverability Eval Score` is below 4.
- Email is guessed or unverified.
- Evidence URL is missing.
- Account is C-tier.
- Row is already sent, rejected, held, disqualified, errored, or needs review.
- The draft does not pass outreach eval.

Set:

- `Edge Case Type`: `Domain safety risk`
- `Risk Flags`: `Deliverability risk`
- `Recovery Action`: explain exactly what must improve before send.

## Edge-Case Output Contract

When an edge case is detected, agents should return:

```json
{
  "edge_case_type": "",
  "risk_flags": [],
  "recovery_action": "",
  "next_best_action": "",
  "state_recommendation": "NEEDS_REVIEW | DISQUALIFIED | HOLD | CLOSED | NEEDS_EDIT",
  "tier_recommendation": "A | B | C | unchanged"
}
```

The orchestrator writes the fields and applies deterministic routing.
