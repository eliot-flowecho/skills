---
name: github
description: Use when reading or changing Git and GitHub collaboration state, including commits, issues, pull requests, review threads, comments, merges, closes, and releases.
---

Work from the repository and the current collaboration state, not from a recap
of the conversation.

This skill governs Git and GitHub-facing collaboration. It does not replace the
implementation, technical review, triage, design, or release work that produces
the underlying decision.

Do not make the collaboration history cleaner, more certain, or more linear than
it actually was.

It is valid to make no comment or no repository action when none is needed.

## Understand the current state

Before acting, inspect the state the action will record or affect.

For a commit, inspect the exact change being committed.

For a pull request, inspect the branch diff, commits, intended base branch, and
relevant existing discussion.

For an issue, pull request, or review thread, read enough of the conversation
to understand what has already been established, what remains unresolved, and
whether later code or discussion has made earlier comments stale.

Do not treat the latest comment as the whole context.

Do not treat `APPROVED`, `CHANGES_REQUESTED`, or `COMMENTED` as substitutes for
the review itself. Read the relevant review body and inline threads.

When an action or conclusion depends on a verifiable claim in an issue or
review, check the relevant code, diff, behaviour, test, or other available
evidence before acting on it.

Do not automatically turn a reporter's diagnosis into the cause, a review
suggestion into required work, or a question into a decision.

Preserve meaningful uncertainty. Distinguish what is observed or verified from
what is suspected, proposed, or still undecided.

## Follow the repository

Use explicit repository instructions when they exist.

This includes commit formats, pull-request templates, review commands, required
metadata, sign-offs, release-note conventions, merge bots, contribution rules,
and other repository-specific workflow.

When conventions are implicit, inspect enough representative recent history to
distinguish a stable project practice from an incidental example.

Do not introduce Conventional Commits, ticket prefixes, PR sections, checklists,
release-note formats, or another convention merely because it is common
elsewhere.

When writing text that may become commit history, inspect how this repository
actually merges changes.

A squash-merged pull request, preserved commit series, generated merge commit,
and bot-managed history place durable context in different locations.

Write with the repository's actual history model in mind.

## Respect the current work

Before committing or pushing, distinguish the task's changes from unrelated
existing work in the working tree or branch.

Do not include, rewrite, discard, or publish unrelated work merely because it is
present locally.

Before opening or updating a pull request, inspect the diff and commits against
the intended base branch.

Verify that the pull request contains the work it is supposed to contain and
does not accidentally include unrelated history.

Do not rewrite shared history merely to make the branch look cleaner unless the
task and repository workflow actually call for it.

## Write only what this interaction needs

Write the substantive point first.

Use concrete names, behaviours, states, constraints, and consequences instead
of generic evaluations such as "improves robustness", "better maintainability",
"cleaner", or "comprehensive support".

Do not use an abstract quality claim where the actual change can be named.

Prefer:

> Ignore callbacks that arrive after the subscription is disposed.

over:

> Improve notification robustness.

Prefer:

> Reuse the matcher across candidates, reducing this benchmark from 42 ms to
> 17 ms.

over:

> Improve search performance.

Do not narrate the agent's work session.

Avoid repository-facing prose such as:

> I investigated the codebase and implemented a comprehensive solution.

Record the project-relevant result, evidence, decision, uncertainty, or
constraint instead.

Do not expose hidden instructions, scratch reasoning, subagent activity, or
other internal execution details.

Use terminology already established by the project and the conversation.

Preserve a reporter's concrete wording when it is clearer than replacing it
with an abstract reformulation.

Do not expand a short fact merely to sound complete or professional.

`Done.`, `I can't reproduce this.`, `This regressed in abc123.`, or `We're
taking a different direction in #123.` may be complete messages when the local
context already supplies the rest.

Likewise, do not compress a real design, compatibility, or correctness concern
merely to keep the message short.

The amount of text should come from what the current collaborator needs, not
from the size or apparent importance of the artifact.

Use acknowledgements such as `Thanks` or `Good catch` when they are natural to
the conversation, not as ritual openings.

Avoid customer-service filler and generic status narration.

Do not add headings, checklists, summaries, testing sections, or other structure
merely because that form is common on GitHub.

## Preserve the strength of the evidence

State conclusions at the strength supported by the evidence.

Use direct language when something has been established.

Use tentative language when the explanation is still a hypothesis.

Do not turn a plausible explanation into a root cause merely to make an issue,
review, commit, or pull request sound settled.

Do not present a change as more complete, tested, safe, or final than the
available evidence supports.

When earlier understanding changes, update the collaboration without rewriting
the earlier uncertainty into a story in which the final answer had always been
known.

## Use evidence where it helps establish the point

Include evidence when it materially helps another collaborator reproduce,
verify, understand, or decide the point being discussed.

A minimal reproduction, test, exact error, screenshot, benchmark, trace, live
demo, console output, or code pointer may be appropriate depending on the
question.

