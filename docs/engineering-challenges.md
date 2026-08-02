# Engineering Challenges

Building the Compliance Checking Application required solving several complex engineering hurdles, blending document parsing, algorithm design, and UI performance.

## 1. Cross-Format Normalization
**The Challenge**: The application needed to parse reports spanning disparate formats—primarily PDF and DOCX. PDFs rely on absolute coordinate-based rendering, making text extraction messy and unstructured. DOCX files rely on a continuous XML-based flow. 
**The Solution**: Engineered a unified parser interface that abstracts the underlying file type. The PyMuPDF (PDF) and python-docx (Word) modules feed raw text, styling metadata, and embedded images into a standardized internal data model. The validation engines only ever interact with this normalized structure, remaining entirely decoupled from file format logic.

## 2. False Positive Reduction in Branding Validation
**The Challenge**: Ensuring the correct organizational logo is present on client deliverables. A naive image matching algorithm would flag a document as "non-compliant" if it detected a third-party vendor logo (e.g., a firewall provider) instead of the primary client logo.
**The Solution**: Developed a weighted discovery algorithm that analyzes the semantic context surrounding the image. By determining if the extracted text denotes the primary organization versus a tertiary tool/vendor mentioned in passing, the algorithm assigns a confidence score to the logo, drastically reducing false positives.

## 3. Contextual Text Analysis for Vulnerabilities
**The Challenge**: It is not enough to simply regex-search a document for "CVE-XXXX-XXXX". To be compliant, a vulnerability mention must be accompanied by its severity context (e.g., a CVSS score) nearby. 
**The Solution**: Built a semantic matching engine that dynamically bounds its search window around a detected CVE. It intelligently handles edge cases where multiple CVEs are listed in a single table or paragraph by establishing localized text boundaries, ensuring the correct CVSS score is associated with the corresponding CVE.

## 4. Non-Blocking UI with Heavy Processing
**The Challenge**: The initial prototype froze completely during document scans. Initializing the computer vision models and parsing massive PDFs blocked the main Python execution thread, resulting in a poor user experience.
**The Solution**: Implemented a multi-threaded architecture. The core processing engine operates on background daemon threads, communicating state changes and progress metrics back to the main CustomTkinter GUI thread via thread-safe event queues. This ensures the UI remains highly responsive, allowing the dashboard KPIs to update in real-time.

## 5. Packaging Complex Dependencies
**The Challenge**: Distributing a Python application requiring deep C-bindings (PyMuPDF, OpenCV) and massive internal UI assets to non-technical end users.
**The Solution**: Configured PyInstaller with a heavily customized `.spec` file to force the inclusion of hidden imports, custom rule datasets, and GUI themes into a single, portable executable requiring zero external installation steps from the user.
