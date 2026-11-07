# Investigation 03 — Context-segmented execution: development through repository-mediated enactment

## Status and relationship to prior investigations

This record reconstructs the development of the ChatGPT-session emulation of context-segmented execution after the initial trial described in [Investigation 02](02-context-segmented-execution-and-agent-proposition.md).

It is a separate investigative movement. It does **not** reopen the stopped early-chronology traversal in Pass 1 / Checkpoint 01, replace Investigation 02, or establish that the candidate arrangement is a universal procedure.

The primary terrain remains the Android Mainline Port translation project, specifically the `translation/english-reconstruction` branch. This record distinguishes:

- the harness-oriented agentic segmentation strategy, which remains the reference proposition;
- the ChatGPT-session arrangement, which is an experimental enactment in a different execution environment;
- the repository records that prescribe or preserve the arrangement;
- the enactments and acceptance decisions evidenced by task records and checkpoints;
- the effects that remain unmeasured or untested.

## Evidence position

The reconstruction below is grounded in the following Android repository records:

| Evidence | Revision / position | Evidential role |
|---|---|---|
| `translation/EXECUTION-SEGMENTATION.md` | blob `05ee569421b89366bbc0993afe62cb22a0644913` | Candidate execution arrangement, context bands, eight-field handoff and evaluation questions |
| `translation/ORCHESTRATOR-INGRESS.md` | blob `b96894ce5734d79be4fe2df2c4c7174a7057df8b` | Orchestrator reconstruction, task preparation, independent acceptance and continuity reconciliation |
| `translation/WORKER-INGRESS.md` | blob `774db08a06b5b27d89a43e709f3944981afcea82` | Independent worker entry, task discovery/selection, evidence boundary, stop conditions and handoff |
| `reconstruction/zh/continuation/current-position.md` | blob `585104c2fe13c30e896b6b73591c7002d92b5ebf` | Current project position and accepted task sequence through Task 016 |
| Pass 4 / Checkpoint 11 | blob `7dd2a73bb365a047ffa067f99fd3e01f9618f12b`; records branch head `bf4d779bf4f583067cb6227a6b124798b2f452e2` | Independent orchestrator acceptance of Task 016 and explicit limits on what acceptance establishes |
| Task 016 completed record | blob `48ef17afd35227846c0a107992102e25cf5befef` | Detailed worker stop, orchestrator re-authorization, execution handoff and provenance |
| Task 013 completed record | blob `d566e425ba34ec7092193d2805876e644597e8f3` | Example of a bounded cross-document read-only operation and eight-field handoff |
| Task 011 completed record | blob `502f6da88d98fa3f22518b8511b7c3aaf19bacce` | Example of a deliberately incomplete representative workflow scenario and bounded assessment |

The branch head recorded by Checkpoint 11 is the evidence snapshot used for this reconstruction. Later changes to the Android branch may alter its current position; this record does not claim to be a live mirror of that project.

## Development from the initial trial

Investigation 02 recorded a first cold-start exercise with a limited result:

- a clean orchestrator session reconstructed its position from repository ingress;
- it prepared a worker task prompt manually in the originating conversation;
- a separate worker session executed that prompt and returned a handoff;
- the orchestrator did not itself persist the job;
- the worker did not independently enter through repository ingress and discover/select a persisted task;
- the complete repository-mediated task-to-integration cycle was not exercised.

That first exercise supported only clean-session orchestrator reconstruction and bounded worker execution. It did not validate the proposed end-to-end arrangement.

The later repository records show a more developed operational arrangement. The change is not simply a more detailed description of the original proposal: the task sequence and checkpoints preserve repeated bounded operations, worker completion records and separate orchestrator acceptance decisions.

## Observed operational arrangement

### 1. Separate entry surfaces

The project now has distinct ingress records for the coordinating session and the worker session.

The orchestrator ingress directs a fresh session to reconstruct the current project position from repository records, follow the current reading sequence, verify revisions, identify the next supportable operation and prepare a durable bounded task. It explicitly prohibits the orchestrator from performing the worker's file-level operation or dispatching a worker from the same session.

The worker ingress directs an independent session to read the execution contract, inspect pending task records, select one available task, verify its evidence pins and execute only within that task's boundary. It prohibits reliance on the originating conversation and prevents the worker from changing project-level continuity.

This is a concrete separation of entry and responsibility in the ChatGPT enactment. It remains an environment-specific implementation of the broader proposition, not proof that every runtime must use Markdown ingress files or chat sessions.

### 2. Durable task boundary and evidence pins

The task records specify identity, purpose, observer position, exact input paths and revisions, permitted changes, constraints, validation, stop conditions and the expected handoff.

Revision pins are operational controls, not merely descriptive references. Task 016 preserves an actual instance in which the task's current-position pin became stale after the orchestrator advanced the checkpoint. The worker stopped before substantive execution. The orchestrator independently reconstructed the mismatch, identified its own sequencing error, explicitly re-authorized the task against the new position, and required a fresh worker session to verify all pins again.

This event provides evidence for a particular stop-and-reconciliation movement:

1. worker detects a mismatch against the task's declared evidence boundary;
2. worker stops rather than silently substituting a newer revision;
3. worker records the stop and its evidence;
4. orchestrator reconstructs the discrepancy independently;
5. orchestrator explicitly re-authorizes the corrected position;
6. worker restarts from a fresh ingress and re-verifies the pins.

The event does not establish that revision pinning prevents every form of drift. It demonstrates that the mechanism was used to expose and contain one concrete position mismatch.

