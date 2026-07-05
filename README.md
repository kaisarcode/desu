# DeSU

![DeSU logo](desu.svg)

**DeSU** is a prompt for generating **Dense Semantic Units (DSUs)** for compact, portable, reconstructive LLM context continuity.

A DSU is a compact, self-contained natural-language representation of the **active semantic state** of an ongoing reasoning, conversational, or task process. It preserves enough future-relevant structure for a capable model to continue usefully without transporting the full history that produced that state.

In this repository, DeSU is the prompt in `desu.txt`. A DSU is the artifact that prompt produces from input context.

In compact form:

```text
DeSU(input context) -> DSU
```

A DSU is the artifact. DeSU is the prompt that generates it.

## Name

**DeSU** deliberately keeps `DSU` visible in the project name while also reading as *desu*, echoing the Japanese copular expression `です`. The linguistic correspondence is not exact and is not part of the technical definition, but the association is fitting: DeSU attempts to produce a compact statement of what the active semantic state **is** for purposes of future continuation.

## Core Idea

Conversation history is often much larger than the semantic structure actually needed to continue useful work.

DeSU attempts to preserve the information whose loss would materially change future reasoning or action, such as:

* active decisions;
* constraints and prohibitions;
* critical negation and limits;
* concepts and relations;
* unresolved dependencies;
* important exclusions;
* uncertainty and conflict;
* current objectives;
* open questions;
* effective conclusions and reasoning outcomes;
* temporally relevant facts;
* identifiers, paths, URLs, filenames, code symbols, acronyms, and other literals when they matter.

It should discard information that no longer changes continuation, such as:

* redundancy;
* repeated support;
* rhetoric and politeness;
* obsolete exploration;
* superseded branches;
* unnecessary source order;
* reconstructible narrative;
* low-value examples;
* duplicated explanations;
* surface form whose preservation has no future utility.

The result is deliberately lossy.

The goal is not archival fidelity. The goal is to preserve enough semantic structure for reconstructive continuation.

## Dense Semantic Units

A **Dense Semantic Unit (DSU)** is a practical minimum-sufficient semantic checkpoint.

It is:

* compact;
* self-contained enough for direct contextual use;
* expressed in natural language;
* future-inference-oriented;
* aggressively lossy when loss is low-impact;
* model-conditioned and non-canonical;
* inspectable by humans;
* directly consumable by sufficiently capable LLMs;
* portable across sessions and model families;
* regenerated as the underlying interaction state evolves.

A DSU is not required to reproduce its source history exactly.

A DSU is not mathematically unique or minimal.

A DSU is not a hidden model state transfer protocol.

A DSU is not an archival record.

Its purpose is functional continuity under transformation.

## Reconstructive Continuity

DeSU is built around the hypothesis that useful conversational continuity depends less on preserving history than on preserving enough semantic structure for capable agents to resume the process.

The effective continuation state is distributed across:

* the DSU;
* the receiving model's priors and capabilities;
* the human user's memory and pattern recognition;
* active artifacts and environment;
* new conversation;
* correction and clarification;
* newly introduced evidence.

This means an omitted detail is not automatically a continuity failure.

Some omissions may be reconstructed from preserved constraints, model knowledge, user correction, environmental evidence, contradiction detection, pattern completion, or ordinary continued interaction before they affect behavior.

For that reason, DeSU distinguishes:

* **raw information loss** — information absent from the DSU;
* **observable functional loss** — a downstream failure caused by the omission;
* **residual unrepaired loss** — a failure that remains after normal human-model interaction has had an opportunity to repair the gap.

The project treats conversation itself as part of the memory mechanism.

## Lifecycle

The intended lifecycle is:

```text
conversation or reasoning
    -> semantic distillation
    -> DSU
    -> reload into a capable model
    -> continued human-LLM interaction
    -> gap filling, correction, reinterpretation, new evidence, new decisions
    -> regenerate a new DSU from the evolved state
```

A simplified form:

```text
H_t -> DeSU -> DSU_t
DSU_t + interaction -> evolved state
evolved state -> DeSU -> DSU_t+1
```

