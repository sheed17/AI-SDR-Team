# Research Playbook

## Goal

Turn a candidate into an evidence-backed prospect record. Research must support qualification, recommended angle, and outreach draft.

## Source Priority

Research in this order:

1. Company website
2. Contact, request quote, get started, or shipment intake pages
3. Careers, jobs, hiring pages
4. Sales Navigator account and lead search when available
5. LinkedIn company or jobs pages when available through the operator session
6. LinkedIn decision-maker profiles when available through the operator session
7. Search results, job boards, and business directories

## LinkedIn Operator Session Rules

The operator may provide access to a logged-in LinkedIn alt/operator account for research.

Allowed:

- View company pages, jobs, people lists, and public/visible profile details.
- Use visible profile details to identify decision-makers.
- Capture profile-based personalization notes.
- Draft outreach for the operator to send later from the main account.

Not allowed:

- Send messages.
- Send connection requests.
- Follow, react, comment, endorse, or otherwise engage.
- Scrape at high volume or bypass access controls.
- Treat private profile details as evidence for pain claims unless they support a non-sensitive personalization note.

If LinkedIn access is unavailable or blocked, continue with public website, jobs pages, search results, and operator-provided notes.

## Research Steps

1. Confirm the company is a freight forwarder or customs broker.
2. Estimate headcount using website, LinkedIn, directory snippets, or public staff pages.
3. Identify region and service focus.
4. Look for Signal A: manual intake workflow.
5. Look for Signal B: hiring for document-heavy operations roles.
6. Run the decision-maker discovery pass.
7. For A-tier candidates, map the buying committee.
8. Write `Account POV` and `Workflow Audit Angle`.
9. Review visible LinkedIn profile details for relevant personalization.
10. Capture evidence URLs and exact short evidence quotes.
11. Write a neutral research summary.

## Signal A Evidence

Signal A is a public manual-intake workflow.

Strong evidence:

- A downloadable quote, customs, or shipment PDF form
- Instructions to fill and email forms
- Instructions to email shipping documents
- Email-only quote workflow
- A static quote form asking for manual follow-up without automated pricing or upload workflow

Capture:

- `Signal A Found`: yes/no
- `Signal A Evidence URL`
- `Signal A Evidence Quote`

Evidence quote should be short and exact. Do not quote more than needed.

## Signal B Evidence

Signal B is hiring for document-heavy operations work.

Strong evidence:

- Current or recent posting for Manifest Clerk
- Data Entry Clerk
- Logistics Coordinator
- Import/Export Specialist
- Documentation Clerk
- Customs Entry Writer
- Brokerage Entry Clerk

Capture:

- `Signal B Found`: yes/no
- `Signal B Evidence URL`
- `Signal B Job Title`

## Decision-Maker Research

Decision-maker discovery is required before outreach drafting. Do this even when the company has a general inbox.

Search LinkedIn and public search with combinations of:

- `[Company] founder`
- `[Company] owner`
- `[Company] president`
- `[Company] COO`
- `[Company] operations`
- `[Company] customs broker`
- `[Company] import manager`
- `[Company] brokerage manager`
- `[Company] LinkedIn people`

Prefer contacts in this order:

1. Founder
2. Owner or President
3. Managing Director
4. COO
5. VP Operations
6. Head of Operations
7. Operations Manager
8. Customs Brokerage Manager, Import Manager, Export Manager, or senior licensed customs broker

Decision-maker confidence:

- `HIGH`: named person visibly tied to the exact company in a founder, owner, president, executive, or operations leadership role.
- `MEDIUM`: named person visibly tied to the exact company in a senior customs, import/export, brokerage, or operations role.
- `LOW`: company page only, unclear current employment, old profile, directory-only mention, or title fit is weak.

If confidence is `LOW`, keep the company email draft but do not pretend the outreach is person-specific. If no named person is findable after a real pass, write `No named decision-maker found after LinkedIn/search pass` in `LinkedIn Profile Notes`.

Capture:

- Name
- Title
- Company LinkedIn URL, saved in `LinkedIn URL`
- Direct decision-maker profile URL, saved in `Decision Maker LinkedIn URL`
- LinkedIn Profile Notes when visible and relevant
- Personalization Hook for approved outreach
- Email only when available from a credible public source or approved enrichment workflow

