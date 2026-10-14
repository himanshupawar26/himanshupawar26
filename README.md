<div align="center">

# Himanshu Pawar

### ServiceNow Developer & SDET

[![Email](https://img.shields.io/badge/Email-himanshupawar.work%40gmail.com-D14836?logo=gmail&logoColor=white)](mailto:himanshupawar.work@gmail.com)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-himanshupawar26-0A66C2?logo=linkedin&logoColor=white)](https://www.linkedin.com/in/himanshupawar26)

</div>

I build on the ServiceNow platform — Fluent scoped apps, Agent Studio AI agents, Flow Designer/IntegrationHub automation — and I test what I build, across both the ServiceNow stack and general web/API automation (Selenium, Playwright, Cucumber, REST Assured).

The four repos below are deliberately **one cohesive project**, not four unrelated demos. They're built around a single small-business operations domain, **BizOps360** (inventory, sales orders, purchase orders, lightweight reporting), so the app, the AI agent on top of it, the autonomous automation on top of that, and the testing frameworks around all of it fit together the way they would on a real team, instead of being four disconnected "hello world" exercises.

---

## 🧩 BizOps360 — ServiceNow platform

A small-business ops domain spanning three layers: a core scoped app, a conversational AI agent on top of it, and an autonomous automation pipeline alongside it. All three are private repos — happy to share access on request. **Status: design complete** (full `PLAN.md` / data model / flows / security model docs written for each); **build is pending PDI provisioning** (signed up, currently waitlisted).

| Repo | What it is |
|---|---|
| **bizops360-app** | The core Fluent scoped app: inventory, sales orders, purchase orders, and a reporting layer — explicitly *not* a POS and *not* an accounting system. 8 tables, 3 roles with row- and field-level ACLs, 3 Flow Designer flows with real branching logic. Stock levels are computed from an immutable, append-only Stock Movement ledger rather than a directly-editable field. |
| **bizops360-store-assistant** | A conversational AI agent (Agent Studio) on top of the app. Answers questions about stock/sales/orders and *proposes* — never silently executes — restock actions, under the same role-based ACLs as the app. 5 tool definitions, grounding/guardrail rules, a 10-scenario eval set. |
| **bizops360-replenishment-pipeline** | An autonomous nightly Flow Designer/IntegrationHub pipeline, no chat interface. Depletion-rate stockout detection, reuses the app's PO lifecycle and duplicate-prevention, a 5-row escalation table for ambiguous cases, idempotency requirements, and a structured audit log. Reactive-and-human-confirmed (the Store Assistant) vs. autonomous-and-exception-escalated (this pipeline) — the two are explicitly compared in its docs. |
| **bizops360-e2e-tests** *(planned)* | Playwright + JavaScript end-to-end suite against `bizops360-app`, covering both the UI and the AI agent's proposed-action flows. Starts once the app exists. |

## 🧪 Test Automation

Two public frameworks, each rebuilt from a stale course exercise into something CI-verified against a live target, in a different language/tooling combination on purpose — to show range, not to pad a repo count.

| Repo | Stack | Status |
|---|---|---|
| **[API-Automation-Testing-BDD-Framework](https://github.com/himanshupawar26/API-Automation-Testing-BDD-Framework)** | Java 17 · Cucumber 7 (JUnit Platform Suite) · REST Assured 5 · Allure · GitHub Actions | 12 scenarios / 42 steps passing against the live [ReqRes](https://reqres.in) API. [Live Allure report](https://himanshupawar26.github.io/API-Automation-Testing-BDD-Framework/). |
| **[Selenium-AutomationTesting-DDF-Framework](https://github.com/himanshupawar26/Selenium-AutomationTesting-DDF-Framework)** | Java 17 · Selenium 4 · TestNG 7 · ExtentReports · GitHub Actions | Page Object Model, CSV-driven login coverage, thread-safe parallel execution, against the live [Sauce Labs demo site](https://www.saucedemo.com). [Live Extent report](https://himanshupawar26.github.io/Selenium-AutomationTesting-DDF-Framework/). |

Once `bizops360-app` exists, it becomes a second target for the REST Assured/Cucumber framework (API layer) and the home of the planned Playwright suite (UI + agent layer).

---

<div align="center">

<sub>Built fresh, on personal time, against a personal PDI — nothing here is copied or reconstructed from any employer's internal code, schemas, or designs.</sub>

</div>