The next DSU is not expected to be a copy of the previous one.

`DSU_t+1` may:

* recover information absent from `DSU_t`;
* drop information that lost relevance;
* reformulate dependencies;
* incorporate user corrections;
* preserve newly discovered distinctions;
* encode new decisions;
* reflect a different capable model's conceptualization.

DSUs are therefore **plastic**.

The framework values continuity under transformation rather than semantic immobility.

## Interactive Regeneration vs Recursive Self-Copy

DeSU may reconsolidate previous DSUs, but recursive self-copy is not the primary lifecycle.

This is supported:

```text
DSU_0 -> DeSU -> DSU_1 -> DeSU -> DSU_2
```

but repeated lossy transformation without new interaction can accumulate drift, erase distinctions, or converge toward generic state because missing information has no external source for recovery.

The preferred lifecycle is:

```text
DSU_0
  -> real interaction
  -> DeSU
  -> DSU_1
  -> real interaction
  -> DeSU
  -> DSU_2
```

Interactive regeneration can incorporate new evidence, user correction, environmental state, model inference, and repaired gaps.

A new DSU should represent the evolved interaction state, not mechanically reproduce the previous checkpoint.

## Portability

Portability is central.

A DSU should be directly usable as context by sufficiently capable model families without requiring a specialized:

* parser;
* decoder;
* embedding lookup;
* vector index;
* retrieval algorithm;
* graph traversal;
* reranking stage;
* model-specific state-transfer protocol.

Natural language is the shared semantic interface.

This can support handoff between local and cloud models, for example:

```text
local model -> DSU -> cloud model
cloud model -> evolved interaction -> DSU -> local model
```

Portability does not imply invariant interpretation.

The same DSU may yield different continuations in different models because interpretation depends on:

* model training;
* priors;
* world knowledge;
* capabilities;
* active system context;
* current user input.

The artifact remains usable across capable interpreters even when continuation is not identical.

## Model Dependence

DeSU is executed by a model:

```text
d = G_M(X)
```

where:

* `X` is the input context;
* `M` is the generating model;
* `G_M` is DeSU's consolidation behavior under that model;
* `d` is the resulting DSU.

Different models may produce different valid DSUs from the same input.

Variation can affect:

* entity resolution;
* abstraction level;
* contradiction handling;
* what is judged future-relevant;
* semantic merge quality;
* inferred dependencies;
* uncertainty preservation;
* compression aggressiveness.

DSU production is therefore **generative semantic reconstruction**, not neutral extraction.

This is powerful and risky.

A model may make latent dependencies explicit, but it may also consolidate model-specific assumptions or incorrect inferences.

DeSU must therefore avoid:

* inventing unsupported facts;
* inventing certainty;
* merging non-equivalent core ideas;
* erasing critical negation;
* silently resolving unsupported contradictions;
* collapsing distinct entities or scopes.

## What DeSU Optimizes For

DeSU aims to preserve information that changes future answers or actions.

A useful conceptual objective is:

```text
maximize future semantic utility
subject to strong reduction
```

The prompt should jointly interpret the complete input rather than shorten fragments independently.

Source boundaries have no privileged status.

Related information may be:

* deduplicated;
* merged;
* reorganized;
* connected across distant fragments;
* collapsed into a unified semantic state.

Effective decisions and reasoning outcomes should usually be preserved instead of full reasoning traces.

Strong reduction is desirable, but no fixed ratio defines success.

Aggressive token reduction targets may be used as prompt-level heuristics to discourage conservative restatement, but they are not protocol guarantees or defining DSU properties.

### Semantic Importance Is Not Discursive Prominence

DeSU should not infer semantic importance, commitment, or state change merely from recency, token volume, repetition, discussion length, or surface elaboration.

A compact established decision or constraint may remain more important to future continuation than a long recent discussion of an uncommitted possibility.

For example:

```text
established state:
storage:SQLite
```

followed by extensive discussion of LMDB or RocksDB does not by itself imply that the storage decision changed.

