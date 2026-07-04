# Model Selection Guide

> When to use which model — a decision guide grounded in 10+ foundation-model papers from 2026 H1.

---

## 🎯 The One Question That Matters

**Before picking a bigger model, ask: "Have I exhausted inference-time compute on my current one?"**

The single most repeated finding of 2026 H1: *a small model given more thinking time often beats a large model answering fast.*

- **TTS** ([2502.06703](https://arxiv.org/abs/2502.06703)): a 0.5B model + compute-optimal test-time scaling beat GPT-4o on MATH-500; 7B beat o1 and DeepSeek-R1.
- **Spatial-TTT** ([2603.12255](https://arxiv.org/abs/2603.12255)): a 2B test-time-trained model beat GPT-5 on streaming spatial tasks.

**💡 Default move:** try more inference budget (longer reasoning, best-of-N, verification) *before* upgrading tiers.

---

## 🗺️ Decision Tree

```
Is the task reasoning-heavy (math, code, planning)?
├── YES → Start with a reasoning model + test-time scaling
│         └── Still failing? → RL-trained variant (see RL Playbook)
└── NO  → Is latency critical?
          ├── YES → Small model + speculative decoding (DSpark, 60–85% faster)
          └── NO  → Is it multimodal / spatial / physical?
                    ├── YES → World-model native (Kairos) or TTT (Spatial-TTT)
                    └── NO  → Cheapest model that passes your eval suite
```

---

## 📊 Model Class Cheat-Sheet

| If you need... | Reach for... | Evidence |
|---|---|---|
| Frontier reasoning, cost no object | DeepSeek R2 / V4-class | Sparse MoE brings frontier reasoning to consumer scale |
| Strong reasoning on one consumer GPU | Gemma 4, DeepSeek R2 (sparse MoE) | Explicitly consumer-GPU targeted |
| Long context (100k+) | Hybrid SSM+attention (Nemotron 3 Ultra) | Keep some **full-attention** layers — they carry long-context ability ([2606.15378](https://arxiv.org/abs/2606.15378)) |
| Spatial / streaming / physical | Kairos (world model), Spatial-TTT | Native world models beat bolt-on approaches |
| Agentic engineering / coding | GLM-5 ([2602.15763](https://arxiv.org/abs/2602.15763)), Ling/Ring-2.6 ([2606.15079](https://arxiv.org/abs/2606.15079)) | Agent-native training |
| Lowest cost on complex tasks | **Small orchestrator + delegated big models** | SciOrch: +3.74% over strongest single model at **$10.42** ([2606.15872](https://arxiv.org/abs/2606.15872)) |

---

## 💸 The Orchestrator Pattern (best cost/quality lever)

Instead of "one big model for everything," use a small model to **decompose → delegate → synthesize**:

```
□ Small orchestrator (7–8B) reads the task
□ Decomposes into sub-questions
□ Routes each to the cheapest model that can answer it
□ Synthesizes a final answer
```

SciOrch showed this beats the strongest single model while costing ~$10 for a full benchmark run. This is the highest-ROI architectural choice for complex, heterogeneous workloads.

---

## ✅ Selection Checklist

```
□ Wrote an eval suite (20–50 tasks) BEFORE choosing a model
□ Tried test-time scaling on the small model first
□ Measured end-to-end latency, not just parameter count
   (⚠️ quantized reasoning models "overthink" — more tokens, [2606.00206])
□ Priced per-task cost, not per-token
□ Considered orchestrator pattern for heterogeneous tasks
□ Re-ran the eval suite on every model swap
```

---

## 🚨 Common Mistakes

1. **Chasing leaderboards** instead of running your own eval suite.
2. **Upgrading tiers** before trying more inference compute.
3. **Judging by size** — a quantized 70B can be slower end-to-end than a well-scaled 7B.
4. **One model for everything** — you're overpaying on the easy 80% of requests.

---

*Based on foundation-model papers — see [Foundation Models](../topics/foundation-models.md) & [Inference Optimization](../topics/inference-optimization.md) · [Back to README](../README.md)*
