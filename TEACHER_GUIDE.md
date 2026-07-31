# Biology Pre / Post Diagnostic — Teacher Guide & Answer Key

**Course:** Biology I, Grade 10 (Georgia Standards of Excellence, 26.01200)  
**Assessment:** 40-item multiple-choice diagnostic, aligned to the Georgia Milestones Biology EOC blueprint  
**Use:** Administer as a **pre-test** (Week 1) to guide instruction, and again as a **post-test** (Week 18) to measure semester growth.

## 1. What this package contains

| File | Purpose |
|---|---|
| `biology-pre-post-diagnostic.html` | The online test students take. Self-contained — no internet, login, or install needed. Auto-scores and reports by standard. |
| `TEACHER_GUIDE.md` | This document: administration, data, alignment, and the full answer key. |
| `item-bank.json` | The raw item data (stems, options, key, standard, DOK) for reuse or import into another platform. |

## 2. How to administer online

1. **Share the test.** Open `biology-pre-post-diagnostic.html` in any browser and share the page/link with students (post it in your LMS, Google Classroom, or a shared drive; it also runs from a USB or local file).
2. **Students log in.** Each student types their name and class period, chooses **Pre-Test** or **Post-Test**, and clicks *Begin*.
3. **Taking the test.** One question per screen, with a progress bar, a *Flag for review* button, a full question navigator, and free forward/back movement. No time limit. Answers can be changed until submitted.
4. **On submit**, the student sees their score, projected achievement level, and a breakdown by reporting category — but **not** the correct answers, so items stay secure for the post-test.

## 3. Getting robust data to individualize instruction

Open the **Teacher dashboard** (button at the bottom of the start screen; default passcode **`biology`**). It gives you:

- **Class overview** — average score, achievement-level distribution, and strongest/weakest reporting categories.
- **Standard mastery** — a color-coded table of class % correct for every standard element (SB1.a … SB6.e). Red (<50%) = reteach, amber (50–69%) = reinforce, green (70%+) = on track.
- **Students** — each student's score, projected level, and focus areas; tap a row for a standard-by-standard breakdown.
- **Growth (Pre→Post)** — for any student with both tests recorded, the change in total and per-category scores.
- **Grouping & reteach** — ready-made small-group lists of the students below 50% in each category and standard.
- **Data** — export the whole class as one CSV, or paste in rows students submitted from their own devices to combine everything in one place.

> **Change the teacher passcode** in the file's `META` block before sharing with students.

## 3a. Automatic logging to a Google Sheet (recommended for whole-class data)

Send every submission straight into one Google Sheet — no per-student sign-in, no manual collecting. Each row lands with the score, projected level, per-category percentages, and every answer, so you can sort, filter, and pivot however you like.

**One-time setup (about 5 minutes):**

1. Go to **sheets.new** to create a blank Google Sheet.
2. **Extensions → Apps Script.** Delete the sample code, paste the script in section 3b below, and click **Save**.
3. **Deploy → New deployment → Web app.** Set **Execute as: Me** and **Who has access: Anyone**. Click **Deploy** and authorize when prompted.
4. Copy the **Web app URL** it gives you (ends in `/exec`).
5. Put that URL into the test — either paste it in the Teacher dashboard → **Data** tab (that device only), or, to cover every student, open `biology-pre-post-diagnostic.html` in a text editor and paste it between the quotes on the line `const SHEET_ENDPOINT = "";` near the top, then share that file.
6. Use **Send a test row** in the Data tab to confirm a row appears in your sheet.

> **Where it runs:** live logging works from the **downloaded or hosted file** — put it in your LMS, Google Drive/Sites, or open it locally. The claude.ai online preview blocks outside connections for security, so use the actual file for real class logging. Local saving and CSV export always work as a backup either way.

### 3b. Google Apps Script code

