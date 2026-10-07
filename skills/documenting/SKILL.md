---
name: documenting
description: Create, update, remove, or review project documentation when explicitly requested, when current work changes something readers need to know, or when real user feedback reveals a possible documentation problem.
---

Work within the scope of the request or the event that caused this skill to be
invoked.

Do not broaden a local documentation need into a wider audit, reorganization,
or documentation effort. When the user explicitly asks for project-wide work,
such as building documentation for an existing project or reviewing the
documentation as a whole, that wider scope is intentional.

It is valid for the result to be no documentation change.

## Establish the documentation need

Before deciding what to write, inspect the relevant product, code, UI, existing
documentation, navigation, and other available sources of truth.

Determine what the intended reader needs to know, decide, look up, or accomplish
that they cannot already learn more reliably from the product or an existing
source.

A user question, issue, support problem, completed slice, or code change is
evidence to investigate. None automatically requires a new page or any
documentation change.

Do not create documentation merely because a feature, screen, subsystem,
directory, public implementation detail, or navigation group exists.

If the underlying problem is better fixed in the product, UI, error message,
API, behaviour, or tooling, do not use documentation as a substitute for that
fix. Still document current behaviour when readers genuinely need to understand
it.

When current work changes reader-visible behaviour, a public interface,
configuration, supported workflow, requirement, limitation, or an existing
documented fact, update the documentation that became wrong or incomplete.

An internal implementation change does not need documentation merely because
code changed.

## Match the document's job

Determine whether the document describes current behaviour, intended behaviour,
a past decision, a contribution workflow, or a change between versions. Do not
blur these together.

User documentation should describe behaviour that is actually available in the
version it applies to.

Specs and design documents may describe intended behaviour. Record decisions
that were actually made, distinguish unresolved questions from decisions, and
do not fill unspecified parts merely to make the design look complete.

Documents that explain past decisions should preserve the rationale,
alternatives, and constraints that are actually known. Do not reconstruct
missing history merely to make a decision record complete.

Migration and release documentation should be organized around the delta from
the reader's current state. Explain what changed, who is affected, and what
they need to do. Show changed behaviour or code directly when that is clearer
than re-explaining the destination system. Distinguish what must change, what
can remain temporarily, and what automated migration can safely handle.

## Decide what should exist

Prefer changing an existing page when it already serves the reader's need.

Create a new page when readers have a distinct reason to seek it: a task,
question, explanation, lookup need, recurring situation, or stable entry point
that is not better served by an existing page.

When a page no longer serves a useful purpose, remove, merge, or move it
instead of preserving it for structural symmetry.

Do not start from a standard documentation tree and fill it in. Let document
types and collections appear because existing information needs benefit from
them, not because a mature project is expected to have them.

Do not create a section landing page merely because a sidebar group exists.

An overview or index page can be useful when readers need information on that
page to understand meaningful differences between several destinations and
choose where to go next. If removing the page would only remove a second copy
of the navigation, it probably should not exist.

Similar pages are not necessarily redundant. Different frameworks, platforms,
integrations, or environments may give readers distinct reasons to seek
separate entry points even when much of the procedure is shared. When those
pages repeat authoritative facts, prefer sharing, generating, or linking to a
common source where practical instead of maintaining drifting copies by hand.

Consider how readers reach documentation at the moment they need it. Search and
navigation are not the only entry points. A product screen, error code, CLI
message, API response, another guide, or an agent may be the more useful route
to a page.

When the product can reliably identify a specific failure, state, or next
action, linking directly to the relevant documentation may be more useful than
adding another troubleshooting or index page.

## Common document jobs

A README or documentation homepage should help a new reader understand what the
project is, whether it is relevant to them, and where to begin.

Do not turn it into an inventory of every capability, architectural choice,
integration, or documentation section. Let detailed guides and reference carry
that material.

A getting-started or quick-start page should get a new reader to the first
meaningful success quickly. Do not make it carry the full production,
administration, troubleshooting, or reference manual. Include prerequisites,
warnings, or limitations necessary to make that first success honest and safe.

