---
name: moat
description: "Run an AI-era moat audit of the SaaS business behind the current repo, using Rob Walling's and Einar Vollset's MicroConf Europe 2026 framework (10 AI attacks, 8 moats, the dashboard to compounding AI worker ladder and its five tests, and the Moats in the Age of AI Field Guide scorecard). Gathers evidence from the codebase and docs, circles the likeliest attacks, scores all 8 moats 0 to 10 with file-level evidence, places the product on the worker ladder, and writes a report with a score chart, an ordered build list, a skip list, founder decisions and a positioning-drift check. Use when the user says 'moat audit', '/moat', 'what are our moats', 'how defensible are we against AI', 'will AI kill this business', 'AI moat review', 'SaaSpocalypse', 'Rob Walling moats', 'AI worker ladder', or asks how an acquirer would judge the product's AI risk, even without naming the framework. Read-only. For a single pricing or positioning question, use a pricing or positioning skill instead."
license: MIT
metadata:
  version: 1.1.0
---

# /moat: AI-era moat audit

Audit how defensible the business behind this repo is against AI, and what to build next, using the framework Rob Walling and Einar Vollset presented at MicroConf Europe 2026. The output is a report the founders will argue with, so every score needs evidence and every recommendation needs a reason.

This skill is an unofficial companion to their work. The framework is theirs; see the sources section of the report.

## Read first

Load these before scoring. They hold the depth; this file holds the procedure.

- `references/rob-walling-defense.md`: the 10 attacks, the old moats that dried up, the 8 moats with examples, evaluation questions and codebase signals.
- `references/einar-vollset-offense.md`: the three options, the ladder, the five tests, the learning-loop properties, and his spoken points.
- `references/field-guide.md`: the scorecard method, gut-check questions, bands, price-band playbooks, and scoring calibration.
- `references/example-audit.md`: a finished audit of a fictional business, for calibrating tone and how hard to score. Never import its conclusions.

## Step 0: Business context

Before any code, learn what the business is. Read whatever of these exists:

- `README`, `AGENTS.md`, `CLAUDE.md` or similar agent instructions.
- Project memory or agent notes, if your agent keeps any.
- Product specs, PRDs, roadmap or task files (often under `docs/`, `tasks/` or `specs/`).
- Positioning, marketing or pricing docs, and any landing-page copy in the repo.
- Plan or pricing config.

Note:

- What the product does, who buys it, who uses it daily, and any platform it sits on.
- Pricing model (per seat, per usage, flat tiers) and where most paying customers sit by price.
- Customer count and stage, if recorded anywhere. If not, say unknown.
- **Locked positioning promises** (taglines, "we never X", pricing promises). These constrain recommendations later.
- **Who the reader is.** Write as "we" when the user owns or runs the business: they said so, or the docs name them as a founder, owner, CEO or the person who decides what ships and what it costs. The word "founder" does not have to appear. Write in the third person ("Acme's moats"), including the chart title and section headings, when the user is an outside reviewer, a contractor, an investor or a buyer, or when you cannot tell. If you cannot tell and the user is available, ask in the same question as the business context below.

If the business is still unclear (no docs, a bare codebase), ask the user one short question before going on: what the product is and who pays for it. If the user is not available to answer, state your best reading of the business as an assumption at the top of the report and repeat it in one clause of the short answer.

### Product shape

The framework is built for a live, paid SaaS. Decide which shape this is, say so near the top of the report, and apply the matching adjustments throughout. If two shapes fit, name both and apply both sets of adjustments.

