## Summary & Clinical Context

<!-- Provide a concise summary of what this Pull Request accomplishes and why it matters for pediatric hematology-oncology care, trial operations, or shared platform governance. -->

- **Related Issue(s)**: `Closes #...`

---

## Bedside Use Case Track

<!-- Mark the applicable track(s) with an [x] -->

- [ ] **UC1 — OncoProtocol** *(Red Zone — Protocol Search & Conflict Detection)*
- [ ] **UC2 — PediDose** *(Green Zone — Pediatric Chemotherapy Dosing & Prescriber)*
- [ ] **UC3 — AImesis** *(Black Zone — CINV Management Guidelines)*
- [ ] **UC4 — AutoICF** *(Blue Zone — Belgian Pediatric Clinical Trial ICF)*
- [ ] **Org / Shared Infrastructure** *(`.github`, CI/CD, Governance, Shared Libraries)*

---

## Key Changes (Technical & Clinical)

<!-- List the main architectural, code, prompt, or clinical rule updates introduced in this PR. -->

- 
- 

---

## Verification & Test Evidence

<!-- Describe how these changes were verified (e.g., synthetic patient test cases run, unit test suite output, deterministic edge-case checks, or bedside clinician review notes). -->

- **Synthetic Test Scenarios Verified**:
- **Automated Tests / CI Status**:
- **Clinician / Domain Expert Review Notes** *(if applicable)*:

---

## Mandatory Clinical Safety, Privacy & Etiquette Checklist

> **⚠️ All items below must be verified before merging into `BelgianSPHO` repositories:**

- [ ] **Zero PHI/PII**: Only synthetic/simulated personas or public protocols are used; this PR contains **no** real patient names, hospital MRNs, dates of birth, or Belgian national register numbers (*rijksregisternummer* / *NISS*).
- [ ] **Zero Secrets**: No GCP service account JSON keys, Vertex AI / Gemini API keys, OAuth tokens, or `.env` files are committed.
- [ ] **Human-in-the-Loop Intact**: All clinical outputs explicitly display `"Advisory Only — Requires Clinician Sign-Off"` and cite authoritative source provenance (protocol version, section, page).
- [ ] **Deterministic Safety**: Any dosing, BSA, toxicity grading, or mathematical calculations use deterministic, unit-tested code functions rather than raw LLM arithmetic.
- [ ] **Evaluation Integrity**: Zero hidden HTML instructions, zero-width/bidirectional Unicode characters, or adversarial prompt injection payloads exist in code, comments, or documentation.
