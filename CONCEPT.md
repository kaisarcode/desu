# Dense Semantic Units: Conceptual Framework

## 1. Core Definition

A **Dense Semantic Unit (DSU)** is a dense, language-based representation of **consequential resultant state**, designed for direct interpretation by capable LLMs.

It represents the semantic state that remains in force after prior interaction, reasoning, task activity, correction, exploration, or decision-making, insofar as that state may still affect future continuation.

A DSU does **not** primarily preserve the history that produced the state.

It represents the result that remains semantically consequential.

In compact form:

```text
trajectory -> resultant state -> consequential projection -> DSU
```

The central distinction is:

```text
history = what happened
DSU = what remains in force
```

A long interaction may contain substantial historical and inferential structure while producing a much smaller resultant state.

For example:

```text
A was proposed
B was explored
C corrected part of A
A was reconsidered
D was tested and rejected
E was finally adopted
```

A history-oriented representation may preserve that sequence.

A DSU may represent:

```text
state:E
```

If additional information remains consequential:

```text
state:E;constraint:X;dependency:Y unresolved
```

The omitted trajectory may still have historical value.

It is simply not part of the DSU unless it continues to affect future reasoning, answers, actions, interpretation, or operational behavior.

---

## 2. Representational Target and Preservation Priority

Any finite representation of prior context imposes preservation choices.

A DSU is characterized by both:

1. **its representational target**;
2. **its preservation priorities**.

Its representational target is:

> **consequential resultant state**

Its preservation priority is:

> **semantic structure whose loss may still alter future continuation**

A DSU does not primarily target:

* transcript fidelity;
* historical completeness;
* chronological continuity;
* source coverage;
* reconstruction of all prior reasoning;
* preservation of every explored alternative.

It may preserve:

* current decisions;
* active constraints;
* objectives;
* unresolved questions;
* uncertainty;
* conflict;
* exclusions;
* dependencies;
* prohibitions;
* supported state transitions;
* semantically active relations;
* relevant temporal conditions;
* operational facts;
* exact identifiers, paths, filenames, symbols, or other literals whose alteration matters.

A DSU may omit information that was previously useful when that information has already completed its role in producing the current state.

This yields an important principle:

> **Information may be valuable during inference without remaining valuable after inference.**

A reasoning path can be necessary to reach a conclusion without needing to remain permanently active once the conclusion and its consequential conditions are established.

---

## 3. Trajectory and Resultant State Are Different Objects

A major source of misunderstanding is treating history and state as alternative encodings of the same object.

They are not.

### Trajectory

Trajectory describes the process by which the current situation emerged.

It may include:

* sequence;
* attempts;
* alternatives;
* revisions;
* reversals;
* explanations;
* intermediate reasoning;
* temporary hypotheses;
* mistakes;
* abandoned branches;
* causal narrative;
* discussion order.

Trajectory answers questions such as:

* What happened?
* What was tried?
* How did the decision evolve?
* Why was an alternative considered?
* What changed over time?

### Resultant state

Resultant state describes what remains semantically active after that process.

It may include:

* what is currently true;
* what is currently adopted;
* what remains constrained;
* what remains prohibited;
* what remains uncertain;
* what remains unresolved;
* what depends on what;
* what still governs continuation.

Resultant state answers questions such as:

* What is now in force?
* What should future reasoning assume?
* What remains undecided?
* What constraints still apply?
* What state should the next inference continue from?

These are different representational objectives.

---

## 4. Consequential Resultant State

The phrase **consequential resultant state** has three parts.

### Resultant

The state is treated as the result of prior interaction, reasoning, correction, or task activity.

It is not a compressed retelling of that activity.

### State

The representation captures what remains active:

* facts;
* decisions;
* constraints;
* relations;
* uncertainty;
* dependencies;
* exclusions;
* unresolved elements;
* operational conditions.

### Consequential

Not every element of the resultant state needs to be retained.

The focus is on semantic structure whose omission may still alter:

* future reasoning;
* answers;
* actions;
* decisions;
* interpretation;
* operational behavior.

