---
name: tailor-resume
description: Tailor the LaTeX resume (main.tex) to a specific job description for maximum ATS keyword match, producing a per-application copy without modifying the master. Use when the user supplies a job posting/description and asks to tailor, customize, target, or ATS-optimize their resume for it.
user-invocable: true
allowed-tools:
  - Read
  - Write
  - Edit
  - Glob
  - Grep
  - Bash
  - WebFetch
---

# /tailor-resume — ATS-targeted resume tailoring

Tailors `main.tex` to one job description and produces a compiled, per-application PDF.

Arguments passed: `$ARGUMENTS` (job description text, a path to a file containing it, or a job posting URL).

---

## The one rule that overrides everything

**Never fabricate.** Tailoring means *surfacing, reordering, and rewording things that are already true* — never inventing them.

Forbidden, no exceptions, even if the user asks:
- Adding a technology, framework, or tool Gabriel has not actually used
- Inventing or inflating metrics, percentages, team sizes, or scale figures
- Changing employers, job titles held, or employment dates
- Claiming seniority, certifications, or degrees not held
- White-text/invisible keyword stuffing, hidden divs, off-page text, or repeating keywords in ways a human reader would find absurd

Modern ATS pipelines flag stuffing, and recruiters read the PDF. A resume that wins the keyword scan and collapses in the screening call is a net loss.

**Attribution rules — four bank entries were withdrawn for violating these:**
- **Never claim ownership from commit volume alone.** Check who *created* the code and how
  Gabriel's contribution compares to the other contributors. Being the top committer on a
  repository is not the same as owning a feature.
- **Never filter git history by the name "Gabriel."** Two engineers named Gabriel worked in
  these repositories. Gabriel Carneiro is `gacarneirojr@hotmail.com`; Gabriel Caetano is
  `98gabrielsc@gmail.com`.
- **Never claim a delivered outcome for work that did not ship.** His contract ended July 2026;
  the Symfony migration was never deployed. Say "remediation", not "completed the migration".

**Never restate years of experience to match a JD's threshold.** Gabriel has 5+ years in
tech, the last 3+ backend-focused in Python, PHP, and TypeScript.

- **True and usable:** 3+ years of professional **full-stack** work, server-rendered. His job
  title at Full Cycle was Full Stack Developer, and the front-end work is real: 712 Twig
  templates, 222 HTML files, 71 SCSS files, AJAX-driven filtering, dynamic dropdowns, modals,
  defensive loading and double-submit handling, SCSS through webpack. See the
  "FRONT-END AT FULL CYCLE" section of the bank.
- **Not true:** 3 years of professional **React**, Node.js, or component-framework SPA work.
  Those are real skills evidenced by deployed personal projects built in 2026.

If a JD gates on "N years of React" or "N years of Node", report it as a **real gap**. Do not
tailor around it. Use the full-stack framing where a JD wants full-stack breadth without
naming a framework, which is honest and often exactly what is being asked.

**Never use an activity number as a metric.** Commits, lines of code, files touched, and
models defined measure effort, not impact. A recruiter reads them as busywork. Valid metrics
are business outcomes: percent, dollars, time, volume. Activity numbers live in
`achievements/EVIDENCE.md` and are for interviews only. They may appear inside a *method*
clause ("across a 369,000-line codebase") but never as the result.

**Style:** no em dashes or en dashes in any user-facing text — Gabriel considers them an AI
tell. Use commas, colons, or parentheses.

**What you *can* do freely:** reorder, re-weight, re-word using the JD's exact vocabulary, choose which true bullets to include or cut, adjust emphasis, and expand on real work that the base resume compressed.

If the JD requires something genuinely missing, do not paper over it — report it as a gap (see Step 7).

---

## Step 1 — Get the job description

Resolve `$ARGUMENTS` in this order:
1. **Looks like a URL** → fetch it with WebFetch. If the fetch is blocked or returns a login wall (common for LinkedIn/Workday), ask the user to paste the text instead — do not guess at the posting's contents.
2. **Looks like a file path** → Read it.
3. **Looks like pasted JD text** → use it directly.
4. **Empty** → ask the user to paste the job description before doing anything else.

