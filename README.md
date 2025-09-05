````markdown
# PDF OCR and Summarisation for GitHub Repositories

This script scans a GitHub repository for PDF files, downloads them, extracts text (using **OCR** for scanned files or direct extraction for digital files), generates summaries with Hugging Face models, extracts keywords and named entities, calculates readability scores, and outputs all results in **JSON format**.

---

## Features
- 🔍 Automatically list **all PDFs** in a GitHub repo (recursively).
- 📥 Download and process PDFs:
  - Direct text extraction for digital PDFs.
  - OCR (Tesseract) for scanned PDFs.
- 📝 Summarise content using Hugging Face models:
  - BART, T5, FLAN-T5.
- 📊 Analyse text for:
  - Keywords
  - Named entities
  - Readability metrics
- 💾 Save results in a structured JSON file.
- ✅ Works in **Google Colab** (system dependencies auto-installed).

---

## Requirements

The script installs missing Python packages automatically:

- `pytesseract`
- `pdf2image`
- `transformers`
- `torch`
- `sentencepiece`
- `einops`
- `accelerate`
- `spacy`
- `textstat`
- `tqdm`
- `numpy`
- `requests`
- `PyPDF2`

### System dependencies (only needed if running locally)
- **Poppler** (for `pdf2image`)
- **Tesseract OCR**

On Linux (Debian/Ubuntu):
```bash
sudo apt-get install poppler-utils tesseract-ocr
````

On Windows and MacOS, install Poppler and Tesseract manually and add them to your PATH.

> On **Google Colab**, these system dependencies are installed automatically.

---

## Quickstart

### 1. Clone this repository

```bash
git clone https://github.com/yourusername/pdf-ocr-summariser.git
cd pdf-ocr-summariser
```

### 2. Run the script

```bash
python3 pdf_ocr_github.py
```

### 3. Provide inputs interactively

Example run:

```
Enter GitHub repository owner: seansphd
Enter GitHub repository name: PAGE-Archive
Enter repository path (leave blank for root):
Enter GitHub token (leave blank if not needed):

Do the PDFs require OCR? (y/n): y
Enter OCR resolution (DPI, recommended 300): 300
Enhance images before OCR? (y/n): y

Available models:
1. BART CNN (fast)
2. T5 Small (fastest)
3. T5 Base (balanced)
4. FLAN-T5 Base (recommended)
5. FLAN-T5 Large (better quality)

Select model (1-5): 1
Enter output JSON filename (default: pdf_summaries.json):
```

### 4. Output

A JSON file (default: `pdf_summaries.json`) containing structured results for each PDF:

```json
[
  {
    "pdf_name": "example.pdf",
    "url": "https://github.com/.../example.pdf",
    "status": "success",
    "num_pages": 12,
    "word_count": 3456,
    "summary": "This PDF discusses ...",
    "top_keywords": {"Artificial Intelligence": 5, "Archives": 3},
    "readability": {
      "flesch_reading_ease": 45.2,
      "word_count": 3456
    },
    "entities": {
      "ORG": ["Computer Arts Society"],
      "DATE": ["1969"]
    }
  }
]
```

---

## Example Run

For the [PAGE-Archive](https://github.com/seansphd/PAGE-Archive) repository:

```
Enter GitHub repository owner: seansphd
Enter GitHub repository name: PAGE-Archive
```

This will process all PDFs in the archive and save results to `pdf_summaries.json`.

---

## Notes

* Use OCR only for scanned PDFs; direct extraction is faster and more accurate.
* Large models (e.g. FLAN-T5 Large) may be slow without GPU acceleration.
* The script saves progress after each file to avoid data loss when batch processing large repositories.

```

Do you want me to also add **badges** (e.g. Python version, Colab link, license) so it looks more like a polished GitHub project?
```
