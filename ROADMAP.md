# Roadmap

A canvas where you drag and drop your software architecture and it generates a real GitHub repo. When someone pushes code, an agent proposes matching changes to the canvas, each tied to a commit and a reason. Built for solo founders and tiny teams. Decisions behind this live in [DECISIONS.md](DECISIONS.md).

Status: planning. Nothing here is built yet. Timeline is a first guess.

## v1: prove the loop (about 6 weeks)

The one thing v1 has to show: when someone edits the generated repo by hand, the agent proposes a correct, useful canvas change tied to that commit.

- [ ] **Weeks 1 to 2: canvas and codegen.** Fixed blocks (app, database, auth, Stripe, email). Generate a repo for one stack, Next.js + Postgres.
- [ ] **Week 3: GitHub connection.** GitHub app, repo creation, push webhook.
- [ ] **Early, before the UI: diff eval set.** Collect about 20 real diffs, label which are true architecture changes (new service, new external dependency) and which are just details. Score the agent against it.
- [ ] **Weeks 4 to 5: diff agent and proposal UI.** Proposal shows the commit link and a one-line reason. Accept or dismiss each one.
- [ ] **Week 6: five solo builders.** Hand it over and watch them use it.

Success: most testers still have the repo connected after a week, and they accept more than half of the proposals.

## Out of scope for v1

- Custom blocks, extra stacks, teams
- Real billing and tiers (hardcode a usage cap)
- Enterprise anything
- Canvas edits that rewrite existing code (still an open question)

## Later (not committed)

- Tiered subscriptions metered on analyzed commits, with a small permanent free tier
- More stacks and more blocks
- Custom workflows and user-defined blocks
- Agents for custom logic inside the generated repo

## Agent team for building this

Using [wshobson/agents](https://github.com/wshobson/agents). It has 92 local plugins, so we install only what a stage needs. Install with `/plugin marketplace add wshobson/agents`, then `/plugin install <plugin>@claude-code-workflows`.

**Install now**

| Plugin | Why |
|---|---|
| conductor | Context, spec, plan, implement. Keeps this roadmap and the build in sync. |
| agent-teams | Parallel feature work and review. |
| full-stack-orchestration | End to end feature flow with testing and deployment. |
| backend-development | API design and backend structure for the canvas and webhook service. |
| frontend-mobile-development | The canvas UI itself. |
| database-design | Schema for projects, blocks, proposals, and commit links. |
| llm-application-dev | The diff agent. |
| backend-api-security | Webhook signature checks, auth, rate limiting. |
| payment-processing | The Stripe block we generate, plus our own billing later. |
| comprehensive-review | Review pass before anything ships. |

**Install when needed**

- c4-architecture: reference for how to model architecture in the canvas data model
- cicd-automation: pipelines in generated repos and our own
- git-pr-workflows and tdd-workflows: once more than one person is committing
- startup-business-analyst: when we get to pricing and market sizing

**Skip for now:** everything else in the catalog.

## Working in this fork

- Keep upstream as `origin` so we can pull updates. Our product docs (this file and DECISIONS.md) live at the repo root.
- Before pushing source changes, the repo's own gates are `make validate STRICT=1`, `make garden`, `make test`. They aren't needed for doc-only changes.