User guides help readers accomplish real tasks, understand behaviour, and deal
with situations that arise while using the product. Base them on real tasks,
questions, situations, and concepts, not on a tour of screens, menus, features,
or internal subsystems.

Do not force user documentation into a fixed learning sequence. Readers may
arrive directly from search, an error, another page, or an agent.

A user guide does not need to describe everything the product can do. Explain
what the product itself does not make sufficiently clear: consequences,
conditions, scope, permissions, surprising behaviour, recovery, important
limitations, and parts of a workflow that require judgement.

Do not document an obvious control merely because it exists. Actions such as
rename, download, sort, or switch view usually do not need prose when the
interface already makes them clear.

A concept page is useful when understanding the concept changes how readers
use, configure, extend, or reason about the product. Do not force a real
concept into a procedural guide, and do not create concept pages merely to
explain internal architecture.

Troubleshooting documentation should start from observable symptoms, errors, or
failed tasks and help the reader narrow the cause and recover. Do not organize
it primarily around internal subsystems unless that is how readers can actually
diagnose the problem.

A cookbook is useful when enough standalone, reusable tasks exist to benefit
from being collected as recipes. Do not create a cookbook first and then look
for material to fill it.

A playbook is useful when a real situation calls for a repeatable sequence of
checks, decisions, actions, and verification. Do not rename an ordinary guide
or checklist merely to make it sound more formal.

Reference documentation serves lookup rather than a reading path. Public APIs,
CLI flags, configuration fields, component props, protocol fields, and other
lookup-oriented interfaces may need systematic and exhaustive coverage.

Readers may enter reference directly from search or an agent. Give each entry
enough local context to identify and use the interface, and link to
authoritative cross-cutting guidance instead of repeating it on every entry.

Prefer generated or machine-checked facts where the project provides an
authoritative source.

## Contribution documentation

Contribution documentation should help people find a realistic path from
wanting to contribute to making a contribution the project can accept.

Do not assume contribution means code. Reflect the kinds of contribution the
project actually accepts and route readers to distinct guidance when their
workflows materially differ.

A repository-level CONTRIBUTING file can serve as an entry point rather than a
complete manual. Surface important gates and project-specific expectations
there, then link to authoritative setup, coding, documentation, translation,
bug-reporting, or other guidance instead of duplicating it.

For code contributions, document the project-specific path to a change that can
be reviewed: development setup, relevant validation, generated sources,
conventions, and review expectations where they actually affect the work.

Verify setup and validation commands against the repository and CI rather than
inventing a conventional workflow.

Do not teach generic Git or GitHub usage unless the intended contributors
genuinely need it.

Explain architecture where it changes a contributor's action: where a change
belongs, which boundary must be preserved, or which source is authoritative.
Do not require contributors to read a general architecture tour before making
unrelated changes.

Keep maintainer-only procedures separate when contributors do not need them to
make or validate a contribution.

## Write for the reader

Structure a page around what the reader is trying to understand or do, not
around the shape of the codebase and not around a fixed documentation template.

Do not explain every fact you know. Include a detail when omitting it would
materially affect the reader's understanding, action, decision, or ability to
diagnose a real problem.

Prefer information grounded in actual behaviour, implementation, real use,
bugs, support questions, feedback, and known constraints over generic advice
about how a product of this kind usually works.

When evidence is sparse, write only what the available evidence supports. Do
not invent personas, workflows, recurring problems, historical rationale, or
product maturity to make the documentation feel complete.

Keep implementation details out of user documentation unless the reader needs
them to understand observable behaviour, make a decision, or diagnose a
problem.

Use existing project terminology and ordinary language. Do not promote ordinary
behaviour into a coined concept, named pattern, or artificial category merely
to make the documentation feel more structured.

Use a heading when readers may reasonably want to find or return to that block
independently. Do not manufacture headings merely to break prose into regular
chunks.

Do not make the documentation more certain, complete, stable, or mature than
the product. Make version boundaries, uncertainty, limitations, unsupported
cases, and known rough edges visible where they affect the reader.

