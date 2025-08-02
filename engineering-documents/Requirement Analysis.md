# Requirement Analysis Document

## Project Overview

The **AAIE GenAI Integrated Evaluation System** aims to enhance academic integrity by integrating AI detection and prompt-text similarity analysis into the OnTrack platform. Students must submit both their final work and the AI prompts used. If the similarity between prompts and final submissions is **40% or more**, the submission will require revision and resubmission.

The project spans **three years**, with the current trimester (**T2 2025**) focusing on a standalone MVP with core functionalities. Year 1 will focus on OnTrack integration, followed by advanced analytics and explainability in Years 2 and 3.

---

## Stakeholder Analysis

| Stakeholder        | Needs / Expectations                             | Impact                                          |
|--------------------|--------------------------------------------------|-------------------------------------------------|
| Educators          | Advanced AI detection and prompt-text similarity | Ensures academic integrity and fairness         |
| Students           | Transparent GenAI rules and fair evaluation      | Encourages responsible AI use and fair scoring  |
| OnTrack Team       | Smooth API integration and workflow alignment    | Enhanced platform performance and reliability   |
| AAIE Technical Teams | Backend modules for detection and feedback     | Streamlined cross-pillar collaboration          |
| Researchers        | Access to structured datasets and metrics        | Supports academic research on AI misuse         |

---

## Functional Requirements

| Feature              | Description                                                 |
|----------------------|-------------------------------------------------------------|
| Prompt Submission     | Students must submit AI prompts with their final work       |
| Prompt-Text Similarity| Detects similarity ≥40% and flags for resubmission         |
| AI Usage Detection    | Checks over-reliance on AI-generated content                |
| Feedback System       | Provides rubric-aligned feedback editable by educators      |
| Standalone MVP        | Developed during T2 2025 with all core features             |
| OnTrack Integration   | Planned for Year 1 after MVP testing                        |

---

## Technical Dependencies

| Component        | Description                                                   |
|------------------|---------------------------------------------------------------|
| Frontend         | Streamlit/React for MVP UI development                        |
| Backend          | FastAPI for prompt similarity and AI detection                |
| Similarity Engine| NLP models using cosine similarity or embeddings              |
| Version Control  | GitLab repository with CI/CD pipelines                        |
| OnTrack API      | Planned integration for submission and feedback workflows     |

---

## Constraints & Assumptions

| Category     | Details                                                            |
|--------------|---------------------------------------------------------------------|
| Constraints  | MVP must be delivered as a standalone app this trimester           |
| Constraints  | Similarity threshold fixed at 40% initially                        |
| Assumptions  | Students will upload all GenAI prompts honestly                    |
| Assumptions  | Similarity APIs will remain accessible                             |
| Assumptions  | Educators and students will participate in pilot testing           |

---

## Personas (Educators)

| Persona              | Role                          | Needs / Pain Points                              |
|----------------------|-------------------------------|--------------------------------------------------|
| Dr. Nazia Haque      | Senior Lecturer, Business & Law| Needs reliable AI detection                      |
| Mr. Junyu Yung       | IT Lecturer                   | Needs efficient prompt checks for large cohorts  |
| Ms. Karina Bhatya    | Health Sciences Coordinator   | Needs detailed reports on AI usage and prompts   |

---

## Scenarios (Use Cases)

| Scenario                | Description                                                                 |
|-------------------------|-----------------------------------------------------------------------------|
| Academic Integrity Check| Student uploads work and prompts → similarity check → resubmit if ≥ 40%     |
| Rubric Feedback         | Educator reviews and edits rubric-aligned feedback                          |
| Downloadable Reports    | Educators can download evaluations for record-keeping                       |

---

## Deliverables Summary (T2 2025)

| Deliverable            | Description                                                         |
|------------------------|---------------------------------------------------------------------|
| Standalone MVP App     | Core functionality: prompt submission and AI detection              |
| Rubric Feedback System | Editable rubric-aligned feedback for educators                      |
| API and Backend Modules| FastAPI endpoints for checks and evaluations                        |
| Documentation          | Technical guides, workflow diagrams, and README                     |
| Version Control        | Organized GitLab repo with commits and test reports                 |

---

## Project Plan (Trimester & Year 1)

| Phase           | Activities                                                              |
|------------------|-------------------------------------------------------------------------|
| Trimester 2, 2025| Develop MVP with prompt similarity → Collect feedback from educators    |
| Phase 1 (T2–T3)  | Deploy MVP and refine based on educator/student feedback                |
| Phase 2 (T4)     | Begin OnTrack integration and expand API features                       |
| Phase 3 (T1 2026)| Add explainability, analytics dashboards, and pilot testing             |

---

## 3-Year Plan (Overview)

| Year             | Goals                                                                  |
|------------------|------------------------------------------------------------------------|
| Year 1 (T2 2025–T2 2026) | MVP delivery, OnTrack integration, feedback refinement     |
| Year 2 (T3 2026–T2 2027) | Advanced analytics and educator-facing explainability       |
| Year 3 (T3 2027–T2 2028) | Final deployment, cross-discipline adoption, large-scale evaluation |

---