- **Live paid SaaS, self-serve:** the default; no adjustments.
- **Live, sales-led or early** (customers sign up through demos, contracts or invoices; billing may live outside the product; a handful of accounts or an unknown count): score from what the code and docs show, not from the plan config, which in these apps is often template code nobody uses. Say the customer count is unknown if it is. Moats 6 and 7 rest on so few accounts that they score low by definition; say that once. Weight attack 5 (agencies and consultants building custom versions) and the sales-led price band.
- **Pre-launch or dormant** (no prices, no customers, or no commits in many months): score what exists today, not what the plans promise, and put the potential in each moat's gap. Moats 1, 6 and 7 are near zero by definition without customers; say that once instead of arguing it eight times. Lead the build list with whatever must be true before anyone pays.
- **Open source or self-hosted:** score the project as it stands, and frame the build list around a paid offering it could have (hosting, support, a managed agent). The project is itself attack 3 for paid rivals. Test 4 of the five tests fails structurally unless outcomes flow back to a hosted service; say so rather than scoring it as a gap.
- **No price at all:** no price band applies. Name the nearest band, label it as an assumption, and ask the 10x question against the price of the nearest paid substitute.

Name the decision section for whoever decides: "Decisions for the founders", or "for the maintainers" on a community project.

## Step 1: Gather evidence

