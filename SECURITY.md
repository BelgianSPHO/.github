# Security, Clinical Safety & Data Privacy Policy

**Organization**: [Belgian Society of Paediatric Haematology and Oncology (BSPHO)](https://bspho.be/) (`BelgianSPHO`)  
**Initiative**: Hacking4Good / Solve with Google x BSPHO Pediatric Oncology Hackathon (2026) & Open-Source Clinical AI Ecosystem  
**Primary Security & Privacy Contact**: [`secretary@bspho.be`](mailto:secretary@bspho.be)

---

## Overview

The `BelgianSPHO` GitHub organization hosts open-source clinical decision support, regulatory automation, and care-coordination prototypes developed for pediatric haematology and oncology wards across Belgium. Because these repositories address high-stakes pediatric oncology workflows—spanning **Red Zone (`UC1 — OncoProtocol`)**, **Green Zone (`UC2 — PediDose`)**, **Black Zone (`UC3 — AImesis`)**, and **Blue Zone (`UC4 — AutoICF`)**—data privacy, cloud credential hygiene, and clinical AI safety guardrails are **non-negotiable**.

Every contributor, hackathon builder, clinical mentor, and maintainer must strictly adhere to the policies below before committing code, prompts, datasets, or documentation to any `BelgianSPHO` repository.

---

## 1. Emergency Procedure for Accidental PHI/PII or Secret Exposure

If you accidentally commit or upload **Protected Health Information (PHI)**, **Personally Identifiable Information (PII)**, unpublished hospital documents, or **live cloud/API credentials** to any branch, pull request, issue, or discussion in `BelgianSPHO`:

### ⚠️ DO NOT Open a Public GitHub Issue Containing the Sensitive Data
Opening a public issue that pastes, quotes, or links directly to exposed patient data or live credentials broadcasts the exposure to public watchers and search indexers.

### Immediate Step-by-Step Action Plan

1. **Notify BSPHO Security & Repo Admins Immediately**:
   - Send an urgent email to **[`secretary@bspho.be`](mailto:secretary@bspho.be)** with the exact subject line:
     ```text
     [URGENT-SECURITY/PHI] <repo-name>
     ```
   - Include:
     - Repository name and URL
     - Commit SHA(s), branch name(s), or PR/Issue number(s) affected
     - Brief classification of what was exposed (e.g., *unredacted hospital PDF*, *GCP service account key*, *patient identifier*) **without pasting the sensitive data itself into the email**
     - Your name, Table/Team ID (if at the hackathon), and phone/Slack/floor contact
   - **During Onsite Hackathon Events**: Immediately flag the **BSPHO GitHub Desk (Elias Schroons)** or the **GCP Sandbox & Tech Desk (Murat Eken)** in addition to sending the email.

2. **Rotate & Revoke Exposed Credentials Immediately (Within 5 Minutes)**:
   - Assume any credential pushed to a repository (even for a few seconds or on a non-default branch) is compromised.
   - **GCP Service Account Keys**: Delete the key immediately in IAM & Admin (`gcloud iam service-accounts keys delete <KEY_ID> --iam-account=<SA_EMAIL>`).
   - **Vertex AI / Google Cloud API Keys**: Restrict or delete the key in Google Cloud Console > APIs & Services > Credentials.
   - **GitHub Personal Access Tokens (PATs) / OAuth Tokens**: Revoke immediately under GitHub Settings > Developer settings.

3. **Purge Git History & Invalidate GitHub Caches**:
   - **Never rely on `git rm` + a new commit**—the sensitive payload remains permanently accessible in the `.git` commit graph.
   - Rewrite repository history using [`git-filter-repo`](https://github.com/newren/git-filter-repo):
     ```bash
     # Remove a sensitive file across all branches and tags
     git filter-repo --invert-paths --path path/to/sensitive_file.ext --force

     # Or scrub literal strings/secrets using a replacements file
     git filter-repo --replace-text replacements.txt --force
     ```
   - Force-push the cleaned history (`git push origin --force --all && git push origin --force --tags`).
   - Coordinate with `BelgianSPHO` organization administrators (`secretary@bspho.be`) to:
     - Delete any cached pull request refs (`refs/pull/*`) or dangling commits
     - Contact GitHub Support if necessary to trigger server-side `git gc` and purge CDN/web caches.

---

## 2. Zero-PHI/PII Data Mandate (GDPR & Belgian Healthcare Privacy)

All `BelgianSPHO` repositories operate under a strict **Zero-PHI/PII Mandate** in compliance with the **EU General Data Protection Regulation (GDPR — Regulation (EU) 2016/679)**, notably **Article 9** (processing of special categories of personal data concerning health and genetic data), the **Belgian Law of 30 July 2018** on the protection of natural persons with regard to the processing of personal data, and the **Belgian Law of 22 August 2002 on Patient Rights**.

### Explicit Checklist of Prohibited Identifiers

You must **NEVER** commit, hardcode, upload, or log any of the following in code, unit tests, prompt templates, screenshots, vector stores, or evaluation logs:

- [ ] **Real Patient or Family Names**: Full names, initials paired with clinical context, or parent/guardian names.
- [ ] **Belgian National Identifiers**: *Rijksregisternummer* / *Numéro de registre national* (NISS / INSZ — 11-digit national register numbers).
- [ ] **Hospital & Clinical Identifiers**: Medical Record Numbers (MRNs), *Elektronisch Patiëntendossier* (EPD / EAD) numbers, encounter IDs, accession numbers, or pharmacy order barcode IDs.
- [ ] **Exact Dates Associated with a Real Patient**: Exact dates of birth (DOB), admission dates, discharge dates, exact treatment/infusion timestamps, or dates of death.
- [ ] **Contact & Biometric Details**: Home addresses, postal codes combined with rare diagnoses, phone numbers, personal email addresses, or patient photographs/voice recordings.
- [ ] **Unredacted Clinical Notes & Letters**: Raw EHR exports, ward handover notes, pathology/cytogenetics reports, or discharge summaries from UZ Gent, UZA, Cliniques Universitaires Saint-Luc, UZ Leuven, HUDERF, or any other hospital.
- [ ] **Unpublished or Proprietary Hospital Documents**: Internal hospital SOPs, draft clinical trial protocols, or institutional guidelines that have **not** been explicitly cleared and preloaded by BSPHO for public/hackathon use.

### Synthetic Personas & Approved Datasets Only

- **100% Synthetic Patient Profiles**: Every test fixture, demo scenario, nursing verification sheet (`UC2`), antiemetic passport (`UC3`), and evaluation benchmark must use **100% synthetic pediatric personas** (e.g., *"Synthetic Patient: Lucas, 4y, 16.0 kg, 0.68 m²"*).
- **Approved Reference Corpus**: Only use publicly published clinical protocols (e.g., public `ALLTogether1` publications, POGO/MASCC guidelines, BCFI / Kinderformularium public formularies, FAMHP/EMA public ICF templates) or the curated, de-identified documents preloaded into the official event GCS buckets.

---

## 3. Cloud & Credential Security

### Strictly Prohibited in All Commits

Never commit any of the following files or token patterns to a `BelgianSPHO` repository:

| Prohibited Secret / File Type | Detection Signature / Pattern |
| :--- | :--- |
| **GCP Service Account Keys** | JSON files containing `"type": "service_account"` or PEM private key headers |
| **Google Cloud / Vertex AI API Keys** | Strings matching `AIza[0-9A-Za-z\-_]{35}` |
| **OAuth 2.0 Client Secrets** | `client_secret*.json`, refresh tokens, or bearer access tokens (`ya29.*`) |
| **GitHub Tokens & SSH Keys** | `ghp_*`, `github_pat_*`, `gho_*`, `ghs_*`, or private SSH keys (`id_rsa`, `id_ed25519`) |
| **Local Environment Files** | `.env`, `.env.local`, `.env.production`, `.gcloud/`, or Terraform state files (`*.tfstate`) |

### Required Cloud Authentication & Configuration Patterns

1. **Local Development — Application Default Credentials (ADC)**:
   - Authenticate locally using short-lived user credentials rather than downloaded JSON key files:
     ```bash
     gcloud auth application-default login
     ```
   - Client libraries (`google-genai`, `google-cloud-aiplatform`, `google-cloud-storage`, ADK) automatically detect ADC without any key file on disk.

2. **CI/CD & GitHub Actions — Workload Identity Federation (OIDC)**:
   - Use keyless **Workload Identity Federation** (`google-github-actions/auth@v2`) with short-lived OIDC tokens scoped to least-privilege IAM roles. Never store long-lived service account JSON blobs in GitHub Actions secrets when OIDC is available.

3. **Runtime Secrets — Google Cloud Secret Manager**:
   - Store any required third-party API keys or application secrets in **Google Cloud Secret Manager** (`europe-west1` preferred) and inject them at runtime via Cloud Run secret environment bindings.

4. **`.env.example` Templates Only**:
   - Ensure `.env` and `*.json` credential patterns are listed in `.gitignore`.
   - Provide a tracked `.env.example` containing **placeholder values only**:
     ```dotenv
     # .env.example — Copy to .env locally (NEVER commit .env)
     GOOGLE_CLOUD_PROJECT=your-gcp-project-id
     GOOGLE_CLOUD_LOCATION=europe-west1
     GCS_PROTOCOL_BUCKET=gs://your-curated-protocol-bucket
     ```

---

## 4. Clinical AI & LLM Safety Guardrails

Pediatric oncology leaves zero margin for silent hallucinations, unverified dosage math, or fabricated regulatory text. All `BelgianSPHO` repositories building with Large Language Models (LLMs), Retrieval-Augmented Generation (RAG), or agent frameworks must enforce the following four architectural guardrails:

### 4.1 Mandatory `"Advisory Only — Requires Clinician Sign-Off"` Framing

- **Not a Certified Medical Device**: Unless explicitly certified under **EU MDR (Regulation (EU) 2017/745)**, software in `BelgianSPHO` is developed for research, hackathon prototyping, and clinician-in-the-loop workflow support.
- **Persistent UI & Output Banner**: Every user interface, generated PDF/handout, dosing sheet, and API response must prominently display:
  > ⚠️ **CLINICAL DECISION SUPPORT PROTOTYPE — ADVISORY ONLY — REQUIRES INDEPENDENT CLINICIAN / PHARMACIST / ETHICS SIGN-OFF BEFORE BEDSIDE OR PATIENT USE.**
- **Explicit Clinician Verification Step**: Workflows that produce actionable documents (e.g., `UC2` nursing verification sheets, `UC3` patient antiemetic passports, `UC4` informed consent forms) must require an explicit human verification checkpoint before export or printing.

### 4.2 Deterministic Calculation Separation (Zero Raw LLM Arithmetic)

- **Never Delegate Medical Math to an LLM**: Generative models must **never** perform free-text mental arithmetic for drug dosing, body surface area (BSA), glomerular filtration rate (GFR), toxicity dose reductions, or multi-day chemotherapy cumulative totals.
- **Deterministic Code Execution (`UC2 — PediDose` & `UC3 — AImesis`)**:
  - LLMs may assist in extracting structured parameters (With strict schema validation) or formatting patient-friendly instructions, but **all quantitative calculations**—including BSA (`m²` via Mosteller/Haycock formulas), weight-based dosing (`mg/kg`, `mg/m²`), maximum dose caps, renal/hepatic adjustments, and emetic risk scoring—**must be executed by deterministic, unit-tested Python/TypeScript functions**.
  - Every calculation module must include automated unit tests covering edge cases (neonates/infants `< 10 kg`, obesity/BSA caps, maximum single/daily dose ceilings, and unit conversion traps such as `mg` vs. `mcg` / `µg`).

### 4.3 Citation & Provenance Grounding ("Cite or Refuse")

Every clinical or regulatory statement generated across the four zones must be deterministically traceable to an authoritative source document:

- **UC1 — Protocol Search Assistant (`OncoProtocol` / Red Zone)**:
  - Every answer must cite the **exact protocol identifier, version/amendment date, hospital SOP tier** (e.g., Master `ALLTogether1` protocol vs. local UZ Gent / UZA / Saint-Luc SOP override), **section number, and PDF page number**, linking directly to the highlighted source passage.
  - **Strict "Cite or Refuse" Rule**: If the retrieved context does not explicitly contain the answer, or if a conflict between a master protocol and a local hospital SOP cannot be resolved from the documents, the system **must refuse to guess** and explicitly state that the answer was not found in the verified corpus.
- **UC2 — Pediatric Prescriber (`PediDose` / Green Zone)**:
  - Every dosing rule, administration route, and tablet dispersion/tube-flushing instruction must cite its reference formulary (**Belgian BCFI**, **Dutch Kinderformularium**, or institutional pharmacy monograph) alongside the version/retrieval date.
- **UC3 — CINV Management (`AImesis` / Black Zone)**:
  - Emetic risk classifications (HEC / MEC / LEC / Minimal) and antiemetic prophylaxis schedules must cite the governing guideline (**UZA Anti-emetica beleid v2**, **POGO**, or **MASCC/ESMO** pediatric guidelines).
- **UC4 — Belgian Pediatric Clinical Trial ICF (`AutoICF` / Blue Zone)**:
  - All generated Adult, Parent, Adolescent (12–17y), and Child (8–11y) consent/assent drafts across Dutch (`NL`), French (`FR`), and English (`EN`) must enforce a **Verbatim Ethics Lock** on mandatory legal clauses required by the **Belgian Law of 7 May 2004** on experiments on the human person (including **Article 29 no-fault liability insurance** / *foutloze aansprakelijkheid* / *responsabilité sans faute*) and official **FAMHP (FAGG/AFMPS) / EMA** templates, citing the source protocol section for every study-specific insertion.

### 4.4 Defense Against Indirect Prompt Injection, Document Poisoning & Trojan Source

- **Untrusted Document Isolation**: Treat all ingested PDFs, clinical documents, and user inputs as untrusted data, never as executable system instructions. Delimit retrieved RAG chunks clearly and instruct the model to ignore any imperative commands embedded inside source documents (indirect prompt injection).
- **Corpus Integrity Verification**: Verify SHA-256 checksums of reference protocol PDFs and formulary tables before indexing them into vector stores or RAG pipelines to prevent document poisoning.
- **Bidirectional & Invisible Unicode Sanitization (Trojan Source Defense)**:
  - Reject or strip invisible zero-width characters (`U+200B`, `U+200C`, `U+200D`, `U+FEFF`) and bidirectional control characters (`U+202A`–`U+202E`, `U+2066`–`U+2069`) in both source code PRs and ingested clinical text so that hidden text cannot silently invert dosing logic (`<` vs. `>`), decimal separators, or negation ("do *not* administer").

---

## 5. Coordinated Vulnerability Disclosure & SLA

We welcome reports from security researchers, clinicians, pharmacists, and developers regarding **software security vulnerabilities**, **data privacy risks**, or **clinical safety flaws** (such as dosing calculation bugs, citation hallucination vectors, or broken ethics-clause locks).

### How to Report Privately

1. **Email Disclosure (Preferred for All Clinical Safety & Cross-Repo Issues)**:
   - Send a detailed report to **[`secretary@bspho.be`](mailto:secretary@bspho.be)** with the subject line:
     - `[SECURITY VULNERABILITY] <repo-name>` for software/cloud vulnerabilities, or
     - `[CLINICAL SAFETY FLAW] <repo-name>` for dosing math, protocol grounding, or regulatory compliance flaws.
2. **GitHub Private Vulnerability Reporting**:
   - Where enabled on individual `BelgianSPHO` repositories, navigate to the repository's **Security** tab > **Report a vulnerability** to submit an encrypted advisory directly to the maintainers.
   - For non-sensitive clinical logic bugs that do **not** involve exploitable security flaws or PHI/PII, you may also use the [Clinical Safety Review Issue Template](.github/ISSUE_TEMPLATE/clinical_safety_review.yml).

### What to Include in Your Report

- Affected repository, branch, and commit SHA or release tag
- Clear description of the technical vulnerability or clinical safety hazard
- Step-by-step reproduction instructions (using **synthetic inputs only**)
- Potential clinical or security impact (e.g., *unit conversion error for patients < 10 kg*, *bypass of verbatim Article 29 clause check*, *unauthenticated endpoint*)
- Suggested remediation or patch, if available

### Response Targets (SLA)

| Milestone | Active Hackathon / Live Event SLA | Standard Open-Source SLA |
| :--- | :--- | :--- |
| **Initial Acknowledgment** | **Within 24 hours** (typically `< 1 hour` via floor desk) | **Within 72 hours** |
| **Triage & Severity Assessment** | **Within 4 hours** (jointly with Zone Clinical Lead & Google Cloud CE) | **Within 5 business days** |
| **Mitigation / Patch or Deprecation** | **Before final demo / clinical review** | **Within 14–30 days** depending on complexity |

Please practice **Coordinated Vulnerability Disclosure**: allow the `BelgianSPHO` maintainers and clinical leads time to verify and remediate the issue before disclosing it publicly.
