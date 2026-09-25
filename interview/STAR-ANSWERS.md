# Interview Scripts (STAR, 2 minutes each)

**Timing:** 2 minutes of speech is roughly 280 to 300 words at a natural pace. Each script
below is written to that length. Rough budget: Situation and Task 35 seconds, Action 60
seconds, Result 25 seconds.

**Rules for yourself:**
- Every number here is verified. Do not round up under pressure.
- If asked about React, Node, TypeScript, FastAPI, or LangChain, say **personal projects**.
  Never imply professional use. Same for AWS EC2 and Lambda.
- Say **remediation**, not "completed the migration". Your contract ended before deploy.
- If you do not know a number, say so. "I did not measure that" is a strong answer.

---

## 1. Tell me about yourself

*Not STAR. This is your opener and it sets the frame for everything after.*

I am a software engineer with five and a half years at Full Cycle, a Brazilian software
engineering company that runs a large developer education platform. I started as a Software
Analyst supporting students on their projects, moved into backend development, and spent my
last two years as a Full Stack Developer.

My depth is backend, Python with Django and PHP with Symfony, working on a platform with
around three hundred entities and a large amount of production traffic. Most of my work has
been in two areas. The first is performance and reliability: I cut one endpoint's response
time by twenty times by finding the root cause of a pagination bug, and reduced query latency
by up to eighty percent by building a caching layer over complex multi-join queries. The
second is automation: I have removed a lot of manual work from the business, including
building an in-house diploma issuance system that replaced a third-party university issuer
and cut issuance time by eighty-five percent.

More recently I have been working with AI, and not just using it. I built a set of custom AI
agent audit skills to drive a framework migration across a three hundred and sixty thousand
line codebase, which cut the remediation time by about seventy-five percent. I also have three
applications I built and deployed myself, using FastAPI, NestJS and React, which is where my
TypeScript and front-end framework experience comes from.

I hold two MBAs, one in Software Architecture and one in Software Engineering with AI. I am
looking for a team where I can keep working on backend systems with real business impact.

---

## 2. What is your most significant technical achievement?

**Situation.** Full Cycle runs accredited postgraduate programs, so every graduating student
needs a formal diploma. When I joined that work, the company could not issue diplomas itself.
Every diploma was routed through a partner university, which meant paying a per-certificate
fee, waiting on an external party, and a lot of manual coordination on our side.

**Task.** I was asked to build the system that would let the company issue diplomas as the
institution itself. In Brazil that is not just a PDF generator. There are regulatory
requirements: you have to maintain a diploma registry book with sequential pages, a registry
code and publication number for each entry, a named responsible party with their CPF on
record, and a formal process for closing a book.

**Action.** I designed and built two core entities, a DiplomaBook and a DiplomaRegistry. The
book tracks its own registry count, closure date, who closed it and their identification, and
it rejects any attempt to write to a book that is already closed. Each registry records the
page, registry code, publication, registration date, issue date, conclusion date and
graduation date, and supports cancellation with a full audit trail. I built the service layer
around it, the controllers and admin screens, and tests for the entities, the repository, the
service and the controller.

**Result.** The company became able to issue its own diplomas for the first time, which was a
new capability rather than an efficiency gain. Issuance time dropped by about eighty-five
percent, and we stopped paying the partner university per certificate. It is the work I am
most proud of because it was regulated, it had to be correct, and it changed what the business
could do rather than just making something faster.

---

## 3. Tell me about the hardest bug you have debugged

**Situation.** We had critical administrative endpoints in a PHP Symfony platform that had
become unusably slow and were frequently crashing with Out-Of-Memory errors during peak hours.
Users were waiting multiple seconds on pages that should have loaded instantly, and team members
had started treating slow queries as normal.

**Task.** I investigated to find the underlying architectural cause rather than just bumping
container memory limits or adding an unprincipled cache layer on top of a broken query.

