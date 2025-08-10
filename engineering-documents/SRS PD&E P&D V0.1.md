# Software Requirements Specification (SRS) for Product Design & Engineering

**Project:** Artificial Assessment Intelligence for Educators (AAIE) Platform  
**Version:** 0.1  
**Date:** August 3, 2025  

---

## 1. Introduction

### 1.1 Purpose
This Software Requirements Specification (SRS) outlines the functional and non-functional requirements for the Artificial Assessment Intelligence for Educators (AAIE) system.  

The AAIE platform supports educators in evaluating student submissions by analyzing rubric alignment, AI-generated content, and prompt similarity using Large Language Models (LLMs). It enables educators to submit prompts, student responses, and AI chat logs, and automatically generates structured, rubric-aligned feedback with AI usage classification.  

Phase 1 focuses on a standalone MVP (T2 2025), with future plans for OnTrack integration and enhanced analytics.

This SRS covers two development phases:
- **T2 (MVP):** Implementation of a single evaluation workflow (Scenario 1).
- **Future Scope:** Planned enhancements and extended capabilities for subsequent releases.

---

### 1.2 Scope
The AAIE system will be a web-based application enabling educators to:
- Upload student submissions.
- Classify submissions as **Human**, **AI**, or **Hybrid**.
- Score submissions across defined rubric criteria.
- Generate AI-based improvement suggestions.
- Allow teachers to add final feedback.

**T2 (MVP) Scope:**
- Supports one complete evaluation scenario:  
  *Scenario 1:* A student submits an assignment; the system classifies the content, scores it using a rubric, provides LLM feedback, and allows the teacher to append final comments and show it.

**Future Scope:**
- Multiple submission types.
- Similarity checks.
- Plagiarism detection.
- LMS integration.
- AI bias tracking.
- PDF report generation.
- Multi-model comparison.

---

### 1.3 Definitions, Acronyms, and Abbreviations
- **AAIE:** Academic AI Evaluator  
- **LLM:** Large Language Model  
- **MVP:** Minimum Viable Product  
- **LMS:** Learning Management System  
- **JWT:** JSON Web Token  

---

### 1.4 References
- Requirement Analysis  
- AAIE API Specification  
- AAIE Evaluation  

---

## 2. Overall Description

### 2.1 Product Perspective
The AAIE system is an independent application in T2, using **FastAPI** for backend services and **React.js** for the frontend. In the future, it will integrate with Deakin University’s OnTrack LMS for automatic result management.

### 2.2 Product Functions

**T2 (MVP):**
- Upload and process student submission.
- Classify submission content (**Human**, **AI**, **Hybrid**).
- Apply rubric scoring:
  - Conceptual Understanding
  - Real-World Application
  - Critical Evaluation
  - Academic Writing
- Generate AI feedback with improvement suggestions.
- Allow teacher comments.
- Generate PDF report.

**Future Scope:**
- Multi-scenario evaluation (text, coding, multi-part).
- Similarity and plagiarism detection.
- Automated LMS integration.
- AI bias and hallucination analysis dashboards.
- Multi-model evaluation pipeline.
- Generate PDF report.

### 2.3 User Characteristics
- **Educators** – primary system operators.
- **Administrators** – manage configuration, access control, and monitoring.
- **Students** – indirect stakeholders benefiting from improved feedback.

### 2.4 Constraints
- T2 supports only text-based input.
- Evaluation must complete in ≤ 5 seconds.
- Future Scope integration depends on LMS API availability.

### 2.5 Assumptions and Dependencies
- Internet connectivity is available.
- AI model services are operational.
- Educator accounts are authenticated.

---

## 3. Specific Requirements

### 3.1 Functional Requirements

#### 3.1.1 T2 (MVP) Functional Requirements

| Req ID  | Requirement Description                                                        | Priority |
|---------|--------------------------------------------------------------------------------|----------|
| FR-001  | The system shall allow an educator to upload a student submission in a single request. | High     |
| FR-002  | The system shall classify the submission as Human, AI, or Hybrid.              | High     |
| FR-003  | The system shall generate rubric-based scores for four evaluation criteria.    | High     |
| FR-004  | The system shall generate AI feedback with improvement suggestions.            | High     |
| FR-005  | The system shall allow an educator to enter additional feedback.               | Medium   |

#### 3.1.2 Future Scope Functional Requirements

| Req ID  | Requirement Description                                                        | Priority |
|---------|--------------------------------------------------------------------------------|----------|
| FR-007  | The system shall support evaluation of multiple assessment types.              | High     |
| FR-008  | The system shall perform similarity detection.                                 | High     |
| FR-009  | The system shall flag submissions with ≥40% similarity for resubmission.       | High     |
| FR-010  | The system shall integrate with OnTrack LMS for automated result submission.   | High     |
| FR-011  | The system shall generate AI bias and hallucination analysis reports.          | Medium   |
| FR-012  | The system shall allow comparative evaluation using multiple AI models.        | Medium   |
| FR-006  | The system shall generate a downloadable PDF report containing the full evaluation. | High  |

---

### 3.2 External Interface Requirements

#### 3.2.1 User Interfaces
- **T2:** Single-page Streamlit form for input and evaluation results.
- **Future:** Multi-tab interface for advanced options and analytics.

#### 3.2.2 Hardware Interfaces
- Standard educator device with web browser (no special hardware).

#### 3.2.3 Software Interfaces
- Azure OpenAI API for LLM processing.
- Local database for storing evaluation records.

---

### 3.3 Non-Functional Requirements

#### 3.3.1 T2 (MVP) NFRs

| Req ID   | Requirement Description                               | Priority |
|----------|-------------------------------------------------------|----------|
| NFR-001  | The system shall process each evaluation in ≤ 5 seconds. | High     |
| NFR-002  | The system shall be available with ≥99% uptime.       | High     |
| NFR-003  | The system shall implement JWT authentication for API access. | High |

#### 3.3.2 Future Scope NFRs

| Req ID   | Requirement Description                               | Priority |
|----------|-------------------------------------------------------|----------|
| NFR-004  | The system shall support 10,000 concurrent users.     | High     |
| NFR-005  | The system shall implement role-based access control. | High     |
| NFR-006  | The system shall be compliant with GDPR and academic integrity policies. | High |

---

## 4. Appendices

### Appendix A – T2 Evaluation Criteria
- Conceptual Understanding
- Real-World Application
- Critical Evaluation
- Academic Writing

### Appendix B – AI Classification Categories
- Human
- AI
- Hybrid
