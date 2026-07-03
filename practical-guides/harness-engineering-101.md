# Practical Guide: Harness Engineering 101

> The 98% of your agent system that determines success or failure

---

## 🎯 What is a Harness?

The **harness** is everything between the model and the user:

```
User Request
    │
    ▼
┌──────────────────────────────────────┐
│           THE HARNESS (98%)           │
│                                      │
│  ┌──────────┐  ┌──────────────────┐  │
│  │ Context   │  │ Tool Integration │  │
│  │ Manager   │  │ + Type Safety    │  │
│  └──────────┘  └──────────────────┘  │
│                                      │
│  ┌──────────┐  ┌──────────────────┐  │
│  │ Memory    │  │ Safety Guardrails│  │
│  │ System    │  │ + Sandboxing     │  │
│  └──────────┘  └──────────────────┘  │
│                                      │
│  ┌──────────────────────────────────┐│
│  │  Evaluation + Monitoring + Audit ││
│  └──────────────────────────────────┘│
└──────────────────────────────────────┘
    │
    ▼
┌──────────────────────────────────────┐
│         THE MODEL (2%)               │
│    Just generates text/tokens        │
└──────────────────────────────────────┘
```

The MAP study (ICML 2026) confirmed: **swapping model families no longer changes outcomes much.** The harness is where production agents win or lose.

---

## 🏗️ The 5-Layer Harness Architecture

Based on synthesis of Anthropic's agent engineering guides, OpenAI's Codex harness practice, and 20+ case studies from the MAP research:

### Layer 1: Context Management

```
Principle: APPEND-ONLY STORAGE + PROJECTION AT READ TIME
```

- Never delete transcripts. Compaction produces a VIEW, not a mutation.
- This preserves audit trails — critical for EU AI Act compliance.
- When context approaches limits, compress into structured summaries, not truncation.

### Layer 2: Tool Integration

```
Principle: TYPED TOOLS WITH COMPILE-TIME VALIDATION
```

- Every tool has a type signature: `tool[T](input) → Output`
- The model proposes tool calls; the harness type-checks BEFORE execution.
- Rejected calls never reach the environment (Lacuna pattern).
- Benefits: prevents prompt injection from reaching tools, catches malformed calls.

### Layer 3: Memory System

```
Principle: FOUR MODULES, TASK-SPECIFIC GRANULARITY
```

The SJTU/Tsinghua study (2606.24775) decomposed agent memory into:
1. **Representation & Storage**: How is memory structured? (timeline, semantic graph, state log)
2. **Extraction**: What gets saved? (key facts, decisions, state changes)
3. **Retrieval & Routing**: How is relevant memory found? (semantic search, temporal query)
4. **Maintenance**: How is memory kept fresh? (local updates, not global rebuilds)

**Key finding**: No single architecture works for all tasks. Match memory design to task type.

### Layer 4: Safety Guardrails

```
Principle: LAYERED DEFENSE WITH SELF-VERIFICATION
```

1. **Type system** (Lacuna): Compile-time rejection of unsafe actions
2. **Vector alignment** (LLM-VA): Minutes to deploy, no training needed
3. **Self-verification** (SInternal): Train model to verify its own outputs
4. **Process monitoring** (ProCeedRL): Real-time intervention at critical steps

### Layer 5: Evaluation & Monitoring

```
Principle: MEASURE WHAT MATTERS, NOT JUST WHAT'S EASY
```

The MAP study found:
- 74% of production agents rely primarily on HUMAN evaluation
- This is unsustainable at scale
- Build automated regression suites with:
  - Representative task sets with expected outcomes
  - Adversarial inputs (prompt injection, missing fields, ambiguity)
  - Run on every model/prompt/tool change

---

## 📋 Production Agent Checklist

```
□ Context Management
  □ Append-only storage with compaction views
  □ Structured summaries, not truncation
  □ Full audit trail preservation

□ Tool Integration
  □ Type signatures for all tools
  □ Compile-time validation before execution
  □ Rejected calls leave environment untouched
  □ Tool registry with versioning

□ Memory System
  □ Task-matched memory granularity (timeline/semantic/state)
  □ Local maintenance, not global rebuilds
  □ Periodic memory recovery audit (MEMPROBE approach)

□ Safety Guardrails
  □ LLM-VA vector alignment (minutes, no training)
  □ Type-checked agent actions (Lacuna)
  □ Self-verification training (SInternal)
  □ Human checkpoint every 5-10 steps

□ Evaluation & Monitoring
  □ Automated regression test suite
  □ Adversarial input testing
  □ Drift detection on prompts/models/tools
  □ Structured audit logs
```

---

## 📊 Harness Design Patterns

| Pattern | When to Use | Example |
|---------|-------------|---------|
| **Supervisor + Workers** | Complex tasks with independent sub-parts | Supervisor owns plan and commits; workers explore in clean windows |
| **ReAct Loop** | Simple, well-defined tools | Think → Act → Observe → Repeat |
| **Decentralized Queue** | 5+ parallel sub-tasks | Shared context + async task claiming (DeLM) |
| **Orchestrator** | Multiple heterogeneous models | Small model routes to specialized large models (SciOrch) |
| **Type-Safe Agent** | High-risk operations | `agent[T](task)` — type-checked before execution (Lacuna) |

---

## 🚫 Common Mistakes

1. **Chasing model leaderboards**: MAP study: model choice explains <5% of production success variance.
2. **Over-engineering autonomy**: 68% of agents run ≤10 steps. Design for this reality.
3. **Neglecting context management**: Passive history accumulation is the #1 cause of long-task failure.
4. **Skipping evaluation infrastructure**: "We'll evaluate later" = "We'll never evaluate."
5. **Ignoring type safety**: Compile-time checks are cheaper than runtime failures.

---

## 📎 References

- [MAP Study](https://arxiv.org/abs/2512.04123) — Measuring Agents in Production (ICML 2026 Spotlight)
- [Anthropic Agent Design Guide](https://docs.anthropic.com/en/docs/agents-and-tools) — Official agent engineering guides
- [The 98% Problem](https://labs.beconfident.app/papers/harness-engineering-survey) — Harness Engineering Survey (June 2026)
- [Awesome Agent Harness](https://github.com/HKUST-KnowComp/Awesome-Agent-Harness) — Curated harness research papers

---

*Last updated: July 2026 · [Back to README](../README.md)*