This leads to the central definition:

> **A DSU is a dense representation of consequential resultant state: the semantic state that remains in force and may still affect future continuation.**

---

## 5. DSU Is Not History Compaction

A DSU should not be defined as a better form of history compaction.

History compaction and DSU consolidation solve different problems.

### History compaction

```text
history -> shorter representation of history
```

Its goal is generally to preserve enough of the trajectory to maintain historical continuity.

A compacted history may retain:

* sequence;
* major turns;
* changes of direction;
* rejected alternatives;
* explanations;
* important prior discussion.

### DSU consolidation

```text
history + reasoning + interaction -> consequential resultant state
```

Its goal is to preserve what remains semantically in force.

A DSU may discard almost the entire path if the path no longer affects continuation.

The distinction is:

> **History compaction prioritizes continuity of trajectory. A DSU prioritizes continuity of consequential resultant state.**

Both are lossy.

The difference is not whether information is lost.

The difference is what each representation spends its limited budget preserving.

This can be expressed as:

> **Loss is unavoidable; preservation priorities are the design choice.**

---

## 6. DSU Does Not Replace History

A DSU is not an argument against storing history.

Historical information may exist in parallel.

A system may maintain:

```text
raw history
compacted history
DSU
artifacts
logs
retrieval indexes
external memory
```

Each serves a different purpose.

### Raw history

Useful for:

* exact review;
* audit;
* debugging;
* provenance;
* reconstruction;
* detailed search.

### Compacted history

Useful for:

* shorter narrative continuity;
* historical review;
* understanding how a state evolved;
* reconstructing major prior events.

### DSU

Useful for:

* continuing from the current effective state;
* reducing inferential baggage;
* limiting influence from obsolete states;
* conserving context budget;
* loading dense semantic state directly into a model.

### Retrieval

Useful for:

* recovering specific details;
* bringing back relevant historical evidence;
* selectively restoring omitted information.

These mechanisms are complementary.

A DSU occupies a distinct role:

> **active semantic state for continuation**

---

## 7. Resultant-State Consolidation and Inferential Cleanup

A long context contains more than currently useful state.

It also contains residue from prior inference.

Examples include:

* outdated assumptions;
* rejected alternatives;
* temporary hypotheses;
* intermediate formulations;
* corrected mistakes;
* superseded decisions;
* redundant explanations;
* repeated discussion;
* branches that were useful to explore but are no longer active.

This material may continue influencing a model simply because it remains textually present.

A DSU targets the resultant state.

As a consequence, resultant-state consolidation often has a cleanup effect: inferential material that no longer contributes to the active state can leave the active representation.

Example:

```text
A proposed
A fails under initial configuration
B explored
A reconsidered
configuration error discovered
A works
C explored
C rejected
A adopted
```

A trajectory-preserving representation may retain much of this sequence.

A DSU may represent:

```text
decision:A;prior failure:configuration issue resolved;C:rejected
```

Or, if the prior failure and rejection no longer matter:

```text
decision:A
```

The governing principle is:

> **Prior inferential material should not remain influential merely because it remains textually present.**

Inferential cleanup is therefore a frequent effect of DSU consolidation, not the primary definition of a DSU.

---

## 8. Density Is a Means, Not the Definition

DSUs are intentionally dense.

They may use:

* telegraphic language;
* compact relations;
* reduced grammar;
* deduplication;
* semantic merging;
* direct state notation;
* minimal explanatory prose.

Example:

```text
project:X;architecture:E;deployment:local-only;external deps:none;cloud support:unresolved
```

This density is valuable because context is limited.

However, a DSU is not defined merely by compression ratio.

The objective is not:

```text
minimum tokens at any cost
```

The objective is:

```text
maximum consequential semantic utility per token
```

Reduction is subordinate to preserving distinctions that still matter.

A shorter DSU is not automatically better.

A denser DSU is better only while consequential semantic structure remains intact.

---

## 9. State Consolidation Is Not Simple Summarization

A conventional history-oriented summary usually preserves a reduced account of source content or trajectory.