Place caveats near the behaviour they qualify when that is where the reader
needs them. Collect limitations together when readers genuinely need to assess
a capability as a whole; do not add a generic limitations section merely as a
closing ritual.

When an example is easy to use in the common case but easy to misinterpret in a
way that affects security, correctness, or data, explain that boundary beside
the example rather than relying on a separate best-practices page.

Do not explain the document before writing the document. Skip introductions
such as "This page covers" or "In this section you will learn" when the title
and first useful paragraph already establish the scope.

Let different pages and different parts of a page take different shapes. Do not
add headings, summaries, examples, FAQs, callouts, or closing sections merely
to make pages structurally consistent.

A real problem may justify a sentence, a local note, a change to an existing
page, a new page, a direct link from the product, or no documentation change at
all.

When a useful detail or workaround is local, let it remain local. Do not
promote every observation into a named concept, general rule, new page, or new
documentation category.

Do not add material merely because it makes the documentation feel complete.

## Choose the form from the information

Choose the representation from the relationship in the information, not from
the components the documentation system makes available.

Do not reach for a specialized form before you can say what it lets the reader
understand or do better than simpler alternatives.

Use prose when relationships between facts matter: cause, consequence,
condition, exception, trade-off, sequence, or experience.

Be cautious with unordered lists. Use one when the reader benefits from
scanning several genuinely parallel items independently. The items should be
the same kind of thing and at roughly the same level.

Do not turn a paragraph into bullets merely because it contains several facts.
If the important information is how facts depend on, qualify, explain, or
follow from one another, preserve that relationship in prose.

Be more cautious with ordered lists. Use one only when the order itself carries
meaning, such as an actual procedure, sequence, or ranking.

Do not number related ideas, recommendations, phases, considerations, or topics
merely to give them structure.

Avoid list items that are only miniature headings followed by a sentence when
ordinary prose would express the same information more naturally.

Use a table when the reader needs to compare or look up the same dimensions
across several things. Do not use a table merely because information can be
made rectangular.

Use a diagram when seeing relationships spatially makes them meaningfully
faster or less ambiguous to understand. Topology, branching, state transitions,
multiple participants, timing, and non-trivial data flow are common reasons.
Do not draw a diagram merely because something happens in a sequence.

Use a screenshot when visual location, appearance, or state is itself useful
information. Do not screenshot text or obvious controls merely to decorate a
procedure. Prefer a live example or durable description when a screenshot would
quickly become stale.

Before using a documentation component, ask what the component itself adds to
the reader's understanding or action.

Use a component when its behaviour matches a real relationship in the
information: choosing between alternatives, switching between equivalent
representations, revealing genuinely optional detail, drawing attention to
information that should stand apart from the normal reading flow, comparing
things, navigating a complex example, or letting the reader inspect or try
something directly.

Do not use components to decorate a page, make it feel more complete, hide weak
organization, duplicate navigation, or impose a relationship that the
information does not actually have.

Do not assume that a component is appropriate merely because the documentation
framework provides it.

A callout is useful when separate visual attention materially helps the reader
notice, interpret, or act on information. Do not add callouts by habit or use
them to compensate for weak page structure.

For visual or interactive APIs such as component libraries, a working demo may
be part of the documentation itself. Show examples that reveal important
appearance, interaction, composition, accessibility, edge cases, or states.
Do not create a demo for every option merely to make the gallery complete.

For HTTP APIs, SDKs, configuration, CLIs, and component libraries, keep
reference facts complete where completeness is useful for lookup. Keep
cross-cutting explanations in guides rather than repeating them on every
reference page.

## When agents are readers

Treat agents as a distinct reader only when they are a real way people use,
integrate with, operate, or modify the product.

First determine what the agent is missing.

If the problem is discovery or retrieval, prefer making authoritative material
directly accessible through stable Markdown, generated reference, indexes, or
other machine-readable forms.

Do not maintain a second hand-written copy of the same knowledge solely for
agents when it can drift from the human-facing source.

A dedicated agent entry point can orient an agent to authoritative sources,
relevant files, tools, and assumptions. Give it enough context to decide what
to read next rather than dumping the whole documentation set into it.

