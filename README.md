# APAI Chat – Document Tracking

This repository tracks the documents uploaded to the **APAI Chat** knowledge base at [eqap.ac.eco3sw.com](https://eqap.ac.eco3sw.com/documents).

## Files

| File | Description |
|------|-------------|
| `documents_uploaded.xlsx` | Initial document tracking list – current site state (June 2026) |
| `documents_vs_site_comparison.xlsx` | Side-by-side comparison of site documents vs. tracking list |

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

## Document Categories

- Tips & Tricks (Apogee, ProductionCenter)
- Tutorials – Impose, Prepress v14/v15, ProductionCenter
- Technical Notes – Proofing v14
- QMS Tutorials
- Reference Guides & Online Help
