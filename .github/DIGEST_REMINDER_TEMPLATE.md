**Time to publish the {{MONTH}} digest.** 🗓️

Keeping a visible monthly rhythm is the single biggest driver of stars for a curated list. Aim to close this within the first week of the month.

### Checklist

- [ ] Skim arXiv (cs.AI, cs.CL, cs.LG) + top-venue accepted lists for {{MONTH}}
- [ ] Pick the ~15–25 papers that actually change what a builder should do
- [ ] Copy `papers/_TEMPLATE-monthly-digest.md` → `papers/<YYYY>-<MM>-spotlight.md`
- [ ] For each paper write a real **💡 takeaway** (an action, not a summary)
- [ ] Verify every arXiv/DOI link resolves (no placeholder IDs — the CI will catch them)
- [ ] Add any breakout paper as a full card in the right `topics/` file
- [ ] Update `papers/2026-h1-review.md` (or the running master index) with new rows
- [ ] Link the new digest from `README.md` ("Latest digest")
- [ ] Commit with a clear message so the update shows in the history

### Definition of done

A new dated `*-spotlight.md` file is merged, the master index reflects it, and the README points to it. Close this issue with a link to the digest.
