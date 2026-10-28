# QA Portfolio — SauceDemo Web Store and Restful-Booker API

End-to-end QA project by **Yasmin Sosa**, from exploratory testing to a documented release recommendation, plus an automated API test suite in Postman.

- **Web application:** [SauceDemo](https://www.saucedemo.com), a practice e-commerce store by Sauce Labs
- **API:** [Restful-Booker](https://restful-booker.herokuapp.com), a practice hotel booking API
- **Browsers:** Chrome and Safari on macOS

## Results at a glance
| Area | Result |
|---|---|
| Requirements covered | 11 / 11 (100%) |
| Manual test cases executed | 22 / 22 in Chrome and Safari |
| Pass rate | 86% (19 passed, 3 failed, each linked to a bug) |
| Critical (P1) test cases | 7 / 7 passed in both browsers |
| Bugs reported | 4 (2 Medium, 2 Low), with steps, evidence, and impact |
| API tests (Postman) | 17 / 17 passed across 8 requests |

## What is in this repository
| Folder | Contents |
|---|---|
| [00-exploratory-notes](./00-exploratory-notes/Exploratory_Session_SauceDemo.md) | Exploratory session used to learn the app and find early defects |
| [01-test-plan](./01-test-plan/Test_Plan_SauceDemo.md) | Test plan: scope, requirements traceability, approach, entry and exit criteria, risks, and metrics |
| [02-test-cases](./02-test-cases/) | 22 test cases with steps, data, and results in two browsers, plus a downloadable spreadsheet |
| [03-bug-reports](./03-bug-reports/) | 4 bug reports with severity, priority, steps to reproduce, and screenshots or video |
| [04-api-testing](./04-api-testing/) | Postman collection for the booking lifecycle (auth and CRUD) with automated tests |

## Bugs found
| ID | Summary | Severity |
|---|---|---|
| [BUG-001](./03-bug-reports/BUG-001.md) | Login and access error messages are cut off in the error banner | Low |
| [BUG-002](./03-bug-reports/BUG-002.md) | "Remove" buttons stay after Reset App State empties the cart | Medium |
| [BUG-003](./03-bug-reports/BUG-003.md) | Lazy Load catalog shows the same products more than once | Medium |
| [BUG-004](./03-bug-reports/BUG-004.md) | Sort dropdown arrow does not open the menu, although the cursor shows it as clickable | Low |

## Skills 
**Shown in this portfolio**
- **Requirements analysis and traceability:** requirements → test cases → results → bugs
- **Test planning:** scope, risk-based priority (P1/P2/P3), smoke suite, entry, suspension, and exit criteria, and metrics
- **Test case design:** functional, negative, UI and readability, calculation, and cross-browser (Chrome and Safari)
- **Exploratory testing**, turning findings into requirements and test cases
- **Defect reporting:** severity vs. priority, steps to reproduce, evidence (screenshots and video), impact, and open questions for Product
- **API testing with Postman:** REST methods, status codes, JSON validation, token authentication, chained requests, negative tests, and the Collection Runner
- **Clear documentation** in Markdown on GitHub

**Professional experience (Meta and Google, via Wipro)**
- Functional, regression, exploratory, smoke, sanity, UAT, and accessibility testing
- Mobile and web: iOS and iPadOS (Xcode, iOS Simulator), Android (Android Studio), web, and Meta Quest (VR)
- Localization and internationalization: RTL, CJK, Indic, and pseudo-locales
- Release triage, regression bisection, and crash analysis
- Agile/Scrum · Jira · Bugzilla
- AI data quality: training data audits and annotation guidelines
- Team leadership: training 20+ testers and onboarding an offshore team

**In progress:** Playwright UI automation · SQL for QA

## Tools used in this project
Chrome · Safari · Postman · Google Sheets · GitHub · Markdown

## About me
QA engineer with **7+ years** testing consumer products used by millions, embedded with **Meta and Google teams through Wipro**.

- **Built QA from the ground up (Google, via Wipro):** created test plans and test cases from Figma designs and product specs for new iOS and iPadOS apps and features. Zero escalations from the QA team, and every release shipped successfully.
- **Led and scaled testing teams (Meta, via Wipro):** trained and coached 20+ testers, onboarded a 10-person offshore team in India, and kept the Commerce testing team at 95–100% weekly quality.
- **Designed "Safety Net":** a system that brought every testing queue and tool into one place, so no task got lost or missed the 24-hour SLA.
- **Release risk and triage:** bisected regressions, triaged issues that could block Continuous Push, and communicated launch risk to Engineering, Product, and leadership.
- **Global quality:** constant localization testing (RTL, CJK, Indic, and pseudo-locales) across Meta and Google products.
- **AI quality:** audited AI training data at Meta and helped refine annotation guidelines. Today I design AI-assisted workflows with a source-of-truth file and evidence rules that block the AI from inventing facts, and I QA the output like a product.

A.A.S. in Software Testing, Austin Community College · English (professional) and Spanish (native)

**Connect:** [LinkedIn](https://www.linkedin.com/in/softwaqasoftwaretesteranddataanalyst)
