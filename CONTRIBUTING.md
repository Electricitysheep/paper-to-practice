# Contributing to Paper-to-Practice

Thanks for your interest in contributing! This repository thrives on community contributions.

## Ways to Contribute

### 1. Add a Paper Summary
The most valuable contribution! Follow the paper card format:

```markdown
### N. Paper Title
- **Authors**: ... | **Institution**: ... | **arXiv**: [ID](https://arxiv.org/abs/ID)
- **Venue**: ICLR/ICML/ACL/CVPR 2026
- **TL;DR**: [One-sentence summary in plain language]
- **Key Innovation**: [What's new vs. existing approaches]
- **Key Results**: [Numbers that matter]
- **💡 For Practitioners**: [1-3 concrete, actionable takeaways]
```

**Process:**
1. Fork the repo
2. Add your paper to the appropriate `topics/` file (or create a new topic file)
3. If adding a new topic, link it in README.md
4. Submit a PR

### 2. Suggest a Practical Takeaway
Open an issue with the `[Takeaway]` prefix. Format:
```
[Takeaway] Paper: [Title] (arXiv: [ID])
What I learned: [Your insight]
Why it matters: [Practical application]
```

### 3. Fix Errors
Paper links break, typos happen. PRs fixing these are always welcome!

### 4. Translate
Help us reach developers in other languages:
- Open an issue: `[Translation] Language: [name]`
- We'll create a `README_XX.md` file
- Translate any subset of content

## 📅 The Monthly Digest (maintainer rhythm)

This repo commits to a **visible monthly cadence** — the biggest single driver of stars for a curated list. Each month:

1. A GitHub Action opens a **"Publish the &lt;month&gt; digest"** reminder issue on the 1st.
2. Copy [`papers/_TEMPLATE-monthly-digest.md`](papers/_TEMPLATE-monthly-digest.md) → `papers/<YYYY>-<MM>-spotlight.md`.
3. Fill it with the ~15–25 papers that actually change what a builder should do, each with a real **💡 takeaway**.
4. Add breakout papers as full cards in `topics/`, update the master index, and link the digest from the README.

Publishing the digest = a real dated commit, so the "Updated Monthly" badge is backed by evidence.

## ✅ Automated checks

Every push and PR runs a **link check** (`.github/workflows/link-check.yml`):
- **Internal links & anchors** are verified on every change and **must resolve** — a broken relative link fails CI.
- **External links** (arXiv, DOIs) are fully checked monthly; broken ones open a tracking issue.

Placeholder arXiv IDs (`2606.xxxxx`) are **not allowed** — either find the real ID or omit the link. Fabricated papers/links are the fastest way to lose a research audience's trust.

## Quality Guidelines

- **Accuracy**: Verify arXiv IDs, author names, and institution affiliations
- **Practicality**: Every paper MUST have the "💡 For Practitioners" section
- **Conciseness**: Paper summaries should be scannable in 30 seconds
- **Neutrality**: Present findings objectively. No hype, no marketing language.

## Review Process

1. Maintainers review within 3-5 days
2. Feedback provided if changes needed
3. Merged after approval

## Code of Conduct

Be respectful. Be constructive. Focus on the science and its practical applications.

---

*Questions? Open an issue or start a discussion!*
