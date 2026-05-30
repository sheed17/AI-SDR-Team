# Orchestration and Execution Model

## Core Principle

Agents are agentic within a step. The flow between steps is deterministic.

Within a step, an agent can reason, browse, search, use LinkedIn as a sourcing/research surface through the operator session, and choose its own tool path. This is where autonomy belongs.

Between steps, the orchestrator decides what runs next from the prospect state. Agents do not call each other. Agents do not decide pipeline order. Each agent does one job, returns structured output, and stops.

The conveyor belt is deterministic. The work at each station is agentic.

## v0 Interpretation

For Neyma Freight v0, do not jump straight to a full backend.

Use this model as the operating contract:

- Notion is the source of truth.
- `Neyma Freight Campaigns` is the goal input surface.
- `Neyma Freight Pipeline` is the prospect execution surface.
- Prospect `State` is the position in the pipeline.
- A Codex/operator run can act as the worker loop at first.
- A simple polling worker can be added later when the manual process proves itself.
- Redis, Celery, FastAPI, Postgres, and custom UI remain out of scope until needed.

## State Machine

Canonical states:

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

Allowed main path:

`NEW -> SOURCING -> SOURCED -> RESEARCHING -> RESEARCHED -> QUALIFYING -> QUALIFIED -> DRAFTING -> DRAFTED -> PENDING_APPROVAL`

Approval path:

`PENDING_APPROVAL -> SENDING -> SENT -> FOLLOWING_UP`

Optional review path:

`PENDING_APPROVAL -> APPROVED -> SENDING -> SENT -> FOLLOWING_UP`

Terminal or parked paths:

- Any pre-approval step can route to `DISQUALIFIED`.
- Any step can route to `NEEDS_REVIEW`.
- Tool or validation failures can route to `ERROR`.
- Operator can route `PENDING_APPROVAL` to `REJECTED` or `HOLD`.
- Follow-up can end in `REPLIED`, `NO_REPLY`, or `CLOSED`.

## Transition Unit

For a prospect in state `S`:

1. Orchestrator looks up which handler owns state `S`.
2. Context assembly builds the handler input from Notion fields and the relevant Markdown playbook.
3. The handler runs one agentic step using available tools.
4. The handler returns structured output only.
5. Orchestrator validates output.
6. Orchestrator applies the three gates in `13_agent_evals.md`.
7. If valid and required gates pass, write output to Notion and advance state.
8. If invalid, retry once with a repair prompt.
9. If still invalid or a required gate fails, route to `NEEDS_REVIEW`, `DISQUALIFIED`, or C-tier.
10. Log the run in `Notes` or a separate run log.

The DB/Notion row is the handoff. Agents never pass directly to each other.

## State Handler Registry

Suggested handler map:

| Current State | Handler | Next State |
| --- | --- | --- |
| `NEW` | Discovery/Sourcing | `SOURCING` |
| `SOURCING` | Discovery/Sourcing | `SOURCED` |
| `SOURCED` | Research | `RESEARCHING` |
| `RESEARCHING` | Research | `RESEARCHED` |
| `RESEARCHED` | Qualification | `QUALIFYING` |
| `QUALIFYING` | Qualification | `QUALIFIED`, `DISQUALIFIED`, or `NEEDS_REVIEW` |
| `QUALIFIED` | Outreach | `DRAFTING` |
| `DRAFTING` | Outreach | `DRAFTED` |
| `DRAFTED` | Approval prep | `PENDING_APPROVAL` |
| `PENDING_APPROVAL` | Human review or explicit send command | `APPROVED`, `REJECTED`, `HOLD`, `NEEDS_EDIT`, or `SENDING` |
| `APPROVED` | Sending layer | `SENDING` only after explicit operator send command |
| `SENT` | Follow-up | `FOLLOWING_UP` |
| `FOLLOWING_UP` | Follow-up | `REPLIED`, `NO_REPLY`, `CLOSED`, or `NEEDS_REVIEW` |

## Deterministic Boundaries

These decisions belong to the orchestrator or operator, not the LLM:

- Which handler runs for a state.
- State transitions.
- Output validation.
- Gate validation and routing.
- Retry and repair.
- Routing to `NEEDS_REVIEW`.
- Approval gate.
- Send gate.
- Account de-duplication.
- Rate limits.
- Release of company/contact locks.

## Agentic Boundaries

These decisions belong inside a step:

- Which LinkedIn searches to run during sourcing.
- Which LinkedIn company, job, or profile results are worth adding as candidates.
- Which pages to inspect during research.
- Which visible LinkedIn profile details matter.
- Whether Signal A or Signal B is strong.
- How to map the buying committee inside a research step.
- How to write the account POV and workflow audit angle.
- Which hook is most relevant.
- How to phrase the email and LinkedIn draft.
- How to reason about follow-up wording.

