# PP-SPEC-051: Proof of Efficacy Mapping to the CSA AI Controls Matrix (AICM)

| Field | Value |
|---|---|
| Status | DRAFT v0.1 |
| Author | Craig Ellrod, Nebulonium, Inc. (dba HACKERverse®) |
| Date | October 8, 2026 |
| License | CC BY 4.0 |
| Maps to | Cloud Security Alliance AI Controls Matrix (AICM) v1.1 (released June 22, 2026) |
| Series | Proof Protocol Framework Mapping Specifications |

---

## 1. Purpose

This specification defines how AI and cloud control objectives in the Cloud Security Alliance (CSA) AI Controls Matrix (AICM) can be bound to Proof Protocol test cases, evidence, and efficacy results.

The upstream source remains authoritative for its own requirements, identifiers, terminology, and guidance. This document defines a **Proof Protocol mapping** and does not supersede, reproduce, modify, or certify conformance to the upstream source.

## 2. Scope

The AICM is a vendor-agnostic control framework for AI systems published by CSA. As of the date of this specification, the current version is **AICM v1.1**, released by CSA on June 22, 2026, superseding AICM v1.0 (announced July 10, 2025). CSA describes AICM v1.1 as containing 247 control objectives across 18 security domains, and as a superset of the CSA Cloud Controls Matrix (CCM) v4.1: the CCM domains are carried forward and AICM adds the Model Security (MDS) domain. The AICM v1.1 release also includes Implementation Guidelines, Auditing Guidelines, the AI-CAIQ questionnaire, and CSA-authored mappings to other frameworks.

AICM supplies external control context that can identify what should be examined or tested. Proof Protocol supplies an independent evidence model for determining what happened during a test and whether a selected control performed as claimed.

Independent witnessing, proof validity, evidence capture, packaging, anchoring, and efficacy semantics are defined elsewhere in the Proof Protocol specification family.

## 3. Core Question

Proof of efficacy asks:

> **Was there a control, and did it work?**

A framework requirement, criterion, principle, or obligation may identify a condition of interest. A product, architecture, policy, process, or safeguard may claim to satisfy or mitigate that condition. Proof Protocol binds the external context, test, control, observed behavior, downstream outcome, and evidence into a result that can be independently examined.

An AICM control objective identifies what a control is expected to achieve. A completed AI-CAIQ response, implementation statement, or assigned ownership role records what a party asserts about that objective. Neither is, by itself, evidence that the control operated or that the protected outcome was achieved. Proof Protocol keeps those assertions separate from empirically tested results.

A Proof Protocol result does **not** by itself establish legal, audit, regulatory, or standards conformance unless the applicable authority separately determines that the evidence is sufficient.

## 4. Metric Definitions

Against a defined corpus or test condition, each applicable empirical case is recorded as **blocked**, **detected**, **missed**, or **INVALID** where those verdicts are meaningful.

Relevant measurements can include containment rate, detection rate, miss rate, false-positive rate, robustness under bypass or failure conditions, version-level results, and **INVALID** when required evidence is incomplete or broken.

Not every upstream requirement is empirical. Governance, documentation, organizational, legal, and procedural requirements MUST NOT be converted into efficacy scores merely because they can be referenced by a proof record.

## 5. Evidence Produced

Mapped tests can produce:

- **Proof records** binding external context, test case, control, system/version, verdict, timestamp, and evidence references;
- **ProofStamp™** trusted timestamps bound to evidence/verdict objects;
- **ProofBundle™** packages containing proof records, metrics, corpus manifests, and environment/context;
- **ProofRegister™** records for issued proof artifacts; and
- corpus and environment manifests identifying the tested conditions.

## 6. Mapping to the CSA AI Controls Matrix (AICM)

Exact upstream identifiers and titles SHOULD be taken from the authoritative AICM version being mapped and recorded in the ProofBundle™ where licensing permits. This specification does not redefine AICM control objectives. Control identifiers use the domain abbreviation and a sequence number (for example, `MDS-01` in the Model Security domain).

