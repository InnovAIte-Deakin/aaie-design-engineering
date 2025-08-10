# AAIE System Overview & Context Diagram

## Table of Contents
1. [Overview](#overview)
2. [Important Notes](#important-notes)  
   2.1 [In Scope](#in-scope)  
   2.2 [Deferred to Phase 2](#deferred-to-phase-2)
3. [Diagram Description – Context Diagram](#diagram-description--context-diagram)  
   3.1 [System Boundary (AAIE Platform)](#1-system-boundary-aaie-platform)  
   3.2 [External Actors](#2-external-actors)  
   3.3 [Key Functional Modules](#3-key-functional-modules-inside-aaie)  
   3.4 [Major Data Flows](#4-major-data-flows)  
   3.5 [Scope Notes (Phase 1 – from PO)](#5-scope-notes-phase-1--from-po)  
4. [System Components](#6-system-components-inside-aaie)  
5. [Data Flow Description](#7-data-flow-description)

---

![AAIE Context Diagram](../product-diagram/Context_Diagram(v.1.1).png)

---

## Overview
The context diagram for the **AAIE (Academic AI Evaluator)** system outlines the high-level structure of the application by defining the interactions between the system and its external actors. It serves as a top-level view of the system’s boundaries, inputs, and outputs, showing how various stakeholders interact with the platform.  
It ensures all development teams (Product Engineering, Model Development, and Data Curation) have a shared understanding of the system’s role in the broader academic environment.

---

## Important Notes
**Phase 1** of AAIE focuses on enabling educators to submit student work for automated AI classification, rubric-based scoring, and formative feedback. The system allows educators to review results, add their own comments, and combined feedback reports.

### In Scope
- Educator login/register  
- Upload student work  
- **LLM Engine** analysis: AI usage classification (Human / AI / Hybrid), rubric scoring, and short feedback generation  
- Educator review of AI output and addition of teacher feedback  
- Download of final structured feedback report  

### Deferred to Phase 2
- Role-Based Access Control (RBAC) enforcement  
- Rubric upload and rubric alignment logic  
- Prompt history viewing/audit logs  
- Plagiarism detection and prompt similarity analysis  
- Student-facing submission workflows  

![AAIE Context Diagram](../product-diagram/Context_Diagram(v.1.2).png)

---

## Diagram Description – Context Diagram
**Diagram Name:** AAIE Prompt Feedback & Detection System – Context Diagram  
**Version:** v1.2  
**Stakeholders:** Educators, Students (phase 2), System Admins, PO, LLM & Model Team  
**Purpose:** This context diagram illustrates how the core AAIE platform interacts with external actors and subsystems, defining the system boundary and identifying all major data flows and integration points.

---

### 1. System Boundary (AAIE Platform)
The **AAIE platform** is the core system providing:
- Prompt evaluation  
- Feedback generation  
- AI usage detection  
- Academic integrity checks  

Modules are tightly coupled to form the **feedback and detection workflow**.

---

### 2. External Actors
#### **A. Educator (Primary User)**
- Logs in and uploads prompts/student responses (real or simulated)  
- Selects rubrics or defines new evaluation criteria (Deferred to Phase 2)
- Reviews AI feedback, similarity results, and rubric scores  
- View structured feedback reports  

**Interactions:**
- Initiates prompt submission and feedback generation  
- Views outputs and evaluation reports  
- Receives academic integrity and AI misuse analysis  

#### **B. System Admin / Developer** (Product Engineering Team)
- Oversees platform operations and simulation processes  
- Uploads synthetic responses for testing  
- Connects backend models (APIs, LLM endpoints)  
- Deploys and monitors model updates  

**Interactions:**
- Deploys or updates LLM APIs  
- Monitors hallucinations, biases, and logs  

#### **C. Model Developers** (Model Design Team)
- Provide backend LLM models  
- Maintain API endpoints for detection and feedback  
- Evaluate authenticity, hallucination, and rubric alignment  

**Interactions:**
- Model API integration and result evaluation  
- Design few-shot/zero-shot prompts  
- Return structured evaluation data  

#### **D. Internal Data Curation Team**
- Supply curated and synthetic datasets for training  
- Ensure prompt-response pairs are realistic  

#### **E. Students** (Phase 2+)
- Indirectly represented in Phase 1  
- In Phase 2, receive feedback reports and resubmit corrected responses  

#### **Optional Actors**
- University Stakeholders (Governance Layer)  
- External Services (e.g., FastAPI, Hosting, GitHub)  

---

### 3. Key Functional Modules (Inside AAIE)
1. **Prompt Submission** – collects input data, metadata, and triggers evaluation  
2. **Feedback Generation** – calls LLM API and aligns with rubric  
3. **AI Usage Detection** – classifies as Human/AI/Hybrid  
4. **Rubric Evaluation** – scores clarity, structure, relevance  
5. **Report Generator** – produces PDF/JSON feedback reports  (Deferred to Phase 2)
6. **Model Interaction / Monitoring** – deploy/update LLMs, log outputs  
7. **Synthetic Data Generator** – creates test data for evaluation  
8. **LLM Output Evaluator** – validates accuracy, bias, hallucination  
9. **Prompt-to-Output Chain Tracker** – maintains audit trail  
10. **Model Deployment & API Infrastructure** – versioning, health checks  
11. **Bias and Hallucination Monitor** – flags factual issues  
12. **Admin Tools and Analytics Dashboard** – system usage metrics  

---

### 4. Major Data Flows
- **Prompt/Response Data** → Educator → Feedback Engine  
- **Generated Feedback** → UI → Download   (Deferred to Phase 2)
- **Rubric Scoring + Detection Results** → Final Report  
- **API Results & Metrics** → Admin/Model Team  
- **Synthetic Data** → System for testing  

---

### 5. Scope Notes (Phase 1 – from PO)
- Real student data not required  
- Focus on few-shot/zero-shot testing over fine-tuning  
- Prioritize prompt outlining, alignment evaluation, authenticity scoring  
- Ensure report delivery tracking  

---

## 6. System Components (Inside AAIE)
(Full description of 12 components as listed above with **Purpose** and **Functionality**)

### 1. Prompt Submission & Feedback Interface
- **Purpose:** Allows educators to submit student work (prompts + responses).
- **Functionality:** Supports file/text input, metadata tagging (e.g., subject), and triggers the evaluation process.
- **Links with:** User authentication in Phase 1; role-based access control in Phase 2.

### 2. Enforce Role-Based Access Control (RBAC) *( (Deferred to Phase 2)*
- **Purpose:** Ensures actions within the system are authorized based on user roles (educator, system admin, student in future phases).
- **Functionality:** Limits access to specific functionalities such as viewing analytics or uploading assessments based on assigned privileges.
- **Important For:** Academic integrity, data privacy, and traceability.

### 3. Generate Feedback Module
- **Purpose:** Interacts with the LLM API to generate detailed feedback based on educator-submitted prompts.
- **Functionality:** Converts structured input into evaluation requests and formats feedback into readable summaries.

### 4. Rubric Alignment Engine  (Deferred to Phase 2)
- **Purpose:** Aligns LLM-generated feedback with rubric categories provided by educators.
- **Functionality:** Compares AI feedback against expected learning outcomes and highlights alignment/misalignment.

### 5. AI Usage Detection (Academic Integrity Module)
- **Purpose:** Identifies if a student submission was potentially generated by AI.
- **Functionality:** Uses linguistic features, AI usage scoring, and cross-checking with known patterns to determine authenticity.
- **Flagging Options:** `AI`, `Hybrid`, `Human`.

### 6. Feedback Report Generator  (Deferred to Phase 2)
- **Purpose:** Combines outputs from rubric alignment, feedback generation, and AI usage detection into a single downloadable document.
- **Export Options:** PDF, structured JSON (for LMS integration), or internal dashboard display.

### 7. Synthetic Data Generator (GenAI)
- **Purpose:** Replaces real student data with simulated responses for testing and validation.
- **Benefits:** Avoids ethical/data privacy issues during testing.

### 8. LLM Output Evaluator
- **Purpose:** Evaluates and validates LLM performance for accuracy, clarity, bias, and hallucination.
- **Workflow:**
  1. Test with few-shot prompts.
  2. Monitor performance using benchmark rubrics and curated samples.
- **PO Insight:** Shift focus from fine-tuning to zero/few-shot testing for faster iteration.

### 9. Prompt-to-Output Chain Tracker
- **Purpose:** Monitors the full journey from prompt submission to final feedback for transparency.
- **Includes:** Prompt structure, rubric references, AI output logs, and educator revisions.

### 10. Model Deployment & API Infrastructure
- **Purpose:** Manages backend LLM integration.
- **Tools:** FastAPI or similar frameworks.
- **Controls:** Versioning, access control, and health checks.

### 11. Bias and Hallucination Monitor
- **Purpose:** Flags responses that are inaccurate or biased.
- **Use:** Ensures academic fairness and factual accuracy.

### 12. Admin Tools and Analytics Dashboard
- **Purpose:** Allows system administrators and governance users to:
  - Track usage
  - Access evaluation metrics
  - Review flagged submissions
- **Planned Features:** AI usage statistics, rubric heatmaps.

---

## 7. Data Flow Description

### 1. Input Stage – Prompt Submission
- **Actors:** Educator (primary), System Admin (optional).
- **Actions:**
  1. Educator logs in.
  2. Submits prompt and student response (real or synthetic).
  3. Chooses or uploads rubric.  (Deferred to Phase 2)
  4. Sets evaluation parameters.
- **Data Created:** Prompt text, student response, rubric reference (Deferred to Phase 2), evaluation metadata.
- **Flow:** Input → Prompt Management Module → Prompt Database.

### 2. Preprocessing & Role Enforcement *(Phase 2)*
- **Component:** RBAC.
- **Function:** Validates user permissions and routes requests.
- **Flow:** Prompt Data → RBAC Filter → Feedback & Detection Engine.

### 3. Feedback Generation + (Rubric Alignment Deferred to Phase 2)
- **Components:** Feedback Engine (Phase 1), Rubric Alignment Engine (Phase 2).
- **Function:** LLM generates feedback → Feedback matched against rubric (Deferred to Phase 2) → Misalignments highlighted (Deferred to Phase 2).
- **Flow:** Prompt + Response + Rubric (Phase 2) → LLM API → Feedback → Alignment Module → Output.

### 4. AI Usage Detection
- **Components:** AI Detector, History Cross-Check *(Phase 2)*.
- **Function:** Analyzes text style/tokens, compares with AI patterns.
- **Outcome:** Likelihood score (Deferred to Phase 2) + classification.
- **Flow:** Response → AI Detection Engine → Label + Explanation.

### 5. Report Generation & (Download Deferred to Phase 2)
- **Component:** Report Formatter / (Export Module for Phase 2).
- **Function:** Aggregates results into PDF/JSON/dashboard. (Deferred to Phase 2)
- **Flow:** Feedback + Rubric (phase 2) + Detection → Report Generator (Phase 2) → Download/View.

### 6. Backend Monitoring & Logging
- **Components:** API Tracker, Bias Monitor, System Logs.
- **Function:** Tracks API latency, anomalies, submission history, and role changes.
- **Flow:** All Outputs → Log Aggregator → Dev Analytics Dashboard / GitHub.

### 7. GenAI Simulation (Optional Data Source)
- **Actor:** System Admin / Developer.
- **Function:** Generates simulated responses for testing rubric alignment and LLM evaluation.
- **Flow:** Rubric → GenAI → Synthetic Prompt/Response → Feedback Pipeline.

### 8. Output Archival *(Phase 2/3)*
- **Stores:** Submission records, reports for audits, AI detection logs.
- **Compliance:** Must align with privacy laws when using real student data.
- **Flow:** Final Reports → Secure Storage (Encrypted Database).

---

These descriptions clarify user interactions, data movement, and system boundaries, supporting **detailed component design**, **API documentation**, and **testing plans**.

---

**Please refer to ![System Design](../) for detailed information.**

---
