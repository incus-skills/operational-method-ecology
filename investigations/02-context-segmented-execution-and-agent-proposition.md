# Investigation 02 — Agentic segmentation strategy and ChatGPT session emulation

## Status and relationship to the current traversal

This record captures a new operational proposition arising from continued work on the Android Mainline Port translation project.

It does **not** reopen the stopped early-chronology traversal in Pass 1 / Checkpoint 01. That traversal stopped because its proposed next hop failed adequacy. This is a distinct investigative movement prompted by a later operational concern: repeated context loading during single-file work.

The arrangement below is a candidate implementation and an object for observation, not an established invariant or a completed method specification.

## Reference strategy and separate ChatGPT emulation

A distinction established during this investigation changes how the work below must be read.

The agentic segmentation strategy described here is the **existing harness-oriented proposition** under investigation. Its definitions and principles are the reference. The current ChatGPT work is a separate experimental enactment of those principles through independent chat-interface sessions, using the project repository as the shared durable surface and a single GitHub access definition.

The ChatGPT enactment is not a replacement for, merger with, or proposed successor to the existing harness strategy. Nor is it a claim that the chat interface reproduces the harness faithfully. It is an experiment in whether the strategy's principles can be enacted in this different execution environment, what adaptations the environment forces, and what those adaptations reveal about the strategy.

The intended experimental arrangement is deliberately modest:

- a clean orchestrator chat enters through a project-held orchestrator prompt and repository ingress;
- it reconstructs the current project position and prepares a bounded, durable job in the repository;
- a separate clean worker chat enters through a short worker ingress, uses the shared GitHub access definition, discovers its assigned job and performs only that operation;
- the worker returns a reconstructable handoff and, where the job requires code changes and the available permissions support it, publishes the changes for integration;
- a separate orchestrator session integrates and adjudicates the result against the project constraints.

The exact prompts, job discovery mechanism and publication path remain experimental details to be tested, not architecture already proven by their description. The repository is the shared continuity and evidence surface; the chat sessions do not inherit one another's conversational context.

Pass identifiers may be recorded in repository jobs and handoffs as **accounting and provenance**: they make it possible to identify which experimental traversal produced a result and to compare successive traversals. This is not an importation of the Android translation project's Pass 1/2/3 methodology, and it does not merge the experimental accounting with the translation passes or with the separate OE investigation traversal.

The experiment asks whether the arrangement improves bounded-session context consumption while preserving reconstructability and work quality. Relevant observations include per-session context use, total context and coordination cost across all sessions, quality of orchestrator reconstruction, whether a worker can act from the job without conversation history, boundary discipline, handoff sufficiency, integration effort and continuity across successive sessions. Reduced context in one session is not evidence of overall efficiency if the cost has merely moved to another session. No quantitative improvement should be claimed without measurements.

### Evidence boundary of the current trial

The first cold-start exercise reconstructed the orchestrator position from repository ingress in a clean chat. It then prepared a worker task prompt manually in the originating conversation. A separate worker chat executed that prompt and returned a handoff identifying one source/target discrepancy.

This establishes some useful evidence about clean-session reconstruction and bounded worker execution. It does **not** yet test the full intended emulation: the clean orchestrator did not itself generate and persist the job; the worker did not enter through a project-held one-line ingress and independently discover/claim that job; and the complete job-to-integration cycle was not exercised as a repository-mediated sequence. The trial therefore does not yet validate the proposed session arrangement or demonstrate context savings.

## Prompting observation

A translation session can appear to make modest visible progress while consuming substantial context. Repository retrieval, source material, tool output, reconstruction reports and accumulated continuation state all contribute to the active context.

The operational question is whether every file-level operation needs to reload or retain the entire repository and the full history of prior work.

The proposed separation is:

- preserve the project-wide position once in a small coordinating context;
- give each bounded operation only the source, target and constraints it needs;
- return a reconstructable handoff;
- integrate results against selected wider constraints rather than reloading everything by default.