| AICM context | Proof Protocol treatment | Evidence |
|---|---|---|
| Domain | Record the AICM domain name and abbreviation as test context. | Requirement metadata |
| Control objective (for example, `MDS-01`) | Bind the control identifier and AICM version to one or more reproducible test cases where the objective is empirically testable. | Proof record; corpus manifest |
| Control specification | Record the asserted control separately from observed behavior. Do not copy the specification text into the proof record. | Control descriptor |
| Control Type pillar | Record the control type as metadata; it does not alter the verdict model. | Requirement metadata |
| Control Applicability and Ownership pillar | Bind the tested party role (for example, Model Provider, Orchestrated Service Provider, Application Provider, AI Customer, or Cloud Service Provider) to the result so shared-responsibility claims are attributable. | Control descriptor; environment descriptor |
| Architectural Relevance and Lifecycle Relevance pillars | Record the architectural layer and lifecycle stage exercised by the test. | Environment descriptor |
| Threat Category pillar | Use as threat context for independently authored test conditions, including negative, bypass, and misuse cases. | Corpus metadata; robustness evidence |
| Control operation | Exercise the defined condition and capture whether the control operated and whether the protected objective was achieved. | Execution evidence; outcome evidence |
| Implementation Guidelines and Auditing Guidelines | Treat as upstream guidance for scoping. Proof Protocol results MAY support an auditor's examination but are not CSA audit outcomes. | ProofBundle |
| AI-CAIQ response | Record as a non-empirical self-assertion. It MUST NOT be scored as efficacy. | Assertion record |
| CSA cross-framework mappings | Treat as CSA-authored context. A Proof Protocol result for an AICM control does not transfer to a mapped framework without its own mapping. | Requirement metadata |
| System/version context | Bind material model, agent, data pipeline, policy, configuration, and environment versions to the result. | Environment descriptor |

ProofBundle™ packages MUST NOT embed AICM control specifications, guideline text, or AI-CAIQ question text unless CSA has granted the necessary permission. Identifiers and AICM version references are sufficient for interoperability.

## 7. Interoperability Rules

1. The authoritative upstream source, edition/version, and applicable identifier SHOULD be recorded.
2. Upstream identifiers and terminology MUST NOT be silently redefined.
3. Proof Protocol verdicts are Proof Protocol results; they are not upstream certifications, audit opinions, legal determinations, or endorsements.
4. A control's presence, configuration, activation, detection, and efficacy are distinct facts.
5. A policy decision, alert, log entry, or control trigger does not by itself establish efficacy when the claim concerns a downstream protected outcome.
6. Target, application, tool, SIEM, vendor, service, resource, or equivalent evidence SHOULD complete the evidence round trip when required to establish the result.
7. Missing required evidence MUST yield **INVALID**, not PASS.
8. Material changes to the tested system, policy, control, environment, mapping, or corpus SHOULD trigger retesting where they can affect the result.
9. Non-empirical requirements MUST remain distinguishable from empirically tested efficacy assertions.

## 8. Framework-Agnostic Architecture

> **Threat, control, audit, and regulatory frameworks are pluggable inputs to Proof Protocol. Proof Protocol is framework-agnostic.**

External frameworks can identify **what to test or examine**. Proof Protocol independently establishes **whether the control worked and what evidence proves that result**.

No external framework is required for Proof Protocol to operate. An implementation MAY use the CSA AI Controls Matrix (AICM), another recognized framework, a proprietary threat model, several frameworks simultaneously, or no external framework when the test condition is otherwise sufficiently defined.

Adding, replacing, muting, or removing a framework mapping does not alter the Proof Protocol architecture, evidence model, Proof of Efficacy determination, ProofBundle™, ProofStamp™, ProofRegister™, or independent corroboration requirements.

