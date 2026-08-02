# Feature Development

## Core Processing Engine
The primary feature developed during Week 3 was the backend processing engine.

### Knowledge Base Loading
To power the automated checks, the application required structured dictionaries. I successfully loaded the following datasets into the system:
- **Dictionary**: Over 6,700 standard entries.
- **Cybersecurity Terms**: Over 430 domain-specific terms.
- **Acronyms**: Over 110 common industry acronyms.
- **Vulnerability KB**: Over 110 tracked CVEs for contextual matching.

### Parsing Implementation
I began writing the abstract base classes (`BaseValidator`) and the format-specific parsers (`pdf_parser.py` using PyMuPDF and `docx_parser.py`) to extract raw text and metadata, normalizing it into a standard format for the upcoming validation engines.
