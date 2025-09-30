# 🧪 TEST_PLAN.md  
Selenium Automated Purchase Simulation – Swag Labs Demo

---

## 1. Objective
Verify that the Selenium automation script performs a full e-commerce purchase flow on [Swag Labs Demo](https://www.saucedemo.com/) and logs each transaction correctly into an Excel file.

---

## 2. Scope
Covered:
- Browser automation using Chrome + Selenium.
- Login with valid credentials.
- Adding predefined items to cart.
- Checkout with random user data.
- Transaction logging to `transactions_log.xlsx`.
- Looping multiple purchase runs.

Not Covered:
- Negative testing of invalid credentials.
- UI visual validation.
- Performance/stress testing of the Swag Labs site.

---

## 3. Test Environment
| Component         | Details                                    |
|-------------------|---------------------------------------------|
| OS                | Windows 10 or later                         |
| Browser           | Google Chrome (latest stable)               |
| WebDriver         | ChromeDriver matching Chrome version         |
| Python            | 3.8 or later                                |
| Dependencies      | `selenium`, `openpyxl`                      |
| Test Data Source  | Hard-coded in script (items, names, zip)     |
| Network           | Stable internet connection                   |

---

## 4. Test Data
- **Credentials**:  
  - Username: `standard_user`  
  - Password: `secret_sauce`
- **Items to Add**:  
  - `add-to-cart-sauce-labs-backpack`  
  - `add-to-cart-sauce-labs-bike-light`  
  - `add-to-cart-sauce-labs-bolt-t-shirt`
- **Random Pools**: First names, last names, and 5-digit zip codes are generated from script lists.

---

## 5. Test Scenarios

| ID | Scenario | Steps | Expected Result |
|----|---------|------|------------------|
| TC01 | Login | Launch Chrome → Navigate to site → Enter credentials → Submit | User is redirected to Products page without error |
| TC02 | Add Items to Cart | For each item ID, click “Add to Cart” | Each item button changes to “Remove” and cart badge increments |
| TC03 | Checkout Flow | Open cart → Click Checkout → Enter random details → Continue → Finish | Checkout completes and confirmation page displays |
| TC04 | Excel Logging | After each run, open `transactions_log.xlsx` | A new row is appended with purchase #, random names, zip, item list, and `SUCCESS` |
| TC05 | Loop Execution | Set `num_runs=20` and run script | Script completes 20 successful purchase cycles and closes browser |
| TC06 | Missing Excel File | Delete `transactions_log.xlsx` before run | Script creates new file with header row and first transaction logged |
| TC07 | Element Failure Handling | Temporarily change an item ID to an invalid value | Script prints warning and continues next item without crash |

---

## 6. Test Data Validation
- Verify each Excel row contains:
  - Sequential purchase number starting at 1.
  - Non-empty first and last name.
  - 5-digit zip code.
  - Comma-separated list of all 3 item IDs.
  - Status column = `SUCCESS` unless forced error.

---

## 7. Entry and Exit Criteria
**Entry**  
- ChromeDriver installed and path configured.  
- Python dependencies installed.  
- Internet access to https://www.saucedemo.com.

**Exit**  
- All test scenarios executed.  
- No unhandled exceptions in console.  
- Excel log reflects all executed runs.

---

## 8. Risks & Mitigations
| Risk | Mitigation |
|------|------------|
| Swag Labs site downtime | Re-run when site is available |
| ChromeDriver version mismatch | Confirm driver version matches Chrome |
| Network instability | Ensure stable internet before execution |

---

## 9. Reporting
- Console output: real-time progress, warnings for missing elements.
- Excel file: persistent record of each transaction.
- Defects: capture console stack traces and Excel row anomalies.

---

## 10. Maintenance
- Update ChromeDriver when Chrome updates.
- Adjust selectors if Swag Labs UI changes.
- Parameterize item list or run count if test coverage changes.
