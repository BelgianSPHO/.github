# `BelgianSPHO/.github` — Organization Profile, Clinical AI Safety Policies & Shared Workflows

[![Organization](https://img.shields.io/badge/GitHub%20Org-BelgianSPHO-0284c7?style=flat-square)](https://github.com/BelgianSPHO)
[![Website](https://img.shields.io/badge/BSPHO-bspho.be-0f172a?style=flat-square)](https://bspho.be/)
[![CI Hygiene](https://img.shields.io/badge/Workflow-Reusable%20CI%20Hygiene-16a34a?style=flat-square)](.github/workflows/ci-hygiene.yml)
[![License](https://img.shields.io/badge/License-Apache%202.0-2563eb?style=flat-square)](LICENSE)

Welcome to **`BelgianSPHO/.github`**, the central organization-wide configuration and governance repository for the **Belgian Society of Paediatric Haematology and Oncology (BSPHO)** ([https://bspho.be/](https://bspho.be/)).

This repository serves as the **single source of truth** for:
1. **The Public Organization Profile** rendered at [`https://github.com/BelgianSPHO`](https://github.com/BelgianSPHO) (`profile/README.md`).
2. **Default Community Health & Governance Files** automatically inherited by every repository in the `BelgianSPHO` organization (`CODE_OF_CONDUCT.md`, `CONTRIBUTING.md`, `GOVERNANCE.md`, `SECURITY.md`, `SUPPORT.md`).
3. **Clinical AI Safety, Privacy & Evaluation Integrity Standards** governing the **Hacking4Good / Solve with Google × BSPHO Pediatric Oncology Hackathon (2026)** and ongoing bedside clinical AI initiatives (`UC1`–`UC4`).
4. **Standardized Issue Templates, Pull Request Checklists, and Reusable CI Guardrails** (`.github/ISSUE_TEMPLATE/`, `.github/PULL_REQUEST_TEMPLATE.md`, `.github/workflows/ci-hygiene.yml`).

---

## 📬 Hackathon Onboarding & Repository Access Notice

> **If you have any issues with your repository or need to make sure your entire team/table has access, please contact [secretary@bspho.be](mailto:secretary@bspho.be).**
>
> For detailed onboarding steps, repository permissions troubleshooting, and clinical mentor escalation paths, see [**`BSPHO contact.md`**](BSPHO%20contact.md) and [**`SUPPORT.md`**](SUPPORT.md).

---

## Bedside Clinical Missions Overview (`UC1`–`UC4`)

All repositories across `BelgianSPHO` support or extend one of our four clinician-led pediatric hematology-oncology missions:

| Use Case | Codename | Zone | Summary | Clinical Leads / Standards |
| :--- | :--- | :--- | :--- | :--- |
| **UC1** | **`OncoProtocol`** | **Red Zone** 🔴 | Clinical protocol lookup, version/amendment conflict detection (e.g., `ALLTogether1`), and eligibility validation across complex pediatric oncology trial protocols. | Dr. Ruben Van Paemel (UZ Gent) & Dr. Gabriel Levy (Saint-Luc Brussels) |
| **UC2** | **`PediDose`** | **Green Zone** 🟢 | BSA/weight-based pediatric oncology chemotherapy dosing decision support, toxicity modification rules, and nurse-ready verification sheets. | Prof. Dr. Bram De Wilde & Sofie Moreels (UZ Gent) |
| **UC3** | **`AImesis`** | **Black Zone** ⚫ | Chemotherapy-Induced Nausea and Vomiting (CINV) guideline-driven management for clinicians, nurses, and families. | UZA v2, POGO & MASCC Guidelines; Belgian Formulary Resources |
| **UC4** | **`AutoICF`** | **Blue Zone** 🔵 | Automated drafting and compliance verification of Belgian pediatric Informed Consent & Age-Appropriate Assent Forms in **NL / FR / EN**. | Belgian Law of 7 May 2004 (Art. 29 no-fault liability insurance) & FAMHP/EMA templates |

---

## Repository Directory Tree & Documentation Index

```text
BelgianSPHO/.github/
├── README.md                                     # This file: repo architecture & usage guide
├── BSPHO contact.md                              # Direct hackathon & repository access contact card
├── CODE_OF_CONDUCT.md                            # Interdisciplinary behavioral & clinical ethics standards
├── CONTRIBUTING.md                               # Contribution workflow, safety rules & rubric guide
├── GOVERNANCE.md                                 # Clinical stewardship, roles & repository lifecycle
├── SECURITY.md                                   # Secret hygiene, zero-PHI policy & incident reporting
├── SUPPORT.md                                    # Team onboarding, access requests & FAQ
├── CITATION.cff                                  # Machine-readable citation metadata (CFF 1.2.0)
├── LICENSE                                       # Apache License 2.0 (with clinical disclaimers)
├── profile/
│   └── README.md                                 # Public landing page rendered on github.com/BelgianSPHO
└── .github/
    ├── PULL_REQUEST_TEMPLATE.md                  # Default PR template with Clinical AI Safety Checklist
    ├── ISSUE_TEMPLATE/
    │   ├── config.yml                            # Issue chooser config & support contact links
    │   ├── clinical_safety_or_guideline_gap.yml  # Report dosing, protocol, CINV or ICF compliance gaps
    │   ├── bug_report.yml                        # Report technical bugs using synthetic reproduction steps
    │   └── feature_or_use_case_proposal.yml      # Propose new clinical AI features aligned with UC1-UC4
    └── workflows/
        └── ci-hygiene.yml                        # Reusable CI workflow (secrets, PHI/NISS, bidi/injection scan)
```

### Complete File Index

| File / Path | Purpose |
| :--- | :--- |
| [`profile/README.md`](profile/README.md) | Public organization profile displayed on [`https://github.com/BelgianSPHO`](https://github.com/BelgianSPHO), introducing BSPHO's mission, the four clinical use cases (`UC1`–`UC4`), safety pillars, and the 100-point hackathon evaluation rubric. |
| [`BSPHO contact.md`](BSPHO%20contact.md) | Quick-reference contact card for repository access and team/table onboarding via [`secretary@bspho.be`](mailto:secretary@bspho.be). |
| [`SUPPORT.md`](SUPPORT.md) | Comprehensive support guide covering repository access requests, clinical mentor consultation, and technical troubleshooting. |
| [`CONTRIBUTING.md`](CONTRIBUTING.md) | Developer and clinician contribution guide covering branch/PR workflows, synthetic data rules, human-in-the-loop labeling, and evaluation integrity. |
| [`SECURITY.md`](SECURITY.md) | Security and privacy policy detailing zero-PHI rules, credential hygiene, prompt-injection prohibitions, and emergency disclosure procedures. |
| [`CODE_OF_CONDUCT.md`](CODE_OF_CONDUCT.md) | Contributor Covenant-aligned Code of Conduct tailored for collaboration among clinicians, engineers, researchers, and patient advocates. |
| [`GOVERNANCE.md`](GOVERNANCE.md) | Organization governance structure defining BSPHO Executive Board oversight, Clinical Lead sign-off authority, and maintainer responsibilities. |
| [`CITATION.cff`](CITATION.cff) | Standard `CITATION.cff` file enabling researchers and contributors to cite BSPHO open-source clinical AI repositories accurately. |
| [`LICENSE`](LICENSE) | Apache License 2.0 governing open-source software in this repository, paired with explicit clinical and copyright disclaimers below. |
| [`.github/PULL_REQUEST_TEMPLATE.md`](.github/PULL_REQUEST_TEMPLATE.md) | Organization-wide pull request checklist enforcing use-case tagging (`UC1`–`UC4`), zero-PHI/zero-secret verification, and clinician sign-off readiness. |
| [`.github/ISSUE_TEMPLATE/`](.github/ISSUE_TEMPLATE/) | Structured YAML issue forms for clinical safety/guideline discrepancies, technical bug reports, and feature proposals. |
| [`.github/workflows/ci-hygiene.yml`](.github/workflows/ci-hygiene.yml) | Automated and reusable GitHub Actions workflow checking for leaked cloud/API credentials, Belgian National Register numbers (NISS) / PHI markers, and hidden bidirectional Unicode or prompt-injection payloads. |

---

## How Inheritance & Reusable Workflows Work

### 1. Automatic Inheritance of Community Health Files & Templates
By GitHub convention, any public or internal repository under `BelgianSPHO` automatically inherits the files in this `.github` repository **unless** that repository defines its own local override:
* **Policies (`CODE_OF_CONDUCT.md`, `CONTRIBUTING.md`, `GOVERNANCE.md`, `SECURITY.md`, `SUPPORT.md`)**: Automatically linked in the repository sidebar, Community Standards checklist, and PR/Issue composer prompts across all `BelgianSPHO/*` repositories.
* **Issue & Pull Request Templates (`.github/ISSUE_TEMPLATE/*`, `.github/PULL_REQUEST_TEMPLATE.md`)**: Automatically presented whenever a contributor opens a new Issue or Pull Request in any `BelgianSPHO` repository that does not define its own `.github/ISSUE_TEMPLATE/` or `.github/PULL_REQUEST_TEMPLATE.md`.

### 2. Calling the Reusable CI Hygiene Workflow (`ci-hygiene.yml`)
Every `BelgianSPHO` team repository is strongly encouraged to invoke the organization's reusable CI hygiene workflow (`BelgianSPHO/.github/.github/workflows/ci-hygiene.yml@main`) to automatically scan pushes and pull requests for:
* **Accidental Secrets & Cloud Keys** (GCP service account JSON keys, Vertex AI / Gemini tokens, GitHub PATs, private keys, `.env` files).
* **PHI / PII Indicators** (Belgian National Register / *rijksregisternummer* / NISS patterns and patient-identifiable markers).
* **Evaluation Integrity & Anti-Prompt-Injection Checks** (hidden bidirectional/zero-width Unicode characters and adversarial jury-grading strings).

To enable this check in any `BelgianSPHO` repository, create `.github/workflows/ci.yml` in your project repository with the following configuration:

```yaml
name: Clinical & Security Hygiene

on:
  push:
    branches: [main, master]
  pull_request:

permissions:
  contents: read

jobs:
  org-hygiene:
    uses: BelgianSPHO/.github/.github/workflows/ci-hygiene.yml@main
```

---

## Licensing & Clinical Disclaimer

### Open-Source Code License (Apache 2.0)
Unless otherwise noted in a specific repository, all source code, templates, and documentation created within `BelgianSPHO` repositories are licensed under the [**Apache License, Version 2.0**](LICENSE).

### Clinical Trial Protocol & Guideline Copyrights
Clinical trial protocols (such as `ALLTogether1`), hospital formularies, and national/international clinical practice guidelines (including UZA, POGO, MASCC, FAMHP, and EMA reference materials) referenced or parsed by tools in this organization **remain the intellectual property and copyright of their respective academic trial consortia, medical societies, and regulatory authorities**. Inclusion of synthetic excerpts or structured rule representations for research and hackathon prototyping does not transfer copyright of underlying clinical protocols.

### No Medical Warranty & Mandatory Clinician Supervision
> **IMPORTANT CLINICAL DISCLAIMER**: All software, prompts, models, dosing calculators, protocol search indices, CINV pathways, and ICF drafting tools hosted under the `BelgianSPHO` GitHub organization are research and decision-support prototypes provided **"AS IS"**, without warranty of any kind, express or implied.
>
> **Every output is strictly `Advisory Only — Requires Clinician Sign-Off`.** Nothing in any `BelgianSPHO` repository constitutes autonomous medical diagnosis, treatment advice, or pharmaceutical prescribing. Qualified pediatric hematology-oncology clinicians, pharmacists, and ethics committees retain sole responsibility for verifying all calculations, protocol interpretations, and regulatory documents prior to clinical or trial use.
