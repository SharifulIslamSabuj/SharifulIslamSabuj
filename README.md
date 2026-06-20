<div align="center">

# Md. Shariful Islam

**Senior QA Automation Engineer &nbsp;·&nbsp; SDET &nbsp;·&nbsp; Automation Framework Architect**

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=flat&logo=linkedin&logoColor=white)](https://linkedin.com/in/islammdshariful)
&nbsp;
[![Email](https://img.shields.io/badge/Email-shariful.islam5417@gmail.com-EA4335?style=flat&logo=gmail&logoColor=white)](mailto:shariful.islam5417@gmail.com)
&nbsp;
[![GitHub](https://img.shields.io/badge/GitHub-SharifulIslamSabuj-181717?style=flat&logo=github&logoColor=white)](https://github.com/SharifulIslamSabuj)

</div>

---

13+ years building test automation infrastructure for enterprise software across insurance, healthcare, retail, and e-commerce. I design automation frameworks from first principles — architecture decisions, not just test scripts — and integrate quality gates into CI/CD pipelines that engineering teams can rely on in production.

My work spans the full testing spectrum: UI automation, REST API validation, mobile automation, and performance engineering. I have led QA strategy for systems at the scale of MetLife's Core Life Insurance platform, and delivered automation that reduced manual regression effort by 40% across multiple organizations.

---

## About Me

I started in QA in 2011 doing manual testing and defect management. Over 13 years I moved progressively into automation engineering, framework architecture, and quality process leadership — building each layer on top of the last rather than abandoning one for the next.

What distinguishes my work from standard QA automation:

- **I build frameworks, not just scripts.** At every organization I have joined, I have designed the automation architecture from scratch — driver management, configuration systems, test data strategies, reporting pipelines — before writing the first test case.
- **I treat test architecture as software architecture.** Thread safety, separation of concerns, explicit waits, typed exceptions, clean configuration management. The same decisions that make production code maintainable make automation frameworks maintainable.
- **I connect automation to delivery.** Automation that runs only locally is a local tool. My frameworks are built to run in CI/CD pipelines — on every push, with artifacts published and failures visible to the team.
- **I understand the business layer.** Leading UAT for MetLife's Core Life Insurance Solution — managing 100+ business scenarios, defect triage with stakeholders, traceability matrices — required understanding what "correct behavior" meant for an insurance system, not just what the UI rendered.

---

## Core Technical Expertise

### Automation Engineering

| Capability | Technologies |
|---|---|
| **Web Automation** | Selenium WebDriver 4, Page Object Model, Fluent API, Thread-Safe Driver Management (ThreadLocal) |
| **BDD Frameworks** | Cucumber 7, Gherkin, Step Definitions, Hooks, tag-based suite management |
| **API Automation** | REST Assured, Postman, POJO-based serialization, token management, E2E workflow validation |
| **Mobile Automation** | Appium, Android (Emulator + Real Device) |
| **Performance Testing** | Apache JMeter, Load Testing, Stress Testing, bottleneck identification |
| **Security Testing** | OWASP ZAP (trained) |
| **Test Runners** | TestNG (parallel DataProvider), JUnit |
| **Data-Driven Testing** | Excel (Apache POI), API-generated data, parameterized test suites |

### Programming & Design

| Area | Detail |
|---|---|
| **Language** | Java 17 — primary automation language across all roles |
| **OOP & Design Patterns** | Builder, Singleton, Factory, Page Object, Layered Architecture |
| **Code Quality** | Clean code principles, private locators, typed exception hierarchies, zero `Thread.sleep()` |
| **Database** | SQL — test data validation and database state verification |

### DevOps & Infrastructure

| Area | Technologies |
|---|---|
| **CI/CD** | GitHub Actions, Jenkins, Azure DevOps |
| **Containerization** | Docker (multi-stage builds, Compose), Selenium Grid 4 (Hub + Node), noVNC |
| **Build Tools** | Gradle 9, Maven |
| **Version Control** | Git, GitHub |

### Reporting & Observability

Allure Reports (trend graphs, history) &nbsp;·&nbsp; ExtentReports (interactive HTML) &nbsp;·&nbsp; Cucumber HTML &nbsp;·&nbsp; TestNG Reports &nbsp;·&nbsp; SLF4J + Logback with MDC thread tracing

### Quality Process & Governance

Test Strategy Design &nbsp;·&nbsp; UAT Leadership &nbsp;·&nbsp; Defect Lifecycle Management &nbsp;·&nbsp; RTM &nbsp;·&nbsp; CMMI Level 5 &nbsp;·&nbsp; ISO 9001 / QMS &nbsp;·&nbsp; Agile / Scrum

---

## Automation Architecture Skills

These are the decisions that separate maintainable automation from technical debt:

**Thread-Safe Parallel Execution**
Using `ThreadLocal<WebDriver>` to isolate browser instances per test thread, combined with TestNG's `@DataProvider(parallel=true)`, allows true parallel execution without race conditions or shared state. This is not a configuration toggle — it requires deliberate driver lifecycle management in `@Before` and `@After` hooks.

**Environment-Aware Configuration**
A 4-level priority chain (JVM system property → environment variable → properties file → built-in default) means the same codebase runs locally, in Docker, on Selenium Grid, and in GitHub Actions CI without code changes. Credentials flow through environment variables and GitHub Secrets — never into source control.

**API-First Test Data Setup**
Registering test users via HTTP API (Java `HttpClient`) rather than UI flows removes a fragile dependency on registration pages. Tests set up their own preconditions programmatically, which makes the suite faster and decouples test data creation from the feature under test.

**Typed Exception Hierarchy**
A `FrameworkException` base class with specific subtypes (`WaitException`, `DriverInitializationException`) lets the framework distinguish between a test failure and an infrastructure failure — and handle each appropriately without swallowing errors in generic `catch(Exception)` blocks.

**Layered API Architecture**
Separating the test layer (what to validate) from the service layer (business logic) from the client layer (HTTP execution) means individual tests are readable, service methods are reusable across tests, and the HTTP client can be modified without touching any test logic.

---

## Featured Engineering Projects

### BDD Automation Framework — ParaBank Banking Application

[![CI](https://github.com/SharifulIslamSabuj/BDDFramework-ParabankAutomation/actions/workflows/automation-test.yml/badge.svg)](https://github.com/SharifulIslamSabuj/BDDFramework-ParabankAutomation/actions)
&nbsp;&nbsp;
[![Java](https://img.shields.io/badge/Java-17-007396?logo=openjdk&logoColor=white)](https://openjdk.org/)
[![Selenium](https://img.shields.io/badge/Selenium-4-43B02A?logo=selenium&logoColor=white)](https://www.selenium.dev/)
[![Cucumber](https://img.shields.io/badge/Cucumber-7-23D96C?logo=cucumber&logoColor=white)](https://cucumber.io/)
[![Docker](https://img.shields.io/badge/Docker-enabled-2496ED?logo=docker&logoColor=white)](https://www.docker.com/)

**The problem this solves:** Most automation portfolios demonstrate that someone can write Selenium scripts. This project demonstrates what comes after that — the framework decisions that determine whether automation scales or collapses: how do you manage drivers across parallel threads? How do you configure 4 environments without duplicating code? How do you set up test data without relying on brittle UI flows?

**Architecture highlights:**

- **BDD layer:** Cucumber 7 + Gherkin feature files with TestNG parallel `@DataProvider`. Scenarios run concurrently with full thread isolation.
- **Driver management:** `DriverManager` (ThreadLocal) + `DriverFactory` (local vs. RemoteWebDriver) — same code routes to Chrome locally, Docker container, or Selenium Grid based on config.
- **Page Object layer:** `BasePage` with reflection-based typed `createPage()` factory. Locators are private `By` fields — step definitions never call `driver.findElement()` directly.
- **Test data:** Three independent strategies — API registration via Java `HttpClient` (primary), Excel DDT via Apache POI (data-driven scenarios), LoremIpsum generated data (no PII in source).
- **Configuration:** 4-level priority chain across 4 environments (qa / staging / uat / prod). Credentials via GitHub Secrets — never committed.
- **Infrastructure:** Multi-stage Dockerfile, `docker-compose.yml` for local container execution, `docker-compose.grid.yml` for Hub + Chrome Node + noVNC live session viewing.
- **CI/CD:** GitHub Actions pipeline — Chrome stable + Xvfb virtual display, artifact upload on failure, concurrency cancel-in-progress for stale runs.
- **Reporting:** ExtentReports, Allure, Cucumber HTML, TestNG — all generated per run. Failure screenshots embedded automatically.
- **Exception handling:** Typed hierarchy (`FrameworkException` → `WaitException`, `DriverInitializationException`) — infrastructure failures are distinguishable from test failures.

[View Repository](https://github.com/SharifulIslamSabuj/BDDFramework-ParabankAutomation)

---

### API Automation Framework — Grocery Store REST APIs

[![Java](https://img.shields.io/badge/Java-17-007396?logo=openjdk&logoColor=white)](https://openjdk.org/)
[![REST Assured](https://img.shields.io/badge/REST_Assured-API-green)](https://rest-assured.io/)
[![TestNG](https://img.shields.io/badge/TestNG-runner-orange)](https://testng.org/)
[![Allure](https://img.shields.io/badge/Allure-reporting-yellow)](https://allurereport.org/)

**The problem this solves:** API tests written directly in test classes become unreadable and unreusable quickly. Every test knows the HTTP details, the business logic, and the assertion — mixing three concerns in one place. This framework separates them: tests express intent, service methods encode business logic, the client handles HTTP.

**Architecture highlights:**

- **3-layer structure:** Test layer → Service layer (`CartService`, `OrderService`) → Client layer (`ApiClient`). Changing the HTTP library requires touching only the client layer.
- **POJO modeling:** Request and response bodies are typed Java objects, not raw JSON strings. Serialization and deserialization are handled centrally.
- **Token management:** `TokenManager` (Singleton) generates and caches authentication tokens. Secured endpoints receive valid tokens without each test managing auth independently.
- **E2E workflow validation:** Full order placement flow — get products → create cart → add item → place order — validated as a single end-to-end scenario in addition to individual endpoint tests.
- **Design patterns:** Builder (request construction), Singleton (token management), Layered Architecture throughout.

[View Repository](https://github.com/SharifulIslamSabuj/api-automation-framework)

---

### Additional Projects

| Project | What it demonstrates | Stack |
|---|---|---|
| [ParabankAutomation-AdvancedFramework](https://github.com/SharifulIslamSabuj/ParabankAutomation-AdvancedFramework) | POM framework with parallel execution, data-driven testing, dual reporting | Java · Selenium · TestNG · ExtentReports · Allure |
| [MobileAutomation-Appium](https://github.com/SharifulIslamSabuj/MobileAutomation-Appium) | Android automation on emulator and real device | Java · Appium · TestNG · Allure |

---

## Professional Experience

**ADN DigiNet Limited — Principal Engineer, Test Automation** *(Sep 2024 – Mar 2025)*
Designed and built Selenium + Java automation frameworks; automated 80+ critical regression scenarios; implemented REST Assured API testing and JMeter performance testing; integrated test execution into Jenkins CI/CD pipelines.

**ADN DigiNet / MetLife Inc. — Test Orchestrator, Core Life Insurance UAT** *(Jan 2024 – Aug 2024)*
Led enterprise UAT execution for MetLife's Core Life Insurance Solution. Managed 100+ business scenarios end-to-end, ran defect triage with cross-functional stakeholders, maintained RTM, and delivered QA release reports that supported go/no-go decisions.

**LEADS Corporation Limited — Sr. SQA Engineer / Lead Process Engineer** *(Feb 2015 – Dec 2023)*
Led QA across enterprise systems used by FedEx, Walmart, ASOS, Tesco, Kaiser Permanente, and Aetna. Drove QA process improvement and governance aligned with ISO 9001 and CMMI standards. Reduced defect leakage by 30%. Delivered manual and automation testing across web and mobile platforms at scale.

**RootNext Solutions Ltd. — Sr. SQA Engineer** *(Mar 2013 – Jan 2015)*
Built Selenium + Java + TestNG automation frameworks from scratch; automated 50+ regression test cases; conducted cross-browser and real-device mobile testing.

**ServicEngineBPO — Software Test Engineer** *(Sep 2011 – Mar 2013)*
Manual functional and regression testing; defect lifecycle management; digital accessibility testing for UsableNet Inc. across real devices and multiple browsers.

---

## Process Leadership & Knowledge Transfer

At LEADS Corporation, I drove QA process improvement across multiple enterprise product lines — introducing structured test strategy documentation, standardising defect classification and triage workflows, and aligning QA practices with ISO 9001 and CMMI Level 5 standards. These initiatives reduced defect leakage by 30% and improved test execution consistency across teams.

For the MetLife Core Life Insurance UAT program, I built the end-to-end testing process from scratch: requirements traceability matrix, scenario prioritisation, defect lifecycle management, and release-readiness reporting for senior stakeholders. The goal was to give decision-makers a clear signal — not a test case count.

I document automation architecture decisions in depth, writing repository READMEs that explain the engineering rationale behind each framework choice. The expectation is that a new engineer joining the team should understand not just how to run the tests, but why the framework is structured the way it is.

---

## Currently Exploring

- Cloud-based test infrastructure — BrowserStack and Sauce Labs for cross-browser scale
- Security testing in CI pipelines — OWASP ZAP integration with GitHub Actions
- Distributed performance engineering — JMeter in distributed execution mode
- Test observability — flaky test detection, test result trend analysis

---

## GitHub Activity

<div align="center">

![GitHub Stats](https://github-readme-stats.vercel.app/api?username=SharifulIslamSabuj&show_icons=true&theme=default&hide_border=true&count_private=true)

![Top Languages](https://github-readme-stats.vercel.app/api/top-langs/?username=SharifulIslamSabuj&layout=compact&theme=default&hide_border=true)

</div>

---

## Connect

I am open to Senior QA Automation Engineer, SDET, and QA Lead roles — particularly with teams building enterprise software at scale.

| | |
|---|---|
| **LinkedIn** | [linkedin.com/in/islammdshariful](https://linkedin.com/in/islammdshariful) |
| **Email** | [shariful.islam5417@gmail.com](mailto:shariful.islam5417@gmail.com) |
| **GitHub** | [github.com/SharifulIslamSabuj](https://github.com/SharifulIslamSabuj) |
| **Location** | Dhaka, Bangladesh &nbsp;·&nbsp; Open to remote roles |

---

<div align="center">

*M.Sc. in Computer Science & Engineering — University of Rajshahi*

</div>
