---
name: agent-admin
description: Use by @agent-admin when handling Buzz requests to create or change agents, runtimes, skills, MCP capabilities, secrets, SSH access, or resource assignments.
---

Treat a capability request as a description of need, not as authorization for
every configuration change that could satisfy it.

Read the relevant current configuration, assignments, active work, and
environment policy before changing anything.

Choose the smallest change that provides the needed capability with the
narrowest useful scope and duration.

Distinguish configuration that has been recorded from capability that is
actually usable by the intended agent.

Never request, expose, or repeat secret values in Buzz.

## Understand the requested capability

Determine the outcome the requester needs, not only the mechanism they happened
to suggest.

If the capability already exists and is correctly assigned, use the existing
resource instead of creating a duplicate.

Fix the layer that actually owns the problem.

If an agent lacks an MCP assignment, fix the assignment rather than changing
its instructions to work around the missing tool.

If the runtime is materially mismatched to the task, change the runtime when
appropriate rather than installing unrelated skills to imitate the missing
capability.

If authorization is missing, request authorization rather than weakening the
access boundary.

Do not turn a simple capability request into a configuration interview.

Ask only for information that cannot be derived from the environment and
materially changes the operation.

## Check authority, scope, and duration

A request from an agent or human establishes the desired outcome. It does not
automatically authorize broader access.

Check whether the requested access and scope are permitted by environment
policy and the requester's role.

When approval is required, obtain it before granting the capability.

Choose the narrowest useful scope.

Distinguish:

- a capability needed for the current task or worker;
- a project-level assignment;
- a durable change to the agent's default configuration;
- a shared or global resource.

Do not turn a temporary runtime, model, reasoning, access, or tool request into
a permanent default unless that is what was requested or decided.

Do not make a resource global merely because one agent needs it.

When a temporary change has an expected end, make that boundary visible.

## Preserve agent identity

Treat the named Buzz agent as the persistent identity.

Changing harness, model, reasoning effort, worker, skills, MCP assignments, or
other runtime configuration does not create a new agent unless a new identity
was requested.

Preserve unrelated configuration when changing one capability.

Do not recreate an agent merely to modify something that can be reassigned or
updated directly.

Keep worker replacement out of the team-facing explanation unless it affects
when the requested capability becomes usable.

## Keep resource boundaries clear

Keep agent identity, runtime configuration, skills, external tools,
authentication, and agent assignments conceptually separate.

Change the resource that is actually wrong instead of compensating in another
layer.

Do not encode a missing platform capability into an agent prompt when the
platform can provide it directly.

Do not create nearly identical copies of shared resources when the existing
resource can be assigned or updated safely.

Preserve configuration unrelated to the requested change.

## Manage runtimes as executable capabilities

Use the platform's runtime-management path to create, update, test, and remove
runtimes.

When adding or changing a runtime, verify that its executable and required
configuration are available and that it can establish the expected agent
protocol before assigning it.

Do not report a runtime as ready merely because its configuration was saved.

When changing a runtime used by an active agent, preserve the Buzz identity and
apply the change at a safe worker or session boundary unless the requester is
blocked on the change.

## Manage skills with provenance

Use the platform's existing skill package-management path rather than creating a
parallel installation model.

When installing from a repository, identify the actual skill or skills needed
instead of treating the repository itself as one skill.

Preserve enough provenance to understand and update the installation later,
including its source and selected skill, and revision or version when the
platform provides one.

Respect assignment scope.

Use project-scoped assignment for project-specific behavior.

Use shared or global assignment only when the behavior is intentionally meant
to apply that broadly.

Use the existing package-management update mechanism for installed skills
rather than manually replacing the installation from its source repository.

When updating a skill, preserve intentional pins or local modifications unless
the request explicitly replaces them.

Do not call the operation complete until the intended agent can actually receive
the skill in the environment where it will run.

## Manage external capabilities and authentication separately

Treat an external capability, its connection definition, its authentication,
and its assignment to agents as separate concerns.

This applies whether the capability is provided through a local MCP server,
remote MCP server, or another managed external tool.

Creating or updating the external resource does not imply that every agent
should receive it.

Assign it only to the agents and scope that require it.

Use the authentication mechanism the resource requires, including managed OAuth
or managed credential bindings when applicable.

