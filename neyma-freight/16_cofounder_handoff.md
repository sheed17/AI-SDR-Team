# Cofounder Handoff Workflow

## Purpose

This playbook defines what Neyma should prepare for the human operator before any LinkedIn or email approach.

The AI system should automate the mindless work:

- finding the right businesses
- verifying ICP fit
- finding decision-makers
- gathering evidence
- writing account POVs
- drafting structured outreach
- surfacing edge cases
- prioritizing who is worth a human touch

The cofounder should handle the human work:

- final judgment
- LinkedIn approach
- relationship tone
- manual message/send
- calls
- referrals
- pilot close

## Handoff Principle

Do not hand the cofounder a list of leads.

Hand him a ranked queue of business cases.

Each row should answer:

1. Why this company?
2. Why this person?
3. Why now?
4. What workflow are we pointing at?
5. What should he say?
6. What should he do next?

## Cofounder Queue Fields

Add these fields to `Neyma Freight Pipeline`:

| Field | Type | Notes |
| --- | --- | --- |
| Cofounder Owner | Text/Person | Who owns the human touch |
| Handoff Status | Select | READY, NEEDS_ENRICHMENT, TOUCHED, REPLIED, BOOKED, CLOSED |
| Human Touch Priority | Number | 1-5 priority for the cofounder |
| LinkedIn Approach Type | Select | connect, message existing connection, comment/context, profile review only |
| LinkedIn Opener | Text | Exact suggested manual opener |
| Email Opener | Text | Exact suggested email opener |
| Proof Asset Needed | Select | none, sample extraction, workflow teardown, before/after sketch |
| Proof Asset Notes | Text | What proof would make the touch stronger |
| Pilot Fit | Select | HIGH, MEDIUM, LOW |
| Pilot Motion | Text | Recommended first pilot shape |

## Handoff Readiness

A row is handoff-ready only when:

- `Account Tier` is A or strong B.
- `Booking Priority` is `HIGH` for A-tier.
- `Person 1 LinkedIn URL` is a direct `/in/...` URL or a clear reason is written.
- Evidence URL and evidence quote/job title exist.
- `Account POV` is complete.
- `Workflow Audit Angle` is complete.
- `Booking Hypothesis` explains why this person may care now.
- `LinkedIn Opener` is written for manual use.
- `Next Best Action` is clear.

If any item is missing, use:

- `Handoff Status`: `NEEDS_ENRICHMENT`
- `Next Best Action`: the exact missing step

## Daily Cofounder Workflow

The cofounder should open Notion and work views in this order:

1. `Cofounder Today`
2. `Booking Priority`
3. `Needs Buying Committee`
4. `Edge Cases`
5. `Booked Call Learning`

Daily rhythm:

1. Review 10-20 prepared rows.
2. Choose 5-10 best human touches.
3. Open each LinkedIn profile manually.
4. Sense-check the person, title, company, and signal.
5. Send or save a manual LinkedIn touch only if it feels specific.
6. Mark `Handoff Status` as `TOUCHED`.
7. Set `Last Touch Date` and `Next Touch Date`.
8. Record any reply, referral, objection, or booked call.

## What The AI Should Prepare

For each A-tier account, prepare:

- company summary
- evidence-backed pain signal
- account POV
- workflow audit angle
- buying committee map
- primary and secondary person URLs
- LinkedIn profile notes
- LinkedIn opener
- email opener
- email draft
- follow-up angle
- booking hypothesis
- proof asset recommendation
- pilot fit and pilot motion

## LinkedIn Approach Types

Use `connect` when:

- the person is not connected
- profile fit is strong
- opener is short and specific

Use `message existing connection` when:

- the cofounder already has a connection
- the relationship context is clean

Use `comment/context` when:

- the person posted something relevant
- a comment would be more natural than a cold pitch

Use `profile review only` when:

- confidence is low
- the profile looks stale
- the person may not be the right buyer

## LinkedIn Opener Templates

Founder/Owner:

`Hi [Name], noticed [Company] handles [customs/import/freight workflow]. I’m looking at where small brokerages lose time re-keying POA/ISF/invoice docs into ops systems. Thought this might be relevant given [specific signal].`

Ops:

`Hi [Name], saw [specific signal] at [Company]. I’m looking at the intake-to-entry workflow where shipment docs get validated and keyed into internal systems. Worth comparing notes?`

Brokerage/Import:

`Hi [Name], noticed [specific POA/ISF/import signal]. We help turn messy customs docs into structured fields before entry prep. Thought this might be relevant to your team.`

Documentation:

`Hi [Name], saw [specific documentation signal]. We’re focused on reducing copy/paste from commercial invoices, packing lists, and carrier PDFs into ops workflows. Thought this might be useful context.`

## Email Opener Template

`Noticed [specific evidence] at [Company]. That looks like a workflow where the team may be collecting docs, validating fields, and re-keying shipment data into internal systems.`

## Proof Asset Framework

For A-tier accounts, decide whether a proof asset is needed.

Use:

- `none` when signal/person/timing are already strong.
- `sample extraction` when the workflow involves invoices, packing lists, POAs, ISF, bills of lading, or carrier PDFs.
- `workflow teardown` when the public intake flow itself is the hook.
- `before/after sketch` when the buyer likely needs to understand the operational change quickly.

Do not attach proof assets in cold email. Use them as a reason to book or continue:

`I can show what this would look like on one sample invoice/packing-list flow.`

## Pilot Motion

The first sale should be a narrow done-for-you pilot, not a broad platform pitch.

Good pilot shapes:

- commercial invoice and packing list extraction into spreadsheet/export
- POA intake packet to structured importer profile
- ISF worksheet to validated shipment fields
- carrier PDF to line-item table
- email/fax intake to reviewed brokerage work packet

Pilot framing:

`Start with one document type, one workflow, and a reviewed output. If it works, expand.`

## Call Framework

The first call is a workflow audit.

Ask:

1. Which docs are most painful to process?
2. Where do they arrive?
3. What fields are manually keyed?
4. Where do those fields go?
5. How often does this happen?
6. What breaks or slows things down?
7. Who reviews exceptions?
8. What would a useful structured output look like?

Do not lead with model architecture, generic AI, or a big platform demo.

## Close Path

Use this path:

1. Manual LinkedIn or email touch.
2. 5-minute workflow audit.
3. Ask for 1-3 sample or representative docs.
4. Produce structured output or workflow sketch.
5. Propose one narrow done-for-you pilot.
6. Convert to recurring automation if the pilot works.

## Handoff Output Contract

Every handoff-ready row should include:

```json
{
  "handoff_status": "READY",
  "human_touch_priority": 5,
  "linkedin_approach_type": "connect",
  "linkedin_opener": "",
  "email_opener": "",
  "proof_asset_needed": "sample extraction",
  "proof_asset_notes": "",
  "pilot_fit": "HIGH",
  "pilot_motion": "",
  "next_best_action": ""
}
```

If the row is not ready, set:

```json
{
  "handoff_status": "NEEDS_ENRICHMENT",
  "next_best_action": "Find second decision-maker LinkedIn URL"
}
```

## Definition Of Done

The AI has done its job when the cofounder can act in under 2 minutes per row.

He should not need to research from scratch.

He should only need to:

- inspect the profile
- decide whether the suggestion is good
- adjust tone if needed
- send manually
- record outcome
