---
name: revisit
description: Revisit earlier decisions after real implementation or use has given us new information.
license: MIT
metadata:
  author: Eliot
  org: FlowEcho
disable-model-invocation: true
---

Review the period of work or use I point you at.

Base the review on concrete material: implementations, actual use, bugs,
workarounds, feedback, logs, and the earlier decisions or assumptions they bear
on.

Before saying that experience changed an assumption or decision, find where
that assumption or decision actually came from. If you cannot find one, report
the observation without inventing a previous expectation.

Look for things that actual implementation or use now gives us a reason to
reconsider.

This may include:
- different real uses running into the same workaround or awkwardness;
- a new real use that does not fit something earlier uses made look reasonable;
- something we expected to stay separate repeatedly needing to be handled
  together, or the reverse;
- something treated as stable that real work keeps changing;
- functionality or machinery that real use consistently avoids or works around.

Count distinct real cases, not the number of commits, tickets, comments,
reviews, or generated artifacts describing the same case.

Do not search for findings merely to fill these categories. It is valid for a
review to find nothing worth reconsidering.

For every finding, point to the concrete cases and the earlier decision or
assumption it bears on, when one exists. Explain why it matters for work we are
actually doing.

Do not infer that repetition requires an abstraction, that lack of change means
an interface is stable, or that an awkward case should become a general
capability.

Do not redesign the system yet. Bring back only the things that now deserve
another look.

Use the user's words, existing project terminology, and plain descriptions.
Do not invent names for the patterns you find.

If deciding what to do about a finding requires my judgement, discuss it with
me one question at a time.
