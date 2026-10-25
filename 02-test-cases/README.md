Test Cases & Execution Results — SauceDemo
Test Plan: TP-SD-001
Executed by: Yasmin Sosa · Date: 2026-10-25
Environment: Chrome 156.0.8078.48 and Safari 27.0.1 on macOS 27.0.1 (26A434) · User: standard_user
Download: Test_Cases_SauceDemo.xlsx (full workbook with steps, data, and summary)
Execution summary
Metric	Chrome	Safari
Test cases executed	22 / 22 (100%)	22 / 22 (100%)
Passed	19	19
Failed	3	3
Blocked	0	0
Pass rate	86%	86%
P1 (smoke) passed	7 / 7	7 / 7
Requirement coverage	11 / 11 (100%)	11 / 11 (100%)

Exit criteria (Test Plan, Section 9): ✅ all test cases executed · ✅ 100% of P1 test cases pass in both browsers · ✅ no open High-severity defects · ✅ every failed test case is linked to a documented defect.

Defects: 4 logged — 3 from failed test cases (BUG-001, BUG-002, BUG-003) and 1 found during execution of TC-06 (BUG-004). BUG-001 has a second occurrence found in TC-19.

Results
ID	Section	Title	Priority	Type	Req	Chrome	Safari	Bug
TC-01	Login	Log in with valid credentials	P1	Smoke	REQ-01	✅ Pass	✅ Pass	
TC-02	Login	Log in with both fields empty	P2	Negative	REQ-02	✅ Pass	✅ Pass	
TC-03	Login	Log in with valid username and empty password	P2	Negative	REQ-02	✅ Pass	✅ Pass	
TC-04	Login	Log in with wrong password shows a readable error	P2	Negative / UI	REQ-02	❌ Fail	❌ Fail	BUG-001
TC-05	Login	Locked-out user cannot log in	P1	Negative	REQ-03	✅ Pass	✅ Pass	
TC-06	Catalog	Sort products by Name (A to Z)	P2	Functional	REQ-04	✅ Pass	✅ Pass	BUG-004 (found during execution)
TC-07	Catalog	Sort products by Name (Z to A)	P3	Functional	REQ-04	✅ Pass	✅ Pass	
TC-08	Catalog	Sort products by Price (low to high), including same-price items	P2	Functional	REQ-04	✅ Pass	✅ Pass	
TC-09	Catalog	Sort products by Price (high to low)	P3	Functional	REQ-04	✅ Pass	✅ Pass	
TC-10	Product details	Open product details and add to cart from the details page	P2	Functional	REQ-05	✅ Pass	✅ Pass	
TC-11	Cart	Add a product updates the cart badge and button	P1	Smoke	REQ-06	✅ Pass	✅ Pass	
TC-12	Cart	Remove a product from the catalog and from the cart page	P2	Functional	REQ-06	✅ Pass	✅ Pass	
TC-13	Cart	Cart contents are kept when navigating between pages	P2	Functional	REQ-06	✅ Pass	✅ Pass	
TC-14	Checkout	Checkout shows an error for each missing required field	P1	Negative	REQ-07	✅ Pass	✅ Pass	
TC-15	Checkout	Order overview shows the correct item total, 8% tax, and total	P1	Smoke	REQ-08	✅ Pass	✅ Pass	
TC-16	Checkout	Cancel on the overview keeps items in the cart	P2	Functional	REQ-09	✅ Pass	✅ Pass	
TC-22	Checkout	Cancel on Checkout: Your Information returns to the cart and keeps items	P3	Functional	REQ-09	✅ Pass	✅ Pass	
TC-17	Checkout	Complete an order shows a confirmation and empties the cart	P1	Smoke	REQ-09	✅ Pass	✅ Pass	
TC-18	Checkout	Generate PDF order downloads the order details	P3	Functional	REQ-09	✅ Pass	✅ Pass	
TC-19	Menu	Logout ends the session and blocks access to the products page	P1	Smoke	REQ-10	✅ Pass	✅ Pass	BUG-001 (2nd occurrence)
TC-20	Menu	Reset App State clears the cart and resets product buttons	P2	Functional	REQ-10	❌ Fail	❌ Fail	BUG-002
TC-21	Menu	Lazy Load catalog shows each product variant once	P3	Functional	REQ-11	❌ Fail	❌ Fail	BUG-003

