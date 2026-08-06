# Offline Bulk OCR Studio (`o-bulk-ocr-studio`)

![Version](https://img.shields.io/badge/version-v1.7.0--offline-blue.svg)
![Air-Gapped](https://img.shields.io/badge/air--gapped-100%25-success.svg)
![IndexedDB](https://img.shields.io/badge/storage-IndexedDB%20(Dexie.js)-orange.svg)
![License](https://img.shields.io/badge/license-MIT-green.svg)

**Offline Bulk OCR Studio** (`o-bulk-ocr-studio`) is a 100% air-gapped, zero-internet-required variant of Bulk OCR Studio. It is specifically built for restricted enterprise and office environments where Python installations, network calls, and external server connections are strictly forbidden.

---

## 🔒 100% Offline & Vendored Architecture
All core JavaScript libraries—including **Tesseract.js**, **PDF.js**, **SheetJS (xlsx)**, **JSZip**, **Dexie.js (IndexedDB)**, and **Lucide Icons**—are locally vendored inside the `./vendor/` directory and referenced via relative paths. 

* **Zero External Calls**: Once placed on your local machine or laptop, you can unplug your internet entirely. The app runs completely inside your browser's sandboxed WebAssembly and Web Worker environment.
* **IndexedDB Caching**: Document processing, regex searches, low-confidence word reviews, and JSONC exports all execute locally with zero data leakage.

---

## 🚀 Quick Start

1. Open `o-bulk-ocr-studio/index.html` directly in any modern desktop/laptop browser (Chrome, Safari, Firefox, Edge).
2. Drag and drop your folders of images, PDFs, CSVs, or Excel spreadsheets.
3. Review low-confidence words, configure LLM schemas/prompts, and export schema-compliant `.jsonc` payloads for downstream LLMs!
