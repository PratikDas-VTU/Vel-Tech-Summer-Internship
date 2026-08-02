# System Architecture

The Compliance Checking Application follows a modular, pipelined architecture designed to process disparate document formats, run them through parallel validation algorithms, and generate a unified compliance report.

## High-Level Data Flow

The following diagram illustrates a generalized workflow of a document entering the system, passing through the core processing engines, and resulting in an exported PDF report.

```mermaid
graph TD
    %% Input Layer
    subgraph Input Phase
        A[Client Security Report] -->|Upload| B(File Type Router)
        B -->|PDF| C[PyMuPDF Parser]
        B -->|DOCX| D[python-docx Parser]
    end

    %% Processing Layer
    subgraph Core Processing Engine
        C --> E[Normalized Data Model]
        D --> E
        E --> F{Validation Orchestrator}
    end

    %% Validation Layer
    subgraph Parallel Validation Modules
        F --> G[Terminology & Spelling Validation]
        F --> H[Semantic Vulnerability Engine]
        F --> I[Computer Vision Branding Engine]
    end

    %% Knowledge Base Layer
    subgraph Dynamic Knowledge Base
        J[(Dictionaries & Terms)] -.->|Rules Data| G
        K[(CVE/CVSS Database)] -.->|Validation Rules| H
        L[(Organization Assets)] -.->|Logo Signatures| I
    end

    %% Output Layer
    subgraph Output Phase
        G --> M[Aggregated Results]
        H --> M
        I --> M
        M --> N(Dashboard UI Display)
        M --> O[ReportLab PDF Exporter]
        O --> P[Final Compliance Report]
    end
```

## Architectural Components

1. **Input Layer (Parsers)**: Abstracts the differences between coordinate-based PDFs and XML-based DOCX files, extracting raw text, metadata, and embedded images.
2. **Core Processing Engine**: Normalizes the extracted data into a unified object model, readying it for the validation modules.
3. **Parallel Validation Modules**: Independent modules focusing on linguistics, semantic context matching (for CVEs), and computer vision (for branding checks).
4. **Dynamic Knowledge Base**: JSON-driven, local data stores that feed the validation engines. Unknown terms encountered during processing are sent to a Learning Queue for future inclusion.
5. **Output Phase**: Scan results are fed back to the CustomTkinter GUI asynchronously to ensure UI responsiveness, and a detailed PDF report is exported for auditing purposes.
