# Long-Horizon Tasks & Memory — The Final Frontier for Agents

> **8+ papers reviewed** | Key insight: Memory recovery rate ~0.6 even when tasks succeed. Being useful ≠ remembering users.

---

## 🔬 Key Papers

### 1. KLong: Training for Extremely Long-Horizon Tasks
- **arXiv**: [2602.17547](https://arxiv.org/abs/2602.17547)
- **TL;DR**: Trajectory-splitting SFT + progressive RL. 106B model beats Kimi K2 Thinking (1T) by 11.28% on PaperBench.
- **Key Innovation**: Research-Factory — automated pipeline that collects papers, builds rubrics, generates long-horizon trajectories.
- **💡 For Practitioners**: Long-horizon training is about trajectory management, not model size. Split trajectories with overlap, progressively extend RL timeouts.

### 2. MEMPROBE: Probing Agent Memory Quality
- **arXiv**: [2606.24595](https://arxiv.org/abs/2606.24595)
- **TL;DR**: First benchmark measuring memory as an auditable artifact — can you reconstruct user state from what the agent remembers?
- **Key Finding**: Task completion nearly saturates, but memory recovery rate is only ~0.6. Drops further under top-k retrieval.
- **💡 For Practitioners**: Start measuring memory recovery rate, not just task success. Your agent may be "useful" but "forgetful."

### 3. SJTU/Tsinghua: Agent-Native Memory Systems
- **arXiv**: [2606.24775](https://arxiv.org/abs/2606.24775)
- **TL;DR**: Systematic study from data management perspective. Decomposes memory into 4 modules.
- **Key Finding**: No single architecture dominates. Local maintenance > global reorganization for cost efficiency.
- **💡 For Practitioners**: Design memory like a database, not a log. Match memory type to task type: timeline for events, semantic graph for conversations, state log for databases.

### 4. Agent-BRACE: Belief State Decoupling
- **arXiv**: [2605.11436](https://arxiv.org/abs/2605.11436)
- **TL;DR**: Decouples agent into belief state model and policy model. Belief state = natural language claims with confidence labels.
- **Key Results**: +14.5% improvement on 3B model. Constant context window regardless of episode length.
- **💡 For Practitioners**: Explicitly modeling uncertainty improves decision quality in partially observable environments.

### 5. ProAct: Agentic Lookahead
- **arXiv**: [2602.05327](https://arxiv.org/abs/2602.05327)
- **TL;DR**: Grounded LookAhead Distillation (GLAD) + Monte-Carlo Critic. Distills search trees into concise reasoning chains.
- **Key Results**: 4B model rivals SOTA closed-source models on 2048 and Sokoban.
- **💡 For Practitioners**: Long-horizon planning can be learned through distilled search experience, not runtime tree search.

---

## 💡 Consolidated Takeaways

1. **Trajectory management > model size**: KLong proves split-then-train beats bigger models.
2. **Measure memory quality separately**: MEMPROBE shows task success ≠ memory quality.
3. **Match memory to task**: Timeline, semantic graph, state log — different tasks need different memory.
4. **Model uncertainty explicitly**: Agent-BRACE shows confidence-labeled beliefs improve decisions.
5. **Distill search, don't run it**: ProAct shows search tree knowledge can be compressed into model weights.

---

*Last updated: July 2026 · [Back to README](../README.md)*
