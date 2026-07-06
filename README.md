# DeSU

![DeSU logo](desu.svg)

**DeSU** is a prompt for generating **Dense Semantic Units (DSUs)**.

A **Dense Semantic Unit** is a dense, language-based representation of **consequential resultant state**, designed for direct interpretation by capable LLMs.

```text
DeSU(input context) -> DSU
```

DeSU does not primarily preserve a compressed account of what happened.

It attempts to consolidate what remains semantically in force.

```text
history = what happened
DSU = what remains in force
```

## Prompt

The generator prompt is ![desu.txt](desu.txt)

And it's also DSU by itself.

## Why

Long interactions accumulate more than current state.

They may contain:

* exploration;
* repetition;
* temporary hypotheses;
* corrections;
* abandoned branches;
* superseded decisions;
* resolved questions;
* obsolete assumptions;
* intermediate reasoning.

Some of that material may remain historically useful while no longer being necessary for continued inference.

DeSU attempts to consolidate the resultant state instead of preserving the full path that produced it.

Example:

```text
A was proposed.
B was explored.
A was reconsidered.
C was tested and rejected.
E was adopted.
```

A history-oriented representation may preserve that sequence.

A DSU may simply represent:

```text
type:context;protocol:context_only;content:state:E
```

If additional information remains consequential:

```text
type:context;protocol:context_only;content:state:E,constraint:X,dependency:Y unresolved
```

The distinction is intentional.

## DeSU and Compaction

DeSU is not defined in opposition to compaction.

Compaction is a broad operation:

```text
context -> smaller representation
```

What the smaller representation preserves depends on the implementation.

A compaction system may target:

* trajectory;
* current state;
* task continuity;
* selected evidence;
* unresolved work;
* a handoff checkpoint;
* another implementation-defined representation.

It may also produce a DSU.

DeSU is narrower and more explicit about its target:

```text
context
-> consequential resultant state
-> dense language-based DSU
```

Therefore:

```text
compaction = broad reduction operation
DSU = specific representational target and portable artifact
DeSU = one prompt-based DSU generator
```

The distinction is not that compaction must preserve history while a DSU preserves state.

That depends on the compaction implementation.

The distinction is that a DSU explicitly targets what remains consequentially in force and materializes it as a dense language-based checkpoint for direct reuse by capable LLMs.

Raw history, compacted context, retrieval systems, artifacts, logs, and DSUs may coexist.

## What DeSU Preserves

Depending on the input, a DSU may preserve:

* effective decisions;
* active constraints;
* prohibitions;
* critical negation;
* objectives;
* active relations;
* unresolved questions;
* unresolved dependencies;
* uncertainty;
* conflict;
* relevant temporal conditions;
* supported state transitions;
* operational facts;
* exact paths, URLs, IDs, filenames, code symbols, acronyms, and other consequential literals.

## What DeSU May Remove

A DSU may omit material that no longer affects continuation, including:

* filler;
* politeness;
* rhetoric;
* repetition;
* redundant support;
* obsolete exploration;
* superseded branches;
* resolved discussion;
* reconstructible narrative;
* low-impact examples;
* unnecessary source order;
* intermediate reasoning whose role has already been absorbed into the resulting state.

The output is deliberately lossy.

## Core Behavior

DeSU interprets the complete input semantically rather than shortening fragments independently.

It may:

* deduplicate equivalent information;
* merge complementary information;
* reorganize content by semantic relation;
* preserve effective state across long interaction;
* revise state when supported change occurs;
* preserve uncertainty when conflict cannot be resolved;
* omit obsolete inferential residue.

Important distinctions include:

```text
exploration != adoption
repetition != validation
volume != commitment
recency != centrality
prior consolidation != truth
```

The goal is not to preserve every statement.

The goal is to preserve the state that still matters.

## Example

Input:

```text
The current transport is HTTP.

Unix domain sockets might reduce local overhead.
We should investigate them.

After testing, we completed the migration.
Local transport now uses Unix domain sockets.

SQLite remains unchanged.
No external service dependency should be introduced.
```

Possible DSU:

```text
type:context;protocol:context_only;content:transport:Unix domain sockets,storage:SQLite,dependencies:no external service
```

The DSU does not preserve the entire transition history.

It represents the resulting active state.

## Consolidation

Related input may be merged and reorganized.

Input:

```text
The project uses C.
The project is written in C.
C is the implementation language.
```

Possible DSU:

```text
type:context;protocol:context_only;content:project implementation:C
```

Input:

```text
Project X uses C.
The parser belongs to Project X.
The parser has no external dependencies.
```

Possible DSU:

```text
type:context;protocol:context_only;content:X implementation:C,parser:no external dependencies
```

Sentence, paragraph, turn, and source boundaries do not need to survive when a denser semantic organization is clearer.

## State Change

DeSU should not treat every new statement as a state transition.

Input:

```text
The transport is HTTP.

Unix domain sockets could be better.
Let's compare them.
```

Possible DSU:

```text
type:context;protocol:context_only;content:transport:HTTP
```

No adoption occurred.

Different input:

```text
The transport is HTTP.

The migration is complete.
Local transport now uses Unix domain sockets.
HTTP is no longer used locally.
```

Possible DSU:

```text
type:context;protocol:context_only;content:transport:Unix domain sockets
```

The difference is supported state change, not recency alone.

