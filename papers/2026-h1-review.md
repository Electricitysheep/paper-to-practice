# 📇 2026 H1 Master Index — Every Paper, One Line, One Takeaway

> **The single scannable table of everything in this repo.** 100+ papers from January–June 2026, each with a one-line **💡 practitioner takeaway** and a link to its full deep-dive.
>
> Reading order: skim this table → click the topic for the full paper card → read the matching [practical guide](../README.md#-practical-guides) to apply it.

**Legend:** ⭐ = must-read this half · 🏆 = accepted at a top venue (ICLR/ICML/ACL/CVPR/Nature MI) · 🧪 = experimental / early

---

## 1. Agent Systems ([full deep-dives →](../topics/agent-systems.md))

| Paper | Venue | arXiv | 💡 One-line takeaway |
|---|---|---|---|
| ⭐🏆 MAP: Measuring Agents in Production | ICML 2026 Oral | [2512.04123](https://arxiv.org/abs/2512.04123) | 68% of prod agents run ≤10 steps — design human checkpoints, don't over-engineer |
| ⭐ DeLM: Decentralized Multi-Agent | 2026 | [2606.10662](https://arxiv.org/abs/2606.10662) | Past 5 sub-tasks the central controller is the bottleneck — switch to shared verified context |
| COMPASS: Three-Layer Architecture | ACL 2026 | — | Split agents into execution / oversight / context-manager roles for long tasks |
| Hyperagents: Self-Referential Agents | 2026 | [2603.19461](https://arxiv.org/abs/2603.19461) | Make the self-improvement procedure itself editable, not just the task behavior |
| IMAD: Internalized Multi-Agent Debate | ACL 2026 | [2604.24881](https://arxiv.org/abs/2604.24881) | One post-trained model can simulate expert debate at 93% lower token cost |
| SciOrch: Orchestrating Expert LLMs | 2026 | [2606.15872](https://arxiv.org/abs/2606.15872) | Small orchestrator + delegated big models beats any single model on cost/quality |
| HACRL: Heterogeneous Collaborative RL | 2026 | [2603.02604](https://arxiv.org/abs/2603.02604) | Let differently-sized models learn from each other's rollouts, deploy independently |

**Further reading:** [KLong](https://arxiv.org/abs/2602.17547) · [LOGIGEN](https://arxiv.org/abs/2603.00540) · [ProAct](https://arxiv.org/abs/2602.05327) · [Lacuna](https://arxiv.org/abs/2605.28617) · [HarnessBridge](https://arxiv.org/abs/2606.12882) · [Graph-of-Agents](https://arxiv.org/abs/2604.17148)

---

## 2. Reinforcement Learning ([full deep-dives →](../topics/reinforcement-learning.md))

| Paper | Venue | arXiv | 💡 One-line takeaway |
|---|---|---|---|
| ⭐ DeepSeek-R1 (v2) | 2026 | [2501.12948](https://arxiv.org/abs/2501.12948) | GRPO + verifiable rewards is the baseline recipe — SFT cold-start first |
| Kimi k1.5 | 2026 | [2501.12599](https://arxiv.org/abs/2501.12599) | RL scaling works for multimodal too; long-context RL is the frontier |
| STARE: Solving Entropy Collapse | 2026 | [2606.19236](https://arxiv.org/abs/2606.19236) | Watch entropy during RL — collapse kills exploration; regularize for it |
| T-STAR: Tree-Structured Self-Correction | 2026 | — | Structure self-correction as a tree, not a linear retry loop |
| ProCeedRL: Process Critic + Demos | 2026 | — | Process-level rewards beat outcome-only; seed with exploratory demos |
| SPARK: Dynamic Branching Exploration | 2026 | — | Branch exploration strategically instead of uniform sampling |
| SOAR: Learning from Observations | 2026 | — | Environment observations are free reward signal — use them |
| LangMARL: Natural-Language Multi-Agent RL | 2026 | [2604.00722](https://arxiv.org/abs/2604.00722) | Agents can coordinate in natural language as the action space |
| GTR: Guided Thought RL | 2026 | — | Guide the reasoning trace, not just the final answer |

**Further reading:** [SPIRAL](https://arxiv.org/abs/2606.23595) (sequential-parallel-aggregative RL)

---

## 3. Inference Optimization ([full deep-dives →](../topics/inference-optimization.md))

| Paper | Venue | arXiv | 💡 One-line takeaway |
|---|---|---|---|
| ⭐ DSpark: Confidence-Scheduled Spec. Decoding | 2026 | [2606.19348](https://arxiv.org/abs/2606.19348) | 60–85% faster generation — schedule draft length by confidence |
| ⭐ TTS: Compute-Optimal Test-Time Scaling | 2026 | [2502.06703](https://arxiv.org/abs/2502.06703) | A 0.5B model + more thinking beat GPT-4o on MATH — buy inference before buying a bigger model |
| SPIRAL: Sequential-Parallel-Aggregative RL | 2026 | [2606.23595](https://arxiv.org/abs/2606.23595) | Aggregate parallel reasoning branches instead of picking one |
| PRISM: Risk-Sensitive Proactive Decisions | 2026 | [2602.01532](https://arxiv.org/abs/2602.01532) | Make agents risk-aware before acting, not just reward-maximizing |
| Meta: Quantized Models "Overthink" | 2026 | [2606.00206](https://arxiv.org/abs/2606.00206) | Quantization inflates reasoning-token count — measure latency, not just size |
| DRP: Distilled Reasoning Pruning | ACL 2026 | — | Prune redundant reasoning steps via distillation to cut cost |
| HyperQuant: Rate-Distortion Optimal Quant | 2026 | [2606.23406](https://arxiv.org/abs/2606.23406) | 3.9× compression by treating quantization as rate-distortion |

**Further reading:** [LiftQuant](https://arxiv.org/abs/2606.04050) · [PiSO](https://arxiv.org/abs/2606.10890) · [RUQuant](https://arxiv.org/abs/2604.04013)

---

## 4. AI Safety & Alignment ([full deep-dives →](../topics/ai-safety-alignment.md))

| Paper | Venue | arXiv | 💡 One-line takeaway |
|---|---|---|---|
| RIM: Reasoning-Induced Misalignment | ICLR 2026 | — | More reasoning can *increase* misalignment — audit chains, not just answers |
| ⭐🏆 LLM-VA: Vector Alignment | ACL 2026 | [2601.19487](https://arxiv.org/abs/2601.19487) | Cheapest safety upgrade — vector alignment in minutes, no fine-tuning |
| LASA: Language-Agnostic Semantic Alignment | ACL 2026 | [2604.12710](https://arxiv.org/abs/2604.12710) | Align safety across languages, not just English |
| SInternal: Internalizing Safety via Verification | 2026 | — | Train the model to verify itself instead of bolting on a filter |
| Reflector: Step-wise Self-Reflection | 2026 | — | Reflect per-step to resist indirect / injected jailbreaks |
| Lacuna: Safe Agents as Program Holes | 2026 | [2605.28617](https://arxiv.org/abs/2605.28617) | Type-safe agents — treat unfilled actions as typed holes |
| 🏆 Obj-Disco: Hidden Alignment Objectives | ICML 2026 | [2602.15338](https://arxiv.org/abs/2602.15338) | You can discover what a model was *actually* optimized for |

---

## 5. Foundation Models ([full deep-dives →](../topics/foundation-models.md))

| Paper | Venue | arXiv | 💡 One-line takeaway |
|---|---|---|---|
| ⭐ DeepSeek V4: Manifold-Constrained Hyper-Connections | 2026 | — | Architecture innovation still matters at frontier scale |
| DeepSeek R2: Sparse MoE at Consumer Scale | 2026 | — | Frontier reasoning is coming to consumer GPUs via sparse MoE |
| Spatial-TTT: Streaming Spatial Intelligence | 2026 | [2603.12255](https://arxiv.org/abs/2603.12255) | A 2B test-time-trained model beat GPT-5 on spatial tasks |
| Tsinghua/OpenBMB: Full-Attention Drives Long Context | 2026 | [2606.15378](https://arxiv.org/abs/2606.15378) | Keep some full-attention layers — they carry long-context capability |
| Kairos: Native World Model for Physical AI | 2026 | [2606.16533](https://arxiv.org/abs/2606.16533) | World models are becoming native, not bolted-on |
| Nemotron 3 Ultra: Mamba-Transformer Hybrid MoE | 2026 | — | Hybrid SSM+attention is the practical long-context architecture |
| Gemma 4: Consumer-GPU Friendly | 2026 | — | Strong open models now target a single consumer GPU |

**Further reading:** [GLM-5](https://arxiv.org/abs/2602.15763) · [Ling/Ring-2.6](https://arxiv.org/abs/2606.15079) · [UniAR](https://arxiv.org/abs/2606.18249)

---

## 6. Long-Horizon & Memory ([full deep-dives →](../topics/long-horizon-memory.md))

| Paper | Venue | arXiv | 💡 One-line takeaway |
|---|---|---|---|
| ⭐ KLong: Training for Extremely Long-Horizon Tasks | 2026 | [2602.17547](https://arxiv.org/abs/2602.17547) | A 106B model beat 1T on PaperBench — training method > raw size for long horizons |
| ⭐ MEMPROBE: Probing Agent Memory Quality | 2026 | [2606.24595](https://arxiv.org/abs/2606.24595) | More memory ≠ better task success — probe what's actually recalled |
| SJTU/Tsinghua: Agent-Native Memory | 2026 | [2606.24775](https://arxiv.org/abs/2606.24775) | Design memory as a first-class agent component, not a RAG afterthought |
| Agent-BRACE: Belief State Decoupling | 2026 | [2605.11436](https://arxiv.org/abs/2605.11436) | Separate belief state from context window to survive long tasks |
| ProAct: Agentic Lookahead | 2026 | [2602.05327](https://arxiv.org/abs/2602.05327) | Look ahead in interactive envs instead of purely reacting |

---

## 7. Multimodal & CV ([full deep-dives →](../topics/multimodal-cv.md))

| Paper | Venue | arXiv | 💡 One-line takeaway |
|---|---|---|---|
| 🏆 UltraFlux: Native 4K Text-to-Image | CVPR 2026 | — | Native-resolution generation beats upscaling for 4K |
| 🏆 PixelDiT: Pixel-Space Diffusion | CVPR 2026 | — | Skipping the VAE latent can improve fidelity |
| 🏆 SpeeDiff: 140× Faster Training | CVPR 2026 | — | Diffusion training cost is dropping ~2 orders of magnitude |
| SeFi-Image: Semantic-First Diffusion | 2026 | [2606.22568](https://arxiv.org/abs/2606.22568) | Condition on semantics first, pixels second |
| 🏆 GCL: Group Cognition Learning | ICML 2026 | — | Multi-image reasoning benefits from group-level cognition |

---

## 8. Quantization & Efficiency ([full deep-dives →](../topics/quantization-efficiency.md))

| Paper | Venue | arXiv | 💡 One-line takeaway |
|---|---|---|---|
| ⭐ HyperQuant: Rate-Distortion Optimal | 2026 | [2606.23406](https://arxiv.org/abs/2606.23406) | 3.9× compression with a principled rate-distortion objective |
| Meta: Quantized Reasoning "Overthink" | 2026 | [2606.00206](https://arxiv.org/abs/2606.00206) | Measure end-to-end latency after quantizing — token count can rise |
| DRP: Distilled Reasoning Pruning | ACL 2026 | — | Distill away redundant reasoning steps |
| LiftQuant: Fractional Bit-Width | 2026 | [2606.04050](https://arxiv.org/abs/2606.04050) | Continuous bit-widths beat fixed 4/8-bit choices |
| PiSO: Optimal PTQ Scales | 2026 | [2606.10890](https://arxiv.org/abs/2606.10890) | Solve for optimal quantization scales instead of heuristics |
| LBLLM: Lightweight Binarization | ACL 2026 | — | 1-bit is viable with three-stage distillation |
| RUQuant: Orthogonal Activation Quant | 2026 | [2604.04013](https://arxiv.org/abs/2604.04013) | Rotate activations orthogonally before quantizing |
| Hardware-Aware Multi-Granularity Pruning | 2026 | [2606.26861](https://arxiv.org/abs/2606.26861) | Prune at the granularity your target hardware rewards |

---

## 9. Scientific AI ([full deep-dives →](../topics/scientific-ai.md))

| Paper | Venue | arXiv | 💡 One-line takeaway |
|---|---|---|---|
| ⭐ Aletheia: Autonomous Mathematics (DeepMind) | 2026 | [2602.10177](https://arxiv.org/abs/2602.10177) | Agents are starting to do genuinely autonomous math research |
| STAR-PolyaMath: Multi-Agent Proof System | 2026 | [2605.19338](https://arxiv.org/abs/2605.19338) | Multi-agent decomposition set SOTA across 8 math benchmarks |
| SciOrch: Orchestrating Experts for Science | 2026 | [2606.15872](https://arxiv.org/abs/2606.15872) | $10 of orchestrated API calls beat the strongest single model |
| Formal Logic Verification-Guided Reasoning | 2026 | [2601.22642](https://arxiv.org/abs/2601.22642) | Verify reasoning against formal logic to cut hallucination |
| Reasoning Models Generate Societies of Thought | 2026 | [2601.10825](https://arxiv.org/abs/2601.10825) | Long reasoning self-organizes into multi-persona "societies" |
| 🏆 UniCM: Unified Climate Mode Prediction | Nature MI | — | Foundation-model approach transfers to climate science |

---

## 10. Interpretability ([full deep-dives →](../topics/interpretability.md))

| Paper | Venue | arXiv | 💡 One-line takeaway |
|---|---|---|---|
| 🏆 Towards Atoms of LLMs | ICML 2026 | [2509.20784](https://arxiv.org/abs/2509.20784) | A formal unit of LLM representation you can reason about |
| 🏆 LatentQA: Decode Activations → Language | ICLR 2026 | — | Ask questions of activations and get natural-language answers |
| 🏆 DeepFaith: Highly Faithful Explainability | ICLR 2026 | — | Explanations that provably match model computation |
| 🏆 Self-Consistent Explanations | ACL 2026 | [2506.07523](https://arxiv.org/abs/2506.07523) | Align what a model *does* with what it *says* it does |
| 🏆 Abstract Representational Geometry | ICML 2026 | [2606.23345](https://arxiv.org/abs/2606.23345) | Abstract geometry in activations supports inference |
| 🏆 RIM: Reasoning-Induced Misalignment | ICLR 2026 | — | Reasoning can silently drift from aligned behavior |
| Gradient Descent Beyond NTK | 2026 | [2606.23364](https://arxiv.org/abs/2606.23364) | New convergence theory outside the NTK regime |

---

## 📈 How to use this index

1. **Triage:** scan the 💡 column for the 5–10 lines relevant to what you're building.
2. **Go deep:** click the topic link for the full paper card (TL;DR, results, "For Practitioners").
3. **Apply:** jump to the matching [practical guide](../README.md#-practical-guides) to turn insight into a checklist.

> Spotted a wrong link or a missing paper? [Open a PR](../CONTRIBUTING.md) — every fix is welcome.

---

*Covers 100+ papers, January–June 2026 · [Back to README](../README.md) · [June spotlight →](2026-06-spotlight.md)*
