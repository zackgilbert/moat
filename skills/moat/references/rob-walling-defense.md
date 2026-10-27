# Rob Walling: Defense (10 attacks, 8 moats)

Source: Rob Walling, MicroConf Europe 2026 (Iceland) talk, co-written with Einar Vollset after Einar spent about a month working through 89 papers from think tanks, PE groups and Gartner. The talk video, slides and the Field Guide PDF are at https://microconf.com/moats. See also Startups for the Rest of Us episodes 836 and 855.

These are summary notes with short attributed quotes, written for applying the framework in an audit. The framework, examples and quoted material belong to Rob Walling and Einar Vollset. For the full argument, watch the talk or listen to the episodes.

## Contents

1. The headline call
2. Why buyers care (M&A context)
3. The 10 attacks
4. The old moats that dried up
5. The 8 moats that still hold
6. Rob's "how to move toward each moat" list
7. The earlier five-moat version (episode 836)

## 1. The headline call

- "Everyone gets AI": you, your customers, your competitors, agencies, open-source maintainers and your platform.
- Rob's estimate: 10 to 20% of all SaaS companies will decline or go to zero because of AI. Not a SaaSpocalypse, but not "back to normal" either.
- No single attack wipes a business out. Each one takes a few points. Ten of them together is what hurts.
- "You're probably lucky, probably doing pretty well if you have one or two of these" moats.
- Every moat is a spectrum (0 to 10, or 0 to 100), not on or off. Salesforce or Shopify might sit at 90 on trust; the question is how to go from 10 to 20 or 30.
- Thought experiment to apply to every moat: assume the cost of writing code approaches zero, the way disk space and bandwidth did. What is still protecting you?

## 2. Why buyers care (M&A context)

- Private equity does about 70% of acquisitions of bootstrapped-size SaaS and follows public markets.
- Buyers are not scared about the present; they cannot tell whether you will be around in 1, 3 or 5 years. Moats are what lets them pay the old multiples.
- Public-market example (August 2026): HubSpot beat earnings and did a $1B buyback, and the stock fell 21%. Atlassian reported similar results with MCP server usage roughly doubling, and rose 35%. Rob's read: Jira has several of the moats; HubSpot's inbound-marketing engine is badly exposed to AI.
- Episode 836: some PE firms now refuse to look at a deal without at least one AI moat. "That company is not buying your company no matter what" (Einar). Even if 30 to 50% of buyers do this, multiples soften.
- This matters even if you never sell: the money flowing into SaaS M&A is what holds the ecosystem's valuations up.

## 3. The 10 attacks

Basic economics: supply shocks commoditize you (one scheduling-link app becomes 99), demand shocks shrink who will pay you.

### Supply shocks: more alternatives to you (1 to 6)

1. **Your customer builds it.** "They don't need your 50 features. They only need the three that they use." The hair-stylist or lawn-care founder who says "my customers will never vibe code this" has covered only this one attack.
   - Codebase signal: a long feature list with low per-account usage; a narrow core job.
2. **A competitor reaches parity.** Eight of 46 AI notetakers (Otter 2016 through Granola 2024) are now basically the same product. "I could start one today and probably have pretty close feature parity in a few months." Features used to buy you a lot of time; they buy much less now.
   - Signal: the core value is visible UI that can be copied from screenshots.
3. **Open source gets good enough.** OSS moves faster with AI too, and non-technical buyers can now deploy it by asking Claude to run it. No longer "free like a puppy."
   - Signal: an active OSS project in the category.
4. **A platform ships your feature.** The system of record you integrate with can build your feature in a week or a month, already has the customers, and "you've basically given them a spec through your UI." Example: CRMs (Salesforce, HubSpot, Close) building every ancillary add-on.
   - Signal: the product is an add-on, extension or marketplace app on someone else's platform.