Run the seven evidence passes below. **If your agent can run parallel subagents** (for example Claude Code's Explore agent), launch one per pass in a single message so they run at the same time. **Otherwise**, do the passes in sequence yourself, reading excerpts rather than whole files.

Each pass names the moats it serves, collects concrete evidence (file paths, counts of jobs, tables and integrations, dates), looks for counter-evidence and gaps too, and reports in about 400 words. If a pass finds nothing relevant, that is a finding; record it. Adapt each pass's examples to the product; the lists below are prompts, not a checklist.

For a small repo (a few dozen source files), merge the passes into two or three; seven separate passes is overkill there.

If a pass turns up a serious security or data-handling problem, record it. It goes in the report as a precondition (Step 5) because it undercuts moats 1 and 4 directly. Serious means a stranger or another customer could, today, read or change data that is not theirs, or move money: one account's data visible from another, an admin area or API with no login, an incoming webhook that acts without checking its signature, live secrets or real customer data committed to the repo (history included). Development-only keys, missing hardening and dependency advisories are not preconditions; mention them in one line under "Skip for now" or leave them out. Cite the file path only; never copy a secret or a customer's data into the report.

1. **Pricing and plans** (attacks 8, 9; price band): plan config, tier names and prices, per seat vs usage vs flat, limits, what is plan-gated. Which tier most customers are on, if any data or docs say.
2. **Integrations and operations** (moat 8, attack 4): sync code, background jobs touching third parties (count them), retry and self-heal logic, rate limits, token refresh, documented API quirks, incident runbooks. Which platform or vendor the product depends on and what that platform already ships.
3. **Data ownership and actions** (moats 2, 3): tables and state that exist only in this product vs data that lives in a platform it syncs from; outbound webhooks or APIs other systems consume; every action taken on the customer's behalf (writes to their systems, emails or SMS sent, money moved, refunds). Where a human still does the last step.
4. **Correctness and trust** (moat 4): reconciliation, idempotency, double-count or double-charge guards, audit logs, correctness tests on money and counts. Counter-evidence: open or recent issues where customers caught wrong numbers, manual repair scripts.
5. **Approvals and network** (moats 5, 6): certifications, compliance docs, security questionnaires, marketplace or app-store listings, special platform permissions, carrier or regulatory registration. Multi-user features: invited members, end users who are not the buyer, groups, shared spaces. Typical users per account.
6. **Learning and partners** (moats 7, 1): outcome logging (action, then result), anything that learns across accounts, AI features and what they do (assist vs act). Partner, referral, affiliate or reseller programs: do payouts exist, is attribution stored, is there a multi-client view for agencies.
7. **Agents and in-flight work** (Einar's "charge the agents"; drift): MCP server or public API and whether it is plan-gated; agent-readable public pages (structured data, `llms.txt`); open issues, PRs, roadmap docs or task boards for work already under way, so the build list does not propose what is already being built. Use the git log and any issue tracker the repo or your tools can read. If you cannot reach the tracker, say so in the report and treat the in-flight list as incomplete.

Spot-check yourself only the few claims you will quote as headline evidence. If the evidence contradicts the docs, that is drift (Step 6), not an error to smooth over.

## Step 2: Circle the attacks

From the 10 attacks, circle the 2 or 3 most likely to hit in the next 12 to 24 months. For each, one or two sentences: why it is likely for this business specifically, with evidence. Then a short "where we're safe" list covering the remaining attacks, grouped where the reason is shared, each with its reason.

Weight attack 4 (platform) heavily for any extension, add-on or marketplace app; attack 5 (agencies) when buyers already work through designers or consultants; attacks 8 and 9 when pricing is per seat or the main user is a role AI is replacing; attack 6 when the core job is generating text, images or analysis. When the platform the product depends on is also the model vendor (a wrapper around one AI provider's API), attacks 4 and 6 are the same threat; treat them as one. For a standalone app, attack 4 means a vendor whose product the customer already uses for the same job and who could ship this product's core feature (accounting software adding the workflow, a CRM adding the scheduler). Payment, email and hosting vendors the app merely calls (Stripe, Postmark, AWS) are dependencies, not attack 4; mention them under moat 8 if keeping them working is hard. Direct competitors belong under attack 2.

You may name likely competitors or open-source rivals from general knowledge for attacks 2 and 3; label them as unchecked, since the audit makes no web searches.

Name the price band from the Field Guide and give its advice in a sentence (see Product shape when there is no price).

## Step 3: Score the 8 moats

Score each 0 to 10 using the calibration in `references/field-guide.md`. For each moat record:

- **What we have:** concrete evidence (paths, counts, dates, named programs).
- **The gap:** what a competitor could route around, or why customers don't feel it yet.
- Test the score against the moat's gut-check question.

Score honestly and conservatively. A program that exists on paper but has never paid out, an approval every competitor also holds, or a strength customers cannot see should score low to middling. A 9 or 10 is almost never right for a small SaaS. Say in the report that scores are a rough first read meant to be argued with.

Then read off the Field Guide band (strong, middle, weak) and say which moat is closest to becoming strong. The guide's bands are qualitative; if you use the numeric working rule from `references/field-guide.md`, label it as the skill's rule, not the guide's.

## Step 4: Place the product on Einar's ladder

- List the jobs the customer's staff do in or around the product. Place each on the ladder: 1 dashboard, 2 AI assistant, 3 AI worker, 4 compounding AI worker. An AI chat or insights feature is stage 2, not 3. Place a job by what reaches the customer: automation whose output nobody receives or acts on is not yet a worker.
- Pick **one job** for the worker to take first: the product can take the action (or nearly), the outcome is observable in the product's own data, and any platform or vendor it sits on does not see that outcome. A payment or email vendor seeing a fragment (that a charge cleared, that an email opened) does not fail the third criterion; it fails when another product could rebuild the whole outcome from what it sees. If no job meets all three, pick the closest, name the criterion it fails, and make fixing that part of the build item.
- Run the five tests on that job: pass, fail, or needs building, with a one-line reason each.
- Describe stage 3 and stage 4 for that job concretely.
- If test 2 or 3 fails, recommend logging outcomes now so real-world data accumulates before the worker ships.
- Ask the 10x question with this business's real price ("charging $X/month, what would make them happily pay $10X?"). If the price is unknown, use the most common tier and say so.

## Step 5: Build list, skip list, decisions

**Preconditions (only if Step 1 found any).** Serious security or data-handling problems come first, in a short list above the build list, each with its file path. Do not bury them as a build item.

**What to build, in order (3 to 6 items).** Each item gets a bold title naming the moat numbers it strengthens and the attacks it answers, then 2 to 4 bullets: what to do, what already exists or is in flight, and why it moves the score. Prefer items that turn a threat into a moat (an agency threat into a partner channel; for an add-on, a platform threat into a revenue line the platform wants to keep). Usually include the worker's first job and "welcome the agents" (MCP or API access, the unnamed-agent test, agent-readable public pages, two-track SEO).

**Skip for now.** Moats or projects that are real but wrong for this stage and team size, each with the reason (too expensive for the team, too few customers for the data to be credible, and so on).

**Decisions for the founders.** Things a founder must decide, framed as a choice with the tradeoff. Always include how to price the worker. Flag every conflict between a recommendation and the business's locked positioning (for example outcome pricing against a "never a per-transaction fee" promise, or a platform revenue share against steering customers to sign up direct) as a decision. Do not resolve those conflicts yourself; lay out the options.

## Step 6: Positioning drift

If the business has positioning, marketing, pricing or spec docs (a README's feature list counts), list every place they disagree with the live product or recent decisions you found in Steps 1 to 5 (recent commits, issues, notes). One table: topic, what the doc says, what is true now, where it shows (file path, issue, commit or date). If there is no drift or no such docs, say so in one line. Do not edit those docs yourself.

## Step 7: Write the report

**Where it goes.** Use the first of these that applies:

1. The user named a place: write it there.
2. The user asked for nothing in the repo to change, the repo is not theirs, or it has uncommitted work you should not mix with: write `moat-audit-YYYY-MM-DD.md` to your scratch or temp directory (or the user's home directory if you have none) and give the full path.
3. Otherwise: write `docs/moat-audit-YYYY-MM-DD.md` in the repo, using today's date. Leave it uncommitted and say so, so the user decides whether it belongs in the repo.

Do not commit it unless asked.

**Optional:** if your environment has a first-party docs connector (for example Claude Docs) and the user wants a shared doc, make the audit a doc instead and follow that connector's own instructions. Use the same sections, and put the scores in its chart format.

The score chart is a horizontal text bar chart in a code block, sorted high to low, one `#` per point, with a title line that states the finding:

```
One strong moat: hard to keep running scores 7 of 10

8. Hard to keep running            7  #######
3. Allowed to act                  5  #####
...
```

Title the report "<Business> Moats in the Age of AI" with the date under it. Sections, in this order:

1. **Short answer:** 2 or 3 sentences: how many strong, partial and near-zero moats, the biggest risks, and the band with the moat closest to strong. If you placed the band with the skill's numeric rule, say "(using this skill's working rule, not the guide's)" once, here.
2. **The framework:** a compact recap for readers who have not seen the talks, modeled on the one in `references/example-audit.md`: the 10 attacks (supply 1 to 6, demand 7 to 10), the dried-up moats, the 8 moats with gut checks (table), Einar's three options, the ladder and five tests, and his two spoken points (the many-AI-receptionists problem; two-track SEO). Keep it short.
3. **Where AI hits us:** circled attacks, where we're safe, price-band advice.
4. **Our moats today:** the chart, then a table of moat, score, what we have, the gap, sorted by score.
5. **What to build, in order:** preconditions first if any, then the build list, with the ladder placement and five-test results inside the worker item.
6. **Skip for now.**
7. **Decisions for the founders** (or maintainers; as a checklist).
8. **Positioning drift** (if any).
9. **Sources:** the links in `references/field-guide.md` (Field Guide, Rob's and Einar's talks, Startups for the Rest of Us 836 and 855), plus the files in this repo the evidence came from.

Headings above use "we" and "our"; switch them to the business's name when writing in the third person (Step 0).

End your chat reply with one line and the report path or link. Findings live in the report, not the chat.

## House style for the report

- No em dashes. Use commas, colons, semicolons, parentheses or separate sentences.
- No pipes as text separators (markdown table syntax is fine).
- No "It's not X, it's Y", no "X isn't just Y", no punchline reversals, no rhetorical-question hooks.
- Plain words and short sentences. Simple bullets. Name things concretely (file paths, counts, dates) instead of adjectives.
- Quote Rob and Einar briefly and attribute them; never paste transcripts or the Field Guide.
- Never invent dates, customer counts or revenue. If a number is not in the evidence, say it is unknown.

## Guardrails

- Read-only. The audit changes no code, opens no issues or PRs, and writes no production data. The only file it writes is the report.
- No network calls beyond what your agent already does. Do not run the app, call its APIs or query production.
- Do not propose building something that the in-flight work (Step 1, pass 7) shows is already under way; reference it instead.
- A score is a judgment. When evidence is thin, give the lower score and say what evidence would raise it.
