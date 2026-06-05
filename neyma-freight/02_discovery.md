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

Use an account-first sourcing motion. The goal is not to collect every freight company; it is to build a small account universe, then keep only brokerages with a plausible carrier-payables or reconciliation signal.

## Source Stack

Use sources in this order:

1. Sales Navigator account search through the cofounder's logged-in session for account discovery, headcount, geography, and similar-company expansion.
2. Sales Navigator lead search through the cofounder's logged-in session for founder, ops, accounting/AP, billing, settlements, and carrier-payables contacts.
3. Public search for company websites, carrier/billing pages, and signal discovery.
4. FMCSA/SAFER or equivalent public authority lookup when an MC/DOT/company record is available, to verify broker/forwarder/carrier status and avoid carrier-only false positives.
5. Freight directories and load-board-adjacent directories when available, such as DAT Directory or Truckstop broker/carrier directory surfaces.
6. LinkedIn jobs, Google jobs, company careers pages, and job boards for timing signals.

Assume the cofounder is logged into LinkedIn Sales Navigator unless the tool/browser shows otherwise. If Sales Navigator is unavailable, continue with public search and note the limitation in `Gate Notes`.

## Account-First Sourcing Workflow

Run sourcing in passes:

1. Sales Nav universe pass: collect companies that appear to be small truckload freight brokerages in the target region.
2. Fit pass: remove carrier-only fleets, warehouse-only firms, software vendors, marketplaces, enterprise 3PLs, and forwarding/customs-only operators without truckload brokerage fit.
3. Signal pass: search each remaining account for carrier invoice, POD, billing, settlements, TMS, AP, or brokerage-ops evidence.
4. Sales Nav person pass: only after the account has plausible fit/signal, map founder/owner/ops/accounting/carrier-payables contacts.
5. Capture pass: add clean rows to Notion with source, signal notes, Sales Nav URLs, mapped people, and early tier.

Prefer a smaller sourced list with evidence over a larger generic list.

## Search Queries

Use Sales Navigator through the cofounder's logged-in session, plus search and browser research. Start narrow.

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

Directory and authority lookup queries:

- `site:safer.fmcsa.dot.gov "[Company]" freight broker`
- `[Company] MC number freight broker`
- `[Company] DOT number broker authority`
- `DAT Directory freight broker [region]`
- `Truckstop broker directory [region]`
- `carrier onboarding [Company] freight broker`

Signal-enrichment queries:

- `site:company.com "[Company]" "POD"`
- `site:company.com "[Company]" "carrier invoice"`
- `site:company.com "[Company]" "billing"`
- `site:company.com "[Company]" "carrier payables"`
- `site:company.com "[Company]" "lumper"`
- `site:company.com "[Company]" "accessorial"`
- `site:company.com "[Co