Also identify the **company name** and **exact job title**. If either is unclear from the JD, ask — both are needed for the output filename and for title alignment.

## Step 2 — Read the master and know the truth inventory

Read `main.tex` in full. It is the source of truth for what Gabriel has actually done.

**Then read `achievements/ACHIEVEMENTS.md` in full.** This is the achievement bank: every
verified accomplishment, including many that do not fit on the two-page master. It is the
primary source for bullet swapping and it is fair game for tailoring. Also read
`achievements/README.md` for the current state summary.

The bank's entries are labelled. Obey the labels:

| Label | Meaning | Use it? |
|---|---|---|
| **READY (R1-R12)** | Verified outcome metric, confirmed by Gabriel | **Yes** |
| **W14** | 75%, modeled from observed throughput, not measured | Yes, but say "modeled" if asked |
| **NO Y** (W1, W2) | Real work, no outcome metric available | Supporting bullet only, never a lead |
| **AWAITING Y** with a `[Y]` placeholder | Number not yet supplied | **Never.** Do not ship a placeholder. |
| **WITHDRAWN / MERGED** | Failed attribution, unshipped, or duplicated | **Never.** Read the reason before arguing with it. |
| **PERSONAL PROJECTS (P)** | Gabriel's own, three deployed | Projects section only |

Never treat a previous *tailored* copy as the truth inventory — those are already slanted toward a different job. Always start from `main.tex` plus the bank.

## Step 3 — Extract JD keywords

Build a keyword list from the JD, separating:
- **Hard requirements** — languages, frameworks, databases, cloud, tools, methodologies stated as required/must-have
- **Preferred / nice-to-have**
- **Domain & responsibility language** — e.g. "event-driven", "microservices", "distributed systems", "API design", "observability", "mentoring"
- **The exact job title** and any seniority framing

Record each keyword in the **JD's exact surface form**. ATS keyword matching is largely literal (with light stemming), not semantic: "REST API" and "RESTful API" may not match each other, and "K8s" may not match "Kubernetes". When Gabriel genuinely has the skill, use the JD's spelling — or carry both forms, e.g. `Kubernetes (K8s)`, `CI/CD (Continuous Integration/Continuous Deployment)`.

## Step 4 — Map keywords to real evidence

For each JD keyword, classify:

| Class | Meaning | Action |
|---|---|---|
| **Direct** | Already in `main.tex` verbatim | Keep; move it earlier if it's a hard requirement |
| **Equivalent** | Has the skill, different wording | Re-word to the JD's exact term |
| **Adjacent** | Real, demonstrable through related work | Surface it honestly, without overstating |
| **Missing** | No genuine basis | Do NOT add. Log for the gap report |

Do this mapping before editing anything — it drives every edit that follows.

## Step 5 — Write the tailored copy

**Never edit `main.tex`.** Copy it to `tailored/<Company> - Resume Gabriel Carneiro.tex`
(create `tailored/` if needed), then edit only the copy. That exact filename pattern is
Gabriel's convention — the recruiter sees the filename. If the company name is unknown, use
the role instead and tell him to rename it. Keep the preamble, macros, spacing, and overall layout of the template exactly as-is — it is already ATS-friendly (single column, text-based, no images, no multi-column tables, no critical info in headers/footers). Do not restructure it.

Tailor these sections, in this priority order:

**1. Skills block** — the densest keyword zone and the highest-leverage edit.
   - Reorder the seven categories so the ones the JD emphasizes come first.
   - Within each line, put JD-matching items first.
   - Re-word to the JD's exact terms wherever it's the same real skill.
   - Cut items irrelevant to this JD if space is tight — but only if they aren't transferable signal.
   - Never add a technology Gabriel hasn't used.

