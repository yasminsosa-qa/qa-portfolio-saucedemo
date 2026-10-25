# Test Plan — SauceDemo (Swag Labs) Web Store

| Field | Value |
|---|---|
| **Test Plan ID** | TP-SD-001 |
| **Version** | 1.1 |
| **Prepared by** | Yasmin Sosa, QA Engineer |
| **Date** | 2026-10-25 |
| **Application** | https://www.saucedemo.com (public practice e-commerce site by Sauce Labs) |
| **Related documents** | [Exploratory session notes](../00-exploratory-notes/Exploratory_Session_SauceDemo.md) · [Test cases and results](../02-test-cases/) · [Bug reports](../03-bug-reports/) |

## 1. Introduction
This test plan defines how the core shopping flow of SauceDemo is validated before release: login, product catalog, cart, checkout, and menu actions. SauceDemo has no published requirements, so the requirements in Section 4 were **derived from observed behavior** during the exploratory session on 2026-10-23 and from standard e-commerce expectations.

## 2. Scope

### In scope
| Feature | Coverage |
|---|---|
| Login | Valid login, required-field validation, invalid credentials, locked-out user |
| Product catalog | Product list, 4 sort options (including a same-price edge case), product details |
| Cart | Add and remove products, cart badge, button state, cart contents |
| Checkout | Required-field validation, order overview, 8% tax and total calculation, cancel (both steps), confirmation, PDF order |
| Menu | Logout, Reset App State, Dynamic Catalog (Lazy Load) |

### Out of scope
- Real payments and payment processing (practice site, no payment gateway)
- Performance and load testing with tools
- Security and penetration testing
- Mobile devices and screen sizes below tablet width
- API and backend testing (covered separately in [04-api-testing](../04-api-testing/))

## 3. Test objectives
1. Confirm that a customer can complete the full purchase flow (login → add to cart → checkout → confirmation) with **standard_user**.
2. Confirm that order totals are correct: item total + **8% tax** = total, verified manually.
3. Confirm that all required-field validations show a **clear and readable** error message.
4. Confirm that the cart badge, product buttons, and cart page always show the **same cart state**.
5. Achieve **100% requirement coverage** and execute **100%** of planned test cases in Chrome and Safari.

## 4. Requirements and traceability
| Req ID | Requirement (derived from observed behavior) | Test cases |
|---|---|---|
| REQ-01 | A registered user can log in with valid credentials | TC-01 |
| REQ-02 | Login validates empty fields and wrong credentials with a clear, readable error | TC-02, TC-03, TC-04 |
| REQ-03 | A locked-out user cannot access the store | TC-05 |
| REQ-04 | Products can be sorted by name (A–Z, Z–A) and price (low–high, high–low) | TC-06 to TC-09 |
| REQ-05 | The product details page shows product information and allows adding to cart | TC-10 |
| REQ-06 | The cart badge, buttons, and cart page reflect added and removed items | TC-11 to TC-13 |
| REQ-07 | Checkout requires First Name, Last Name, and Postal Code | TC-14 |
| REQ-08 | The order overview shows the correct item total, 8% tax, and total | TC-15 |
| REQ-09 | A customer can cancel or complete checkout; completing shows a confirmation and empties the cart | TC-16, TC-17, TC-18, TC-22 |
| REQ-10 | Menu actions work: Logout ends the session and Reset App State clears the cart and UI | TC-19, TC-20 |
| REQ-11 | The Lazy Load catalog shows each product variant once *(assumed expected behavior, pending Product confirmation)* | TC-21 |

**Requirement coverage:** 11 of 11 requirements mapped to test cases = **100%**
*(Test Coverage = requirements mapped to test cases ÷ total requirements × 100)*

## 5. Test approach

### Test types
| Type | How it is applied |
|---|---|
| Exploratory | Initial session to learn the app and find early defects (2026-10-23), and continued during execution (BUG-004 and TC-22 came from it) |
| Smoke | P1 test cases run first; if any fails, deeper testing pauses (see Section 9) |
| Functional | Each requirement validated with documented test cases |
| Negative | Empty fields, wrong password, locked-out user, access after logout |
| UI / readability | Error messages, labels, button states, and cursor feedback checked visually |
| Calculation | Tax and totals verified manually against the 8% rate |
| Cross-browser | All test cases executed in Chrome and Safari |