```javascript
// Google Apps Script — paste into your Sheet's Apps Script editor (Extensions > Apps Script)
// Then Deploy > New deployment > Web app (Execute as: Me, Who has access: Anyone).
function doPost(e) {
  var lock = LockService.getScriptLock();
  lock.waitLock(30000);
  try {
    var ss = SpreadsheetApp.getActiveSpreadsheet();
    var sheet = ss.getSheetByName('Results') || ss.insertSheet('Results');
    var body = JSON.parse(e.postData.contents);
    if (sheet.getLastRow() === 0 && body.header) {
      sheet.appendRow(body.header);
      sheet.setFrozenRows(1);
    }
    sheet.appendRow(body.row);
    return ContentService
      .createTextOutput(JSON.stringify({ ok: true }))
      .setMimeType(ContentService.MimeType.JSON);
  } catch (err) {
    return ContentService
      .createTextOutput(JSON.stringify({ ok: false, error: String(err) }))
      .setMimeType(ContentService.MimeType.JSON);
  } finally {
    lock.releaseLock();
  }
}
```

## 4. Blueprint alignment

Item counts mirror the Georgia Milestones Biology reporting-category weights.

| Reporting category | Standards | Blueprint weight | Items on this test |
|---|---|---|---|
| Cells | SB1 | 20% | 8 |
| Cellular Genetics & Heredity | SB2, SB3 | 23% | 9 |
| Classification & Phylogeny | SB4 | 13% | 5 |
| Ecology | SB5 | 27% | 11 |
| Theory of Evolution | SB6 | 17% | 7 |
| **Total** | | **100%** | **40** |

**Depth of Knowledge (DOK):** Level 1 (recall) — 7 items (18%); Level 2 (skill/concept) — 23 items (57%); Level 3 (strategic reasoning) — 10 items (25%). This matches the blueprint targets (L1 10–20%, L2 50–60%, L3 25–35%).

## 5. Achievement levels (projected)

Projected from percent correct as an instructional guide — **not** an official Georgia Milestones scale score.

| Level | Percent correct |
|---|---|
| Beginning Learner | Below 40% |
| Developing Learner | 40–59% |
| Proficient Learner | 60–79% |
| Distinguished Learner | 80–100% |

## 6. Item-writing quality checks

- **Balanced answer key:** correct answers are evenly distributed — **A: 10, B: 10, C: 10, D: 10** (10 each).
- **No length cue:** the correct answer is the single longest option in only 9 of 40 items (below the 25% chance level), so "pick the longest answer" does not work.
- **Distractors** are built from common student misconceptions noted in the Georgia Biology Teacher Notes.

## 7. Answer key & item map

| # | Standard | DOK | Key | Correct answer |
|---|---|---|---|---|
| 1 | SB1.a | 1 | **A** | Mitochondrion |
| 2 | SB1.a | 2 | **B** | work together as a system to maintain homeostasis |
| 3 | SB1.b | 2 | **C** | Mitosis makes identical cells; meiosis makes varied gametes |
| 4 | SB1.b | 2 | **C** | copies the DNA so the new cells match the parent |
| 5 | SB1.c | 1 | **A** | Nucleic acid |
| 6 | SB1.d | 3 | **C** | Water will move out of the cell, causing it to shrink |
| 7 | SB1.d | 2 | **D** | Diffusion |
| 8 | SB1.e | 2 | **B** | The products of one process are the reactants of the other |
| 9 | SB2.a | 1 | **A** | nucleotides |
| 10 | SB2.a | 2 | **D** | Transcription |
| 11 | SB2.b | 1 | **D** | mutation |
| 12 | SB2.b | 3 | **B** | swaps segments between homologous chromosomes |
| 13 | SB2.c | 2 | **D** | Possible long-term effects on health are still debated |
| 14 | SB3.a | 2 | **A** | Alleles separating into different gametes |
| 15 | SB3.b | 2 | **B** | 1/4 |
| 16 | SB3.b | 3 | **B** | 1 red : 2 pink : 1 white |
| 17 | SB3.c | 2 | **B** | A single parent can reproduce quickly |
| 18 | SB4.a | 2 | **C** | were once free-living bacteria taken in by a host cell |
| 19 | SB4.a | 1 | **C** | Bacteria |
| 20 | SB4.b | 3 | **D** | the most closely related |
| 21 | SB4.c | 2 | **C** | They cannot reproduce without a host cell |
| 22 | SB4.b | 2 | **B** | share a common ancestor |
| 23 | SB5.a | 1 | **A** | carrying capacity |
| 24 | SB5.a | 2 | **A** | Disease spreading as the population grows |
| 25 | SB5.a | 2 | **D** | strongly affects its ecosystem despite low numbers |
| 26 | SB5.b | 2 | **A** | decreases |
| 27 | SB5.b | 3 | **C** | They lose their main source of food |
| 28 | SB5.b | 2 | **D** | They return nutrients to the soil |
| 29 | SB5.c | 3 | **D** | provides more ways to recover from disturbance |
| 30 | SB5.d | 2 | **C** | Restoring wetlands and native plants |
| 31 | SB5.d | 2 | **D** | outcompetes native species for resources |
| 32 | SB5.e | 2 | **B** | can tolerate the new conditions with its traits |
| 33 | SB5.a | 3 | **D** | reached its carrying capacity |
| 34 | SB6.a | 2 | **A** | supporting the idea that species change over time |
| 35 | SB6.b | 1 | **B** | biodiversity |
| 36 | SB6.c | 2 | **B** | common ancestry |
| 37 | SB6.c | 3 | **A** | They have very similar DNA and protein sequences |
| 38 | SB6.d | 3 | **A** | changes allele frequencies by chance |
| 39 | SB6.e | 3 | **C** | lets resistant bacteria survive and reproduce |
| 40 | SB6.e | 2 | **C** | Those best suited to their environment |

