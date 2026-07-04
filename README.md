# 🤖 Paper-to-Practice: Turning AI Research into Production Wisdom

<p align="center">
  <b>The only AI-research list that tells you what to <i>do differently</i> — not just what to read.</b><br>
  <sub>📄 100+ Top-Tier Papers → 💡 50+ Production Takeaways for AI Agent Builders</sub><br>
  <sub>ICLR · ICML · ACL · CVPR · ECCV · Nature MI — January–June 2026</sub>
</p>

<p align="center">
  <a href="#-by-the-numbers"><img src="https://img.shields.io/badge/Papers-100%2B-blue?style=flat-square" alt="Papers"></a>
  <a href="#-topics"><img src="https://img.shields.io/badge/Topics-10-brightgreen?style=flat-square" alt="Topics"></a>
  <a href="#-practical-guides"><img src="https://img.shields.io/badge/Guides-5-orange?style=flat-square" alt="Guides"></a>
  <a href="papers/2026-06-spotlight.md"><img src="https://img.shields.io/badge/Updated-Monthly-ff69b4?style=flat-square" alt="Updates"></a>
  <a href="https://github.com/Electricitysheep/paper-to-practice/actions/workflows/link-check.yml"><img src="https://github.com/Electricitysheep/paper-to-practice/actions/workflows/link-check.yml/badge.svg" alt="Link Check"></a>
  <a href="README_CN.md"><img src="https://img.shields.io/badge/中文-完整版-red" alt="Chinese"></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/License-MIT-yellow" alt="License"></a>
</p>

<p align="center">
  <sub>📅 Latest digest: <a href="papers/2026-06-spotlight.md">June 2026 Spotlight</a> · <a href="papers/2026-h1-review.md">Master Index (100+ papers)</a></sub>
</p>

---

## ⚡ Why This Repo Exists

In 2026, **AI Agents moved from lab to production**. Yet a massive gap remains:

| Academia publishes... | Practitioners need... |
|---|---|
| 1376 papers/month on arXiv (cs.AI alone) | "What should I actually do differently?" |
| Mathematical proofs and ablation studies | Architecture decisions and deployment checklists |
| Benchmarks on curated datasets | Reliability in real-world production |

**This repo bridges that gap.** Every paper we cover includes a **💡 For Practitioners** section — concrete, actionable advice you can apply today.

### 🆚 How this differs from other "awesome" lists

| Typical awesome-list | Paper-to-Practice |
|---|---|
| Paper title + 1-line summary | Paper card **+ a "what to do differently" takeaway** |
| A list to bookmark | 5 **practical guides** that turn insights into checklists |
| "Here's what to read" | "Here's what to *change* in your system" |

> 👉 **New here? Start with the [📇 Master Index](papers/2026-h1-review.md)** — every paper, one line, one takeaway.
>
> 📖 [中文版 (Chinese Version) →](README_CN.md)

---

## 📊 By The Numbers

| Metric | Value |
|---|---|
| 📄 Papers Reviewed | **100+** ([full index](papers/2026-h1-review.md)) |
| 🔬 Deep-Dive Cards | **68** with full analysis + takeaways |
| 🏫 Institutions Covered | **30+** (Tsinghua, Stanford, MIT, Berkeley, CMU, Oxford, DeepMind, Meta, Google, DeepSeek...) |
| 📅 Time Span | **January–June 2026** (6 months) |
| 🎯 Topics | **10** research themes |
| 💡 Actionable Takeaways | **50+** |
| 🌐 Languages | **English + 中文** (fully bilingual) |

---

## 🗺️ Reading Map

```
                    ┌──────────────────────────────┐
                    │     START HERE                │
                    │  README.md (this page)        │
                    └──────────┬───────────────────┘
                               │
          ┌────────────────────┼────────────────────┐
          ▼                    ▼                     ▼
   ┌──────────────┐   ┌──────────────┐    ┌──────────────────┐
   │  Quick Start │   │ Topic Deep   │    │ Practical Guides │
   │  (5 min)     │   │ Dives        │    │ (Implementation) │
   └──────┬───────┘   └──────┬───────┘    └────────┬─────────┘
          │                  │                      │
   ┌──────▼──────┐   ┌──────▼──────────┐   ┌───────▼──────────┐
   │papers/      │   │topics/          │   │practical-guides/ │
   │2026-h1-     │   │agent-systems    │   │production-agent  │
   │review.md    │   │rl-training      │   │harness-eng       │
   │             │   │inference-opt    │   │model-selection   │
   │             │   │ai-safety        │   │rl-playbook       │
   │             │   │foundation-models│   │memory-design     │
   │             │   │long-horizon     │   │                  │
   └─────────────┘   └─────────────────┘   └──────────────────┘
```

---

## ⚡ 5-Minute Summary: What 2026 H1 Taught Us

### 1. Agent Systems Are Production-Ready (But Simple Wins)
> The MAP study (ICML 2026 Oral) surveyed 86 practitioners (plus 20 in-depth interviews) across 26 domains: **68% of production agents execute ≤10 steps** before human intervention. **70% use prompting, not fine-tuning.** The top challenge is **reliability, not capability.**

**💡**: Don't over-engineer. Start with simple prompt chains. Add RL only when needed. ([Read more →](topics/agent-systems.md))

### 2. RL Became the Dominant Training Paradigm
> DeepSeek-R1/R2, Kimi k1.5, and dozens of papers established **GRPO + Verifiable Rewards** as the standard recipe. **Process-level rewards > outcome-only rewards.**

**💡**: SFT first, then GRPO. Don't jump straight to RL without SFT cold-start. ([Read more →](topics/reinforcement-learning.md))

