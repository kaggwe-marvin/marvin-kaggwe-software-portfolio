# AI Instructions (Personal)

This folder contains reusable prompts and templates I use to quickly adapt my CV to different job descriptions.

## Quick start
1. Copy the target job description into `cv/99-job-description-template.md`.
2. Run the prompts in order:
   - `01-analysis-scorecard.prompt.md`
   - `02-rewrite-google-xyz.prompt.md`
   - `03-ats-tired-manager.prompt.md`
3. Apply the final edits to `CV.md`.
4. (Optional) Pull relevant modules from `10-coursework-bank.md` into the Education section when the role needs it.
# How to use these CV prompts

## Inputs you provide each time
- The **Job Description** (JD)
- Your current **CV.md**
- (Optional) a **target role title** and **country/location** (for tone and norms)

## Output standard
- Keep results in Markdown.
- Avoid fluff; prefer measurable outcomes.
- Do not invent experience, employers, dates, or credentials.
- If something is missing, suggest a truthful alternative (project-based evidence, coursework, or skills).

## Suggested workflow
1. **Score & gaps**: run `01-analysis-scorecard.prompt.md`
2. **Rewrite**: run `02-rewrite-google-xyz.prompt.md`
3. **ATS + skim test**: run `03-ats-tired-manager.prompt.md`
4. Final pass: spelling, consistency, dates, formatting, links.
# Prompt 01 — Recruiter match scorecard (company-specific)

Act as a **senior recruiter for this exact company**.

## Input
You will be given:
1) A **Job Description**  
2) My **CV**

## Task
Analyze my CV against the job description and return:

1. **Match score (0–100)** with a short explanation (3–6 bullet points).
2. **Top 5 missing keywords/skills** that are important for ATS + hiring manager alignment.
3. **Top 3 red flags you’d notice in under 3 seconds** (the immediate skim test).
4. **Top 5 strongest matches** (keywords, accomplishments, or experiences that align well).
5. **Role level assessment**: is this CV presenting me as junior / mid / senior for this JD? Explain why.

## Rules
- Be strict and realistic (like a recruiter screening 200 resumes).
- Prefer keywords that appear in the JD (or are clearly implied).
- Do not recommend adding anything untrue.
- If the JD is missing info (e.g., no tech stack), say what you inferred and what you cannot infer.

## Output format
### Match score
### Missing keywords (top 5)
### Red flags (top 3)
### Strong matches (top 5)
### Level assessment
# Prompt 02 — Rewrite CV to fit JD (Google XYZ + remove red flags)

You are a **senior technical recruiter + hiring manager**.

## Input
You will be given:
1) Job Description
2) Current CV
3) (Optional) extra coursework and skills bank

## Task
Rewrite my CV to better match the JD while remaining truthful.

### Must do
- Incorporate the **missing keywords** identified in Prompt 01 where they truthfully apply.
- Remove or reduce the **red flags** from Prompt 01.
- Apply **Google XYZ formula** in bullet points where possible:
  - "Accomplished **X**, measured by **Y**, by doing **Z**."
- Improve **ATS compatibility**:
  - Use standard headings: Summary, Skills, Experience, Projects, Education, Certifications.
  - Avoid tables and complex formatting.
- Keep it to **1 page** if possible; **max 2 pages** if absolutely necessary.
- Keep my location/contact details.
- Keep tone: confident, concise, technical.

### If metrics are missing
- Do NOT invent numbers.
- Suggest realistic, honest measurement options in [brackets] like:
  - `[add metric: bookings per week]`, `[add metric: uptime]`, `[add metric: latency]`

## Output format
Return the full rewritten CV in Markdown.
# Prompt 03 — ATS filter + tired hiring manager skim test

Act as:
1) An **ATS parser**, and
2) A **tired hiring manager** reading **200 resumes** in one sitting.

## Input
You will be given:
- Job Description
- The *new* rewritten CV

## Task
1. **ATS parsing check**
   - Identify sections that may parse poorly (non-standard headings, formatting issues).
   - Identify missing or weak keyword coverage.

2. **Skim/stop-the-scroll check**
   - Tell me what will get skipped in a 6–10 second scan.
   - Identify the first 3 things you notice (good or bad).
   - Rewrite the most skippable sections so they "stop the scroll".

## Output format
### ATS risks
### Skim test (6–10 seconds)
### Sections likely skipped
### Rewrites to stop the scroll (provide improved text)
# Coursework bank (Education add-ons)

Use this as a copy/paste bank when a job description requires more academic detail.

## Bachelor of Business Computing — Makerere University Business School (MUBS)

### Year 1
**Semester 1**
- Principles of Accounting
- Business Administration
- Principles of Information Communication Technology
- Business Communication Skills

**Semester 2**
- Programming Principles for Business
- Business Software Application
- ICT Fundamentals
- Principles of Economics
- Principles of Marketing

### Year 2
**Semester 1**
- System Analysis and Design
- Computerized Accounting
- Software Modeling for Business
- Financial Management

**Semester 2**
- Programming in Java or Oracle (Oracle option)
- Information Systems Development and Management
- E-business and Web Designing
- Computerized Investment Appraisal
- Business Law
- Business Statistics

### Year 3
**Semester 1**
- Strategic Management
- Enterprise Network Administration and Management
- Research Methods
- Human Resource Management
- Corporate Database Management

**Semester 2**
- ICT and Corporate Transformation
- Business Software Engineering
- Entrepreneurship Development
- Business Ethics
- Project Report
