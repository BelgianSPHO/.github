# Open-Source & Clinical Governance Model (`BelgianSPHO`)

This document defines the organizational governance, decision-making roles, clinical safety authority, repository lifecycle, and intellectual property framework for the **Belgian Society of Paediatric Haematology and Oncology (`BelgianSPHO`)** GitHub organization (`https://github.com/BelgianSPHO`).

---

## 1. Mission & Institutional Context

The **Belgian Society of Paediatric Haematology and Oncology (BSPHO)** ([https://bspho.be/](https://bspho.be/)) unites pediatric hematology and oncology centers across Belgium to advance clinical care, collaborative research, and education for children and adolescents with cancer and blood disorders.

Launched through the **Hacking4Good / Solve with Google x BSPHO Pediatric Oncology Hackathon (2026)**, the `BelgianSPHO` open-source ecosystem develops safe, clinician-in-the-loop AI and software tools across four flagship clinical missions:

1. **UC1 — Protocol Search Assistant (`OncoProtocol` / Red Zone)** — Leads: Dr. Ruben Van Paemel (UZ Gent) & Dr. Gabriel Levy (Cliniques Universitaires Saint-Luc Brussels).
2. **UC2 — Pediatric Prescriber (`PediDose` / Green Zone)** — Leads: Prof. Dr. Bram De Wilde & Sofie Moreels (UZ Gent).
3. **UC3 — CINV Management (`AImesis` / Black Zone)** — Grounded in UZA v2 / POGO / MASCC clinical practice guidelines & Belgian formulary resources.
4. **UC4 — Belgian Pediatric Clinical Trial ICF (`AutoICF` / Blue Zone)** — Grounded in the Belgian Law of 7 May 2004 (Art. 29 no-fault liability insurance) & FAMHP/EMA templates in NL/FR/EN.

---

## 2. Governance Roles & Decision-Making Authority

Governance within `BelgianSPHO` balances open-source engineering agility with rigorous clinical safety oversight.

### A. BSPHO Board & Secretariat (`secretary@bspho.be`)
* **Role**: Institutional stewardship, legal and ethical oversight, inter-hospital coordination, and GitHub organization administration.
* **Responsibilities**:
  * Chartered authority over the `BelgianSPHO` GitHub organization, brand, and official public communications.
  * Final escalation authority for [Code of Conduct](./CODE_OF_CONDUCT.md) enforcement, data privacy incidents, and institutional partnerships.
  * Approval of any repository's transition into multi-center Belgian clinical validation or regulatory study under hospital Ethics Committees (*Ethisch Comité* / *Comité d'Éthique*) and the Federal Agency for Medicines and Health Products (FAMHP / FAGG / AFMPS).
* **Contact**: [`secretary@bspho.be`](mailto:secretary@bspho.be) | [https://bspho.be/](https://bspho.be/)

### B. Clinical Use Case Leads (UC1–UC4)
* **Role**: Domain authority over clinical requirements, medical protocol accuracy, pediatric dosing rules, supportive care algorithms, informed consent regulations, and patient safety.
* **Designated Leads & Domain Scope**:
  * **UC1 (`OncoProtocol` / Red Zone)**: Dr. Ruben Van Paemel (UZ Gent) & Dr. Gabriel Levy (Saint-Luc Brussels) — Oncology treatment protocol navigation, eligibility criteria, toxicity grading, and source provenance.
  * **UC2 (`PediDose` / Green Zone)**: Prof. Dr. Bram De Wilde & Sofie Moreels (UZ Gent) — Pediatric anthropometric calculations (BSA/weight), chemotherapy and supportive drug dosing, capping rules, and pharmacy verification workflows.
  * **UC3 (`AImesis` / Black Zone)**: Designated BSPHO Supportive Care & Oncology Pharmacy Leads — Chemotherapy-induced nausea and vomiting (CINV) risk classification, UZA v2 / POGO / MASCC prophylaxis and rescue regimens, and Belgian formulary (BCFI/CBIP) alignment.
  * **UC4 (`AutoICF` / Blue Zone)**: Designated BSPHO Clinical Trial & Ethics Leads — Belgian Law of 7 May 2004 (Article 29 no-fault liability insurance), FAMHP/EMA pediatric informed consent/assent templates, and trilingual (NL/FR/EN) age-appropriate communication.
* **Clinical Safety Veto Power**:
  > **Clinical Use Case Leads hold absolute, non-overridable Clinical Safety Veto Power.** Any Clinical Use Case Lead may block, revert, or suspend any feature, dosing calculation, model prompt, retrieval pipeline, UI element, or release that poses a plausible risk of clinical misinterpretation, calculation error, or patient harm. A Clinical Safety Veto cannot be overridden by Technical Maintainers or community vote.

### C. Technical Maintainers & Architecture Coaches
* **Role**: Engineering stewardship, software architecture, cloud security, CI/CD guardrails, and reproducibility.
* **Responsibilities**:
  * Reviewing Pull Requests for code quality, deterministic test coverage, dependency security, and adherence to `.github` templates and workflows.
  * Enforcing technical guardrails: **Zero PHI/PII**, **Zero Secrets/Credentials**, mandatory `"Advisory Only — Requires Clinician Sign-Off"` UI/API framing, and anti-prompt-injection protections.
  * Managing branch protection rules, automated test suites, and release tagging in coordination with Clinical Use Case Leads.

### D. Hackathon Teams & Open-Source Contributors
* **Role**: Interdisciplinary innovators (engineers, data scientists, clinicians, nurses, pharmacists, students, and advocates) building features, reporting issues, authoring tests, and improving documentation.
* **Responsibilities**:
  * Adhering to [CONTRIBUTING.md](./CONTRIBUTING.md) and [CODE_OF_CONDUCT.md](./CODE_OF_CONDUCT.md).
  * Participating transparently in peer review and evaluation benchmarks without adversarial gaming or prompt injection.
  * Escalating discovered clinical edge cases via the Clinical Safety Review issue template (`clinical_safety_review.yml`).

---

## 3. Repository Lifecycle & Clinical Maturity Stages

Every repository in `BelgianSPHO` carries a clearly documented maturity stage in its `README.md` so clinicians and external users immediately understand its validation status:

### Stage 1: Hackathon Sandbox / Research Prototype
* **Scope**: Rapid prototyping during the **Hacking4Good / Solve with Google x BSPHO Hackathon (2026)** and early community sprints.
* **Data Policy**: Strictly **100% synthetic/simulated patient data** and publicly accessible protocol/guideline extracts.
* **Clinical Use**: **Strictly prohibited from use in live patient care.** Must display prominent `"HACKATHON PROTOTYPE — ADVISORY ONLY — NOT FOR CLINICAL USE"` banners.

### Stage 2: Clinical & Technical Audit (Pre-Pilot Hardening)
* **Scope**: Post-hackathon consolidation selected by Clinical Use Case Leads and Technical Maintainers for deeper verification.
* **Requirements**:
  * Comprehensive golden test suite co-authored by pediatric oncologists and hospital pharmacists (100% pass rate on deterministic dosing, edge-case weight bands, and citation grounding).
  * Formal security, privacy (GDPR / Belgian Health Data Authority), and adversarial red-teaming audit.
  * Written sign-off from the relevant Clinical Use Case Leads (UC1–UC4) and Technical Maintainers.

### Stage 3: Validated Clinical Decision-Support Pilot
* **Scope**: Controlled institutional or multi-center clinical pilot under hospital governance.
* **Requirements**:
  * Formal classification and compliance assessment under **EU Medical Device Regulation (MDR 2017/745)** / **In Vitro Diagnostic Regulation (IVDR 2017/746)**, the **EU AI Act** (High-Risk AI system provisions where applicable), and **Belgian FAMHP (FAGG/AFMPS)** guidance.
  * Institutional **Ethics Committee (*Ethisch Comité* / *Comité d'Éthique*)** approval and Hospital Data Protection Officer (DPO) sign-off.
  * Continuous post-deployment clinical monitoring, audit logging, and mandatory human-in-the-loop clinician sign-off (`"Advisory Only — Requires Clinician Sign-Off"`).

---

## 4. Licensing & Intellectual Property Clarification

To foster open scientific collaboration while respecting medical copyright and clinical consortium governance, `BelgianSPHO` enforces a strict separation between **open-source software code** and **clinical reference protocols**:

1. **Open-Source Software & Original Repository Assets (`Apache-2.0`)**:
   * Unless otherwise noted in a specific repository, all original source code, software architectures, UI components, synthetic patient generators, evaluation scripts, and documentation templates authored within `BelgianSPHO` are licensed under the **[Apache License, Version 2.0](./LICENSE)**.
2. **Underlying Clinical Protocols, Guidelines & Formularies (Third-Party IP Retained)**:
   * **Clinical trial protocols** (such as `ALLTogether1` and other international pediatric oncology study protocols), **clinical practice guidelines** (such as **MASCC**, **POGO**, and **UZA v2** CINV guidelines), **national pharmacotherapeutic references** (such as **BCFI / CBIP** Belgian formulary data), and **regulatory templates** (**FAMHP / EMA** and statutory provisions of the Belgian Law of 7 May 2004) **remain the exclusive intellectual property and copyright of their respective clinical consortia, academic authors, medical societies, and regulatory authorities**.
   * Inclusion of short public extracts, structural schemas, or citation pointers within `BelgianSPHO` repositories is solely for research, educational benchmarking, and clinical decision-support prototyping, and does not re-license the underlying medical protocols under Apache-2.0.
   * Users deploying `BelgianSPHO` software in institutional settings are responsible for ensuring their hospital holds appropriate consortium membership and authorization to access full-text clinical trial protocols.

---

## 5. Amendments & Contact

Changes to this governance model require a Pull Request approved by the **BSPHO Secretariat** and a majority of active **Clinical Use Case Leads**.

* **Organization**: Belgian Society of Paediatric Haematology and Oncology (BSPHO)
* **Website**: [https://bspho.be/](https://bspho.be/)
* **Secretariat Contact**: [`secretary@bspho.be`](mailto:secretary@bspho.be)
