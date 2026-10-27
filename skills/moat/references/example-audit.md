# Worked example: Kettlebook (fictional)

Kettlebook is a made-up business. Every name, number and file path below is invented to show what a finished audit looks like. Use it to calibrate tone, depth and how hard to score. Never copy its conclusions into another business's audit.

Business context gathered in Step 0: Kettlebook is an online booking and reminders add-on for small physiotherapy, massage and chiropractic clinics. It installs as an app on Framewise, a (fictional) website builder with an app marketplace, and embeds a booking widget on the clinic's Framewise site. Two founders, no employees. About 150 paying clinics, per the founders' notes. Tiers: Solo $29/month (1 practitioner), Clinic $59/month (up to 5), Group $99/month (up to 15); most clinics are on Clinic. Locked positioning, from `docs/positioning.md`: "One flat price. Never a fee per booking."


# Kettlebook Moats in the Age of AI

2026-10-01

Scores are a rough first read meant to be argued with.

## Short answer

We have one strong moat: our SMS reminders run on a registered sender with carrier approval, and the reminder pipeline is hard to keep running. Three more moats are partly there, and four are close to zero. Our biggest AI risks are Framewise shipping its own booking block, and the AI receptionists clinics are already being pitched. Band: middle ("strengthen the moat you're closest to, on purpose"); the closest is being the clinic's system of record for the schedule and intake forms.

## The framework

Rob Walling and Einar Vollset presented this at MicroConf Europe 2026. Rob's view: 10 to 20% of SaaS companies will decline or go to zero because of AI, and no single attack does it; each takes a few points.

**Ten attacks.** Supply shocks, more alternatives to us: (1) the customer builds it, (2) a competitor reaches parity, (3) open source gets good enough, (4) a platform ships our feature, (5) agencies sell custom software at SaaS-ish prices, (6) the model absorbs the product. Demand shocks, less need for us: (7) the customer's industry shrinks, (8) seats go away, (9) the user's job goes away, (10) the step we manage stops mattering.

**Moats that dried up:** lots of code, a big feature set, integrations, switching costs and UX familiarity. AI copies, integrates and exports its way past all of them.

**Eight moats that still hold:**

| # | Moat | Gut check |
| --- | --- | --- |
| 1 | Buyers know and trust us | Who has built their business around recommending us? |
| 2 | System of record | If a clinic left tomorrow, what would break downstream? |
| 3 | Allowed to act | Does a human still do the last step? |
| 4 | Nobody checks our work | What would clinics never trust a homemade version to do? |
| 5 | Someone official said yes | What approvals would a competitor need first? |
| 6 | Everyone's already in it | How many people would have to move together? |
| 7 | Every customer makes us smarter | What do we know from real use that nobody could simulate? |
| 8 | Hard to keep running | If a clinic vibe coded us perfectly, what breaks in 6 months? |

**Einar's offense.** Three options: move faster with AI (table stakes), charge the agents (MCP or API access, priced), and move into labor markets by selling the outcome instead of the tool. The ladder runs from dashboard (1) to AI assistant (2) to AI worker (3) to compounding AI worker (4); stage 3 reaches the labor budget and stage 4 is the durable advantage. Five tests for a compounding worker: it takes the action, sees the outcome, changes what it does next, improves results for other customers, and keeps the learning with us. Two spoken points: when everyone can build an AI receptionist, the worker alone is copyable and only the learning loop defends it; and SEO now runs on two tracks, how people find us and how agents find us.

## Where AI hits us

Circled attacks:

