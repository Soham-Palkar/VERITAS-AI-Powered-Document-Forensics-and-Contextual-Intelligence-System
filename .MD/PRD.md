# VERITAS
## Product Requirements Document (PRD)

**Project:** AI-Powered Document Forensics and Contextual Intelligence System  
**Version:** 1.0  
**Date:** 6 November 2026  
**Development model:** Solo developer  
**Target deadline:** 7 November 2026  
**Architecture:** Open-source, CPU-first, evidence-driven

---

# 1. Product Overview

VERITAS is an AI-powered document forensics and contextual intelligence platform designed to analyze digital and scanned documents, identify suspicious modifications, detect contextual inconsistencies, and generate evidence-backed investigation reports.

Unlike conventional OCR-based systems that primarily extract text and validate individual fields, VERITAS combines:

- Optical Character Recognition (OCR)
- Document structure understanding
- Computer vision and image forensics
- Contextual information verification
- Cross-document correlation
- Evidence mapping and traceability
- Explainable investigation reporting

The system will analyze multiple related documents within a single investigation and identify discrepancies that may not be visible when documents are examined independently.

**Core principle:** Every finding must be supported by evidence from an actual uploaded document and must be traceable to its original source location.

# 2. Problem Statement

Financial institutions and enterprises process large volumes of documents, including:

- Application forms
- Identity proofs
- Bank statements
- Salary slips
- Employment letters
- Transaction requests
- Declarations
- Supporting documents

Traditional document-processing systems rely heavily on OCR and predefined validation rules.

However, text extraction alone cannot establish whether information is authentic, consistent, or reliable.

Documents may contain:

- Overwritten fields
- Suspicious image modifications
- Inconsistent fonts and spacing
- Misplaced signatures
- Conflicting information
- Altered amounts or dates
- Discrepancies across related documents

VERITAS aims to address these limitations through contextual and evidence-driven document investigation.

# 3. Product Objectives

1. Extract structured information from scanned and digital documents.
2. Identify suspicious visual characteristics and potential alterations.
3. Understand relationships between extracted fields.
4. Compare information across multiple related documents.
5. Identify contextual inconsistencies.
6. Associate each finding with original document evidence.
7. Generate explainable investigation reports.
8. Maintain traceability throughout the investigation process.

# 4. Target Users

- Financial institutions
- Banking document verification teams
- Insurance companies
- Enterprise compliance teams
- Fraud investigation teams
- Document verification professionals

# 5. Scope

## 5.1 MVP – Mandatory Features

The following capabilities are required by the hackathon problem statement.

### Module 1: Document Ingestion

- Upload PDF documents.
- Upload JPG, JPEG and PNG images.
- Support multiple documents in one investigation.
- Generate unique investigation and document IDs.
- Validate file formats and sizes.
- Preserve original uploaded documents.
- Maintain document source references.

### Module 2: Document Classification

- Identify document categories.
- Identify document type using extracted text and document characteristics.
- Support common financial and identity documents.
- Record classification confidence.
- Allow uncertain classifications to be marked for manual review.

Classification must not be presented as reliable when the model is uncertain.

### Module 3: OCR and Information Extraction

- Extract printed text from documents.
- Process scanned PDFs through image rendering.
- Extract relevant fields.
- Identify names, dates, amounts, addresses and identifiers.
- Extract tables where supported.
- Store field-level confidence.
- Preserve page numbers and text coordinates.
- Support manual inspection of extracted information.

Handwriting recognition is an optional extension.

### Module 4: Document Structure Understanding

- Identify document pages and sections.
- Identify field relationships.
- Organize extracted information into structured JSON.
- Detect missing fields.
- Detect duplicated fields.
- Preserve references to original page locations.

### Module 5: Visual Forensic Analysis

Use actual image processing to examine:

- Font and text-region characteristics.
- Alignment and spacing inconsistencies.
- Localized image irregularities.
- Image insertion or replacement indicators.
- Compression inconsistencies.
- Potentially suspicious regions.

Generate visual evidence overlays for detected regions.

**Important:** A visual irregularity is an investigative indicator, not definitive proof of document forgery.

### Module 6: Contextual Verification

Check consistency between fields within a document.

Examples:

- Issue date versus expiry date.
- Subtotal versus total amount.
- Declared age versus date of birth.
- Missing or conflicting information.
- Invalid date relationships.

### Module 7: Cross-Document Correlation

Compare related documents within one investigation.

Examples:

- Applicant name across identity proof and application form.
- Salary across salary slip and employment letter.
- Address across identity proof and application.
- Account-related information across supporting records.

The system must identify:

- Matching fields.
- Conflicting fields.
- Missing information.
- Potentially duplicated information.
- Supporting source documents.

### Module 8: Evidence Mapping

Every anomaly must include:

- Anomaly ID.
- Anomaly category.
- Source document ID.
- Page number.
- Bounding box where available.
- Original extracted value.
- Compared value where applicable.
- Explanation.
- Confidence or evidence strength.
- Observation status.

The user must be able to navigate from an anomaly to the original document page.

### Module 9: Investigation Dossier

Generate a downloadable PDF containing:

1. Investigation overview.
2. Document overview.
3. Extracted information.
4. Contextual analysis.
5. Cross-document discrepancies.
6. Visual forensic findings.
7. Supporting evidence.
8. Confidence and observation status.
9. Investigation summary.
10. Areas requiring further verification.
11. System limitations.

### Module 10: Audit Trail

Record:

- Investigation creation.
- Document uploads.
- Processing activities.
- Extraction status.
- Analysis completion.
- Findings generated.
- Report generation.
- Processing failures.

The audit trail must preserve the association between original documents and generated findings.