**2. Summary** — the second-densest zone, and where title alignment happens.
   - Open by aligning to the target title (e.g. if the JD is "Backend Engineer", lead as a backend engineer — this is a true framing of his last 3+ years, not a fabricated title).
   - Fold in the top 5–8 JD keywords naturally, in prose that still reads like a person wrote it.
   - Mirror the JD's domain language (e.g. "distributed systems", "event-driven architecture").
   - Keep it truthful about years of experience: 5+ years in tech, last 3+ backend-focused.
   - **The bank licenses claims the master's summary does not make.** These are all verified,
     so use them when the JD calls for them: **FastAPI** (ATSProof and Technical Challenge
     Reviewer, so it may go in a bullet, not just Skills), **LangChain**, **MCP** and
     **multi-agent workflows** (DevATS ADRs), **React and TypeScript** on the front end,
     **prompt-injection defense** and **multi-provider LLM failover** (ATSProof),
     **SDD and ADR** (DevATS, 5 and 5).

**3. Experience bullets** — reorder, select, and **swap in from the bank**; do not invent.

   **Swapping is the highest-value edit after Skills.** `main.tex` carries only what fits on
   two pages. When the JD emphasises something a bank entry covers better than a bullet
   currently on the master, swap it in and drop the weaker one. Rules:

   - Only **READY** entries (R1-R12) and **W14**. Never an `[Y]` placeholder, never a
     WITHDRAWN entry.
   - Each entry has several pre-written phrasings angled differently (backend, full stack,
     security, data, product/growth, integration, AI). Pick the one matching the JD's framing
     rather than rewriting from scratch.
   - Place the swapped bullet under **the role where the work actually happened**. The bank
     records dates; check them. Never move work between employers or roles to make it look
     more recent.
   - Lead with the largest Y that is *also relevant*. A relevant 15% beats an irrelevant 20x.

   **Some bank entries supersede the master's wording. Prefer the bank version.** The master
   was written before the achievement interview and a few of its bullets understate the work:

   | Master bullet | Bank version | Why the bank wins |
   |---|---|---|
   | "Cut manual administrative effort by 90%... diploma credential lifecycle" | **R7: reduced diploma issuance time by 85%, brought in-house** | The master describes an efficiency gain; the real story is that the company could not issue diplomas at all before, and stopped paying a partner university. A capability beats a percentage. |
   | "Prevented sales lead loss... with automatic retries" (no metric) | **R11: made 100% of failed CRM lead syncs recoverable** | The master version has no Y at all. |

   When an entry in the bank carries a note saying it supersedes or replaces a master bullet,
   follow it. The bank is newer and better evidenced than `main.tex`.

   **Mutual exclusions — never use both of a pair on one resume:**

   | Pair | Why | Prefer |
   |---|---|---|
   | R7 and W2 | Both read as "credentials/certificates" work | R7 (has a Y, and he originated it) |
   | R9 and R12 | Both are "made the Django admin faster" | R9 unless the JD stresses campaigns |
   | R1/R2 and any generic query-optimisation bullet | The vague one makes the specific ones look padded | R1 and R2 |

   Also: never place two `100%` bullets adjacent (R5, R6, R11). Space them across roles or
   drop one, or the set reads as rounding rather than measurement.
   - Within each role, lead with the bullets closest to the JD's responsibilities.
   - Re-word existing accomplishments in the JD's vocabulary while keeping every metric exactly as it is in the master.
   - Drop bullets irrelevant to this JD when trimming for length.
   - The italic **Context** paragraphs are useful keyword real estate and explain domain fit — keep them when they carry JD-relevant language, but they are the first thing to trim when cutting to fit.

**4. Projects** — flex this section per role. `main.tex` ships three: ATSProof (FastAPI, LLM
   integration), DevATS (NestJS, React, TypeScript), AMAE (Django, financial domain). All
   three are deployed with live URLs, which is the point: a recruiter can click.

   - **Reorder** so the most JD-relevant project comes first.
   - **AI or LLM role** → ATSProof leads. Consider adding *Technical Challenge Reviewer* from
     the bank (FastAPI + LangChain, multi-provider failover) if FastAPI or LangChain are
     required. It is not deployed, so mention no URL for it.
   - **Node / React / TypeScript role** → DevATS leads, and it earns a second line.
   - **Fintech or payments** → AMAE leads.
   - **Pure backend PHP or Python role, tight on space** → cut to two projects, or drop the
     section entirely to protect metric-bearing Experience bullets.
   - Keep every project to one or two lines. Personal projects are **supplementary** for a
     senior candidate: they must never displace a bullet that carries a business metric.
   - **Never move a personal project into the Experience section**, and never attribute one to
     Full Cycle.