**Action.** I started from the database and memory profiling side rather than the application
views, because resource consumption scaled with the total row count rather than with concurrent
traffic. When I traced how our Doctrine repositories interacted with the pagination layer, I
found that multiple repositories were executing `$qb->getQuery()->getResult()` before handing
data over to the paginator. The ORM was loading and hydrating tens of thousands of full entity
objects into PHP RAM just to display thirty records on screen.

Instead of patching only the single endpoint that crashed, I audited the pattern across the
entire codebase. I systematically refactored twenty-six repositories and controllers, converting
eager hydration calls into database-delegated queries where the database executes strict LIMIT
and OFFSET clauses and PHP hydrates only the active page.

**Result.** PHP memory consumption dropped by over ninety percent across those routes, completely
eliminating out-of-memory crashes, and endpoint response times dropped by up to twenty times.
The lesson I took is that an ORM abstraction will happily hide massive memory allocations behind
clean-looking code. When debugging latency and resource exhaustion, I always inspect the hydration
lifecycle and the generated SQL directly.

---

## 4. Tell me about a time you improved performance

**Situation.** Students on the platform had a news feed showing chapter releases for their
courses. It was one of the most frequently loaded views on the platform and it was slow. The
underlying query joined across several tables to work out which chapters had been released for
which student, based on their enrollment.

**Task.** Make it fast without changing what students saw, and without denormalizing the data
model, which would have created a consistency problem elsewhere.

**Action.** The queries were expensive but highly repetitive. Many students share the same
course and chapter release state, so the same expensive multi-join was being recomputed for
different users with identical inputs. Rather than caching the rendered page, which would have
been wrong because the content is per-student, I built a custom result-caching layer over
Doctrine keyed on the query parameters. Identical parameter sets return a cached result set,
and different ones do not collide. That meant the cache worked at the level where the
expense actually was, the query, rather than at the level where the variation was, the user.

I also had to think about invalidation, since a chapter release changing has to be reflected
promptly for students who are waiting on it.

**Result.** Query latency dropped by up to eighty percent on that feed. What I would highlight
is the choice of caching layer. The obvious place to cache was the page, and it would have
been wrong. Finding the level where the work is shared is usually more important than the
caching technology itself.

---

## 5. Tell me about a time you took initiative to improve how the team works

**Situation.** We were beginning a major framework upgrade on our main platform, a PHP Symfony
codebase of about three hundred and sixty thousand lines across eighteen bundles. The work was
mostly deprecation remediation: finding every place using an API that the new version had
changed, and fixing it, without breaking behaviour.

**Task.** No one asked me to do this part. I was doing the remediation by hand, working
through entities, and I could see how the arithmetic was going to end. In one day of manual
work I got through about forty files. At that rate the full codebase was going to take weeks
of tedious, error-prone review where the real risk was not difficulty but missing something.

**Action.** I stopped doing the remediation and spent two days building tooling instead. I
wrote a set of custom AI agent audit skills, one per concern: entities, repositories,
listeners, migrations, config, templates. Each one knows what the new framework version
requires for that kind of file and reports what fails. I worked on this alongside a colleague
who built several of the others.

The hard part was not generating findings, it was calibration. The first versions flagged
everything, which is useless, because a report with three hundred warnings and no ranking is
the same as no report. I spent most of the second day tuning them to surface genuine blockers
rather than noise.

**Result.** Once the skills worked, I audited all eighteen bundles and applied controller
remediation across six hundred and eighty-five files in a single day, against forty by hand.
Accounting for the two days spent building the tooling, it cut the remediation timeline by
about seventy-five percent. To be precise, that is a figure I calculated from throughput
before and after, not something we instrumented.

*If asked how it ended: my contract finished before the upgrade was deployed.*

---

## 6. Tell me about a time you worked on a security problem

*Answer this when asked about security work. If you are asked specifically about a problem you
**discovered**, say plainly that this one was identified by the tech lead and that you owned
the remediation. Do not let the framing drift.*

