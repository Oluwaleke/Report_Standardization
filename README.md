# Monthly Expense Report Standardization

A reproducible Python pipeline that ingests a raw, messy CSV of company expenses and outputs a clean, standardized expense report ready for analysis or accounting systems.

---

## 📁 Project Structure

data-entry-monthly-expense/

├── data/
  └── raw_expense_report.csv

├── output/
   └── cleaned_expense_report.csv

├── expense_standardization.ipynb

  └── README.md 


---

## 🛠️ Requirements

- Python 3.7+  
- pandas  
- numpy  
- pdfplumber (not used here, but part of ETL toolbelt)  
- openpyxl (if you export to Excel)  

Install via:

```
pip install pandas numpy openpyxl
```

🚀 Usage
Generate or replace the raw CSV:

If you’re following the tutorial, run "Generate dummy raw CSV and inspect" in expense_standardization.ipynb to generate data/raw_expense_report.csv.

Otherwise, drop your own raw_expense_report.csv into the data/ folder.

Run the cleanup:

In Jupyter: open and run all cells in expense_standardization.ipynb.

Or, from the command line (if you created extract_clean_expenses.py):

python extract_clean_expenses.py


Inspect the output:

  The cleaned file appears at output/cleaned_expense_report.csv.

It contains:

  -Date as YYYY-MM-DD datetime

  -Vendor names normalized (e.g. “ABC Company”)

  -Category filled with “Uncategorized” where missing

  -Amount as a float (no $ or commas)

  -Payment type preserved

  -Duplicate flag for identical Date+Vendor+Amount rows

Use in analysis: load cleaned_expense_report.csv into your BI tool or accounting system.


🔍 Cleaning Steps

Date parsing – convert MM/DD/YYYY strings to true datetimes.

Amount conversion – strip currency formatting and cast to float.

Vendor normalization – map common variants (using regex) to canonical names.

Category fill‐down – replace missing categories with “Uncategorized.”

Duplicate flagging – identify repeated entries for QA.

Save – export the final table as CSV.



🎯 Why This Matters

Ensures consistency across financial records.

Automates repetitive cleanup tasks in seconds.

Flags potential errors (duplicates) before they reach accounting.

Can be extended to handle additional columns or new vendors.

📄 License
This project is released under the MIT License. Feel free to adapt and extend for your own workflows!
