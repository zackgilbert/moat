# Einar Vollset: Offense ("How to Unfuck Your SaaS")

Source: Einar Vollset (Discretion Capital, TinySeed), MicroConf Europe 2026, given a couple of hours after Rob's defense talk. Subtitle: "Or, the greatest opportunity this century." The talk video and slides are at https://microconf.com/moats, with the Field Guide, which covers the same offense moves in short form.

These are summary notes with short attributed quotes, written for applying the framework in an audit. The framework and quoted material belong to Einar Vollset and Rob Walling.

## Contents

1. The setup
2. The three options
3. Labor budgets and "sell the outcome"
4. Why features alone are no moat
5. The learning loop and what makes it ideal
6. The ladder (collections example)
7. The five tests for a compounding worker
8. Spoken points not on the slides
9. How to apply this in an audit

## 1. The setup

- Rob's message recapped: everyone gets AI; supply goes up for most of you; demand changes (down for many, up for some); some moats are dry.
- "If the only moat you have is 'it took a long time to build this software,' then you might be slightly worried. Or panicked?"
- "May you live in interesting times" cuts both ways. Disruption and risk is what an upstart should want: in stable systems the gains stay with the incumbents, who have the most resources. Risk is the opening for small, not-well-funded companies.

## 2. The three options

1. **Move faster with AI.** Table stakes; everyone has to. Mature SaaS businesses report shipping at least about 3x faster than before AI. If your moats are strong ("I have six of ten, I'm amazing"), this may be enough by itself.
2. **Charge the agents.** For some products it will be obvious that people want to use them through agents. Work out how to make access easy for agents and how to charge them. Einar admits he does not know how many businesses this fits. The Field Guide version: offer an MCP server, control access, charge for it, and test whether an agent picks you when asked to solve your problem without being told your name.
3. **Move into labor markets.** The biggest opportunity for most founders (the Field Guide says right for about 80%).

## 3. Labor budgets and "sell the outcome"

- Labor budgets are far larger than software budgets; most businesses spend much more on salaries than on software.
- SaaS always worked this way: in MicroStrategy's early days the competitor was spreadsheets or pencil and paper, and the pitch was getting done in half a day what took two people three days. This is the supercharged version.
- If your SaaS is "a business owner gives my tool to an employee they pay a salary, who clicks it to get an outcome," then "somebody is going to go to your customer and sell the outcome without the employee having to do the clicking. And as far as I'm concerned, that might as well be you. If you don't do it, someone will. Guarantee it."
- On the guilt ("aren't people losing jobs?"): "Well, it was ever thus."
- Incumbent advantage: it is "far from obvious" that a fresh Silicon Valley startup with a $10M token budget, zero customer experience and zero relationships is better placed than an established SaaS that knows the industry and whose customers know it. Field Guide: 40 to 50% of recent YC launches are agentic SaaS, but they lack your customers, industry knowledge and trust.
- Field Guide's 10x question: "I'm charging $75/month. What would I have to do for the same customer to happily pay me $750/month?"
- Einar gives no pricing model for the worker. Do not invent one on his behalf; surface pricing as a founder decision.

## 4. Why features alone are no moat

- The classic product loop: observe customers, see what they need, use founder judgment to choose what to build, write the code, ship to everyone, and one lesson helps many. Colin's version: identify need, ship something useful, get feedback, repeat.
- AI makes only the "write the code" step faster. Everything else stays the same, and every competitor and in-house team gets the same speed-up.
- You might spend three or four months finding the best solution from deep industry knowledge, craft it, ship it, "and then some dude with Claude says, 'Hey, use my credentials to log in, screenshot that stuff, and replicate it for my product,' and they have it in six hours." This is why Einar agrees with Rob that strong opinions in a product are not a moat.
- So: keep shipping (table stakes), but use the extra code capacity to steer toward the moats that last in your space. And realize even that may not be enough, which is where the learning loop comes in.
- His capability-space picture: one blob is what current LLMs (or a startup with Claude) can do, another is what your SaaS does. The angst is how fast the first swallows the second. That was always the problem (competitors out-featuring you); AI just speeds it up.

## 5. The learning loop and what makes it ideal

