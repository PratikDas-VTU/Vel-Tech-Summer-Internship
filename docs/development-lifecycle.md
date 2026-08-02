# Software Development Lifecycle

This document traces the engineering evolution of the Document Compliance & Validation Application. Note that this lifecycle maps the technical phases of the software build and is distinct from the chronological weekly internship logs.

## Phase 1: Foundation & Requirements
The project began by establishing the core repository structure and defining the abstract base classes (`BaseValidator`). The initial focus was entirely on data modeling: creating the foundational JSON rulesets that would house the cybersecurity terms, acronyms, and organizational dictionaries required for baseline QA checks.

## Phase 2: Parsers & Core Engine
The next critical step was data ingestion. The `docx_parser.py` and `pdf_parser.py` modules were developed to abstract away file-type differences. Simultaneously, the central `scanner.py` orchestrator was built to route incoming documents through the parsers and construct the unified, normalized text model.

## Phase 3: Basic Validators
With data successfully flowing into the system, the first tier of validation logic was implemented. This included building text-based modules (`spelling.py`, `terminology.py`, `sections.py`) to verify that reports adhered to standard structural and linguistic guidelines.

## Phase 4: Advanced Validators & Output
The logic increased in complexity with the introduction of the `vulnerability.py` engine, which implemented semantic context checking to ensure CVEs were properly paired with CVSS scores. To surface these findings, `report_exporter.py` was integrated, utilizing ReportLab to generate programmatic PDF compliance outputs.

## Phase 5: UI & Branding (The "Enterprise" Polish)
This phase transformed the backend scripts into an enterprise product:
* **UI Framework**: The CustomTkinter GUI framework was established (`main_window.py`, `theme.py`), providing a modern dark mode aesthetic.
* **Dashboard Construction**: The complex `dashboard.py` was built to display Trend KPIs, Knowledge Base statistics, and the Activity Timeline.
* **Branding Engine**: The `BrandingEngine` (`branding.py`) was integrated, incorporating OpenCV computer vision to execute the logo and brand-matching algorithms.

## Phase 6: Packaging & Optimization
The final phase focused on DevOps and deployment. The `ComplianceChecker.spec` file was created, optimizing PyInstaller to successfully bundle the hidden imports, C-binaries, and local datasets into a final, portable standalone Windows executable.