**Situation.** Our tech lead flagged that a production Django application, a set of
public-facing sales pages, was exposed to automated scanner traffic. Bots probing for
configuration files, backup files, source files, dependency manifests like composer.json and
requirements.txt, and WordPress and phpMyAdmin exploit paths. The application was answering
those requests rather than refusing them.

**Task.** He identified the exposure and I owned the remediation. My job was to work out what
was actually reachable, close it, and do it without breaking the site, because these are
revenue-generating sales pages.

**Action.** I went through the categories one at a time and blocked five classes at the Nginx
gateway: dotfiles like .git and .env, source and config and backup extensions, build and
dependency filenames, CMS scanner paths, and PHP entirely, since it is a Python application
and no PHP should ever be served. I turned off the Nginx version banner and added baseline
security headers. On the Django side I configured the app to trust ingress TLS termination and
set session and CSRF cookies to secure outside debug mode. I also found directory listing was
enabled on the static path and turned it off.

Two judgment calls I want to mention. I deliberately did not add per-IP rate limiting, and I
documented why: these are public sales pages, and many legitimate buyers from one company come
through a single corporate NAT address. Rate limiting would have blocked real customers, so
brute-force protection belonged at the application layer. And I anchored the CMS-scanner rules
at path boundaries, so a marketing URL containing something like "wp-admin" as part of a course
name would not be blocked.

**Result.** Five classes of entry point removed from the public attack surface, with no
disruption to the marketing pages.

## 7. Tell me about your experience with AI

*Common now, and your strongest differentiator. Not strictly STAR.*

I would separate three things: using AI, integrating AI into products, and building tooling
that makes AI agents effective.

On integration, at Full Cycle I automated a manual grading process. Instructors were reviewing
every student challenge submission by hand. I built a webhook integration from our Symfony
application to an AI-powered microservice that evaluates submissions and reports back. That
removed one hundred percent of the manual evaluation. I also worked on cost control: we had a
feature where courses could reply with AI, and disabled courses were still consuming tokens.
I added per-course feature flags with admin controls, which eliminated all of that wasted spend.

I later rebuilt that whole problem myself, in Python, to understand the LLM side properly. It
is a FastAPI microservice that clones a GitHub repository, collects the source, evaluates it
through LangChain, and reports back over an authenticated webhook with retry and backoff. The
part I learned most from was defensive handling of model output. Models do not reliably return
clean JSON, so I had to strip markdown fences, extract JSON from surrounding prose, and
normalize the fields. That is the actual work in LLM integration.

I also built a live tool called ATSProof with three-tier provider failover across Gemini and
Groq, so a rate limit or outage on one provider fails over automatically, plus prompt-injection
defenses. Untrusted input is isolated inside XML boundaries and the system instructions
neutralize adversarial instructions embedded in uploaded documents.

And on tooling, the audit skills I built for the framework migration, where the interesting
problem was calibrating agents to report real blockers rather than noise.

---

## 8. Tell me about a time you received difficult feedback

**Situation.** I had submitted the Nginx hardening configuration I described earlier. It
blocked five classes of scanner traffic on a production application, and I was fairly
confident in it because I had reasoned through each rule.

**Task.** It came back from review with a number of changes requested. Not a rejection, but
enough that roughly half the file changed.

**Action.** My first instinct was that I had already thought about most of it. But the
reviewer's concern was one I had underweighted: my deny rules were pattern-based, and on a
marketing site the URLs are business-owned. Marketing creates course slugs freely. A rule
matching "wp-admin" anywhere in a path would block a legitimate page called something like
"wp-admin-do-curso". A security rule that takes down a sales page is not a good trade,
because the cost lands on the business rather than on the attacker.

So I went back through every pattern and anchored them properly, so the CMS rules only match
at a path boundary rather than anywhere in the URL. I also kept the well-known path reachable
so ACME certificate renewal would not break, which was the same class of mistake waiting to
happen.

