September 2026 Sales Analysis

This project reads the electronics sales export with Python's standard-library csv module, cleans messy numeric fields, calculates comprehensive sales metrics, outputs a formatted text report, and uses pandas exclusively at the end to independently audit and verify headline results.

Project Structure

sales_analysis.py: Main execution script containing all standard-library data ingestion, cleaning pipelines, custom statistical functions, and pandas cross-verification.

data/electronics_sales.csv: Raw transactional dataset containing sales records from various branches across Kenya.

output/sales_report.txt: Generated text summary featuring revenue breakdowns, top-performing products, high-value orders, and key metrics.

Running the Script

Ensure you are in the project directory, then run:

python sales_analysis.py


Note: Core data loading, cleaning, and statistical calculations rely purely on Python's built-in libraries. Pandas must be installed solely for the final verification routine.

Data Cleaning Rules

Whitespace & Delimiters: Numeric values are stripped of surrounding whitespace and thousands separators (commas).

Currency Symbols: Leading KES currency prefixes are safely removed (e.g., repairing records like KES 18999).

Anomalies & Textual Numbers: Blank entries, N/A, NONE, and textual inputs like two are safely parsed or rejected based on robust dictionary mappings.

Positive Constraints: Quantity and unit price must both be strictly greater than zero. Invalid records are filtered out and logged into a skipped-rows manifest retaining their unique sale_id and error reason.

Custom Statistical Engine

To deepen data structures knowledge, statistical aggregations (mean, median, minimum_maximum) are implemented natively without importing the statistics module.

Tie-Breaking Strategy: When calculating top performers using top_n(), multi-level sorting handles financial revenue ties deterministically:

Primary sorting by revenue volume in descending order.

Secondary alphabetical tie-breaker (A–Z) by item name.
