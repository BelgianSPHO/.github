# Support & Community Help Guide — BelgianSPHO

Welcome to the **Belgian Society of Paediatric Haematology and Oncology (BSPHO)** open-source clinical AI ecosystem (`https://github.com/BelgianSPHO`). This guide explains where and how to get help—whether you are participating in the **Hacking4Good / Solve with Google x BSPHO Pediatric Oncology Hackathon (2026)** or contributing to our long-term clinical decision-support repositories.

> **🔒 Emergency Notice (Accidental PHI/PII or Leaked Credentials)**:
> **NEVER** post real patient data (PHI/PII), Belgian National Register Numbers (*rijksregisternummer* / *NISS*), hospital MRNs, or cloud credentials/keys in a public GitHub issue, discussion, or pull request. If sensitive data or secrets were accidentally exposed, follow the emergency procedure in [`SECURITY.md`](SECURITY.md) and email **[`secretary@bspho.be`](mailto:secretary@bspho.be)** immediately with subject `[URGENT-SECURITY/PHI] <repo-name>`.

---

## 1. Hackathon Team & Table Onboarding / Repository Access

If you have any issues with repository permissions—such as making sure your entire team/table is added to your repository or invited to the `BelgianSPHO` GitHub organization:

1. **Email the BSPHO Secretariat**: Send an email to **[`secretary@bspho.be`](mailto:secretary@bspho.be)** (or flag a Hackathon Floor Coach at the registration/tech desk).
2. **Include in your request**:
   - **Team / Table Name & Number**
   - **Clinical Use Case Track & Zone** (`UC1` Red, `UC2` Green, `UC3` Black, or `UC4` Blue)
   - **Target Repository Name** (if already created)
   - **GitHub Usernames (`@handle`)** of all team members needing write/maintainer access

See [`BSPHO contact.md`](BSPHO%20contact.md) for a quick copy-paste onboarding template.

---

## 2. Clinical Domain Support by Bedside Mission (Use Case Zones)

Each clinical AI mission in `BelgianSPHO` is guided by pediatric hematology-oncology clinicians, oncology nurses, pharmacists, and regulatory specialists. When building or validating clinical logic, consult your zone's clinical mentors and authoritative references:

| Zone | Use Case & Codename | Clinical Scope & Key References | Clinical Leads & Domain Mentors |
| :--- | :--- | :--- | :--- |
| 🔴 **Red Zone** | **UC1 — Protocol Search Assistant (`OncoProtocol`)** | Clinical protocol lookup, version/amendment conflict detection (e.g., `ALLTogether1`), and eligibility validation across complex pediatric oncology trial protocols. | **Dr. Ruben Van Paemel** (UZ Gent)<br>**Dr. Gabriel Levy** (Cliniques universitaires Saint-Luc, Brussels) |
| 🟢 **Green Zone** | **UC2 — Pediatric Prescriber (`PediDose`)** | BSA/weight-based pediatric chemotherapy dosing decision support, age/weight threshold adjustments, organ toxicity modification rules, and nurse-ready verification sheets. | **Prof. Dr. Bram De Wilde** (UZ Gent)<br>**Sofie Moreels** (UZ Gent) |
| ⚫ **Black Zone** | **UC3 — CINV Management (`AImesis`)** | Chemotherapy-Induced Nausea and Vomiting (CINV) antiemetic classification and management for clinicians, nurses, and families grounded in **UZA v2**, **POGO**, and **MASCC** guidelines plus Belgian formulary resources (BCFI/CBIP). | BSPHO Supportive Care & Pediatric Oncology Nursing / Pharmacy Mentors |
| 🔵 **Blue Zone** | **UC4 — Belgian Pediatric Clinical Trial ICF (`AutoICF`)** | Automated drafting and compliance verification of Belgian pediatric Informed Consent & Age-Appropriate Assent Forms in **Dutch (NL)**, **French (FR)**, and **English (EN)** aligned with the **Belgian Law of 7 May 2004** (including mandatory **Art. 29 no-fault liability insurance** clauses) and **FAMHP / EMA** templates. | BSPHO Clinical Trial Coordinators & Ethics/Regulatory Mentors |

---

## 3. Technical & Google Cloud / AI Engineering Support

For architecture, Vertex AI / Gemini ADK agents, evaluation harness (`agents-cli`), or CI/CD questions:

- **On-Site Coaches (During Hackathon Events)**: Reach out to the **Solve with Google / Google Cloud Engineering** floor coaches assigned to your zone.
- **Cloud & Credential Setup**:
  - Authenticate locally via `gcloud auth application-default login` or Workload Identity Federation (OIDC).
  - Never commit service account `.json` keys or `.env` secrets (see [`SECURITY.md`](SECURITY.md)).
- **Clinical AI Guardrail Architecture**:
  - Keep arithmetic and dosing calculations (e.g., Mosteller/Haycock BSA, mg/m² vs. mg/kg rules) in deterministic, unit-tested Python/TypeScript functions—never rely on raw LLM token generation for clinical math.
  - Ensure every UI view and exported document prominently displays `"Advisory Only — Requires Clinician Sign-Off"`.

---

## 4. How to File Effective GitHub Issues

We use structured GitHub Issue Forms across all `BelgianSPHO` repositories (blank issues are disabled to ensure clinical and technical context is captured cleanly):

1. **🐛 [Bug Report](.github/ISSUE_TEMPLATE/bug_report.yml)**:
   - Report reproducible software defects, broken workflows, UI rendering bugs, or pipeline errors using **synthetic test inputs only**.
2. **✨ [Feature Request](.github/ISSUE_TEMPLATE/feature_request.yml)**:
   - Propose clinical workflow enhancements, new protocol parsers, UX improvements for clinicians/nurses/families, or evaluation benchmarks.
3. **🩺 [Clinical Safety & Protocol Accuracy Review](.github/ISSUE_TEMPLATE/clinical_safety_review.yml)**:
   - Dedicated pathway for clinicians, nurses, pharmacists, and trial coordinators to flag protocol version discrepancies, dosing edge cases, CINV guideline updates, Belgian ICF legal requirements, or LLM hallucination risks.

---

## 5. General Organization Contact

- **Organization**: Belgian Society of Paediatric Haematology and Oncology (BSPHO)
- **Website**: [https://bspho.be/](https://bspho.be/)
- **Email**: [`secretary@bspho.be`](mailto:secretary@bspho.be)
- **Related Documents**:
  - [Organization Profile (`profile/README.md`)](profile/README.md)
  - [Quick Onboarding Contact Card (`BSPHO contact.md`)](BSPHO%20contact.md)
  - [Contributing Guide (`CONTRIBUTING.md`)](CONTRIBUTING.md)
  - [Code of Conduct (`CODE_OF_CONDUCT.md`)](CODE_OF_CONDUCT.md)
  - [Governance Model (`GOVERNANCE.md`)](GOVERNANCE.md)
  - [Security & Data Privacy Policy (`SECURITY.md`)](SECURITY.md)
