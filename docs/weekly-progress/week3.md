# Week 3: Automation Design & Prototyping

## Objectives
- Transition from manual VAPT report QA to an automated software-driven approach.
- Design the initial UI for the **Document Compliance & Validation Application**.
- Structure and integrate the underlying cybersecurity knowledge base.

## Tasks Completed
### Application Architecture & UI Prototyping
- Conceptualized the core architecture of the application, splitting it into a frontend dashboard and a backend parsing/validation engine.
- Designed the initial "DCV Checker" interface, establishing the layout for uploading documents, viewing compliance scores, and managing validation rules.

### Knowledge Base Curation & Integration
To power the automated checks, the application required structured dictionaries. I curated and loaded the following datasets into the system:
- **Dictionary**: Over 6,700 standard entries.
- **Cybersecurity Terms**: Over 430 domain-specific terms.
- **Acronyms**: Over 110 common industry acronyms.
- **Vulnerability KB**: Over 110 tracked CVEs for contextual matching.

## Engineering Challenges Addressed
- **Data Modeling**: Structuring the disparate datasets into JSON formats optimized for rapid, in-memory lookup during document scans.
- **UI Layout**: Designing a dashboard capable of cleanly presenting complex QA metrics (Findings, Critical Issues, Validations) without overwhelming the user.

## Learning Outcomes
- Transitioned from manual spreadsheet tracking (Week 2) to software architecture design.
- Gained hands-on experience in managing and structuring large domain-specific datasets (cybersecurity terminology).
- Began applying UI/UX principles to security tooling.
