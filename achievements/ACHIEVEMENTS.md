# Achievement Bank

Every entry is written in **Google's XYZ format**: *"Accomplished [X] as measured by [Y] by doing [Z]."*

- **X** = the outcome, not the task
- **Y** = the number that proves it, and it must be a **business outcome**: percent, dollars, time, or volume
- **Z** = the method that got you there

`main.tex` already follows this pattern. This bank extends it.

## Why Y matters

| Finding | Source |
| --- | --- |
| 58% of recruiters say measurable achievements are what make a resume stand out most | Jobscan |
| Quantified resumes get 2.5x more interview invitations | LinkedIn Talent Report 2023 |
| Quantified resumes get 40% more callbacks, 40% more likely to shortlist | TalentWorks 2023 |
| 75% of hiring managers want achievements over duties | high5test 2024 |
| Only 26% of resumes contain 5+ measurable results | Jobscan analysis |

## What counts as Y, and what does not

| Valid Y (outcome) | Invalid Y (activity) |
| --- | --- |
| 20x faster response time | 1,351 commits |
| 80% lower query latency | 369,000 lines of code |
| 90% less manual effort | 716 files touched |
| 100% of a cost eliminated | 203 test files |
| $X/month saved | 91 Django models |
| 15% performance gain | 3rd highest committer |

Activity numbers are not resume material. They are kept in `EVIDENCE.md` because they are
useful for interview conversation and for proving scope when someone asks, but they never
go in a bullet.

## Status legend

- **READY** — complete XYZ. Outcome metric confirmed by Gabriel. Usable today.
- **AWAITING Y** — X and Z are verified and drafted; the outcome number is missing.
  Gabriel supplies Y and the bullet is ready. See `QUESTIONS.md`.

---

# READY (10)

These are the bullets currently earning their place. All confirmed by Gabriel.

### R1. 20x endpoint response time
**Y = 20x** | PHP, Symfony, Doctrine

- *Backend:* Decreased an endpoint's response time by 20x by identifying the root cause of a pagination query bug in a production PHP/Symfony service and shipping an immediate fix.
- *Performance:* Cut a production endpoint's response time 20x by root-causing and fixing a pagination query defect.

### R2. Up to 80% lower query latency
**Y = up to 80%** | PHP, Symfony, Doctrine

- *Backend:* Reduced student news-feed query latency up to 80% by caching complex multi-join chapter-release queries with a custom parameter-based Doctrine result-caching layer.
- *Scalability:* Improved scalability under load, cutting query latency up to 80%, by designing a parameter-keyed result cache over complex multi-join relational queries.

### R3. 15% server performance gain
**Y = 15%** | Python, Django

- *Backend:* Accomplished a 15% increase in server performance by performing runtime, framework, and dependency upgrades to a production Python/Django sales application.
- *Platform:* Gained 15% server performance on a production Django application through runtime, framework, and dependency modernization, with no regression in availability.

### R4. 20% faster CI/CD feedback
**Y = 20%** | Python, pytest-xdist, Docker

- *DevOps:* Reduced CI/CD pipeline feedback time by 20% by parallelizing test execution with the Python pytest-xdist library in Docker.
- *Quality:* Tightened the quality feedback loop 20% by parallelizing the test suite in Docker.

### R5. 100% of wasted LLM token spend eliminated
**Y = 100%** | Python, Django

- *AI:* Cut 100% of unwanted LLM API token consumption on disabled courses by engineering granular feature flags in Python/Django with admin controls and conditional rendering.
- *Cost:* Eliminated 100% of wasted AI API spend by shipping per-course feature flags gating LLM-backed replies behind an admin toggle.

### R6. 100% of manual challenge evaluation eliminated
**Y = 100%** | PHP, Symfony, webhooks

- *AI:* Eliminated manual work 100% by developing an AI feature that automates challenge evaluation, integrating a Symfony webhook with an AI-powered microservice.
- *Automation:* Removed a fully manual grading process by wiring an event-driven webhook integration to an AI-powered microservice.

### R7. 85% faster diploma issuance, brought in-house
**Y = 85% (time to issue)** | PHP, Symfony
**Verified originator:** first commit creating `DiplomaBook` and `DiplomaRegistry` is his (2024-07-19); top contributor (78 file-touches). Co-built with Gabriel Caetano (41). **Not** the same subsystem as W2.
**What it is:** a digital diploma registry book meeting Brazilian institutional requirements: sequential pages, `registry_code`, `publication`, issue/conclusion/graduation dates, a named responsible party with CPF, formal book closure, and cancellation with audit. This is what allowed the company to issue diplomas as the institution itself instead of routing every diploma through a partner university (integrated separately as `Tecfy`, built mostly by another engineer).

**Three wins, all confirmed by Gabriel:** capability (the company could not issue diplomas itself before), time (85% faster), and cost (a per-diploma fee to the partner, eliminated).