## 8. Full test master copy

Correct answer marked with ✅.

**1. (SB1.a, DOK 1)** Which organelle is the primary site of cellular respiration, releasing energy the cell can use?

- A. Mitochondrion ✅
- B. Ribosome
- C. Golgi apparatus
- D. Vacuole

**2. (SB1.a, DOK 2)** A cell's membrane controls what enters and leaves, its ribosomes build proteins, and its mitochondria supply energy. This coordinated activity best shows how organelles —

- A. compete with one another for limited space
- B. work together as a system to maintain homeostasis ✅
- C. each carry out every cell function independently
- D. function only during cell division

**3. (SB1.b, DOK 2)** How does mitosis differ from meiosis?

- A. Meiosis produces two cells identical to the parent cell
- B. Mitosis produces four unique gametes used for reproduction
- C. Mitosis makes identical cells; meiosis makes varied gametes ✅
- D. Both processes always produce cells with doubled chromosome numbers

**4. (SB1.b, DOK 2)** Binary fission in bacteria and mitosis in your skin cells both maintain genetic continuity because each —

- A. reduces the chromosome number by half each cycle
- B. requires two parent organisms in order to occur
- C. copies the DNA so the new cells match the parent ✅
- D. produces gametes that are later used in fertilization

**5. (SB1.c, DOK 1)** Which type of macromolecule stores hereditary information and directs protein synthesis?

- A. Nucleic acid ✅
- B. Carbohydrate
- C. Lipid
- D. Phospholipid

**6. (SB1.d, DOK 3)** A freshwater plant cell is placed in very salty water. What will happen to the water in the cell?

- A. Water will move into the cell, causing it to swell
- B. Water will stay balanced because the cell is isotonic
- C. Water will move out of the cell, causing it to shrink ✅
- D. Water will stop moving across the membrane entirely

**7. (SB1.d, DOK 2)** Which process moves molecules from an area of high concentration to low concentration WITHOUT using cellular energy?

- A. Active transport
- B. Endocytosis
- C. Exocytosis
- D. Diffusion ✅

**8. (SB1.e, DOK 2)** Which statement best describes the relationship between photosynthesis and cellular respiration?

- A. Both processes release oxygen as a waste product
- B. The products of one process are the reactants of the other ✅
- C. Both processes occur only in animal cells
- D. Respiration stores energy while photosynthesis releases it

**9. (SB2.a, DOK 1)** The repeating subunits (monomers) that make up a molecule of DNA are called —

