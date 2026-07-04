# Interpretability — Understanding What LLMs Actually Learn

> **5+ papers reviewed** | Key insight: We can now decode model activations into natural language and find the "atoms" of LLM representation.

---

## 🔬 Key Papers

### 1. Towards Atoms of Large Language Models (ICML 2026)
- **Authors**: Chenhui Hu et al. | **arXiv**: [2509.20784](https://arxiv.org/abs/2509.20784)
- **TL;DR**: First formal definition of LLM's "basic representational units" — atoms. Non-Euclidean "atomic inner product" characterizes intrinsic geometry.
- **Key Results**: Threshold SAE recovers atom sets precisely. Gemma2/Llama3.1: R²≈99.9%, stability q*≈99.85%.
- **💡 For Practitioners**: We now have a formal way to evaluate representation quality. If you're training or fine-tuning models, atomic fidelity (R²) and stability (q*) are metrics worth tracking.

### 2. LatentQA: Decoding Activations into Natural Language (ICLR 2026)
- **Authors**: LatentQA Team | **Code**: [latentqa.github.io](https://latentqa.github.io)
- **TL;DR**: Treats activation interpretation as instruction tuning. Fine-tunes a decoder LLM to translate activations into natural language descriptions.
- **Key Finding**: Can steer model into "Golden Gate Claude" purely through natural language loss. Can extract harmful knowledge from safety-aligned models.
- **💡 For Practitioners**: This is the most practical interpretability tool yet. You can literally ask "what is this model thinking?" and get a natural language answer. Use for monitoring, auditing, and safety steering.

### 3. DeepFaith: Highly Faithful Explainability (ICLR 2026)
- **Authors**: Multi-institutional | **OpenReview**: [bLgkkEGgBy](https://openreview.net/forum?id=bLgkkEGgBy)
- **TL;DR**: Derives self-supervised objective from 10 faithfulness metrics. Trains amortized explainer that produces more faithful explanations than all prior methods.
- **💡 For Practitioners**: Faithfulness ≠ accuracy. A model can be 95% accurate while its explanations are 40% faithful. Use DeepFaith-style evaluation to audit explanation quality.

### 4. Self-Consistent Explanations: Aligning What LLMs Do and Say (ACL 2026)
- **Authors**: Multi-institutional | **arXiv**: [2506.07523](https://arxiv.org/abs/2506.07523)
- **TL;DR**: Built 85K decision × 428K explanation bank. Measures feature attribution gap between answers and explanations.
- **Key Finding**: Self-consistency and accuracy are ORTHOGONAL. Inconsistent explanations can still accompany correct answers. DPO optimization improves consistency without harming accuracy.
- **💡 For Practitioners**: Your model may give correct answers with wrong explanations. This is dangerous in high-stakes domains. Add self-consistency as a quality metric.

### 5. Abstract Representational Geometry Supports Inference in LLMs (ICML 2026)
- **Authors**: Yunan Zeng, Yuwang Wang | **arXiv**: [2606.23345](https://arxiv.org/abs/2606.23345)
- **TL;DR**: LLMs form hippocampus-like abstract geometric structures when performing generalizable reasoning. Organized hierarchically across model depth.
- **Key Finding**: Higher layers form abstract context geometry. Geometric regularization increases generalizable inference emergence.
- **💡 For Practitioners**: LLMs are not just pattern matchers — they form genuine abstract representations. For tasks requiring generalization, look at higher-layer representations.

### 6. RIM: Reasoning-Induced Misalignment (ICLR 2026)
- **Authors**: Seacowx et al. | **Code**: [GitHub](https://github.com/seacowx/When-Thinking-Backfires)
- **TL;DR**: When reasoning is enhanced, safety mechanisms break because "refusal attention heads" reduce attention to CoT tokens.
- **Key Finding**: Reasoning and safety compete for the same neurons. RAS metric predicts safety degradation (r=0.891, p=0.003).
- **💡 For Practitioners**: If you enhance reasoning capability (CoT, math fine-tuning), always re-audit safety. The two are in direct competition at the neuron level.

### 7. Gradient Descent Convergence Beyond NTK Regime (June 2026)
- **Authors**: Yuqing Wang | **arXiv**: [2606.23364](https://arxiv.org/abs/2606.23364)
- **TL;DR**: Proves GD convergence for general architectures (including pre-normalized transformers) beyond the NTK regime.
- **Key Finding**: Learning rate scale depends on depth and bottleneck dimensions, NOT the largest width.
- **💡 For Practitioners**: When tuning learning rates for deep transformers, focus on depth and bottleneck dimensions, not total parameter count.

---

## 💡 Consolidated Takeaways

1. **LLM representations have structure we can measure**: Atomic fidelity (R²) and stability (q*) are now quantifiable.
2. **You can decode what a model is "thinking"**: LatentQA translates activations to natural language — practical for monitoring.
3. **Accurate ≠ well-explained**: A model can be right for the wrong reasons. Audit explanation faithfulness separately.
4. **Reasoning and safety compete**: RIM shows this at the neuron level. Always re-audit after reasoning enhancement.
5. **Higher layers = abstract reasoning**: Abstract representations for generalization live in deeper layers.

---

## 📎 Related Papers

- [LLM-VA](https://arxiv.org/abs/2601.19487) — Vector alignment for safety (ACL 2026)
- **LASA** — Language-agnostic semantic alignment (ACL 2026) · *arXiv link TBD*
- [Obj-Disco](https://arxiv.org/abs/2602.15338) — Discovering hidden alignment objectives (ICML 2026)

---

*Last updated: July 2026 · [Back to README](../README.md)*