- *Primary, time as Y (USE THIS):* Reduced diploma issuance time by 85% by building an in-house diploma registry and issuance system in PHP/Symfony, replacing a manual process routed through a third-party university issuer.
- *Capability framing:* Enabled the company to issue its own diplomas for the first time, cutting issuance time 85%, by building a compliant digital diploma registry with sequential registration, formal book closure, and cancellation auditing.
- *ON RESUME (superseded, weaker):* Cut manual administrative effort by 90% with a PHP/Symfony API, automating the diploma credential lifecycle with comprehensive domain validation.
- *Short:* Cut diploma issuance time 85% by bringing issuance in-house with a compliant PHP/Symfony diploma registry system.

**Cost angle, deliberately unused:** roughly R$1,000 per certificate paid to the partner. Total annual volume is unknown and Gabriel cannot confirm it, so no currency figure goes on the resume. If the volume is ever recovered and annual savings clear ~R$100k (~US$18k), reconsider leading with money instead of time.

> This bullet replaces the "90% manual administrative effort" version. The 85% time
> reduction is the better Y, and "brought issuance in-house" is a far stronger X than
> "automated a lifecycle". Do not use both R7 and W2 on the same resume.

### R8. 90% less manual sync-recovery effort
**Y = 90%** | PHP, Symfony, HubSpot API

- *Integration:* Cut manual sync-recovery effort 90% by building a PHP/Symfony HubSpot integration manager that auto-lists failed payment syncs with one-click retries.
- *Reliability:* Shortened incident recovery on a third-party CRM integration 90% by making every failed sync visible, diagnosable, and retryable from the admin UI.

### R9. 90% faster page section setup for the marketing team
**Y = 90%** | Python, Django
**Verified sole author:** every `DuplicateSection` commit in the repository is his (May 2025).
**Basis for Y (interview only, never in the bullet):** marketing created each section and every related item by hand in the Django admin, ~30 min; one-click cloning brought it to ~2 min. Arithmetic is 93%; 90% is the conservative figure used.

- *ON RESUME:* Accomplished a 90% acceleration in page section setup by engineering reusable Python/Django admin mixins, enabling instant deep-cloning of multi-relational sections.
- *Beneficiary named:* Cut the marketing team's page section setup time by 90% by engineering a reusable Django admin deep-clone for multi-relational sections and their related items.
- *Short:* Reduced marketing's page section setup time 90% with a one-click Django admin deep-clone of multi-relational sections.

### R10. 5 classes of exposed entry points removed, plus transport hardening
**Y = 5 classes** | Python, Django, Nginx, Kubernetes ingress
**Verified sole author:** three commits, 2026-06-19 (`chore: harden nginx config and tighten .dockerignore`, `fix: refine nginx hardening per review`, `feat: trust ingress TLS and secure cookies in prod`).

**DATE CORRECTION — ACT ON THIS.** `main.tex` files this bullet under **Backend Developer,
June 2023 to June 2024**. The work is dated **2026-06-19**, which belongs under
**Full Stack Developer, July 2025 to July 2026**. There is no earlier bot-blocking Nginx
work by Gabriel in any of the three repositories. Move the bullet up two job entries.

**W9 merged in.** The "production TLS and transport hardening" entry was the same work.
There is only one Nginx security achievement, not two.

What the config actually does:
- `server_tokens off` (stops leaking the Nginx version), `client_max_body_size 10m`
- Security headers: `X-Content-Type-Options: nosniff`, `X-Frame-Options: SAMEORIGIN`, `Referrer-Policy: strict-origin-when-cross-origin`
- Five deny classes: dotfiles (`.git`, `.env`, `.aws`, with `.well-known` kept reachable), source/config/backup extensions (`.bak`, `.sql`, `.key`, `.pem`), build/dependency filenames (`composer.json`, `package-lock.json`, `requirements.txt`, `Dockerfile`), CMS scanner paths (WordPress, phpMyAdmin), and `.php` entirely
- `autoindex off` on `/static` — it had been **on**, exposing a directory listing
- Django: `SECURE_PROXY_SSL_HEADER`, plus `SESSION_COOKIE_SECURE` and `CSRF_COOKIE_SECURE` outside DEBUG
- Tightened `.dockerignore` to shrink the build context

- *ON RESUME (accurate, just misfiled):* Removed 5 classes of exposed entry points, config, backup, source, dependency, and CMS-exploit paths, from a Python/Django app's public attack surface by blocking automated bot probes at the Nginx gateway.
- *Fuller version:* Removed 5 classes of exposed entry points from a production Python/Django app's public attack surface, and enforced HTTPS-only session and CSRF cookies behind Kubernetes ingress TLS, by hardening the Nginx gateway with deny rules, security headers, and version suppression.
- *Short:* Removed 5 classes of exposed entry points from a production Django app's attack surface via Nginx gateway hardening.

> **Interview gold:** he deliberately declined per-IP rate limiting, documenting that public
> sales pages draw many legitimate buyers sharing one corporate NAT IP, and pushed
> brute-force protection to the application layer instead. He also anchored the CMS-scanner
> regex with `(/|$)` so marketing slugs like `/wp-admin-do-curso/` are not blocked. Being
> able to explain a control you chose *not* to add, and why, reads as senior judgment.

