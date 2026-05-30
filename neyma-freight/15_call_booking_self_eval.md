# Call Booking Self-Eval

## Purpose

This playbook evaluates whether Neyma is likely to produce booked 5-minute workflow audits, not just researched rows or sent emails.

The system should optimize for booked conversations with real operators who have document-heavy workflows.

## Core Question

For every A-tier or send-ready B-tier row, ask:

`Would this specific person have a clear reason to say yes to a 5-minute workflow audit this week?`

If the answer is not clear, improve the account, person, angle, or timing before sending.

## Notion Booking Fields

Add these fields to `Neyma Freight Pipeline`:

| Field | Type | Notes |
| --- | --- | --- |
| Booking Likelihood Score | Number | 1-5 likelihood of getting a useful reply or workflow-audit call |
| Booking Hypothesis | Text | Why this person may care now |
| Call CTA | Text | Exact CTA used in outreach |
| Meeting Outcome | Select | booked, interested, referred, not now, no show, unqualified, lost |
| Objection Category | Select | Main objection if one appears |

## Booking Likelihood Score

Use:

- `5`: Strong account, strong signal, right person, good timing, sharp workflow audit angle.
- `4`: Good shot; one minor weakness.
- `3`: Possible, but likely needs better person or stronger trigger.
- `2`: Low chance; hold or enrich.
- `1`: Do not send.

An A-tier send should normally have `Booking Likelihood Score` of 4 or 5.

## What Drives Booked Calls

Booked calls usually require five things:

1. Real pain signal.
2. Correct person.
3. Immediate relevance.
4. Low-friction CTA.
5. Credible reason to trust the sender.

Neyma already handles 1, 2, and 4 reasonably. The biggest improvement opportunities are 3 and 5.

## Current Pipeline Self-Eval

### Strengths

- Account-first, not lead-first.
- Evidence required before drafting.
- Buying committee mapping exists for A-tier accounts.
- LinkedIn person URLs are separated from company URLs.
- Drafts are short and tied to a workflow audit.
- Eval and edge-case routing prevent obvious bad sends.
- Notion gives the operator a clear control surface.

### Weaknesses

- The current motion may still be too cold if the account has no urgency trigger.
- Public evidence proves a workflow exists, but not that the company is actively trying to fix it.
- General inbox sends are weaker than named-person sends.
- A 5-minute audit is low-friction, but it may still feel abstract without a concrete example.
- There is not yet a strong proof asset: sample extraction, before/after workflow, or one-page teardown.
- Follow-ups may restate the same angle without adding new value.
- The system tracks replies, but should more explicitly learn what booked meetings have in common.

## Improvements To Actually Get Booked Calls

### 1. Add a Stronger Trigger Layer

Prioritize accounts with both:

- manual-document signal
- timing signal

Timing signals:

- hiring for documentation/import/logistics roles
- recent growth or new location
- job posts mentioning systems, data entry, customs entries, TMS, ERP, CargoWise, Descartes, NetSuite, Magaya, Cargowise, or ACE/ABI workflows
- recent LinkedIn posts about growth, new services, bottlenecks, compliance, or hiring
- company page activity suggesting operational change

If no timing signal exists, the account can still be good, but the booking likelihood should be lower.

### 2. Build a Micro-Proof Asset

For A-tier accounts, create a tiny proof point before outreach:

- a 3-line workflow audit note
- a before/after sketch
- a sample document extraction example using a public/sample logistics doc
- a one-paragraph teardown of the observed intake flow

Do not attach files in cold email. Mention it lightly:

`I can show what this would look like on one sample invoice/packing-list flow.`

### 3. Improve Persona-Specific Angles

Founder/Owner:

- angle: fewer manual ops bottlenecks without hiring another coordinator
- avoid: technical extraction details too early

COO/Ops:

- angle: reduce re-keying and exception handling in the intake-to-entry workflow
- avoid: vague AI pitch

Brokerage/Import Manager:

- angle: cleaner POA/ISF/commercial-invoice intake before entry prep
- avoid: sounding like a replacement for brokerage judgment

