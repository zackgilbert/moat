# moat

An agent skill that audits how defensible your SaaS business is against AI, and tells you what to build next.

Point it at your product's repo and run `/moat`. It reads your code and docs, circles the AI attacks most likely to hit you, scores your eight moats from 0 to 10 with file-level evidence, places your product on the AI worker ladder, and writes a report with an ordered build list, a skip list, decisions for the founders, and a check for places where your positioning docs no longer match the product.

The framework comes from Rob Walling and Einar Vollset (see [Credit](#credit)). This skill is an unofficial companion that applies it to a codebase.

**This is not endorsed by or affiliated with Rob Walling, Einar Vollset, or MicroConf.** It is my own project. For the original material, go to [microconf.com/moats](https://microconf.com/moats).

## How this came about

I'm a co-founder of [Eventually](https://eventuallyticketing.com), an official Squarespace Extension for event ticketing. After Rob and Einar's talks at MicroConf Europe 2026, I wanted to know how our own business held up against AI. So I wrote this skill and ran its first audit on Eventually's codebase at [eventuallyticketing.com](https://eventuallyticketing.com).

That first audit turned into real work within the week. We started logging what happens after each action, so a future AI worker has outcomes to learn from. We added an alert for when a store's order webhooks go quiet. We published an `llms.txt` so AI agents can read what the product does. And we picked our first AI worker job: offering freed seats to the people on an event's waitlist, automatically.

I then ran the skill on two other apps, one of them sales-led, and fixed what those runs showed (see [VERSIONS.md](VERSIONS.md)). The worked example below is a made-up company, so no real business's private details live in this repo.

## What you get

A markdown report at `docs/moat-audit-YYYY-MM-DD.md` with these sections:

1. Short answer
2. The framework, recapped for readers who missed the talks
3. Where AI hits us: the 2 or 3 likeliest attacks, and where you're safe
4. Our moats today: a score chart and a table of evidence and gaps
5. What to build, in order, including your first AI worker job and how it does on the five tests
6. Skip for now
7. Decisions for the founders
8. Positioning drift
9. Sources

Here is an excerpt from the worked example in [`skills/moat/references/example-audit.md`](skills/moat/references/example-audit.md), an audit of Kettlebook, a made-up booking add-on for physio and massage clinics:

> We have one strong moat: our SMS reminders run on a registered sender with carrier approval, and the reminder pipeline is hard to keep running. Three more moats are partly there, and four are close to zero. Our biggest AI risks are Framewise shipping its own booking block, and the AI receptionists clinics are already being pitched.

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

Scores are a first read meant to be argued with. The skill is told to score conservatively and to cite a file, count or date for every claim.

## Install

### npx skills

Using [skills](https://github.com/vercel-labs/skills):

```bash
npx skills add zackgilbert/moat
```

### Claude Code plugin

```bash
/plugin install moat --marketplace zackgilbert/moat
```

On older Claude Code versions, add the marketplace first:

```bash
/plugin marketplace add zackgilbert/moat
/plugin install moat
```

### SkillKit

Using [SkillKit](https://github.com/rohitg00/skillkit), which installs into several agents (Claude Code, Cursor, Copilot and others):

```bash
npx skillkit install zackgilbert/moat
```

### By hand

Copy `skills/moat/` into your agent's skills folder (for example `.agents/skills/moat/` or `~/.claude/skills/moat/`).

## Usage

Open your agent in the repo for your product and run:

```
/moat
```

Or ask in plain words: "run a moat audit", "what are our moats", "how defensible are we against AI".

It works best when the repo has some business context: a README, positioning or pricing docs, plan config, or agent notes. If it cannot tell what the business is or who pays for it, it asks you one question first.

If your agent can run subagents in parallel (Claude Code's Explore agent, for example), the skill launches seven evidence passes at once. Otherwise it runs them one after another. A full audit takes a while either way; it reads a lot.

## What it reads and writes

- **Reads:** your repo's code, config, docs, git history, and any project notes or issue tracker your agent can already reach.
- **Writes:** one file, the report. It changes no code, opens no issues or PRs, and does not commit the report unless you ask.
- **Network:** none beyond what your agent already does. It does not run your app, call your APIs or touch production.

If your agent has a first-party docs connector (such as Claude Docs) and you ask for a shared doc, it can write the report there instead.

## Credit

The framework belongs to **Rob Walling** and **Einar Vollset**. Everything this skill knows about attacks, moats, the worker ladder and the five tests comes from their work:

- The talk videos, slides and the "Moats in the Age of AI" Field Guide: [microconf.com/moats](https://microconf.com/moats). This is the place to start.
- Rob Walling's talk on defense (the 10 attacks and 8 moats) and Einar Vollset's talk "How to Unfuck Your SaaS" (offense, the worker ladder), both at MicroConf Europe 2026. Watch both at [microconf.com/moats](https://microconf.com/moats).
- More MicroConf talks: [YouTube](https://www.youtube.com/@microconf) and [microconf.com/videos](https://microconf.com/videos)
- Startups for the Rest of Us episode 855, [The Eight SaaS Moats that Still Work in the Age of AI](https://www.startupsfortherestofus.com/episodes/episode-855-the-eight-saas-moats-that-still-work-in-the-age-of-ai)
- Startups for the Rest of Us episode 836, [The 5 A.I. Moats Acquirers Value Most](https://www.startupsfortherestofus.com/episodes/episode-836-the-5-a-i-moats-acquirers-value-most)

This is not endorsed by or affiliated with Rob Walling, Einar Vollset, or MicroConf (or TinySeed or Discretion Capital). It is my own project, shared with their permission. The reference files hold summary notes and short attributed quotes; for the full argument, watch the talks, read the Field Guide and listen to the episodes.

## Contributing

Issues and pull requests are welcome. Before opening one, run:

```bash
./validate-skills.sh            # quick checks against the Agent Skills spec
./validate-skills-official.sh   # the official skills-ref validator
```

See [AGENTS.md](AGENTS.md) for the repo layout and the house style for skill text.

## License

MIT for the skill text and scripts in this repo; see [LICENSE](LICENSE). The moat framework and the quoted material remain the work of their authors.

Made by [Zack Gilbert](https://github.com/zackgilbert).