5. **Custom software at SaaS-ish prices.** Agencies that charged $30K to $50K for a three-month build can now do it in a third to a fifth of the time, and they want recurring revenue. Against your $99/month one-size-fits-all: completely custom, supported, at $299 to $999/month. Rob: if he were in his early 20s he'd consider this business model.
   - Signal: the product's buyers already work with designers, agencies or consultants.
6. **The model absorbs your product.** Apps that generated ad copy, headlines and images went away once the foundation models did it out of the box.
   - Signal: the core job is generating text, images or analysis with no state, no action and no integration.

### Demand shocks: less need for you (7 to 10)

7. **Your customer stops existing.** Translation and transcription volume went through the roof, while the agencies doing it are heading to zero (Rob: 80 to 90% of them). Copywriting too. "While the activity grows, your customers' ability to pay you plummets." Pure involuntary churn, no recovery.
8. **Your seats go away.** Support teams shrink from about eight humans to one or two supervising AI agents. Per-seat revenue can drop 70 to 80% while the customer does fine. Zendesk and Help Scout are moving toward outcome-based pricing to get around this.
   - Signal: per-seat pricing in plan config.
9. **Your user's job goes away.** (The Field Guide numbers it 9; in Rob's spoken order it was 10.) Receptionist or call-center software at $50/month: someone will sell your software plus a 90%-accurate autonomous agent for $300 to $500/month and the customer lets the human go. "If you don't agentify your software, build some type of agent on top of it, I think you're going to zero in the next couple years."
10. **The step you manage stops mattering.** Take-home coding test software: nobody gives take-homes now, because AI does them (Rob and Derrick Reimer switched to pair programming). Ask whether the product manages a step that existed only because humans needed to coordinate.

Attacks 8 and 9 can become opportunities: if AI is replacing your users, build that AI and sell it yourself (see Einar's offense file).

## 4. The old moats that dried up

Rob's nine classic moats from *SaaS Playbook*, and what AI did to each:

- **Unique features / lots of code:** AI does not bring build cost to zero, but dramatically lowers it; products converge as everyone copies whoever is best at product and UX.
- **Owned traffic channels / SEO:** 50/50. Good SEO is still fine, but AI is making marketing muddy.
- **Clever code, complex algorithms:** gone (AI is solving unsolved math proofs).
- **UX familiarity:** if usage goes agentic, UX does not matter at all; agents need no retraining.
- **Integrations:** "Isn't the API really just the spec to hand to my bot?" A well-documented API now takes a day or two to integrate.
- **High switching costs / hard to export:** an AI pointed at an app can pull all the data out even with no export.

Survivors carried forward: system of record, coordination between people, and brand (plus more). Rob then added five more to reach eight.

## 5. The 8 moats that still hold

For each: what it means, Rob's examples, his evaluation question, and how to spot it in a codebase.

### Moat 1. Buyers know and trust you

- Strong brand, you know your buyers and how they buy, partners who built their businesses around recommending you, and a champion inside each account who will fight for you.
- Strongest form: a competitor with better, vibe-coded software still has to build all of this.
- Examples: **QuickBooks** ("QuickBooks is terrible software. I hate using it, but I don't care because my accountant uses it and he likes it." A better product does not get you into that conversation; Xero is 10 to 12 years in). **Shopify**: thousands of implementing agencies; when a merchant hires one, "the platform's already decided."
- Question: who has built their business or career around recommending or defending you?
- Codebase signals: partner/affiliate/referral models and payouts actually made, attribution stored, agency or multi-client views, certification programs for implementers. Absence of payouts or attribution is a gap even if a program exists on paper.

### Moat 2. You're the system of record

- The source of truth for data; daily operations are built around you; people log in every day; if you go down, the business barely works. Balances, approvals, statuses, workflows, roles and rules live in you; other systems read from you or push data in, and it does not come out.
- Examples: **Jira** (you can export tickets in an afternoon, but not the history, audit trail, integrations and every team moving at once; "it just has gravity"). **Gymdesk** (TinySeed): started as one part of the gym, spread into billing and key-fob door hardware; very few gyms switch.
- Question: if a customer wants to leave, what can't they export, what breaks downstream, and what would they have to rebuild? (Rob's checklist phrasing: do you hold the definitive view of the work, or just a view of it?)
- Codebase signals: tables for state that exists nowhere else (balances, approvals, credits, statuses); outbound webhooks and integrations other systems depend on. Counter-signal: the money and orders live in a platform you sync from.