# 6. Advanced Features and Proposed Novelty

These are proposed differentiators, not mandatory requirements.

## 6.1 Evidence Relationship Graph

Create a visual graph connecting:

- Investigations.
- Documents.
- Extracted entities.
- Conflicting fields.
- Anomalies.
- Evidence references.

Example:

Application Form → Applicant Name → Identity Proof → Matching Result.

Salary Slip → Monthly Salary → Employment Letter → Conflicting Result.

Every relationship must originate from actual extracted data.

## 6.2 Visual Forensic Heatmap

Create an overlay showing regions identified by actual image-processing methods.

The overlay must display:

- Original document image.
- Highlighted suspicious region.
- Detection method.
- Evidence details.
- Explanation.

## 6.3 Evidence-First AI Explanation

Provide explanations grounded in the actual findings.

For example:

"Monthly salary extracted from Document A differs from the monthly salary extracted from Document B. Both values and their source locations are available for inspection."

Do not generate unsupported explanations or treat discrepancies as confirmed fraud.

## 6.4 Investigation Confidence Breakdown

Separate confidence into:

- OCR confidence.
- Field extraction confidence.
- Visual detection confidence.
- Contextual comparison result.
- Overall investigation evidence strength.

Do not combine unrelated confidence values into an arbitrary fraud probability.

# 7. User Journey

1. User opens VERITAS.
2. User creates a new investigation.
3. User uploads multiple documents.
4. System validates and stores document references.
5. System classifies document types.
6. OCR extracts information.
7. Extracted fields are structured.
8. Visual forensic analysis examines document images.
9. Contextual verification checks individual documents.
10. Cross-document correlation compares related information.
11. Evidence mapping associates findings with original pages.
12. User reviews findings.
13. System generates the investigation dossier.

# 8. Functional Requirements

| ID | Requirement | Priority |
|---|---|---|
| FR-01 | Multi-document upload | Critical |
| FR-02 | PDF and image support | Critical |
| FR-03 | OCR extraction | Critical |
| FR-04 | Structured field extraction | Critical |
| FR-05 | Document classification | High |
| FR-06 | Document structure understanding | High |
| FR-07 | Visual anomaly detection | Critical |
| FR-08 | Contextual verification | Critical |
| FR-09 | Cross-document comparison | Critical |
| FR-10 | Evidence mapping | Critical |
| FR-11 | Investigation dossier | Critical |
| FR-12 | Audit trail | High |

# 9. Non-Functional Requirements

### Performance
- Process documents asynchronously where necessary.
- Avoid loading unnecessarily large documents entirely into memory.
- Provide meaningful processing states.
- Handle processing failures gracefully.

### Reliability
- Preserve original document references.
- Never replace missing analysis results with fabricated findings.
- Distinguish processing failures from successful analysis.
- Preserve field-level provenance.

### Security
- Validate uploaded files.
- Restrict supported formats.
- Enforce upload-size limits.
- Prevent unauthorized access to investigations.
- Avoid exposing sensitive information in logs.
- Use environment variables for secrets.
- Delete temporary files when processing completes.

### Portability
- Support CPU-only deployment.
- Avoid mandatory GPU dependencies.
- Keep inference modules independent of the frontend.
- Use open-source software and appropriately licensed models.

# 10. Technology Constraints

- No paid AI API dependency.
- No proprietary OCR dependency.
- No fabricated or simulated anomaly detection.
- No mock forensic evidence.
- No requirement for a cloud GPU.
- No Docker or Kubernetes requirement.
- No training of a custom deep-learning model within the initial deadline.

# 11. MVP Acceptance Criteria

The MVP will be considered demonstrable when:

1. A user can upload multiple real documents.
2. The system extracts information from supported documents.
3. Extracted information is structured.
4. Document fields retain their source locations.
5. Actual visual analysis runs on document images.
6. Actual inconsistencies are identified.
7. Cross-document comparison works.
8. Findings can be traced to original documents.
9. Suspicious regions can be inspected visually.
10. An investigation dossier can be generated.
11. Processing failures and unsupported scenarios are reported honestly.

# 12. Out of Scope for Initial MVP

- Universal handwriting recognition.
- Definitive signature forgery detection.
- Universal detection of sophisticated image manipulation.
- Blockchain-based evidence preservation.
- Large-scale enterprise deployment.
- Custom model training.
- Automated fraud approval or rejection.
- Production-grade multi-tenant access management.

# 13. Ethics and Safety

- Use only authorized documents.
- Use synthetic or publicly licensed sample documents for demonstrations.
- Do not process real customer information without authorization.
- Do not equate inconsistencies with confirmed fraud.
- Preserve human oversight.
- Maintain source traceability.
- Clearly communicate limitations and uncertainty.

# 14. Hackathon Demonstration Plan

Demonstrate the following using genuine sample documents:

1. Upload two or more related documents.
2. Show actual OCR output.
3. Show structured extracted fields.
4. Show a genuine cross-document discrepancy.
5. Demonstrate a real visual forensic finding, if detected.
6. Open the original document page.
7. Highlight the associated evidence.
8. Explain the finding.
9. Generate the investigation dossier.
10. Show the audit trail.

Do not prepare a demonstration that depends on hardcoded findings.

# 15. Success Criteria

VERITAS succeeds when it demonstrates that document processing can go beyond text extraction and become an intelligent, contextual, evidence-driven investigation process.

**Primary success measure:** Every reported finding is supported by actual source evidence, is explainable, and can be independently inspected by the user.

---

**Document status:** Development specification  
**Source:** Innovation Hackathon – PS1.pdf  
**Implementation status:** Planned; capabilities must be verified through actual testing.