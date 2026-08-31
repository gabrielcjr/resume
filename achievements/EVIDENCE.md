# Scope Evidence (NOT resume metrics)

**These numbers do not belong in resume bullets.** They are activity measures (commits,
lines, files, models), and a recruiter reads them as effort rather than impact. Google's
XYZ formula requires Y to be a business outcome: percent, dollars, time, or volume.

Keep them for three purposes only:

1. **Interviews.** When asked "how big was the system?" or "what was your role on the
   team?", these answer it credibly and immediately.
2. **Proving scope.** If a claim in `ACHIEVEMENTS.md` is challenged, this is the receipt.
3. **Scope inside Z.** A phrase like "across a 369,000-line codebase" can strengthen the
   *method* half of a bullet. It can never serve as the Y.

Every figure was measured directly from the git history and working tree of the three
Full Cycle repositories on 2026-08-31. None is estimated. Commands are recorded so any
number can be re-derived or challenged.

## Overall contribution (all three repos, Mar 2023 to Jun 2026)

| Measure | Value |
| --- | --- |
| Commits authored | **1,856** |
| Lines added | **148,447** |
| Lines deleted | **53,683** |
| Distinct files touched | **2,601** |
| Distinct active days | **364** |
| Span | 3 years 4 months |

## Per repository

| | codeplatform | eventsplatform | forum-code-education |
| --- | --- | --- | --- |
| Stack | PHP 8.1 / Symfony 4.4, Doctrine, Twig | Python / Django, Celery | Python / Django |
| Gabriel's commits | **1,351** | **419** | **86** |
| Rank on team | **3rd of 20+ contributors** | 7th | 4th |
| Lines added / deleted | 105,063 / 38,248 | 41,542 / 14,242 | 1,842 / 1,193 |
| Files touched | 1,301 | 1,243 | 57 |
| Active days | 269 | 74 | 21 |

## Codebase scale (what he was operating inside)

**codeplatform** (production platform, PHP/Symfony)

| Measure | Value |
| --- | --- |
| Application PHP | **369,253 lines across 1,711 files** |
| Doctrine entities | **308** |
| Controllers | **136** |
| Repositories | **76** |
| Test classes | **475** (187,877 lines) |
| Database migrations | **314** |
| Twig templates | **411** |

**eventsplatform** (Python/Django)

| Measure | Value |
| --- | --- |
| Python | **993,317 lines across 4,168 files** |
| Django apps | 12 |
| Models | 45 model modules |
| Database migrations | 326 |

**dynamic_sales_page** — the Django app Gabriel primarily owned (1,499 of his file touches)

| Measure | Value |
| --- | --- |
| Django models | **91** |
| Database migrations | **114** |
| Templates | **284** |
| Fixture files | **88** |
| Python | 14,773 lines |
| Gabriel's contribution | **34,637 lines added, 7,831 deleted** |

## Per-theme contribution

| Theme | Measure |
| --- | --- |
| Testing | **203 test files authored**, **41,254 lines of test code** (40,130 PHPUnit + 1,124 pytest) |
| Database migrations authored | **58** |
| Deprecation remediation (Symfony upgrade) | **716 files touched** |
| Payments / invoicing / checkout | **254 files touched** |
| Audit logging | **18 entities audited**, 164 files touched |
| Certificates / diplomas | **60 of the codebase's 66 certificate files touched** |
| Operational reporting | 50 files touched |
| HubSpot CRM integration | 29 files touched |

## Ratios worth quoting

- **Test code is 28% of everything Gabriel wrote** (41,254 of 148,447 lines added). This
  substantiates "writing well-tested code is non-negotiable" with a number.
- **He touched 60 of the 66 certificate-related files** in codeplatform, which is
  effective ownership of that subsystem.
- **1,351 commits out of a 20+ person team's history**, third highest, on a platform with
  369k lines of application PHP.

## Provenance

```bash
# commits, lines, files, active days (per repo)
git log --author="gacarneirojr@hotmail.com" --pretty=tformat: --numstat \
  | awk '{a+=$1; d+=$2} END {print a, d}'
git log --author="gacarneirojr@hotmail.com" --name-only --pretty=format: \
  | grep -v '^$' | sort -u | wc -l
git log --author="gacarneirojr@hotmail.com" --pretty='%ad' --date=short | sort -u | wc -l

# team ranking
git log --pretty="%an <%ae>" | sort | uniq -c | sort -rn

# codebase scale
find src -name "*.php" -exec cat {} + | wc -l
find src -path "*Entity*" -name "*.php" | wc -l

# test authorship
git log --author="gacarneirojr@hotmail.com" --pretty=tformat: --numstat -- "*Test.php" \
  | awk '{a+=$1} END {print a}'
```

Gabriel's git identity across all three repos: `gacarneirojr@hotmail.com`
(plus 7 commits as `gabrielcarneiro@fullcycle.com.br`).

## Still unmeasurable from git

These need Gabriel, since no repository can answer them:

1. **Platform user count** — students on the platform, concurrent or total.
2. **Traffic** — requests per day, peak RPS.
3. **Database size** — rows in the largest tables, total DB size.
4. **Team size** — engineers on his immediate team, not total repo contributors.
5. **Business volume** — certificates issued per term, payments processed per month,
   leads synced per month.
6. **Cost figures** — monthly cost of the eliminated worker pod, monthly LLM spend before
   the feature flags.

Any one of these would upgrade several bullets at once, because they supply the
denominator that turns "built X" into "built X at Y scale".

## Attribution warning

**Two engineers named Gabriel worked in these repositories.**

| Person | Git identity |
| --- | --- |
| **Gabriel Carneiro Jr** (this resume) | `gacarneirojr@hotmail.com`, plus 7 commits as `gabrielcarneiro@fullcycle.com.br` |
| Gabriel Caetano (different person) | `98gabrielsc@gmail.com`, names `Gabriel Caetano` / `gabrielsc1998` / `Gabriel da Silva Caetano` |

Never filter git history by the name "Gabriel". Always filter by email.

Being a top committer on a repository is not the same as owning a feature or an app. Before
claiming ownership, check who created the app and how the author's contribution compares to
the other contributors, not just the raw count. W7 was withdrawn on 2026-08-31 for exactly
this error.