Documentation Lead:

- angle: reduce repetitive copy/paste from carrier/customer docs
- avoid: over-positioning as a strategic transformation

### 4. Use a Two-Person ABM Path for A-Tier

For A-tier accounts:

- Primary email goes to best executive/operator persona.
- LinkedIn manual touch goes to same or second person.
- If referral happens, update buying committee and move to referred-person path.

Do not blast all people at once. Multi-threading should be deliberate and low-volume.

### 5. Make Follow-Ups Add Value

Follow-up 1 should add a specific example:

`The workflow I had in mind was POA/ISF intake -> field validation -> entry-prep packet, not a broad AI platform.`

Follow-up 2 should offer a sample:

`Happy to mock this up against a sample commercial invoice/packing list if useful.`

This is better than “just bumping this.”

### 6. Track Reply-to-Meeting Conversion

Do not stop at reply rate.

Track:

- positive reply rate
- referral rate
- meeting booked rate
- meeting held rate
- qualified opportunity rate
- wrong-person rate
- objection category

Booked-call learning should be more important than sent-email learning.

### 7. Add a Pre-Send Call Booking Eval

Before sending, score:

- Does the evidence show a real workflow?
- Is this the best person?
- Is there a timing trigger?
- Is the CTA concrete?
- Is there a micro-proof offer?
- Is the email credible and non-generic?

If the answer is weak, enrich before sending.

## Pre-Send Booking Checklist

Before a row is sent, check:

- `Booking Likelihood Score` is 4 or higher for A-tier.
- `Booking Hypothesis` explains why this person may care now.
- `Call CTA` is exactly stated.
- Account has Signal A or Signal B evidence.
- A-tier has at least two mapped people or a note explaining the gap.
- Outreach names the workflow audit angle.
- Email does not sound like an AI automation vendor blast.
- Follow-up path adds value, not only bumps.

## Call CTA Examples

Good:

`Worth a 5-minute workflow audit?`

`Open to a 5-minute look at where this could remove re-keying?`

`Would it be useful if I showed what this could look like on one sample invoice/packing-list flow?`

Weak:

`Would you like a demo?`

`Can I get 30 minutes?`

`Are you interested in AI automation?`

## Learning Loop For Booked Calls

After every positive reply or booked call, update:

- `Meeting Outcome`
- `Reply Type`
- `Objection Category`
- `Learning Notes`
- `Booking Hypothesis`

Capture:

- evidence signal that caused the reply
- title/persona that replied
- exact CTA used
- whether the workflow audit ask landed
- objections or questions raised
- what proof asset would have helped

## Pipeline Scorecard

Review weekly:

| Metric | Good v0 Target |
| --- | ---: |
| A-tier accounts with 2+ mapped people | 70%+ |
| A-tier rows with strong timing signal | 50%+ |
| Direct person LinkedIn URL coverage | 80%+ |
| Verified/public email coverage | 60%+ |
| Positive reply rate | 8-15% |
| Workflow audit booked rate | 2-5% |
| Bounce rate | Under 3% |
| Wrong-person replies | Under 15% |

These are not permanent benchmarks. They are starting guardrails for a low-volume, high-quality motion.

## Honest Self-Eval

Current system grade: `B`

Why not higher:

- It is strong on research discipline and avoiding garbage sends.
- It is not yet strong enough on urgency, proof, and call conversion learning.
- The first pilot sent too many rows before the enterprise-style quality loop was fully mature.
- The motion still needs better trigger sourcing and a repeatable micro-proof asset.

What makes it potentially top-tier:

- It is already account-first.
- It separates evidence, person mapping, draft quality, deliverability, and booking likelihood.
- It has a way to learn from each row.
- It keeps LinkedIn manual and low-risk.
- It can become extremely good if the first 20-50 accounts are treated as a learning lab, not a volume campaign.

Next best improvement:

Focus the next campaign on 10 A-tier accounts with both manual-document evidence and a timing trigger. Send fewer emails, but make each one strong enough that the recipient feels the note was written after real operational observation.