### Moat 3. You're allowed to act

- A tool that recommends a payment versus one that makes it. Handing over a spreadsheet of PayPal emails and amounts makes you a report. Moving the money makes you plumbing. "Advisors are easy to replace. Plumbing isn't."
- Examples: **Stripe Connect** (moves money, nobody switches off). **ReMB** (TinySeed): reimburses job candidates' travel via Venmo, PayPal, Cash App, soup to nuts; "you don't have to be Stripe to have the authority to pay." **Churnkey**: many tools tell you who will churn; Churnkey is allowed into the cancellation flow to make the offer, in front of your customers, unchecked.
- Question: can your software act, or can it only advise?
- Codebase signals: OAuth write scopes, background jobs that write to customer systems, sending email or SMS on the customer's behalf, payment movement, refunds. Note where a human still does the last step.

### Moat 4. They don't check your work

- You act, and customers trust you so much they skip reviewing it. Not just "we're trustworthy": the permission was earned by being right for years.
- Examples: **Gusto** (Rob has used it since about 2013 and has never checked anything but his own W-2; he could go to jail if they got it wrong). **Avalara** (sales tax; nobody checks the number). Rob struggled to find a small-company example.
- Question: do customers trust your output enough that they don't check it?
- Codebase signals: reconciliation jobs, idempotency, oversell and double-charge guards, audit logs, correctness tests on money and counts. Counter-signals: open bugs where customers caught wrong numbers, manual repair recipes, support threads asking "is this right?"

### Moat 5. Someone official already said yes

- Regulations, licenses, accreditations, certifications: a third-party body where you, the vendor, had to qualify. "Serving regulated customers isn't the same as holding an approval yourself."
- Examples: SOC 2, ISO 27001, HIPAA (compliance is brutal enough that Vanta became a billion-dollar company). A TinySeed company whose courses count toward ABA credentials needs board approval, so a vibe-coded copy can't just appear. **US SMS**: carrier registration and consent laws make texting "shockingly difficult"; the software is not hard, the permission is. **SignWell** (Field Guide): signatures that hold up when a contract is disputed.
- Rob notes the AI labs themselves are trying to regulate their industry to pull the ladder up.
- Question: what approvals or legal complexity have you navigated that a newcomer would have to earn or wait for?
- Codebase signals: compliance docs, security questionnaires, marketplace or app-store approvals, special permissions or scopes granted by a platform, carrier registration. Weigh exclusivity: an approval every competitor also holds is a small moat.

### Moat 6. Everyone's already in it

- Network effect. One person can switch in an afternoon; a whole team, company or community almost never moves.
- Examples: **Slack** (competitors exist; nobody can name them). **CommitSwimming** (TinySeed): swim-team management where every non-technical family is signed up for meet notifications, so the whole league has to agree to move. Field Guide: school apps with 1,000 students and 4,000 parents.
- Question: would a competitor have to move everyone at once? How many people would have to move together for one customer to leave?
- Codebase signals: invited members, end-user accounts that are not the buyer, group or league entities, shared calendars, notifications to many people per account. Counter-signal: most accounts have one user.

### Moat 7. Every customer makes you smarter (most durable)

