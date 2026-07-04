# RL Training Playbook

> When and how to RL-train your agent — based on DeepSeek R1/R2, STARE, and 15+ RL papers from 2026 H1.

---

## 🚦 First: Should You RL At All?

**70% of production agents never fine-tune** (MAP study). RL is the *last* lever, not the first.

```
Climb this ladder in order — stop the moment quality is good enough:
1. Prompt engineering        ← 70% of production teams stop here
2. SFT on curated trajectories
3. GRPO with verifiable rewards
4. Process-level rewards + exploration tricks
```

**💡 Never jump straight to RL without an SFT cold-start.** DeepSeek-R1 ([2501.12948](https://arxiv.org/abs/2501.12948)) established SFT-then-GRPO as the standard recipe for a reason.

---

## 🧪 The Standard Recipe (2026 consensus)

```
□ Step 1 — SFT cold-start
   • Curate a few thousand high-quality trajectories
   • Get the model into the right output format/behavior first

□ Step 2 — GRPO with verifiable rewards
   • Use rewards you can check programmatically (math answers, unit tests, format)
   • Verifiable > learned reward models for stability

□ Step 3 — Prefer PROCESS rewards over OUTCOME-only
   • Reward good intermediate steps, not just the final answer
   • ProCeedRL: process critic + exploratory demonstrations

□ Step 4 — Watch for entropy collapse
   • If exploration dies, training stalls
   • STARE ([2606.19236]) directly targets entropy collapse
```

---

## ⚠️ The #1 Failure Mode: Entropy Collapse

As RL progresses, the policy can become over-confident, entropy crashes, exploration stops, and learning plateaus.

```
□ Log token-level entropy every N steps
□ If it trends toward zero early → apply STARE-style regularization
□ Keep a temperature / KL budget for exploration
```

**STARE** ([2606.19236](https://arxiv.org/abs/2606.19236), Tsinghua/Tencent Hunyuan) is the go-to reference for diagnosing and fixing this.

---

## 🌳 Structure the Search, Don't Just Retry

Linear "try again" loops waste compute. 2026 papers structure exploration:

| Technique | Paper | Idea |
|---|---|---|
| Tree-structured self-correction | T-STAR | Branch corrections as a tree, prune bad paths |
| Strategic dynamic branching | SPARK | Branch where uncertainty is highest |
| Sequential-parallel-aggregative | SPIRAL ([2606.23595](https://arxiv.org/abs/2606.23595)) | Run branches in parallel, aggregate the best |
| Guided thought RL | GTR | Supervise the reasoning trace, not only the answer |

---

## 🤝 Multi-Model & Multi-Agent RL

```
□ Multiple model sizes? → HACRL: share verified rollouts during training,
  deploy each model independently at inference.
□ Need multi-perspective reasoning? → IMAD ([2604.24881]): post-train ONE
  model to internalize debate — 93% fewer tokens than running N agents.
□ Coordination task? → LangMARL ([2604.00722]): natural language as the
  multi-agent action space.
```

---

## ✅ Pre-Flight Checklist

```
□ Confirmed prompting + SFT genuinely aren't enough (measured, not assumed)
□ Have programmatically verifiable rewards
□ SFT cold-start done before any RL
□ Entropy logging in place
□ Process-level rewards where possible
□ Regression eval suite runs on every checkpoint
□ Budget cap on rollout sampling cost
```

---

## 🚨 Common Mistakes

1. **RL before SFT** — unstable, wastes compute.
2. **Outcome-only rewards** — the model games the final answer.
3. **Ignoring entropy** — silent collapse, plateau with no obvious cause.
4. **Linear retries** — structure the search instead.
5. **RL when a prompt would do** — 70% of teams never needed it.

---

*Based on RL papers — see [Reinforcement Learning](../topics/reinforcement-learning.md) · [Back to README](../README.md)*