TC-22 was added during execution to cover the Cancel button on step 1 of checkout. Test case IDs stay stable; cases are grouped by section.

Test case details

Click a test case to see its preconditions, data, steps, expected result, and actual result.

<details> <summary><b>TC-01</b> — Log in with valid credentials (P1 · ✅ Pass)</summary>
Section / Type / Requirement: Login · Smoke · REQ-01
Preconditions: On the login page, logged out
Test data: standard_user / secret_sauce
Steps:
Go to https://www.saucedemo.com
Enter the username
Enter the password
Click Login
Expected result: Products page opens (URL ends in /inventory.html), the header shows "Products", and 6 products are listed.
Actual result: Products page opens (URL: /inventory.html). Header shows "Products" and 6 products are listed.
Status: Chrome Pass · Safari Pass
</details> <details> <summary><b>TC-02</b> — Log in with both fields empty (P2 · ✅ Pass)</summary>
Section / Type / Requirement: Login · Negative · REQ-02
Preconditions: On the login page, logged out
Test data: Username: (empty) / Password: (empty)
Steps:
Leave both fields empty
Click Login
Expected result: Error banner shows "Epic sadface: Username is required". Both fields are highlighted in red with an × icon. User stays on the login page.
Actual result: Error "Epic sadface: Username is required" is displayed. Both fields are highlighted in red. User stays on the login page.
Status: Chrome Pass · Safari Pass
</details> <details> <summary><b>TC-03</b> — Log in with valid username and empty password (P2 · ✅ Pass)</summary>
Section / Type / Requirement: Login · Negative · REQ-02
Preconditions: On the login page, logged out
Test data: standard_user / (empty)
Steps:
Enter the username
Leave the password empty
Click Login
Expected result: Error banner shows "Epic sadface: Password is required". User stays on the login page.
Actual result: Error "Epic sadface: Password is required" is displayed. User stays on the login page.
Status: Chrome Pass · Safari Pass
</details> <details> <summary><b>TC-04</b> — Log in with wrong password shows a readable error (P2 · ❌ Fail)</summary>
Section / Type / Requirement: Login · Negative / UI · REQ-02
Preconditions: On the login page, logged out
Test data: standard_user / abc123
Steps:
Enter the username
Enter the wrong password
Click Login
Read the full error message
Expected result: The full message "Epic sadface: Username and password do not match any user in this service" is displayed and fully readable inside the error banner. User stays on the login page.
Actual result: Error text "Epic sadface: Username and password do not match any user in this service" is cut off at the top and bottom of the banner and is not fully readable.
Status: Chrome Fail · Safari Fail
Defect: BUG-001
Notes: Shorter error messages display correctly. See BUG-001.
</details> <details> <summary><b>TC-05</b> — Locked-out user cannot log in (P1 · ✅ Pass)</summary>
Section / Type / Requirement: Login · Negative · REQ-03
Preconditions: On the login page, logged out
Test data: locked_out_user / secret_sauce
Steps:
Enter the username
Enter the password
Click Login
Expected result: Error banner shows "Epic sadface: Sorry, this user has been locked out." The Products page is not accessible.
Actual result: Error "Epic sadface: Sorry, this user has been locked out." is displayed. Access to the Products page is blocked.
Status: Chrome Pass · Safari Pass
</details> <details> <summary><b>TC-06</b> — Sort products by Name (A to Z) (P2 · ✅ Pass)</summary>
Section / Type / Requirement: Catalog · Functional · REQ-04
Preconditions: Logged in as standard_user on the Products page, cart empty
Test data: Sort option: Name (A to Z)
Steps:
Check the default sort option
Select "Name (A to Z)"
Read the product order
Expected result: "Name (A to Z)" is the default. Order: Sauce Labs Backpack, Sauce Labs Bike Light, Sauce Labs Bolt T-Shirt, Sauce Labs Fleece Jacket, Sauce Labs Onesie, Test.allTheThings() T-Shirt (Red).
Actual result: "Name (A to Z)" is selected by default. Products are listed from Sauce Labs Backpack to Test.allTheThings() T-Shirt (Red) in alphabetical order.
Status: Chrome Pass · Safari Pass
Notes: Found during execution: clicking the dropdown arrow (▼) does not open the sort menu, although the cursor changes to a pointer. Clicking the text opens it. See BUG-004
</details> <details> <summary><b>TC-07</b> — Sort products by Name (Z to A) (P3 · ✅ Pass)</summary>
Section / Type / Requirement: Catalog · Functional · REQ-04
Preconditions: Logged in as standard_user on the Products page, cart empty
Test data: Sort option: Name (Z to A)
Steps:
Select "Name (Z to A)"
Read the product order
Expected result: Order: Test.allTheThings() T-Shirt (Red), Sauce Labs Onesie, Sauce Labs Fleece Jacket, Sauce Labs Bolt T-Shirt, Sauce Labs Bike Light, Sauce Labs Backpack.
Actual result: Products are listed from Test.allTheThings() T-Shirt (Red) to Sauce Labs Backpack in reverse alphabetical order.
Status: Chrome Pass · Safari Pass
</details> <details> <summary><b>TC-08</b> — Sort products by Price (low to high), including same-price items (P2 · ✅ Pass)</summary>
Section / Type / Requirement: Catalog · Functional · REQ-04
Preconditions: Logged in as standard_user on the Products page, cart empty
Test data: Sort option: Price (low to high)
Steps:
Select "Price (low to high)"
Read the prices in order
Expected result: Prices in ascending order: $7.99, $9.99, $15.99, $15.99, $29.99, $49.99. Both $15.99 products appear between $9.99 and $29.99.
Actual result: Prices display in ascending order: $7.99, $9.99, $15.99, $15.99, $29.99, $49.99. The two $15.99 items (Sauce Labs Bolt T-Shirt and Test.allTheThings() T-Shirt (Red)) appear together in the correct position.
Status: Chrome Pass · Safari Pass
Notes: Same-price items ($15.99): Sauce Labs Bolt T-Shirt appears before Test.allTheThings() T-Shirt (Red). Ties are ordered alphabetically by name. Not a defect.
</details> <details> <summary><b>TC-09</b> — Sort products by Price (high to low) (P3 · ✅ Pass)</summary>
Section / Type / Requirement: Catalog · Functional · REQ-04
Preconditions: Logged in as standard_user on the Products page, cart empty
Test data: Sort option: Price (high to low)
Steps:
Select "Price (high to low)"
Read the prices in order
Expected result: Prices in descending order: $49.99, $29.99, $15.99, $15.99, $9.99, $7.99.
Actual result: Prices display in descending order: $49.99, $29.99, $15.99, $15.99, $9.99, $7.99.
Status: Chrome Pass · Safari Pass
Notes: Same-price items keep the same order as in TC-08 (Bolt T-Shirt first), which confirms a secondary sort by name (A–Z). Not a defect.
</details> <details> <summary><b>TC-10</b> — Open product details and add to cart from the details page (P2 · ✅ Pass)</summary>
Section / Type / Requirement: Product details · Functional · REQ-05
Preconditions: Logged in as standard_user on the Products page, cart empty
Test data: Product: Sauce Labs Backpack
Steps:
Click the product name "Sauce Labs Backpack"
Review the details page
Click Add to cart
Click Back to products
Expected result: Details page shows the name, description, price $29.99, and image. After Add to cart, the button changes to "Remove" and the cart badge shows 1. Back on Products, the Backpack button shows "Remove".
Actual result: Details page shows name, description, $29.99, and image. After Add to cart, the button shows "Remove" and the badge shows 1, also on the Products page.
Status: Chrome Pass · Safari Pass
</details> <details> <summary><b>TC-11</b> — Add a product updates the cart badge and button (P1 · ✅ Pass)</summary>
Section / Type / Requirement: Cart · Smoke · REQ-06
Preconditions: Logged in as standard_user on the Products page, cart empty
Test data: Products: Sauce Labs Bike Light, Sauce Labs Backpack
Steps:
Click Add to cart on Sauce Labs Bike Light
Click Add to cart on Sauce Labs Backpack
Expected result: After step 1: the Bike Light button shows "Remove" and the cart badge shows 1. After step 2: the Backpack button shows "Remove" and the badge shows 2.
Actual result: Badge shows 1 after adding Bike Light and 2 after adding Backpack. Both buttons change to "Remove".
Status: Chrome Pass · Safari Pass
</details> <details> <summary><b>TC-12</b> — Remove a product from the catalog and from the cart page (P2 · ✅ Pass)</summary>
Section / Type / Requirement: Cart · Functional · REQ-06
Preconditions: Logged in as standard_user; Backpack and Bike Light in the cart (badge 2)
Test data: Products: Sauce Labs Bike Light, Sauce Labs Backpack
Steps:
On Products, click Remove on Sauce Labs Bike Light
Open the cart
Click Remove on Sauce Labs Backpack
Expected result: After step 1: the button returns to "Add to cart" and the badge shows 1. After step 3: the cart page is empty and the badge disappears.
Actual result: Badge drops to 1 after removing Bike Light. After removing Backpack from the cart page, the cart is empty and the badge disappears.
Status: Chrome Pass · Safari Pass
</details> <details> <summary><b>TC-13</b> — Cart contents are kept when navigating between pages (P2 · ✅ Pass)</summary>
Section / Type / Requirement: Cart · Functional · REQ-06
Preconditions: Logged in as standard_user; Backpack and Bike Light in the cart (badge 2)
Test data: Products: Sauce Labs Backpack, Sauce Labs Bike Light
Steps:
Open the cart
Click Continue Shopping
Open a product details page and click Back to products
Refresh the page (Cmd + R)
Open the cart
Expected result: The badge shows 2 after every step, and the cart still lists both products after the refresh.
Actual result: Badge stays at 2 across the cart, product details, Products page, and after refresh. Cart lists both products.
Status: Chrome Pass · Safari Pass
</details> <details> <summary><b>TC-14</b> — Checkout shows an error for each missing required field (P1 · ✅ Pass)</summary>
Section / Type / Requirement: Checkout · Negative · REQ-07
Preconditions: Logged in as standard_user; 1 product in the cart; on Checkout: Your Information
Test data: First Name: Test · Last Name: User · Postal Code: 78701
Steps:
Click Continue with all fields empty
Enter First Name and click Continue
Enter Last Name and click Continue
Enter Postal Code and click Continue
Expected result: Step 1: "Error: First Name is required". Step 2: "Error: Last Name is required". Step 3: "Error: Postal Code is required". Step 4: the Checkout: Overview page opens.
Actual result: Errors display in order: "First Name is required", "Last Name is required", "Postal Code is required". Overview opens once all fields are filled.
Status: Chrome Pass · Safari Pass
</details> <details> <summary><b>TC-15</b> — Order overview shows the correct item total, 8% tax, and total (P1 · ✅ Pass)</summary>
Section / Type / Requirement: Checkout · Smoke · REQ-08
Preconditions: Logged in as standard_user; Backpack and Fleece Jacket in the cart
Test data: First Name: Test · Last Name: User · Postal Code: 78701
Steps:
Open the cart and click Checkout
Enter the test data and click Continue
Read Item total, Tax, and Total
Calculate the tax manually (item total × 0.08)
Expected result: Item total: $79.98 · Tax: $6.40 · Total: $86.38. Manual check: $79.98 × 0.08 = $6.398, rounded to $6.40; $79.98 + $6.40 = $86.38.
Actual result: Item total $79.98, Tax $6.40, Total $86.38. Manual check matches: $79.98 × 8% = $6.40.
Status: Chrome Pass · Safari Pass
</details> <details> <summary><b>TC-16</b> — Cancel on the overview keeps items in the cart (P2 · ✅ Pass)</summary>
Section / Type / Requirement: Checkout · Functional · REQ-09
Preconditions: On Checkout: Overview with Backpack and Fleece Jacket
Test data: —
Steps:
Open the cart and click Checkout
Enter First Name, Last Name, and Postal Code, then click Continue
On the Checkout: Overview page, click Cancel
Check the cart badge
Open the cart
Expected result: After Cancel on the Overview page, the Products page opens. The badge still shows 2, and the cart lists both products.
Actual result: Cancel returns to the Products page. Badge still shows 2 and the cart lists both products.
Status: Chrome Pass · Safari Pass
</details> <details> <summary><b>TC-22</b> — Cancel on Checkout: Your Information returns to the cart and keeps items (P3 · ✅ Pass)</summary>
Section / Type / Requirement: Checkout · Functional · REQ-09
Preconditions: Logged in as standard_user; Backpack and Bike Light in the cart (badge 2)
Test data: — (no data entered)
Steps:
Open the cart and click Checkout
Leave First Name, Last Name, and Postal Code empty
Click Cancel
Check the cart badge and the cart contents
Expected result: The Your Cart page opens. The badge still shows 2, and the cart lists both products. No validation errors appear.
Actual result: Cancel on Checkout: Your Information returns to the Your Cart page with both products listed. Badge still shows 2. No validation errors appear.
Status: Chrome Pass · Safari Pass
Notes: Added during execution to cover the Cancel button on step 1 of checkout. TC-16 covers Cancel on step 2 (Overview).
</details> <details> <summary><b>TC-17</b> — Complete an order shows a confirmation and empties the cart (P1 · ✅ Pass)</summary>
Section / Type / Requirement: Checkout · Smoke · REQ-09
Preconditions: On Checkout: Overview with Backpack and Fleece Jacket
Test data: —
Steps:
Click Finish
Read the confirmation page
Check the cart badge
Click Back Home
Expected result: Confirmation shows "Thank you for your order!" and "Your order has been dispatched, and will arrive just as fast as the pony can get there!". The badge is cleared. Back Home opens Products with all buttons showing "Add to cart".
Actual result: Confirmation shows "Thank you for your order!" and the dispatch message. Badge is cleared. Back Home opens Products with all buttons showing "Add to cart".
Status: Chrome Pass · Safari Pass
</details> <details> <summary><b>TC-18</b> — Generate PDF order downloads the order details (P3 · ✅ Pass)</summary>
Section / Type / Requirement: Checkout · Functional · REQ-09
Preconditions: On the order confirmation page
Test data: —
Steps:
Click Generate PDF order
Open the downloaded PDF
Expected result: A PDF downloads and shows the order details. The items and amounts match the order overview.
Actual result: PDF downloads. Items and amounts in the PDF match the order overview.
Status: Chrome Pass · Safari Pass
</details> <details> <summary><b>TC-19</b> — Logout ends the session and blocks access to the products page (P1 · ✅ Pass)</summary>
Section / Type / Requirement: Menu · Smoke · REQ-10
Preconditions: Logged in as standard_user on the Products page, cart empty
Test data: URL: https://www.saucedemo.com/inventory.html
Steps:
Open the menu (☰) and click Logout
Click the browser Back button
Enter the inventory URL directly in the address bar
Expected result: Step 1: the login page opens. Steps 2 and 3: the Products page is not shown; the user stays on (or is sent back to) the login page with an error message.
Actual result: Logout opens the login page. Back button and direct URL both stay on the login page with the error "Epic sadface: You can only access '/inventory.html' when you are logged in". Products are not shown.
Status: Chrome Pass · Safari Pass
Notes: Access is correctly blocked. The error text is cut off in the banner (same root cause as BUG-001); added as a second occurrence in BUG-001.
</details> <details> <summary><b>TC-20</b> — Reset App State clears the cart and resets product buttons (P2 · ❌ Fail)</summary>
Section / Type / Requirement: Menu · Functional · REQ-10
Preconditions: Logged in as standard_user; Backpack and Bike Light in the cart (badge 2)
Test data: —
Steps:
Open the menu (☰) and click Reset App State
Check the cart badge
Check the product buttons
Open the cart
Expected result: The badge disappears, the cart is empty, and the Backpack and Bike Light buttons change back to "Add to cart" without a page refresh.
Actual result: Badge disappears and the cart is empty, but the Backpack and Bike Light buttons still show "Remove" until the page is refreshed.
Status: Chrome Fail · Safari Fail
Defect: BUG-002
Notes: Buttons update only after a page refresh. See BUG-002.
</details> <details> <summary><b>TC-21</b> — Lazy Load catalog shows each product variant once (P3 · ❌ Fail)</summary>
Section / Type / Requirement: Menu · Functional · REQ-11
Preconditions: Logged in as standard_user
Test data: —
Steps:
Open the menu (☰) → Dynamic Catalog → Lazy Load
Scroll down slowly until more products load
Compare product names and sizes
Expected result: Each product variant (name and size) appears only once. (Expected behavior assumed; pending Product confirmation.)
Actual result: The list repeats the same sequence of products in the same order (Bike Light, Bolt T-Shirt (XS), Onesie…) after more items load.
Status: Chrome Fail · Safari Fail
Defect: BUG-003
Notes: Expected behavior assumed (no official requirement); pending Product confirmation. See BUG-003.
</details>
