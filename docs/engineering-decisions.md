# Engineering Decisions & Trade-offs

During the development of the Compliance Checking Application, several high-level architectural and engineering decisions were made. This document outlines the rationale behind the technologies selected and the trade-offs considered.

## 1. Desktop Application vs. Web Application
**Decision**: The application was built as a standalone Windows desktop executable using CustomTkinter rather than a cloud-hosted web application.
**Rationale**: 
* **Data Privacy**: Cybersecurity VAPT reports contain highly sensitive client vulnerability data. Keeping all processing local on the analyst's machine ensures zero data leaves the corporate network, eliminating cloud transit risks.
* **Trade-off**: Distributing updates requires repacking and distributing a new executable, which is harder to manage than a centralized web app deployment. This was mitigated by building a dynamic learning queue so the rules engine could update locally without requiring a software patch.

## 2. Python as the Core Language
**Decision**: Python 3.x was selected as the primary language.
**Rationale**: Python offers unparalleled libraries for computer vision (OpenCV), document parsing (PyMuPDF), and rapid UI prototyping. It allowed for quick iteration on complex text matching algorithms.
* **Trade-off**: Python is generally slower than compiled languages like C++ or Go, which could be an issue when processing massive PDFs. This was mitigated by relying on C-bound libraries (like PyMuPDF and NumPy) for heavy lifting.

## 3. CustomTkinter for GUI
**Decision**: CustomTkinter was chosen over PyQt or standard Tkinter.
**Rationale**: Standard Tkinter looks outdated, and PyQt introduces heavy, complex licensing dependencies. CustomTkinter provided a modern, dark-mode compatible interface that matched enterprise aesthetic requirements while remaining lightweight and entirely native to Python.

## 4. Asynchronous Threading Model
**Decision**: Implementing Python's `threading` module to decouple the UI event loop from document processing tasks.
**Rationale**: Parsing hundreds of pages and executing computer vision algorithms on embedded images is blocking. Without threading, the GUI would freeze ("Not Responding") during scans.
* **Trade-off**: Managing thread safety and race conditions (especially when updating UI widgets from background threads) added significant complexity to the codebase.

## 5. JSON for Knowledge Base Storage
**Decision**: Storing the dynamic knowledge bases (dictionaries, acronyms, CVEs) as flat JSON files rather than a relational database (e.g., SQLite).
**Rationale**: JSON allows for extremely fast loading into Python dictionaries for in-memory lookup. It also makes the data structure highly portable and easily packable by PyInstaller.
* **Trade-off**: Flat JSON files do not support concurrent writes well, but since the application is single-user and local, this limitation was deemed acceptable.

## 6. PyInstaller for Deployment
**Decision**: Utilizing PyInstaller to bundle the application.
**Rationale**: Allowed the complex environment (containing OpenCV binaries, UI themes, and document parsers) to be delivered as a single `.exe` file to analysts who may not have Python installed.
* **Trade-off**: Generated large file sizes and required complex `.spec` file configurations to properly map hidden imports and internal data assets.
