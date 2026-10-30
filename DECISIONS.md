# Product decisions

Log of what we've settled and what's still a proposal. If something changes, edit the line and note the date instead of deleting it.

## Decided (Sunny)

2026-10-30, direction change
- **Core problem:** AI writes more and more of the code, and the humans who own it lose track of what was built. The product helps people remember what their codebase contains and why it changed. That the market for this is big is Sunny's belief, not something we've verified.
- **The core is the commit-linked loop:** a webhook fires on every push, an agent reads the diff and proposes updates to the architecture, and each proposal links to the commit that caused it with a reason.
- **The canvas and code generation are on hold.** They come back later only if the loop proves itself. They were the weakest part of the idea, because AI coding tools already scaffold apps from a prompt.

2026-10-30, still true from before
- **Audience:** small scale. Fast builders, solo founders, tiny teams. Not enterprise.
- **Pricing shape:** tiered subscriptions. Higher tiers get more usage and more projects. A free tier exists.
- **No lock-in:** everything lives in the user's own GitHub repo.

Superseded as the core (kept for history): a drag and drop canvas that generates a GitHub repo from preset blocks like payments and email.

## Proposed (Claude's suggestions, not confirmed yet)

2026-10-30
- **Test before building:** ship only the GitHub app first. It comments on pushes with what changed architecturally and why. Install it on five builders' real repos.
- **Proposals are never applied silently:** the user accepts or dismisses each one. This is how we keep the architecture record from drifting away from the code.
- **Early risk to test:** the agent flagging noise. Build a labeled set of about 20 real diffs and score the agent before polishing anything.
- **Success measure:** testers keep the app installed after a week, they act on more than half of the proposals, and at least 3 of 5 say they'd miss it if it went away.
- **Meter on usage, not project count:** analyzed commits per month tracks the real cost. Project caps stay a secondary lever.
- **Free tier as a small permanent allowance** instead of a time-limited demo. Gate analysis volume, not the basics.

## Landscape (checked 2026-10-30, one page per tool, so shallow)

- The problem is widely discussed as "comprehension debt". A Faros article on it cites an Anthropic study where heavy AI users scored 17% lower on comprehension tests, and Faros data showing bigger PRs and more unreviewed merges with heavy AI use.
- **Archyl:** generates C4 architecture diagrams from a codebase, detects drift between docs and code, stores architecture as YAML in Git. Freemium. Aimed at architects and teams.
- **DeepWiki:** auto-generated wiki per repo with citations pinned to a commit. Looks like a snapshot you refresh by hand.
- Several small open source doc generators also show up in search.
- Not checked: pricing, and whether any tool already explains each push with a reason the way we plan to.
- The gap we're betting on: a per-commit, reason-linked, accept or dismiss record for people whose code is mostly written by AI, living in the GitHub workflow.

## Open questions

- Where the output lives: PR or push comments, a file in the repo, a hosted page, or all three.
- How we differ from Archyl and DeepWiki in one sentence.
- Product name. "Blocks" was for the canvas.
- Pricing numbers and tier names.
- Whether the canvas comes back later as a view over the same data.
