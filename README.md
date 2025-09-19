# 🛒 Selenium Automated Purchase Simulation (Swag Labs Demo)

This project demonstrates the use of **Python + Selenium WebDriver** for end-to-end **test automation** of an e-commerce workflow.  
It simulates a customer logging in, adding multiple items to the cart, checking out, and recording transaction details in an **Excel file**.

---

## 📂 Project Files
- **test.py** → Main Selenium automation script.  
- **transactions_log.xlsx** → Excel log file that records all simulated transactions (created automatically on first run).  
- **chromedriver.exe** → Chrome WebDriver used by Selenium to automate the Chrome browser.  

---

## ⚡ Features
✔️ Logs in to [Swag Labs Demo](https://www.saucedemo.com/) with a test account.  
✔️ Adds multiple items (`backpack`, `bike light`, `t-shirt`) to the cart.  
✔️ Simulates a **real checkout** with random first name, last name, and zip code.  
✔️ Completes purchase and returns to products page.  
✔️ **Logs every transaction** (purchase #, name, zip, items, status) into `transactions_log.xlsx`.  
✔️ Runs multiple times in a loop (default: 20 runs).  

---

## 🛠️ Requirements
- Python **3.8+**
- Google Chrome (latest version)
- ChromeDriver (matching your Chrome version)
- Python dependencies:
  ```bash
  pip install selenium openpyxl

⚠️ Disclaimer

This project is for educational/demo purposes only.
It uses the Swag Labs demo site provided by Sauce Labs for practice in automation testing.