**5. Education** — usually untouched. Reorder only if the JD emphasizes a specific credential.

**6. Header** — never change. Name and contact details stay exactly as-is.

**Length:** target ≤ 2 pages. Trim in this order: Context paragraphs → least-relevant bullets → oldest role's detail.

## Step 6 — Compile and verify

Compile the tailored copy, not the master:

```bash
PDFLATEX="/mnt/c/Users/gacar/AppData/Local/Programs/MiKTeX/miktex/bin/x64/pdflatex.exe"
cd /home/gacar/resume/tailored
"$PDFLATEX" -synctex=1 -interaction=nonstopmode -file-line-error <file>.tex 2>&1 \
  | grep -E "Overfull|Underfull|Error|Output written|Warning"
```

Environment notes for this machine (WSL):
- The project lives in WSL at `/home/gacar/resume`, but **there is no LaTeX installed inside WSL**. The only TeX is Windows MiKTeX, invoked through the `.exe` path above. `which pdflatex` returns nothing — that is expected, not a broken setup.
- Do **not** try `export PATH=.../miktex/bin/x64` and then run bare `pdflatex`. The directory is already on `$PATH`, and Node/shell resolution of the extensionless name fails with `EACCES`. Always call the full `.exe` path.
- MiKTeX resolves *Windows* paths, so pass a **bare filename** (`main.tex`, not an absolute WSL path) and rely on the working directory. `%DOCFILE%`, not `%DOC%`, in LaTeX Workshop config for the same reason.
- `latexmk` does **not** work here (MiKTeX ships no Perl); use `pdflatex` directly. VSCode's LaTeX Workshop is configured in `.vscode/settings.json` with a plain-`pdflatex` recipe pointing at the full `.exe` path.
- On-the-fly package installation is enabled, so missing `.sty` files self-resolve on first use.
- MiKTeX may print `pdflatex: major issue: So far, you have not checked for MiKTeX updates.` after a successful run. It is noise, not a build failure — check for `Output written on` instead.

Fix any `Overfull \hbox` warnings (usually an over-long heading — shorten the text rather than changing the macros), then recompile until the output is clean. Confirm the PDF was written and check the page count.

Optional sanity check that the PDF's text layer extracts cleanly (this is what an ATS sees):

```bash
"/mnt/c/Users/gacar/AppData/Local/Programs/MiKTeX/miktex/bin/x64/miktex-pdftotext.exe" \
  <file>.pdf - | head -60
```

Note the `miktex-` prefix: MiKTeX ships its poppler tools under that name, and there is no plain `pdftotext` on this machine. If it fails, skip the check — don't install anything for this.

## Step 7 — Report honestly

Report back:

1. **Output path** of the `.tex` and `.pdf`, and the page count.
2. **Coverage table** — each hard requirement from the JD → matched / not matched → where it now appears.
3. **Gaps** — every JD requirement with no genuine basis, stated plainly. This is the most valuable part of the report: it tells Gabriel what he'd be asked about, or whether the role is a stretch. Never quietly omit a gap because it looks bad.
4. **Bullets swapped** — which bank entries were pulled in, which master bullets were dropped
   to make room, and why. Two or three lines.
5. **Projects section** — which projects were kept, reordered, or cut, and why.
6. **Judgment calls** — any place a term was stretched to fit the JD's wording, so he can veto it.

Keep the report short and scannable. Do not restate the whole resume.

---

## Reference: what actually moves an ATS

- **Exact-term matching beats synonyms.** Match the JD's literal phrasing for real skills.
- **Both forms of acronyms** — spelled out and abbreviated — in at least one place.
- **Title alignment** is heavily weighted; the summary is the safe place to align without falsifying past titles.
- **Skills section density** carries most of the keyword score.
- **Parseability**: single column, real text, standard section headings (`Skills`, `Experience`, `Education`), no images, no text boxes, no critical info in headers/footers. This template already satisfies all of it — don't "fix" it.
- **Recency weighting**: keywords in the most recent role count more than in the oldest.
- What does *not* help: keyword stuffing, invisible text, tables of keywords, or padding the skills list with things he can't discuss in an interview.
