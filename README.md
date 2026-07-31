# Biology Pre / Post Diagnostic — Grade 10 (Georgia Milestones Aligned)

An online, auto-scoring multiple-choice diagnostic for an 18-week Biology I semester
course. Give it as a **pre-test** to guide instruction and again as a **post-test** to
measure growth. Results break down by standard so instruction can be targeted.

## Files

| File | What it is |
|---|---|
| [`biology-pre-post-diagnostic.html`](biology-pre-post-diagnostic.html) | The test students take. Open it in any browser — self-contained, no internet, login, or install required. Auto-scores and reports by standard, with a built-in teacher dashboard. |
| [`TEACHER_GUIDE.md`](TEACHER_GUIDE.md) | Administration instructions, data-collection guide, blueprint alignment, and the full answer key + item map. |
| [`item-bank.json`](item-bank.json) | Raw item data (stems, options, key, standard, DOK) for reuse or import into another platform. |

## Highlights

- **40 items** weighted to the Georgia Milestones Biology EOC blueprint: Cells 20%,
  Cellular Genetics & Heredity 23%, Classification & Phylogeny 13%, Ecology 27%,
  Theory of Evolution 17%.
- **DOK spread** matching the blueprint (L1 18%, L2 57%, L3 25%).
- **Robust teacher data** — class overview, per-standard mastery heatmap, per-student
  breakdowns, Pre→Post growth, ready-made reteach groups, and CSV export/import.
- **Optional Google Sheet logging** — send every submission into one Google Sheet via a
  Google Apps Script endpoint (setup steps and code in the Teacher dashboard → Data tab
  and `TEACHER_GUIDE.md`).
- **Balanced answer key** (A/B/C/D = 10 each) with no "longest answer is correct" cue.

## Getting started

1. Open `biology-pre-post-diagnostic.html` and share it with students (LMS, Google
   Classroom, shared drive, or a local file).
2. Students enter their name and period, pick **Pre-Test** or **Post-Test**, and begin.
3. Open the **Teacher dashboard** from the start screen (default passcode `biology` —
   change it in the file's `META` block before sharing). See `TEACHER_GUIDE.md` for
   details on combining results collected across multiple devices.