DeSU should distinguish between information that is merely prominent in the discourse and information that actually changes the active semantic state.

In compact form:

```text
discursive prominence != semantic importance
```

Information should be weighted by its effect on future answers or actions, including whether it changes:

* active decisions;
* constraints;
* effective relations;
* unresolved dependencies;
* uncertainty;
* objectives;
* expected downstream behavior.

Recent or verbose material should replace or substantially reweight prior state only when the complete input supports a real revision, supersession, correction, or newly effective state.

This is especially important during DSU regeneration. A previous DSU may represent stable semantic state very compactly, while subsequent interaction may occupy many more tokens. The larger textual footprint of new discussion should not by itself displace the compact semantic core.

Conceptually:

```text
DSU_t + interaction
```

should not be treated merely as:

```text
small amount of old text + large amount of new text
```

but as:

```text
prior consolidated semantic state + potential state transitions
```

The subsequent interaction may contain:

* genuine revisions;
* corrections;
* new decisions;
* extensions;
* unresolved exploration;
* speculation;
* repetition;
* rhetorical emphasis;
* temporary attention shifts.

Only some of these should alter the semantic checkpoint.

A useful evaluation property is therefore:

```text
semantic stability under discourse imbalance
```

Semantically equivalent interaction with very different levels of repetition or elaboration should produce functionally similar DSUs when no real state change occurred.

For example:

```text
DSU_t
+ brief exploration of alternative X
-> DSU_t+1
```

and:

```text
DSU_t
+ extensive repeated exploration of alternative X
-> DSU_t+1
```

should remain functionally similar when alternative X was not adopted and did not materially change future reasoning or action.

This principle distinguishes semantic state consolidation from discourse-proportional summarization.

A traditional summary may tend to allocate space according to how much source material discussed a topic. A DSU should instead allocate representation according to what materially changes continuation.

## Context-Only Envelope

The prompt uses a minimal context-only serialization envelope:

```text
type:context;protocol:context_only;content:<dense_semantic_record>
```

Optional semantically relevant constraints may be represented as:

```text
type:context;protocol:context_only;content:<dense_semantic_record>;rules:<optional_constraints>
```

The envelope is transport and interpretation metadata.

It is not the source of semantic intelligibility.

A capable model can understand the DSU because the payload is natural-language semantic context.

`context_only` means that the artifact is intended to be read and retained as context. Its presence does not by itself request action.

Operational language inside the source must be preserved as contextual meaning rather than automatically converted into a new request to the consumer.

Input:

```text
Do not deploy before approval.
```

Possible DSU:

```text
type:context;protocol:context_only;content:deployment requires prior approval
```

The deployment restriction remains semantically active, but the DSU itself is not a new deployment request.

The wrapper is stable in the prompt, but it is not the definition of a DSU and should not be confused with the DeSU concept itself.

## Example: Deduplication

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

Equivalent meaning is represented once.

## Example: Complementary Merge

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

The output is organized by semantic relationship rather than source order.

## Example: State Change

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

This result is valid only because the complete input supports interpreting the later statement as a state transition.

Without sufficient support, uncertainty or conflict should be preserved.

## Contradictions and Uncertainty

Conflicting input may represent:

* unresolved disagreement;
* temporal change;
* stale state;
* different scopes;
* different entities;
* one effective state supported by stronger context.

DeSU must not impose a universal rule such as always trusting the last statement.

The complete input should be interpreted jointly.

When the evidence does not support a clearer unified state, preserve uncertainty, ambiguity, or conflict.

> Consolidate without inventing unsupported facts or certainty.

## Frequent Regeneration

A central project hypothesis is that frequent semantic-state regeneration may outperform late conventional compaction near context exhaustion.

Long histories accumulate:

* redundancy;
* obsolete branches;
* repeated explanations;
* stale assumptions;
* contradictory historical residue;
* competing continuation paths.

Frequent regeneration may keep active state smaller and cleaner while reducing:

* peak context pressure;
* total tokens processed;
* latency;
* generation cost;
* the size of expensive late compression events.