- A. nucleotides ✅
- B. amino acids
- C. fatty acids
- D. monosaccharides

**10. (SB2.a, DOK 2)** During which process is the information in DNA used to build a molecule of messenger RNA (mRNA)?

- A. Replication
- B. Translation
- C. Digestion
- D. Transcription ✅

**11. (SB2.b, DOK 1)** A change in the sequence of DNA bases, sometimes caused by radiation or certain chemicals, is called a —

- A. fertilization
- B. dominant trait
- C. phenotype
- D. mutation ✅

**12. (SB2.b, DOK 3)** Crossing over during meiosis increases genetic variation because it —

- A. makes exact copies of each chromosome for the gametes
- B. swaps segments between homologous chromosomes ✅
- C. lowers the total number of genes found in a cell
- D. stops fertilization from being able to take place

**13. (SB2.c, DOK 2)** Which is an ethical concern often raised about using biotechnology such as genetically modified crops?

- A. Modified crops can never increase how much food is produced
- B. DNA can never be moved between two different organisms
- C. The process always removes all genetic variation from crops
- D. Possible long-term effects on health are still debated ✅

**14. (SB3.a, DOK 2)** Mendel's law of segregation is explained by which event during meiosis?

- A. Alleles separating into different gametes ✅
- B. The copying of all the DNA before the cell divides
- C. Two gametes joining together during fertilization
- D. Chromosomes being copied in ordinary body cells

**15. (SB3.b, DOK 2)** In pea plants, tall (T) is dominant to short (t). If two Tt plants are crossed, what fraction of the offspring are expected to be short?

- A. 0 (none)
- B. 1/4 ✅
- C. 1/2
- D. 3/4

**16. (SB3.b, DOK 3)** In four-o'clock flowers, red (R) and white (W) alleles show incomplete dominance, so RW plants are pink. Crossing two pink plants gives offspring in about what ratio?

- A. all pink
- B. 1 red : 2 pink : 1 white ✅
- C. 3 red : 1 white
- D. all red

**17. (SB3.c, DOK 2)** Which is an advantage of asexual reproduction compared with sexual reproduction?

- A. It produces much greater genetic variation
- B. A single parent can reproduce quickly ✅
- C. Offspring are better able to adapt to change
- D. It requires two parents and more total energy

**18. (SB4.a, DOK 2)** The theory of endosymbiosis explains the origin of mitochondria and chloroplasts by proposing that they —

- A. developed from inward folds of the cell membrane over time
- B. split off from the cell's nucleus a very long time ago
- C. were once free-living bacteria taken in by a host cell ✅
- D. are built only out of nucleic acids

**19. (SB4.a, DOK 1)** Which group of organisms is made of cells that LACK a membrane-bound nucleus?

- A. Animals
- B. Plants
- C. Bacteria ✅
- D. Fungi

**20. (SB4.b, DOK 3)** On a cladogram, two species whose branches share the most recent common ancestor are —

- A. the most distantly related
- B. unrelated to all other species
- C. identical in every trait
- D. the most closely related ✅

**21. (SB4.c, DOK 2)** Why do many scientists argue that viruses are NOT truly living organisms?

- A. They contain genetic material
- B. They are made of proteins
- C. They cannot reproduce without a host cell ✅
- D. They are able to cause diseases

**22. (SB4.b, DOK 2)** Two species are found to have very similar DNA and protein sequences. This is best used as evidence that they —

- A. live in the same habitat
- B. share a common ancestor ✅
- C. are the same species
- D. do not evolve at all

**23. (SB5.a, DOK 1)** The largest population size that an environment can support over time is called its —

- A. carrying capacity ✅
- B. biodiversity
- C. keystone species
- D. limiting factor

**24. (SB5.a, DOK 2)** Which is a density-dependent limiting factor for a growing deer population?

- A. Disease spreading as the population grows ✅
- B. An unusually severe drought during the winter
- C. A fast-moving forest fire in the area
- D. A sudden drop in the outdoor temperature

**25. (SB5.a, DOK 2)** A keystone species is best described as one that —