### 3. Bounded execution and reconstructable handoff

The execution contract specifies an eight-field handoff:

1. task identity;
2. observer position;
3. observations;
4. decisions;
5. unresolved matters;
6. validation;
7. change boundary;
8. next dependency.

The handoff is required to be concise but reconstructable. It does not replace the underlying artifacts, diffs or source evidence.

The completed Task 013 and Task 016 records demonstrate use of this contract for different bounded operations: a read-only cross-document review and a documentation change. Task 011 supplies another bounded example, using an incomplete hypothetical device request to test whether a workflow can identify missing evidence without inventing device facts.

These examples show that the task boundary was used for more than one task type. They do not establish that the same contract is optimal or sufficient for every capability.

### 4. Separate worker completion and orchestrator acceptance

The records distinguish worker execution completion from acceptance.

A worker appends its handoff and moves the task record to the completed directory. That movement records execution only. The orchestrator must then retrieve the task, verify the evidence revisions, compare the handoff with the actual artifacts and changes, and record one of three dispositions:

- **ACCEPTED** — the bounded operation is sufficiently evidenced and suitable for integration within its stated boundary;
- **REJECTED** — a material defect or boundary violation prevents acceptance;
- **UNRESOLVED** — evidence is incomplete, conflicting or inadequate to decide.

Only an accepted operation is incorporated into accepted project continuity. The orchestrator then creates a new checkpoint, advances the current-position record and reconciles other position-bearing records where required. Historical checkpoints remain unchanged.

The current-position record and Checkpoint 11 report Tasks 008–016 as independently accepted within their recorded boundaries. Checkpoint 11 also makes clear that these acceptances do not establish Pass 4 completion, runtime installation, skill activation, representative workflow success or context-segmentation effectiveness.

This is stronger evidence of repeated enactment than the first cold-start trial. It is still evidence of operation within one project and one experimental environment, not evidence of universal transferability.

### 5. Lightweight coordination rather than a scheduler

The worker ingress specifies that only one worker should select and execute work at a time for the initial trial. It explicitly says not to add a claim or locking mechanism, not to infer priority or strict execution order from task numbering, and to record a collision if concurrent selection occurs.

The orchestrator ingress similarly describes a lightweight sequence of numbered Markdown task records and prohibits expanding it into a scheduler, board, formal task schema or assignment system without evidence of need.

Thus repository-mediated task discovery and durable task records are now specified and used, but concurrency control is deliberately absent. The arrangement should not be described as a multi-worker scheduling system.

## What has become more explicit through enactment

Comparison with Investigation 02 reveals several distinctions that have become operationally consequential:

- **Position reconstruction versus task execution:** successfully reconstructing the orchestrator position does not establish that a worker can independently reconstruct and execute a bounded task.
- **Task preparation versus dispatch:** a durable task record is the shared work boundary; the orchestrator does not carry out the worker operation in the same session.
- **Worker completion versus acceptance:** moving a task to `completed/` is not acceptance.
- **Evidence pin versus remembered position:** the worker verifies the task's declared revisions; a mismatch is a stop condition, not permission to infer a replacement.
- **Acceptance versus continuity integration:** accepted work is incorporated only after independent reconstruction; continuity records are reconciled as a separate operation.
- **Task sequence versus scheduling policy:** numbering provides identity and provenance, not priority, ownership, locking or execution order.
- **Handoff versus evidence:** the handoff supports reconstruction but does not replace artifacts, diffs or source evidence.
- **Integration acceptance versus external completeness:** orchestrator acceptance is bounded to a task and does not establish whole-pass or project completeness.

These are observed distinctions in the current enactment and its records. Their recurrence and transferability remain open.

## Limits and unresolved evidence

The available records do not establish:

- quantitative context consumption before and after segmentation;
- total context and coordination cost across orchestrator and worker sessions;
- a controlled comparison with an equivalent unsegmented workflow;
- whether bounded workers consistently identify all consequential omitted dependencies;
- how the arrangement behaves under concurrent task selection;
- whether a task can always be independently discovered and reconstructed from repository state without any conversational assistance;
- whether the eight-field handoff is sufficient for all task types;
- whether selective integration preserves whole-project coherence at acceptable cost;
- whether the arrangement transfers to another project, runtime or harness without material adaptation.

The Android project records explicitly retain context segmentation as an arrangement whose effects remain to be observed. Accepted task operations are not measurements of context savings.

The current arrangement also contains a known non-authoritative stale paragraph in `translation/EXECUTION-SEGMENTATION.md` that still names an earlier Pass 3 position. The current-position record and active checkpoint are identified as position authority; the stale paragraph is preserved as an unresolved documentation discrepancy rather than silently treated as current.

## Investigative disposition

The later Android records establish that the ChatGPT-session experiment has moved beyond the initial manually prepared worker-prompt trial. A repository-mediated task sequence, distinct orchestrator and worker ingress, evidence-pinned task packets, bounded worker handoffs, independent acceptance and continuity reconciliation are now represented in the operational records and have been used across multiple bounded operations.

The evidence supports recording this as a developed experimental enactment. It does not support promoting the arrangement to a stable general method, claiming context savings, or declaring the harness-oriented proposition validated.

The next investigative movement should compare further enactments and, where available, actual context/coordination observations against the open questions above. Any such comparison must preserve the distinction between the harness-oriented reference strategy and its ChatGPT-specific enactment.

The Pass 1 early-chronology traversal remains stopped because its proposed next hop failed adequacy. This investigation does not supply the missing primary evidence for that chronology and does not alter that stop.
