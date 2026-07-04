# Reinforcement Learning — The Dominant Training Paradigm of 2026

> **15+ papers reviewed** | Key insight: GRPO + Process Rewards. SFT first, RL second.

---

## 📊 The Big Picture

If 2025 was RL's "trial year" in LLM training, 2026 H1 was the year RL took over. From DeepSeek-R1/R2 to Kimi k1.5, from STARE to T-STAR, RL became the **standard recipe** for training reasoning models and agents.

---

## 🔬 Key Papers

### 1. DeepSeek-R1 Technical Report (v2)
- **Authors**: DeepSeek-AI | **arXiv**: [2501.12948v2](https://arxiv.org/abs/2501.12948)
- **Date**: January 2026
- **TL;DR**: Expanded 60 pages disclosing the full R1 training pipeline. Three-stage "Dev" process. Admitted MCTS failure for general reasoning.
- **Key Innovation**: Established GRPO (Group Relative Policy Optimization) as the standard RL algorithm for reasoning training.
- **💡 For Practitioners**: GRPO + verifiable rewards (RLVR) is the proven recipe. Don't waste time on MCTS for general reasoning tasks — DeepSeek tried and failed.

### 2. Kimi k1.5: Multimodal LLM RL Scaling
- **Authors**: Moonshot AI | **arXiv**: [2501.12599](https://arxiv.org/abs/2501.12599)
- **Date**: January 2026
- **TL;DR**: Released same day as DeepSeek-R1. Demonstrated RL scaling for multimodal LLMs.
- **Key Innovation**: Used verifiable rewards instead of process reward models (PRM). No human feedback needed.
- **💡 For Practitioners**: Verifiable rewards > human feedback for scalable RL training. Design tasks with automatically verifiable outcomes.

### 3. STARE: Solving Entropy Collapse in RL Training
- **Authors**: Tsinghua / Tencent Hunyuan | **arXiv**: [2606.19236](https://arxiv.org/abs/2606.19236)
- **Date**: June 2026
- **TL;DR**: Discovered word-level causes of "strategy entropy collapse" in RL training. Proposed STARE method.
- **Key Results**: +4-8% AIME accuracy across 1.5B-32B models.
- **💡 For Practitioners**: If your RL-trained model seems to "stop improving" or converges to repetitive strategies, check for entropy collapse. STARE's entropy-targeted closed-loop control can fix this.

### 4. T-STAR: Tree-Structured Self-Correction
- **Venue**: ACL 2026 Findings
- **TL;DR**: Merges multiple sampled trajectories into a Cognitive Tree. Identifies critical divergence points. Synthesizes corrective reasoning by comparing success/failure branches.
- **💡 For Practitioners**: Don't wait for full task failure to retry. Identify the exact step where trajectories diverge and intervene there.

### 5. ProCeedRL: Process Critic with Exploratory Demonstration
- **Venue**: ACL 2026 Findings
- **TL;DR**: Identified the "vicious cycle" in agent exploration — suboptimal actions → noisy observations → degraded decisions. Process critic monitors and intervenes in real-time.
- **💡 For Practitioners**: Add real-time process monitoring to your agent. Catch and rewind adverse steps before they compound.

### 6. SPARK: Strategic Dynamic Branching Exploration
- **Venue**: ACL 2026
- **TL;DR**: Adaptive branching at critical decision states for resource-efficient exploration. Prioritizes sample quality over blind coverage.
- **Key Results**: Higher success rates with significantly fewer training samples.
- **💡 For Practitioners**: Not all steps deserve equal exploration budget. Identify critical decision points and branch there.

### 7. SOAR: Learning from Environment Observations
- **Venue**: ACL 2026
- **TL;DR**: Uses observation token entropy as supervision signal. Agent learns from environmental feedback, not just outcome rewards.
- **Key Results**: +16.9% on deep research tasks.
- **💡 For Practitioners**: Your agent's environment observations contain valuable learning signals. Don't just look at final success/failure.

### 8. LangMARL: Natural Language Multi-Agent RL
- **arXiv**: [2604.00722](https://arxiv.org/abs/2604.00722)
- **TL;DR**: First framework bringing credit assignment and policy gradients from classical MARL into language space.
- **💡 For Practitioners**: Multi-agent RL is now possible in pure language space. Centralized Language Critic can attribute team outcomes to individual agents.

### 9. GTR: Guided Thought RL (Tsinghua/PKU/Tencent)
- **Date**: 2026
- **TL;DR**: Discovered "thought collapse" in VLM agent RL training. Automated corrector provides real-time thought guidance without human annotation.
- **Key Results**: LLaVA-7B + GTR surpassed GPT-4o on 24-point card game.
- **💡 For Practitioners**: VLM agents in RL training can "forget how to think." Process-level thought guidance prevents this collapse.

---

## 📈 The Recipe: How to RL-Train Your Agent

```
Phase 1: SFT Cold-Start
├── Collect high-quality agent trajectories
├── Supervised fine-tuning on these trajectories
└── Establishes basic tool-use and reasoning patterns

Phase 2: GRPO Training
├── Use verifiable rewards (RLVR), not human feedback
├── Process-level rewards > outcome-only rewards
├── Group-relative advantage normalization
└── Monitor for entropy collapse (use STARE if needed)

Phase 3: Self-Correction
├── T-STAR: Tree-structured error analysis
├── ProCeedRL: Real-time process monitoring
└── SPARK: Strategic exploration at critical points
```

---

## 💡 Consolidated Takeaways

1. **SFT first, GRPO second**: Never jump straight to RL. Cold-start with SFT on curated trajectories.
2. **Verifiable rewards > human feedback**: Design tasks with automatically checkable outcomes.
3. **Process rewards > outcome rewards**: Your agent needs feedback on HOW it reasons, not just final answers.
4. **Monitor entropy**: If training plateaus, check for entropy collapse. STARE can fix it.
5. **Strategic exploration**: Not all steps are equal. Branch exploration at critical decision points.
6. **Environment signals matter**: Tool call results, intermediate observations — all are learning signals (SOAR).

---

## 📎 Related Papers

- [DEEPPLANNER](https://aclanthology.org/2026.findings-acl.370/) — Advantage shaping for agent planning (ACL 2026)
- [HACRL](https://arxiv.org/abs/2603.02604) — Heterogeneous agent collaborative RL (share verified rollouts in training, deploy independently)

---

*Last updated: July 2026 · [Back to README](../README.md)*
