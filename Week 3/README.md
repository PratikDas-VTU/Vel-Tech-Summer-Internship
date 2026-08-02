# Week 3: Automation Design & Prototyping

## Objectives
- Transition from manual VAPT report QA to an automated software-driven approach.
- Design the initial UI for the Document Compliance Validation tool.
- Structure and integrate the underlying cybersecurity knowledge base.

## Activities
1. **Application Prototyping**: Designed the initial "DCV Checker" interface, establishing the layout for uploading documents and viewing compliance scores.
2. **Knowledge Base Integration**: Curated and loaded datasets into the system's Rules Engine, including a massive dictionary, cybersecurity terms, acronyms, and a vulnerability KB tracking CVEs.
3. **Data Modeling**: Structured the disparate datasets into JSON formats optimized for rapid, in-memory lookup during automated document scans.

## Learning
- Transitioned from manual spreadsheet tracking to software architecture design.
- Gained hands-on experience in managing and structuring large domain-specific datasets.
- Began applying UI/UX principles to security tooling.

## Technologies Used
- Python, CustomTkinter, JSON data structures.

## Challenges
- Designing a dashboard capable of cleanly presenting complex QA metrics without overwhelming the user.
- Normalizing thousands of distinct cybersecurity terms into a uniform database structure.

## Key Outcomes
- Successfully laid the foundation for the automated compliance application.
- Initialized the core Rules Engine which will power the automated checks in the final week.

## Screenshots
### Initial Interface Prototype
![Initial Interface](Screenshots/01_Initial_Interface.jpeg)

### Rules Engine Integration
![Rules Engine](Screenshots/02_Rules_Engine.jpeg)