## Regeneration

A DSU may later be combined with continued interaction and consolidated again.

```text
DSU_t + interaction -> DeSU -> DSU_t+1
```

A prior DSU may represent state that has already undergone selection, integration, and reduction.

Later interaction may contain:

* new evidence;
* corrections;
* actual decisions;
* unresolved exploration;
* repetition;
* temporary attention shifts.

DeSU therefore attempts to preserve prior effective state when no supported change is established and revise it when the complete input supports change.

Prior consolidated state has persistence, not immunity.

```text
prior consolidation != truth
```

## Contradiction and Uncertainty

Conflicting input may represent:

* unresolved disagreement;
* temporal change;
* stale state;
* different scopes;
* different entities;
* a supported transition.

DeSU should interpret the complete input jointly.

It should not rely on a universal rule such as:

```text
latest statement wins
```

When conflict cannot be resolved from the input, uncertainty should remain explicit.

Input:

```text
Deployment may need cloud support.
Current requirement is local-only deployment.
It is unclear whether the cloud requirement still applies.
```

Possible DSU:

```text
type:context;protocol:context_only;content:deployment:local-only current requirement,cloud requirement status unresolved
```

## Output Format

DeSU emits one line using a minimal context envelope:

```text
type:context;protocol:context_only;content:<dense_semantic_record>
```

Optional explicit permissions, prohibitions, or operational constraints may use:

```text
type:context;protocol:context_only;content:<dense_semantic_record>;rules:<optional_constraints>
```

`context_only` means that the artifact is intended to be interpreted as context.

Its presence does not itself request action.

Operational language in source material should remain contextual rather than automatically becoming a new command.

Input:

```text
Do not deploy before approval.
```

Possible DSU:

```text
type:context;protocol:context_only;content:deployment requires prior approval
```

## Direct LLM Interpretation

A DSU is represented in language rather than in a model-specific hidden format.

It is designed to be directly interpretable by capable LLMs.

Example:

```text
type:context;protocol:context_only;content:project:X,architecture:monolith,deployment:local-only,cloud support:unresolved
```

The representation may be:

* telegraphic;
* relational;
* grammatically minimal;
* highly compact.

It does not need to resemble natural prose.

The intended path is:

```text
DSU -> LLM context -> continued inference
```

A DSU does not require a mandatory specialized decoder or model-specific state-transfer mechanism.

This does not imply identical interpretation across models.

## Portability and Agnosticism

A DSU is an explicit language-based artifact.

It can be stored, inspected, copied, versioned, passed between sessions, or supplied to another capable LLM context without requiring a mandatory vendor-specific memory service or hidden-state transfer mechanism.

The intended property is format-level portability, not identical interpretation.

```text
DSU -> another session
DSU -> another runtime
DSU -> another capable model
DSU -> local/cloud handoff
DSU -> file or prompt context
```

A DSU does not inherently depend on:

* a specific conversation database;
* a specific agent runtime;
* a specific model family;
* a graph backend;
* a retrieval backend;
* a specialized decoder;
* vendor-specific hidden state.

This agnosticism is part of the practical value of materializing state explicitly in language.

## Model Dependence

DeSU is executed by a model.

Different models may differ in:

* entity resolution;
* abstraction;
* contradiction handling;
* relevance judgment;
* uncertainty preservation;
* recognition of supported state transitions;
* compression aggressiveness.

DSU generation is therefore model-conditioned.

DeSU can orient model behavior but cannot guarantee correctness.

## Failure Modes

Important failure modes include:

* losing critical negation;
* dropping an active constraint;
* merging distinct entities or scopes;
* erasing uncertainty;
* preserving stale state;
* inventing facts or relations;
* inventing certainty;
* resolving contradiction without support;
* resurrecting rejected branches;
* confusing exploration with adoption;
* overwriting established state because later discussion is longer or more recent;
* treating prior consolidated state as unquestionable truth;
* overcompressing until consequential distinctions disappear.

## Non-Goals

DeSU is not:

* a transcript;
* a history archive;
* reversible compression;
* a canonical encoding;
* a retrieval protocol;
* a complete memory architecture;
* a hidden-state transfer mechanism;
* a guarantee of exact reconstruction;
* a formal proof of semantic sufficiency.

It is a prompt for generating dense contextual representations of consequential resultant state.

## Possible Uses

Possible uses include:

* local LLM continuity under limited context budgets;
* active-context checkpoints;
* cross-session continuation;
* project state reuse;
* task handoff;
* model switching;
* local/cloud model handoff;
* context renewal after long exploration;
* integration into larger memory or retrieval systems.

These are integration choices.

They are not implemented by the prompt itself.

## Status

DeSU is experimental.

Its behavior depends on the generating and receiving models.

Questions around:

* long-term regeneration;
* cross-model portability;
* discourse-imbalance resistance;
* gap recovery;
* continuation quality;
* comparison with alternative compaction and continuation-checkpoint policies;

require further practical and controlled evaluation.

## License

This project is distributed under the GNU General Public License version 3 (GPLv3).

## Name

**DeSU** keeps `DSU` visible in the project name while also reading as *desu*, echoing the Japanese copular expression `です`.

The linguistic correspondence is informal and is not part of the technical definition.

---

## License

This project is distributed under the GNU General Public License version 3 (GPLv3).
