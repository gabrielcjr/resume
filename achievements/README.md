# Achievements Repository

A bank of accomplishments to draw from when tailoring resumes. `main.tex` holds what fits on
two pages. This holds everything, so a tailored resume can swap in whichever bullets match
the job description.

## The standard: Google's XYZ formula

> "Accomplished **[X]** as measured by **[Y]** by doing **[Z]**."
> — Laszlo Bock, former SVP of People Operations, Google

- **X** = the outcome, not the task
- **Y** = the number proving it. Must be a **business outcome**: percent, dollars, time, volume.
- **Z** = the method

Why: 58% of recruiters say measurable achievements are what make a resume stand out most
(Jobscan). Quantified resumes get 2.5x more interview invitations (LinkedIn Talent Report
2023) and 40% more callbacks (TalentWorks). 75% of hiring managers want achievements over
duties. Only 26% of resumes carry five or more measurable results.

## Files

| File | Contents |
| --- | --- |
| `ACHIEVEMENTS.md` | The bank. 12 READY, 2 NO Y, 7 withdrawn or merged, 4 personal projects. |
| `QUESTIONS.md` | What is still missing and where to look for it. |
| `EVIDENCE.md` | Scope evidence and the attribution warning. Interview use only, **never in a bullet**. |

## Current state

**12 READY bullets (R1-R12)** with verified business-outcome metrics:

| | Y | Note |
| --- | --- | --- |
| R1 | 20x | endpoint response time, root-caused pagination bug |
| R2 | up to 80% | query latency, custom Doctrine result cache |
| R3 | 15% | server performance, runtime and dependency upgrades |
| R4 | 20% | CI/CD feedback, pytest-xdist parallelization |
| R5 | 100% | wasted LLM token spend eliminated |
| R6 | 100% | manual challenge evaluation eliminated |
| R7 | **85%** | diploma issuance time, brought in-house (rewritten) |
| R8 | 90% | manual sync-recovery effort |
| R9 | 90% | page section setup for the marketing team |
| R10 | 5 classes | exposed entry points removed |
| R11 | **100%** | failed CRM lead syncs made recoverable (new) |
| R12 | **87%** | catalog-wide campaign updates, 8 ops to 1 (new) |

**Plus W14 (75%)** — AI agent tooling for legacy code remediation. Modeled from observed
throughput, not measured. The strongest AI differentiator in the bank.

**2 kept without a Y:** W1 (worker pod eliminated), W2 (billing delinquency program).
Both usable as supporting bullets, never leads.

**7 withdrawn or merged.** Four failed attribution or ownership checks (W3 payments, W5 audit
logging, W7 sales page platform, W11 test suite), one cannot claim a delivered outcome (W6
Symfony migration, contract ended before deploy), two were duplicates (W4 into W2, W9 into
R10), one was too vague beside better bullets (W12).

**4 personal projects,** three deployed and live. They supply the only evidence for React,
Node/NestJS, FastAPI, LangChain, MCP, multi-agent workflows, SDD, and ADR.

## How to use

1. Read the JD. Pick READY entries by keyword and domain overlap.
2. Copy the phrasing variant matching the role's framing (backend, full stack, security,
   data, product/growth, integration, AI).
3. Build the tailored copy in `tailored/`.
4. Lead with the largest Y that is also relevant. A relevant 15% beats an irrelevant 20x.
5. Flex the Projects section per role: DevATS leads for Node/React, ATSProof for AI,
   drop it entirely for a pure backend PHP role if space is tight.

## Rules

- **Never invent a Y.**
- **Never use an activity number as a Y** (commits, lines, files). Those live in `EVIDENCE.md`.
- **Never claim ownership without checking who created the code** and how the contribution
  compares to others. Four entries were withdrawn for exactly this.
- **Never filter git history by the name "Gabriel."** Two engineers named Gabriel worked in
  these repositories. Filter by `gacarneirojr@hotmail.com`.
- **Keep personal projects in their own Projects section**, never as bullets under a Full
  Cycle role.
- Personal projects cannot carry business metrics. Do not give them any.