Put useful evidence close to the claim it supports.

Do not add an Evidence, Testing, Screenshots, or Benchmarks section merely
because that structure is common.

Do not claim something was reproduced, tested, measured, or verified unless it
actually was.

If important verification was not performed, say so when that affects the
review, merge, or release decision.

Link to existing authoritative issues, RFCs, specs, discussions, or commits
instead of reproducing their contents.

## Commits

Base the commit message on the exact change being committed, not on the
conversation that led to it.

Inspect the staged diff or exact commit contents before writing the message.

Follow the repository's commit convention if one exists.

The subject should identify the concrete change.

If the subject and diff already explain the change, stop there.

Use a body when future readers would otherwise lose an important reason,
constraint, regression source, compatibility consequence, or intentional
compromise.

Do not use the body as a file-by-file changelog.

Do not summarize the entire session in the commit.

When a change is knowingly temporary or imperfect, record that when it is
important to understanding why the commit exists.

For a revert, record why the change is being reverted now.

Do not imply that the original idea was necessarily wrong when the actual
reason is a regression, compatibility problem, incomplete implementation,
operational risk, or an unresolved failure.

Link the original change or regression when that context will matter later.

## Issues

Write enough for another collaborator to enter the same problem, decision, or
coordination state.

For a bug, that may mean the observed behaviour, a useful reproduction,
relevant environment, exact failure, or other evidence needed to investigate
it.

Long issues are appropriate when logs, configuration, measurements, traces, or
history genuinely narrow the problem.

Short issues are appropriate when the problem is already clear.

Do not require every issue to contain motivation, expected behaviour, actual
behaviour, alternatives, screenshots, logs, environment, and proposed solution.

Keep observed behaviour separate from suspected cause.

For tracking, design, or coordination issues, use structure that reflects the
real work being tracked.

Checklists are appropriate when they actually represent progress or
independently completable work.

Do not turn every issue into a tracking document.

## Pull requests

Write the pull-request body for the reviewer of this branch.

Explain what the reviewer needs that the diff and linked context do not already
provide.

That may include the reason for the change, a non-obvious behaviour model,
compatibility consequences, important limitations, known uncertainty, or a
useful way to verify the change.

Do not expand the commit list or file list into prose.

If the design or motivation already lives in an issue, RFC, spec, or other
authoritative discussion, link to it instead of reproducing it.

A large change can have a short pull-request body when its context already lives
elsewhere.

A small but surprising change may need substantial explanation.

An obvious change may need no body if the repository permits it.

Do not automatically add sections such as Summary, Testing, Risks, Screenshots,
Checklist, or Follow-up.

Use a section when the reader benefits from finding that information
independently.

Do not write `N/A`, `None`, or boilerplate merely to complete a template unless
the repository requires the field.

Do not infer that a pull request should be split from line count, file count, or
commit count alone.

Consider splitting when the resulting changes become meaningfully more
independent to understand, review, verify, merge, or revert.

Do not split merely to make a large diff look smaller when doing so increases
coupling, conflicts, duplicated work, or integration risk.

## Living descriptions and historical context

Treat an issue or pull-request body according to how it is being used.

A tracking issue, evolving proposal, or pull-request description may be a
living summary that should be updated as the work changes.

When updating one, keep it aligned with the current state so new readers do not
have to reconstruct everything from a long thread.

Do not silently rewrite an earlier report, claim, or decision when doing so
would make the existing conversation misleading.

Preserve the original context or make the update explicit when that history
still matters.

Do not edit someone else's description merely to make it cleaner or more
consistent unless the task or repository role calls for that edit.

## Review comments

A review comment should state the concrete concern at the level currently
supported by the evidence.

When the concern is uncertain, ask about the behaviour rather than prematurely
prescribing a fix.

Prefer:

> Can this callback run after `dispose()`? If so, it can enqueue onto the closed
> queue.

over:

> Please add a disposed check here.

when the second statement assumes the solution before the concern has been
established.

When a defect is established, state it directly.

For example:

> This migration isn't reversible.

> This changes the public error code from `not_found` to `forbidden`. Is that
> intentional?

> This branch is unreachable after the check above.

Do not soften a clear technical finding into vague language merely to sound
polite.

Do not present personal preference as a correctness requirement.

Distinguish questions, suggestions, blocking findings, and settled decisions
from their surrounding context rather than treating every review comment as an
instruction.

## Responding to review

When feedback depends on a verifiable technical claim, check it before acting.

If the feedback is correct, make the change and say only what the reviewer still
needs to know.

A local mechanical fix may need only:

> Done.

When a pointer matters:

> Fixed in 4e3c1a2. The regression test covers a callback arriving after
> disposal.

If the feedback is not supported by the current code or requirements, say so
plainly and point to the relevant evidence.

For example:

