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

**Situation.** We had an endpoint in a PHP Symfony service that had become unusably slow.
Users were waiting a long time on a page that should have returned quickly, and it had been
that way long enough that people had started treating it as normal.

**Task.** I picked it up to find out what was actually happening rather than adding a cache on
top of a problem nobody understood.

**Action.** I started from the database side rather than the application code, because the
response time scaled with data volume rather than with request rate, which pointed at a query
rather than at load. When I traced the query the endpoint was generating, the pagination was
wrong. Instead of limiting the result set at the database, the query was pulling far more rows
than the page needed and the pagination was effectively being applied after the fact. Every
request was doing a large amount of work and then throwing most of it away.

The fix itself was not large once I understood it, which is often how these go. The
significant part was confirming the diagnosis before changing anything: I wanted to know that
the query was the cause and not just correlated with the symptom, so I checked the generated
SQL directly rather than trusting the ORM abstraction.

**Result.** Response time dropped by twenty times. The lesson I took from it is that the
slowest part of debugging is usually deciding where to look, and that an ORM will happily hide
a bad query behind reasonable-looking code. I now read the generated SQL early when something
is slow, rather than late.

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

## 6. Tell me about a time you found a security problem

**Situation.** I was looking at the access logs for a production Django application, a set of
public-facing sales pages, and there was a constant stream of automated probe traffic. Bots
scanning for exposed configuration files, backup files, source files, dependency manifests
like composer.json and requirements.txt, and WordPress and phpMyAdmin exploit paths.

**Task.** Nothing had been breached, but the application was answering these requests instead
of refusing them, and I wanted to know what was actually reachable before deciding what to do.

**Action.** I went through the categories one at a time and blocked five classes at the Nginx
gateway: dotfiles like .git and .env, source and config and backup extensions, build and
dependency filenames, CMS scanner paths, and PHP entirely, since it is a Python application
and no PHP should ever be served. I also turned off the Nginx version banner and added
baseline security headers. On the Django side I configured the app to trust the ingress TLS
termination and set session and CSRF cookies to secure outside debug mode.

Two decisions I want to mention. I found directory listing was enabled on the static path and
turned it off. And I deliberately did not add per-IP rate limiting, and I documented why: these
are public sales pages, and a lot of legitimate buyers from one company come through a single
corporate NAT address. Rate limiting there would have blocked real customers. Brute force
protection belonged at the application layer instead.

**Result.** Five classes of entry point removed from the public attack surface. I also
anchored the CMS-scanner rules carefully so that a marketing URL containing something like
"wp-admin" as part of a course name would not be blocked.

---

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
