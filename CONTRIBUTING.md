# Contributing

This applies to every repository in the Human Adaptive Technology Studio unless a repository says otherwise in its own `CONTRIBUTING.md`.

## What is enforced, and what is expected

Almost nothing in this document is enforced by GitHub. On our current plan, private repositories do not support protected branches, required reviews, or required status checks. That means:

| | |
| --- | --- |
| **Enforced** | Two-factor authentication for all members. Repository access via the organisation. That is the current list. |
| **Expected** | Everything else in this document. |

Nothing will stop you pushing directly to `main`, merging your own pull request, or committing a file that should not be in Git. These practices work because people follow them, not because a system blocks them. Please read them in that spirit.

Where this document says **must**, it means a rule with consequences — usually about data, credentials or publication. Where it says **should**, it is a strong default you may depart from with a reason.

## Contribution philosophy

Research code has a real tension in it: you are exploring, and exploration is messy, but the result may end up supporting a published claim or being handed to someone who was not there. We try to hold a practical line — not production engineering discipline on a two-week probe, but not code that only its author can run either.

The test we use: **could a competent colleague pick this up in six months and understand what it does and why?** If a project ends and nobody can run its code, the work is much harder to build on, and reproducing a result may become impossible.

## Branches

- `main` is the default branch in every repository and should always be in a working state.
- Work on a branch, not on `main`. Name it for what it does: `add-hrv-baseline`, `fix-session-timeout`, `spike-eye-tracking`.
- Short-lived branches are easier to review. If a branch has been open for weeks, consider whether it can be split.
- Delete branches after merging.

Direct commits to `main` are not blocked, and for a genuinely trivial change (a typo, a README line) they are fine. For anything that changes behaviour, use a branch.

## Pull requests

Open a pull request for anything that changes how the code behaves. The PR template will prompt you through the checks below.

**Small changes** — a bug fix, a small addition, a documentation update. One reviewer, or self-merge if you are the only person on the project and the change is low risk. Say so in the PR rather than merging silently.

**Substantial changes** — new capability, a change to an interface others use, anything affecting how data is handled or stored, anything touching a shared component, anything that could affect a research result. These **should** be reviewed by someone else before merging, even when you could merge them yourself. If you are the only person who can review it, that is worth raising with your project lead.

Since nothing enforces review, the honest version of this rule is: **the more consequential the change, the less you should be the only person who has looked at it.**

## Review

Reviewing is a normal part of the work, not a favour. When reviewing:

- Read for correctness first, style second.
- Check the data and secrets boxes on the PR yourself rather than trusting the ticks — this is the check most worth duplicating.
- Ask questions rather than issuing instructions. Research code often has context you do not have.
- Approve when it is good enough to merge, not when it is perfect.

When receiving review, assume good faith and disagree openly where you disagree.

## Issues

- Use issues for work that is worth tracking. Not everything is.
- Link the pull request to its issue (`Closes #12`) so the history explains itself later.
- Use the `research_task` template for work driven by a research question, and `bug_report` or `feature_request` for engineering work. They prompt for different things on purpose.

## Commits

- Write a subject line that says what changed: `Add resampling to HRV pipeline`, not `updates` or `fix`.
- Explain *why* in the body when the reason is not obvious. The diff already shows what.
- Commit in coherent steps where you can. Nobody will object to a messy history on an exploratory branch.
- Use the Git identity you use in the organisation, so contributions are attributed to you.

## Testing

Proportionate to the risk:

- Code that produces a number appearing in a paper, or that transforms participant data, **should** have tests. A wrong result is worse than a crash, because it does not announce itself.
- Shared components — anything another project depends on — should have tests.
- Exploratory prototypes need not, but should say in the README how to check they are working.

If a repository has tests, run them before opening a pull request. Nothing enforces this.

## Documentation

Every repository **must** have a README that answers: what is this, what does it need, how do I run it, who maintains it, and what state is it in. A prototype README saying "this is an unfinished spike, ask Kunal" is more useful than a polished one that is out of date.

Update documentation in the same pull request as the change. Documentation updated later is documentation not updated.

## Working with research code

- **Record what a result came from.** If a figure or number came from a specific commit, note the commit. Tag before generating results you intend to publish.
- **Keep configuration out of the code.** Paths, thresholds and parameters in a config file are far easier to audit than the same values scattered through a script.
- **Notebooks:** clear outputs before committing. Notebook outputs routinely embed data — including plots of participant recordings — and are easy to commit without noticing.
- **Seeds and versions matter.** Record random seeds and dependency versions where a result depends on them.

## Data

**Do not commit research data to GitHub.** The Studio's data governance rules are in the internal handbook, and every member should read them before their first commit. In summary:

- Participant-identifiable information, linkage files, consent forms, health information, and raw participant recordings **must never** be committed. Not to a private repository either.
- Anonymised samples, synthetic data, small example biosignal files, benchmark fixtures, derived aggregates, model weights and calibration files **require review before** they go in.
- Raw datasets, study datasets, training data, large model artefacts and participant audio or video belong in approved research storage, not here.

**A private repository is not a data protection measure.** It is visible to every current and future member of the organisation, and its history is permanent.

**If you are unsure, ask before committing.** Removing something afterwards is far harder than not adding it — see below.

## Secrets

Never commit passwords, API keys, tokens, certificates, private keys or production credentials. Use environment variables or a local `.env` file that is listed in `.gitignore`.

Our current plan does not provide GitHub secret scanning or push protection on private repositories, so nothing will catch a committed credential automatically. If you commit one, follow [SECURITY.md](SECURITY.md) — **rotate the credential first**, before worrying about the history.

## Git history is permanent

Deleting a file in a later commit does not remove it from the repository. The content stays in history and in every clone anyone has already made. Removing it properly requires rewriting history and coordinating with everyone who has a copy, and even then, copies already taken are out of your control.

This is why the checks happen before you commit.

## Intellectual property and public release

- Repositories are **private by default** and stay private until ownership, licensing, ethics, cultural governance, publication status and partner obligations have been considered.
- **Do not add a licence file** to a repository on your own initiative. An added licence is a statement about ownership that may not be yours to make.
- **Do not make a repository public** without approval from the Organisation Owner.
- Do not copy code from a Studio repository into a personal or public repository.
- When you add a third-party dependency, check its licence is compatible with how the work might eventually be released, and mention it in the pull request.

If you are contributing as a student, your contributions are recognised — see the handbook on contribution credit. Ownership of student work varies, so it is worth being clear early rather than at publication.

## Acknowledgement

Contributors are credited. Where a repository supports a publication it should carry citation metadata naming its contributors. If you have contributed meaningfully and are not credited, say so — that is an oversight, not a decision.

## When to ask before acting

Ask first, every time, before you:

- commit anything derived from participant data
- add a dataset, model weights, or a large binary file
- make a repository public, or add a licence
- give anyone outside the Studio access to a repository
- rewrite history on a shared branch
- add a dependency with an unusual or restrictive licence
- move code out of a project into a shared component

The cost of asking is a short conversation. The cost of not asking, for most items on this list, is not recoverable.

Ask your project lead, or the Organisation Owner: Dr. Kunal Gupta — <kunal.gupta@auckland.ac.nz>