This is an empirical hypothesis, not an established result.

## Local-First Usage Direction

DeSU itself is the prompt in `desu.txt`.

The surrounding usage model is deliberately small, inspectable, and local-first.

Tooling around the prompt may support operations such as:

```text
distill
apply
save
load
model switch
```

A practical flow is:

```text
user triggers distill
    -> generate current DSU
    -> optionally preview or save
    -> clear or replace local context/KV as appropriate
    -> re-inject base system context + DSU
    -> continue
```

The project should avoid premature dependence on:

* event systems;
* automatic delta logic;
* vector retrieval;
* HNSW;
* knowledge graphs;
* complex memory orchestration;
* enterprise-style agent infrastructure.

Those systems may be useful elsewhere, but they are not semantically necessary for the minimal DeSU mechanism.

## Task-Based Model Arbitration

A major practical objective is task-based model arbitration.

For example:

```text
local model
    -> routine implementation and iteration
    -> difficult ambiguity or reasoning boundary
    -> selective cloud model use
    -> evolve state
    -> DeSU
    -> return compact DSU to local model
    -> continue locally
```

This may allow constrained local hardware to reuse the outcome of expensive reasoning without repeatedly transporting long histories or paying cloud costs for routine continuation.

Cross-model handoff is therefore a first-class use case.

## Evaluation

DeSU should be evaluated by practical continuity, error, recoverability, cost, and portability rather than perfect textual fidelity.

### Core comparisons

Useful comparisons include:

* frequent DSU regeneration vs late conventional compaction;
* full-history continuation vs DSU-only continuation;
* same-model generation/consumption vs cross-model handoff;
* recursive DSU self-copy vs interactive regeneration.

### Candidate metrics

Relevant metrics include:

* functional continuity retention;
* residual unrepaired error;
* decision divergence;
* constraint loss;
* rejected-branch resurrection;
* invented commitments;
* gap recovery;
* state drift;
* latency;
* token cost;
* peak context pressure;
* total context usage;
* cross-session continuity;
* cross-model portability.

### Discourse-Imbalance Tests

Experiments should test whether DeSU remains stable when semantic content is held approximately constant while discursive prominence changes.

Variables may include:

* recency;
* token volume;
* repetition count;
* discussion length;
* number of examples;
* degree of elaboration;
* rhetorical emphasis;
* position within the context.

For example, compare:

```text
established decision
+ 50 tokens of uncommitted exploration
```

against:

```text
same established decision
+ 5000 tokens of semantically equivalent uncommitted exploration
```

If no effective state change occurred, the resulting DSUs should remain functionally similar.

These tests can measure whether verbose recent material improperly displaces compact established state.

### Gap-injection tests

Experiments should separately remove:

* reconstructible detail;
* critical constraints;
* decisions;
* examples;
* uncertainty.

Then observe whether omissions:

* are silently reconstructed;
* are corrected through interaction;
* remain harmless;
* cause observable downstream failure;
* remain as residual unrepaired error.

### Behavioral evaluation

Full-history and DSU-only continuation should be judged primarily by downstream behavior and decisions, not textual similarity.

A continuation can differ in wording while preserving functional state.

## Working Hypotheses

DeSU motivates several testable hypotheses.

### 1. Useful state is much smaller than history

Many long conversations may contain a compact semantic core sufficient for useful continuation.

### 2. Latent omission can coexist with low observable failure

Missing details may be repaired by model inference, user correction, current environment, or later interaction before they affect behavior.

### 3. There may be a practical compression region

Large token reduction may cause little functional degradation until overcompression removes high-impact distinctions.

### 4. Obsolete context may actively harm continuation

Removing stale branches and competing historical residue may reduce misleading continuation paths and some forms of hallucination-like drift.

### 5. Interactive regeneration may resist degradation better than recursive self-copy

Real interaction introduces new evidence and repair opportunities that pure DSU-to-DSU transformation lacks.

### 6. Semantic state may remain stable under large differences in discourse volume

When no real state change occurs, semantically equivalent interaction with different levels of recency, repetition, or elaboration may still support functionally similar DSUs.

