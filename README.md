# APAI Chat – Document Tracking

This repository tracks the documents uploaded to the **APAI Chat** knowledge base at [eqap.ac.eco3sw.com](https://eqap.ac.eco3sw.com/documents).

## Files

| File | Description |
|------|-------------|
| `documents_uploaded.xlsx` | Initial document tracking list – current site state (June 2026) |
| `documents_vs_site_comparison.xlsx` | Side-by-side comparison of site documents vs. tracking list |
| `doc_readiness_checklist.xlsx` | Phase 1 documentation readiness checklist (Section 5 of AI Testing & Evaluation Plan) |

## Summary (as of 2026-06-02)

- **79 documents** currently uploaded to the APAI Chat site
- All documents in `documents_uploaded.xlsx` match the site (Service Manuals not yet uploaded)
- Audience fields split into separate columns in the comparison file
- Site document status tracked: COMPLETED / PARTIALLY\_COMPLETED / FAILED

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
5. Regenerate `documents_vs_site_comparison.xlsx` with a version or date suffix (e.g. `documents_vs_site_comparison_v2.xlsx` or `documents_vs_site_comparison_2026-07-01.xlsx`)
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
| **Readiness Checklist** | 15 sampled documents scored on 8 criteria | Manual review required |

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

**Sample selection** — one document per product × doc type × version category (15 samples total):

| Product | Doc Type | Version | Sample Document |
|---------|----------|---------|-----------------|
| APOGEE | Tips & Tricks | 14.0 | Apogee-Impose-Trick\_Automatic-Page-Numbering |
| PREPRESS | Tips & Tricks | 14.0 | Apogee-Trick\_Apogee-DQS |
| PREPRESS | Online Help | 14.0 | Apogee\_Prepress\_OLH\_14.0.2\_en-US |
| PREPRESS | Reference Guide | 14.0 | Apogee\_Impose\_RG\_14.0.1\_en-US |
| PREPRESS | Reference Guide (QMS) | 14.0 | Apogee Prepress\_QMS\_OLH |
| PREPRESS | Tutorial | 14.0 | Basic Administrative Tasks |
| PREPRESS | Tutorial – Impose | 14.0 | Lesson 26 - Number-Up Cut and Assemble |
| PREPRESS | Technical Note | 14.0 | TN Apogee Prepress 14 - Custom Media advanced mode |
| PREPRESS | Tutorial – QMS | 14.0 | QMS-Check-and-Double-Check |
| PREPRESS | Tutorial – Proofing | 14.0 | Proofing-Contract-Proofing |
| PREPRESS | Tutorial | 15.0 | Advanced Job Management |
| PREPRESS | Online Help | 3.0 | PrintSphere\_OLH\_en-US\_draft01 |
| PRODUCTION\_CENTER | User Guide | 14.0 | ProductionCenter\_UG\_14.0\_en-US |
| PRODUCTION\_CENTER | Tips & Tricks | 14.0 | ProductionCenter-Tips\_Passkeys |
| PRODUCTION\_CENTER | Tutorial | 14.0 | Approve and reject pages |

**Steps to complete:**
1. Open `doc_readiness_checklist.xlsx` → **Readiness Checklist** sheet
2. For each sample row, open the corresponding PDF
3. Score each of the 8 criteria (1–5) based on the definitions above
4. Fill in the **Priority Action** column for any criterion scoring ≤ 2
5. Update `doc_readiness_checklist.xlsx` with a version/date suffix when re-run
6. Commit and push

---

## Document Categories

- Tips & Tricks (Apogee, ProductionCenter)
- Tutorials – Impose, Prepress v14/v15, ProductionCenter
- Technical Notes – Proofing v14
- QMS Tutorials
- Reference Guides & Online Help