### 3. Small Models + More Thinking > Big Models + Fast Answers
> Tsinghua's TTS strategy: **0.5B model beat GPT-4o** on MATH-500. **7B beat o1 and DeepSeek-R1.** Inference-time compute is the new scaling axis.

**💡**: Before upgrading your model, try giving it more inference budget. ([Read more →](topics/inference-optimization.md))

### 4. The Harness Is 98% of the Work
> Production agents: **~2% model code, ~98% harness code** (context, tools, safety, memory, evaluation). Model choice matters less than harness design.

**💡**: Stop chasing model leaderboards. Invest in your harness layer. ([Read more →](practical-guides/harness-engineering-101.md))

### 5. Safety Research Moved From Symptoms to Mechanisms
> RIM, LLM-VA, LASA, SInternal: Safety is no longer "add a system prompt." It's about **vector alignment, semantic bottlenecks, and internalized verification.**

**💡**: Vector alignment (LLM-VA) is the cheapest safety upgrade — minutes, no fine-tuning. ([Read more →](topics/ai-safety-alignment.md))

---

## 📚 Topics

| # | Topic | Papers | Key Insight |
|---|-------|--------|-------------|
| 1 | [Agent Systems](topics/agent-systems.md) | 20+ | Multi-agent > single-agent. DeLM: decentralized beats centralized |
| 2 | [RL Training](topics/reinforcement-learning.md) | 15+ | GRPO + process rewards. T-STAR: tree-structured self-correction |
| 3 | [Inference Optimization](topics/inference-optimization.md) | 10+ | DSpark: 60-85% faster. TTS: small models beat big ones |
| 4 | [AI Safety & Alignment](topics/ai-safety-alignment.md) | 10+ | LLM-VA: vector alignment in minutes. SInternal: self-verification |
| 5 | [Foundation Models](topics/foundation-models.md) | 10+ | DeepSeek V4/R2. Spatial-TTT 2B > GPT-5 |
| 6 | [Long-Horizon & Memory](topics/long-horizon-memory.md) | 8+ | KLong: 106B beats 1T on PaperBench. MEMPROBE: memory ≠ task success |
| 7 | [Multimodal & CV](topics/multimodal-cv.md) | 8+ | CVPR 2026: UltraFlux 4K, PixelDiT, SpeeDiff 140x |
| 8 | [Quantization & Efficiency](topics/quantization-efficiency.md) | 8+ | HyperQuant 3.9x. Meta: quantized models "overthink" |
| 9 | [Scientific AI](topics/scientific-ai.md) | 6+ | Aletheia: autonomous math. STAR-PolyaMath: 8 benchmarks SOTA |
| 10 | [Interpretability](topics/interpretability.md) | 7+ | Atoms of LLMs (ICML). LatentQA: decode activations → language |

---

## 🛠️ Practical Guides

These guides synthesize insights across papers into **ready-to-use workflows**:

| Guide | Description | Based On |
|-------|-------------|----------|
| [Production Agent Playbook](practical-guides/production-agent-playbook.md) | Step-by-step checklist for deploying reliable agents | MAP study + 20+ papers |
| [Harness Engineering 101](practical-guides/harness-engineering-101.md) | How to design the 98% of your agent system | Harness surveys + Anthropic guides |
| [Model Selection Guide](practical-guides/model-selection-guide.md) | Architecture comparison: when to use which model | 10+ foundation model papers |
| [RL Training Playbook](practical-guides/rl-training-playbook.md) | When and how to RL-train your agent | DeepSeek R1/R2 + STARE + 15 papers |
| [Memory System Design](practical-guides/memory-system-design.md) | Designing agent memory that actually works | MEMPROBE + SJTU/Tsinghua study |

---

## 📖 Paper Deep-Dives

| Paper | Focus | What You'll Learn |
|-------|-------|-------------------|
| [DSpark: Speculative Decoding](papers/dspark-deep-dive.md) | Inference acceleration | 60-85% faster generation with semi-autoregressive draft |
| [2026 H1 Comprehensive Review](papers/2026-h1-review.md) | Full semester survey | All 100+ papers organized by theme with takeaways |
| [June 2026 Spotlight](papers/2026-06-spotlight.md) | Monthly digest | 40+ papers from June alone |

---

## 🤝 Contributing

We welcome contributions! Here's how:

1. **Add a paper**: Fork → Create paper-card in `topics/` → PR ([template](.github/pull_request_template.md))
2. **Suggest a takeaway**: Open an issue with `[Takeaway]` prefix
3. **Translate**: Help us reach developers in Japanese, Korean, French...
4. **Fix errors**: Paper links break, typos happen — PRs welcome!

See [CONTRIBUTING.md](CONTRIBUTING.md) for detailed guidelines.

### Contributors

<a href="https://github.com/Electricitysheep/paper-to-practice/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=Electricitysheep/paper-to-practice" />
</a>

---

## ⭐ Star History

If you find this useful, **star the repo** to stay updated! We publish monthly digests and new practical guides.

---

## 📜 License

MIT © 2026 — Free to use, share, and adapt. Papers cited retain their original licenses.

---

## 🙏 Acknowledgements

This repo builds on the work of thousands of researchers across 30+ institutions. Special thanks to:

- **Sebastian Raschka** — whose curated paper lists inspired this format
- **The MAP study authors** — for the first large-scale production agent survey
- **DeepSeek, Meta, Google, Alibaba, Tsinghua** — for open-sourcing models and research
- **All paper authors** — without your work, there'd be nothing to translate

---

<p align="center">
  <sub>Built with ❤️ for the AI agent builder community</sub>
</p>