The loop: the product acts (does the work), the world responds (a real customer outcome), the outcome is observed (success or failure becomes data), the next action improves, behavior changes automatically. It does not have to cover the whole product; for most companies some parts fit and some don't.

The ideal learning loop:

- **Does not leak to the outside world.** The learning stays with your company; it is not pushed to an external party, and customers cannot export it and get the value for themselves.
- **Requires world-clock actions and observations.** Lessons come only from real people doing things in the real world. It cannot be simulated or fast-forwarded by a competitor ("not fast-forwardable").
- **Improves across customers.** A new customer gets a materially better outcome because of what was learned from existing ones. A competitor facing your 1,000 customers over five years has to live through those experiences to catch up. Einar says not everyone can reach this one.

This is why becoming the worker matters: the worker generates the outcomes the loop needs. The Field Guide calls moat 7 something you get "almost automatically" when you become the worker.

## 6. The ladder (collections example)

| Stage | Name | Collections example | Who does the work |
| --- | --- | --- | --- |
| 1 | SaaS dashboard | Shows overdue invoices, statuses, what offer was made when | A person chases them |
| 2 | AI assistant | Drafts a reminder email | A person still decides and sends |
| 3 | AI worker | Chooses whom to contact, what offer to make, sends, follows up, handles replies, perhaps from hard-coded best practices | No human necessarily in the loop |
| 4 | Compounding AI worker | Payment outcomes improve the next action, across customers | The system improves itself |

"Stage 3 reaches the labor budget. Stage 4 creates the durable advantage." Stage 4 is "really the only way to automatically stay ahead of this AI capability, because it means someone can't just take the frontier model that's going to get better every year, plug it into the system, and catch up with you instantly."

Placing a product: be honest. Most products with an AI chat or insights feature are at stage 2. Stage 3 means the product takes the action without a human approving each one. A product can be at different stages for different jobs; name the stage per job.

## 7. The five tests for a compounding worker

1. **Does the product take the action?** It has to do it, not recommend it.
2. **Can it see what happened afterward?** The outcome must be observable inside your system.
3. **Does the outcome change what it does next?** Ideally automatically.
4. **Can the lesson improve results for other customers?** The ideal; not everything qualifies.
5. **Does the accumulated learning stay with you?** "That's the crucial part." Fails if the outcome data lives only in a platform, or the customer can export the learned value.

"Customer outcomes create experience competitors cannot fast-forward."

## 8. Spoken points not on the slides

- **The gazillion AI receptionists.** "I make an AI receptionist, then the next day, there's a gazillion AI receptionists. Where's the defensibility in that offense?" Moving into labor markets alone is copyable; the learning loop (stage 4) is the defense.
- **Six-hour copy.** Credentials plus screenshots plus Claude replicates a carefully crafted feature in about six hours.
- **3x shipping speed** at mature SaaS businesses since AI arrived.
- **Two-track SEO.** Referencing the AEO talks at the conference: "There's almost two parallel tracks for SEO now. There's how do humans find things and how do agents find things. And they may not be quite the same thing." Audit both: does your marketing site and public content get found by people, and do agents (ChatGPT, Claude, Perplexity, buyers' agents) find and pick you?
- **Disruption favors the challenger;** stability favors incumbents.
- **Not every part of a product needs the loop;** pick the parts where acting and observing outcomes is natural.
- **Six of ten moats and moving faster may be enough;** the worker is for everyone else, which is most people.

From episode 836 (same speaker, earlier): "Now is the opportunity. Go against the stream." AI-native SaaS faces a higher bar with acquirers, who scrutinize disruption risk and are slow to underwrite it.

## 9. How to apply this in an audit

- List the jobs the customer's staff do with the product (or around it, outside it). For each, place it on the ladder.
- Pick the one job where (a) the product can already take the action or nearly can, (b) the outcome is observable in your own data, and (c) the outcome is not visible to the platform you sit on. That is the worker's first job.
- Run the five tests on that job; mark pass, fail, or "needs building."
- Recommend logging outcomes (action, then result) now, before the worker ships, so world-clock data accumulates.
- For "charge the agents": check for an MCP server or public API, whether access is plan-gated, whether public pages are agent-readable, and run the unnamed-agent test.
- Pricing the worker is a founder decision, especially where outcome pricing collides with the business's own promises.
