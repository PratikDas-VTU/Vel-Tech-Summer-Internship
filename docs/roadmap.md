# Roadmap & Milestones

The Compliance Checking Application was developed rapidly over a one-month summer internship. Below is a high-level roadmap of completed milestones and potential future enhancements.

## Completed Milestones
* [x] **Core Parsing Engine**: Unified ingestion of PDF and DOCX formats.
* [x] **Vulnerability Context Engine**: Intelligent semantic matching for CVE/CVSS validation.
* [x] **Branding Engine**: OpenCV-based image extraction and logo consistency verification.
* [x] **Dynamic Knowledge Base**: Curation of over 6,900 English words, 430+ cyber terms, 110+ acronyms, and 110+ tracked vulnerabilities.
* [x] **Enterprise GUI**: Responsive, multi-threaded CustomTkinter dashboard.
* [x] **Standalone Deployment**: Fully packaged `.exe` via PyInstaller.

## Future Improvements
* **Cloud API Integration**: Integrating directly with NVD (National Vulnerability Database) APIs to fetch real-time CVE data, replacing the static local JSON knowledge base.
* **LLM Semantic Checking**: Augmenting the regex-based validation engines with a lightweight Local LLM (Large Language Model) to perform deeper contextual and grammar checks on analyst writing.
* **Expanded File Support**: Extending the unified parser to handle markdown (`.md`) and raw HTML reports.
* **Cross-Platform Compilation**: Refining the PyInstaller build process to generate native macOS and Linux binaries.

---
*Note: Due to organizational confidentiality, the source code supporting these milestones remains closed-source. It will only be published if explicit approval is received from the organization.*
