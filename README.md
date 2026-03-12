# Codal Financial Scraper

A Selenium-based scraper for [Codal.ir](https://codal.ir), the official disclosure portal of the Iranian stock exchange (Tehran Stock Exchange and Iran Fara Bourse). Collects structured financial report data for listed companies.

## What it collects

For each company, the scraper downloads and parses:
- **Monthly activity reports** — sales volume, units sold, and operational metrics per period
- **Annual and interim fiscal reports** — balance sheets, income statements, and cash flow statements (audited and unaudited)

All data is saved as Excel files, organized by company ID and report type.

## Structure

| File | Role |
|---|---|
| `codal_normal_functions.py` | Utility functions (Persian digit conversion, text cleaning, Excel I/O) |
| `codal_oop_functions.py` | `stock_codal`, `activity`, and `fiscal` classes — company and report objects |
| `codal_oop_table_functions.py` | HTML table parsing (`cell`, `table`, `codal_table`) and Excel file generation (`make_file`) |
| `codal_main_function.py` | Main scraping loop — iterates companies, paginates reports, fetches and saves tables |
| `all_in_one.py` | Standalone version combining all modules |
| `stock_names.xlsx` | Input file listing company names and IDs to scrape |

## Usage

1. Populate `stock_names.xlsx` with the target company symbols
2. Run `codal_main_function.py` and provide start/end row indices
3. Output Excel files are written to `codal/<company_id>/`
