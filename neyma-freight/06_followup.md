# Follow-Up Playbook

## Goal

Prepare concise follow-ups for sent outreach, while preserving the explicit operator send gate.

Follow-ups are drafts unless a human explicitly asks to send.

## Eligibility

Create a follow-up draft only when:

- The original outreach was sent by explicit operator command.
- The prospect has not replied.
- The original evidence is still valid.
- The follow-up references the same grounded signal or a newly found real signal.
- `Workflow Audit Angle` is still relevant.

## Send Gate

Never send a follow-up unless:

- `State` is `SENT` or `FOLLOWING_UP`
- The operator explicitly asked to send the follow-up
- The row is not rejected, held, disqualified, errored, or already closed

If send instruction is unclear, draft only and stop.

## Follow-Up Timing

Suggested manual cadence:

- Follow-up 1: 3-5 business days after send
- Follow-up 2: 7-10 business days after follow-up 1
- Close: after no reply to follow-up 2, unless operator chooses another path

## Follow-Up 1 Template

`Hi [First Name], quick follow-up on my note about [specific signal].`

`If your team is manually checking carrier invoices, PODs, or accessorials against rate cons, Neyma can usually start with one narrow workflow and show what the exception queue would look like.`

`Worth a 5-minute reconciliation audit?`

## Follow-Up 2 Template

`Hi [First Name], closing the loop here.`

`I reached out because [specific signal] looked like a possible carrier-payables reconciliation workflow around [invoice/POD/rate-con process]. If this is not a priority, no worries.`

`If it is on your radar later, happy to compare notes.`

## Reply Handling

If prospect replies:

- Set `State` to `REPLIED`
- Capture summary in `Outcome` and `Notes`
- Set `Reply Type` to `positive`, `referral`, `objection`, `not interested`, `bounce`, or `no reply`
- Capture useful wording in `Learning Notes`
- Update `Meeting Outcome` when the reply leads toward or away from a reconciliation audit
- Update `Objection Category` when the reply contains an objection
- Update `Booking Hypothesis` if the reply confirms or disproves the original reason for outreach
- Do not auto-respond
- Draft a response only when the operator asks

If prospect declines:

- Set `State` to `CLOSED`
- Set `Outcome` to `Not interested` or a more specific reason

If prospect asks for details:

- Set `State` to `REPLIED`
- Prepare a concise response grounded in the original signal
- Prefer moving toward a 5-minute reconciliation audit over sending a long expla