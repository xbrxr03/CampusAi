# Retrieval API Test Log

**Endpoint:** `POST http://localhost:8000/api/query`

---

## Test 1 — Engineering Programs

### Request

```json
{
  "context": "I'm interested in full-time programs",
  "query": "Tell me about engineering programs"
}
```

### Response

```json
{
  "success": true,
  "data": {
    "answer": "At Centennial College, you can find various engineering technology programs. One such program is the **Software Engineering Technology – Artificial Intelligence**, which focuses on AI application development, machine learning, natural language processing, data visualization, big data fundamentals, image recognition, recommender systems, and digital ethics.\n\nThis program is available in both online and on-campus versions and offers a co-op option as well. It's open to graduates of Software Engineering Technology or similar programs, and holders of a degree/diploma in a computing-related field. There are also fast-track options for qualified applicants that allow you to enter directly into Semester 3.\n\nFor more information about the **Downsview Campus**, which is home to aerospace and aviation programs including Aviation Technician – Aircraft Maintenance and related Engineering Technology programs, feel free to contact their department.",
    "confidence": 0.75,
    "sources": [
      {
        "title": "Program Offerings and Credentials",
        "excerpt": "### Software Engineering Technology – Artificial Intelligence - **School:** Engineering Technology and Applied Science - **Credential:** Advanced Diploma (optional co-op; online and on-campus versions available) - Focuses on AI application development, machine...",
        "section": "Software Engineering Technology – Artificial Intelligence",
        "source_path": "programs/centennial_programs (1).md",
        "url": "https://www.centennialcollege.ca/programs-and-courses"
      },
      {
        "title": "School of Transportation",
        "excerpt": "- **Downsview Campus** — home to the College's aerospace and aviation programs, including Aviation Technician – Aircraft Maintenance and related Engineering Technology programs in Aerospace Manufacturing. The campus reuses the historic de Havilland Canada airc...",
        "section": "Campuses",
        "source_path": "departments/6_school_of_transportation.md",
        "url": "https://www.centennialcollege.ca/about-centennial/schools/school-of-transportation/"
      },
      {
        "title": "School of Flexible Learning (Part-time Learning)",
        "excerpt": "- **Part-time Online Learning** — programs and courses that can be completed entirely on the learner's own schedule.",
        "section": "Offerings",
        "source_path": "departments/8_school_of_flexible_learning.md",
        "url": "https://www.centennialcollege.ca/about-centennial/faculties-and-schools/faculty-of-lifelong-learning-and-industry-training/school-of-flexible-learning"
      }
    ]
  },
  "message": "Query processed successfully",
  "error": null
}
```

---

## Test 2 — AI Program Details

### Request

```json
{
  "context": "Looking for tech diplomas",
  "query": "What does the Artificial Intelligence program cover?"
}
```

### cURL

```bash
curl -X 'POST' \
  'http://localhost:8000/api/query' \
  -H 'accept: application/json' \
  -H 'Content-Type: application/json' \
  -d '{
  "context": "Looking for tech diplomas",
  "query": "What does the Artificial Intelligence program cover?"
}'
```

**Request URL:** `http://localhost:8000/api/query`
**Status Code:** `200`

### Response

```json
{
  "success": true,
  "data": {
    "answer": "The Artificial Intelligence program at Centennial College covers AI application development, machine learning, natural language processing, data visualization, big data fundamentals, image recognition, recommender systems, and digital ethics. It is a 3-year Advanced Diploma in the School of Engineering Technology and Applied Science.",
    "confidence": 0.75,
    "sources": [
      {
        "title": "Program Offerings and Credentials",
        "excerpt": "### Software Engineering Technology – Artificial Intelligence - **School:** Engineering Technology and Applied Science - **Credential:** Advanced Diploma (optional co-op; online and on-campus versions available) - Focuses on AI application development, machine...",
        "section": "Software Engineering Technology – Artificial Intelligence",
        "source_path": "programs/centennial_programs (1).md",
        "url": "https://www.centennialcollege.ca/programs-and-courses"
      },
      {
        "title": "School of Engineering Technology and Applied Science",
        "excerpt": "## Program Areas Programs span applied science, computer systems, software engineering, electronics, and related technology fields, including: - Software Engineering Technology, and Software Engineering Technology – Artificial Intelligence - Honours Bachelor o...",
        "section": "Program Areas",
        "source_path": "departments/4_school_of_engineering_technology_and_applied_science.md",
        "url": "https://www.centennialcollege.ca/about-centennial/schools/school-of-engineering-technology-and-applied-science/"
      },
      {
        "title": "Program Offerings and Credentials",
        "excerpt": "## Quick Reference for the AI Receptionist - **\"What's the difference between a diploma and an advanced diploma?\" →** 2 years vs. 3 years of full-time study, respectively. - **\"Can I go straight into a degree program from high school?\" →** Yes, if OSSD/Grade 1...",
        "section": "Quick Reference for the AI Receptionist",
        "source_path": "",
        "url": ""
      }
    ]
  },
  "message": "Query processed successfully",
  "error": null
}
```