Agent-specific instructions may define constraints that exist because an agent
is acting: what it may inspect, which tools it should use, when it must ask for
approval, how it should handle secrets, and which choices must remain with the
user.

Do not hide product facts, security requirements, compatibility constraints, or
other knowledge that human readers also need only inside prompts or agent
instructions. Keep those facts in an authoritative source shared by both paths.

When reusable agent instructions are the better medium, point the work there
rather than expanding ordinary product documentation to contain them.

If an agent understands the task but cannot operate the product reliably,
consider whether the real fix is a CLI, API, structured output, MCP server, or
another operable interface rather than more documentation.

### Prompts for delegated work

A prompt is useful when delegating the task to an agent is itself a supported
or common way to accomplish the reader's goal.

Treat the prompt as executable instructions, not as another prose explanation
of the surrounding task.

State the outcome the agent is responsible for. Let it discover facts from the
repository, product, and authoritative documentation instead of copying those
facts into the prompt.

When the delegated task changes an existing project, account, configuration, or
other persistent state, tell the agent what existing state it should inspect
and what must be preserved before acting.

Make user-owned decisions and approval boundaries explicit when they actually
matter. The agent should not guess choices that materially affect migration,
security, accounts, data, or product behaviour merely to complete the task.

When useful, tell the agent which tools or authoritative sources to use and how
to verify that the task actually worked.

A prompt may contain operating constraints that exist specifically because an
agent is performing the work. Facts that human readers also need should remain
in normal authoritative documentation.

Do not turn a durable, branching operating procedure into a large copy-paste
prompt. When the same instructions need to be reused, maintained, or composed
with other agent behaviour, prefer a skill, AGENTS.md, or another durable agent
instruction source and let the documentation prompt serve as an entry point.

## Broad documentation work

For project-wide documentation work, inspect the project before deciding the
documentation structure.

Use evidence that actually exists: known readers, observed usage, public
behaviour, interfaces, recurring tasks, support questions, product constraints,
and existing sources.

Do not invent personas, workflows, recurring problems, or a standard
documentation hierarchy to fill gaps in the evidence.

Do not assume that every reader type needs its own section or that every product
subsystem needs a corresponding documentation page.

Navigation and page boundaries should follow information readers actually need.
A sidebar group does not require an index page. A product subsystem does not
require a feature page.

When documentation is being created for an existing project from little or
nothing, discover the information needs first. Do not begin by creating a
complete documentation hierarchy and filling it afterwards.

For broad work where several independent sources need substantial inspection,
subagents may gather bounded evidence in parallel.

Use subagents to investigate concrete sources, not to independently design the
documentation taxonomy or write separate parts of the final documentation.
Keep editorial decisions and the final structure with the main agent.

It is valid for an investigation to find no documentation need.

## Verify the result

Compare changed documentation with the actual product and the sources used to
write it.

Check that commands, paths, names, UI labels, configuration, examples, public
behaviour, version assumptions, and limitations are still true.

Run examples, commands, documentation builds, link checks, schema checks, or
other relevant verification when practical instead of assuming an example is
correct because it looks plausible.

When reference material can be generated or checked against code, schemas,
component metadata, OpenAPI, CLI definitions, or another authoritative source,
prefer that over maintaining duplicate facts by hand.

For substantial documentation changes, dispatch a fresh reviewer.

Give the reviewer the intended reader or task, the documentation change, and
the relevant product or source material. Do not give it the writer's rationale
unless that rationale is itself part of the documentation decision being
reviewed.

Ask the reviewer to report concrete cases where the documentation is inaccurate,
omits information required for the stated reader task, adds content without a
clear reader need, unnecessarily duplicates an authoritative fact, obscures
relationships through its structure or formatting, presents the product or a
decision as more stable or complete than the evidence supports, or contains a
page or section that appears to exist only to complete the documentation
structure.

Do not ask the reviewer for generic suggestions about what else could be
documented. It is valid for it to find nothing.

If a significant unresolved product or documentation decision materially
changes what should be written and cannot be determined from available
evidence, ask the user one question instead of guessing.