If this holds, DeSU can resist discourse-level prominence that would otherwise distort the compact semantic checkpoint.

These are working hypotheses and require controlled validation.

## Failure Modes

DeSU can fail by changing meaning during consolidation.

Examples include:

* losing negation;
* losing a critical restriction;
* merging distinct entities;
* preserving stale state;
* erasing uncertainty;
* inventing a relation;
* inventing certainty;
* resolving contradiction without support;
* resurrecting discarded hypotheses;
* dropping a decision whose loss changes future behavior;
* overgeneralizing examples;
* compressing away scope distinctions;
* overweighting recent, repeated, verbose, or highly elaborated exploration relative to compact established state;
* interpreting discussion volume as commitment, adoption, or state change.

Recursive reuse can also degrade information when an earlier DSU removed distinctions that later become important.

Protocol failures may include:

* missing or duplicated envelope fields;
* copying wrapper metadata into semantic payload;
* treating contextual operational language as a new request;
* confusing transport metadata with DSU meaning.

## Relationship to Retrieval Systems

DeSU is not a retrieval protocol.

A retrieval system may store DSUs with:

* embeddings;
* timestamps;
* identifiers;
* scope;
* provenance;
* ranking metadata.

It may retrieve several DSUs and consolidate them again.

Those are external architectural choices.

Retrieval, filtering, ranking, chunk selection, graph traversal, and prompt assembly are not semantically required for the minimal DeSU mechanism.

A DSU should be self-contained enough that a capable recipient does not need separate heuristics to decide which internal fragments to retrieve or how to merge them before reasoning.

## Relationship to Agent Memory

DeSU can be used inside an agent-memory architecture.

Possible uses include:

* project state reuse;
* task handoff;
* long-running agent continuity;
* conversation memory;
* model switching;
* compact checkpoints;
* cross-session state transfer.

That is a use case, not the complete definition of DeSU.

Whether an external agent acts depends on mechanisms outside the mere presence of a DSU.

## Theoretical Connections

The project has partial conceptual connections to areas such as:

* sufficient statistics;
* Information Bottleneck;
* predictive or causal state ideas;
* belief-state compression;
* state abstraction;
* behavioral equivalence;
* recurrent textual memory;
* reconstructive memory.

DeSU should not be claimed as identical to any of them.

It does not provide a mathematically canonical minimal encoding or a formal proof of sufficiency.

Its distinctive practical combination is a compact, inspectable, aggressively lossy, future-inference-oriented, natural-language, model-conditioned, directly consumable, cross-session and cross-model portable checkpoint regenerated through live human-LLM interaction.

## What DeSU Is Not

DeSU is not:

* reversible compression;
* a traditional summary;
* an archival format;
* a formal DSL;
* a compiler or parser;
* a retrieval engine;
* a vector database;
* a metadata store;
* an event log;
* a hidden-state transfer protocol;
* a guarantee of deterministic reproduction;
* a guarantee of exact reconstruction;
* a requirement for recursive self-copy stability;
* an instruction envelope for its consumer.

## Terminology

The terminology used here is:

```text
DSU
    the conceptual semantic-state artifact

DeSU
    the prompt for distilling DSUs from active context

distill
    produce a DSU from active context

apply / rehydrate
    install a DSU into active model context

portable semantic state
    a property of a usable DSU

frequent regeneration
    a lifecycle strategy
```

This repository is `desu.txt`, the DeSU prompt, plus documentation for the DSU concept it describes.

DeSU asks a practical question:

> What is the smallest practical semantic state that still lets reconstructive human-model systems continue useful work?

## Status

DeSU is an active research prompt and concept document.

Preliminary practical observations suggest that capable models can often continue productively from aggressively compact semantic checkpoints, including across fresh sessions and different model families.

These observations are promising but not universal results.

The project explicitly distinguishes:

* hypotheses;
* preliminary practical evidence;
* controlled experimental results;
* established claims.

## License

This project is distributed under the GNU General Public License version 3 (GPLv3).
