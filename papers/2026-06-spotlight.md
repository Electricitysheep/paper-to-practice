# 🔦 June 2026 Spotlight

> A monthly digest of the papers that mattered most in **June 2026** — the busiest month of the half. Each entry: what it is, and the one thing to do about it.

For the full half-year picture, see the [2026 H1 Master Index](2026-h1-review.md).

---

## 🏆 The month in one sentence

June crystallized three shifts: **inference-time compute became the main scaling axis**, **decentralized multi-agent beat centralized control**, and **quantization got a principled (rate-distortion) footing**.

---

## ⚡ Inference & Efficiency

| Paper | arXiv | Why it mattered | 💡 Do this |
|---|---|---|---|
| **DSpark** — confidence-scheduled speculative decoding | [2606.19348](https://arxiv.org/abs/2606.19348) | 60–85% faster, already in DeepSeek-V4 prod | Add speculative decoding first; tune verify length to load ([deep-dive](dspark-deep-dive.md)) |
| **SPIRAL** — sequential-parallel-aggregative RL | [2606.23595](https://arxiv.org/abs/2606.23595) | Train models to use all 3 inference primitives | Don't pick sequential *or* parallel — train for both + aggregation |
| **HyperQuant** — rate-distortion optimal quant | [2606.23406](https://arxiv.org/abs/2606.23406) | 3.9× compression, principled objective | Treat quantization as rate-distortion, not heuristics |
| **Meta** — quantized models "overthink" | [2606.00206](https://arxiv.org/abs/2606.00206) | Quantization inflates reasoning tokens | Re-measure end-to-end latency after quantizing |
| **LiftQuant** / **PiSO** — fractional bit-width & optimal scales | [2606.04050](https://arxiv.org/abs/2606.04050) · [2606.10890](https://arxiv.org/abs/2606.10890) | Beyond fixed 4/8-bit | Consider continuous bit-widths and solved-for scales |

---

## 🤖 Agents & RL

| Paper | arXiv | Why it mattered | 💡 Do this |
|---|---|---|---|
| **DeLM** — decentralized multi-agent | [2606.10662](https://arxiv.org/abs/2606.10662) | +10.5pp SWE-bench, ~50% cheaper | Past 5 sub-tasks, drop the central controller for shared verified context |
| **SciOrch** — orchestrating expert LLMs | [2606.15872](https://arxiv.org/abs/2606.15872) | Beat strongest single model for ~$10 | Small orchestrator + delegated big models = best cost/quality |
| **STARE** — solving entropy collapse | [2606.19236](https://arxiv.org/abs/2606.19236) | Fixes the #1 RL training failure | Log entropy during RL; regularize before it collapses |
| **HarnessBridge** — learnable harness controller | [2606.12882](https://arxiv.org/abs/2606.12882) | The harness itself becomes learnable | Treat the harness as a component you can optimize |

---

## 🧠 Foundation & Memory

| Paper | arXiv | Why it mattered | 💡 Do this |
|---|---|---|---|
| **Full-attention drives long context** (Tsinghua/OpenBMB) | [2606.15378](https://arxiv.org/abs/2606.15378) | Which layers carry long-context ability | Keep some full-attention layers in hybrid designs |
| **Kairos** — native world model | [2606.16533](https://arxiv.org/abs/2606.16533) | World models going native | For physical/spatial tasks, prefer native world models |
| **MEMPROBE** — probing memory quality | [2606.24595](https://arxiv.org/abs/2606.24595) | More memory ≠ better results | Measure recall at decision time, not storage volume |
| **SJTU/Tsinghua** — agent-native memory | [2606.24775](https://arxiv.org/abs/2606.24775) | Memory as a first-class component | Match memory structure to task type |

---

## 🔬 Interpretability & Science

| Paper | arXiv | Why it mattered | 💡 Do this |
|---|---|---|---|
| **Abstract Representational Geometry** | [2606.23345](https://arxiv.org/abs/2606.23345) | Geometry in activations supports inference | Useful lens for probing model internals |
| **Gradient Descent Beyond NTK** | [2606.23364](https://arxiv.org/abs/2606.23364) | New convergence theory | Background for training-dynamics work |

---

## 📌 If you only read three things this month

1. **[DSpark](dspark-deep-dive.md)** — the biggest free speedup for anyone serving LLMs.
2. **DeLM** ([2606.10662](https://arxiv.org/abs/2606.10662)) — decentralization is the scaling answer for multi-agent.
3. **MEMPROBE** ([2606.24595](https://arxiv.org/abs/2606.24595)) — stop confusing "stored" with "usable."

---

*Monthly digest · [Master Index →](2026-h1-review.md) · [Back to README](../README.md)*
