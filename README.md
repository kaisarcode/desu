# DeSU

![DeSU logo](desu.svg)

**DeSU** is a prompt for generating **Dense Semantic Units (DSUs)**: compact semantic state records for LLM context reuse.

A DSU preserves enough future-relevant active state for useful continuation without transporting the full history that produced it.

In this repository:

* `desu.txt` is the DeSU prompt.
* A DSU is the artifact produced by that prompt.

```text
DeSU(input context) -> DSU
```

## Core Idea

Conversation, reasoning, and task histories often grow far beyond the semantic state still needed for continuation.

A long process may contain exploration, repetition, corrections, abandoned branches, examples, resolved questions, and intermediate reasoning. Future work often depends on a much smaller structure: what remains decided, constrained, unresolved, uncertain, excluded, related, or operationally significant.

DeSU attempts to consolidate that active structure into a dense one-line record.

The goal is not to preserve source coverage or natural prose. The goal is to preserve information whose loss may change future reasoning, answers, or actions.

A DSU may preserve:

* effective decisions;
* constraints and prohibitions;
* critical negation and limits;
* entities and relations;
* objectives;
* important exclusions;
* open questions;
* unresolved dependencies;
* uncertainty and conflict;
* effective conclusions and reasoning outcomes;
* semantically relevant temporal facts;
* exact paths, URLs, IDs, filenames, code symbols, acronyms, and other operational literals.

It may remove:

* filler and politeness;
* rhetoric;
* repetition;
* redundant support;
* unnecessary explanation;
* obsolete exploration;
* superseded branches;
* resolved residue;
* reconstructible narrative;
* low-impact examples;
* source order and boundaries that no longer affect meaning.

The result is deliberately lossy.

## Dense Semantic Units

A **Dense Semantic Unit** is a compact, self-contained, language-based representation of active semantic state.

It is optimized for dense direct interpretation by capable LLMs rather than natural prose.

A DSU may use telegraphic phrasing, compact relations, and minimal grammar when meaning remains clear:

```text
type:context;protocol:context_only;content:project:X,implementation:C,dependencies:no external,parser:preserve byte offsets,transport:Unix domain sockets
```

A DSU is:

* compact;
* directly interpretable by capable LLMs;
* future-inference-oriented;
* aggressively lossy when consequential meaning survives;
* model-conditioned and non-canonical;
* inspectable;
* reusable across sessions;
* potentially portable across model families;
* regenerable as interaction evolves.

A DSU is not:

* an archive;
* reversible compression;
* a transcript;
* a canonical encoding;
* a formal proof of sufficiency;
* a hidden-state transfer protocol;
* a guarantee of exact reconstruction.

Its purpose is useful continuity under transformation.

## Consolidation

DeSU interprets the complete input semantically rather than shortening fragments independently.

Related information may be deduplicated, merged, reorganized, or expressed through denser relations. Sentence, paragraph, turn, source, and prior DSU boundaries do not have to survive when semantic reorganization is clearer.

Effective state should usually survive instead of the full reasoning trajectory that produced it.

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

The output is organized by semantic relation rather than source order.

## Regeneration and Consolidated State

A DSU may later be combined with continued interaction and consolidated again.

```text
DSU_t + interaction -> DeSU -> DSU_t+1
```

This input should not be treated as one homogeneous body of text.

A prior DSU may represent semantic state that has already undergone selection, integration, and reduction. Later interaction may contain new evidence, corrections, real decisions, unresolved exploration, repetition, temporary attention shifts, or branches that are never adopted.

DeSU therefore attempts to infer, from the complete input, whether material represents:

* previously consolidated semantic state;
* unconsolidated interaction;
* exploration;
* new evidence;
* an effective state transition.

This distinction is model-conditioned and approximate. DeSU does not assume perfect recognition.

Previously consolidated state has semantic persistence because it already represents prior post-processing. Its compactness, older position, or smaller token footprint should not make it weak by default.

At the same time, prior consolidation is not proof of truth and does not make state immune to revision.

DeSU should preserve effective state when no supported change is established and revise it when the complete input supports:

* addition;
* correction;
* resolution;
* invalidation;
* supersession;
* scope change;
* new uncertainty;
* another effective semantic transition.

Recency, repetition, token volume, verbosity, discussion length, and elaboration are not sufficient evidence of importance or state change.

Likewise, prior consolidation status alone is not sufficient evidence of truth.

The intended behavior is semantic persistence without semantic immobility.

## State Change

Input:

```text
The transport is HTTP.
We dropped HTTP and moved local transport to Unix domain sockets.
SQLite stays.
```

Possible DSU:

```text
type:context;protocol:context_only;content:transport:Unix domain sockets,storage:SQLite
```

The complete input supports a transition from HTTP to Unix domain sockets.

If the input only explored Unix domain sockets without adopting them, the prior effective state should not be replaced merely because that exploration was longer or more recent.

## Contradiction and Uncertainty

Conflicting input may represent:

* unresolved disagreement;
* temporal change;
* stale state;
* different scopes;
* different entities;
* one effective state supported by stronger context.

DeSU should interpret the complete input jointly.

It should not use a universal rule such as always trusting the latest statement.

When the input does not support a clearer unified interpretation, uncertainty, ambiguity, or conflict should remain explicit.

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

## Reconstructive Continuity

A DSU does not need to preserve every recoverable detail.

Useful continuation depends on more than the checkpoint itself. It may also depend on:

* the receiving model's capabilities and priors;
* current user input;
* active artifacts and environment;
* correction and clarification;
* later evidence;
* continued interaction.

An omitted detail is therefore not automatically a continuity failure.

A gap may be reconstructed from preserved constraints, model knowledge, user correction, current artifacts, contradiction detection, or later interaction before it affects behavior.

This motivates three different notions of loss:

* **raw information loss** — information absent from the DSU;
* **observable functional loss** — downstream failure caused by the omission;
* **residual unrepaired loss** — failure that remains after ordinary interaction had an opportunity to repair the gap.

DeSU is concerned more with useful continuity than textual reconstruction.

## Plasticity

DSUs are checkpoints, not frozen truth objects.

Continued interaction may:

* add evidence;
* repair omissions;
* revise decisions;
* resolve uncertainty;
* expose new distinctions;
* remove stale material;
* reformulate relations.

A later DSU should represent the evolved state.

```text
DSU_t
+ interaction
+ correction
+ new evidence
-> DeSU
-> DSU_t+1
```

The next DSU is not expected to reproduce the previous one mechanically.

## Interactive Regeneration

Repeated DSU-to-DSU transformation without new interaction can accumulate drift because removed distinctions have no external source for recovery.

```text
DSU_0 -> DeSU -> DSU_1 -> DeSU -> DSU_2
```

This is possible, but it is not the preferred lifecycle.

Interactive regeneration introduces new evidence and repair opportunities:

```text
DSU_0
-> real interaction
-> DeSU
-> DSU_1
-> real interaction
-> DeSU
-> DSU_2
```

Whether this resists degradation better than recursive self-copy is a project hypothesis, not an established result.

## Portability

A DSU should be directly usable by sufficiently capable LLMs without requiring a specialized:

* parser;
* decoder;
* embedding lookup;
* vector index;
* retrieval algorithm;
* graph traversal;
* reranking stage;
* model-specific state-transfer protocol.

Dense language is the shared interface.

Portability does not imply invariant interpretation.

Different models may continue differently from the same DSU because interpretation depends on model training, capabilities, world knowledge, active system context, and current input.

The practical claim is weaker: a DSU may remain directly usable across capable sessions and model families without requiring a model-specific decoding mechanism.

## Model Dependence

DeSU is executed by a model, so DSU generation is model-conditioned.

Different models may differ in:

* entity resolution;
* abstraction;
* contradiction handling;
* inferred dependencies;
* relevance judgments;
* uncertainty preservation;
* compression aggressiveness;
* recognition of previously consolidated state;
* interpretation of effective state transitions.

DSU production is generative semantic reconstruction rather than neutral extraction.

That creates both value and risk.

A model may expose an implicit dependency or reorganize fragmented state more clearly. It may also invent a relation, erase uncertainty, merge distinct scopes, preserve stale state, or convert exploration into commitment.

The quality of consolidation therefore depends on model capability. DeSU can orient that capability but cannot guarantee it.

## Context-Only Envelope

DeSU emits a minimal envelope:

```text
type:context;protocol:context_only;content:<dense_semantic_record>
```

Optional explicit permissions, prohibitions, or operational constraints may use:

```text
type:context;protocol:context_only;content:<dense_semantic_record>;rules:<optional_constraints>
```

`context_only` means that the artifact is intended to be read and retained as context. Its presence does not itself request action.

Operational language inside source material should be preserved as contextual meaning rather than automatically converted into a new command.

Input:

```text
Do not deploy before approval.
```

Possible DSU:

```text
type:context;protocol:context_only;content:deployment requires prior approval
```

The wrapper is not semantic payload and does not define DSU meaning.

DeSU may use wrapper markers as contextual evidence that material is previously consolidated, but markers are neither required nor proof. Consolidation status is inferred from the complete input and semantic form.

## What DeSU Optimizes For