### W1. Always-on worker pod eliminated
**Status:** NO Y BY DESIGN. Use as a supporting bullet, never a lead. | PHP, Symfony, Kubernetes
**Verified sole author:** 14 commits, Feb 2025 (`CursoAdminController` report-progress action, `getStudentContentProgress` repository methods, ROLE_ADMIN authorization, feature tests).
**Y considered and rejected:** roughly 1 of 13 pods (~8%), idle most of the time. Gabriel is not confident in the count, and 8% is weak beside the 20x / 90% / 100% bullets. Do not use it.

- *ON RESUME (keep as-is):* Cut infrastructure costs by eliminating an always-on worker pod, building a PHP/Symfony API that serves student-progress data on demand.
- *Architecture framing (preferred):* Replaced a permanently running worker pod with an on-demand PHP/Symfony API, removing idle compute cost from the student-progress workload.
- *Short:* Eliminated an always-on worker pod by serving student-progress data through an on-demand API.

> The value here is the architectural judgment, replacing a standing process with an
> on-demand endpoint, not the magnitude. It reads well without a percentage and invites a
> good interview conversation. Adding an uncertain 8% would weaken it and expose it to
> probing.

### W2. Billing delinquency management program
**Status:** NO Y AVAILABLE. Gabriel does not know the collections outcome and it is not recoverable from git. Keep as a domain-signal bullet; never a lead. | PHP, Symfony, Doctrine
**Verified top contributor:** 51 commits, 26 of them his vs. Euller (12) and Isac (9), Dec 2025 to Apr 2026. His most recent substantial work.

Branches merged: `feature-expand-billing-delinquency-management`, `feature-defaulters-consolidated-report` plus three follow-ups (active/inactive split, by course finish date, improvements), `feature-classroom-filter-delinquency-report`, `feature-certificate-request-overdue-column`.

Scope built: consolidated defaulters report with paid and overdue amounts and overdue invoice counts; overdue awareness report with classroom selection over AJAX; an endpoint returning classrooms with overdue invoices; overdue invoice counts on the sales summary report; per-product overdue calculation for students holding more than one product; and a financial-standing panel (Inadimplente/Adimplente plus a pending-installments table showing installment number, amount, and due date) rendered directly above the approve button on the certificate request review screen.

- *Domain framing (preferred):* Built a billing delinquency management suite in PHP/Symfony, delivering consolidated defaulters reporting, overdue awareness reports by classroom, and per-product overdue calculation, giving the finance team a live view of outstanding revenue that replaced manual spreadsheet tracking.
- *Decision-support framing:* Put student financial standing and outstanding installments directly on the certificate approval screen, so reviewers could see delinquency at the point of decision instead of checking a separate system.
- *Short:* Built consolidated defaulters and overdue-awareness reporting for the finance team, covering delinquency across products, classrooms, and enrollment status.

**Why no Y:** the collections outcome (recovery rate, revenue recovered, staff time saved) was never measured and Gabriel cannot recall it. Commits prove what was built, never how much it moved. Do not invent one.

**Absorbed:** the former certificate-subsystem entry (W2) and the certificate financial gating were folded in here. The `CertificateRequest` workflow itself was originated by another engineer (Isac Sousa, Mar 2024); Gabriel is its largest contributor but not its author, so no ownership claim is made. Credentials are carried by **R7** instead. Do not use R7 and W2 as two separate credential bullets.

> Value on a resume: this is revenue-facing vocabulary (billing, delinquency, defaulters,
> outstanding balances, installments, collections) and it is recent. Use it for fintech and
> payments roles, where the domain match matters more than the missing percentage.

### W3. WITHDRAWN — Payments, invoicing, and enrollment orders
**Status:** REMOVED after attribution check on 2026-08-31. Do not use.

On the payments core (`Fatura`, `Checkout`, `Payment`, `Sale`, `Contract`), Gabriel is
**fifth of eight contributors**: Euller (1,123 file-touches), Isac (1,067), Silas (860),
Luiz (731), Gabriel Carneiro (631). The `EnrollmentExtension` entities were created by
Isac Sousa (2025-05-14); Gabriel has 16 commits on them.

631 touches is genuine contribution, but any bullet claiming he built or owned the payment
and invoicing domain would repeat the W7 error. Four engineers did more.

**Use W2 instead.** The billing delinquency program is where his payments claim is
defensible: top contributor on a named initiative, and it carries the same domain
vocabulary (billing, invoices, installments, outstanding balances, defaulters).

### W4. MERGED INTO W2 — Operational reporting suite
**Status:** absorbed. Do not use as a separate bullet.

