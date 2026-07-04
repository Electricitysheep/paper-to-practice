# Memory System Design

> Designing agent memory that actually works — based on MEMPROBE, the SJTU/Tsinghua agent-native memory study, and long-horizon papers.

---

## ⚠️ The Uncomfortable Truth

**More memory ≠ better task success.**

MEMPROBE ([2606.24595](https://arxiv.org/abs/2606.24595)) probed what agents actually recall and found a gap between *storing* information and *using* it. You can have a huge memory store and still fail the task because the right fact was never retrieved at the right moment.

**💡 Design principle:** optimize for *recall at decision time*, not for storage volume.

---

## 🧩 Match Memory Type to Task Type

Don't default to "vector DB for everything." The SJTU/Tsinghua agent-native memory work ([2606.24775](https://arxiv.org/abs/2606.24775)) treats memory as a first-class component, matched to the task:

| Task shape | Memory structure | Why |
|---|---|---|
| Event / temporal | **Timeline** (ordered log) | Order and recency matter |
| Conversational | **Semantic graph** | Entities & relations, not raw turns |
| Database / API / tools | **State log** | Exact current state, replayable |
| Long-horizon reasoning | **Belief state** (decoupled) | Survives context-window limits |

---

## 🏗️ Core Architecture Patterns

### 1. Append-only + compaction views
```
□ Never mutate history — append events
□ Build compacted "views" for the model's working context
□ Keep the full log for audit and recovery
```

### 2. Decouple belief state from context window
Agent-BRACE ([2605.11436](https://arxiv.org/abs/2605.11436)) separates *what the agent believes* from *what's in the prompt*. This is what lets agents survive tasks longer than the context window.
```
□ Maintain an explicit belief/state object
□ Reconstruct the prompt from it each step (don't just append forever)
```

### 3. Local maintenance, not global rebuilds
```
□ Update the slice of memory that changed
□ Avoid re-embedding / re-summarizing the whole store every turn
```

---

## 📏 Long-Horizon: Training > Raw Size

KLong ([2602.17547](https://arxiv.org/abs/2602.17547)) showed a **106B model beat a 1T model on PaperBench** — because it was *trained* for long-horizon tasks. For long tasks, how you train the agent to manage state beats simply scaling parameters.

Pair this with **ProAct** ([2602.05327](https://arxiv.org/abs/2602.05327)): agentic *lookahead* — anticipate future needs instead of purely reacting.

---

## ✅ Design Checklist

```
□ Chose memory structure by task type (not "vector DB by default")
□ Append-only storage with compaction views
□ Belief state decoupled from the context window
□ Local incremental maintenance (no global rebuilds)
□ Retrieval measured at decision time (MEMPROBE-style probe)
□ Periodic "memory recovery" audit — can the agent still find old facts?
□ Full audit trail for every memory write
```

---

## 🚨 Common Mistakes

1. **Hoarding** — storing everything, retrieving the wrong thing.
2. **Passive accumulation** — appending raw history until the agent loses coherence (~10+ turns).
3. **One structure for all tasks** — timelines and semantic graphs solve different problems.
4. **Never auditing recall** — assuming stored = usable.
5. **Scaling params instead of training for long horizons** — KLong shows method wins.

---

*Based on memory & long-horizon papers — see [Long-Horizon & Memory](../topics/long-horizon-memory.md) · [Back to README](../README.md)*