**Result.** The revised version went in, and it is better than what I first submitted. What I
took from it is that in security work the failure mode I need to worry about is not only what
I let through, it is what I break. I now try to ask who else's work my rules touch before I
write them, rather than after review.

---

## 9. Why are you leaving, and what are you looking for?

I was at Full Cycle for five and a half years, which is a long time, and it ended when my
contract finished in July. I would have been happy to continue, so this is not a departure out
of frustration.

What I want next is honestly informed by what I have been doing since. I have spent the time
building and deploying three applications of my own rather than only applying to roles. I did
that partly to stay sharp and partly because there were things I wanted to understand properly
rather than at the level a job had required, particularly LLM integration and modern
TypeScript front ends.

What I am looking for is a team where backend work is connected to a real business domain. The
work I have been proudest of has been where I understood why something mattered commercially,
not just what the ticket said. The diploma system is the clearest example. I could not have
built it correctly by implementing a specification, because the requirements came from Brazilian
education regulation and from what the finance side needed. The same is true of the delinquency
reporting I built, where the value was entirely in understanding how collections actually work.

I would also like to keep working on AI in a serious way rather than a decorative one. I am
more interested in the engineering around models, the failover, the output handling, the cost
control, the tooling that makes agents reliable, than in the model layer itself.

Practically, I am looking for a remote role with an international team. I have worked fully
remote and asynchronously for five years, so that is a mode I am comfortable in rather than one
I am hoping to try.

---

## 10. Tell me about a time you had to learn something quickly

**Situation.** When my contract at Full Cycle ended, my professional experience was Python and
PHP on the backend, with server-rendered front ends: Twig, Django templates, SCSS and jQuery.
I could see from the roles I was interested in that a lot of them expected TypeScript and a
component framework, and that reading about it would not be enough.

**Task.** I decided the only credible way to learn it was to build and deploy real
applications, not follow tutorials, so that the failure modes would be real ones.

**Action.** I built three. The first is a job market analytics platform with a NestJS and
Prisma backend and a React front end, with Redis for caching and rate limiting, and a CI
pipeline that enforces backward compatibility by detecting database migration drift. The second
is a resume and job description matcher in FastAPI with multi-provider LLM failover. The third
is a Django platform for a missionary support organization that handles financial adoptions,
transaction ledgers and generated receipt PDFs.

I deployed all three on a virtual machine I manage myself on Oracle Cloud, with their own
domains and TLS, because deploying and operating them is where I learned the most. I also
documented the architecture decisions properly, with Architecture Decision Records, partly
because I wanted the practice and partly because I was using AI agents heavily and they need
unambiguous written contracts to work against.

**Result.** All three are live and I can walk through any of them. I would be direct that this
is project experience rather than years of production TypeScript, but it is real, deployed,
and I own every decision in it.

---

## 11. Tell me about a time a third-party integration failed and how you handled it

**Situation.** On our landing pages, user sign-ups and sales leads were synchronized directly
with an external CRM via the ActiveCampaign API. The integration was executed synchronously
inside a Django post-save signal during the web request lifecycle.

**Task.** Whenever the third-party API experienced network latency spikes or transient outages,
our web requests hung until timing out with 504 Gateway errors. Prospective buyers saw a broken
page, and high-value marketing leads were silently lost because there was no durable retry mechanism.

**Action.** I decoupled the external CRM integration from the user-facing request flow by moving
it to an asynchronous Celery task queue running on Docker workers with Redis. In the signal, I
only serialized the conversion data and dispatched a background task.

In the task definition, I configured an automatic exponential retry policy for transient network
exceptions with up to ten retries over an extended backoff window, guarded by an idempotency flag
on the database record to prevent duplicate CRM entries. To ensure total operational transparency,
I built a custom Celery result backend that extracted the lead's email address and displayed it
directly in the Django admin interface alongside failure tracebacks and a one-click manual retry action.