### Test case priority and type
- **P1 (Critical):** blocks purchase or access; part of the smoke suite.
- **P2 (High):** important function or validation; a workaround may exist.
- **P3 (Medium):** secondary function or cosmetic issue.

**Smoke suite (P1):** TC-01, TC-05, TC-11, TC-14, TC-15, TC-17, TC-19

### Test cases
| ID | Title | Priority | Type | Req |
|---|---|---|---|---|
| TC-01 | Log in with valid credentials | P1 | Smoke | REQ-01 |
| TC-02 | Log in with both fields empty | P2 | Negative | REQ-02 |
| TC-03 | Log in with valid username and empty password | P2 | Negative | REQ-02 |
| TC-04 | Log in with wrong password shows a readable error | P2 | Negative / UI | REQ-02 |
| TC-05 | Locked-out user cannot log in | P1 | Negative | REQ-03 |
| TC-06 | Sort products by Name (A to Z) | P2 | Functional | REQ-04 |
| TC-07 | Sort products by Name (Z to A) | P3 | Functional | REQ-04 |
| TC-08 | Sort products by Price (low to high), including same-price items | P2 | Functional | REQ-04 |
| TC-09 | Sort products by Price (high to low) | P3 | Functional | REQ-04 |
| TC-10 | Open product details and add to cart from the details page | P2 | Functional | REQ-05 |
| TC-11 | Add a product updates the cart badge and button | P1 | Smoke | REQ-06 |
| TC-12 | Remove a product from the catalog and from the cart page | P2 | Functional | REQ-06 |
| TC-13 | Cart contents are kept when navigating between pages | P2 | Functional | REQ-06 |
| TC-14 | Checkout shows an error for each missing required field | P1 | Negative | REQ-07 |
| TC-15 | Order overview shows the correct item total, 8% tax, and total | P1 | Smoke | REQ-08 |
| TC-16 | Cancel on the overview keeps items in the cart | P2 | Functional | REQ-09 |
| TC-22 | Cancel on Checkout: Your Information returns to the cart and keeps items *(added during execution)* | P3 | Functional | REQ-09 |
| TC-17 | Complete an order shows a confirmation and empties the cart | P1 | Smoke | REQ-09 |
| TC-18 | Generate PDF order downloads the order details | P3 | Functional | REQ-09 |
| TC-19 | Logout ends the session and blocks access to the products page | P1 | Smoke | REQ-10 |
| TC-20 | Reset App State clears the cart and resets product buttons | P2 | Functional | REQ-10 |
| TC-21 | Lazy Load catalog shows each product variant once | P3 | Functional | REQ-11 |

Detailed steps, test data, and results: [02-test-cases](../02-test-cases/)

## 6. Test schedule
| Phase | Start | End | Status |
|---|---|---|---|
| Exploratory testing | 2026-10-23 | 2026-10-23 | ✅ Done |
| Test planning | 2026-10-25 | 2026-10-25 | ✅ Done |
| Test case design | 2026-10-25 | 2026-10-25 | ✅ Done |
| Test execution (Chrome and Safari) | 2026-10-25 | 2026-10-25 | ✅ Done |
| Defect reporting and verification | 2026-10-23 | 2026-10-25 | ✅ Done |
| API testing (Postman) | 2026-10-25 | 2026-10-26 | In progress |

## 7. Test environment and test data
| Item | Value |
|---|---|
| OS | macOS 27.0.1 (26A434) |
| Browsers | Chrome 156.0.8078.48, Safari 27.0.1 |
| Application URL | https://www.saucedemo.com |
| Test users | standard_user (main), locked_out_user, problem_user, error_user |
| Password | secret_sauce (provided by the application for testing) |
| Checkout test data | First Name: Test · Last Name: User · Postal Code: 78701 |
| Tools | Chrome and Safari, Google Sheets (test cases), GitHub (documentation), Postman (API testing) |

No real personal or payment data is used.

## 8. Resources and responsibilities
| Role | Name | Responsibilities |
|---|---|---|
| QA Engineer | Yasmin Sosa | Test planning, test case design, execution, defect reporting, and summary report |
| Product / Development | N/A (practice application) | Open questions are documented in the bug reports as "Questions for Product" |

## 9. Entry, suspension, and exit criteria

### Entry criteria
- The application is available and the test users can log in.
- The test plan and test cases are written.

