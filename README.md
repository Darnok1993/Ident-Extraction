# Ident Extraction App

#### Video Demo: https://www.youtube.com/watch?v=BiEitp3IfJ8
#### Author: Konrad Wranik  
#### GitHub: Darnok1993  
#### Location: Fürth, Germany  
#### Date: July 2025

---

## 📌 Overview

The Ident Extraction App is a web-based tool that enables users to extract structured identifiers (Idents) from technical documents in PDF, Word (.docx), or Excel (.xlsx) formats. These identifiers typically follow a standardized pattern commonly used in manufacturing and documentation systems.

Extracted data is automatically cleaned, deduplicated, and exported as an Excel file — ready for further analysis. The tool was built with Flask (Python) powering the backend and Bootstrap providing a responsive and user-friendly frontend interface.

This project addresses a real-world challenge encountered in industrial settings at my company, where manual inspection and comparison of test reports and technical documents is inefficient, error-prone, and hard to scale.

Within our validation department, we often perform revalidations that depend heavily on historical validations. This involves thoroughly reviewing legacy documents to understand their contents and identify which documents are referenced. A key part of this process is determining whether existing documents can be reused as-is in the new validation workflow or whether they must be replaced by equivalent documents from related sectors.

By systematically analyzing past documentation, we uncover what was previously included, what remains relevant today, and what new information must be incorporated. This comparison facilitates the creation of updated, accurate validation documentation aligned with current standards and requirements.

Manual review of these documents is time-consuming and susceptible to human error. Automating the extraction of structured identifiers from technical files not only streamlines the process but also reduces mistakes and greatly accelerates the preparation of new validation materials.

The Ident Extraction App integrates seamlessly into this workflow, offering a reliable and automated solution to collect and analyze document identifiers across multiple file types, thereby enhancing quality assurance, traceability, and overall document management efficiency in our industrial environment.

---

## 🚀 Features

- Upload support for `.pdf`, `.docx`, and `.xlsx` files
- Pattern recognition using **regular expressions (regex)**
- Dynamic extraction from:
  - PDFs
  - Word files
  - Multiple Excel sheets
- Export of results to an `.xlsx` file
- Automatic deduplication and formatting
- Temporary file handling with automatic deletion after download
- Responsive user interface using Bootstrap 5

---

## 🧱 Tech Stack

- **Python 3**
- **Flask** – backend web framework
- **pandas** – for data manipulation
- **regex** – for pattern matching
- **python-docx** – to parse Word files
- **PyMuPDF (fitz)** – to read PDF content
- **Bootstrap 5** – for styling the frontend

---

## 🗂 Project Structure

Ident-Extraction/
├── app.py # Main Flask application
├── uploads/ # Temporary folder for uploaded and processed files
├── templates/
│ └── index.html # Upload interface
├── README.md # This file
├── requirements.txt # Python dependencie

---

## 🔍 Pattern Explanation

The application extracts identifiers that follow a typical format used in technical documentation, such as:

ABCD-XYZ-123-01

Each component is parsed as:

- **Document Code**
- **Type**
- **Part**
- **Version** (optional)

Regex pattern used:

```python
(?P<DocNumber>[a-zA-Z0-9-_]+)\n?-(?P<DocType>[a-zA-Z0-9]{3})\n?-(?P<DocPart>[a-zA-Z0-9]{3})\n?-?(?P<DocVersion>\d{1,2})
```

The pattern matches document identifiers with the following components:

DocNumber: The first part of the identifier, which consists of one or more alphanumeric characters, dashes (-), or underscores (_). This segment typically represents the main document and can include letters (both uppercase and lowercase), numbers, and some special characters.
Example: ABCD_123, X-45, test_01

DocType: Exactly three alphanumeric characters following a dash. This usually denotes the type or category of the document or component. The strict length of three characters helps ensure uniformity.
Example: XYZ, ABC, 123, AB1

DocPart: Exactly three alphanumeric characters following a dash. This represents a subclassification or specific type within the broader DocType category. It helps to further specify the part or section within the document or product series.

DocVersion: An optional one- or two-digit numeric version number. This indicates the version or revision of the document or part.
Examples: 1, 12, or omitted if no version is specified.

---

🧠 Design Considerations

Lightweight Framework: Flask was chosen for its simplicity and fast setup.

Unique Filenames: UUID-based file naming prevents collisions and improves security.

Auto-Deletion: Temporary upload and output files are deleted automatically after download.

Flexible Regex: The pattern can be easily adapted to other identifier formats.

Scalability: The modular code structure allows for easy future expansion, e.g., additional file formats or output options.

---

🤖 AI Tool Usage
Parts of this project — particularly Flask error handling and concept refinement — were developed with support from ChatGPT.

My approach is to first write the code independently and then iteratively improve it through a “philosophical ping-pong” with AI — asking for feedback, alternative solutions, and edge-case handling. Every suggestion was critically reviewed and adjusted before integration.

This tool is now successfully used in my company’s workflow and has significantly improved document processing efficiency.

ChatGPT also supported me in drafting and polishing this README.md — in line with its intended use to assist with clarity and communication. The final content, however, reflects my full ownership and understanding of the code and its purpose.