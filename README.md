<div align="center">

# Md. Shariful Islam

### Senior QA Automation Engineer &nbsp;·&nbsp; SDET &nbsp;·&nbsp; Automation Framework Architect

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=flat&logo=linkedin&logoColor=white)](https://linkedin.com/in/islammdshariful)
&nbsp;&nbsp;
[![Email](https://img.shields.io/badge/Email-shariful.islam5417%40gmail.com-EA4335?style=flat&logo=gmail&logoColor=white)](mailto:shariful.islam5417@gmail.com)
&nbsp;&nbsp;
[![GitHub](https://img.shields.io/badge/GitHub-SharifulIslamSabuj-181717?style=flat&logo=github&logoColor=white)](https://github.com/SharifulIslamSabuj)

**13+ Years &nbsp;·&nbsp; Enterprise Software &nbsp;·&nbsp; Insurance · Healthcare · Retail · E-commerce &nbsp;·&nbsp; Open to Remote**

</div>

---

QA engineer who designs automation infrastructure, not just test scripts. I build frameworks from first principles — thread-safe parallel execution, environment-aware configuration, API-driven test data, typed exception hierarchies — and integrate them into CI/CD pipelines that teams can rely on in production. I have led QA strategy for systems at the scale of MetLife's Core Life Insurance platform, delivered automation that reduced manual regression effort by 40%, and driven quality governance aligned with CMMI Level 5 and ISO 9001 across enterprise product suites serving FedEx, Walmart, ASOS, and Kaiser Permanente.

---

## About Me

What separates senior automation engineers from tool operators is the set of decisions made before the first test is written. Over 13 years — starting with manual testing in 2011 and moving progressively through automation engineering, framework architecture, and quality leadership — I have learned which decisions matter:

- **Framework design before test design.** Driver management strategy, configuration priority chain, test data independence, reporting pipeline, and exception hierarchy are architecture decisions. They determine whether a suite is maintainable at 500 tests the same way it was at 50.
- **Test architecture mirrors software architecture.** Thread safety, separation of concerns, private locators, explicit waits. The standards that make production code durable make automation durable.
- **Automation belongs in the pipeline, not on a laptop.** CI/CD integration — artifact publishing, concurrency control, environment switching — is what turns a local test suite into a team-level quality signal.
- **Quality engineering requires business context.** Leading UAT for MetLife's Core Life Insurance Solution meant understanding what "correct" meant for an insurance claim workflow, not just what the UI rendered. Requirement traceability, stakeholder defect triage, and release-readiness reporting are part of the job.
- **Senior engineers raise the floor, not just their own ceiling.** Introducing structured QA processes, coaching engineers on automation best practices, and documenting architectural decisions so new team members can contribute without asking — this is what makes quality improvements lasting.

---

## Technical Skills

**Test Automation**

| Area | Technologies & Practices |
|---|---|
| Web Automation | Selenium WebDriver 4, Page Object Model, Fluent API, `ThreadLocal` driver management |
| BDD | Cucumber 7, Gherkin, Step Definitions, Hooks, tag-based suite selection |
| API Automation | REST Assured, Postman, POJO serialization, token management, E2E workflow validation |
| Mobile Automation | Appium, Android (Emulator + Real Device) |
| Performance Testing | Apache JMeter, Load & Stress Testing, bottleneck identification |
| Security Testing | OWASP ZAP (trained, CI pipeline integration) |
| Test Runners | TestNG (parallel `@DataProvider`), JUnit |
| Data Strategies | Excel DDT (Apache POI), API-generated data, parameterized suites — no PII in source |

**Engineering**

| Area | Detail |
|---|---|
| Language | Java 17 — primary automation language across all roles and frameworks |
| Design Patterns | Builder, Singleton, Factory, Page Object, Layered Architecture |
| Code Practices | Typed exception hierarchies, explicit waits only, private locators, clean configuration |
| Database | SQL — test data setup, state verification, post-condition validation |

**DevOps & Infrastructure**

| Area | Technologies |
|---|---|
| CI/CD | GitHub Actions, Jenkins, Azure DevOps |
| Containers | Docker (multi-stage builds, Compose), Selenium Grid 4 (Hub + Node + noVNC) |
| Build | Gradle 9, Maven |
| Reporting | Allure (trend graphs), ExtentReports (interactive HTML), Cucumber HTML, Logback + SLF4J MDC |

**Quality Process**

Test Strategy &nbsp;·&nbsp; UAT Leadership &nbsp;·&nbsp; Defect Lifecycle Management &nbsp;·&nbsp; RTM &nbsp;·&nbsp; CMMI Level 5 &nbsp;·&nbsp; ISO 9001 / QMS &nbsp;·&nbsp; Agile / Scrum

---

## Automation Architecture Decisions

These are the framework decisions that separate maintainable automation from technical debt. Each one is demonstrated in the portfolio projects below.

**Thread-Safe Parallel Execution**
`ThreadLocal<WebDriver>` isolates browser instances per test thread. Combined with TestNG's `@DataProvider(parallel=true)`, scenarios run concurrently without shared state or race conditions. This requires deliberate driver lifecycle management in `@Before` / `@After` hooks — it is not a configuration flag.

**Environment-Aware Configuration**
A 4-level priority chain (JVM system property → environment variable → properties file → built-in default) means the same codebase runs locally, in Docker, on Selenium Grid, and in GitHub Actions CI without code changes. Credentials flow through environment variables and GitHub Secrets — never committed to source control.

**API-First Test Data**
Registering test state via HTTP API (`Java HttpClient`) rather than UI flows removes fragile dependencies on registration pages, makes suites faster, and decouples test data creation from the feature being tested. Browser-based fallback is retained where the API path is unavailable.

**Typed Exception Hierarchy**
A `FrameworkException` base with specific subtypes (`WaitException`, `DriverInitializationException`) allows the framework to distinguish between a test failure and an infrastructure failure. This prevents infrastructure problems from surfacing as misleading test failures.

**Layered API Architecture**
Test layer (what to validate) → Service layer (business logic) → Client layer (HTTP execution). Tests remain readable. Service methods are reusable across test classes. The HTTP client is replaceable without touching any test logic.

---

## Featured Projects

### BDD Automation Framework — ParaBank Banking Application

[![CI](https://github.com/SharifulIslamSabuj/BDDFramework-ParabankAutomation/actions/workflows/automation-test.yml/badge.svg)](https://github.com/SharifulIslamSabuj/BDDFramework-ParabankAutomation/actions)
&nbsp;
[![Java](https://img.shields.io/badge/Java-17-007396?logo=openjdk&logoColor=white)](https://openjdk.org/)
&nbsp;
[![Selenium](https://img.shields.io/badge/Selenium-4-43B02A?logo=selenium&logoColor=white)](https://www.selenium.dev/)
&nbsp;
[![Cucumber](https://img.shields.io/badge/Cucumber-7-23D96C?logo=cucumber&logoColor=white)](https://cucumber.io/)
&nbsp;
[![Docker](https://img.shields.io/badge/Docker-Compose-2496ED?logo=docker&logoColor=white)](https://www.docker.com/)

**Problem it solves:** Most automation portfolios show that someone can write Selenium scripts against a demo app. This project demonstrates what comes after: the framework decisions that determine whether a test suite scales or becomes a maintenance burden. How do you manage WebDriver instances across 4 parallel threads without shared state? How do you configure 4 deployment environments without duplicating code? How do you create test users without relying on brittle UI registration flows?

**Engineering decisions:**

| Decision | Implementation |
|---|---|
| Parallel execution | TestNG `@DataProvider(parallel=true)` + `ThreadLocal<WebDriver>` — full thread isolation |
| Driver routing | `DriverFactory` creates `ChromeDriver` locally or `RemoteWebDriver` for Selenium Grid — switched via config, not code |
| Page Object layer | `BasePage` with reflection-based typed `createPage()` factory — step definitions never call `driver.findElement()` directly |
| Test data | 3 independent strategies: API registration (primary), Excel DDT via Apache POI, generated data via LoremIpsum |
| Configuration | 4-level priority chain across 4 environments (qa / staging / uat / prod) |
| Infrastructure | Multi-stage Dockerfile + `docker-compose.yml` (local) + `docker-compose.grid.yml` (Hub + Node + noVNC) |
| CI/CD | GitHub Actions — Chrome stable + Xvfb, artifact upload on failure, concurrency cancel-in-progress |
| Reporting | ExtentReports, Allure, Cucumber HTML, TestNG — all generated per run with failure screenshots embedded |
| Exception handling | Typed hierarchy: `FrameworkException` → `WaitException`, `DriverInitializationException` |
| Security | No credentials in source; GitHub Secrets integration; passwords never logged |

[View Repository →](https://github.com/SharifulIslamSabuj/BDDFramework-ParabankAutomation)

---

### API Automation Framework — Grocery Store REST APIs

[![Java](https://img.shields.io/badge/Java-17-007396?logo=openjdk&logoColor=white)](https://openjdk.org/)
&nbsp;
[![REST Assured](https://img.shields.io/badge/REST_Assured-6-green)](https://rest-assured.io/)
&nbsp;
[![TestNG](https://img.shields.io/badge/TestNG-7-orange)](https://testng.org/)
&nbsp;
[![Allure](https://img.shields.io/badge/Allure-Reports-yellow)](https://allurereport.org/)

**Problem it solves:** API tests written directly in test classes mix three concerns in one place: what to validate, the business logic behind the validation, and the HTTP mechanics of making the call. This makes tests long, hard to read, and impossible to reuse. This framework separates those concerns into three explicit layers.

**Engineering decisions:**

| Decision | Implementation |
|---|---|
| Layered architecture | Test → Service (`CartService`, `OrderService`) → Client (`ApiClient`) — one responsibility per layer |
| Request modeling | POJO-based serialization — typed Java objects, not raw JSON strings |
| Token management | `TokenManager` (Singleton) — dynamic token generation and caching; no test manages auth independently |
| E2E validation | Full order flow: get products → create cart → add item → place order — one coherent end-to-end scenario |
| Design patterns | Builder (request construction), Singleton (token), Layered Architecture throughout |

[View Repository →](https://github.com/SharifulIslamSabuj/api-automation-framework)

---

### Additional Portfolio

| Project | Engineering Value | Stack |
|---|---|---|
| [ParabankAutomation-AdvancedFramework](https://github.com/SharifulIslamSabuj/ParabankAutomation-AdvancedFramework) | Parallel POM framework with data-driven testing and dual reporting (ExtentReports + Allure) | Java · Selenium · TestNG · Gradle |
| [MobileAutomation-Appium](https://github.com/SharifulIslamSabuj/MobileAutomation-Appium) | Android automation — same test code executes on emulator and real device | Java · Appium · TestNG · Allure |

---

## Engineering Philosophy

**Automation is an investment, not a one-time task.** A framework that runs correctly for two years and degrades slowly is worth more than one that passes all tests on day one and collapses after the first refactor. Architectural discipline up front is the cheapest maintenance strategy available.

**Test failures should be informative, not ambiguous.** When a test fails, the output should tell you whether the application broke, the infrastructure broke, or the test data broke. These are three different problems with three different resolution paths. Frameworks that conflate them waste engineering time.

**Coverage is a lagging indicator.** The goal is not a high test count — it is confident release decisions. A suite of 50 well-designed, well-maintained tests that gives the team genuine confidence is more valuable than 500 flaky tests that nobody trusts.

**Quality processes outlast any individual tool.** The test strategy, defect classification system, and reporting structure that an engineering team internalises will still be delivering value after the specific tools have been replaced or upgraded. Investing in process is investing in durability.

**Documentation is part of the deliverable.** An automation framework that only the author understands is a single point of failure. Architecture decisions, configuration options, and execution instructions belong in the repository — not in someone's head.

---

## Professional Experience

**ADN DigiNet Limited — Principal Engineer, Test Automation** *(Sep 2024 – Mar 2025)*
Designed and built Selenium + Java automation frameworks; automated 80+ critical regression scenarios; implemented REST Assured API testing and JMeter performance testing; integrated test execution into Jenkins CI/CD pipelines. Advised on test architecture, execution strategy, and reporting standards.

**ADN DigiNet / MetLife Inc. — Test Orchestrator, Core Life Insurance UAT** *(Jan 2024 – Aug 2024)*
Led enterprise UAT execution for MetLife's Core Life Insurance Solution — 100+ business scenarios end-to-end. Built the testing process from scratch: requirements traceability matrix, defect lifecycle management, and release-readiness reporting for senior stakeholders. Managed defect triage across cross-functional teams and delivered structured QA reports that supported go/no-go release decisions.

**LEADS Corporation Limited — Sr. SQA Engineer / Lead Process Engineer** *(Feb 2015 – Dec 2023)*
Led QA across enterprise systems serving FedEx, Walmart, ASOS, Tesco, Kaiser Permanente, and Aetna. Drove QA process improvement and governance aligned with ISO 9001 and CMMI Level 5 standards. Reduced defect leakage by 30%. Mentored QA engineers on automation practices, test strategy, and structured defect management. Delivered functional, regression, and automation testing across web and mobile platforms at enterprise scale.

**RootNext Solutions Ltd. — Sr. SQA Engineer** *(Mar 2013 – Jan 2015)*
Built Selenium + Java + TestNG automation frameworks from scratch; automated 50+ regression test cases; conducted cross-browser and real-device mobile testing. Guided junior engineers on test case design and automation patterns.

**ServicEngineBPO — Software Test Engineer** *(Sep 2011 – Mar 2013)*
Manual functional and regression testing; defect lifecycle management using Jira; digital accessibility testing for UsableNet Inc. across real devices and multiple browsers.

---

## QA Leadership & Mentoring

Across 13 years and multiple organisations, leadership has taken three forms:

**Process governance.** At LEADS Corporation, I introduced structured test strategy documentation, standardised defect classification workflows, and aligned QA practices with ISO 9001 and CMMI Level 5 — reducing defect leakage by 30% and improving consistency across teams working on different product lines simultaneously.

**UAT program ownership.** For MetLife's Core Life Insurance UAT engagement, I designed the entire testing programme: scenario inventory, traceability matrix, triage process, and stakeholder reporting. The output was a release confidence signal — not a spreadsheet of test case statuses.

**Coaching and documentation.** I have guided QA engineers on automation framework usage, test case design principles, and structured defect management. I write repository documentation at a depth where a new engineer should understand not just how to run the tests, but why each framework decision was made — so the knowledge is not lost when people move on.

---

## Currently Exploring

- Cloud-based test infrastructure — BrowserStack and Sauce Labs for cross-browser scale without local grid overhead
- Security testing in CI — OWASP ZAP integration in GitHub Actions pipelines
- Distributed performance engineering — JMeter in distributed execution mode for realistic load simulation
- Test observability — flaky test detection, historical trend analysis, test result dashboards

---

## GitHub Activity

<div align="center">

![GitHub Stats](https://github-readme-stats.vercel.app/api?username=SharifulIslamSabuj&show_icons=true&theme=default&hide_border=true&count_private=true)
&nbsp;&nbsp;
![Top Languages](https://github-readme-stats.vercel.app/api/top-langs/?username=SharifulIslamSabuj&layout=compact&theme=default&hide_border=true)

</div>

---

## Connect

Available for **Senior QA Automation Engineer, SDET, QA Lead, and Automation Architect** roles — remote-first, open to global opportunities.

| | |
|---|---|
| **LinkedIn** | [linkedin.com/in/islammdshariful](https://linkedin.com/in/islammdshariful) |
| **Email** | [shariful.islam5417@gmail.com](mailto:shariful.islam5417@gmail.com) |
| **GitHub** | [github.com/SharifulIslamSabuj](https://github.com/SharifulIslamSabuj) |
| **Location** | Dhaka, Bangladesh &nbsp;·&nbsp; Remote-first &nbsp;·&nbsp; Open to global opportunities |

---

<div align="center">

*M.Sc. in Computer Science & Engineering — University of Rajshahi*

</div>