## Review and Send Gate

`PENDING_APPROVAL` is the intentional human review stop for normal campaign runs.

The loop must not cross this gate unless:

- The operator explicitly asks to send a campaign, row, or exact message.
- The row passes send validation.

Notion approval fields are useful for review, but v0 sending is authorized by explicit operator command plus validation.

Email sending is authorized through Gmail after explicit send instruction.

LinkedIn drafts are prepared for manual send from the operator's main account. LinkedIn navigation is allowed for sourcing and research, but LinkedIn sending or engagement is not part of v0.

## LinkedIn Sourcing and Research Boundary

The logged-in LinkedIn alt/operator account is a sourcing and research surface only.

Allowed:

- Search for companies, jobs, people, and regional/service-line clues.
- Navigate company pages, people pages, jobs, and visible profiles.
- Add candidate companies and decision-makers to Notion.
- Capture role context and business-relevant profile notes.
- Draft personalized copy for the main account.

Forbidden:

- Sending messages.
- Connection requests.
- Comments, reactions, follows, endorsements, or profile edits.
- Automated high-volume scraping.
- Bypassing platform access controls.

## Email Sending Boundary

The connected Gmail account may be used for operator-commanded email outreach.

Allowed:

- Create Gmail drafts for qualified prospects.
- Send Gmail messages after the operator explicitly asks to send and the row has credible email, evidence, account tier A or strong B, workflow audit angle, and draft content.
- Update Notion to `SENT` after a successful send.

Forbidden:

- Sending without explicit operator command.
- Sending when evidence, credible email, account tier, workflow audit angle, or draft content is missing.
- Sending LinkedIn messages through the browser.
- Bulk sending without operator-selected rows and explicit send instruction.

## Account De-Dup Lock

Only one active contact per company should move through outreach at a time.

Acquire lock when:

- A prospect reaches `QUALIFIED`, or
- A draft is prepared for a decision-maker.

Hold other contacts at the same company unless the operator overrides.

Release lock when:

- Prospect reaches `DISQUALIFIED`, `REJECTED`, `CLOSED`, or `NO_REPLY`.
- Prospect is on `HOLD` beyond an operator-defined timeout.
- Operator manually releases the company.
- A better decision-maker is selected and the old contact is closed or rejected.

## Run Logging

Log each step with:

- Timestamp
- Prospect
- Starting state
- Ending state
- Handler
- Tool surfaces used
- Signal Gate
- Person Gate
- Message Gate
- Booking Priority
- Gate Notes
- Estimated tokens
- Actual tokens when available
- Tool call count when available
- Outcome
- Confidence
- Error or review reason
- Token/cost/latency if available

In v0, logs can live in Notion `Notes`. Later, move them to a separate run table.

## Worker Loop Pseudocode

```text
while run_is_active:
  campaigns = find_campaigns_with_state(REQUESTED, RUNNING)
  for campaign in campaigns:
    set_campaign_state(RUNNING)
    source_until_target_count_or_source_exhausted(campaign)

  prospects = find_rows_with_actionable_state()
  for prospect in prospects:
    if prospect.state == PENDING_APPROVAL:
      continue
    handler = registry[prospect.state]
    context = assemble_context(prospect, handler.playbook)
    result = handler.run(context)
    gate_result = apply_gates(result, prospect, "13_agent_evals.md")
    if validate(result) and required_gates_pass(gate_result):
      write_result_to_notion(prospect, result)
      write_gates_to_notion(prospect, gate_result)
      advance_state(prospect, result.next_state)
      log_run(prospect, result)
    else:
      repaired = retry_once(handler, context, validation_or_gate_error)
      repaired_gates = apply_gates(repaired, prospect, "13_agent_evals.md")
      if validate(repaired) and required_gates_pass(repaired_gates):
        write_result_to_notion(prospect, repaired)
        write_gates_to_notion(prospect, repaired_gates)
        advance_state(prospect, repaired.next_state)
        log_run(prospect, repaired)
      else:
        route_to_needs_review_or_disqualified(prospect, validation_or_gate_error)

  update_campaign_counters()
  mark_done_when_campaign_has_no_actionable_rows()
```

## Build Order

1. Keep using Markdown playbooks and Notion manually for the first 20 prospects.
2. Use `Neyma Freight Campaigns` to turn operator goals into run inputs.
3. Add structured output templates for research, qualification, and outreach.
4. Use `11_worker_checklist.md` as the Codex-run worker checklist that processes rows by state.
5. Add Notion sync/polling only after the manual flow proves useful.
6. Add deterministic glue such as YepCode or a simple script only when handoffs become repetitive.
7. Use Gmail for explicit operator-commanded email sends; keep LinkedIn as draft-only until the operator deliberately changes that policy.
