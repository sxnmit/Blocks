# Roadmap

AI writes more of our code, and people lose track of what got built. This product watches every push to a GitHub repo, keeps the user's picture of the codebase current, and teaches them their own code through short, engaging explanations instead of walls of text. Each update ties to a commit and a reason. You accept or dismiss each one. Built for solo founders and tiny teams. Decisions behind this live in [DECISIONS.md](DECISIONS.md).

Status: planning. Nothing is built. The direction changed on 2026-10-30: the loop above is the product, and the drag and drop canvas with code generation is a later bet. Timeline is a first guess.

## Step 1: prove people care (about 3 to 4 weeks)

Two questions to answer. When the app explains a push, do people read it, trust it and act on it? And when we teach them a piece of their code, do they finish it and actually understand it afterward?

- [ ] **Week 1: GitHub app and diff agent, no UI.** Push webhook. Agent reads the diff and posts a comment with what changed, the commit link, and a one-line reason.
- [ ] **Week 1, in parallel: diff eval set.** Collect about 20 real diffs, label which are real architecture changes and which are details. Score the agent. This is the noise test.
- [ ] **Week 1, in parallel: ten conversations** with people who ship AI-written code. Ask when they last got lost in their own repo, what it cost them, and what they'd pay to avoid it.
- [ ] **Week 2: hand-built lesson test.** One 5-minute lesson with three questions, made by hand for a real AI-built repo. Give it to someone who didn't write the code. Do they finish it, and do they get the questions right? No lesson UI yet.
- [ ] **Week 2: a living architecture summary.** A file in the repo (for example ARCHITECTURE.md with a diagram) that updates as proposals are accepted.
- [ ] **Week 3: five builders.** Install it on their real repos, mostly AI-written code. Give each one a lesson on a real push. Watch what they do.
- [ ] **Week 4: read the result and decide** whether to keep going, change course, or bring the canvas back.

Keep going if: testers keep it installed after a week, act on more than half of the updates, finish lessons and answer most questions correctly, and at least 3 of 5 say they'd miss it.

Stop or rethink if: people mute it, skip the lessons, or the agent keeps calling details architecture changes.

## Not in step 1

- Canvas, drag and drop, code generation
- A lesson UI, or any curriculum
- Custom blocks, teams, enterprise anything
- Real billing and tiers (hardcode a usage cap)

## Later (only if step 1 works)

- Lessons in a proper interface: short, tied to a change, weighted by risk
- An understanding map showing which parts of the codebase you've engaged with
- A short optional curriculum for new developers joining a project
- Tiered subscriptions metered on analyzed commits, with a small permanent free tier
- A canvas as a view over the same data, and generating starter repos from it

## Agent team for building this

Using [wshobson/agents](https://github.com/wshobson/agents). It has 92 local plugins, so we install only what a stage needs. Install with `/plugin marketplace add wshobson/agents`, then `/plugin install <plugin>@claude-code-workflows`.

**Install now**

| Plugin | Why |
|---|---|
| conductor | Context, spec, plan, implement. Keeps this roadmap and the build in sync. |
| agent-teams | Parallel feature work and review. |
| llm-application-dev | The diff agent and the lesson generator. |
| backend-development | Webhook service and API. |
| backend-api-security | Webhook signature checks, GitHub app auth, rate limiting. |
| database-design | Schema for repos, commits, proposals and lesson results. |
| c4-architecture | Reference for how to describe architecture in the summary and diagrams. |
| full-stack-orchestration | End to end feature flow with testing and deployment. |
| comprehensive-review | Review pass before anything ships. |

**Install when needed**

- frontend-mobile-development: the lesson interface, and the canvas if it comes back
- payment-processing: our own billing, and the Stripe block if code generation comes back
- cicd-automation: pipelines for our own repo
- git-pr-workflows and tdd-workflows: once more than one person is committing
- startup-business-analyst: pricing and market sizing

**Skip for now:** everything else in the catalog.

## Working in this fork

- `origin` is this fork (sxnmit/Blocks). The original repo is the `upstream` remote, so we can pull its updates when we want them. Our product docs (this file and DECISIONS.md) live at the repo root.
- Before pushing source changes, the repo's own gates are `make validate STRICT=1`, `make garden`, `make test`. They aren't needed for doc-only changes.