> **Note:** The third source in this response was cut off in the original log (missing `source_path` and `url`). Fill these in if you have the full output.

---

## Test 3 — Progress Campus Location

### Request

```json
{
  "context": "I am a new international student",
  "query": "Where is Progress Campus located?"
}
```

### cURL

```bash
curl -X 'POST' \
  'http://localhost:8000/api/query' \
  -H 'accept: application/json' \
  -H 'Content-Type: application/json' \
  -d '{
  "context": "I am a new international student",
  "query": "Where is Progress Campus located?"
}'
```

**Request URL:** `http://localhost:8000/api/query`
**Status Code:** `200`

### Response

```json
{
  "success": true,
  "data": {
    "answer": "Progress Campus is located at 941 Progress Ave., Scarborough, ON M1G 3T8.",
    "confidence": 0.75,
    "sources": [
      {
        "title": "School of Hospitality, Tourism and Culinary Arts",
        "excerpt": "## Facilities The School is housed in a roughly 350,000-square-foot facility at Progress Campus, which also includes a Centennial Student Residence with accommodation for about 740 students. The facility includes state-of-the-art culinary labs, baking labs, a ...",
        "section": "Facilities",
        "source_path": "departments/5_school_of_hospitality_tourism_and_culinary_arts.md",
        "url": "https://www.centennialcollege.ca/about-centennial/schools/school-of-hospitality-tourism-and-culinary-arts/"
      },
      {
        "title": "Campuses and Facilities",
        "excerpt": "## Progress Campus **Address:** 941 Progress Ave., Scarborough, ON M1G 3T8 Progress is Centennial's largest campus and is home to the School of Business and the School of Hospitality, Tourism and Culinary Arts, along with Advanced Manufacturing and Automation ...",
        "section": "Progress Campus",
        "source_path": "facilities/centennial_facilities.md",
        "url": "https://www.centennialcollege.ca/about-centennial/campuses/"
      },
      {
        "title": "Campuses and Facilities",
        "excerpt": "## Quick Reference for the AI Receptionist - **Business, hospitality, culinary programs →** Progress Campus - **Health, community services programs →** Morningside Campus - **Automotive programs →** Ashtonbee Campus - **Media, communications, design, performin...",
        "section": "Quick Reference for the AI Receptionist",
        "source_path": "facilities/centennial_facilities.md",
        "url": "https://www.centennialcollege.ca/about-centennial/campuses/"
      },
      {
        "title": "Campuses and Facilities",
        "excerpt": "## Shared Services Across All Campuses - **CCSAI (Centennial College Student Association Incorporated):** student lounges, health and legal services, food bank, clubs - **Libraries and Learning Centres:** research support, study spaces, computer access - **Par...",
        "section": "Shared Services Across All Campuses",
        "source_path": "facilities/centennial_facilities.md",
        "url": "https://www.centennialcollege.ca/about-centennial/campuses/"
      }
    ]
  },
  "message": "Query processed successfully",
  "error": null
}
```

---

## Test 4 — Aerospace and Aviation Programs

### Request

```json
{
  "context": "Interested in specialized trades",
  "query": "Tell me about the aerospace and aviation programs"
}
```

### Response

