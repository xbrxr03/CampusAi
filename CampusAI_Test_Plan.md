# CampusAI — QA Test Plan

Software Engineering Fundamentals — Centennial College
Prepared by: Nahirobies Sanchez — QA & Presentation Lead
Last Updated: July 29, 2026

---

## 1. Introduction

This document defines the QA testing strategy for CampusAI, an AI-powered virtual receptionist prototype for Centennial College students. It is owned by the QA & Presentation Lead and is intended to guide testing activities from Meeting 2 (repository setup) through Meeting 5 (final testing and presentation).

CampusAI is a proposed AI-powered virtual receptionist for colleges and universities, allowing students to interact naturally — via voice or text — with an animated avatar at kiosks, information desks, or on the school website.

Using retrieval-augmented generation (RAG), the system pulls answers from verified, official school sources (websites, FAQs, academic calendars, policies, databases) to minimize inaccurate responses. It helps students with common questions about admissions, registration, tuition, financial aid, campus navigation, deadlines, events, and student services.

### 1.1 Purpose

To ensure that CampusAI's chat, retrieval, citation, avatar, and text-to-speech features work correctly, reliably, and are easy to use before each milestone demo and the final presentation.

Key features include speech recognition, text-to-speech, an animated avatar, department classification, and human escalation — if the AI can't confidently answer, it routes the student to the right department or a staff member.

The goal isn't to replace reception staff, but to handle repetitive questions, cut wait times, offer support outside office hours, and free up staff to focus on more complex student needs.

### 1.2 Project Reference

Full project scope and architecture are defined in `PROJECT_SOURCE_OF_TRUTH.md` and `docs/ARCHITECTURE.md`. This test plan should be read alongside those documents.

## 2. Scope

### 2.1 In Scope for Testing

- AI Chat Interface (conversational Q&A)
- Retrieval-Augmented Generation (RAG) accuracy
- Source citation display
- Talking avatar behavior
- Text-to-speech output
- Department recommendation logic
- Backend API endpoints (`/api/query`, `/health`)
- Basic usability and cross-browser checks

### 2.2 Out of Scope

- Student authentication / login
- Course registration and payment processing
- Production load/stress testing
- Mobile application testing (no mobile app in this version)

## 3. Test Strategy

Testing is organized into the following layers, aligned with the project's Next.js + FastAPI + LangChain/ChromaDB architecture:

| Layer | Description |
|---|---|
| **Unit Testing** | Backend logic (Pydantic schemas, services) and frontend components tested in isolation. Owned mainly by developers, reviewed by QA. |
| **API Testing** | Manual and scripted checks of `/api/query` and `/health` using curl/Postman — valid input, invalid input, edge cases, and error handling. |
| **RAG / Content QA** | Ask a fixed set of representative questions and verify answers against the actual knowledge base documents — checking for accuracy, hallucination, and correct citation. |
| **Functional / UI Testing** | Manual walkthroughs of the chat UI, avatar, and TTS against the test cases in Section 5. |
| **Usability Testing** | A non-team member attempts common student questions unassisted; QA records friction points. |
| **Regression Testing** | Before each milestone demo, re-run prior passing test cases to confirm new changes haven't broken existing features. |
| **Performance (light)** | Track response time for a handful of representative queries; flag anything that would hurt a live demo. |

## 4. Test Environment & Tools

| Area | Details |
|---|---|
| **Frontend** | Local dev server (`npm run dev`) at `localhost:3000`, tested in Chrome, Firefox, Edge |
| **Backend** | Local FastAPI server (`python main.py`) at `localhost:8000`, docs at `/docs` |
| **API Testing Tool** | Postman or curl |
| **LLM** | Ollama Pro (local) running the project's configured model |
| **Bug Tracking** | GitHub Issues on the team repository, labeled by feature and severity |
| **Test Case Tracking** | This document + a shared spreadsheet (Pass/Fail/Blocked status per milestone) |

## 5. Test Cases

The table below covers the MVP features. Each test case should be re-run at every milestone once the related feature is implemented. Status columns (Pass/Fail/Blocked) are tracked in the companion spreadsheet, not duplicated here — see `CampusAI_Test_Logs.md` for run-by-run results.

