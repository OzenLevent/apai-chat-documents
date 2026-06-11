# APAI Chat – Document Tracking & Readiness

This repository supports the **APAI Chat** AI assistant at [eqap.ac.eco3sw.com](https://eqap.ac.eco3sw.com). It tracks all documents uploaded to the APAI Chat knowledge base, monitors their ingestion health, evaluates their RAG-readiness, and manages the question-answer dataset used to validate AI response quality.

---

## Files

| File | Description | Last Updated |
|------|-------------|--------------|
| `documents_uploaded.xlsx` | Initial document tracking list – current site state (June 2026) | 2026-06-03 |
| `documents_vs_site_comparison.xlsx` | Side-by-side comparison of site documents vs. tracking list | 2026-06-03 |
| `doc_readiness_checklist.xlsx` | Phase 1 documentation readiness checklist – 14 samples scored · 24 sampled docs selected · all 79 docs (auto) | 2026-06-11 |
| `ai-testing-evaluation-plan.md` | AI Testing & Evaluation Plan v1.4 – full test methodology reference | 2026-06-02 |
| `qa_test.xlsx` | Test Q&A dataset – 4 sheets (one per scored document) · 72 questions total · 58 from ProductionCenter UG · **72 questions tested (4 sheets complete · 46 Pass / 26 Fail · 64%)** | 2026-06-03 |

> **Versioning reminder:** When regenerating comparison or checklist files, add a version or date suffix (e.g. `_v2` or `_2026-07-01`) and update the file table above.
>
> **Update reminder:** Each time any file in this table is changed, update its **Last Updated** date here and commit.

---

## Summary (as of 2026-06-03)

- **79 documents** currently uploaded to the APAI Chat site
- All documents in `documents_uploaded.xlsx` match the site (Service Manuals not yet uploaded)
- Audience fields split into separate columns in the comparison file
- Site document status tracked: COMPLETED / PARTIALLY\_COMPLETED / FAILED
- **24 documents** selected for manual readiness scoring across all product × doc type × version categories

---

## Maintenance Tasks

### 1. Check & Maintain Uploaded Documents

Regularly verify that the documents tracked in `documents_uploaded.xlsx` match what is actually uploaded on the APAI Chat site.

**Steps:**
1. Log in to [eqap.ac.eco3sw.com/documents](https://eqap.ac.eco3sw.com/documents)
2. Fetch the current file list from the API (`/api/apai/files`)
3. Compare against `documents_uploaded.xlsx` — check for:
   - Documents in the tracking list but **missing from the site** → need to be uploaded
   - Documents on the site but **not in the tracking list** → need to be added to the list
   - Status issues: `PARTIALLY_COMPLETED` or `FAILED` → need to be re-uploaded
4. Update `documents_uploaded.xlsx` to reflect any changes
5. Regenerate `documents_vs_site_comparison.xlsx` with a version or date suffix
6. Update this README (Summary section, file table if filename changed)
7. Commit and push all changes

**Pending items:**
- [ ] Upload **SM JDF Prepress 15.0 Service Manual** to the site
- [ ] Upload **SM Prepress 15 - Service Manual** to the site

---

### 2. Documentation Readiness Check (Phase 1 — AI Testing & Evaluation Plan)

Based on **Section 5** of the AI Testing & Evaluation Plan (`ai-testing-evaluation-plan.md` v1.4), each uploaded document must be evaluated for RAG-friendliness using an 8-criterion checklist.

**File:** `doc_readiness_checklist.xlsx` — two sheets:

| Sheet | Content | How populated |
|-------|---------|---------------|
| **All Documents – Status** | All 79 site documents with ingestion health (status, chunks, failed images) | Automated from API |
| **Readiness Checklist** | 24 sampled documents scored on 8 criteria | Manual review required |

**Scoring criteria (1–5 each):**

| # | Criterion | What to check |
|---|-----------|---------------|
| 1 | Structural clarity | Clear headings, logical hierarchy |
| 2 | Self-containment | Each section understandable independently |
| 3 | Explicit context | Product name, version, prerequisites stated per section |
| 4 | Terminology consistency | Terms used consistently throughout |
| 5 | Text / image ratio | Key information in text, not only images |
| 6 | Procedure clarity | Steps numbered, ordered, complete with warnings |
| 7 | Error / troubleshooting proximity | Symptoms near their resolutions |
| 8 | Chunk-friendliness | A ~375-word excerpt makes sense on its own |

> ⚠ Documents scoring **≤ 2** on any criterion need remediation before launch.

**Sample selection — 24 documents** across all product × doc type × version categories:

| # | Product | Category | Version | Sample Document |
|---|---------|----------|---------|-----------------|
| 1 | APOGEE | Tips & Tricks – Impose | 14.0 | Apogee-Impose-Trick\_Automatic-Page-Numbering |
| 2 | APOGEE | Tips & Tricks – Impose (Folding) | 14.0 | Apogee-Impose-Trick\_Folding-Direction-Arrow |
| 3 | APOGEE | Tips & Tricks – InkDrive | 14.0 | Apogee-InkDrive-Trick\_Accurate-CIP3-Presets |
| 4 | PREPRESS | Tips & Tricks – Proofing | 14.0 | Apogee-Proofing-Trick\_GDIProofer-and-Split4ProofApogee |
| 5 | PREPRESS | Tips & Tricks – Packaging | 14.0 | Apogee-Tips\_Apogee-Prepress-with-Packaging-Pack |
| 6 | PREPRESS | Tips & Tricks – WebApproval | 14.0 | Apogee-Tips\_WebApproval-A-Fully-Integrated-Softproof-Solution |
| 7 | PREPRESS | Tips & Tricks – Automation | 14.0 | Apogee-Trick\_Auto-Route-PDF-Files-with-Automate-TP |
| 8 | PREPRESS | Tips & Tricks – General | 14.0 | Apogee-Trick\_Apogee-DQS |
| 9 | PREPRESS | Tips & Tricks – General | 14.0 | The Essential Role of Virus Scanning and Tuning |
| 10 | PREPRESS | Online Help | 14.0 | Apogee\_Prepress\_OLH\_14.0.2\_en-US |
| 11 | PREPRESS | Reference Guide | 14.0 | Apogee\_Impose\_RG\_14.0.1\_en-US |
| 12 | PREPRESS | Reference Guide (QMS) | 14.0 | Apogee Prepress\_QMS\_OLH |
| 13 | PREPRESS | Tutorial | 14.0 | Basic Administrative Tasks |
| 14 | PREPRESS | Tutorial – Impose | 14.0 | Lesson 26 - Number-Up Cut and Assemble |
| 15 | PREPRESS | Technical Note | 14.0 | TN Apogee Prepress 14 - settings and troubleshooting |
| 16 | PREPRESS | Tutorial – QMS | 14.0 | QMS-Check-and-Double-Check |
| 17 | PREPRESS | Tutorial – Proofing | 14.0 | Proofing-Contract-Proofing |
| 18 | PREPRESS | Tutorial | 15.0 | Advanced Job Management |
| 19 | PREPRESS | Online Help | 3.0 | PrintSphere\_OLH\_en-US\_draft01 |
| 20 | PRODUCTION\_CENTER | Tips & Tricks – Dashboard | 14.0 | ProductionCenter-Tips\_ECO3-Production-Dashboard |
| 21 | PRODUCTION\_CENTER | Tips & Tricks – Collaboration | 14.0 | ProductionCenter-Tips\_Enhanced-Collaboration |
| 22 | PRODUCTION\_CENTER | Tips & Tricks | 14.0 | ProductionCenter-Tips\_Passkeys |
| 23 | PRODUCTION\_CENTER | User Guide | 14.0 | ProductionCenter\_UG\_14.0\_en-US |
| 24 | PRODUCTION\_CENTER | Tutorial | 14.0 | Approve and reject pages |

**How to score each criterion:**

**1. Structural Clarity** — Look at the heading structure. Does the document have a clear title, section headings, and a logical flow? A score of 4–5 means headings are present and the document is easy to navigate. Score 3 if there is only one heading or content is a single block of text. Score 1–2 if there are no headings at all.

**2. Self-Containment** — Can you read a single section and understand it without reading the rest of the document or a different document? Tips & Tricks and standalone tutorials typically score 4–5. Chapters from a larger reference guide that assume prior sections may score 2–3.

**3. Explicit Context** — Is the product name, software version, and any prerequisite clearly stated? Check the header or introduction. If version and product are stated at the top and referenced within sections, score 4–5. If a reader would not know which product or version applies, score 1–2.

**4. Terminology Consistency** — Pick 3–5 key technical terms and check whether they are used the same way throughout. Inconsistent synonyms (e.g. "Press Sheet" vs "sheet" vs "imposition sheet" used interchangeably without definition) lower the score.

**5. Text / Image Ratio** — Read only the text (or the converted .txt file). Does the text alone convey the key information? If a procedure step says "see the arrow" or "notice the difference" and the meaning is only in an image, score 2. If all critical instructions are written out in text (images are supplementary), score 4–5.

**6. Procedure Clarity** — Are steps numbered, in order, and complete? Check for: numbered list, one action per step, any warnings or notes included inline. A document with no steps (conceptual only) scores 3 by default — not a weakness, just not applicable. Score 1–2 only if steps exist but are ambiguous or out of order.

**7. Error / Troubleshooting Proximity** — When the document mentions an error, symptom, or failure condition, is the resolution in the same section or on the same page? If the document has no troubleshooting content at all, score 3 (neutral). Score 4–5 only if symptoms and fixes are clearly paired.

**8. Chunk-Friendliness** — Imagine copying ~375 words (~half a page) from a random location in the document and showing it to the AI with no other context. Does that excerpt make sense on its own? Short documents (1–2 pages) almost always score 4–5. Long reference guides with dense cross-references may score 2–3.

> **Flag rule:** Any criterion scoring ≤ 2 must have a Priority Action entry explaining what needs to change before the document is suitable for RAG ingestion.

**Worked examples (scored as of 2026-06-11):**

| Document | C1 | C2 | C3 | C4 | C5 | C6 | C7 | C8 | Avg | Flag |
|----------|----|----|----|----|----|----|----|----|-----|------|
| Apogee-Impose-Trick\_Automatic-Page-Numbering | 4 | 4 | 4 | 4 | 3 | 4 | 3 | 4 | 3.75 | — |
| Apogee-Impose-Trick\_Folding-Direction-Arrow | 3 | 4 | 4 | 4 | **2** | 3 | 3 | 4 | 3.38 | ⚠ C5: fold arrow meaning is image-only |
| Apogee-InkDrive-Trick\_Accurate-CIP3-Presets | 3 | 4 | 4 | 4 | 3 | 3 | 3 | 4 | 3.50 | — |
| ProductionCenter\_UG\_14.0\_en-US | 5 | 3 | 4 | 5 | 4 | 5 | 3 | 3 | 4.00 | — |
| Apogee-Trick\_Apogee-DQS | 3 | 4 | 4 | 4 | 5 | **2** | **2** | 4 | 3.50 | ⚠ C6: no steps. C7: no troubleshooting |
| Lesson 26 - Number-Up Cut and Assemble | 4 | 3 | 4 | 5 | 3 | 5 | 3 | 3 | 3.75 | — |
| ProductionCenter-Tips\_Passkeys | 3 | 4 | 4 | 4 | 3 | 4 | **2** | 4 | 3.50 | ⚠ C7: no troubleshooting scenarios |
| Approve and reject pages | 5 | 4 | 4 | 5 | 4 | 5 | 4 | 4 | 4.38 | — |
| Apogee-Proofing-Trick\_GDIProofer-and-Split4ProofApogee | **2** | 4 | 4 | 4 | 5 | **2** | **2** | 4 | 3.38 | ⚠ C1: no headings. C6: no steps. C7: no troubleshooting |
| Apogee-Tips\_Apogee-Prepress-with-Packaging-Pack | 4 | 3 | 4 | 4 | 3 | **2** | **2** | 4 | 3.25 | ⚠ C6: overview only, no steps. C7: no troubleshooting |
| Apogee-Tips\_WebApproval-A-Fully-Integrated-Softproof-Solution | 4 | 3 | 4 | 4 | 3 | 3 | 4 | 3 | 3.50 | — |
| The Essential Role of Virus Scanning and Tuning | 3 | 5 | 4 | 4 | 5 | 3 | 4 | 4 | 4.00 | — |
| ProductionCenter-Tips\_ECO3-Production-Dashboard | 3 | 4 | 4 | 4 | 3 | 3 | **2** | 4 | 3.38 | ⚠ C7: no troubleshooting content |
| ProductionCenter-Tips\_Enhanced-Collaboration | 4 | 4 | 4 | 4 | 3 | 3 | **2** | 3 | 3.38 | ⚠ C7: no troubleshooting content |

> The **Approve and reject pages** tutorial is the top scorer in batch 2 (avg 4.38) — well-structured, fully procedural with numbered steps, and includes special-case handling. **ProductionCenter UG** remains the overall reference benchmark (avg 4.00 for a 260-page guide). The dominant pattern across Tips & Tricks documents is C7=2 (no troubleshooting content), which is expected for awareness documents but limits RAG effectiveness for problem-resolution queries. 10 documents remain to be scored.

**Steps to complete:**
1. Open `doc_readiness_checklist.xlsx` → **Readiness Checklist** sheet
2. For each sample row, convert the PDF to `.txt` using `pdftotext -layout` (MiKTeX provides this at `miktex\bin\x64\pdftotext.exe`)
3. Read the `.txt` file and score each of the 8 criteria (1–5) using the guidance above
4. Fill in the **Priority Action** column for any criterion scoring ≤ 2
5. When re-run, save with a version/date suffix and update the file table above
6. Commit and push

---

### 3. Question & Answer Dataset — Build, Test, and Validate

The purpose of this task is to test the quality of APAI Chat's answers against a set of reference questions drawn directly from the uploaded documents.

**How it works:**
1. Questions are generated from each sampled document and a reference answer is written from the source text
2. Each question is asked to APAI Chat at [eqap.ac.eco3sw.com](https://eqap.ac.eco3sw.com)
3. The AI's response is recorded and compared against the reference answer
4. The result is marked as Pass or Fail accordingly

**Current test file:** `qa_test.xlsx` — one sheet per scored document, 72 questions total

**Question types used** (per Section 6 of AI Testing & Evaluation Plan):

| Type | Example pattern |
|------|-----------------|
| DEFINITION | "What is \[term\]?" / "What does \[feature\] do?" |
| HOW\_TO | "How do I \[action\]?" / "What are the steps to \[procedure\]?" |
| COMPARISON | "What is the difference between \[X\] and \[Y\]?" |
| TROUBLESHOOTING | "Why does \[error/symptom\] occur?" / "How do I fix \[issue\]?" |
| OTHER | Broad questions covered by the document |

**Column structure — `qa_test.xlsx`:**

| Column | Purpose |
|--------|---------|
| ID | Unique question identifier per document (e.g. `PC-001`, `AP-IMP-001`) |
| Section / Page | Chapter, section heading, and page number where the answer is found in the source document |
| Question | The question to be asked to APAI Chat |
| Question Type | DEFINITION / HOW\_TO / COMPARISON / TROUBLESHOOTING / OTHER |
| Difficulty | Easy / Medium / Hard — indicates how specific or complex the answer is expected to be |
| Reference Answer (Expected Answer) | The expected correct answer, written verbatim or near-verbatim from the source document |
| Validated (Source) | `Yes` for all rows — confirms the reference answer was verified against the source document text before use |
| APAI-Chat Answer | **Team fills this in** — paste the exact response received from APAI Chat for this question |
| Found Source File | **Team fills this in** — the source file cited by APAI Chat in its response |
| Found Source Page | **Team fills this in** — the page number within that source file |
| Pass / Fail | **Team fills this in** — `Pass` if the APAI Chat answer matches the reference answer, `Fail` if it does not or is incomplete |
| Remarks | **Team fills this in** — optional notes, e.g. "answer was correct but incomplete", "AI referenced wrong version", "AI refused to answer" |

**Steps to run a test cycle:**
1. Open `qa_test.xlsx` and select a sheet (document)
2. For each row, copy the **Question** and ask it to APAI Chat at [eqap.ac.eco3sw.com](https://eqap.ac.eco3sw.com)
3. Paste the AI's response into the **APAI-Chat Answer** column
4. Compare the response against the **Reference Answer (Expected Answer)**
5. Fill in **Pass / Fail**: `Pass` if the answer is correct, `Fail` if it is wrong or incomplete
6. Add any notes in the **Remarks** column if needed
7. When a sheet is complete, save with a date suffix (e.g. `qa_test_2026-06-10.xlsx`) and commit

**Sheets in `qa_test.xlsx`:**

| Sheet | Document | Questions | Tested | Pass | Fail | Score |
|-------|----------|-----------|--------|------|------|-------|
| Impose - Auto Page Numbering | Apogee-Impose-Trick\_Automatic-Page-Numbering | 5 | ✅ Yes | 2 | 3 | 40% |
| Impose - Folding Arrow | Apogee-Impose-Trick\_Folding-Direction-Arrow | 4 | ✅ Yes | 3 | 1 | 75% |
| InkDrive - CIP3 Presets | Apogee-InkDrive-Trick\_Accurate-CIP3-Presets | 5 | ✅ Yes | 3 | 2 | 60% |
| ProductionCenter UG | ProductionCenter\_UG\_14.0\_en-US | 58 | ✅ Yes | 38 | 20 | 66% |
| **Total** | | **72** | **72** | **46** | **26** | **64%** |

**Pending items:**
- [ ] Complete readiness scoring for remaining 10 sample documents
- [ ] Expand `qa_test.xlsx` with questions for all 24 sampled documents

---

## Document Categories

- Tips & Tricks (Apogee Impose, InkDrive, Proofing, Packaging, WebApproval, Automation — and ProductionCenter)
- Tutorials – Impose, Prepress v14/v15, ProductionCenter, QMS, Proofing
- Technical Notes – Proofing v14
- Reference Guides & Online Help (Prepress, Impose, QMS, ProductionCenter, PrintSphere)
