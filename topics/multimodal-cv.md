# Multimodal & Computer Vision — CVPR 2026 Highlights

> **8+ papers reviewed** | Key insight: Native 4K generation, pixel-space diffusion, unified multimodal models.

---

## 🔬 Key Papers

### 1. UltraFlux: Native 4K Text-to-Image (CVPR 2026)
- **Authors**: Tian Ye, Song Fei, Lei Zhu
- **TL;DR**: Flux-based DiT trained natively at 4K. Data-model co-design. Multi-aspect-ratio support.
- **Key Innovation**: Resonance 2D RoPE + YaRN, SNR-Aware Huber Wavelet, Stage-wise Aesthetic Curriculum.
- **💡 For Practitioners**: Native high-res generation > upscaling. UltraFlux matches Seedream 4.0 quality.

### 2. PixelDiT: Pixel-Space Diffusion (CVPR 2026)
- **Authors**: Yongsheng Yu, Jiebo Luo et al.
- **TL;DR**: Eliminates autoencoder bottleneck. Dual-level design: patch DiT (global) + pixel DiT (texture). FID 1.61@256.
- **💡 For Practitioners**: Pixel-space generation is closing the gap with latent methods. No VAE = no reconstruction artifacts.

### 3. SpeeDiff: 140x Faster Training (CVPR 2026)
- **Authors**: Bingliang Zhang, Yang Song et al.
- **TL;DR**: Joint VAE + diffusion training. Tweedie Pixel Reconstruction loss prevents latent collapse. FID 1.50.
- **💡 For Practitioners**: End-to-end training of VAE + diffusion is now practical. 140x training speedup over vanilla SiT.

### 4. SeFi-Image: Semantic-First Diffusion
- **arXiv**: [2606.22568](https://arxiv.org/abs/2606.22568)
- **TL;DR**: Semantic-First Diffusion paradigm. 125K A800 GPU hours (10-20% of Z-Image). 5B model matches Qwen-Image and Z-Image.
- **💡 For Practitioners**: Semantic guidance can dramatically reduce training compute for T2I models. The 1B variant already shows strong instruction following.

### 5. GCL: Group Cognition Learning (ICML 2026)
- **Institution**: Fudan/PKU/USC
- **TL;DR**: Governed two-stage multimodal collaboration. Routing Agent + Auditing Agent prevent modality dominance.
- **💡 For Practitioners**: In multimodal agents, some modalities can "bully" others. Use governance protocols to ensure balanced fusion.

---

*Last updated: July 2026 · [Back to README](../README.md)*
