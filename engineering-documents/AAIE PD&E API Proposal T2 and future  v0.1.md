# AAIE – API Specification

**Prepared by:** Kasfi Ahamed  
**Date:** Trimester 2, 2025  
**Document Version:** v1.0 – T2 & Future Scope  

---

## 1. Overview

The AAIE API Specification provides APIs to evaluate academic work for AI content, rubric scoring, and prompt similarity.

This document defines all required APIs for:

- **LLM Team** – APIs to run AI classification, scoring, rubric evaluation, similarity detection, and feedback generation.
- **Frontend ↔ Backend (Product Engineering)** – APIs for user authentication, submission handling, teacher review, file management, and policy control.

---

## 2. Phase 1 – T2 (Current MVP) APIs

### LLM Team

#### `POST /llm/classify`
- **Purpose:** Decide Human / AI / Hybrid from `{prompt_text, student_submission, chat_log}`; return `{classification, confidence}`.

#### `POST /llm/rubric-score`
- **Purpose:** Score Structure, Clarity, Relevance, Academic Writing using T2 rubric; return labels (Excellent/Good/…).

#### `POST /llm/generate-feedback`
- **Purpose:** Produce student-facing, actionable feedback tied to the prompt; return `{llm_feedback}`.

---

### Frontend ↔ Backend (Product Engineering)

#### **Auth**
- `POST /api/auth/register` – Create teacher/admin accounts with role.
- `POST /api/auth/login` – Authenticate; returns `{token, role}`.
- `GET /api/auth/me` – Get current user details and role for RBAC.

#### **Assignments & Submissions (Teacher/Admin only)**
- `POST /api/assignments` – Create a new assignment for evaluation.
- `GET /api/assignments` – List all assignments.
- `PUT /api/assignments/{assignmentId}` – Update assignment details.
- `DELETE /api/assignments/{assignmentId}` – Remove assignment.
- `POST /api/assignments/{assignmentId}/submit` – Upload and evaluate a submission.  
  **LLM Invoked Automatically:**
  - `/llm/classify` → classification result.
  - `/llm/rubric-score` → rubric labels.
  - `/llm/generate-feedback` → educator review suggestions.
- `POST /api/submissions/{submissionId}/resubmit` – Re-upload a revised version of the same submission, triggering the same LLM evaluation calls.
- `GET /api/submissions/{submissionId}` – View complete submission package: original work, rubric, classification, feedback, and evaluation history.
- `PATCH /api/submissions/{submissionId}/status` – Mark submission status (reviewed, needs follow-up, archived).
- `GET /api/submissions/{submissionId}/download` – Download a compiled evaluation report.
- `DELETE /api/submissions/{submissionId}` – Permanently remove a submission from the system.

#### **Files**
- `POST /api/files` – Upload supporting documents.
- `GET /api/files/{fileId}` – View file.
- `GET /api/files/{fileId}/download` – Download original file.
- `DELETE /api/files/{fileId}` – Remove file.

#### **User Management (Admin only)**
- `GET /api/users` – List all registered users with roles and status.
- `PUT /api/users/{userId}` – Update user’s role or deactivate/reactivate account.
- `DELETE /api/users/{userId}` – Permanently remove a user account.

---

## 3. Future Scope APIs

### LLM Team

#### `POST /llm/ai-score`
- **Purpose:** Return a numeric 0–100 AI likelihood to enable fine-grained institutional policy thresholds.

#### `POST /llm/prompt-similarity`
- **Purpose:** Compare submission vs. prompt text + GenAI chat log; returns `similarity_percent`.  
  **Policy rule:** ≥40% similarity triggers flag for resubmission.

#### `POST /llm/highlight-spans`
- **Purpose:** Provide character-level ranges marking AI-generated or prompt-overlapping text (for Turnitin-style visual highlights in the UI).

#### `POST /llm/evaluate-all`
- **Purpose:** Perform one-shot evaluation returning:
  - Classification (Human / AI / Hybrid)
  - AI Score (0–100)
  - Prompt Similarity (%)
  - Rubric scores (numeric 1–5 per criterion)
  - Structured feedback (student-facing + teacher-only notes)

#### `POST /llm/redact` *(optional)*
- **Purpose:** Automatically remove PII (Personally Identifiable Information) from submissions or chat logs before storage or LLM processing.

---

### Frontend ↔ Backend (Expanded User Roles)

#### **Auth**
- `POST /api/auth/register` – Create student, teacher, and admin accounts with role.
- `POST /api/auth/login` – Authenticate; return `{token, role}`.
- `GET /api/auth/me` – Get current user + role.

#### **Assignments & Prompts**
- `POST /api/prompts` – Create and manage predefined prompts linked to assignments.
- `GET /api/prompts` – List available prompts and their use cases.
- `GET /api/prompts/{promptId}` – Retrieve full prompt details.
- `POST /api/assignments` – Teacher creates assignment, links to a prompt, and sets parameters.
- `GET /api/assignments` – List assignments based on user role (students see assigned ones, teachers see all they created).
- `PUT /api/assignments/{assignmentId}` – Update title, due date, linked prompt.
- `DELETE /api/assignments/{assignmentId}` – Remove assignment.

#### **Submissions (Now with Student Role)**
- `POST /api/assignments/{assignmentId}/submit` – Student submits work (text or file) with optional GenAI chat log; backend calls:
  - `/llm/classify`
  - `/llm/ai-score`
  - `/llm/prompt-similarity`
  - `/llm/highlight-spans`
  - `/llm/rubric-score`
  - `/llm/generate-feedback`
- `POST /api/submissions/{submissionId}/resubmit` – Revision flow, keeping the same submissionId but creating a new version.
- `GET /api/submissions/{submissionId}` –  
  **Teacher view:** full detail (submission, AI scores, highlights, rubric, versions, notes).  
  **Student view:** only rubric, LLM feedback, and teacher comments.
- `PATCH /api/submissions/{submissionId}/status` – Mark reviewed / needs revision / archived.
- `GET /api/submissions/{submissionId}/download` – Download full report with highlights.
- `DELETE /api/submissions/{submissionId}` – Remove submission.

#### **Feedback**
- `POST /api/submissions/{submissionId}/teacher-feedback` – Save teacher feedback + private notes.
- `POST /api/submissions/{submissionId}/student-response` – Student can reply to teacher feedback (optional discussion thread).

#### **Files**
- `POST /api/files` – Upload supporting documents (e.g., reference material).
- `GET /api/files/{fileId}` – View file.
- `GET /api/files/{fileId}/download` – Download file.
- `DELETE /api/files/{fileId}` – Remove file.

#### **User Management (Admin)**
- `GET /api/users` – List all users with roles and activity status.
- `PUT /api/users/{userId}` – Change role, reset password, deactivate/reactivate.
- `DELETE /api/users/{userId}` – Permanently remove user.

---

### Shared Conventions (Quick Reference)
- **Chat log format:**  
  ```json
  [{ "role": "user|ai", "text": "..." }]
