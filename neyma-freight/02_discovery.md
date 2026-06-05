# Discovery Playbook

## Goal

Find candidate small freight brokerages that may fit the ICP, then add them to the `Neyma Freight Pipeline` Notion database as `NEW`, `SOURCING`, or `SOURCED`.

Discovery is not qualification. Do not draft outreach during discovery.

## Inputs

Operator should provide one or more of:

- Region
- City or port
- Target count
- Search theme, such as truckload freight brokerages, carrier payables, freight billing, TMS users, or regional brokerages

Example operator command:

`Run Neyma Freight Discovery for 10 small freight brokerages in Southern California. Stop after adding candidates to Notion.`

## Search Queries

Use Sales Navigator when available, search, browser research, and the logged-in LinkedIn operator session. Start narrow.

Examples:

- `truckload freight brokerage Los Angeles`
- `freight broker carrier payables billing specialist`
- `freight brokerage operations coordinator McLeod`
- `freight brokerage TMS Aljex carrier invoice`
- `site:company.com freight broker "carrier packet"`
- `site:company.com freight broker "POD" "invoice"`
- `site:company.com "carrier payables" "freight"`
- `"Carrier Payables Specialist" "freight brokerage"`
- `"Billing Specialist" "freight broker"`
- `"Settlements Specialist" "freight brokerage"`
- `"Brokerage Operations Specialist" "freight"`
- `"McLeod" "freight broker" "operations"`

## LinkedIn as a Sourcing Surface

LinkedIn can be used to find:

- Freight brokerage company pages.
- Companies by region, port, service line, or keyword.
- Decision-makers at target companies.
- Jobs that reveal carrier-payables, billing, settlements, load-entry, or brokerage-ops work.
- Similar companies from people profiles, company pages, and search results.

Allowed sourcing actions:

- Search LinkedIn for companies, people, and jobs.
- Open visible company pages, job pages, and people profiles.
- Capture URLs and short notes into Notion.
- Use profile/company context to decide whether a prospect is worth researching.

Not allowed during sourcing:

- Send messages.
- Send connection requests.
- Follow companies or people.
- React, comment, endorse, or otherwise engage.
- Scrape at high volume or bypass access controls.

LinkedIn is a finding tool and context source. It is not a sending surface in v0.

## Sales Navigator Sourcing

When Sales Navigator is available, use account-first searches:

- Region: target city, port, state, or trade lane.
- Company headcount: start with 1-10 and 11-50, then inspect fit.
- Keywords: freight broker, truckload brokerage, logistics brokerage, 3PL brokerage, carrier sales, freight billing, carrier payables, settlements, McLeod, Aljex, TAI, TMW.
- Lead titles: Founder, Owner, President, COO, VP Operations, Operations Manager, Accounting Manager, AP Manager, Controller, Billing Manager, Carrier Payables, Settlements.

Save or capture promising accounts only when there is a plausible route to a carrier-payables/reconciliation signal and a buying committee.

## Candidate Capture

For each candidate, capture:

- Company
- Website
- Region
- Initial source URL
- Source Type: website, search, LinkedIn company, LinkedIn job, LinkedIn profile, directory, or operator-provided
- Initial note on why it may fit
- Company LinkedIn URL when available
- TMS mention when available
- Early Account Tier guess: A, B, or C
- State: `NEW`
- Approval Status: `PENDING`

If actively sourcing, set State to `SOURCING`. If the candidate is ready for research, set State to `SOURCED`.

## Early Exclusions

Skip obvious non-fits:

- Large global forwarders or enterprise 3PLs with hundreds/thousands of employees
- Shipping lines, trucking-only carriers, parcel carriers, warehouse-only providers
- SaaS vendors or marketplaces
- Companies with no active website
- Consumer moving companies
- Customs-brokerage or freight-forwarding-only firms with no truckload brokerage or carrier-payables fit

## Discovery Quality Bar

Add a candidate only if there is a plausible path to finding:

- A decision-maker
- A carrier invoice, POD, billing, settlements, or TMS workflow signal
- A relevant hiring signal
- A LinkedIn company, job, or profile clue that points to real brokerage operations
- Or enough company detail to research further

Do not pad the list to hit the target count. A smaller clean list is better than a noisy one.

Before advancing a candidate, apply the Signal Gate in `13_agent_evals.md` when evidence is found and write:

- `Signal Gate`
- `Gate Notes`
- `Estimated Tokens`

## Output

Update Notion with candidate rows.

Do not send messages.

Do not create email drafts unless the operator explicitly asks to continue into research and qualification.
