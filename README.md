# APAI Chat – Document Tracking & Readiness

This repository supports the **APAI Chat** AI assistant at [eqap.ac.eco3sw.com](https://eqap.ac.eco3sw.com). It tracks all documents uploaded to the APAI Chat knowledge base, monitors their ingestion health, evaluates their RAG-readiness, and manages the question-answer dataset used to validate AI response quality.

---

## Files

| File | Description | Last Updated |
|------|-------------|--------------|
| `documents_uploaded.xlsx` | Initial document tracking list – current site state (June 2026) | 2026-06-03 |
| `documents_vs_site_comparison.xlsx` | Side-by-side comparison of site documents vs. tracking list | 2026-06-03 |
| `doc_readiness_checklist.xlsx` | Phase 1 documentation readiness checklist – 4 samples scored (auto) · 24 sampled docs selected · all 79 docs (auto) | 2026-06-03 |
| `ai-testing-evaluation-plan.md` | AI Testing & Evaluation Plan v1.4 – full test methodology reference | 2026-06-02 |

> **Versioning reminder:** When regenerating comparison or checklist files, add a version or date suffix (e.g. `_v2` or `_2026-07-01`) and update the file table above.
>
> **Update reminder:** Each time any file in this table is changed, update its **Last Updated** date here and commit.

---

## Summary (as of 2026-06-02)

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
| 15 | PREPRESS | Technical Note | 14.0 | TN Apogee Prepress 14 - Custom Media advanced mode |
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

**Worked examples (scored 2026-06-03):**

| Document | C1 | C2 | C3 | C4 | C5 | C6 | C7 | C8 | Avg | Flag |
|----------|----|----|----|----|----|----|----|----|-----|------|
| Apogee-Impose-Trick\_Automatic-Page-Numbering | 4 | 4 | 4 | 4 | 3 | 4 | 3 | 4 | 3.75 | — |
| Apogee-Impose-Trick\_Folding-Direction-Arrow | 3 | 4 | 4 | 4 | **2** | 3 | 3 | 4 | 3.38 | ⚠ C5: fold arrow meaning is image-only |
| Apogee-InkDrive-Trick\_Accurate-CIP3-Presets | 3 | 4 | 4 | 4 | 3 | 3 | 3 | 4 | 3.50 | — |
| ProductionCenter\_UG\_14.0\_en-US | 5 | 3 | 4 | 5 | 4 | 5 | 3 | 3 | 4.00 | — |

> The ProductionCenter User Guide is the top scorer so far (avg 4.00). It has 12 numbered chapters, a full glossary, and text-complete procedures — basically the gold standard for what a RAG-ready document looks like. The only soft spots are self-containment (C2=3) and chunk-friendliness (C8=3), which are unavoidable in a 260-page reference guide that naturally cross-references itself. If your document scores lower than this one, it needs work.

**Steps to complete:**
1. Open `doc_readiness_checklist.xlsx` → **Readiness Checklist** sheet
2. For each sample row, convert the PDF to `.txt` using `pdftotext -layout` (MiKTeX provides this at `miktex\bin\x64\pdftotext.exe`)
3. Read the `.txt` file and score each of the 8 criteria (1–5) using the guidance above
4. Fill in the **Priority Action** column for any criterion scoring ≤ 2
5. When re-run, save with a version/date suffix and update the file table above
6. Commit and push

---

### 3. Question & Answer Dataset — Build, Validate, and Export

For each sampled document, generate questions per section based on the document content, validate each question-answer pair against the source document, and export the results as the gold-standard test dataset for Phase 2 of the AI Testing & Evaluation Plan.

**Output file:** `qa_dataset.xlsx` (or `qa_dataset_YYYY-MM-DD.xlsx` for versioned runs)

**Question types to generate** (per Section 6 of AI Testing & Evaluation Plan):

| Type | Route | Example pattern |
|------|-------|-----------------|
| Definition | DEFINITION | "What is \[term\]?" / "What does \[feature\] do?" |
| How-To | HOW\_TO | "How do I \[action\]?" / "What are the steps to \[procedure\]?" |
| Comparison | COMPARISON | "What is the difference between \[X\] and \[Y\]?" |
| Troubleshooting | TROUBLESHOOTING | "Why does \[error/symptom\] occur?" / "How do I fix \[issue\]?" |
| General | OTHER | Broad questions covered by the document |

**Output file structure — `qa_dataset.xlsx`:**

| Column | Description |
|--------|-------------|
| ID | Unique identifier (e.g. `TEST-001`) |
| Document | Source document name |
| Section | Section or heading within the document |
| Question | The generated question |
| Question Type | DEFINITION / HOW\_TO / COMPARISON / TROUBLESHOOTING / OTHER |
| Difficulty | Easy / Medium / Hard |
| Gold Passage | Verbatim quoted text from the document that answers the question |
| Reference Answer | Short expected answer |
| Answerable | Yes / No |
| Should Refuse | Yes / No |
| Refuse Reason | PRICING / OUT\_OF\_SCOPE / PII / (blank) |
| Validated | Yes / No / Partial |
| Validation Notes | Any issues found during validation against source document |

**Steps:**
1. For each document in the **Readiness Checklist** sample:
   - Read each section heading
   - Generate 2–5 questions per section covering the question types above
   - Quote the exact passage from the document that answers each question (Gold Passage)
   - Write a short reference answer
2. Validate each question-answer pair:
   - Confirm the gold passage exists verbatim in the source document
   - Confirm the reference answer is consistent with the gold passage
   - Mark `Validated = Yes / No / Partial` accordingly
3. Export to `qa_dataset.xlsx`
4. Version-stamp when re-run (e.g. `qa_dataset_v2.xlsx`)
5. Update this README (file table, summary count)
6. Commit and push

**Pending items:**
- [ ] Complete readiness scoring (Task 2) before generating questions — documents scoring ≤ 2 should be remediated first
- [ ] Generate Q&A for all 24 sampled documents
- [ ] Second-person review of each validated pair before use in testing

---

## Document Categories

- Tips & Tricks (Apogee Impose, InkDrive, Proofing, Packaging, WebApproval, Automation — and ProductionCenter)
- Tutorials – Impose, Prepress v14/v15, ProductionCenter, QMS, Proofing
- Technical Notes – Proofing v14
- Reference Guides & Online Help (Prepress, Impose, QMS, ProductionCenter, PrintSphere)
