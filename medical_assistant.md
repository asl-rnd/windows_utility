# 📅Project Development Timeline (AI Engineering and Backend Dev)

## Process Diagram
![Process Diagram of the Project](medical_assistant(flow_diagram).png)

### Week 1–2 → Analysis & Design
- **AI Engineering (Me):**
    - Decide AI pipeline (Textract/GPT/Embeddings).
    - Define input/output contract (what JSON you’ll return from AI).
    - Estimate GPT/OCR costs.
- **Backend Dev:**
    - Finalize DB schema (Users, Visits, Medications, Tests, Reports).
    - Define Flask API routes (upload, search, retrieval).
    - Set up Postgres locally (or in Docker).

### Week 3–6 → Development (Core MVP)
- **AI Engineering (Me):**
    - Build pipeline:
        - PDF → image → Textract OCR → raw text.
        - GPT-4.1 → structured JSON.
        - Embeddings (OpenAI `text-embedding-3-small`) for search.
    - Write Python functions that return clean JSON.
    - Provide backend dev with Python module (AI engine).
- **Backend Dev:**
    - Implement user authentication (Flask + JWT). 
    - File upload API (save to S3 or local). 
    - Integrate your AI engine → call your functions. 
    - Insert structured JSON into Postgres.
    - Create endpoints for retrieving reports, meds, tests.
    - Build simple Jinja2 templates (upload form, timeline view).

### Week 7–8 → AI Assistant
- **AI Engineering (Me):**
    - Build retrieval pipeline:
        - Query → vector DB (FAISS) → fetch context → GPT answer.
    - Deliver as callable Python class/module to backend.
- **Backend Dev:**
    - Expose `/ask` API endpoint.
    - Connect your Q&A engine to endpoint.
    - Add simple chat UI (Flask + Jinja form).

### Week 9–10 → UI/UX + Notifications
- **AI Engineering (Me):**
    - Expose API for providing structured test data (for charts).
    - Suggest reminder logic rules (e.g., repeat tests every 6 months).
- **Backend Dev:**
    - Build APScheduler jobs for reminders.
    - Implement email/SMS integration.
    - Add chart API → pass to frontend templates (Chart.js).

### Week 11–12 → Pilot Launch
- **AI Engineering (Me):**
    - Optimize GPT prompts & OCR accuracy.
    - Document usage (how backend should call your AI functions).
- **Backend Dev:**
    - Deploy Flask app on local Linux server (Gunicorn + Nginx).
    - Secure Postgres, set up backups.
    - Onboard test users.
---
### 👥Recap Project Roles
<table border="1" cellpadding="8" cellspacing="0" style="border-collapse:collapse; width:100%;">
  <thead>
    <tr>
      <th style="text-align:left; width:50%;">AI Engineering (Me)</th>
      <th style="text-align:left; width:50%;">Python Backend Dev</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>OCR (AWS Textract) integration — PDF→image pipeline, calling Textract, parsing responses</td>
      <td>Flask API & authentication (JWT / Flask-Login)</td>
    </tr>
    <tr>
      <td>GPT-4.1 structuring — prompt design, error handling, JSON output normalization</td>
      <td>File upload endpoints (accept files, store to local/S3, metadata)</td>
    </tr>
    <tr>
      <td>Embeddings generation (OpenAI embeddings) and FAISS index creation/maintenance</td>
      <td>Postgres database integration (schema, ORM, migrations)</td>
    </tr>
    <tr>
      <td>Semantic search / retrieval pipeline — query → FAISS → context assembly</td>
      <td>Merge/integrate AI module into backend (call your functions, handle responses)</td>
    </tr>
    <tr>
      <td>Q&A assistant logic (construct prompts with context, refine answers)</td>
      <td>API endpoints for retrieval/search/chat (expose `/ask`, `/reports`, `/timeline`)</td>
    </tr>
    <tr>
      <td>Preprocessing & postprocessing utilities (pdf2image, image cleanup, text cleaning)</td>
      <td>Notifications & scheduling (APScheduler/Celery jobs, trigger reminders)</td>
    </tr>
    <tr>
      <td>Testing & validation of AI outputs (accuracy checks, unit tests for AI funcs)</td>
      <td>Deployment & ops on local server (Gunicorn/Nginx or Docker), backups</td>
    </tr>
    <tr>
      <td>Documentation for AI module (function signatures, expected inputs/outputs, error codes)</td>
      <td>Logging, monitoring, and security (access control, DB backups, logs)</td>
    </tr>
    <tr>
      <td>Optimize prompts & cost management (token reduction, batching, retry logic)</td>
      <td>Frontend integration points (provide API contracts to frontend / Jinja templates)</td>
    </tr>
  </tbody>
</table>

### 💰API Costing (Pilot Scale)
- **Textract:** ~$1.50 per 1,000 pages.
- **GPT-4.1:** ~$0.03 per report (2 pages).
- **Embeddings:** negligible (<$1 for pilot).<br>
    👉 Pilot (100 reports/month): ~$5–10.<br>
    👉 Medium (1,000 reports/month): ~$30–50.

---