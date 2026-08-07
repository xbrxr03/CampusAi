# CampusAI — Demo Script

Software Engineering Fundamentals — Centennial College
Prepared by: Nahirobies Sanchez — QA & Presentation Lead

Use this alongside the slides (`CampusAI_QA_Presentation_for_GoogleSlides` — link in the README). Each section maps to a slide; timings are a starting point to adjust once rehearsed.

---

## 1. Opening / Problem & Motivation (~1 min)

- Hook: front-desk and info-line staff at colleges field the same repetitive questions (admissions, registration, tuition, deadlines) every day.
- Problem: long wait times, limited office hours, staff pulled away from complex student needs.
- One-line pitch: **CampusAI is an AI-powered virtual receptionist that answers common student questions instantly, using only verified school information.**

## 2. Project Overview (~1 min)

- What it is: a digital avatar students talk to — by voice or text — at a kiosk, info desk, or on the school website.
- Powered by Retrieval-Augmented Generation (RAG): answers are pulled from official sources, not invented.
- Not a replacement for staff — it handles repetitive questions so staff can focus on complex ones.

## 3. MVP Feature Walkthrough (~2–3 min)

- AI Chat Interface — conversational Q&A
- RAG-based answers grounded in official college info
- Source citations shown with each answer
- Talking avatar + text-to-speech
- Department recommendation / escalation when confidence is low

## 4. Live Demo (~3–4 min)

Suggested demo questions (map to Test Plan Section 5):

1. **In-scope, high-confidence question** (e.g. tuition or registrar location) → show correct, sourced answer (TC-01, TC-03, TC-05).
2. **Out-of-knowledge-base question** → show the system admits uncertainty instead of fabricating (TC-04).
3. **Department-specific question** (e.g. financial aid) → show department recommendation (TC-06).
4. **Out-of-scope request** (e.g. "register me for a course") → show the system correctly declines and redirects (TC-15).
5. Show avatar animation + TTS playback in sync with the answer (TC-07, TC-08).

_Fallback if live demo fails: switch to the recorded demo clip in the slides._

## 5. System Architecture (~1–2 min)

- Data flow: Student Input → Frontend (Next.js) → Backend (FastAPI) → RAG Pipeline (LangChain + ChromaDB + Sentence Transformers) → LLM (Ollama) → Response.
- Why this stack: async-native FastAPI for concurrent queries, local-first ChromaDB for a no-budget prototype, LangChain to orchestrate retrieval → prompt → generation.

## 6. QA & Testing Results (~1–2 min)

- Testing layers covered: unit, integration, RAG accuracy, usability, performance, escalation.
- Reference results from `CampusAI_Test_Logs.md`: pass rate on High-priority cases, any resolved defects.
- Exit criteria met: all High-priority cases pass, no open Critical/High defects, RAG answers accurate and cited.

## 7. Next Steps (~1 min)

- Items still out of scope for this MVP: authentication, registration/payment processing, production load testing, mobile app.
- Planned follow-ups: knowledge base refresh strategy, expanded test coverage, production hardening.

## 8. Closing / Q&A

- Recap the one-line pitch.
- Open the floor for questions.

---

## Rehearsal checklist

- [ ] Run through with slides, timing each section
- [ ] Confirm demo environment (frontend/backend) is running before presenting
- [ ] Have the fallback recorded clip ready
- [ ] Confirm Google Slides link is live and shared
