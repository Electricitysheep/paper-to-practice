# 🔦 July 2026 Spotlight

> **🗓️ Living digest — last updated 2026-07-04 · 11 papers, verified against arXiv.**
> July is early in the month, so this grows as papers land; a final pass runs at month-end (~Aug 1). Every entry is checked against its arXiv source — no placeholder IDs, no fabrication.

For the first-half picture, see the [2026 H1 Master Index](2026-h1-review.md).

---

## 🏆 The month so far, in one sentence

Early July hammers one theme: **the gap between benchmark competence and open-world reliability** — agents that pass static tests but drift under real-world shift, long contexts models don't actually use, reasoning that runs too long, and task-state that gets lost.

## ⭐ Top 3 must-reads (apply this week)

1. **[TSR — Task-State Representation for GUI agents](https://arxiv.org/abs/2607.00502)** — decouple task state from screen observations; +12pp, no retraining. The cheapest agent-reliability win here.
2. **[CAT — Confidence-Adaptive Thinking](https://arxiv.org/abs/2607.00862)** — spend tokens on hard problems, not easy ones. Cuts inference cost/latency today.
3. **[ReContext — Recursive Evidence Replay](https://arxiv.org/abs/2607.02509)** — a 128K window ≠ good recall; replay the relevant evidence before generating.

---

## 🤖 Agents & Tool Use

| Paper | arXiv | Why it matters | 💡 Do this |
|---|---|---|---|
| **TSR: Task-State Representation for Long-Horizon Mobile GUI Agents** | [2607.00502](https://arxiv.org/abs/2607.00502) | Entangling task goals with fleeting screen state makes agents forget goals, hallucinate progress, and re-touch stale UI | Wrap the agent with an external task-state (goal summary + subgoal tracker + action verifier) — +12pp, no retraining |
| **Can Agents Generalize to the Open World?** (LAMDA-NeSy) | [2607.01084](https://arxiv.org/abs/2607.01084) | SFT- and RL-trained agents degrade under open-world shifts in queries, tool sets, and interaction patterns | Don't train only on static benchmarks — inject query/tool/interaction perturbations during fine-tuning |
| **RepoRescue: Whole-Repository Compatibility Rescue** | [2607.01213](https://arxiv.org/abs/2607.01213) | Repo-level code agents fail mainly on **cross-file coordination**, not single fixes | Invest in whole-repo dependency tracking and global refactoring — that's where coding agents break |

## 🎯 RL & Reasoning Training

| Paper | arXiv | Why it matters | 💡 Do this |
|---|---|---|---|
| **Active-GRPO: Adaptive Imitation + Self-Improving Reasoning** | [2607.00531](https://arxiv.org/abs/2607.00531) | Answer-only SFT collapses multi-step reasoning; RLVR alone suffers sparse feedback | Don't anchor to a static reference — let the policy decide per-instance when to imitate vs. reinforce, and keep upgrading the reference to the best rollouts |

## ⚡ Inference & Efficiency

| Paper | arXiv | Why it matters | 💡 Do this |
|---|---|---|---|
| **CAT: Confidence-Adaptive Thinking** | [2607.00862](https://arxiv.org/abs/2607.00862) | Reasoning models "overthink" easy problems, burning tokens and latency | Modulate reasoning length by the model's own confidence — compress confident answers, deliberate only on uncertain ones |
| **ReContext: Recursive Evidence Replay** | [2607.02509](https://arxiv.org/abs/2607.02509) | Even at 128K context, models fail to *use* relevant info already in the window | A bigger window ≠ better recall — replay query-relevant evidence before final generation (training-free) |

## 🔎 Retrieval & RAG

| Paper | arXiv | Why it matters | 💡 Do this |
|---|---|---|---|
| **DCCD: Dual-Confidence Contrastive Decoding for RAG** | [2607.00570](https://arxiv.org/abs/2607.00570) | The overlooked failure is **documents that contradict each other**, not just model-vs-context conflict | Gate on both document-level and token-level confidence when sources disagree — don't weight all docs equally |
| **What Survives Into Context (multi-hop RAG diagnostic)** | [2607.00725](https://arxiv.org/abs/2607.00725) | Retrieving the gold doc ≠ the answer surviving into the packed context (4.6× EM gap even when all gold is retrieved) | Measure "answer-in-context," not just retrieval recall; fancy evidence packing mainly helps weaker readers / tight budgets |

## 🛡️ Safety & Evaluation

| Paper | arXiv | Why it matters | 💡 Do this |
|---|---|---|---|
| **What LLM Agents Say When No One Is Watching** | [2607.02507](https://arxiv.org/abs/2607.02507) | Under social/incentive pressure, an agent's public vs off-the-record decisions diverge from ~3% to ~40% | Don't evaluate agents on public outputs alone — use multi-channel monitoring |

## 🧠 World Models & Foundations

| Paper | arXiv | Why it matters | 💡 Do this |
|---|---|---|---|
| **AGI Maze: Benchmark for World-Modeling Agents** | [2607.00627](https://arxiv.org/abs/2607.00627) | Vanilla LLMs can't build a persistent, manipulable internal world-state — they fail even small mazes | For partially-observable tasks, maintain explicit external world-state; prompt/memory tricks won't fix it |

## 🔬 Scientific AI

| Paper | arXiv | Why it matters | 💡 Do this |
|---|---|---|---|
| **AgentODE: LLM-Guided ODE Discovery** | [2607.00733](https://arxiv.org/abs/2607.00733) | Recovers mechanistic ODE models from **aggregate** cohort statistics, sometimes beating individual-data baselines | For sparse, privacy-sensitive science (e.g. rare disease), try mechanistic discovery from summary stats instead of raw records |

---

## 🚧 Month-end pass (to finalize ~Aug 1)

- [x] Agents, RL, inference, RAG, safety, world-models, science — seeded
- [ ] Add quantization / KV-cache efficiency papers as they land
- [ ] Add foundation-model releases and technical reports
- [ ] Add multimodal & CV
- [ ] Re-rank the **Top 3** once the full month is in

> Want to help fill this in? [Suggest a paper](../.github/ISSUE_TEMPLATE/add-paper.md) or open a PR — real arXiv links only.

---

*Living monthly digest · [Master Index →](2026-h1-review.md) · [Back to README](../README.md)*
