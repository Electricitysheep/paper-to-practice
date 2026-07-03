# Inference Optimization — Small Models + More Thinking = Big Wins

> **10+ papers reviewed** | Key insight: Inference-time compute is the new scaling law. DSpark: 60-85% faster generation.

---

## 📊 The Big Picture

2026 H1 established inference-time compute as a **first-class optimization dimension**. The key insight: giving a small model more time to think often beats using a larger model with fast answers. DSpark (from DeepSeek/PKU) showed 60-85% per-user speedup in production.

---

## 🔬 Key Papers

### 1. DSpark: Confidence-Scheduled Speculative Decoding
- **Authors**: DeepSeek / Peking University | **arXiv**: [2606.19348](https://arxiv.org/abs/2606.19348)
- **GitHub**: [DeepSpec](https://github.com/deepseek-ai/DeepSpec)
- **TL;DR**: Semi-autoregressive speculative decoding framework. Already deployed in DeepSeek-V4 production.
- **Key Innovation**:
  - Semi-autoregressive architecture: parallel backbone + lightweight Markov head (rank 256)
  - Confidence-scheduled verification: dynamically adjusts verification length based on system load
  - Hardware-aware prefix scheduler
- **Key Results**:
  - V4-Flash: 60-85% faster per-user generation
  - V4-Pro: 57-78% faster per-user generation
  - Throughput improvement: 51-661% (depending on concurrency)
- **💡 For Practitioners**: If you're serving LLMs in production, speculative decoding is the single biggest speedup you can add. DSpark is open-source (MIT) and works on non-DeepSeek models (Qwen3, Gemma4 tested).

### 2. TTS: Compute-Optimal Test-Time Scaling
- **Authors**: Tsinghua/HIT/BUPT | **arXiv**: [2502.06703](https://arxiv.org/abs/2502.06703)
- **TL;DR**: Small models with compute-optimal test-time scaling strategies can surpass much larger models.
- **Key Results**:
  - 0.5B model > GPT-4o on MATH-500
  - 3B model > 405B model on MATH-500 and AIME24
  - 7B model > o1 and DeepSeek-R1
- **💡 For Practitioners**: Before upgrading to a larger model, try scaling your inference compute. A 0.5B model with optimal TTS can beat GPT-4o. The cost-performance tradeoff is staggering.

### 3. SPIRAL: Sequential-Parallel-Aggregative RL
- **Authors**: Stanford | **arXiv**: [2606.23595](https://arxiv.org/abs/2606.23595)
- **TL;DR**: Trains models to use three inference primitives: sequential reasoning, parallel exploration, and aggregation.
- **Key Finding**: Joint training > GRPO alone. Recursive self-aggregation scales best at test time.
- **💡 For Practitioners**: Don't just do sequential reasoning OR parallel sampling. Train your model to use ALL three primitives for maximum test-time scaling.

### 4. PRISM: Risk-Sensitive Proactive Agent Decision
- **Authors**: Yuxuan Fu et al. | **arXiv**: [2602.01532](https://arxiv.org/abs/2602.01532)
- **TL;DR**: Formalizes "when should an agent intervene?" as cost-sensitive selective intervention. Uses slow reasoning only near decision boundaries.
- **Key Results**: -22.78% false alarms, +20.14% F1.
- **💡 For Practitioners**: Your agent shouldn't always think deeply. Use fast mode for routine decisions, slow mode only when uncertain. PRISM's calibrated probability threshold tells you when.

### 5. Meta: Quantized Models "Overthink"
- **Authors**: Sanae Lotfi et al. (Meta AI) | **arXiv**: [2606.00206](https://arxiv.org/abs/2606.00206)
- **TL;DR**: Aggressive quantization causes models to generate longer CoT — but up to 52% of failures are "thought of the right answer but didn't output it."
- **Key Innovation**: Simple training-free logit penalty on "overthinking markers" (wait, but, alternatively) reduces CoT 12-23% while maintaining accuracy.
- **💡 For Practitioners**: If you've quantized your reasoning model, it's probably overthinking. Add a logit penalty on markers like "wait" and "but" — it's instant and training-free.

### 6. DRP: Distilled Reasoning Pruning
- **Venue**: ACL 2026 Findings
- **TL;DR**: Combines inference-time pruning with tuning-based distillation. Teacher operates directly on student's reasoning paths.
- **Key Results**: GSM8K tokens 917→328 (+2.4% accuracy). AIME tokens -43% (no accuracy drop).
- **💡 For Practitioners**: Most reasoning tokens are redundant. DRP shows you can cut 64% of tokens while IMPROVING accuracy. Prune before deploying.

### 7. HyperQuant: Rate-Distortion Optimal Quantization
- **arXiv**: [2606.23406](https://arxiv.org/abs/2606.23406)
- **TL;DR**: Hadamard rotation + optimal lattice quantization + entropy coding. Unified PTQ for weights and KV cache.
- **Key Results**: 4bps: 3.9x weight compression, 3.79x KV cache compression, near-lossless.
- **💡 For Practitioners**: The best production quantization pipeline we've seen. Works on LLMs AND diffusion models (19B DiT tested).

---

## 📈 Inference Optimization Stack

```
┌─────────────────────────────────────┐
│ Layer 1: Speculative Decoding       │ ← DSpark (60-85% faster)
│   Semi-AR draft + confidence sched  │
├─────────────────────────────────────┤
│ Layer 2: Test-Time Compute Scaling  │ ← TTS, SPIRAL
│   Optimal compute allocation        │
├─────────────────────────────────────┤
│ Layer 3: Token Efficiency           │ ← DRP (-64% tokens)
│   Reasoning pruning + distillation  │
├─────────────────────────────────────┤
│ Layer 4: Model Quantization         │ ← HyperQuant (3.9x)
│   Rate-distortion optimal PTQ       │
├─────────────────────────────────────┤
│ Layer 5: Overthinking Prevention    │ ← Meta logit penalty
│   Suppress redundant thinking       │
└─────────────────────────────────────┘
```

---

## 💡 Consolidated Takeaways

1. **Speculative decoding is production-ready**: DSpark delivers 60-85% speedup with open-source code.
2. **Small models can beat big ones**: 0.5B with optimal TTS > GPT-4o. Try inference scaling before model scaling.
3. **Prune reasoning tokens**: DRP shows most CoT tokens are redundant. Cut 64% and accuracy IMPROVES.
4. **Quantized models overthink**: Simple logit penalty fixes it instantly.
5. **Dynamic reasoning budgets**: Not all queries need deep thinking (PRISM). Save compute for ambiguous cases.

---

## 📎 Related Papers

- [LiftQuant](https://arxiv.org/abs/2606.04050) — Continuous (fractional) bit-width quantization
- [PiSO](https://arxiv.org/abs/2606.10890) — Optimal post-training quantization scales
- [RUQuant](https://arxiv.org/abs/2604.04013) — Orthogonal transformation for activation quantization

---

*Last updated: July 2026 · [Back to README](../README.md)*
