# DeSU Demo

This is a small practical demonstration of the behavior DeSU is intended to produce.

It is not a benchmark, a proof of correctness, or evidence that the approach is universally sufficient.

It is simply a record of one real use of the prompt.

## Setup

The model received the following project files together:

```text
CONCEPT.md

desu.txt

MOTIVATION.md

README.md
```

The user instruction was only:

```text
understand and condense this project
```

No custom retrieval pipeline, graph construction step, ontology, persistent memory service, chunking system, embedding index, or orchestration layer was added for this test.

The consolidation behavior came from the DeSU prompt contained in `desu.txt` and the model interpreting the project context.

## Result

The generated `.desu` checkpoint was:

```text
type:context;protocol:context_only;content:DeSU experimental GPLv3 prompt generator for Dense Semantic Units (DSUs): dense language-based lossy semantic checkpoints of consequential resultant state for direct capable-LLM interpretation, targeting what remains in force after interaction/reasoning rather than compressed trajectory; transformation≈context→infer resultant state→project future-consequential structure→dense record, not shorter(history); primary motivation: keep long local LLM sessions usable on constrained consumer hardware (RTX 3060), smaller capable models, finite VRAM/memory/context/latency by renewing active context, reducing token load and obsolete inferential clutter with minimal machinery (one capable model+one consolidation prompt→one dense checkpoint); preserve effective decisions,current facts,objectives,active constraints/prohibitions/critical negation,relations,scope,uncertainty/conflict,unresolved questions/dependencies,relevant temporal conditions,supported transitions,operational facts,exact consequential literals; remove filler,rhetoric,repetition,redundant support,obsolete exploration,superseded branches,resolved residue,temporary hypotheses,corrected mistakes,reconstructible narrative,low-impact examples,unnecessary source order/intermediate reasoning after its role is absorbed; consolidation jointly deduplicates,merges complementary state,reorganizes by semantic relation,resolves overlap/contradiction/state change only when supported; invariants:exploration!=adoption,repetition!=validation,volume!=commitment,recency!=centrality,prior consolidation!=truth; preserve prior effective state absent supported change,revise on supported addition/correction/invalidation/supersession/resolution/scope change/new uncertainty; never invent facts/entities/relations/causality/order/certainty or falsely resolve conflict; preserve distinct entities,local/global scope,negation,conditions,exceptions,epistemic state; density goal=max consequential semantic utility/token,never sacrifice consequential relational/scope integrity; DSU intentionally lossy/non-canonical/model-conditioned/directly reusable/regenerable/inspectable,not transcript/archive/reversible compression/formal proof/hidden-state transfer/canonical truth; raw omission!=functional failure,focus residual unrepaired consequential loss; gaps may be reconstructed,reintroduced,corrected,retrieved,superseded,or rendered non-consequential; regeneration:DSU_t+continued interaction/new evidence/corrections/supported transitions→DeSU→DSU_t+1,interactive regeneration may enable repair but systematic degradation reduction remains empirical; DSU complements rather than replaces raw/compacted history,RAG,retrieval,graphs,skills,AGENTS.md,artifacts/logs/persistent instructions,serving distinct role=active consequential semantic state for continuation; not by itself enterprise knowledge base or institutional archive,does not inherently provide provenance,auditability,access control,canonical records,governance,long-term consistency; candidate uses:local continuity under limited context,cross-session/project/task handoff,model switching,local/cloud handoff,context renewal,larger memory/retrieval integration; evaluation priorities:decision/constraint/negation/uncertainty retention,state-transition accuracy,scope/relation integrity,rejected-branch resurrection,invented commitments,stale-state persistence,downstream divergence,gap recovery,residual unrepaired consequential loss,token cost,latency,peak context pressure,cross-session/cross-model continuation,especially DSU vs history compaction under comparable budgets; open empirical questions:long-term regeneration,cross-model portability,discourse-imbalance resistance,gap recovery,continuation quality,history-compaction comparison; DeSU output contract:one line type:context;protocol:context_only;content:<dense_semantic_record> optionally ;rules:<explicit permissions/prohibitions/operational constraints>,context_only denotes context not action request; project files:desu.txt prompt,README.md overview,CONCEPT.md framework,MOTIVATION.md rationale,desu.svg logo; naming:DeSU keeps DSU visible and informally echoes Japanese です,not technical definition.
```

## What is notable about the result

The input consisted of multiple files with different roles:

- `CONCEPT.md` defined the conceptual framework;
- `desu.txt` defined the consolidation policy;
- `MOTIVATION.md` explained the practical and personal motivation;
- `README.md` presented the project, examples, scope, limitations, and usage context.

A source-oriented condensation could have produced something like:

```text
CONCEPT.md says ...
MOTIVATION.md says ...
README.md says ...
desu.txt instructs ...
```

The generated checkpoint did not primarily preserve those file boundaries.

Instead, it merged the project into a unified semantic state containing, among other things:

```text
conceptual target
+ generator behavior
+ practical motivation
+ preservation rules
+ state-transition policy
+ loss model
+ relation to RAG/graphs/skills/AGENTS.md
+ scope limits
+ evaluation agenda
+ project metadata
```

That is the intended behavior of DeSU: consolidate what remains semantically relevant across the complete input rather than independently shortening each source.

## Why this demo matters to the project

The practical motivation behind DeSU is intentionally modest.

The project was not created to build the most elaborate memory architecture possible. It was created to help keep long local LLM sessions usable under finite hardware, context, memory, and latency constraints.

For this demonstration, the operational shape was approximately:

```text
project files
+ one short user instruction
+ DeSU prompt
-> one dense semantic checkpoint
```

This is part of the design motivation.

A useful checkpoint does not always require a persistent graph, a retrieval pipeline, a custom memory service, or a large orchestration stack. Those systems may be valuable when the problem requires them, and DSUs may complement them. The point is narrower: additional machinery is not assumed to be a prerequisite for producing a useful dense continuation state.

## What this demo does not prove

This single example does not establish:

- universal semantic correctness;
- lossless preservation;
- superiority over summarization, graph memory, RAG, or history compaction;
- long-term regeneration stability;
- cross-model equivalence;
- enterprise knowledge-base suitability;
- optimal compression;
- reliable behavior for every model or every domain.

The generation time was not measured as a formal benchmark, so this demo makes no quantitative latency claim.

The result is model-conditioned and lossy by design.

## What it does illustrate

It illustrates the core engineering motivation:

> A capable model, given a single consolidation prompt, can sometimes turn heterogeneous project context into a compact unified semantic checkpoint with very little surrounding machinery.

Whether that checkpoint is good enough should be evaluated by continuation behavior, preservation of consequential state, operational cost, and residual unrepaired consequential loss rather than by source reconstruction alone.

## Minimal reproduction pattern

```text
1. Provide `desu.txt` as the consolidation instruction.
2. Provide the context to consolidate.
3. Ask the model to understand and condense the material.
4. Save the resulting one-line DSU as a checkpoint.
5. Use the checkpoint as context for continued work.
```

A minimal user instruction may be as small as:

```text
understand and condense this project
```

The exact result will depend on the generating model and the supplied context.
