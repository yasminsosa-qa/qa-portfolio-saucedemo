# Exploratory Session — SauceDemo
**Tester:** Yasmin Sosa · **Date:** 2026-10-23
**Browsers:** Chrome 156.0.8078.48, Safari 27.0 · **OS:** macOS 27.0.1 (26A434)
**Goal:** Learn the application's main features before writing the test plan.

## 1. Login
- Fields: Username, Password, and a Login button. The page lists 6 accepted users and one shared password.
- Both fields empty → "Epic sadface: Username is required" (both fields are highlighted in red with an × icon)
- Username without password → "Epic sadface: Password is required"
- Wrong password → "Epic sadface: Username and password do not match any user in this service"
  - ⚠ The message is cut off inside the error banner → logged as [BUG-001](../03-bug-reports/BUG-001.md)
- locked_out_user → "Epic sadface: Sorry, this user has been locked out."
- standard_user / secret_sauce → user lands on the Products page

## 2. Product catalog
(to be completed)

## 3. Product details
- Product descriptions use code-style text (e.g., "carry.allTheThings()" on the Backpack).
  Likely intentional brand voice, not a defect. Question for Product: could this confuse non-technical customers?

## 4. Cart
(to be completed)

## 5. Checkout
(to be completed)

## 6. Menu
(to be completed)