- A. is the single largest organism found in its ecosystem
- B. is always the top predator in a food web
- C. simply lives longer than the other species do
- D. strongly affects its ecosystem despite low numbers ✅

**26. (SB5.b, DOK 2)** In an energy pyramid, the amount of energy available at each higher level —

- A. decreases ✅
- B. increases
- C. stays exactly the same
- D. disappears completely

**27. (SB5.b, DOK 3)** A disease kills most of the producers in a food web. What is the most immediate effect on the primary consumers?

- A. They increase rapidly in number
- B. They become producers themselves
- C. They lose their main source of food ✅
- D. They gain more available energy

**28. (SB5.b, DOK 2)** Which statement best explains why decomposers are essential in an ecosystem?

- A. They make most of the oxygen in the air
- B. They give energy directly to the sun
- C. They keep matter from cycling at all
- D. They return nutrients to the soil ✅

**29. (SB5.c, DOK 3)** A greater variety of species (high biodiversity) usually makes an ecosystem more stable because it —

- A. prevents any change from ever occurring
- B. guarantees that no species will ever go extinct
- C. removes all competition among the organisms
- D. provides more ways to recover from disturbance ✅

**30. (SB5.d, DOK 2)** Which human action would most directly REDUCE the negative impact of humans on the environment?

- A. Clearing large areas of forest for new farmland
- B. Releasing a non-native fish into a lake
- C. Restoring wetlands and native plants ✅
- D. Burning more fossil fuels to produce energy

**31. (SB5.d, DOK 2)** Introducing a non-native (invasive) species to an ecosystem often reduces biodiversity because the invader —

- A. almost always dies off very quickly
- B. increases the food supply for every species
- C. has many natural predators already present
- D. outcompetes native species for resources ✅

**32. (SB5.e, DOK 2)** An organism is MOST likely to survive an environmental change if it —

- A. completely stops reproducing during the change
- B. can tolerate the new conditions with its traits ✅
- C. carries no genetic variation at all in its population
- D. happens to be the largest member of its species

**33. (SB5.a, DOK 3)** A population grows quickly and then levels off near a steady size. The leveling off happens because the population has —

- A. run out of every resource all at once
- B. no limiting factors acting on it
- C. permanently stopped reproducing
- D. reached its carrying capacity ✅

**34. (SB6.a, DOK 2)** New understandings of Earth's great age and the fossil record influenced biology mainly by —

- A. supporting the idea that species change over time ✅
- B. proving that species can never change at all
- C. showing that Earth is only a few thousand years old
- D. disproving everything that is known about genetics

**35. (SB6.b, DOK 1)** Speciation, the formation of new species over time, tends to increase an area's —

- A. extinction rate only
- B. biodiversity ✅
- C. age of the Earth
- D. average body size

**36. (SB6.c, DOK 2)** The forelimbs of humans, whales, and bats all share the same basic bone arrangement. These homologous structures are evidence of —

- A. identical environments
- B. common ancestry ✅
- C. completely different genetic codes
- D. unrelated origins

**37. (SB6.c, DOK 3)** Which additional finding would BEST support the claim that two species share a common ancestor?

- A. They have very similar DNA and protein sequences ✅
- B. They happen to live on the same continent
- C. They are about the same color
- D. They are hunted by the same predator

**38. (SB6.d, DOK 3)** Genetic drift differs from natural selection because genetic drift —

- A. changes allele frequencies by chance ✅
- B. always improves an organism's survival
- C. occurs only in very large populations
- D. never changes a population at all

**39. (SB6.e, DOK 3)** Repeated use of an antibiotic can produce a resistant bacterial population because the antibiotic —

- A. causes the bacteria to mutate on purpose each time
- B. teaches the bacteria how to become stronger
- C. lets resistant bacteria survive and reproduce ✅
- D. has no real effect on the bacteria at all

**40. (SB6.e, DOK 2)** In natural selection, which individuals are most likely to pass their traits to the next generation?

- A. The largest individuals in the group
- B. The youngest individuals in the group
- C. Those best suited to their environment ✅
- D. Those that reproduce the least often
