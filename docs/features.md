# Core Features

This document outlines the high-level features of the Compliance Checking Application, focusing on the engineering concepts applied and problems solved.

## 1. Document Parsing Engine
* **Purpose**: To extract raw text, metadata, and embedded images from varied report formats.
* **Engineering Concepts**: A unified parser interface was designed to seamlessly handle both PDF (coordinate-based text extraction) and DOCX (XML-based flow) files. This engine normalizes disparate data into a standardized data model for downstream validation algorithms.
* **Skills Demonstrated**: Object-Oriented Programming (OOP) design, robust File I/O operations, and third-party API integration.

## 2. Branding Consistency Engine
* **Purpose**: To detect mismatched logos or incorrect organizational branding within security reports.
* **Engineering Concepts**: Utilizes computer vision algorithms to extract embedded images from scanned documents. These images are fingerprinted and compared against a known database of organizational assets. A weighted discovery algorithm analyzes surrounding text context to reduce false positives before flagging inconsistencies.
* **Skills Demonstrated**: Computer Vision (OpenCV), Algorithm Design, and False-Positive Mitigation techniques.

## 3. Vulnerability Validation System
* **Purpose**: To ensure all referenced security flaws contain necessary contextual information and accurate scoring.
* **Engineering Concepts**: Employs advanced regular expressions and a semantic matching engine to scan document text for vulnerability identifiers (e.g., CVEs). It then verifies that corresponding severity metrics (e.g., CVSS scores) are present within a localized text window, intelligently bounding its search to handle edge cases where multiple vulnerabilities are listed in close proximity.
* **Skills Demonstrated**: Text Pattern Matching, Cybersecurity domain knowledge, Contextual Analysis, and regular expression optimization.

## 4. Dynamic Knowledge Base & Learning Queue
* **Purpose**: To allow the application to adapt to new terminology over time, ensuring scalability.
* **Engineering Concepts**: A subsystem that tracks unknown terms during scans and places them in a "learning queue." Administrators can review and approve these terms into the permanent dictionary via a human-in-the-loop design. 
* **Data Scale**: The underlying proprietary knowledge base tracks thousands of data points, including standard English words, advanced cybersecurity terms, industry acronyms, verified CVE vulnerabilities, and security tools.
* **Skills Demonstrated**: Data Modeling, State Management, Human-in-the-loop application design, and extensive Domain Research.

## 5. Enterprise Metrics Dashboard
* **Purpose**: To provide a high-level overview of QA performance and application health.
* **Engineering Concepts**: A responsive, scrollable UI dashboard that aggregates scan history, knowledge base statistics, and critical issue trends into visual KPI cards. Implements threading mechanisms to ensure non-blocking UI behavior during heavy processing.
* **Skills Demonstrated**: Frontend GUI Development, Data Aggregation, UI/UX Design, and Asynchronous programming.