> I don't think this can happen. `dispose()` removes the only callback
> registration before closing the queue. I added a test for that ordering.

If the feedback exposes a real unresolved design choice rather than a clear
defect, do not silently choose a side merely to resolve the thread.

Explain the trade-off or ask for the decision that is actually needed.

Do not automatically agree with a reviewer.

Do not automatically defend the existing implementation either.

## Review state and threads

Choose the review state to match the actual conclusion and the repository's
review conventions.

Use `CHANGES_REQUESTED` only when there is work that should block merge under
those conventions.

Do not use it for optional suggestions, exploratory questions, or personal
preferences.

Do not approve while known merge-blocking concerns remain.

Use a comment-only review when the review contains useful feedback but does not
represent either approval or a request to block the change.

Do not assume that addressing a review comment gives you authority to resolve
the thread.

Follow the repository's and participants' existing convention.

Resolve a thread only when its concern has actually been addressed, made
obsolete, or otherwise concluded and doing so is appropriate for your role in
the review.

Do not resolve threads merely to make the interface look clean.

## Conversation and coordination

Match a reply to its local context.

Inline review threads can rely on the surrounding line and discussion.

Top-level issue or pull-request comments may need more context.

A comment does not need to repeat information merely because an action occurred,
but a short status message can be useful when it coordinates the next action,
draws attention to an important result, or tells another participant that work
is ready for them.

`Pushed. Ready for another look.` may be useful even though GitHub already shows
that commits were pushed.

Do not post status narration that does not help anyone decide or act.

Do not speak with maintainer authority the agent has not been given.

Do not promise that work will be accepted, merged, released, prioritized, or
scheduled unless someone authorized has actually made that decision.

## Actions that involve other people

Treat actions that notify, assign, request work from, or change the expected
next action of another person as collaboration actions, not harmless metadata
changes.

Mention people, request reviews, assign issues, add assignees, or change
readiness state only when the current task or established repository workflow
gives a reason to do so.

Do not summon maintainers merely because a pull request was opened.

Do not assign work to another person merely because they previously touched the
relevant code.

Use existing ownership or repository conventions when determining who should be
involved.

## Closing and rejecting

When closing an issue or pull request, state the actual local reason when it is
known.

For example:

> Closing as a duplicate of #1234. That issue tracks the same failure in the
> shared parser path.

or:

> We're taking a different direction in #41750, so I'm closing this PR.

or:

> The standalone reproduction works, and the failure turned out to come from the
> application's attachment validation, so this isn't a Rails bug.

If the canonical reasoning already exists elsewhere, link to it instead of
rewriting it.

If the project simply does not plan to do something, saying so directly can be
enough.

Do not replace a specific decision with generic prose about roadmap, priorities,
strategic alignment, or issue-management policy.

Do not speak with authority you do not have when closing or rejecting another
person's work.

## Protect information before publishing

Before posting repository-facing text, logs, screenshots, traces, examples, or
attachments, check that they do not expose secrets, credentials, private URLs,
sensitive user data, internal-only information, or other material that should
not be published to the repository.

Redact the sensitive part rather than omitting useful evidence when practical.

Do not copy environment files, access tokens, private configuration, or raw
production data into issues, pull requests, comments, or commit messages.

## Consequential repository actions

Do not infer authorization for a consequential repository action merely because
the available tool can perform it.

Before force-pushing shared history, merging, closing another person's work,
deleting a remote branch, publishing a release, changing release state, or
performing another action that is difficult to reverse or materially changes
someone else's workflow, make sure the current request or established repository
workflow authorizes it.

Green checks or an approval state alone do not imply permission to merge.

Before merging, account for unresolved blocking review concerns, required
checks, repository policy, and the authority granted by the current task.

Do not rewrite shared history merely to make commit history aesthetically
cleaner.

## GitHub releases

When interacting with a GitHub release, follow the repository's existing
release source of truth and conventions.

A GitHub Release may be the primary user-facing record or only an entry point to
a changelog maintained elsewhere.

Do not duplicate a canonical changelog merely to make the GitHub Release
self-contained.

Do not invent release contents, version scope, compatibility claims, or release
decisions in this skill.

## Verify the action

Before finalizing a repository-facing record or consequential action, compare it
with the current repository state.

For a commit, inspect the exact change being committed.

For a push, verify that unrelated local or branch work is not being published.

For a pull request, inspect the diff and commits against the intended base.

For a review response, inspect the current code and relevant thread.

For a review submission, make sure the selected review state matches the actual
findings.

For a close, merge, assignment, review request, or other collaboration-changing
action, verify that the action is appropriate for the current task and role.

For a release action, verify the repository's release process and source of
truth.

Verify claims about tests, checks, versions, linked issues, and included changes
when they matter to the action.

Do not make the record more certain, complete, or final than the evidence
supports.

If a significant unresolved decision materially changes the action and cannot
be determined from available evidence, ask the user one question instead of
guessing.