A framework mapping therefore establishes **interoperability**, not architectural dependency.

## 9. Relationship to Proof Protocol

This mapping is part of the Proof Protocol specification family maintained by Nebulonium, Inc.

The relationship is intentionally asymmetric:

> **The CSA AI Controls Matrix supplies AI control objectives and ownership context. Proof Protocol supplies the evidence model for independently examining whether a selected control performed as claimed.**

No affiliation, endorsement, certification, audit opinion, or sponsorship by the Cloud Security Alliance (CSA) is implied.

## 10. Source Framework, Attribution, and License

The CSA AI Controls Matrix (AICM) is external work owned and published by the Cloud Security Alliance. AICM names, domain names, identifiers, control specifications, guidelines, questionnaires, trademarks, and expressive content remain subject to CSA's applicable terms.

CSA makes the AICM freely available for download from its website. CSA's website Terms and Conditions (https://cloudsecurityalliance.org/legal/website-terms-and-conditions) state that CSA research publications may not be modified or translated without CSA's prior written consent, that copies must retain CSA's copyright notice and references to CSA, that commercial exploitation of site material requires a license from CSA, and that CSA trademarks may not be used in connection with products or services that are not CSA's without prior written consent. CSA's published terms for its Cloud Controls Matrix v4 (https://cloudsecurityalliance.org/ccm-intellectual-property-rights-agreement) limit use to "personal, informational, non-commercial use", state that the material "may not be modified or altered in any way" and "may not be redistributed", and permit quotation under fair use with attribution to CSA. An AICM-specific license notice could not be confirmed from a public CSA page at the time of drafting; the notice accompanying the AICM v1.1 download SHOULD be checked at the authoritative source before any reuse beyond referencing identifiers.

This specification therefore references AICM identifiers, domain names, pillar names, and structural terms only. It does not reproduce, translate, or redistribute AICM content, and it does not use CSA logos. Requests for uses not covered by CSA's terms SHOULD be directed to CSA.

This Proof Protocol mapping is independently authored and Licensed under the Greater Good Commercial License 1.0 (see LICENSE.md); text CC BY-ND 4.0 under its Part S. Original inventor: Craig Thomas Ellrod (ORCID 0009-0004-1058-7666).

Where upstream material is copyrighted or access-controlled, contributors MUST NOT copy protected normative text into this repository merely to make the mapping self-contained. Reference identifiers and independently authored descriptions should be used where legally appropriate.

### Required attribution

No AICM-specific attribution text could be confirmed from a public CSA page at the time of drafting. The following recommended notice is used:

> Cloud Security Alliance AI Controls Matrix (AICM) v1.1 (https://cloudsecurityalliance.org/artifacts/ai-controls-matrix-v1-1). © 2009–2026 Cloud Security Alliance. All rights reserved. This repository references AICM domain names, control identifiers, and structural terms only and does not reproduce, modify, or redistribute AICM content.

Recommended citation: Cloud Security Alliance, *AI Controls Matrix (AICM) v1.1*, released June 22, 2026, https://cloudsecurityalliance.org/artifacts/ai-controls-matrix-v1-1.

If any portion of AICM text is quoted under fair use, it MUST be attributed to the Cloud Security Alliance AI Controls Matrix and the applicable version, consistent with CSA's terms. This specification reproduces only identifiers, names, and structural terms, so no CSA content is redistributed, modified, or reLicensed under the Greater Good Commercial License 1.0 (see LICENSE.md); text CC BY-ND 4.0 under its Part S. Original inventor: Craig Thomas Ellrod (ORCID 0009-0004-1058-7666).

## 11. Versioning

This mapping is versioned independently of the CSA AI Controls Matrix (AICM). Material upstream changes, including a new AICM release or a change to the underlying CCM version, SHOULD trigger a mapping review and, where necessary, a new version identifying the AICM revision mapped.

---

*Proof Protocol · proofprotocol.io · CC BY 4.0*