Gabriel is second of six on report files (189 file-touches to Isac's 246), but the bulk of
his reporting work *is* the delinquency program already captured in **W2**: the defaulters
consolidated report and the overdue awareness report. A separate reporting bullet would put
the same work on the resume twice.

Genuinely distinct but unremarkable and metric-free, mention only if a JD is reporting-heavy:
enrollment cancellation tracking filtered by period and situation (May 2026), and the
students-by-classroom report with contact details and certificate status.

Also his: `ReportRepository` query decoupling, subquery optimization of
`getDefaultersConsolidatedReport`, and `ReportConstants` extraction, which are craft signals
rather than achievements.

### W14. AI agent tooling for a legacy framework migration
**Needs:** Y from Gabriel (see below). | Claude Code skills, PHP, Symfony
**Verified:** top contributor to `.claude/skills/` (60 file-touches to Isac's 42); **created 7 of the 12 committed skills**: `audit-config-sf4`, `audit-entities-sf4`, `audit-listeners-sf4`, `audit-migrations-sf4`, `audit-repositories-sf4`, `audit-twig-sf4`, `validate-forms-browser`. Co-built with Isac Sousa (June 2026).

Purpose-built AI agent tooling to drive the Symfony 4.4 / PHP 8.1 migration (**W6**): a suite
of audit skills covering config, entities, controllers, repositories, listeners, services,
forms, commands, migrations, twig, and security, plus browser-based form validation and an
end-to-end upgrade validator.

Telling commits: *"add skills and reports for config, entities, repositories and migrations
code validation"*, *"update twig skill to admit twig extensions"*, and
*"calibrate skills to reflect real blocking situations"* — that last one is the substance of
the claim, since tuning agents to surface genuine blockers instead of noise is the hard part
of making them useful on a large codebase.

**Y = 75% (modeled, not measured — see basis below)**

- *Primary (USE THIS):* Cut framework migration remediation time by 75% by designing AI agent audit skills that automatically validate entities, repositories, listeners, migrations, and templates against a target framework version, enabling multi-agent remediation across a 369,000-line PHP codebase.
- *AI-tooling framing:* Accelerated legacy code remediation 4x by building a suite of 12 custom AI agent audit skills, converting file-by-file manual review into parallel multi-agent passes over 18 application bundles of a Symfony 4.4 / PHP 8.1 upgrade.
- *Short:* Cut legacy code remediation time 75% by building custom AI agent audit skills for multi-agent codebase analysis.

> **Wording constraint:** say **remediation**, never "completed the migration". Gabriel's
> contract ended before the upgrade was deployed. Every bullet above describes the
> remediation work he actually performed, which is true independent of the deploy. Do not
> write anything implying he shipped the migration to production.

**Basis for Y (defend it exactly this way):**

| | Files/day | Evidence |
| --- | --- | --- |
| Manual baseline | 42 | 2026-06-08, PHP 8.1 entity hardening, no skills |
| With skills | 685 | 2026-06-15, controller deprecation remediation across 18 bundles |

Raw ratio is 16x. Amortized over the full effort including two days spent building the
skills (Jun 9 and 10): 716 files at 42/day is ~17 days manual, versus ~4 days with skills
(2 building, 2 applying), a **75-80% reduction, about 4-5x**.

**Use 75%, not 16x.** It is the conservative end, it already accounts for the tooling build
cost, and it survives the obvious interview challenge ("did you count the time you spent
building the tools?" — yes). 16x invites disbelief.

**This is a modeled estimate from observed throughput, not an instrumented measurement.**
Say so if asked. The underlying daily file counts are real and reproducible from git.

Corroborating artifact: the 2026-06-15 commit generated per-bundle audit reports
(`plans/migration/controllers/controllers-audit-<Bundle>-2026-06-10.md`) for all 18 bundles,
then applied the fixes.

**This is the first hard evidence for the AI tooling claim in the resume summary**, which
until now rested on nothing in these repositories. It is worth a bullet even without a
percentage, because it is concrete, recent, and rare: most candidates claiming "AI-powered
development tools" mean they used autocomplete.

**Supersedes H1** as the substantiation for MCP/agentic claims. H1 remains unevidenced.

### W5. WITHDRAWN — Entity audit logging system
**Status:** REMOVED. Gabriel did not build it. Confirmed by him and by git.

**Euller Cristian created the AuditBundle** (2025-08-29). Gabriel is second contributor
(34 file-touches to Euller's 59). Any bullet claiming he built entity audit logging is false.

What is genuinely his, and too small for a bullet:

- Extended audit coverage to roughly 10 of the 18 entities (Curso, CursoLiberacao, Capitulo,
  CapituloLiberacao, Conteudo, CertificateRequest, EnrollmentExtensionOrder, User,
  UserProfile, Nfe, Sale), each with tests.
- **Prevented credentials from being written into audit logs**, adding `password`,
  `confirmation token`, and `password requested at` to the ignored-fields list, plus
  suppressing audit noise from last-login and last-viewed-news updates (Nov 2025).

> **Interview material, not resume material.** The sensitive-field exclusion is a good
> answer to "tell me about a time you caught a security issue in review": an audit system
> faithfully logging every field change will happily persist password hashes and reset
> tokens unless someone notices.

### W6. WITHDRAWN as a standalone bullet — Symfony 4.4 / PHP 8.1 migration
**Status:** cannot claim a delivered outcome. **Gabriel's contract ended before the upgrade was deployed.** Do not write a bullet claiming a completed migration, restored security support, or zero-downtime upgrade. None of that is his to claim.

What is true and defensible is the *remediation work*, and that is captured in **W14** with a
measured throughput basis. Use W14.

Verified scope of the work he did perform (June 2026, last commit 2026-06-16):
deprecation remediation across 716 files, PHP 8.1 entity hardening (declared properties,
collection initialization, null-safety, type hints), controller migration to
`AbstractController`, and per-bundle audit reports across 18 application bundles.

> If a JD emphasizes legacy modernization, W14 already carries it. Should an interviewer ask
> how the migration turned out, the honest answer is that his contract finished before
> deploy. Said plainly, that costs nothing. Implied otherwise in a bullet, it is a
> credibility problem.

### W7. WITHDRAWN — Dynamic sales page system
**Status:** REMOVED after attribution check on 2026-08-31. Do not use.

The `dynamic_sales_page` Django app was created by another engineer (candidosouza) in
October 2022. Gabriel is the **third** highest contributor to it, behind Aline Oliveira
(2,096 file-touches) and **Gabriel Caetano** (1,554) against Gabriel Carneiro's 1,499.

Any bullet claiming ownership, authorship, or "built the platform" is false. A
contributor-level claim would be true but too weak to earn a bullet slot.

**Caution:** two engineers named Gabriel worked in this repository. Attribution must always
filter on `gacarneirojr@hotmail.com` (Carneiro), never on the name "Gabriel".
Gabriel Caetano is `98gabrielsc@gmail.com` / `gabrielsc1998`.

What *is* verifiably Gabriel Carneiro's inside this app is captured in **R9** (deep-cloning
sections) and **W13** (bulk admin actions). Those hold up: every commit in the repo touching
`DuplicateSection` is his.

### R12. 87% fewer operations for catalog-wide campaign updates
**Y = 87% (8 operations to 1)** | Python, Django
**Verified sole author:** August 2025, three bulk admin actions plus confirmation templates and tests.

**Basis for Y (derived from code and fixtures, not memory):** the product catalog is **8 dynamic
sales pages** (Go Expert, Liderança Técnica, Full Cycle 4.0 Jr, Full Cycle 4.0 IA, MBA
Arquitetura, Engenharia de Software com IA, DevOps Pro V4, DevOps Pro). A catalog-wide change
previously required editing each page separately: 8 operations. The bulk actions make it 1.
8 to 1 is an 87.5% reduction; use 87%.

What was built:
- `Atualizar - Seções`: updates **32 section fields** across selected pages in one operation (header, bonus, pillar, about, faq, plans, countdown, section_ai, black_friday_banner, mentoring, tutor, discipline, live_classes, learning_paths, and more)
- `Atualizar - Venda, espera ou reserva`: sale / waiting-list / reserve status across pages, i.e. campaign state for the whole product line
- `bulk_update_fields`: general field updates
- Each with a confirmation screen, a cancel path, and a success message reporting fields and pages affected

- *Primary (USE THIS):* Cut catalog-wide campaign updates from 8 page-by-page edits to a single operation, an 87% reduction, by building bulk update actions across 32 section fields in the Django admin.
- *Growth framing:* Enabled the marketing team to switch campaign state (on-sale, waiting list, reserve) across an 8-page product catalog in one operation instead of eight, by building bulk admin actions with confirmation and rollback.
- *Short:* Reduced catalog-wide marketing updates 87%, from 8 edits to 1, with Django admin bulk actions over 32 section fields.

> **Pairs with R9, does not duplicate it.** R9 is creating a section faster (90%, 30 min to 2).
> R12 is applying a change across the whole catalog at once (87%, 8 ops to 1). Different
> operations, different beneficiaries in time. Using both is defensible, but if a resume only
> has room for one admin-efficiency bullet, R9 has the bigger Y and the cleaner story.
>
> The sale-status action is the closest thing in the bank to genuine growth tooling: it is
> campaign state management across a product line. Reach for R12's growth framing when a JD
> mentions campaigns, launches, or marketing enablement.

### R11. 100% of failed CRM lead syncs made recoverable
**Y = 100% (recoverable)** | Python, Django, Celery, Docker
**Verified originator:** `feat: add celery` (2023-05-02), `feat: change celery retry policy` (2023-05-24), and `custom_django_celery_results` created from scratch (2023-05-24), all his. Gabriel Caetano worked on ActiveCampaign use cases afterward; the queue, retry policy, and result backend are Gabriel Carneiro's.
**CRM:** ActiveCampaign (`active_campaign.http` in repo). Keep the bullet stack-agnostic: "CRM".

**Basis for Y (defensible from the code):** a stock Celery result backend records a task ID
and a traceback. The custom result backend Gabriel built surfaces the **lead's email** on
every task result, so any failed sync is identifiable and re-runnable. Combined with the
retry policy, no lead silently disappears: every failure is both retried automatically and,
if it still fails, recoverable by hand. That is the 100%.

- *Primary (USE THIS):* Made 100% of failed CRM lead syncs recoverable by decoupling landing-page lead delivery into a Python/Django Celery task queue on Docker workers, adding automatic retries and a custom result backend that identifies every failed task by lead email.
- *Reliability framing:* Eliminated silent sales lead loss from transient network failures by moving CRM synchronization into an asynchronous Celery task queue with automatic retries and per-lead failure tracking.
- *ON RESUME (current, no Y):* Prevented sales lead loss from transient network failures by decoupling CRM lead sync into a Python/Django Celery task queue on Docker workers, with automatic retries.
- *Short:* Made 100% of failed CRM lead syncs recoverable with an async Celery queue, automatic retries, and per-lead failure tracking.

> **Y is a capability, not a rate.** Gabriel does not know how often syncs failed before, and
> that number is not recoverable. "100% recoverable" is a claim about what the system
> guarantees, provable from the code, and it does not depend on knowing the failure rate.
> Do not restate it as "eliminated 100% of lead loss", which would be a rate claim and is
> not supported.

### W9. MERGED INTO R10 — Production TLS and transport hardening
**Status:** absorbed. Same June 2026 work. There is one Nginx security achievement, not two.

### W10. WITHDRAWN — Passwordless email login
**Status:** REMOVED. Gabriel did not build it, and the substantive code is not inspectable.

Passwordless auth pre-existed him: `argentinaluiz` added the `django-nopassword` fork in
**2019**. Gabriel's work came in March 2024 and consists of driving the 5-minute code expiry
and an `expires_at` bug fix, but **both commits in this repository only bump a pinned git ref**
in `pyproject.toml` and `pdm.lock`. The actual implementation lives in the
`codeedu/django-nopassword` fork, which is not available here.

Also his, and small: `nopassword_wrapper` (post-login redirect to the forum) with e2e tests,
co-touched by Gabriel Caetano.

> **Interview material.** The commit *"fix unchanged expires_at field on nopassword package"*
> reads as login codes not actually expiring before the fix, which would be a real
> authentication weakness he caught and closed. Worth telling; not worth a bullet, since the
> verifiable footprint here is a dependency bump.

### W11. WITHDRAWN — Test suite ownership
**Status:** REMOVED. Not claimable, and the original framing was an activity metric.

On `*Test.php` files in codeplatform, Gabriel is **fourth of six**: Isac (1,509 file-touches),
Luiz (1,283), Euller (1,139), Gabriel Carneiro (830). He wrote a great deal of test code, but
so did three other engineers, by more.

The earlier "203 test files, 41,254 lines, 28% of all code written" framing was also the wrong
kind of number: it measures effort, not outcome. It belongs in `EVIDENCE.md`, and it is there.

**What is his and already on the resume: R4.** The `pytest-xdist` parallelization is
verifiably his in both repositories where it happened (eventsplatform, June 2024, both
commits; forum-code-education, December 2024). That bullet carries a real Y (20%) and needs
no change.

> If a JD stresses testing culture, use R4 and say in the interview that test coverage
> accompanied nearly every feature he shipped. True, and no bullet has to overclaim it.

### W12. WITHDRAWN — Database schema and query optimization
**Status:** REMOVED. Collides with R1 and R2, and has no outcome metric of its own.

A generic "optimized queries and added indexes" bullet sitting next to R1 (20x endpoint) and
R2 (up to 80% query latency) weakens both, because the specific numbers make the vague claim
look like padding.

The underlying work is real (58 migrations authored, 93 index and query commits across a
308-entity schema), but those are activity metrics and live in `EVIDENCE.md`. If scope is
ever needed inside a Z, "across a 308-entity production schema" is a legitimate qualifier
on R1 or R2.

---

---

# PERSONAL PROJECTS

**Structural rule, non-negotiable.** These are Gabriel's own projects, not Full Cycle work.
They must sit in a separate **Projects** section on the resume and never appear as bullets
under a Full Cycle role. Mixing them would be the same attribution failure that withdrew W3,
W5, and W7.

**`main.tex` currently has no Projects section.** Adding one is the single biggest structural
improvement available, because these four projects supply evidence for claims the Full Cycle
work cannot support: React, Node/NestJS, FastAPI, LangChain, MCP, multi-agent workflows, SDD
and ADR.

**Three are deployed and publicly reachable**, which materially raises their weight: a
recruiter can click and see a running application rather than take a repo on faith. Include
the live URL with each.

| Project | Live | Repo | Stack | Commits |
| --- | --- | --- | --- | --- |
| **ATSProof** | `atsproof.website` | `gabrielcjr/atsproof` | FastAPI, HTMX, Tailwind, Gemini + Groq | 40 |
| **DevATS** | `findjobs.gabrielcjr.website` | `gabrielcjr/jobs_nestjs_react` | NestJS, React 19, Prisma, Redis | 56 |
| **AMAE** | `amae.gabrielcjr.website` | `gabrielcjr/amae` | Django 6.1, HTMX 2, PostgreSQL 18 | 62 |
| **Technical Challenge Reviewer** | not deployed | `gabrielcjr/technical_challenge_reviewer` | Django + FastAPI + React + LangChain | 81 |

All four are sole-authored (100% of commits `gacarneirojr@hotmail.com`).

**No business Y is available for any of them, and none should be invented.** Personal projects
cannot claim revenue, users, or cost impact. Their value is evidentiary, plus what they let
Gabriel discuss in an interview.

---

## ATSProof — `atsproof.website`
**FastAPI · HTMX · Tailwind · Google Gemini + Groq · 40 commits · 256 tests · 1,828 lines**

A free, zero-account, privacy-first ATS resume and job matcher. **Deployed and live.**

The most impressive of the four, and the most relevant to AI-focused roles:

- **Three-tier LLM failover:** Gemini 3.6 Flash with native structured schema output, failing over to Groq LLaMA 3.3 70B in JSON mode on `429 Resource Exhausted`, timeouts, or outages, then to LLaMA 3.1 8B.
- **Prompt-injection defense:** untrusted input is isolated inside `<resume_text>` and `<job_description_text>` XML boundaries, with system instructions that neutralize adversarial instructions embedded in uploaded files.
- **Abuse protection:** slowapi rate limiting (5 req/min per IP), a global concurrency semaphore to prevent burst quota exhaustion, and a honeypot bot check.
- **Privacy by architecture:** PDFs parsed in RAM via `io.BytesIO` and discarded immediately. Zero disk, zero database, no PII retained.
- **Observability:** Logfire instrumentation. **256 tests.**

- *Bullet:* Built and deployed a privacy-first ATS resume analyzer in FastAPI with three-tier LLM failover across Google Gemini and Groq, prompt-injection defenses using XML boundary isolation, per-IP rate limiting, and fully in-memory PDF processing that persists no user data.
- *AI-security emphasis:* Engineered defensive LLM integration with structured-schema outputs, adversarial-instruction neutralization, concurrency throttling, and automatic multi-provider failover on rate limits and outages.
- *Short:* Built a live FastAPI resume analyzer with multi-provider LLM failover, prompt-injection defenses, and zero-persistence PDF processing.

> **Rare signal.** Prompt-injection defense and LLM abuse protection are things most engineers
> claiming "AI integration" have never touched. Lead with this for any AI-focused role.
>
> It also implements the **Google XYZ formula** to generate resume bullets, the same standard
> this bank is built on. Good interview anecdote.

---

## DevATS — `findjobs.gabrielcjr.website`
**NestJS 11 (Fastify) · React 19 · Prisma · PostgreSQL 17 · Redis 7 · 56 commits · ~7,100 lines**

Job market analytics platform. **Deployed and live.** Full detail in the entries below.

### Fills the React / Node / NestJS gap
The fix for the most damaging gap in every recent scoring. React, Node.js, and NestJS
previously appeared **once each, in Skills, never in a bullet**, which sank the Middle
Fullstack (Node + React) scoring at 41% and weakened the Senior Product Engineer one on its
hard "TypeScript **and** React" gate.

- *Bullet:* Built and deployed a full-stack job market analytics platform in TypeScript: NestJS with Prisma and PostgreSQL on the back end, React 19 with Vite on the front end, Redis for cache-aside and distributed rate limiting, and a GitHub Actions CI gate enforcing backward compatibility.

### Substantiates the AI/agentic claims (supersedes H1)
- **MCP:** `.agents/mcp_config.json` wires `@modelcontextprotocol/server-postgres`; ADR-0004 records the rationale (agents inspecting live DB schemas and validating aggregation query performance).
- **Multi-agent workflows** as a development methodology: ADR-0003 defines *Multi-Agent Contract Decoupling* via TypeScript interfaces and DOM selectors; SDD-0003 splits frontend QA between *Unit QA Agents* (Vitest) and *Autonomous Browser Agents* (Playwright); ADR-0004 uses typed DTOs so frontend and backend agents work concurrently.
- **Designing code for agent consumption**, the strongest detail: ADR-0003 mandates deterministic `data-testid` attributes *so the Browser Subagent can target and test them reliably*.
- Every ADR has an **Agentic Guardrails** section. ADR-0002 is co-attributed "Gabriel & Antigravity Agent".

- *Bullet:* Designed an agentic development workflow for a full-stack TypeScript project, using Model Context Protocol (MCP) for live database schema introspection and decoupling concurrent frontend, backend, and browser QA agents through typed DTO contracts and deterministic DOM test identifiers.

### Substantiates SDD and ADR
The resume claims both in the summary and Skills. **This is the proof:** 5 ADRs and 5 SDDs,
paired and cross-referenced, each with context, decision drivers, options considered, and
consequences. ADR-0002 covers CI quality gates with Prisma migration drift detection,
isolated PostgreSQL 17 and Redis 7 service containers rather than mocks, concurrency
cancellation, and a sub-3-minute feedback target.

---

## AMAE — `amae.gabrielcjr.website`
**Django 6.1 · HTMX 2 · Tailwind 4 · PostgreSQL 18 · Redis · 62 commits · 5,626 lines · 33 tests**

Connects financial sponsors with missionaries across Brazil: automated financial adoptions,
geocoded field locations, transaction logging, on-the-fly financial statements and receipt
PDFs (reportlab). **Deployed and live.**

- Clean architecture across decoupled Django apps (`accounts`, `finance`, `missions`, `pages`)
- **Redis-backed rate limiter** (middleware, decorator, tests) — `feat/rate-limiter-redis`
- **Production security hardening:** `CSRF_TRUSTED_ORIGINS` and `SECURE_PROXY_SSL_HEADER` for reverse-proxy deployment, plus production security headers — the same pattern as **R10**, independently applied
- SSR + HTMX for a no-build-step reactive frontend; gunicorn + whitenoise

- *Bullet:* Built and deployed a Django financial platform managing sponsor-to-missionary adoptions, transaction ledgers, and generated receipt PDFs, with a Redis-backed rate limiter and production security hardening for reverse-proxy deployment.
- *Domain framing:* Delivered a financial adoption platform with transactional integrity across sponsors, recipients, and payment records, including automated statement and receipt generation.

> Second financial-domain artifact after W2, and this one is fully his. Useful for fintech
> applications where W2's lack of a Y is a weakness.

---

## Technical Challenge Reviewer
**Django 5.1 + DRF + Celery · FastAPI 0.115 + LangChain · React 19 · PostgreSQL 17 · Redis · Nginx · 81 commits**

Not deployed, and not in the portfolio. Still the best evidence for FastAPI and LangChain.

**Architecture:** React SPA → Django REST API (persists submission, returns 201) →
Celery/Redis queue → FastAPI evaluator microservice (clones repo via GitPython, collects
source files, calls LLMs through LangChain) → authenticated webhook callback
(`X-Internal-Token`) → Django applies APPROVED / REJECTED / FAILED → SPA polls.

### Substantiates FastAPI and LangChain
**This closes the open FastAPI question.** FastAPI was Skills-list-only and was deliberately
kept out of experience bullets during the Tech Company tailoring because its depth was
unconfirmed. Confirmed here. LangChain is pinned via `langchain`, `langchain-core`,
`langchain-openai`, and `langchain-google-genai`.

- **Multi-provider LLM fallback:** `evaluate_with_llm` builds a provider sequence, tries them in order, and returns which provider actually served the request.
- **Defensive handling of model output:** `extract_json_from_text`, `_strip_markdown_fence`, `_extract_json_between_braces`, plus normalizers for the approved flag, summary, improvements, and reasoning. The genuinely hard part of LLM integration.
- **Reliable webhook delivery:** Celery task with `autoretry_for=(httpx.RequestError, httpx.HTTPStatusError)` and exponential backoff capped at 3600s.
- Service-to-service auth via `X-Internal-Token`. 9 test suites with pytest-asyncio and respx.

- *Bullet:* Built a distributed LLM evaluation system with a FastAPI microservice that clones and analyzes GitHub repositories through LangChain, with multi-provider failover across Groq and Gemini, reporting results to a Django API over authenticated webhooks with automatic retry and exponential backoff.

### Mirrors R6, and that is a feature
R6 (100% of manual challenge evaluation eliminated, PHP/Symfony webhook to an AI-powered
microservice) is the production version of this exact problem. This is the same domain rebuilt
independently in a different stack.

> Interview narrative: "I automated challenge evaluation at work with a webhook to an AI
> microservice, then rebuilt the whole system myself in Python to understand the LLM
> integration properly." More convincing than either item alone.

---

## Combined coverage

What the four projects supply that Full Cycle work cannot:

| Claim | Evidence |
| --- | --- |
| React, TypeScript | DevATS (React 19), Technical Challenge Reviewer (React 19) |
| Node.js, NestJS | DevATS (NestJS 11, Fastify) |
| FastAPI | ATSProof, Technical Challenge Reviewer |
| LangChain | Technical Challenge Reviewer |
| MCP, multi-agent workflows | DevATS (ADRs/SDDs) |
| SDD, ADR | DevATS (5 + 5, cross-referenced) |
| LLM integration depth | ATSProof (failover, injection defense), TCR (output normalization) |
| Security engineering | ATSProof (injection, rate limiting), AMAE (CSRF, proxy TLS, rate limiter) |

**Weighting:** personal projects carry less weight than production work with a real employer,
so these never displace the READY bullets. They earn a compact Projects section, ideally two
or three lines each with the live URL, and they answer the gaps a recruiter would otherwise
mark as missing.