### Suspension criteria
- The site is unavailable, or **standard_user** cannot log in (TC-01 fails).
- Any smoke test (P1) fails in a way that blocks the purchase flow.

### Exit criteria (release recommendation)
| Criterion | Result |
|---|---|
| 100% of planned test cases executed in Chrome and Safari | ✅ 22/22 in each browser |
| 100% of P1 test cases pass with standard_user | ✅ 7/7 in Chrome and Safari |
| No open High-severity defects | ✅ 0 High (2 Medium, 2 Low) |
| Every failed test case is linked to a documented defect | ✅ TC-04, TC-20, TC-21 |

**Recommendation:** the core purchase flow is ready for release. The 4 open defects (2 Medium, 2 Low) should be fixed in a follow-up release; none blocks a purchase.

## 10. Defect management
- Each defect is logged in [03-bug-reports](../03-bug-reports/) with: title, severity, priority, environment, steps, expected vs. actual result, frequency, impact, and evidence.
- **Severity:** High (blocks purchase, data, or access) · Medium (wrong behavior with a workaround) · Low (cosmetic, readability, or usability).
- Each defect references its test case, and each failed test case references its defect.
- When expected behavior is unclear, the defect is marked "Needs confirmation from Product" instead of assuming.
- A defect with the same root cause found in another test case is logged as an additional occurrence, not as a duplicate defect.

## 11. Risks and mitigation
| Risk | Impact | Mitigation |
|---|---|---|
| Wrong order total or tax | High: customers are charged the wrong amount | Manual tax and total verification in TC-15 |
| Cart state does not match the real cart | High: customers order the wrong items | TC-11 to TC-13 and TC-20 check badge, buttons, and cart page together |
| Unreadable error messages | Medium: customers do not understand why an action failed | TC-04, TC-14, and TC-19 include a visual readability check in two browsers |
| Locked-out user or logged-out user can access the store | High: access control failure | TC-05 and TC-19 |
| Test users with intentional defects | Medium: results differ by user | Cases run with standard_user |
| No official requirements | Medium: expected behavior may be unclear | Requirements derived from exploration; unclear cases flagged for Product |

## 12. Metrics
| Metric | Formula | Chrome | Safari |
|---|---|---|---|
| Requirement coverage | requirements mapped ÷ total requirements × 100 | 11/11 = 100% | 11/11 = 100% |
| Execution progress | test cases executed ÷ planned × 100 | 22/22 = 100% | 22/22 = 100% |
| Pass rate | test cases passed ÷ executed × 100 | 19/22 = 86% | 19/22 = 86% |
| P1 pass rate | P1 passed ÷ P1 executed × 100 | 7/7 = 100% | 7/7 = 100% |
| Defects by severity | count per severity | High 0 · Medium 2 · Low 2 | |

## 13. Deliverables
| Deliverable | Location |
|---|---|
| Exploratory session notes | [00-exploratory-notes](../00-exploratory-notes/) |
| Test plan (this document) | [01-test-plan](../01-test-plan/) |
| Test cases with execution results and summary | [02-test-cases](../02-test-cases/) |
| Bug reports with evidence | [03-bug-reports](../03-bug-reports/) |
| API test collection (Postman) | [04-api-testing](../04-api-testing/) |

## 14. Defects found
| ID | Title | Severity | Status | Test case |
|---|---|---|---|---|
| [BUG-001](../03-bug-reports/BUG-001.md) | Login and access error messages are cut off in the error banner | Low | Open | TC-04, TC-19 (2nd occurrence) |
| [BUG-002](../03-bug-reports/BUG-002.md) | "Remove" buttons stay after Reset App State | Medium | Open | TC-20 |
| [BUG-003](../03-bug-reports/BUG-003.md) | Lazy Load catalog repeats the same products | Medium | Open, needs Product confirmation | TC-21 |
| [BUG-004](../03-bug-reports/BUG-004.md) | Sort dropdown arrow does not open the menu, although the cursor shows it as clickable | Low | Open | Found during TC-06 |

## 15. Version history
| Version | Date | Author | Changes |
|---|---|---|---|
| 1.0 | 2026-10-25 | Yasmin Sosa | Initial test plan |
| 1.1 | 2026-10-25 | Yasmin Sosa | Added TC-22 (found during execution), BUG-004, second occurrence of BUG-001, cross-browser execution of all test cases, and final results and metrics |
