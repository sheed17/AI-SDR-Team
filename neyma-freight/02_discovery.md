# Discovery Playbook

## Goal

Find candidate freight forwarders and customs brokers that may fit the ICP, then add them to the `Neyma Freight Pipeline` Notion database as `NEW`, `SOURCING`, or `SOURCED`.

Discovery is not qualification. Do not draft outreach during discovery.

## Inputs

Operator should provide one or more of:

- Region
- City or port
- Target count
- Search theme, such as customs brokers, freight forwarders, import specialists, or ocean freight

Example operator command:

`Run Neyma Freight Discovery for 10 prospects in Southern California. Stop after adding candidates to Notion.`

## Search Queries

Use Sales Navigator when available, search, browser research, and the logged-in LinkedIn operator session. Start narrow.

Examples:

- `freight forwarder customs broker Los Angeles`
- `customs broker import export specialist Miami`
- `freight forwarding company get a quote PDF form`
- `site:company.com freight forwarding "download" "pdf"`
- `site:company.com customs broker "email" "documents"`
- `"Manifest Clerk" "freight forwarder"`
- `"Documentation Clerk" "customs broker"`
- `"Import Export Specialist" "freight forwarding"`

## LinkedIn as a Sourcing Surface

LinkedIn can be used to find:

- Freight forwarder and customs broker company pages.
- Companies by region, port, service line, or keyword.
- Decision-makers at target companies.
- Jobs that reveal Signal B.
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
- Keywords: customs broker, freight forwarder, import, export, customs brokerage, NVOCC, logistics.
- Lead titles: Founder, Owner, President, Managing Director, COO, VP Operations, Operations Manager, Customs Brokerage Manager, Import Manager, Export Manager, Documentation.

Save or capture promising accounts only when there is a plausible route to a manual-document signal and a buying committee.

## Candidate Capture

For each candidate, capture:

- Company
- Website
- Region
- Initial source URL
- Source Type: website, search, LinkedIn company, LinkedIn job, LinkedIn profile, directory, or operator-provided
- Initial note on why it may fit
- Company LinkedIn URL when available
- Early Account Tier guess: A, B, or C
- State: `NEW`
- Approval Status: `PENDING`

If actively sourcing, set State to `SOURCING`. If the candidate is ready for research, set State to `SOURCED`.

## Early Exclusions

Skip obvious non-fits:

- Large global forwarders with thousands of employees
- Shipping lines, trucking-only carriers, parcel carriers
- SaaS vendors or marketplaces
- Companies with no active website
- Consumer moving companies

## Discovery Quality Bar

Add a candidate only if there is a plausible path to finding:

- A decision-maker
- A manual intake signal
- A relevant hiring signal
- A LinkedIn company, job, or profile clue that points to real freight/brokerage operations
- Or enough company detail to research further

Do not pad the list to hit the target count. A smaller clean list is better than a noisy one.

Before advancing a candidate, apply the Discovery Eval in `13_agent_evals.md` and write:

- `Discovery Eval Score`
- `Eval Status`
- `Eval Notes`
- `Estimated Tokens`

## Output

Update Notion with candidate rows.

Do not send messages.

Do not create email drafts unless the operator explicitly asks to continue into research and qualification.