A DSU instead targets the consequential resultant state inferred from the complete context.

This may require:

* merging repeated claims;
* resolving entity references;
* identifying supersession;
* distinguishing exploration from adoption;
* separating local and global scope;
* preserving unresolved contradiction;
* detecting supported transitions;
* dropping obsolete process;
* reorganizing information by semantic relation rather than source order.

Example input:

```text
The current transport is HTTP.

Unix domain sockets could reduce local overhead.
We should investigate them.

After testing, we decided to replace local HTTP transport with Unix domain sockets.

SQLite remains unchanged.
```

A history-oriented summary may preserve the evolution.

A DSU may represent:

```text
transport:Unix domain sockets;storage:SQLite
```

The operation is therefore better described as:

> **semantic state consolidation**

rather than:

> **history shortening**

---

## 10. Exploration Is Not State

A DSU must distinguish between material that appears in context and material that actually changes state.

This distinction is fundamental.

Examples:

```text
exploration != adoption
proposal != decision
possibility != requirement
concern != fact
repetition != validation
volume != commitment
recency != centrality
```

A model may spend thousands of tokens exploring an alternative without adopting it.

Example:

```text
current architecture:monolith
```

followed by a long discussion of microservices.

If no decision changes the architecture, the resultant state may remain:

```text
architecture:monolith
```

The volume or recency of exploration should not by itself overwrite the established state.

This is especially important when a compact prior DSU is combined with a much larger body of later interaction.

---

## 11. Semantic Persistence Without Immutability

A previously generated DSU represents state that has already undergone:

* selection;
* integration;
* reduction;
* consolidation.

Its small token footprint should not make it semantically weak by default.

Therefore, previously consolidated state has a degree of persistence.

However:

```text
prior consolidation != truth
```

A DSU is not immune to revision.

Later input may support:

* addition;
* correction;
* invalidation;
* supersession;
* resolution;
* scope change;
* new uncertainty;
* another effective state transition.

The intended behavior is:

> **preserve effective state absent supported change; revise it when supported change occurs**

This can be summarized as:

> **semantic persistence without semantic immobility**

---

## 12. Supported State Transition

A DSU generator must distinguish actual state change from mere textual change.

Example:

```text
transport:HTTP
```

Later interaction:

```text
Unix domain sockets might be better.
Let's compare them.
They may simplify local deployment.
```

No supported adoption occurred.

The state may remain:

```text
transport:HTTP
```

Different interaction:

```text
We completed the migration.
Local transport now uses Unix domain sockets.
HTTP is no longer used locally.
```

The state becomes:

```text
transport:Unix domain sockets
```

The difference is not recency.

The difference is supported transition.

A DSU generator should therefore avoid universal rules such as:

```text
latest statement wins
```

or:

```text
most repeated statement wins
```

The complete context must be interpreted jointly.

---

## 13. Uncertainty and Conflict Are Part of State

A resultant state is not always a single resolved truth.

The active state may contain:

* ambiguity;
* uncertainty;
* disagreement;
* unresolved contradiction;
* provisional decisions;
* competing requirements.

Example:

```text
deployment:local-only current requirement
cloud requirement:status unresolved
```

This may be more accurate than forcing either:

```text
deployment:local-only
```

or:

```text
deployment:cloud-enabled
```

A DSU must preserve uncertainty when the available context does not support resolution.

Invented certainty is state corruption.

---

## 14. Loss Is Expected

A DSU is deliberately lossy.

This is not an accidental limitation.

A representation that attempts to preserve every historical detail would cease to serve its intended role.

The relevant distinction is not:

```text
loss vs no loss
```

but:

```text
what was lost
whether it still mattered
whether the loss affected continuation
```

A DSU may omit:

* detailed reasoning paths;
* repeated explanations;
* resolved questions;
* obsolete alternatives;
* narrative transitions;
* low-impact examples;
* historical sequence;
* temporary states.

Such omissions may be acceptable when they no longer alter future continuation.

---

## 15. Information Loss and Continuation Failure Are Different

An omitted detail does not automatically imply a practical continuity failure.

