# Research Playbook

## Goal

Turn a candidate into an evidence-backed prospect record. Research must support qualification, recommended angle, and outreach draft.

## Source Priority

Research in this order:

1. Sales Navigator account page through the cofounder's logged-in session for headcount, geography, active employees, similar companies, and company fit.
2. Sales Navigator lead search through the cofounder's logged-in session for founder, ops, accounting/AP, billing, settlements, and carrier-payables contacts.
3. Company website.
4. Carrier, billing, payments, POD, claims, contact, or accounting pages.
5. Careers, jobs, hiring pages.
6. FMCSA/SAFER or equivalent authority lookup when MC/DOT/company data is available.
7. Freight directories and load-board-adjacent directories when available, such as DAT Directory or Truckstop broker/carrier directory surfaces.
8. LinkedIn company or jobs pages when available through the operator session.
9. LinkedIn decision-maker profiles when available through the operator session.
10. Search results, job boards, and business directories.

Sales Navigator is the default cockpit for account and buyer mapping. Public web, jobs, company pages, and authority/directory sources are still required for evidence. Do not use Sales Navigator alone to claim a company has invoice leakage or reconciliation pain.

## LinkedIn / Sales Navigator Session Rules

The cofounder is expected to be logged into his own LinkedIn/Sales Navigator session in the local browser.

Allowed:

- View company pages, jobs, people lists, and public/visible profile details.
- Use Sales Navigator account and lead search for sourcing and buying-committee mapping.
- Capture Sales Nav account URLs, lead URLs, search filters, and confidence notes.
- Use visible profile details to identify decision-makers.
- Capture profile-based personalization notes.
- Draft outreach for the operator to send later from the main account.

Not allowed:

- Send messages.
- Send connection requests.
- Follow, react, comment, endorse, or otherwise engage.
- Scrape at high volume or bypass access controls.
- Treat private profile details as evidence for pain claims unless they support a non-sensitive personalization note.

If LinkedIn/Sales Navigator access is unavailable or blocked, continue with public website, jobs pages, search results, and operator-provided notes, mark `Person Gate` as `REVIEW` when buyer mapping is weaker, and do not A-tier an account solely from weak person data.

## Research Steps

1. Confirm the company is a small freight brokerage.
2. Estimate headcount using website, LinkedIn, directory snippets, or public staff pages.
3. Identify region, brokerage mode, and service focus.
4. Look for Signal A: carrier-payables, POD, billing, invoice, or TMS workflow signal.
5. Look for Signal B: hiring for brokerage operations, carrier payables, billing, settlements, or load-entry roles.
6. Run the decision-maker discovery pass.
7. For A-tier candidates, map the buying committee.
8. Write `Account POV` and `Workflow Audit Angle`.
9. Review visible LinkedIn profile details for relevant personalization.
10. Capture evidence URLs and exact short evidence quotes.
11. Capture source stack, authority/directory notes, and signal search notes when available.
12. Write a neutral research summary.

## Signal A Evidence

Signal A is public evidence that the brokerage likely handles carrier invoices, PODs, billing docs, or carrier payment workflows outside a fully automated system.

Strong evidence:

- Instructions to email invoices, PODs, billing documents, claims, or accounting questions
- Carrier packet, carrier setup, billing, payment, or document-submission page
- Public TMS mention such as McLeod, Aljex, TAI, TMW, ARK, or EZ Loader
- Website language showing truckload brokerage, carrier network, many modes/lanes, or high-touch carrier operations
- Evidence that PODs, lumper receipts, accessorial backup, or carrier docs are collected through email, fax, portal, or manual upload

Capture:

- `Signal A Found`: yes/no
- `Signal A Evidence URL`
- `Signal A Evidence Quote`

Evidence quote should be short and exact. Do not quote more than needed.

## Signal B Evidence

Signal B is hiring for brokerage operations, carrier payables, billing, settlements, AP, or load-entry work.

Strong evidence:

- Current or recent posting for Carrier Payables Specialist
- Billing Specialist
- Settlements Specialist
- Accounting/AP Specialist
- Brokerage Operations Specialist
- Freight Broker Assistant
- Load Entry Specialist
- Logistics Coordinator
- Operations Coordinator
- Track and Trace Coordinator
- Claims or Compliance Coordinator

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
- `[Company] carrier payables`
- `[Company] billing manager`
- `[Company] accounting manager`
- `[Company] settlements`
- `[Company] freight brokerage operations`
- `[Company] LinkedIn people`

Prefer contacts in this order:

1. Founder
2. Owner or President
3. Managing Director
4. COO
5. VP Operations
6. Head of Operations
7. Operations Manager
8. Accounting Manager, AP Manager, Controller, Billing Manager, Carrier Payables, Settlements, or senior brokerage operations lead

Decision-maker confidence:

- `HIGH`: named person visibly tied to the exact company in a founder, owner, president, executive, or operations leadership role.
- `MEDIUM`: named person visibly tied to the exact company in a senior brokerage operations, billing, settlements, accounting, AP, or carrier-payables role.
- `LOW`: company page only, unclear current employment, old profile, directory-only mention, or title fit is weak.

If confidence is `LOW`, keep the company email draft but do not pretend the outreach is person-specific. If no named person is findable after a real pass, write `No named decision-maker found after LinkedIn/search pass` in `LinkedIn Profile Notes`.

Capture:

- Name
- Title
- Company LinkedIn URL, saved in `LinkedIn URL`
- Sales Nav account URL when available
- Sales Nav lead URL when available
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
- `Person 1 Sales Nav URL` when available
- `Person 1 Email` when verified or public
- `Person 1 Confidence`
- `Person 2 Name`
- `Person 2 Title`
- `Person 2 LinkedIn URL`
- `Person 2 Sales Nav URL` when available
- `Person 2 Email` when verified or public
- `Person 2 Confidence`

Prefer one executive/operator and one operations/accounting person:

- Founder, Owner, President, Managing Director, COO, VP Operations, or Head of Operations
- Operations Manager, Accounting Manager, AP Manager, Controller, Billing Manager, Carrier Payables, Settlements, or senior brokerage operations lead

Do not fill `Person 1 LinkedIn URL` or `Person 2 LinkedIn URL` with a company page or generic search URL. Leave it blank and explain the gap in `Decision Maker Search Notes`.

## Account POV and Workflow Audit Angle

`Account POV` is the account-level thesis. It should say what workflow appears likely from the evidenc