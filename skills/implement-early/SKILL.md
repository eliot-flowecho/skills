---
name: implement-early
description: Implement decided work while allowing implementation to reveal when the current design no longer holds.
license: MIT
metadata:
  author: Eliot
  org: FlowEcho
disable-model-invocation: true
---

Implement the work described by the user, the current conversation, or the
current spec.

Follow decisions that have already been made. Do not continuously reopen the
design while coding.

Use the project's existing test and check workflow. Use TDD when the behaviour
and the boundary being tested are already clear, or when the user asks for it.
Run relevant tests and typechecking while working.

Fix ordinary type errors normally.

Do not use type gymnastics or type-checker escape hatches merely to preserve the
current interface or implementation. If the runtime behaviour is simple but
making it typecheck starts requiring increasingly indirect conditional types,
nested generics, overloads, wrapper types, casts, `any`, `unknown`, ignores, or
similar machinery, inspect whether the interface or data model is the actual
mismatch.

Complex types are fine when they represent real distinctions in the behaviour
or domain. A local escape hatch is also fine for a genuine mismatch outside our
control; keep the reason local and explicit.

If the work fits the current decisions, continue.

Stop and ask me exactly one question if continuing requires you to:
- contradict a decision we already made;
- make a significant decision that has not actually been made;
- substantially widen the requested work.

Do not silently resolve such a conflict by redesigning the surrounding system.

Local, reversible implementation choices can be made normally. Imperfection,
duplication, or an opportunity to refactor is not by itself a reason to stop.

Once the requested behaviour works and the relevant checks have been run,
dispatch a fresh subagent to review the change.

Give the reviewer the requested behaviour or current spec and the diff. Do not
give it the implementation agent's rationale unless that rationale is itself
part of a decision being reviewed.

Ask the reviewer to report only concrete cases where:
- the requested behaviour is missing, partial, or implemented incorrectly;
- an earlier assumption or decision turned out not to hold;
- the implementation had to work around something it was expected to use;
- the implementation introduced a significant decision that was never made;
- the change added behaviour or machinery beyond what the work required;
- type-level complexity or an escape hatch appears to compensate for a
  mismatched design rather than represent real behaviour.

Each finding must point to concrete code and, where applicable, the requirement
or earlier decision it conflicts with. It is valid to find nothing.

Do not report generic cleanup, abstract code smells, duplication, possible
refactors, new abstractions, or new terminology unless they cause one of the
problems above.

Bring the findings back to me. Fix straightforward correctness problems.
If a finding requires product or design judgement, discuss it with me one
question at a time.
