# Product decisions

Log of what we've settled and what's still a proposal. If something changes, edit the line and note the date instead of deleting it.

## Decided (Sunny)

2026-10-30, teaching direction
- **The problem, stated broadly:** humans don't remember or understand what AI built once it's been built. Architecture tracking is one part of the answer, not the whole product.
- **We teach the code to the user.** Beyond catching people up, the product explains their own code in an engaging way instead of plain text. Sunny's position is that this is backed by teaching psychology and proven learning concepts built into how it behaves.
- **Not a curriculum by default.** Lessons are short, tied to a moment of change, and weighted by risk: auth, payments, secrets and data deletion come first.
- **A short curriculum is in scope as an optional feature** for new developers joining a project.

2026-10-30, direction change
- **Core problem:** AI writes more and more of the code, and the humans who own it lose track of what was built. That the market for this is big is Sunny's belief, not something we've verified.
- **The loop:** a webhook fires on every push, an agent reads the diff, and the product updates the user's picture of the codebase. Each update links to the commit that caused it, with a reason.
- **The canvas and code generation are on hold.** They come back later only if the core proves itself. They were the weakest part of the idea, because AI coding tools already scaffold apps from a prompt.

2026-10-30, still true from before
- **Audience:** small scale. Fast builders, solo founders, tiny teams. Not enterprise.
- **Pricing shape:** tiered subscriptions. Higher tiers get more usage and more projects. A free tier exists.
- **No lock-in:** everything lives in the user's own GitHub repo.

Superseded as the core (kept for history): a drag and drop canvas that generates a GitHub repo from preset blocks like payments and email.

## Proposed (Claude's suggestions, not confirmed yet)

2026-10-30
- **Test before building:** ship only the GitHub app first. It comments on pushes with what changed and why. Install it on five builders' real repos.
- **Lesson test:** hand-build one 5-minute lesson with three questions for a real AI-built repo. Give it to someone who didn't write the code and see if they finish it and answer correctly. Do this before building any lesson UI.
- **Ground every lesson in the actual code:** point at real lines and generate quiz questions from the code, so the product never teaches something wrong.
- **Measure retention with a short quiz,** the way the Anthropic study measured comprehension.
- **An understanding map:** which parts of the codebase the user has engaged with and which they haven't, like test coverage. Worth testing as a hook.
- **Learning techniques to check:** retrieval practice (quizzing), spacing, worked examples, and asking the user to explain back. These are general learning-science ideas. We haven't verified which ones transfer to code comprehension.
- **Updates are never applied silently:** the user accepts or dismisses each one, so the record doesn't drift from the code.
- **Early risk to test:** the agent flagging noise. Build a labeled set of about 20 real diffs and score the agent before polishing anything.
- **Success measure:** testers keep the app installed after a week, act on more than half of the updates, finish lessons and answer most questions correctly, and at least 3 of 5 say they'd miss it.
- **Meter on usage, not project count:** analyzed commits per month tracks the real cost. Project caps stay a secondary lever.
- **Free tier as a small permanent allowance** instead of a time-limited demo. Gate analysis volume, not the basics.

## Landscape (checked 2026-10-30, mostly one page per tool, so shallow)

- **The problem is real.** Stack Overflow's 2025 survey: 80% of developers use AI tools, 29% trust their accuracy, and 66% spend extra time fixing "almost right" code. Anthropic's randomized study of 52 mostly junior developers: the AI group scored about 17% lower on a comprehension quiz (50% vs 67%). Asking follow-up questions or for explanations kept understanding. Delegating everything or leaning on AI to debug hurt it. The authors say the pattern analysis isn't causal.
- **Entire** (founded by the ex-GitHub CEO): $60M seed at a $300M valuation, Feb 2026. Its open source Checkpoints tool stores prompts, transcripts and tool calls in the repo, linked to each commit, with search and line attribution. It's capture and review, not teaching.
- **Git AI:** marks which lines AI wrote through agent hooks, stored as git notes, overlaid on git blame.
- **Google Code Wiki:** regenerates a wiki and diagrams after each change. Free preview for open source projects.
- **DeepWiki:** snapshot wiki per repo, pinned to a commit.
- **Archyl:** C4 diagrams from a codebase with drift detection. Freemium, aimed at architects and teams.
- **CodeRabbit:** walkthrough diagram and summary per PR. About $24 to $30 per developer per month, from a third-party review.
- **DIY:** Simon Willison's linear walkthroughs (an agent writes a walkthrough with real code snippets), and spec-driven tools like Kiro, spec-kit and Tessl, which Martin Fowler found tedious to review.
- **Spending:** Lovable passed $400M in annual recurring revenue as of Feb 2026, per a news article. People pay to generate code. We have no evidence yet that they'd pay to understand it.
- **Not found:** anyone teaching the owner their own code interactively. That's from about ten sources, so treat it as a lead, not a fact.

## Open questions

- Where output lives: PR comments, a file in the repo, a hosted page, or several. Same question for lessons.
- How we differ from Entire, Archyl, DeepWiki and Code Wiki in one sentence.
- Which learning techniques actually transfer to code comprehension.
- Who the first user is: an owner catching up on their own AI-built app, or a new developer onboarding.
- Product name. "Blocks" was for the canvas.
- Pricing numbers and tier names.
- Whether the canvas comes back later as a view over the same data.
