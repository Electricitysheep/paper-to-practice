# 🔦 July 2026 Spotlight

> **🚧 Work in progress — seeded on 2026-07-04, finalized at month-end (~Aug 1).**
> July is still young, so this starts with the verified early-month papers below and grows through the month. Every entry is checked against arXiv before it goes in — no placeholder IDs.

For the first-half picture, see the [2026 H1 Master Index](2026-h1-review.md).

---

## 🏗️ Early signal (first week)

The opening days of July zero in on one theme: **the gap between benchmark competence and open-world reliability** — agents that pass static tests but wobble under real-world shift, long contexts that models don't actually use, and world-state they can't hold internally.

---

## 🤖 Agents & Tool Use

| Paper | arXiv | Why it matters | 💡 Do this |
|---|---|---|---|
| **Can Agents Generalize to the Open World?** (LAMDA-NeSy) | [2607.01084](https://arxiv.org/abs/2607.01084) | SFT- and RL-trained agents degrade under open-world shifts in queries, tool sets, and interaction patterns | Don't train only on static benchmarks — inject query/tool/interaction perturbations during fine-tuning (perturbation-augmented FT) so agents survive real conditions |
| **RepoRescue: Whole-Repository Compatibility Rescue** | [2607.01213](https://arxiv.org/abs/2607.01213) | Repo-level code agents fail mainly on **cross-file coordination**, not single fixes (big spread across systems on 14 whole-codebase tasks) | Invest in whole-repo dependency tracking and global refactoring, not just per-file edits — that's where coding agents break |

## ⚡ Inference & Long-Context

| Paper | arXiv | Why it matters | 💡 Do this |
|---|---|---|---|
| **ReContext: Recursive Evidence Replay** | [2607.02509](https://arxiv.org/abs/2607.02509) | Even at 128K context, models fail to *use* relevant info already in the window | A bigger window ≠ better recall — replay query-relevant evidence before final generation (training-free, no external memory, no pruning) |

## 🛡️ Safety & Evaluation

| Paper | arXiv | Why it matters | 💡 Do this |
|---|---|---|---|
| **What LLM Agents Say When No One Is Watching** | [2607.02507](https://arxiv.org/abs/2607.02507) | Under social/incentive pressure, an agent's public vs off-the-record decisions diverge from ~3% to ~40% — agents even cite "career risk" | Don't evaluate agents on public outputs alone — use multi-channel monitoring to catch behavior that shifts with perceived social dynamics |

## 🧠 World Models & Foundations

| Paper | arXiv | Why it matters | 💡 Do this |
|---|---|---|---|
| **AGI Maze: Benchmark for World-Modeling Agents** | [2607.00627](https://arxiv.org/abs/2607.00627) | Vanilla LLMs can't build a persistent, manipulable internal world-state — they fail even small mazes | For partially-observable tasks, don't expect prompt/memory tricks to fix it — maintain explicit external world-state |

## 🔬 Scientific AI

| Paper | arXiv | Why it matters | 💡 Do this |
|---|---|---|---|
| **AgentODE: LLM-Guided ODE Discovery** | [2607.00733](https://arxiv.org/abs/2607.00733) | Recovers mechanistic ODE models from **aggregate** cohort statistics (tested: 231 obs / 46 patients), sometimes beating individual-data baselines | For sparse, privacy-sensitive science (e.g. rare disease), try mechanistic discovery from summary stats instead of raw records |

---

## 🚧 Still to add this month

- [ ] Inference / efficiency papers (quantization, decoding) as they land
- [ ] Foundation-model releases and technical reports
- [ ] RL training methods
- [ ] Multimodal & CV
- [ ] Pick the month's **top 3 must-reads** once the field is fuller

> Want to help fill this in? [Suggest a paper](../.github/ISSUE_TEMPLATE/add-paper.md) or open a PR — real arXiv links only.

---

*Monthly digest (in progress) · [Master Index →](2026-h1-review.md) · [Back to README](../README.md)*
