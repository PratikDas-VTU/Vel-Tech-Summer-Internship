# Testing & Validation

## Iterative QA
To ensure the application was robust, I conducted rigorous testing against sample security assessment reports.

## Testing Process
* **Sample Data**: Utilized mock VAPT reports (e.g., sample `Dark Web Monitoring.pdf`) containing intentional errors, formatting inconsistencies, and missing CVE data.
* **Debugging**: Identified edge cases where the PDF parser would fail to extract text from heavily formatted tables. Adjusted the PyMuPDF parsing logic to better handle these unstructured layouts.
* **Accuracy Tuning**: Refined the spellchecker and terminology dictionaries to stop flagging standard cybersecurity industry jargon as "errors", significantly reducing the false-positive rate on the dashboard.
