# PDF OCR and Summarisation for GitHub Repositories

This project automates the process of finding PDF files in a GitHub repository, extracting their text, and producing structured summaries in JSON format. It is designed to support archives and collections where PDFs may be a mixture of scanned and born-digital documents.

The script uses both direct PDF text extraction and OCR (optical character recognition). You can choose whether OCR is required. Summaries are generated using transformer models from Hugging Face.

The final output is a single JSON file where each entry has the following fields:

* **filename** – the original PDF file name
* **summary** – a condensed text summary of the PDF
* **url** – a link to the PDF on GitHub

---

## Features

* Scans any GitHub repository for PDF files
* Extracts text directly when available, or uses OCR when required
* Generates summaries with models such as BART or FLAN-T5
* Saves all results in one JSON file
* Designed to resume safely, saving after each file is processed

---

## How It Works

1. The script connects to the GitHub repository using the API.
2. It lists all PDFs in the repository and its subfolders.
3. For each PDF:

   * Downloads the file
   * Extracts text (directly or with OCR)
   * Cleans and processes the text
   * Generates a summary using a selected model
4. Writes the results into a JSON file with one entry per PDF.

---

## Quickstart

1. Clone this repository and install Python 3.
2. When you run the script, it will install all required Python packages automatically.
3. Provide the following when prompted:

   * GitHub repository owner and name
   * Path within the repository (leave blank to scan the whole repo)
   * Personal access token (optional but recommended to avoid rate limits)
   * Whether OCR is required
   * Your choice of summarisation model
   * Output filename for the JSON results
4. The script will then process all PDFs and save results in the specified JSON file.

---

## Output

The JSON file is an array of objects, each containing a filename, a summary, and a GitHub URL. This format makes it easy to reuse the results in archives, catalogues, or other projects.

---

Do you want me to also add a short **“Recommended use cases”** section (e.g. for archives, research collections, bulletins), or keep it strictly technical?
