# Exploratory Session — SauceDemo
**Tester:** Yasmin Sosa · **Date:** 2026-10-23
**Browsers:** Chrome 156.0.8078.48, Safari 27.0 · **OS:** macOS 27.0.1 (26A434)
**Goal:** Learn the application's main features before writing the test plan.

## 1. Login
- Fields: Username, Password, and a Login button. The page lists 6 accepted users and one shared password.
- Both fields empty → "Epic sadface: Username is required" (both fields are highlighted in red with an × icon)
- Username without password → "Epic sadface: Password is required"
- Wrong password → "Epic sadface: Username and password do not match any user in this service"
  - ⚠ The message is cut off inside the error banner → [BUG-001](../03-bug-reports/BUG-001.md)
- locked_out_user → "Epic sadface: Sorry, this user has been locked out."
- standard_user / secret_sauce → user lands on the Products page

## 2. Product catalog
- The Products page shows 6 products: Sauce Labs Backpack ($29.99), Sauce Labs Bike Light ($9.99), Sauce Labs Bolt T-Shirt ($15.99), Sauce Labs Fleece Jacket ($49.99), Sauce Labs Onesie ($7.99), and Test.allTheThings() T-Shirt (Red) ($15.99).
- Each product shows an image, name, description, price, and an "Add to cart" button.
- Sort options: (to be completed)

## 3. Product details
- Content observation: some product text uses code-style wording ("carry.allTheThings()" on the Backpack and the product name "Test.allTheThings() T-Shirt (Red)"). Likely intentional brand voice, not a defect. Question for Product: could this confuse non-technical customers?

## 4. Cart
- Adding a product changes its button to "Remove" and updates the cart badge count.
- Removing a product updates the badge correctly.

## 5. Checkout
(to be completed)

## 6. Menu (☰)
- Options: All Items, Dynamic Catalog, About, Logout, Reset App State.
- Reset App State → empties the cart and removes the badge, but product buttons keep showing "Remove" → [BUG-002](../03-bug-reports/BUG-002.md)
- Dynamic Catalog → Lazy Load repeats the same products in the same order → [BUG-003](../03-bug-reports/BUG-003.md)
  - Lazy Load cards are not clickable and have no "Add to cart" button (question for Product, see BUG-003).
