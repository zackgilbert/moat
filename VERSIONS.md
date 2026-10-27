# Versions

Current version of each skill. Agents can compare this against a local copy to check for updates.

| Skill | Version | Last updated |
|-------|---------|--------------|
| moat | 1.1.1 | 2026-10-27 |

## Changelog

### 1.1.1 (2026-10-27)

Fixes from a second test run, on an annual-priced app with slow outcomes:

- A committer or security contact with no stated business role means third person, with the reading stated up top.
- "Dormant" means no commits in six months or more.
- Annual prices convert to monthly for the price band; the sales-led shape defers to the Field Guide's band rule.
- The worker's first job needs an outcome that shows within weeks, or the earliest reliable signal of a slow one.
- Webhook preconditions only when a forgery moves money, changes access or records something binding.
- Third-person decision heading, standalone apps with no platform, and marketing that contradicts the legal pages.

### 1.1.0 (2026-10-27)

Fixes from a test run on a live, sales-led Rails app:

- New product shape for live, sales-led or early apps (demos, invoices, off-platform billing, unknown customer count). Two shapes can apply at once.
- "We" versus third person now follows who owns or runs the business, not whether the docs use the word "founder".
- Price band is chosen by how customers buy first, then by price.
- Attack 4 is defined for standalone apps: payment, email and hosting vendors are dependencies, not the platform threat.
- A bar for which security problems count as preconditions, and a rule never to copy secrets or customer data into the report.
- Clear order for where the report is written, including read-only runs.

### 1.0.0 (2026-10-26)

- First public version: evidence passes, circled attacks, 8 moat scores, the worker ladder and five tests, build and skip lists, founder decisions, positioning drift, markdown report with a text score chart.
- Worked example of a fictional business in `references/example-audit.md`.