- **4, a platform ships our feature.** Framewise already has a contact-form block and a payments block; a basic "book a time" block is one sprint for them, and our UI is their spec. Every clinic we serve is already their customer.
- **9, our user's job goes away.** The person who uses Kettlebook daily is the front-desk receptionist. Three clinics mention "AI phone receptionist" pitches in support threads (`support/exports/2026-08.csv`). An agent that answers the phone and books into any calendar makes our widget optional.
- **2, a competitor reaches parity.** The booking widget is visible UI that can be copied from screenshots (Einar's six-hour copy).

Where we're safe:

- **8 (seats):** pricing is tiered by practitioner, not by front-desk seat; a clinic that drops its receptionist keeps the same practitioners.
- **7 and 10:** hands-on therapy is not going away, and booking a physical slot with a real practitioner stays a real coordination step.
- **1 and 5:** clinic owners will not build software themselves; few use agencies beyond their Framewise site designer, who has not been building booking tools.
- **3:** open-source schedulers exist but need hosting and SMS registration; not a near-term threat for this buyer.
- **6:** a model cannot hold a shared calendar or send registered SMS on its own; it needs a system like ours underneath.

Price band: self-serve under $100/month. Invest in brand and trust now, keep self-serve as the entry point, and offer the worker as a premium tier with more hand-holding.

## Our moats today

```
One strong moat: hard to keep running scores 7 of 10

8. Hard to keep running            7  #######
5. Someone official said yes       5  #####
2. System of record                5  #####
3. Allowed to act                  4  ####
1. Buyers know and trust us        2  ##
4. Nobody checks our work          2  ##
6. Everyone's already in it        1  #
7. Every customer makes us smarter 1  #
```

| Moat | Score | What we have | The gap |
| --- | --- | --- | --- |
| 8. Hard to keep running | 7 | 14 background jobs touch third parties (`app/jobs/`); SMS delivery retries and carrier error handling in `app/services/sms/`; calendar sync with three providers including token refresh recovery; `docs/runbooks/` has 9 incident write-ups. | Clinics only feel it when a clone's reminders stop arriving. Nothing in the product shows them the work. |
| 5. Someone official said yes | 5 | Registered SMS sender and approved campaign (`docs/compliance/sms-registration.md`); Framewise marketplace approval; a signed data processing agreement template. | No health-data certification; any competitor can register SMS in a few weeks. |
| 2. System of record | 5 | Appointments, intake forms, practitioner availability and no-show history live only in Kettlebook (`db/schema.rb`: `appointments`, `intake_responses`, `availability_rules`). | Payments and the client list's billing details live in each clinic's payment processor. No other system reads from us; no outbound webhooks. |
| 3. Allowed to act | 4 | Sends SMS and email reminders on the clinic's behalf; writes to practitioners' external calendars. | Never takes deposits or no-show fees; a human at the front desk still rebooks every cancellation. |
| 1. Buyers know and trust us | 2 | A referral link in `app/models/referral.rb`; good reviews on the Framewise marketplace. | No payouts ever made; no Framewise designers recommend us by habit; no champion program. |
| 4. Nobody checks our work | 2 | Double-booking guard with a database constraint (`db/migrate/..._unique_practitioner_slot.rb`). | Open issue #212: reminders sent in the wrong time zone after a daylight-saving change. Clinics still confirm the next day by phone. |
| 6. Everyone's already in it | 1 | Patients book through the widget but have no account. | Most clinics have one or two staff logins; nobody else would have to move. |
| 7. Every customer makes us smarter | 1 | No-show history per clinic. | Nothing learns across clinics; outcomes are not logged against the reminder that was sent. |

How the scores were held down: the SMS registration scored 5, not higher, because any competitor can earn it; the referral program scored 2 because it has never paid out; the strongest moat scored 7 because clinics cannot see it.

## What to build, in order

1. **Become the worker on one job: filling cancelled slots (ladder; moats 3 and 7; answers attack 9).**
   - Today's ladder: calendar and no-show report are stage 1; the "suggest a reply" button for patient messages is stage 2. Nothing is at stage 3.
   - Proposed job: when a patient cancels, offer the slot to the waitlist and to patients overdue for a follow-up, by SMS, and book whoever accepts first. Stage 3 does this with fixed rules. Stage 4 learns across clinics which offers (time of day, notice period, message wording) fill which kinds of slots.
   - Five tests: 1 takes the action, needs building (we send SMS but do not book from a reply). 2 sees the outcome, pass (the booking lands in our own data). 3 outcome changes the next action, needs building. 4 helps other clinics, needs building. 5 learning stays with us, pass (Framewise never sees bookings or replies).
   - Start logging now: for every reminder and offer sent, record what was sent and what happened (booked, ignored, cancelled), so real-world data builds before the worker ships.
   - 10x question: at $59/month, what would a clinic happily pay $590/month for? Plausibly a front desk that keeps the calendar full without a receptionist.
2. **Make "nobody checks our work" true (moats 4 and 8).**
   - Fix #212 and add a daily reconciliation that confirms every reminder went out at the right local time.
   - Show each clinic a monthly line: "every reminder delivered on time, zero double bookings."
3. **Deepen the system of record (moat 2; answers attack 4).**
   - Add outbound webhooks and a clinic-facing export so their notes and payment tools read from us.
   - Treatment plans (a series of visits) are a natural next record that only we would hold.
4. **Welcome the agents (Einar's second option; answers attack 9).**
   - A small API or MCP server so a clinic's AI receptionist books through Kettlebook instead of replacing it. Gate it to Group.
   - Run the unnamed-agent test: ask an assistant "how do I take physio bookings on my Framewise site with text reminders?" and see whether it names us.
   - Make public booking pages agent-readable (structured data for services, practitioners and open times). Two-track SEO: humans find us in the Framewise marketplace; agents need to find us too.

## Skip for now

- **Health-data certification:** too heavy for two founders at 150 clinics; revisit if hospital groups start asking.
- **A patient app or accounts:** the network moat for clinics is weak, since patients book a few times a year. Not worth an app.
- **Cross-clinic benchmarks as a feature:** 150 clinics is too few to be credible. Log outcomes now; publish later.

## Decisions for the founders

- [ ] **How to price the worker.** The obvious outcome price (a fee per refilled slot) breaks the promise "Never a fee per booking." Options: a premium flat tier (fits the promise), a per-practitioner add-on, or rewording the promise. Raised as a decision, not resolved.
- [ ] **Stay on Framewise only, or add a second website builder.** A second platform halves attack 4's damage but doubles the operating load that moat 8 rests on.
- [ ] **Which job the worker takes first.** Filling cancellations is proposed; intake-form chasing and no-show follow-up are smaller starts.
- [ ] **Partner with AI receptionist vendors or compete with them.** Partnering means the API in build item 4; competing means building voice.

## Positioning drift

| Topic | What the doc says | What is true now | Where it shows |
| --- | --- | --- | --- |
| Calendar sync | "Syncs with every major calendar" (`docs/positioning.md`) | Three providers supported | `app/services/calendar/` |
| Group tier limit | "Unlimited practitioners" | Capped at 15 since August | `config/plans.yml`, commit of 2026-08-14 |
| Deposits | "Take deposits to cut no-shows" | Not built; issue #198 open | Issue tracker |

## Sources

- Rob Walling and Einar Vollset, MicroConf Europe 2026 talks.
- Moats in the Age of AI Field Guide: https://microconf.com/moats
- Startups for the Rest of Us episodes 836 and 855.
- Kettlebook files cited above.