At least three notions of loss should be distinguished.

### Raw information loss

Information is absent from the DSU.

### Observable functional loss

The omission causes a downstream failure.

### Residual unrepaired consequential loss

The omission produces a failure that remains after ordinary continuation had opportunities to reconstruct, correct, reintroduce, supersede, or otherwise neutralize the gap.

These are not equivalent.

A DSU may have substantial raw information loss while maintaining strong functional continuity.

History compaction is also lossy.

DSUs are not uniquely exposed to omission.

The meaningful comparison is between different preservation targets under finite context budgets.

---

## 16. Gap Dynamics

Omissions do not necessarily remain static.

A missing detail may later be:

### Reconstructed

The receiving model infers it from preserved constraints, prior knowledge, or active context.

### Reintroduced

The user, environment, artifact, retrieval system, or later input supplies it again.

### Corrected

A contradiction or failure exposes the missing information and forces repair.

### Superseded

A later decision makes the missing detail obsolete.

### Rendered non-consequential

Later state evolution removes the practical relevance of the omitted detail.

This last case may be described informally as **gap dissolution**.

The key principle is:

> **A gap is not automatically permanent semantic debt.**

A DSU should therefore be evaluated over continued interaction, not only by immediate source reconstruction.

---

## 17. Reconstructive Continuity

Useful continuation depends on more than the DSU alone.

It may depend on:

* the receiving model;
* model priors;
* current user input;
* active artifacts;
* environment;
* correction;
* retrieval;
* later evidence;
* continuing interaction.

Therefore:

```text
continuation quality != information contained exclusively in checkpoint
```

A DSU participates in a larger interactive system.

This does not excuse arbitrary omission.

It means that practical continuity should be evaluated under realistic conditions rather than by textual retention alone.

The relevant question is:

> **Does the omitted information survive as consequential unrepaired loss?**

A second important principle follows:

> **History compaction and DSUs are both lossy; the practical question is which preservation target provides better continuation under the available context budget.**

---

## 18. Regeneration

A DSU is not a frozen endpoint.

Interaction continues.

The state evolves.

A later DSU should represent the evolved resultant state.

```text
DSU_t
+ continued interaction
+ corrections
+ new evidence
+ supported transitions
-> consolidation
-> DSU_t+1
```

The next DSU is not expected to reproduce the previous DSU mechanically.

It should preserve persistent state and revise what has actually changed.

---

## 19. Interactive Regeneration

Repeated transformation without new external interaction can accumulate drift:

```text
DSU_0 -> DSU_1 -> DSU_2 -> DSU_3
```

Once a distinction is removed, no external source may remain to restore it.

Interactive regeneration differs:

```text
DSU_0
-> real interaction
-> DSU_1
-> real interaction
-> DSU_2
```

Continued interaction may provide:

* new evidence;
* repair opportunities;
* correction;
* contradiction detection;
* reintroduction of missing facts;
* state transitions that render prior gaps irrelevant.

Interactive regeneration is therefore an open process rather than recursive self-copy.

Whether it systematically reduces degradation is an empirical question, not a guaranteed property.

---

## 20. DSU as a Semantic Checkpoint

A useful mental model is:

> **A DSU is a semantic checkpoint, not a historical archive.**

Traditional checkpoints attempt to preserve computational state exactly or near-exactly.

A DSU preserves interpreted semantic state approximately.

It is:

* lossy;
* language-based;
* designed for direct LLM interpretation;
* non-canonical;
* model-conditioned;
* directly reusable;
* regenerable;
* inspectable.

It is not:

* reversible compression;
* exact state serialization;
* a transcript;
* a formal proof;
* hidden-state transfer.

The checkpoint analogy is useful because the purpose is to continue from the state reached.

---

## 21. Context Renewal

A DSU enables a form of context renewal.

A long interaction may accumulate significant inferential baggage.

Instead of continuing indefinitely with:

```text
entire trajectory
+ obsolete states
+ repeated explanations
+ active state
+ new interaction
```

a system may continue from:

```text
DSU
+ recent interaction
+ current task
+ relevant artifacts
```

