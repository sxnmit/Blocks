# Product decisions

Log of what we've settled and what's still a proposal. Newest at the bottom of each section. If something changes, edit the line and note the date instead of deleting it.

## Decided (Sunny)

2026-10-30
- **Product:** a drag and drop canvas for planning and building software, mainly SaaS. You lay out the architecture visually instead of stacking code by hand, like Scratch blocks but for real services.
- **Presets:** ship with sensible default blocks. Payment gateways, email, and other common workflows first.
- **No lock-in:** the canvas generates a real GitHub repo. Users keep coding in it. Custom logic is theirs to write in GitHub, and agents help with custom logic on a best-effort basis.
- **Round-tripping:** a webhook on the repo fires on every push. An agent reads the diff and proposes changes to the architecture on the canvas.
- **Traceability:** every proposed canvas change links to the commit that caused it and gives a reason.
- **Audience:** small scale. Fast builders, solo founders, tiny teams. Not enterprise.
- **Pricing shape:** tiered subscriptions. Higher tiers get more usage and more projects. A free demo tier exists.

## Proposed (Claude's suggestions, not confirmed yet)

2026-10-30
- **Meter on usage, not project count:** analyzed commits per month tracks the real cost (LLM diff analysis). Project caps stay as a secondary upsell lever.
- **Free tier as a small permanent allowance** instead of a time-limited demo: for example 1 project and a few dozen analyzed commits a month. Keep canvas and code generation generous, gate analysis volume.
- **Proposals are never applied silently:** the user accepts or dismisses each one. This is how we keep canvas and repo from drifting apart.
- **v1 scope:** fixed blocks (app, database, auth, Stripe, email), one stack (Next.js + Postgres), one commit analysis loop. See ROADMAP.md.
- **Early risk to test:** the agent flagging noise. Build a labeled set of about 20 real diffs and score the agent before building the proposal UI.
- **Success measure for v1:** most testers still have the repo connected after a week, and they accept more than half of the proposals.
- **Test with five solo builders** at the end of the first build.

## Open questions

- Product name.
- Final v1 stack. Next.js + Postgres is a placeholder.
- Pricing numbers and tier names.
- Direction of edits: once the repo exists, can the user also change the canvas and have it update the code? Not discussed yet.
- Where the generated app gets deployed, if anywhere, in v1.
- Whether the product takes a cut of payments that flow through the stack it sets up (floated as an option, not decided).