Keep the two LinkedIn URLs separate:

- `LinkedIn URL` is the company page or company-level LinkedIn context.
- `Decision Maker LinkedIn URL` must be a direct `/in/...` person profile when one is findable.

Do not put a company page, people-search URL, or generic LinkedIn search URL in `Decision Maker LinkedIn URL` unless the search notes explicitly say no direct person profile was found. In that fallback case, set `Decision Maker Confidence` to `LOW`.

Do not guess email addresses unless the operator has approved an enrichment step.

## Enterprise Account Mapping

Neyma uses account-first research. Choose the account, verify the signal, then map the people.

Set `Account Tier`:

- `A`: strong ICP fit, strong signal, at least one credible email, custom account POV, and two direct person LinkedIn URLs when findable.
- `B`: good ICP fit and real signal, but only one person/general inbox or lighter personalization.
- `C`: weak signal, unclear ICP, missing decision-maker, missing email, or needs enrichment.

For A-tier accounts, fill:

- `Buying Committee`
- `Person 1 Name`
- `Person 1 Title`
- `Person 1 LinkedIn URL`
- `Person 1 Email` when verified or public
- `Person 1 Confidence`
- `Person 2 Name`
- `Person 2 Title`
- `Person 2 LinkedIn URL`
- `Person 2 Email` when verified or public
- `Person 2 Confidence`

Prefer one executive/operator and one operations/brokerage person:

- Founder, Owner, President, Managing Director, COO, VP Operations, or Head of Operations
- Customs Brokerage Manager, Import Manager, Export Manager, Documentation lead, or senior licensed customs broker

Do not fill `Person 1 LinkedIn URL` or `Person 2 LinkedIn URL` with a company page or generic search URL. Leave it blank and explain the gap in `Decision Maker Search Notes`.

## Account POV and Workflow Audit Angle

`Account POV` is the account-level thesis. It should say what workflow appears likely from the evidence, without overclaiming.

Example:

`They appear to rely on customer-submitted POA/ISF docs, so the likely workflow is document intake -> validation -> re-keying into brokerage systems.`

`Workflow Audit Angle` names the narrow process to inspect in a 5-minute call.

Good examples:

- `POA onboarding packet -> structured importer profile`
- `ISF worksheet -> clean shipment fields`
- `Commercial invoice and packing list -> line item extraction`
- `Email/fax intake -> validated brokerage work packet`

The audit angle must connect to Signal A or Signal B evidence.

## Profile Personalization

Use profile details only to make the draft more relevant and human, not to invent business pain.

Good personalization sources:

- Role scope, such as operations, customs brokerage, import/export, or growth.
- Recent company move or promotion.
- Mentioned freight lane, market, service line, or operational responsibility.
- Public posts about logistics, documentation, customs, or forwarding operations.

Avoid:

- Sensitive personal details.
- Overfamiliar comments.
- Anything unrelated to the business reason for outreach.
- Pain claims based only on a person's title.

The final hook still needs Signal A or Signal B evidence. Profile details can shape the opener or CTA, but they cannot replace evidence.

## Research Summary Format

Use 3-5 concise sentences:

- What the company does
- Estimated size and region
- What signal was found
- Why the signal suggests manual document work
- Any useful LinkedIn profile personalization
- Any uncertainty

## Stop Conditions

Before setting a final research state, apply the Signal Eval and Buying Committee Eval in `13_agent_evals.md` and write:

- `Signal Eval Score`
- `Buying Committee Eval Score`
- `Eval Status`
- `Eval Failure Reason` when not passing
- `Eval Notes`
- `Estimated Tokens`
- `Tool Calls Used` when available

Set `State` to `NEEDS_REVIEW` when:

- Evidence is ambiguous.
- Company fit is plausible but not confirmed.
- The decision-maker is unclear.

Set `State` to `DISQUALIFIED` when:

- The company is outside the ICP.
- No real Signal A or Signal B exists after reasonable research.
- Evidence cannot support a specific outreach hook.

Never fabricate signals, quotes, titles, or emails.
