# Bulk OCR & LLM Pipeline Studio

![Version](https://img.shields.io/badge/version-v1.4.0-blue.svg)
![Client-Side](https://img.shields.io/badge/client--side-100%25-success.svg)
![IndexedDB](https://img.shields.io/badge/storage-IndexedDB%20(Dexie.js)-orange.svg)
![License](https://img.shields.io/badge/license-MIT-green.svg)
![Build Status](https://img.shields.io/badge/build-passing-brightgreen.svg)

**Bulk OCR & LLM Pipeline Studio** is a 100% client-side, browser-based document ingestion and Optical Character Recognition (OCR) studio. It is specifically engineered to ingest, parse, and package messy multi-format document corpora into structured, schema-compliant **JSONC (JSON with Comments)** payloads ready for downstream Large Language Model (LLM) agents, Retrieval-Augmented Generation (RAG) pipelines, and automated data extraction modules.

---

## 🌟 What It Does, How, and Why

### 1. What It Does
* **Multi-Format Ingestion**: Ingests individual files, entire local directories, or drag-and-drop batches spanning:
  * **Images**: PNG, JPG, WEBP, BMP, TIFF, GIF (via Tesseract.js OCR)
  * **PDF Documents**: Multi-page PDFs (automatically split and rendered page-by-page into high-resolution canvases)
  * **Spreadsheets**: Excel (`.xlsx`, `.xls`) workbooks parsed sheet-by-sheet into structured text
  * **Tabular Data**: CSV files
  * **Text & Markdown**: `.txt` and `.md` files with zero overhead
* **Per-Page Processing & Inspection**: Inspect, review, and manually edit extracted text page-by-page side-by-side with original document previews.
* **LLM Schema & Prompt Packaging**: Embeds custom system prompts and target JSON Schemas directly into `.jsonc` exports so downstream LLMs know exactly how to validate and extract structured entities.
* **Real-Time Token Estimation**: Calculates approximate token usage in real time to ensure your batches fit within LLM context limits.

### 2. How It Works (Architecture)
* **Zero Server Calls (100% Client-Side)**: All PDF rendering (PDF.js), OCR inferencing (Tesseract.js), spreadsheet parsing (SheetJS), and ZIP compression (JSZip) run locally in your browser using WebAssembly and Web Workers. Your files never leave your computer.
* **IndexedDB Persistence (Dexie.js)**: As documents are parsed and processed, results are auto-saved to IndexedDB. This prevents UI freezes and guarantees that your work survives browser refreshes or accidental tab closures.

### 3. Why It Exists
Traditional OCR tools output flat text or fragile formats without provenance, making them difficult to pipe into LLMs. Bulk OCR Studio solves this by turning raw document folders into **self-describing, schema-validated JSONC payloads** equipped with system prompts, word counts, metadata, and comments for seamless RAG and agentic workflows.

---

## 🚀 Quick Start & User Guide

### Running Locally

Because modern web browsers enforce strict security policies on `file://` URLs (treating every file as a unique security origin and blocking Web Workers or local asset fetches), we recommend running a lightweight local HTTP server:

1. **Using Python (Recommended for Air-Gapped/Offline environments)**:
   ```bash
   python3 -m http.server 8000
   ```
   Then open: `http://localhost:8000/o-bulk-ocr-studio/` (offline version) or `http://localhost:8000/bulk-ocr-app/` (CDN version).

2. **Using Node.js**:
   ```bash
   npx serve
   ```

*(Note: If you double-click `index.html` to open it directly from disk (`file://`), modern browsers restrict Web Workers and local sub-requests with CORS/security origin warnings).*

### Step-by-Step Usage Example

1. **Select Input Source**:
   * Click **Select Folder** to point the app to an entire local directory of PDFs and spreadsheets, or **Select Files** to choose individual documents.
   * Alternatively, drag and drop files/folders directly into the drop zone.

2. **Configure LLM Prompt & Schema (Optional)**:
   * Click **LLM Schema & Prompt** in the top navigation bar.
   * Define your custom system prompt and target JSON Schema (e.g. Pydantic-generated JSON schema).

3. **Run Batch Processing**:
   * Choose your OCR language (default is English `eng`).
   * Click **Process Queue**. Watch real-time progress bars, elapsed time, and live **Estimated Time to Remaining (ETA)** countdowns.

4. **Export as JSONC**:
   * Once processing completes, click **Preview JSONC** or **JSONC** in the toolbar to download your fully packaged, schema-ready `.jsonc` file for downstream LLM ingestion!

---

## 📂 Repository Structure

```text
bulk-ocr-studio/
├── bulk-ocr-app/
│   └── index.html       # 100% self-contained client-side application
├── design-system/
│   └── MASTER.md        # Global design tokens and architecture standards
├── PRODUCT.md           # Product overview and downstream consumer specs
├── DESIGN.md            # OKLCH-aligned design system and anti-slop rules
└── README.md            # Comprehensive documentation & quick start
```

---

## 🛡️ License
Distributed under the **MIT License**. Feel free to use, modify, and integrate into your data pipelines.