| ID | Feature | Test Steps | Expected Result | Priority |
|---|---|---|---|---|
| TC-01 | Chat Interface | Open chat UI. Type a general question (e.g. "Where is the registrar's office?") and submit. | Response appears within a reasonable time, is relevant, and is displayed in the chat thread. | High |
| TC-02 | Chat Interface | Submit an empty message. | Submit is disabled or a validation message appears; no request is sent. | Medium |
| TC-03 | RAG Retrieval Accuracy | Ask a question with a known answer in the knowledge base (e.g. a specific program's admission requirement). | Answer matches the source document; no fabricated details. | High |
| TC-04 | RAG Retrieval Accuracy | Ask a question with NO answer in the knowledge base. | System responds that it does not have this information, rather than guessing. | High |
| TC-05 | Source Citations | Ask a factual question and inspect the response. | Response includes a visible citation/source reference matching the retrieved document. | High |
| TC-06 | Department Recommendations | Ask a question related to a specific department (e.g. financial aid). | Correct department is suggested along with contact/next-step info. | Medium |
| TC-07 | Talking Avatar | Submit a query and observe the avatar during response generation. | Avatar animates in sync with the response; no freezing or visual glitches. | Medium |
| TC-08 | Text-to-Speech | Submit a query and listen to the audio output. | Audio plays clearly, matches the on-screen text, and can be paused/stopped. | Medium |
| TC-09 | API - /api/query | Send a valid POST request with a sample question via Postman/curl. | HTTP 200 with a well-formed JSON response containing answer + sources. | High |
| TC-10 | API - /api/query | Send a malformed request (missing required field). | HTTP 4xx with a clear error message; server does not crash. | High |
| TC-11 | API - /health | Send GET request to `/health`. | HTTP 200 with status confirmation. | Low |
| TC-12 | Performance | Submit 5 consecutive queries and measure response time. | Average response time stays within agreed target (e.g. under 5–8s for local LLM). | Medium |
| TC-13 | Usability | Have a first-time user (non-team member) attempt 3 typical questions unassisted. | User completes the task without confusion; UI is intuitive. | Medium |
| TC-14 | Cross-browser | Load frontend in Chrome, Firefox, and Edge. | Layout and functionality are consistent across browsers. | Low |
| TC-15 | Out-of-Scope Guard | Ask the assistant to register for a course or process a payment. | System clearly states this is out of scope rather than attempting the action. | Medium |

## 6. Defect / Bug Reporting Process

- Log every failed test case as a GitHub Issue with: steps to reproduce, expected vs. actual result, screenshots/logs, and severity (Critical / High / Medium / Low).
- Tag the issue with the relevant feature label (`chat`, `rag`, `avatar`, `tts`, `api`, `ui`).
- Assign to the relevant team member per `TEAM_ROLES_AND_DELIVERABLES.md`.
- QA re-tests and closes the issue once a fix is merged.
- Critical/High defects block a milestone demo until resolved or a workaround is agreed with the team.

## 7. Test Schedule

| Milestone | Activities |
|---|---|
| **Meeting 2 (current)** | Finalize this test plan; set up GitHub Issues labels; smoke-test repo skeleton (frontend and backend both start without errors). |
| **Meeting 3** | Test RAG pipeline and knowledge base as they come online (TC-03, TC-04, TC-05); test `/api/query` (TC-09, TC-10, TC-11). |
| **Meeting 4** | Full functional pass on chat UI, avatar, TTS, department recommendations (TC-01, 02, 06, 07, 08); begin regression testing; usability test (TC-13). |
| **Meeting 5** | Final regression pass on all test cases; performance check (TC-12); sign-off; prepare demo script for presentation. |

## 8. Exit Criteria

- All High-priority test cases pass.
- No open Critical or High-severity defects.
- RAG answers are accurate and cited for the demo question set.
- Demo walkthrough has been rehearsed end-to-end without errors.

## 9. Appendix: Blank Test Case Template

| ID | Feature | Test Steps | Expected Result | Priority |
|---|---|---|---|---|
| TC-XX | | | | |

## 10. System Architecture Notes

CampusAI is a **RAG-based conversational agent** (Retrieval-Augmented Generation) — not a fine-tuned model, not a rules-based chatbot. Instead of the LLM's parametric knowledge answering questions, the system performs semantic retrieval against a vector store at inference time, injects the retrieved context into the prompt, and constrains the LLM to generate responses grounded in that context. This is what enables source citation — the system can point to exactly which document chunk produced an answer.

**Data flow:** Student Input → Frontend → Backend → RAG Pipeline → LLM → Response

1. **Frontend (Next.js, App Router)** captures the query client-side, likely via a controlled React component with state managed through hooks (`hooks/`). The chat interaction itself is almost certainly client-side (CSR) since it's a stateful, interactive loop, even though initial page loads may use SSR.
2. **HTTP/REST call** to the FastAPI backend — the boundary between `frontend/` and `backend/` is a network boundary, not just a folder boundary, so the two can be deployed, scaled, and versioned independently. `types/` (frontend) and `schemas/` (backend) need to be kept in sync manually, a common source of drift bugs in split-stack projects.
3. **FastAPI request handling (`app/api/`)** — routes receive the payload, and Pydantic (`app/schemas/`) performs runtime type validation and coercion before any business logic executes, plus automatic OpenAPI schema generation (hence `/docs` being interactive).
4. **RAG Pipeline (LangChain orchestration):**
   - The query is embedded into a vector using **Sentence Transformers**.
   - **ChromaDB** performs an approximate nearest neighbor (ANN) search over the pre-indexed `knowledge/` corpus, returning the top-k most semantically similar chunks.
   - Retrieved chunks are inserted into a prompt template alongside the original query.
   - **Ollama Pro** serves the LLM locally via an OpenAI-compatible API, for cost control and data privacy (no student query data leaves the local environment).
5. **Response assembly** — the generated text is packaged with citation metadata (which `knowledge/` document/chunk contributed), then optionally routed through avatar animation and TTS synthesis.

**Why this stack:**
- **FastAPI over Flask/Django** — async-native, useful since LLM inference and vector search are I/O- or compute-bound and benefit from non-blocking request handling when multiple students query concurrently.
- **ChromaDB over Pinecone/Weaviate** — embeddable and local-first, no external service dependency, fitting a prototype/coursework context.
- **LangChain** — orchestration glue, chaining retrieval, prompt construction, and generation into a single callable pipeline.

**Structural risk points to watch:**
- `.env.example` exists but the real `.env` doesn't ship — each teammate must independently configure secrets.
- No `tests/` directory currently exists — this is the gap the QA role is covering.
- `docs/API.md` is listed as "to be created" — the interactive `/docs` (Swagger UI) is currently the only source of truth for the API contract.
- Knowledge base versioning is unaddressed — if `college_info.json` changes, someone needs to manually re-run the embedding/indexing step into ChromaDB, or the vector store goes stale.
