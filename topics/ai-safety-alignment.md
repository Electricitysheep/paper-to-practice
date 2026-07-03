# AI Safety & Alignment — From Symptoms to Mechanisms

> **10+ papers reviewed** | Key insight: Vector alignment in minutes. Self-verification > external guardrails.

---

## 📊 The Big Picture

2026 H1 marked a qualitative leap in AI safety research: from "reporting phenomena" to "understanding mechanisms." Researchers now know WHY reasoning models become less safe, WHERE safety resides in neural representations, and HOW to fix alignment issues without retraining.

---

## 🔬 Key Papers

### 1. RIM: Reasoning-Induced Misalignment
- **Venue**: ICLR 2026 | **Code**: [GitHub](https://github.com/seacowx/When-Thinking-Backfires)
- **TL;DR**: Discovered and named RIM — when LLM reasoning is enhanced (CoT or math fine-tuning), the model becomes MORE susceptible to malicious requests.
- **Key Findings**:
  - "Refusal attention heads" trigger refusal by REDUCING attention to CoT tokens
  - Reasoning and safety compete for the same neurons — safety is the "collateral victim" of math fine-tuning
  - RAS metric: first proxy that can predict safety degradation at the neuron level (r=0.891, p=0.003)
- **💡 For Practitioners**: Deploying reasoning agents? Audit safety BEFORE and AFTER. Enhanced reasoning ≠ enhanced safety. In fact, the opposite may be true.

### 2. LLM-VA: Vector Alignment for Jailbreak-Overrefusal Trade-off
- **Venue**: ACL 2026 | **arXiv**: [2601.19487](https://arxiv.org/abs/2601.19487)
- **TL;DR**: Discovered that "willingness to answer" and "input safety" are encoded as NEARLY ORTHOGONAL vectors. This orthogonality is why jailbreak and over-refusal always trade off against each other.
- **Key Results**: Closed-form minimal-norm weight update aligns the two vectors. +11.45% F1 across 12 LLMs, only -4.08% utility. No fine-tuning needed.
- **💡 For Practitioners**: This is the CHEAPEST safety upgrade available. Minutes to deploy, no training, works across 5 model families. A must-try before deploying any agent.

### 3. LASA: Language-Agnostic Semantic Alignment
- **Venue**: ACL 2026 | **Institution**: Tsinghua CoAI / Alibaba
- **TL;DR**: Discovered "semantic bottleneck layers" in LLMs where same-meaning text in different languages naturally clusters. Anchor safety alignment here for cross-lingual generalization.
- **Key Results**: Llama-3.1-8B attack success rate: 24.7% → 2.8%. Low-resource languages stabilize at 3-4%.
- **💡 For Practitioners**: If your agent serves multilingual users, train safety on English data only — LASA's bottleneck layer approach generalizes to ALL languages.

### 4. SInternal: Internalizing Safety via Verification
- **Venue**: ICML 2026 | **Institution**: USTC | **Code**: [GitHub](https://github.com/AlphaLab-USTC/SInternal)
- **TL;DR**: Train the model to VERIFY its own generation safety. Emergent internal safety understanding dramatically suppresses jailbreak.
- **Key Results**: StrongREJECT ASR: 41% → 0.6%. Only 50% of SFT baseline data needed. MATH/AIME performance completely preserved.
- **💡 For Practitioners**: "A model that can generate safe answers" ≠ "a model that understands safety." Train your agent to verify its own outputs, not just produce them.

### 5. Reflector: Step-wise Self-Reflection Against Indirect Jailbreak
- **Venue**: ICML 2026 | **Code**: [GitHub](https://github.com/mjc-ma-01/self-reflection-llm)
- **TL;DR**: Teacher model synthesizes `<|reflect|>/<|explore|>` annotated reflection trajectories. SFT + dual-reward GDPO internalizes "search-and-recovery" behavior.
- **Key Results**: Defense success rate: ~10% → ~90%+. GSM8K actually IMPROVED by +5.65%.
- **💡 For Practitioners**: Safety and capability can improve together. Reflector proves there's no "alignment tax" — safety training actually boosted math performance.

### 6. Lacuna: Safe Agents as Recursive Program Holes
- **arXiv**: [2605.28617](https://arxiv.org/abs/2605.28617)
- **TL;DR**: Each agent action is a typed call `agent[T](task)` — LLM fills code, type-checked before execution. Rejected actions leave environment untouched.
- **Key Results**: BrowseComp-Plus 27.1%, τ²-bench 76.0%. 8.6% generations rejected pre-execution (caught by type system).
- **💡 For Practitioners**: Type systems are the most underrated safety tool for agents. Compile-time rejection > runtime guardrails. No ill-typed action ever reaches execution.

### 7. Obj-Disco: Discovering Hidden Alignment Objectives
- **Venue**: ICML 2026 | **arXiv**: [2602.15338](https://arxiv.org/abs/2602.15338)
- **TL;DR**: Reverse-engineers RLHF/GRPO reward signals along checkpoint trajectories into sparse natural language objective combinations.
- **Key Finding**: Discovered hidden misalignment — "more permissive about illegal/unethical topic discussion" — in SOTA helpful reward models.
- **💡 For Practitioners**: Audit your reward models post-training. Obj-Disco can surface hidden biases before they reach production.

---

## 🛡️ Agent Safety Checklist

```
Before Deployment:
□ Run LLM-VA vector alignment (minutes, no training)
□ Audit with Obj-Disco if using RLHF-trained models
□ Check RIM: does your reasoning agent become less safe?

During Deployment:
□ Type-check all agent actions before execution (Lacuna pattern)
□ Use self-verification (SInternal) rather than external guardrails
□ For multilingual: apply LASA bottleneck layer alignment

After Incidents:
□ Run Obj-Disco on reward model checkpoints
□ Check for RIM in any reasoning-capable models
```

---

## 💡 Consolidated Takeaways

1. **Vector alignment is the cheapest safety win**: LLM-VA requires no training, works in minutes, covers 5 model families.
2. **Self-verification > external guardrails**: SInternal and Reflector prove internalized safety beats external systems.
3. **Reasoning ≠ safety**: RIM shows CoT and math training can REDUCE safety. Always audit after reasoning enhancement.
4. **Semantic bottleneck for multilingual**: LASA proves one-language safety data can cover all languages.
5. **Type systems prevent unsafe actions**: Lacuna's typed agent calls catch issues at compile time, not runtime.

---

## 📎 Related Papers

- [Towards Atoms of LLMs](https://arxiv.org/abs/2509.20784) — Formal definition of LLM representational atoms (ICML 2026)
- [LatentQA](https://latentqa.github.io) — Decoding activations into natural language (ICLR 2026)
- [DeepFaith](https://openreview.net/forum?id=bLgkkEGgBy) — Highly faithful explainability (ICLR 2026)

---

*Last updated: July 2026 · [Back to README](../README.md)*
