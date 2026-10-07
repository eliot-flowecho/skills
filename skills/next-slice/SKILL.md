---
name: next-slice
description: Choose one next vertical slice to make real without planning the rest of the project.
license: MIT
metadata:
  author: Eliot
  org: FlowEcho
disable-model-invocation: true
---

Choose exactly one next vertical slice from what we currently know and what
already exists.

Read the relevant conversation, spec, and implementation first. What previous
work revealed may change what should come next.

Choose a concrete behaviour or path to make work now. Prefer something we
actually want to use, or something that makes an important part of the current
design meet a real use for the first time.

A slice may cross as many parts of the system as the behaviour requires. Include
the setup, infrastructure, interfaces, storage, UI, and other work needed to make
that path runnable. Do not turn those parts into separate slices merely because
they are separate technical layers.

Do not split the work just to reduce the diff, fit a session, or make the tasks
look smaller. Split it when a smaller path would still produce behaviour we can
run or use on its own.

Take already-known required uses into account when choosing the slice. Do not
make the current path depend on an assumption that one of those known uses
already disproves. Do not plan or implement those later uses yet.

Choose only the current slice. Do not produce later slices, a backlog,
dependency graph, tickets, issues, or a roadmap.

Describe only:
- what will work when this slice is complete;
- how we can try it.

Leave implementation structure to the implementation work unless an existing
decision already constrains it.

If an unresolved product or design question would materially change which slice
should come next, ask me exactly one question instead of choosing. If we need to
see or try something before that question can be answered, say so instead.
