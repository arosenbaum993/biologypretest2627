# Biology Pre / Post Diagnostic — Grade 10 (Georgia Milestones Aligned)

An online, auto-scoring multiple-choice diagnostic for an 18-week Biology I semester
course. Give it as a **pre-test** to guide instruction and again as a **post-test** to
measure growth. Results break down by standard so instruction can be targeted.

**Take the test:** https://arosenbaum993.github.io/biologypretest2627/

## About

- **40 questions** weighted to the Georgia Milestones Biology EOC blueprint: Cells 20%,
  Cellular Genetics & Heredity 23%, Classification & Phylogeny 13%, Ecology 27%,
  Theory of Evolution 17%.
- **DOK spread** matching the blueprint (L1 18%, L2 57%, L3 25%).
- **Auto-scoring** with a built-in teacher dashboard: class overview, per-standard
  mastery heatmap, per-student breakdowns, Pre→Post growth, ready-made reteach groups,
  and CSV export/import.
- **Optional Google Sheet logging** — send every submission into one private Google
  Sheet via a Google Apps Script endpoint (setup lives in the teacher dashboard →
  Data tab).

## Hosting it for students (GitHub Pages)

1. **Settings → Pages → Source: "Deploy from a branch" → Branch: `main` / `/ (root)` → Save.**
2. Wait ~1 minute, then share the address above with students.

Because it's served as a real web page, the Google Sheet logging works from the Pages
URL. Students only ever see the test — the correct answers are not shown to them, and the
teacher dashboard is passcode-gated.

## For teachers

The teacher guide (administration, data setup, and the full answer key) and the raw item
bank are kept **out of this public repository** so the answer key isn't exposed to
students. They're delivered to the teacher separately. Change the dashboard passcode in
the file's `META` block before sharing the link.
