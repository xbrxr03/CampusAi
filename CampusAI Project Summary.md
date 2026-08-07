# CampusAI

**AI-Powered Virtual Receptionist — Project Summary**
Software Engineering Fundamentals — Centennial College
Prepared by: Nahirobies Sanchez

---

## Executive Summary

CampusAI is a proposed AI-powered virtual receptionist for colleges and universities. It allows students to speak naturally with a digital avatar at an information desk, kiosk, or school website. Using artificial intelligence and Retrieval-Augmented Generation (RAG), the receptionist understands student questions, searches verified school information, and responds using both voice and text.

CampusAI helps students with common questions related to admissions, course registration, tuition, financial aid, campus navigation, deadlines, events, and student services. Because the system retrieves answers only from approved school websites, FAQs, academic calendars, policies, and databases, it reduces inaccurate responses and ensures information comes from official sources.

The system also includes speech recognition, text-to-speech, an animated avatar, department classification, and a human escalation option. When the AI cannot confidently answer a question, it directs the student to the correct department or connects them with a staff member.

The goal of CampusAI is not to replace reception staff, but to support them: handling repetitive questions, reducing wait times, providing support outside regular office hours, and freeing staff to focus on more complex student concerns.

## Core Features (MVP)

- **AI Chat Interface** — conversational Q&A with students
- **Retrieval-Augmented Generation (RAG)** — answers based on official college information
- **Source citations** — shows where each answer comes from
- **Talking avatar** — visual avatar for responses
- **Text-to-speech** — audio output of responses
- **Department recommendations** — suggests the right department for follow-up

## Technology Stack

| Layer | Technologies |
|---|---|
| Frontend | Next.js 14+, TypeScript, Tailwind CSS |
| Backend | Python 3.11+, FastAPI, Pydantic |
| AI / ML | LangChain, ChromaDB, Ollama, Sentence Transformers |
| Infrastructure | Git, GitHub, Docker (optional) |

## QA & Presentation — My Role

As QA & Presentation Lead, my responsibilities are testing, slide design, delivering the presentation, and compiling references. My focus is on making sure CampusAI gives accurate, reliable, and usable answers before each milestone demo.

### Testing Plan

- **Unit Testing** — verify individual functions such as API endpoints and RAG retrieval logic.
- **Integration Testing** — confirm the frontend, backend, and vector database work together end to end.
- **RAG Accuracy Testing** — check that retrieved answers are correct, sourced, and grounded in official documents.
- **Usability Testing** — observe real students using the chat interface and avatar, then collect feedback.
- **Performance Testing** — measure response time and behavior under multiple simultaneous queries.
- **Escalation Testing** — confirm low-confidence answers correctly route to a department or staff member.

### Sample Test Cases

> These are illustrative highlights, not the full matrix. The complete 15-case test suite with its own ID numbering (TC-01…TC-15) lives in `CampusAI_Test_Plan.md`. The IDs below intentionally use an "S-" prefix so they never collide with the official TC IDs.

| ID | Feature | Test Description | Expected Result |
|---|---|---|---|
| S-01 | AI Chat | Ask a tuition fee question | Correct, sourced answer within seconds |
| S-02 | RAG Retrieval | Ask about a policy not in the knowledge base | System admits uncertainty, no fabricated answer |
| S-03 | Source Citations | Ask about registration deadlines | Answer displays the originating source |
| S-04 | Escalation | Ask an ambiguous, low-confidence question | Student redirected to correct department |
| S-05 | Avatar + TTS | Submit any valid query | Avatar animates, audio matches on-screen text |
| S-06 | Performance | Send 20 concurrent queries | All responses returned without failure or delay |

> Full test case list (TC-01…TC-15) lives in `CampusAI_Test_Plan.md`.

### Presentation Plan

The final presentation will walk through: the problem and motivation, project overview, MVP features, system architecture, technology stack, the QA and testing results, and next steps. Slides will use visuals, diagrams, and short demo clips instead of long blocks of text, keeping the audience focused on results.

**Google Slides link:** [CampusAI_QA_Presentation_for_GoogleSlides.pptx](https://github.com/xbrxr03/CampusAI/blob/master/CampusAI_QA_Presentation_for_GoogleSlides.pptx)

## References

- Lewis, P., et al. (2020). Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks. NeurIPS.
- LangChain Documentation. Retrieved 2026, from https://python.langchain.com/
- ChromaDB Documentation. Retrieved 2026, from https://docs.trychroma.com/
- Ollama Documentation. Retrieved 2026, from https://ollama.ai/
- Next.js Documentation. Retrieved 2026, from https://nextjs.org/docs
- FastAPI Documentation. Retrieved 2026, from https://fastapi.tiangolo.com/
- Centennial College. Official Programs, Policies and Academic Calendar. Retrieved 2026, from https://www.centennialcollege.ca/