This does not claim that removed history has no value.

It means that history does not need to remain permanently active in the inference context.

The process can be represented as:

```text
long interaction
      |
      v
semantic consolidation
      |
      v
DSU
      |
      v
renewed active context
      |
      v
continued inference
```

This is especially relevant under limited context budgets.

---

## 22. Parallel Memory Architecture

A DSU naturally fits into a multi-layer system.

Example:

```text
                    +------------------+
                    |  literal history |
                    +------------------+

                    +------------------+
                    | compacted history|
                    +------------------+

interaction ------> +------------------+
                    |       DSU        |
                    | active semantic  |
                    |      state       |
                    +------------------+

                    +------------------+
                    | artifacts / logs |
                    +------------------+

                    +------------------+
                    | retrieval layer  |
                    +------------------+
```

The DSU is not required to carry every function.

Historical fidelity can live elsewhere.

Detailed recovery can live elsewhere.

Artifacts can live elsewhere.

The DSU focuses on active consequential state.

---

## 23. Orthogonality to Graphs, Retrieval, Skills, and Agent Instructions

A DSU does not compete with graphs, RAG, skills, agent configuration files, or other memory and orchestration mechanisms.

These mechanisms address different system concerns.

### Graphs

Graphs primarily provide structured representation of entities and relations.

They may answer questions such as:

* what entities exist;
* how they are related;
* what depends on what;
* what path connects two nodes.

A graph does not by itself determine which explored alternative became adopted state, which prior state was superseded, or which contradiction remains unresolved.

Those are semantic consolidation questions.

A DSU may therefore be projected into a graph, generated from graph-backed context, or used alongside graph memory.

### Retrieval and RAG

Retrieval systems select and reintroduce potentially relevant information.

They may recover:

* historical evidence;
* prior decisions;
* external documents;
* omitted details;
* contradictory sources;
* task-relevant artifacts.

Retrieval does not by itself determine what remains in force after the retrieved material is interpreted jointly.

A DSU may therefore participate before, after, or alongside retrieval:

```text
DSU -> retrieval query context -> retrieved evidence -> updated DSU

retrieval -> relevant evidence -> DSU consolidation

active DSU + retrieval layer + history
```

### Skills and Procedures

Skills primarily encode reusable capabilities, procedures, or task methods.

They may describe:

* how to deploy;
* how to review code;
* how to use an API;
* how to execute a recurring workflow.

A DSU instead represents contingent semantic state such as:

```text
deployment:local-only;release:blocking failure unresolved;transport:Unix domain sockets
```

A skill may act on objectives and constraints represented in a DSU.

The two mechanisms are complementary.

### Agent Instructions and `AGENTS.md`

Persistent agent instructions primarily govern how an agent should behave or operate.

For example:

```text
run tests before commit
do not modify generated files
```

A DSU may simultaneously represent:

```text
feature:X implemented;tests:2 failing;generated files:untouched;release:blocking failure unresolved
```

The distinction is:

```text
agent instructions = how to act
DSU = what consequential state remains in force
```

One may govern behavior while the other represents the contingent state from which reasoning continues.

### Different Axes, Not Competing Replacements

The relevant contrast is therefore not:

```text
DSU vs graphs
DSU vs RAG
DSU vs skills
DSU vs AGENTS.md
```

It is closer to:

```text
DSU -> representation of consequential resultant state
graph -> structured entities and relations
RAG -> selective retrieval and reintroduction
skill -> reusable capability or procedure
agent instructions -> persistent behavioral or operational guidance
summary -> reduced account of source content or trajectory
```

These mechanisms can be combined in many directions:

```text
retrieval -> relevant evidence -> DSU consolidation
DSU -> retrieval planning -> evidence -> updated DSU
graph state -> DSU consolidation
DSU -> graph projection
DSU + skills + agent instructions -> continued inference
```

The DSU claim is therefore not that existing memory, retrieval, graph, summarization, or orchestration mechanisms should be replaced.

The claim is narrower:

