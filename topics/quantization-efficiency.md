# Quantization & Efficiency — Deploy Smarter, Not Heavier

> **8+ papers reviewed** | Key insight: Distillation + pruning > quantization alone. Quantized models "overthink."

---

## 🔬 Key Papers

### 1. HyperQuant: Rate-Distortion Optimal Quantization
- **arXiv**: [2606.23406](https://arxiv.org/abs/2606.23406)
- **TL;DR**: Hadamard rotation + optimal lattice quantization + entropy coding. Unified PTQ for weights AND KV cache.
- **Key Results**: 4bps: 3.9x weight compression, 3.79x KV cache compression. Near-lossless. Also works on 19B DiT video models.
- **💡 For Practitioners**: The current gold standard for production quantization. End-to-end benchmarked on H100. Use this if you're serving at scale.

### 2. Meta: Quantized Reasoning Models "Overthink"
- **Authors**: Sanae Lotfi et al. (Meta AI) | **arXiv**: [2606.00206](https://arxiv.org/abs/2606.00206)
- **TL;DR**: Aggressive PTQ reduces accuracy while increasing CoT length. Up to 52% of failures: model reaches right answer but doesn't commit.
- **Key Innovation**: Training-free logit penalty on "overthinking markers" (wait, but, alternatively) reduces CoT 12-23% while preserving accuracy.
- **💡 For Practitioners**: **If you've quantized a reasoning model, it's probably overthinking.** Add a logit penalty on markers like "wait" and "but" — instant, training-free fix. Overthinking errors reduced by up to 58%.

### 3. DRP: Distilled Reasoning Pruning (ACL 2026)
- **Authors**: Yuxuan Jiang et al. | **Venue**: ACL 2026 Findings
- **TL;DR**: Teacher operates directly on student's reasoning paths — skill-aware step decomposition and pruning.
- **Key Results**: GSM8K: tokens 917→328 (+2.4% accuracy). AIME: tokens -43% (no accuracy drop).
- **💡 For Practitioners**: **Distillation + pruning > either alone.** Cut 64% of reasoning tokens while IMPROVING accuracy. Most CoT tokens are redundant.

### 4. LiftQuant: Continuous (Fractional) Bit-Width Quantization
- **arXiv**: [2606.04050](https://arxiv.org/abs/2606.04050)
- **TL;DR**: First framework enabling arbitrary fractional bit-widths (e.g., 2.4-bit). "Lift-then-project" mechanism decouples quantization rate from coding format.
- **💡 For Practitioners**: Continuous bit-width means true Pareto-optimal deployment under strict memory constraints. No more rigid 2/3/4-bit choices.

### 5. PiSO: Optimal Post-Training Quantization Scales
- **arXiv**: [2606.10890](https://arxiv.org/abs/2606.10890)
- **TL;DR**: Computes provably optimal channel-wise weight scales using calibration data. Closed-form minimizer per interval.
- **Key Finding**: Optimal scales matter MORE at lower bit-widths. PiSO reduces calibration data needed.
- **💡 For Practitioners**: If you're doing ≤3-bit quantization, optimal scale computation (PiSO) is worth the extra step. Benefits increase as bit-width decreases.

### 6. LBLLM: Lightweight Binarization via Three-Stage Distillation (ACL 2026)
- **Authors**: Siqing Song et al. | **Venue**: ACL 2026
- **TL;DR**: W(1+1)A4 quantization. PTQ init → layer-wise distillation → learnable activation factors. Trained with only 0.016B tokens on single GPU.
- **💡 For Practitioners**: Extreme compression (binary weights) is now practical for moderate-sized models. Three-stage decoupled design prevents weight-activation quantization interference.

### 7. RUQuant: Orthogonal Transformation for Activation Quantization
- **arXiv**: [2604.04013](https://arxiv.org/abs/2604.04013)
- **TL;DR**: Two-stage orthogonal transformation method grounded in Lloyd-Max optimality. Aligns non-uniform activation distributions with uniform quantizers.
- **Key Results**: 13B model: W6A6 at 99.8% full-precision accuracy. W4A4 at 97%. ~1 minute to complete.
- **💡 For Practitioners**: Activation quantization is the harder problem. RUQuant solves it with orthogonal transformations — minutes, not hours.

### 8. Hardware-Aware Multi-Granularity Pruning for Edge LLMs
- **arXiv**: [2606.26861](https://arxiv.org/abs/2606.26861)
- **TL;DR**: Cascaded pruning (layers → attention heads → FFN channels) with low-rank recovery between stages.
- **Key Finding**: MHA+GELU architectures prune well (13.8x compression). GQA+SwiGLU architectures collapse (~74pp accuracy loss).
- **💡 For Practitioners**: **Architecture matters for pruning.** If deploying on edge devices, MHA+GELU models are far more prunable than GQA+SwiGLU.

---

## 📈 Efficiency Optimization Stack

```
Layer 1: Distillation + Pruning (DRP)
├── Cut 64% tokens, improve accuracy
└── Best ROI for reasoning models

Layer 2: Optimal Quantization (HyperQuant + PiSO)
├── 3.9x weight compression near-lossless
└── Use PiSO for ≤3-bit scenarios

Layer 3: Activation Quantization (RUQuant)
├── Fix activation distribution mismatch
└── W4A4 at 97% accuracy in 1 minute

Layer 4: Overthinking Prevention (Meta)
├── Logit penalty on thinking markers
└── Training-free, instant deployment

Layer 5: Extreme Compression (LBLLM)
├── Binary weights (W1A4) for edge
└── Only 0.016B training tokens needed
```

---

## 💡 Consolidated Takeaways

1. **Distill + prune > quantize alone**: DRP proves you can cut tokens AND improve accuracy.
2. **Quantized models overthink**: Meta's finding is critical — simple logit penalty fixes it.
3. **Architecture-aware compression**: MHA+GELU prunes well, GQA+SwiGLU doesn't.
4. **Optimal scales matter at low bits**: PiSO's closed-form solution is worth the extra step below 3-bit.
5. **Activation quantization is the frontier**: RUQuant solves it elegantly in minutes.

---

*Last updated: July 2026 · [Back to README](../README.md)*
