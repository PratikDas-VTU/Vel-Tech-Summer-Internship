# Technology Stack

The Compliance Checking Application was built utilizing a modern, scalable Python stack designed to handle complex document processing, computer vision, and desktop GUI requirements.

## Core Language
* **Python 3.x**: Chosen for its robust ecosystem in data processing, rapid prototyping, and extensive library support.

## Document Parsing & Processing
* **PyMuPDF**: Utilized for highly efficient PDF reading, text extraction, and metadata handling.
* **python-docx**: Used for parsing XML-based Word document flows.

## Computer Vision & Image Processing
* **OpenCV (`cv2`) & NumPy**: Applied for extracting embedded images from documents, fingerprinting them, and executing pattern-matching algorithms to verify organizational branding and logo consistency.

## Desktop GUI Framework
* **CustomTkinter**: Selected to build a modern, responsive, dark-mode compatible graphical user interface, featuring interactive dashboards and non-blocking event loops.

## Reporting & Output
* **ReportLab**: Employed to dynamically generate comprehensive, finalized PDF compliance reports based on scan results.

## Linguistics & Validation
* **`pyspellchecker`**: Integrated for baseline terminology and spelling validation against custom cybersecurity dictionaries.
* **Regex Engine**: Advanced regular expressions utilized for semantic vulnerability matching (e.g., CVE/CVSS detection).

## Data Persistence & State
* **JSON**: Used as the lightweight, local storage format for application configuration and the dynamic ruleset/knowledge base state.

## Packaging & Distribution
* **PyInstaller**: Utilized for DevOps and packaging, compiling the complex Python application, C-based binaries (OpenCV/PyMuPDF), and local data assets into a standalone, portable Windows executable for enterprise distribution.
