# Ident Extraction App

#### Video Demo: [Insert YouTube URL here]  
#### Author: Konrad Wranik  
#### GitHub: [your GitHub username]  
#### Location: Fürth, Germany  
#### Date: July 2025

---

## 📌 Overview

The **Ident Extraction App** is a web-based tool that allows users to extract structured **identifiers (Idents)** from technical documents in PDF, Word (`.docx`), or Excel (`.xlsx`) formats. These identifiers typically follow a standardized pattern used in manufacturing or documentation systems.

The extracted data is automatically cleaned, deduplicated, and exported as an Excel file — ready for analysis. The tool was developed using **Flask (Python)** for the backend and **Bootstrap** for the frontend interface.

This project is based on a **real-world use case** and solves a recurring problem in industrial environments at my company, where manual inspection of test reports and documents is inefficient and error-prone.

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

ident-extraction/
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
(?P<DocNumber>[a-zA-Z0-9-_]+)\n?-(?P<DocType>[a-zA-Z0-9]{3})\n?-(?P<DocPart>[a-zA-Z0-9]{3})\n?-?(?P<DocVersion>\d{1,2})?

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