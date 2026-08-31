# Open Questions

Most of the original list was answered in the 2026-08-31 interview. What remains is here.

---

## Answered, for the record

| Question | Answer |
| --- | --- |
| Basis for R9's 90% | Marketing built each section and its items by hand, ~30 min; cloning made it ~2 min. Arithmetic is 93%; 90% kept as conservative. |
| Worker pod cost (W1) | ~1 of 13 pods, idle most of the time. **Rejected**: uncertain, and 8% is weak beside 20x/90%/100%. W1 stays without a Y. |
| Diploma issuance (R7) | Three wins confirmed: capability (company could not issue diplomas at all before), time (**85%**), cost (~R$1,000/certificate to a partner university). Time chosen; volume unknown so no currency figure. |
| Certificates vs diplomas | Different subsystems. `CertificateRequest` was created by Isac Sousa; the DiplomaBook/Registry is Gabriel's. Credentials carried by R7 alone. |
| Delinquency collections outcome (W2) | Unknown, not recoverable. W2 stays without a Y. |
| Migration time saved (W14) | Modeled at **75%** from observed throughput: 42 files/day manual (Jun 8) vs 685/day with skills (Jun 15), amortized over 2 days building the tooling. |
| Symfony migration outcome (W6) | **Contract ended before deploy.** No completion claim is available. |
| CRM lead sync rate (R11) | Failure rate unknown. Y reframed as a capability: **100% recoverable**, provable from the custom result backend. |
| Bulk update scale (R12) | 8 sales pages in the catalog, so 8 operations became 1: **87%**. |
| Is FastAPI real? | **Yes.** Technical Challenge Reviewer and ATSProof. It can now go in a bullet. |
| Is LangChain real? | **Yes.** Technical Challenge Reviewer pins langchain, langchain-core, langchain-openai, langchain-google-genai. Keep it on the resume. |
| MCP and multi-agent? | **Yes**, in DevATS: `.agents/mcp_config.json`, ADR-0003/0004 multi-agent contract decoupling, agent-targetable DOM identifiers. |
| Which AI dev tools? | Claude Code skills (7 of 12 authored in codeplatform), MCP, and an "Antigravity Agent" co-attributed in DevATS ADR-0002. |

---

## Still open

### Would strengthen existing bullets

1. **Go.** Any from the Full Cycle MBA (Arquitetura) or elsewhere? Full Cycle is a Go-centric
   company. This has blocked a hard requirement on more than one JD. Worth roughly +8 points
   where it appears.
2. **Java / Spring Boot.** Any, even academic? Currently zero.
3. **Kafka.** Zero. Celery and webhooks are the same problem space, not the same tool.

### Would supply a denominator for every bullet

No repository can answer these. Each one strengthens the whole set by giving scale:

4. **Students on the platform** — total, or monthly active.
5. **Traffic** — requests per day, or peak concurrent.
6. **Immediate team size** — engineers worked with daily, not the 20+ repo contributors.

"Cut query latency 80%" is good. "Cut query latency 80% on a platform serving 50,000
students" is better.

### Would unlock the two NO Y entries

7. **W1:** monthly cost of the eliminated worker pod, if it is ever recoverable from an old
   invoice or dashboard.
8. **W2:** any collections outcome from the delinquency program — recovery rate, revenue
   recovered, or finance-team hours saved.

---

## Where to look

- **New Relic.** `eventsplatform` and `forum-code-education` both commit a `newrelic.ini`. If
  access remains, it holds throughput, response times, and error rates: it would answer the
  traffic question and could produce genuine before/after numbers for the performance bullets.
- **The `plans/` and `docs/` directories** in codeplatform. Feature specs often state the
  problem in measurable terms.
- **Former colleagues on the business side.** For platform scale and the delinquency outcome,
  someone knows these cold. Asking is legitimate.

## Rule

Do not invent a number. A bullet with a real X and Z and no Y still beats a fabricated Y that
collapses in an interview. If a Y cannot be recovered, the entry stays without one.