**Result.** HTTP request response times for sign-ups dropped to under eighty milliseconds, and we
achieved one hundred percent fault tolerance on lead synchronization. Even during prolonged CRM
API downtime, zero leads disappeared, and every failed sync was visible and recoverable.

---

## 12. Tell me about a time you modernized a legacy codebase or managed technical debt

**Situation.** Our primary sales and events platform was running on Django 3.0 and Python 3.8.
It relied on abandoned open-source libraries, including an unmaintained django-jsonfield fork and
an obsolete model-mommy testing fixture package that triggered constant deprecation warnings and
broke modern test runners. The technical debt prevented us from applying security patches and
blocked the team from taking advantage of modern Python interpreter performance gains.

**Task.** I took ownership of modernizing the core infrastructure across the application without
disrupting ongoing marketing campaigns or causing data regressions in production.

**Action.** I executed the modernization in disciplined, incremental phases. First, I refactored
the domain models to eliminate the third-party jsonfield package, replacing it with Django's native
JSONField and carefully migrating existing historical database migrations. Next, I updated our
entire testing infrastructure from model-mommy to model-bakery, eliminating deprecation noise and
restoring clean test execution.

Finally, I upgraded our container base images and framework configurations directly to Python 3.13
and Django 5.2, updating ecosystem dependencies and adjusting settings to enforce modern defaults.

**Result.** We brought the codebase to the modern LTS version of the framework, completely
eliminating one hundred percent of deprecated legacy packages and resolving critical security
vulnerabilidades with zero production regressions and faster test feedback.

---

## 13. Tell me about a feature you built that eliminated operational bottlenecks

**Situation.** Whenever the marketing and operations teams launched a new course, postgraduate
program, or promotional campaign, setting up the sales page was an arduous manual process. Each
page consisted of dozens of complex sections and nested child entities: mentors, live classes,
curriculum disciplines, bonus items, and testimonials.

**Task.** Setting up a single page took marketing roughly thirty minutes of error-prone data entry
in the admin panel, often requiring backend engineers to write one-off database scripts to help
clone existing campaign structures. I wanted to give non-technical stakeholders complete autonomy.

**Action.** I designed an introspection-based cascade duplication engine in Python. Using Django's
internal meta API, the use case dynamically inspects any model class, creates a deep copy of the
parent section, assigns unique slugs, and automatically discovers all reverse one-to-many
relationships. It then iterates over the related managers, clones each child entity, repoints the
foreign key to the new parent, and commits the entire hierarchy inside an atomic database transaction.

I packaged this logic into a reusable Django Admin Mixin that injected a one-click clone action
across fifteen distinct section models in the CMS.

**Result.** Setting up complex multi-relational sections dropped from thirty minutes of manual
typing to about two minutes, representing an operational acceleration of over ninety percent. It
completely eliminated engineering involvement in marketing page setup and prevented referential
integrity errors during campaign launches.

---

## Questions I still need material for

Two very common questions have no strong verified answer yet. Do not improvise these cold.

### "Tell me about a failure or a mistake"

The scripts above deliberately do not fake one. Interviewers can tell. What is needed is a real
incident: something you shipped that broke, a decision that turned out wrong, or an estimate
you badly missed. The structure that works: what happened, what it cost, what you did
immediately, and specifically what you changed afterwards so it could not recur. The last part
is what is actually being assessed.

### "Tell me about a conflict with a colleague"

Script 8 covers receiving critical feedback, which is adjacent but not the same. If asked
specifically about disagreement, you need a case where you and someone else wanted different
things and it had to be resolved. Technical disagreements about approach count.

### Also worth preparing

- A time you influenced a decision without authority
- A time you had to say no, or push back on scope
- The largest scale you have worked at, and note this needs the platform numbers you do not
  currently have, so prepare an honest framing that describes the system without inventing
  traffic figures