> **Consequential resultant state is a distinct representational target, and it may be useful to materialize that target explicitly in a dense language-based form for continued inference.**

This orthogonality is already compatible with a parallel memory architecture in which history, compacted history, DSUs, graphs, retrieval indexes, artifacts, logs, skills, and persistent instructions coexist.

## 24. Direct LLM Interpretation

A DSU is represented in language rather than in a model-specific hidden format.

It is designed for direct interpretation by capable LLMs.

For example:

```text
project:X;architecture:monolith;deployment:local-only;storage:SQLite;external deps:none;cloud support:unresolved
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

rather than:

```text
encoded state -> mandatory specialized decoder -> reconstructed context -> LLM
```

A DSU does not inherently require a mandatory:

* specialized parser;
* decoder;
* vector lookup;
* graph engine;
* hidden-state transfer mechanism;
* model-specific serialization format.

External systems may still use such mechanisms around DSUs when useful.

Direct interpretation does not imply invariant interpretation.

Different models may interpret the same DSU differently depending on:

* capabilities;
* training;
* priors;
* active system context;
* current input.

---

## 25. Relational and Scope Integrity

Aggressive density introduces risk.

A DSU must preserve not only facts but the structure connecting them.

Important properties include:

* entity identity;
* relation binding;
* negation scope;
* condition scope;
* uncertainty scope;
* temporal scope;
* local vs global applicability;
* exception boundaries.

Example:

```text
auth:disabled,test only
```

may be ambiguous.

A clearer DSU may need:

```text
auth disabled only in test environment
```

Density should not destroy relational integrity.

A useful principle is:

> **Never trade consequential scope integrity for superficial token reduction.**

---

## 26. Primary Failure Modes

A DSU fails when consolidation changes the effective state incorrectly.

Important failure classes include:

### Transition errors

* exploration treated as adoption;
* proposal treated as decision;
* possibility treated as requirement;
* temporary state treated as current state.

### Scope errors

* local rule generalized globally;
* exception merged into default;
* distinct entities collapsed.

### Epistemic errors

* uncertainty erased;
* conflict falsely resolved;
* possibility converted into fact;
* confidence invented.

### Persistence errors

* obsolete state retained;
* valid prior state overwritten by verbose exploration;
* prior DSU treated as unquestionable truth.

### Omission errors

* critical constraint lost;
* active dependency dropped;
* consequential negation removed;
* operational literal corrupted.

### Relation errors

* unsupported relation invented;
* causality invented;
* temporal ordering invented.

These failures matter more than raw compression ratio.

---

## 27. Evaluation

A DSU should not be evaluated primarily by textual similarity to source history.

More relevant measures include:

* decision retention;
* constraint retention;
* critical negation retention;
* uncertainty preservation;
* state transition accuracy;
* rejected-branch resurrection;
* invented commitments;
* stale-state persistence;
* scope integrity;
* relation integrity;
* downstream decision divergence;
* gap recovery;
* residual unrepaired consequential loss;
* token cost;
* latency;
* peak context pressure;
* cross-session continuity;
* cross-model usability;
* continuation quality over subsequent interaction.

A central evaluation question is:

> **Can future inference continue correctly from the DSU without carrying the full inferential trajectory that produced it?**

A particularly relevant comparison is:

```text
history compaction vs DSU
under equal or comparable active-context budgets
```

The objective is not to prove that one representation is universally superior.

The objective is to compare different preservation targets under realistic constraints.

---

## 28. Discourse-Imbalance Resistance

A useful test is to hold effective state constant while changing textual prominence.

Case A:

```text
established decision:E
brief exploration of alternative:B
no adoption
```

Case B:

```text
established decision:E
very long repeated exploration of alternative:B
no adoption
```

If the effective state did not change, both should produce functionally similar DSUs.

For example:

```text
decision:E
```

This tests whether consolidation follows semantic state rather than discourse volume.

---

## 29. Resultant-State Tests

Another useful evaluation family directly tests the distinction between trajectory and result.

Input:

```text
A proposed
B explored
A restored
C tested
C rejected
E adopted
```

Expected state-oriented output:

```text
state:E
```

or, only when still consequential:

```text
state:E;C:rejected
```

The purpose is not to reproduce the sequence.

The purpose is to preserve what remains in force.

---

## 30. DSU and DeSU

A DSU is the artifact.

DeSU is one generator.

```text
DeSU(input context) -> DSU
```

DeSU is a prompt-based consolidation policy that instructs a capable language model to infer and emit consequential resultant state.

DeSU may implement rules such as:

```text
exploration != adoption
repetition != validation
volume != commitment
recency != centrality
prior consolidation != truth
```

It may also instruct the model to:

* preserve effective state absent supported change;
* revise state when supported transitions occur;
* preserve uncertainty when unresolved;
* avoid inventing relations;
* avoid merging non-equivalent entities or scopes;
* produce a dense language-based representation designed for direct LLM interpretation.

The DSU concept is broader than any particular generator.

DeSU is one implementation of the generation process.

---

## 31. Minimal Formal View

Without claiming mathematical completeness, the conceptual transformation can be expressed as:

```text
T = accumulated context and trajectory
R(T) = resultant semantic state inferred from T
C(R) = consequential projection of R
D(C(R)) = dense language-based representation