```json
{
  "success": true,
  "data": {
    "answer": "The aerospace and aviation programs at Centennial College are located on the Downsview Campus. These programs include Aviation Technician – Aircraft Maintenance, which is an industry-aligned training program held in labs and hangars. The campus uses a historic de Havilland Canada aircraft factory for these programs, and it can accommodate up to 1,000 students across various aviation maintenance engineering, engineering technology, and airframe assembly programs.\n\nAdditionally, there's Aerospace Manufacturing, which is delivered jointly with the School of Engineering Technology and Applied Science. This program likely covers manufacturing techniques specific to aerospace industries.",
    "confidence": 0.75,
    "sources": [
      {
        "title": "Program Offerings and Credentials",
        "excerpt": "### Aviation and Aerospace Programs - **School:** School of Transportation (Downsview Campus) - Includes Aviation Technician and Aerospace Manufacturing training in industry-aligned labs and hangars.",
        "section": "Aviation and Aerospace Programs",
        "source_path": "programs/centennial_programs (1).md",
        "url": "https://www.centennialcollege.ca/programs-and-courses"
      },
      {
        "title": "School of Transportation",
        "excerpt": "- **Downsview Campus** — home to the College's aerospace and aviation programs, including Aviation Technician – Aircraft Maintenance and related Engineering Technology programs in Aerospace Manufacturing. The campus reuses the historic de Havilland Canada airc...",
        "section": "Campuses",
        "source_path": "departments/6_school_of_transportation.md",
        "url": "https://www.centennialcollege.ca/about-centennial/schools/school-of-transportation/"
      },
      {
        "title": "School of Transportation",
        "excerpt": "## Program Areas - Automotive Service Technician (including co-op and modified apprenticeship options, e.g., with Canadian Tire) - Auto Body Repair Techniques - Heavy Duty (truck and coach) programs - Truck and Trailer, and modified apprenticeship programs - A...",
        "section": "Program Areas",
        "source_path": "departments/6_school_of_transportation.md",
        "url": "https://www.centennialcollege.ca/about-centennial/schools/school-of-transportation/"
      },
      {
        "title": "Program Offerings and Credentials",
        "excerpt": "### School of Transportation - **Automotive:** Automotive Parts & Service Operations; Auto Body Repair Techniques; Auto Body Repair Technician; Automotive Service Technician (including pre-apprenticeship and OEM-partnered streams with Canadian Tire, Ford/ASSET...",
        "section": "School of Transportation",
        "source_path": "programs/centennial_programs (1).md",
        "url": "https://www.centennialcollege.ca/programs-and-courses"
      }
    ]
  },
  "message": "Query processed successfully",
  "error": null
}
```

---

## Test 5 — School of Community and Health Studies Programs

### Request

```json
{
  "context": "Looking into healthcare careers",
  "query": "What programs are offered in the School of Community and Health Studies?"
}
```

### Response

```json
{
  "success": true,
  "data": {
    "answer": "In the School of Community and Health Studies at Centennial College, you can find a variety of programs that prepare students for careers centered on caring for and supporting others. Here are some of the programs available:\n\n- Pharmacy Technician\n- Paramedic\n- Nursing\n- Massage Therapy\n- Food and Nutrition\n- Esthetician\n- Occupational Therapist Assistant and Physiotherapist Assistant\n- Medical Laboratory Technician\n- Early Childhood Education\n- Social Service Work\n- Child and Youth Care\n- Community Development\n- Recreation and Leisure Services\n- Workplace Wellness and Health Promotion (one of the first programs in Canada, focusing on wellness coaching, health risk assessment, and workplace/community health promotion strategy)\n- A number of liberal arts and pre-health preparatory programs\n\nThese programs cover both health-focused and social/community-focused fields.",
    "confidence": 0.75,
    "sources": [
      {
        "title": "School of Community and Health Studies",
        "excerpt": "# School of Community and Health Studies The School of Community and Health Studies (SCHS) prepares students for careers centred on caring for and supporting others, spanning both health-focused and social/community-focused fields.",
        "section": "School of Community and Health Studies",
        "source_path": "departments/3_school_of_community_and_health_studies.md",
        "url": "https://www.centennialcollege.ca/about-centennial/schools/school-of-community-and-health-studies/"
      },
      {
        "title": "School of Community and Health Studies",
        "excerpt": "## Program Areas The School's programs include: - Pharmacy Technician - Paramedic - Nursing - Massage Therapy - Food and Nutrition - Esthetician - Occupational Therapist Assistant and Physiotherapist Assistant - Medical Laboratory Technician - Early Childhood ...",
        "section": "Program Areas",
        "source_path": "departments/3_school_of_community_and_health_studies.md",
        "url": "https://www.centennialcollege.ca/about-centennial/schools/school-of-community-and-health-studies/"
      },
      {
        "title": "Program Offerings and Credentials",
        "excerpt": "### School of Community and Health Studies - Addiction and Mental Health Worker (Diploma, 2 yrs) - Child and Youth Care (Advanced Diploma, 3 yrs) - Community and Child Studies Foundations (Certificate, 1 yr) - Community and Justice Services (Diploma, 2 yrs) - ...",
        "section": "School of Community and Health Studies",
        "source_path": "programs/centennial_programs (1).md",
        "url": "https://www.centennialcollege.ca/programs-and-courses"
      },
      {
        "title": "Program Offerings and Credentials",
        "excerpt": "### Culinary and Hospitality Programs - **School:** Hospitality, Tourism and Culinary Arts (Progress Campus) - Hands-on training in specialized culinary labs, supporting careers in culinary arts, hotel operations, and tourism management.",
        "section": "Culinary and Hospitality Programs",
        "source_path": "programs/centennial_programs (1).md",
        "url": "https://www.centennialcollege.ca/programs-and-courses"
      }
    ]
  },
  "message": "Query processed successfully",
  "error": null
}
```