- A learning loop: situation arises, human or software acts, you see the result, you correct. Having lots of data is not enough; you have to use it to predict across all customers.
- Examples: **Stripe Radar** (fraud patterns from every merchant protect all others; "no single merchant could ever build it," and if you leave you lose it). **Ramp** (one customer recategorizing a Verizon line item helps everyone). **Churnkey** (every cancellation should improve the engine; Rob planned to tell them to build it). **Mailchimp's Omnivore** spam engine (2009, ML before the AI wave).
- Three gates, all required: (1) every customer makes it better for every other, not siloed; (2) customers can take their data but not what you learned from it; (3) you keep learning, or it stops mattering.
- Field Guide: learning must come from real-world events on a real-world clock. If it can be recreated with synthetic data, it is not a moat. It is the one moat Rob and Einar are confident stays ahead of improving LLMs.
- Question: does what happens to one customer make your product smarter for the rest?
- Codebase signals: outcome logging (action taken, then what happened), cross-account models or rules, recommendation systems trained on aggregate data. Usually the weakest moat in a young SaaS; say so.

### Moat 8. It's hard to keep running

- Easy to build, hard to operate. Ongoing costs only make sense spread across many customers. "That thing that you hate and resent can actually be a moat."
- Examples: **ScrapingBee**: Pieter Levels vibe codes and self-hosts almost everything, tried for weeks to replace it, and gave up and paid $99/month; proxies, IP cycling, anti-bot DevOps (they later had an eight-figure cash exit, partly because they were tired of running it). **Cloudflare**. **Drip**: anyone can send an email, but Drip had multiple full-time people just fighting spam; a vibe-coded ESP on your own SES account does not survive.
- Question: is it hard to build, or hard to keep running? What do you maintain that you resent maintaining? (Field Guide: if a customer vibe coded you perfectly, what would go wrong in 6 months?)
- Codebase signals: many sync jobs, retry and self-heal logic, documented third-party API quirks, rate-limit handling, token refresh recovery, deliverability work, incident runbooks. Counter-signal: customers cannot see this work, so it does not yet feel like a reason to stay.

## 6. Rob's "how to move toward each moat" list

From his closing slide, in moat order:

1. Vertical tool: build an ecosystem; become the vendor the industry recommends.
2. Point solution: become a system of record.
3. Reporting tool: figure out how to act (move the money, make the offer), not just recommend.
4. Calculating something: become the output nobody double-checks.
5. Regulated industry: become the approved provider.
6. Single-seat tool: build the network effect where everyone coordinates.
7. Collecting data: build a learning loop.
8. Babysitting infrastructure you hate: make it the burden nobody else will carry.

## 7. The earlier five-moat version (episode 836)

Startups for the Rest of Us 836, "The 5 A.I. Moats Acquirers Value Most" (recorded May 2026), is an earlier cut of the same thinking, from the acquirer side. Useful as cross-checks:

- **Hardware-software coupling:** replacing it has physical consequences (grocery scales, EV charger software, warehouse printers). TinySeed once saw hardware as a drawback; now a moat. Maps loosely to moats 2 and 8.
- **Marketplace scale / two-sided network effects:** "hard to do, but hard to undo if you succeed at it" (Einar). Rob: bootstrapping one is "like eating glass" unless you already own one side. Maps to moat 6.
- **Communication graph and relationship embed:** where people coordinate messages, approvals and context (Slack: "please give me some more of that sweet, sweet Slack"). Maps to moats 2 and 6.
- **Proprietary data with closed feedback loops:** exclusive data that keeps refreshing (BuiltWith, Fiscal.ai, DealForma); a one-time snapshot is worth little. Maps to moat 7.
- **Operational embed and switching costs:** woven into workflows and routines; technical founders overestimate how much customers want to save on software, and a cheaper rival for a $10K/year system often loses because switching is risky. Maps to moat 2.
- M&A thresholds from the episode: in 2021 about $1M ARR with NRR over 100% sold well; now closer to $2M ARR, NRR over 100%, and attention to GRR. Multiples are set by auction (recent range roughly 4x to 15x).
