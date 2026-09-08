# Resume and Career Intelligence Repository

A structured, evidence-based repository for managing Gabriel Carneiro's master LaTeX resume, tailoring resumes for Applicant Tracking Systems (ATS), maintaining a verified achievement bank, and preparing for technical interviews.

***

## Repository Architecture

```text
├── main.tex                 # Master two-page LaTeX resume (do not edit directly for applications)
├── achievements/
│   ├── ACHIEVEMENTS.md      # Verified accomplishment bank in Google's XYZ formula
│   ├── EVIDENCE.md          # Git commit scopes, file touches, and interview defense material
│   ├── QUESTIONS.md         # Open questions and pending metric confirmations
│   └── README.md            # Achievement bank index and metrics summary
├── interview/
│   └── STAR-ANSWERS.md      # Structured behavioral and technical interview responses
├── tailored/                # Output directory for company-specific .tex and .pdf resumes
├── .agent/
│   └── skills/
│       ├── resume-ats-optimizer/  # Evaluates ATS keyword match and scores job descriptions
│       └── tailor-resume/         # Generates tailored resumes without altering the master
└── .gitignore               # Ignores LaTeX build artifacts and output PDFs
```

***

## Core Principles

1. **Never Fabricate:** Tailoring surfaces, reorders, and rewires verified achievements to match the job description vocabulary. It never invents skills, tools, or metrics.
2. **Business Outcomes over Activity:** Resume bullets strictly follow Google's XYZ formula (*Accomplished [X] as measured by [Y] by doing [Z]*). Commits, lines of code, and file touch numbers belong in [EVIDENCE.md](file:///home/gacar/resume/achievements/EVIDENCE.md) for interview context, never as resume metrics.
3. **Transparent Boundaries:**
   - **Production Fullstack:** 3+ years professional fullstack experience at Full Cycle with Python, Django, PHP/Symfony, PostgreSQL, and server-rendered interfaces (Twig, Django templates, SCSS, AJAX).
   - **Personal Deployed Projects:** Modern component frameworks (React 19, Vite, NestJS, FastAPI) are demonstrated via live, deployed production projects ([DevATS](https://findjobs.gabrielcjr.website), [ATSProof](https://atsproof.website), [AMAE](https://amae.gabrielcjr.website)).
   - **Real Gaps:** Hard requirements like Go, Java/Spring Boot, or Kafka are treated as real gaps and never papered over.
4. **Writing Style:** No em dashes or en dashes in generated resumes or recruiter communications.

***

## How to Use

### 1. Compiling the Master Resume

The master resume is written in standard LaTeX. To compile locally:

```bash
pdflatex main.tex
```

Or using `latexmk`:

```bash
latexmk -pdf main.tex
```

### 2. Evaluating a Job Description (ATS Score & Gap Analysis)

Use the `/resume-ats-optimizer` skill with the job description text or link:

```text
/resume-ats-optimizer <Job Description Text or URL>
```

This will:
- Parse technical must-haves and soft skills.
- Score current [main.tex](file:///home/gacar/resume/main.tex) against the posting.
- Classify gaps as **Coverable** (available in the achievement bank or projects) or **Real** (missing across the entire repository).
- Provide an achievable score after tailoring.

### 3. Tailoring for a Specific Application

Use the `/tailor-resume` skill to build a per-application copy:

```text
/tailor-resume <Job Description Text or URL>
```

This will:
1. Select relevant bullets from [ACHIEVEMENTS.md](file:///home/gacar/resume/achievements/ACHIEVEMENTS.md).
2. Tune the summary and skills lines to mirror the target company's vocabulary.
3. Generate and compile a new version into the `tailored/` folder:
   - `tailored/<Company> - Resume Gabriel Carneiro.tex`
   - `tailored/<Company> - Resume Gabriel Carneiro.pdf`
4. Leave [main.tex](file:///home/gacar/resume/main.tex) untouched.

### 4. Technical Interview Preparation

- **Behavioral Questions:** Check [interview/STAR-ANSWERS.md](file:///home/gacar/resume/interview/STAR-ANSWERS.md) for pre-structured answers (Situation, Task, Action, Result) mapped directly to bank achievements.
- **Defending Metrics:** Check [achievements/EVIDENCE.md](file:///home/gacar/resume/achievements/EVIDENCE.md) for verified git commit hashes, file-touch ratios, and technical trade-offs behind each result.
