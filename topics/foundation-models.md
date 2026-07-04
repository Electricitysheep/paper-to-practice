# Foundation Models — Architecture Innovation Over Raw Scale

> **10+ papers reviewed** | Key insight: Good architecture > big parameters. Spatial-TTT 2B > GPT-5.

---

## 📊 The Big Picture

2026 H1 saw a decisive shift: **architecture innovation matters more than parameter count.** DeepSeek's mHC+Engram+DSA trilogy. Spatial-TTT's 2B model beating GPT-5. Tsinghua proving full-attention layers are what matter for long context. The era of "just scale it up" is over.

---

## 🔬 Key Papers

### 1. DeepSeek V4: Manifold-Constrained Hyper-Connections
- **Authors**: DeepSeek-AI (Liang Wenfeng co-author) | **Date**: January 2026
- **TL;DR**: Three architectural innovations powering the trillion-parameter V4:
  - **mHC**: Alternative to residual connections — stable at 27B, scales to 1T
  - **Engram**: Conditional memory for long-context efficiency
  - **DSA (DeepSeek Sparse Attention)**: ~50% compute reduction
- **Key Result**: Million-token context window WITHOUT proportional cost increase.
- **💡 For Practitioners**: The next generation of efficient LLMs will use mHC-like connections and sparse attention. When choosing a base model, look for these architectural signals.

### 2. DeepSeek R2: Sparse MoE at Consumer Scale
- **Date**: Q1 2026
- **TL;DR**: 28B MoE model with only ~7B activated parameters per token. Quality comparable to 90B dense models.
- **Architecture**: Fine-grained expert routing, 128K context window, MIT license.
- **💡 For Practitioners**: For single-GPU (24GB): use dense models like Gemma 4 9B (62 tok/s). For multi-GPU/A100: R2 MoE delivers much better quality-to-compute. Know your deployment hardware before choosing.

### 3. Spatial-TTT: Streaming Spatial Intelligence
- **Authors**: Liu Fangfu et al. (Tsinghua) | **Venue**: ECCV 2026
- **arXiv**: [2603.12255](https://arxiv.org/abs/2603.12255)
- **TL;DR**: 2B parameter model beats GPT-5 and Gemini-3-pro on spatial intelligence benchmarks. Handles 120 minutes of streaming video.
- **Key Innovation**: Spatial prediction mechanism enables continuous learning as the world changes.
- **💡 For Practitioners**: The 2B model that beats GPT-5. This is the poster child for "architecture > scale." For spatial reasoning tasks, small purpose-built models > giant general models.

### 4. Tsinghua/OpenBMB: Full-Attention Layers Drive Long Context
- **arXiv**: [2606.15378](https://arxiv.org/abs/2606.15378)
- **TL;DR**: In hybrid attention architectures, FULL-attention layers are what matter for long-text capability. Efficient attention layers contribute almost nothing to long-range retrieval.
- **Key Finding**: Removing RoPE from full-attention layers IMPROVES long-text performance by 14.6%.
- **💡 For Practitioners**: When choosing a base model for long-context agent tasks, prioritize models with HIGH full-attention layer ratio. Models with large sliding windows actually perform worse on long context.

### 5. Kairos: Native World Model for Physical AI
- **arXiv**: [2606.16533](https://arxiv.org/abs/2606.16533)
- **TL;DR**: Three-pillar world model: cross-embodiment curriculum pre-training, hybrid linear temporal attention, deployment-aware co-design.
- **Key Innovation**: Formal proof that temporal factorization strictly limits error accumulation.
- **💡 For Practitioners**: For robotics/autonomous driving, Kairos provides a unified infrastructure. Its linear temporal attention is the key innovation for long-horizon physical tasks.

### 6. Nemotron 3 Ultra: Mamba-Transformer Hybrid MoE
- **Institution**: NVIDIA | **Date**: April 2026
- **TL;DR**: Alternates regular attention with Mamba-2 (state space model) layers. Optimized for long-context efficiency in agent harnesses.
- **💡 For Practitioners**: Hybrid architectures (attention + Mamba) are becoming the standard for long-context production models. Expect more of this in H2 2026.

### 7. Gemma 4: Consumer-GPU Friendly
- **Institution**: Google | **Date**: Q1 2026
- **TL;DR**: 9B/27B dense models. Native vision input + 128K context. Apache 2.0 license.
- **💡 For Practitioners**: The go-to model for single-GPU deployment. 9B at 62 tok/s on RTX 4090. Don't use MoE models for batch=1 inference.

---

## 🏗️ Model Selection Decision Tree

```
Need to deploy on single GPU (≤24GB)?
├── Yes → Dense models (Gemma 4 9B, Qwen3)
│         62 tok/s at FP16. MoE overhead kills batch=1.
└── No → MoE models (DeepSeek R2 28B, V4)
         Better quality/compute at batch > 1.

Need long context (>32K)?
├── Yes → High full-attention ratio models
│         Avoid large sliding windows.
│         Prefer models with NoPE (no positional encoding on full-attn layers).
└── No → Any architecture works.

Need spatial/visual reasoning?
├── Yes → Specialized small models (Spatial-TTT 2B)
│         Purpose-built > general-purpose for spatial tasks.
└── No → General foundation models.

Need physical/embodied AI?
└── → Kairos-like world models with linear temporal attention.
```

---

## 💡 Consolidated Takeaways

1. **Architecture > Scale**: Spatial-TTT 2B > GPT-5. Stop chasing parameter counts.
2. **Full-attention layers drive long context**: Not sliding windows, not Mamba layers. Check the architecture before deploying for long-context tasks.
3. **Dense for single GPU, MoE for multi-GPU**: Know your hardware. MoE's expert routing overhead kills batch=1 performance.
4. **Hybrid architectures are the future**: Mamba-Transformer blends (Nemotron 3, Gemma 4) combine efficiency with capability.
5. **Specialized models beat general models in-domain**: Spatial-TTT for spatial tasks. Don't default to the biggest general model.

---

## 📎 Related Papers

- [GLM-5](https://arxiv.org/abs/2602.15763) — From Vibe Coding to Agentic Engineering (Zhipu AI)
- [Ling-2.6/Ring-2.6](https://arxiv.org/abs/2606.15079) — Trillion-parameter agent-native models (InclusionAI)
- **UniCM** — Unified climate mode prediction (Tsinghua, Nature MI) · *DOI link TBD*
- [UniAR](https://arxiv.org/abs/2606.18249) — Unified multimodal autoregressive modeling

---

*Last updated: July 2026 · [Back to README](../README.md)*