DSU = D(C(R(T)))
```

The important point is that the intended transformation is not:

```text
DSU = shorter(T)
```

It is closer to:

```text
DSU = dense(consequential(resultant_state(T)))
```

`C` should not be interpreted as literal subset selection.

Consequential projection may involve:

* preservation;
* integration;
* reorganization;
* reformulation;
* relation consolidation;
* uncertainty retention;
* supported state transition.

The constraint is that consequential semantic structure must not be invented or altered without support.

This is the core conceptual separation from history compaction.

---

## 32. Canonical Short Definition

> **A Dense Semantic Unit (DSU) is a dense, language-based representation of consequential resultant state, designed for direct interpretation by capable LLMs. It captures what remains semantically in force after prior context and may still affect future continuation.**

---

## 33. Extended Definition

> **A Dense Semantic Unit (DSU) is a lossy semantic checkpoint that materializes the consequential resultant state resulting from prior interaction, reasoning, or task activity. It preserves what remains in force for future reasoning, answers, actions, or interpretation while allowing historical trajectory, obsolete inference, repetition, resolved process, and other non-consequential residue to remain outside the active representation. A DSU does not replace history, history compaction, retrieval, or archival storage; it serves a different role as dense active semantic state for continued inference.**

---

## 34. One-Sentence Contrast

> **History compaction preserves a reduced representation of the path; a DSU preserves a dense representation of what remains true, active, constrained, uncertain, unresolved, or otherwise consequential after the path.**

---

## 35. Foundational Principles

The framework can be reduced to the following principles:

1. **Trajectory and resultant state are different objects.**
2. **DSUs represent consequential resultant state, not compressed history.**
3. **Both history compaction and DSUs are lossy; they optimize different preservation targets.**
4. **Historical information may exist in parallel and be retrieved or compacted on demand.**
5. **Information useful during inference may become unnecessary after producing state.**
6. **Resultant-state consolidation may remove obsolete inferential residue from active context.**
7. **Exploration is not adoption, repetition is not validation, volume is not commitment, and recency is not centrality.**
8. **Previously consolidated state has persistence but not immunity from revision.**
9. **Uncertainty, conflict, negation, limits, relations, and scope are part of state and must not be erased for density.**
10. **Raw omission is not identical to functional failure.**
11. **Gaps may be reconstructed, reintroduced, corrected, superseded, or rendered non-consequential by state evolution.**
12. **The primary concern is residual unrepaired consequential loss.**
13. **A DSU is a semantic checkpoint for continued inference, not an archive of how the checkpoint was reached.**
14. **Density is subordinate to preservation of consequential semantic structure.**
15. **A DSU is language-based and designed for direct interpretation by capable LLMs without requiring a mandatory model-specific decoding mechanism.**
16. **The purpose of a DSU is to continue from where the system is without dragging the entire inferential baggage of how it got there.**