The aim is not to reduce preservation. It is to separate preserved evidence from the subset that must be active during a particular operation.

## Candidate responsibility arrangement

### 1. Thin orchestrator

Maintains project control state:

- current project, pass, scope and observer position;
- checkpoint and next adequate hop;
- global constraints and exclusions;
- dependencies, decisions and unresolved matters;
- task assignment and integration state.

It routes work and maintains continuity. It should not reproduce the detailed reasoning of every worker or keep the full repository active by default.

### 2. Bounded workers

Receive an explicit task packet with input and output boundaries. A worker may perform one of several bounded capabilities:

- **Delta observation:** identify what changed in a specified source or evidence set.
- **Reconstruction:** recover the structure, distinctions and relationships needed for a defined question.
- **Translation or transformation:** perform a bounded source-to-target transformation.
- **Review:** assess a candidate result against explicit criteria.

These are task capabilities, not necessarily permanent agent identities, profiles or a fixed hierarchy. One runtime may instantiate them as separate agents; another may use fresh sessions, subprocesses, tools or sequential role changes.

### 3. Integration and adjudication

The orchestrator checks the result against the relevant project-wide constraints and decides whether to accept it, request a bounded correction, acquire additional evidence, or stop because the next hop is inadequate.

Where a genuinely independent review is needed, it should be assigned a separate observer position rather than silently folded into the worker's self-assessment.

### 4. Durable preservation and coordination

The repository remains the authoritative preservation surface for source material, accepted outputs, provenance, decisions and reconstructive records.

A task board or Kanban system may coordinate status, ownership, dependencies and human gates. It is a coordination surface, not the provenance authority. In particular, a local or single-host board must not become the only record of work.

## Runtime-independent handoff contract

Every worker task should specify:

- **Identity:** task ID, project, pass/checkpoint and assigned capability.
- **Input boundary:** exact files, revisions, evidence and permitted context.
- **Observer position:** what question is being asked and from which position.
- **Output boundary:** expected artifact or finding, allowed modifications and format.
- **Constraints:** governing distinctions, invariants, exclusions and authorization limits.
- **Validation:** evidence and checks required to support the result.
- **Stop conditions:** missing evidence, inadequate next hop, repeated failure, scope conflict, timeout or human decision required.
- **Handoff:** observations, decisions, unresolved questions, validation, changed files and next dependency.

The handoff must preserve enough to reconstruct the operation without requiring the next worker to inherit the previous worker's entire context. The actual artifacts and diffs remain available as evidence; the handoff does not replace them.

## Context is loaded by need

A useful provisional distinction is:

| Context band | Function | Typical lifetime |
|---|---|---|
| Project control | Position, scope, pass, next hop and global constraints | Orchestrator lifetime |
| Task contract | Inputs, outputs, observer position, validation and stop conditions | One task |
| Local evidence | Exact files and direct dependencies | One bounded operation |
| Integration evidence | Wider relationships, indexes, cross-file effects and acceptance constraints | Loaded when needed |
| Durable provenance | Accepted artifacts, diffs, decisions, unresolved matters and handoffs | Repository lifetime |

A worker should not infer that omitted context is irrelevant. It should request the missing dependency or stop when adequacy cannot be established.

Context isolation must be real if the goal is to reduce active-window consumption: merely describing a worker as isolated while running it in the same accumulated conversation does not unload prior context. Separate contexts or processes can provide that isolation; a single conversational session can only approximate it through disciplined scoping.

## Extension to the harness-agnostic agent proposition

The proposition should be specified first as a runtime-independent execution architecture, not as a Hermes configuration.

The architecture has these separable concerns:

1. **Control and routing:** a thin orchestrating capacity that assigns bounded tasks and maintains the active project position.
2. **Specialist execution:** replaceable worker instantiations that perform delta observation, reconstruction, translation/transformation or review.
3. **Relational continuity:** explicit contracts connecting the task, observer position, inputs, outputs, constraints and handoff.
4. **Durable coordination:** a task/dependency state that can be represented by Kanban or another coordination mechanism.
5. **Authoritative preservation:** repository records and artifacts from which work can be reconstructed independently of the runtime.
6. **External observation and human authority:** independent review and user decision gates where required; the orchestrator must not become the sole judge of its own completeness or authorization.

### Hermes as one possible harness

Hermes may be evaluated as one implementation of the execution capabilities: delegation, worker execution, routing, task coordination and tool access. Its actual capabilities and limitations must be verified against the specific version and deployment before relying on them.

The architecture must not depend on Hermes-specific profiles, board semantics, memory facilities or delegation APIs. Those belong in an adapter or deployment profile, not in the task contract or method definition.

The proposition should start with a flat routing arrangement if the chosen harness cannot reliably route between differentiated worker profiles. That is an implementation constraint to verify, not a universal architectural requirement. A harness that supports deeper routing may use it, provided the same boundaries and provenance rules remain intact.

### Do not conflate the orchestrator with Hermes continuity

The earlier Hermes continuity specification is a separate relational specification:

- (A): invariant anchor;
- (P_{gen}): generative-position specification;
- (P_{obs}): observational-position specification;
- (R): relational constraints/interface;
- (O_{spec}): constrainedly revisable object-maintenance specification.

That specification is not synonymous with a main agent, orchestrator, runtime or worker. Agents are replaceable instantiations. The thin orchestrator is one possible generative/control position within an execution arrangement; it does not replace the invariant anchor or the independent observational position.

The external observer must remain temporally independent of the generative cadence where the continuity specification requires it. A worker's self-review or the orchestrator's integration check must not silently stand in for that external adjudication.

## Candidate operational flow

1. Establish the project position and external constraints in the orchestrator.
2. Identify the next task whose inputs and purpose can be bounded.
3. Dispatch a worker with exact inputs, observer position, permitted outputs and stop conditions.
4. Worker performs only the assigned operation and returns a reconstructable handoff.
5. Integrate the artifact and inspect only the wider dependencies implicated by the change.
6. Preserve the accepted result, provenance and updated task state in durable records.
7. Determine whether the next hop is adequate; stop if it is not.
8. Re-enter from a preserved sufficient position when another traversal is warranted.
9. Adjudicate completeness separately from the active traversal, from the external observer position in relation to the external anchor.

This is a candidate flow for testing, not a prescribed universal sequence.

## Distinctions to preserve during investigation

- Repository preservation is not active context loading.
- A task board is not authoritative provenance.
- A worker handoff is not the underlying evidence.
- A bounded task is not necessarily a separate permanent agent.
- An orchestrator is not the whole method or the external observer.
- Runtime capability is not runtime-independent architecture.
- Context scoping in one conversation is not genuine context isolation.
- Integration checking is not automatically external completeness adjudication.
- A flat routing topology may be a harness constraint, not a methodological invariant.
- The translation project is the initial test terrain, not proof of universal transferability.

## Open questions

- Which parts of the handoff contract are necessary across all task types, and which are task-specific?
- What is the smallest project-control state that still permits reliable re-entry?
- How much context can be withheld before workers begin missing consequential dependencies?
- Which integration checks can be selective, and which require a whole-scope reconciliation?
- How should a worker expose a dependency without recursively pulling the entire repository into its context?
- What evidence demonstrates that a new worker can reconstruct the required position from repository records and a handoff alone?
- Which capabilities are available in a concrete Hermes deployment, and which require adapters or other services?
- Does the arrangement preserve an independent observational position, or does coordination become self-validating?
- Does this arrangement transfer to another terrain without importing translation-specific assumptions?

## Investigative disposition

Treat this as a candidate architecture and continue observing it through actual translation work. Do not promote it to a general method, fixed agent hierarchy or universal invariant until repeated enactment and reconstruction from independent observer positions support that compression.