DeSU aims to maximize semantic utility per token while preserving consequential meaning.

It favors:

* unified semantic state over source restatement;
* dense interpretability over natural prose;
* effective decisions over full reasoning traces;
* meaningful distinctions over exhaustive coverage;
* strong reduction when future utility survives.

It does not target a fixed compression ratio.

Reduction is subordinate to preserving consequential state.

## Failure Modes

DeSU can fail by changing meaning during consolidation.

Important failures include:

* losing negation;
* dropping a critical restriction;
* merging distinct entities or scopes;
* erasing uncertainty;
* preserving stale state;
* inventing facts or relations;
* inventing certainty;
* resolving contradiction without support;
* resurrecting rejected branches;
* dropping a high-impact decision;
* confusing exploration with adoption;
* overweighting recent or verbose unconsolidated interaction;
* treating prior consolidated state as unquestionable truth;
* overcompressing until consequential distinctions disappear.

These risks follow directly from model-conditioned semantic reconstruction.

## Possible Uses

DeSU itself is only the prompt in `desu.txt`.

Possible uses include:

* compact conversation checkpoints;
* cross-session continuation;
* project state reuse;
* task handoff;
* model switching;
* local/cloud model handoff;
* semantic reset after long exploration;
* reflective re-expansion;
* use inside larger memory or retrieval systems.

These uses are external integration choices. They are not implemented by the prompt itself.

## Relationship to Retrieval and Agent Memory

DeSU is not a retrieval protocol or complete agent-memory architecture.

External systems may store DSUs with embeddings, timestamps, identifiers, scope, provenance, or ranking metadata. They may retrieve several DSUs and consolidate them again.

Those mechanisms are optional.

The minimal DeSU mechanism remains:

```text
input context
-> DeSU
-> DSU
-> direct contextual reuse
```

## Evaluation Ideas

The project is suitable for behavioral evaluation rather than textual similarity alone.

Possible comparisons include:

* full-history continuation vs DSU-only continuation;
* frequent regeneration vs late compaction;
* same-model vs cross-model handoff;
* recursive self-copy vs interactive regeneration.

Possible measures include:

* functional continuity;
* decision retention;
* constraint retention;
* critical negation preservation;
* uncertainty preservation;
* decision divergence;
* rejected-branch resurrection;
* invented commitments;
* state drift;
* gap recovery;
* residual unrepaired error;
* token cost;
* latency;
* peak context pressure;
* cross-session continuity;
* cross-model usability.

### Discourse-Imbalance Tests

A specific test should vary textual prominence while holding semantic state approximately constant.

Compare:

```text
established decision
+ brief uncommitted exploration of alternative X
```

with:

```text
same established decision
+ extensive repeated uncommitted exploration of alternative X
```

If no effective state change occurred, resulting DSUs should remain functionally similar.

This tests whether DeSU preserves compact consolidated state instead of weighting material by recency or volume.

### Gap Tests

Different classes of information can be removed before continuation:

* reconstructible detail;
* critical constraints;
* decisions;
* uncertainty;
* operational literals.

The useful distinction is whether omissions are repaired before impact or remain as residual functional errors.

## Working Hypotheses

The project currently motivates several hypotheses:

1. Useful active state is often much smaller than accumulated history.
2. Large textual loss may coexist with low observable functional loss when gaps are repaired before impact.
3. There may be a broad practical compression region before consequential distinctions disappear.
4. Removing obsolete or competing history may sometimes improve continuation.
5. Interactive regeneration may resist degradation better than recursive self-copy.
6. Consolidated state may remain stable under large differences in recency, repetition, and discourse volume when no effective state change occurred.
7. Dense DSUs may remain practically usable across sessions and capable model families.

These are hypotheses, not guarantees.

## Name

**DeSU** keeps `DSU` visible in the project name while also reading as *desu*, echoing the Japanese copular expression `です`.

The linguistic correspondence is informal and not part of the technical definition. The association is fitting because DeSU attempts to produce a compact statement of what the active semantic state is for future continuation.

## Terminology

* **DSU** — the semantic-state artifact.
* **DeSU** — the prompt in `desu.txt` that generates DSUs.
* **distill** — generate a DSU from input context.
* **regenerate** — produce a new DSU from evolved state.
* **apply / rehydrate** — load a DSU into active model context.
* **portable semantic state** — practical direct usability across capable sessions or models.

## Status

DeSU is an experimental prompt and concept project.

Its behavior depends on the generating and receiving models. Current ideas around reconstruction, cross-model portability, discourse-imbalance resistance, semantic denoising, and frequent regeneration require further practical and controlled evaluation.

## License

This project is distributed under the GNU General Public License version 3 (GPLv3).