Do not embed credentials into Buzz messages, agent prompts, skill files, or
connection configuration that is intended to be non-secret.

Do not create a duplicate external resource merely because an existing one is
missing an assignment or authentication binding.

## Keep secrets outside the conversation

Secrets are managed values, not chat content.

When an API key, password, private key, bearer token, or other secret is
required, create or identify the appropriate secret slot and trigger the
platform's secure HTTP input flow.

For OAuth, start the authorization flow and tell the human what action is
required.

Do not ask the human to paste the value into Buzz.

A secret may be shared by multiple managed resources.

Reuse an existing secret when appropriate instead of creating duplicate secret
values for each binding.

Bind a completed secret or authorization only where it is required.

When required, a managed secret may be exposed to an assigned worker as a named
environment variable. Treat that as granting the agent access to the secret
value.

Replacing a secret changes future injections of that secret. An active worker
continues using the value it received when its environment was created.

Do not restart an active worker solely to replace a credential it already
received unless the current work specifically requires the new value.

Refuse to delete a secret while any managed resource still references it.
Remove or replace those bindings first.

Do not reveal stored secret values when reporting configuration.

If a secret is accidentally posted in Buzz, do not repeat it or import it from
the message. Handle the exposure according to the team's security practice and
use the secure replacement path.

## Manage SSH access explicitly

Treat an SSH target as an explicit access capability, not ambient environment
configuration.

Assign each target only to the agents allowed to use it.

Keep SSH credentials in managed secret bindings rather than Buzz messages or
agent instructions.

Do not silently accept an unknown or changed host key.

When the environment requires trust confirmation, provide the target identity
and fingerprint to the human in Buzz and wait for explicit confirmation there.

Treat a changed known host key as a security event rather than a routine
reconnect failure.

Use only the SSH fields and connection model supported by the managed
environment.

Do not add arbitrary OpenSSH options or construct custom SSH configuration as a
workaround for unsupported behaviour.

## Distinguish configured from usable

A resource that exists is not necessarily usable.

A requested capability may still be waiting for:

- assignment to the intended agent;
- authentication or OAuth;
- secure secret input;
- approval;
- SSH host-key confirmation;
- worker or harness restart;
- the next runtime session.

Do not report the request as complete while one of these conditions still
prevents use.

Verify usability for the intended agent when practical.

If the change will only affect a future worker or session, say so.

## Apply changes around active work

Determine whether a configuration change can take effect without disturbing
current work.

Do not restart or replace active execution merely because the new configuration
could be applied immediately.

If the requesting agent is blocked specifically on the capability, apply it at
the earliest safe point.

If current work can finish without the change, prefer a later safe transition
when that avoids unnecessary interruption.

Tell the requester when the capability actually becomes available.

## Remove and revoke carefully

Before removing, replacing, or unassigning a capability, inspect who depends on
it and whether active work is using it.

Do not revoke a skill, external tool, secret binding, SSH target, runtime
capability, or other assignment from active work without a reason to interrupt
that work.

When replacing a resource, avoid leaving the agent in an unusable intermediate
state.

Do not remove a shared resource merely because one requester no longer needs
it.

Keep the scope of revocation aligned with the scope of the access being removed.

## Request human input only where required

Ask for human input when the platform cannot safely complete the operation
without it.

Typical cases include secret entry, OAuth authorization, SSH host-key
confirmation, or an access decision reserved for a human.

Explain the exact action needed and why the request is waiting.

Do not ask for unrelated configuration choices.

Use the secure HTTP input path only for secret entry and OAuth authorization.

Keep SSH host-key confirmation and other non-secret human decisions in the
shared Buzz conversation.

Keep pending operations resumable so the requester does not need to restate the
whole request after the human step completes.

## Return the usable result

When the operation completes, tell the requester what capability changed, its
scope, and when it is usable.

Report the result rather than narrating the administrative procedure.

Include source, assignment, duration, or other provenance when it matters to
future maintenance.

Do not dump internal configuration, raw management output, credentials, or
implementation details merely to prove the operation happened.

If the request is still waiting on authorization, authentication, confirmation,
or a safe restart, report that pending state instead of calling it complete.

If the requested change could not be performed, state the actual blocker and
the next input or decision required.

When another agent requested the change, return the result in the shared Buzz
conversation so that agent knows whether it can continue.
