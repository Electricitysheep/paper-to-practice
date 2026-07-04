# Agent Systems — From Lab to Production

> **20+ papers reviewed** | Key insight: Multi-agent > single-agent. Simple wins in production.

---

## 📊 The Big Picture

2026 H1 marked the transition of AI Agents from research prototypes to production systems. The [MAP study](https://arxiv.org/abs/2512.04123) (ICML 2026 Spotlight) — the first large-scale empirical study of production agents — revealed surprising truths:

| Finding | Percentage |
|---------|------------|
| Agents executing ≤10 steps before human intervention | **68%** |
| Teams using prompting (not fine-tuning) | **70%** |
| Relying primarily on human evaluation | **74%** |
| Top challenge: Reliability (not capability) | **#1** |

---

## 🔬 Key Papers

### 1. MAP: Measuring Agents in Production
- **Authors**: UC Berkeley, Stanford et al. | **Venue**: ICML 2026 Spotlight
- **arXiv**: [2512.04123](https://arxiv.org/abs/2512.04123)
- **TL;DR**: First large-scale empirical study of production AI agents. 20 in-depth case-study interviews plus a survey of 86 practitioners across 26 domains.
- **Key Findings**:
  - 68% of agents execute ≤10 steps before human intervention
  - 70% rely on prompting off-the-shelf models
  - Reliability is the #1 challenge, addressed through system-level design
- **💡 For Practitioners**: Don't over-engineer. Start with simple prompt chains. Design human checkpoints every 5-10 steps. Invest in harness infrastructure before chasing model upgrades.

### 2. DeLM: Decentralized Multi-Agent Systems
- **Authors**: Yuzhen Mao, Azalia Mirhoseini | **Institution**: Stanford
- **arXiv**: [2606.10662](https://arxiv.org/abs/2606.10662)
- **TL;DR**: Breaks the centralized multi-agent bottleneck. Agents asynchronously claim tasks, read accumulated progress, and write verified updates through a shared context.
- **Key Results**: +10.5pp on SWE-bench Verified, ~50% cost reduction. +5.7pp on LongBench-v2.
- **💡 For Practitioners**: When your agent system exceeds 5 sub-tasks, the central controller becomes the bottleneck. Switch to decentralized: shared verified context + task queue.

### 3. COMPASS: Three-Layer Agent Architecture
- **Authors**: Guangya Wan et al. | **Institution**: Google Cloud AI / UVa
- **Venue**: ACL 2026
- **TL;DR**: Splits agent into Main Agent (execution), Meta-Thinker (strategic oversight), and Context Manager (progress summaries).
- **Key Results**: Up to +20% on GAIA, BrowseComp, HLE vs single/multi-agent baselines.
- **💡 For Practitioners**: Context management is the core bottleneck for long tasks, NOT model capability. Separate your agent into execution, monitoring, and context roles.

### 4. Hyperagents: Self-Referential Agents
- **Authors**: Jenny Zhang et al. | **arXiv**: [2603.19461](https://arxiv.org/abs/2603.19461)
- **TL;DR**: Integrates task agent + meta agent into a single editable program. The meta-level modification procedure is itself editable.
- **Key Results**: Continuous self-improvement across coding, paper review, robotics, and math grading.
- **💡 For Practitioners**: Self-improving agents need editable meta-level processes. Design your agent's improvement mechanism to be as programmable as its task behavior.

### 5. Latent Agents (IMAD): Internalized Multi-Agent Debate
- **Venue**: ACL 2026 | **arXiv**: [2604.24881](https://arxiv.org/abs/2604.24881)
- **TL;DR**: Post-train a single LLM to internalize multi-agent debate. SFT + GRPO two-stage training.
- **Key Results**: Token consumption reduced by up to 93%. Activation steering proves separable agent subspaces in latent space.
- **💡 For Practitioners**: You don't need multiple agents for multi-perspective reasoning. A single model post-trained with IMAD can simulate expert debate at 93% lower cost.

### 6. SciOrch: Orchestrating Expert LLMs
- **Authors**: Jingru Guo et al. | **Institution**: Imperial/Oxford/CUHK/SJTU
- **arXiv**: [2606.15872](https://arxiv.org/abs/2606.15872)
- **TL;DR**: 8B orchestrator learns to decompose science questions, delegate to commercial models, and synthesize answers.
- **Key Results**: 56.66% accuracy, +3.74% over strongest single model. API cost: only $10.42.
- **💡 For Practitioners**: Small model + orchestration > large model alone. The orchestrator pattern is the most cost-effective strategy for complex tasks.

### 7. HACRL: Heterogeneous Agent Collaborative RL
- **Institution**: Beihang/Tsinghua/PKU | **Date**: March 2026
- **TL;DR**: Heterogeneous agents share verified rollouts during training, deploy independently during inference. Breaks the one-way knowledge distillation paradigm.
- **Key Results**: +3.3% avg performance, 50% less sampling cost.
- **💡 For Practitioners**: If you have multiple models of different sizes/architectures, let them learn from each other's rollouts during training. They can deploy independently.

---

## 🛠️ Production Reality Check (from MAP Study)

```
Academic papers assume:          Production reality:
┌─────────────────────┐         ┌─────────────────────┐
│ Fully autonomous     │         │ Human in the loop    │
│ Long reasoning chains│         │ ≤10 steps max        │
│ Fine-tuned models    │         │ Prompt engineering   │
│ Automated evaluation │         │ Manual review        │
│ Model capability     │         │ System reliability   │
└─────────────────────┘         └─────────────────────┘
```

---

## 💡 Consolidated Takeaways

1. **Keep it simple**: 68% of production agents run ≤10 steps. Design for this reality.
2. **Decentralize when scaling**: Central controllers become bottlenecks at 5+ sub-tasks.
3. **Context management > model capability**: Long task failures are context problems, not intelligence problems.
4. **Internalize multi-agent debate**: Save 93% cost by training one model to think from multiple perspectives.
5. **Orchestrator pattern**: Small model scheduling large models is the optimal cost/quality tradeoff.
6. **Heterogeneous collaboration**: Let different models learn from each other's training rollouts.

---

## 📎 Related Papers

- [KLong](https://arxiv.org/abs/2602.17547) — Training agents for extremely long-horizon tasks
- [LOGIGEN](https://arxiv.org/abs/2603.00540) — Logic-driven synthesis of verifiable agent tasks
- [ProAct](https://arxiv.org/abs/2602.05327) — Agentic lookahead in interactive environments
- [Lacuna](https://arxiv.org/abs/2605.28617) — Safe agents as recursive program holes (type-safe agents)
- [HarnessBridge](https://arxiv.org/abs/2606.12882) — Learnable harness controller for LLM agents
- [Graph-of-Agents](https://arxiv.org/abs/2604.17148) — Graph-based multi-agent collaboration

---

*Last updated: July 2026 · [Back to README](../README.md)*
