# Design System & Architecture Master (UI-UX-Pro-Max & Frontend-Design)

This document serves as the global source of truth for design tokens, typography, spacing, component standards, and codebase architecture for Bulk OCR Studio.

## 1. Design Tokens & Palette
- **Primary Color:** Indigo (`#6366f1` / `bg-indigo-600`) with Violet gradients.
- **Background Palette:** Slate 950 (`#020617`) for deep canvas, Slate 900 (`#0f172a`) for containers, Slate 800 (`#1e293b`) for cards and elevated panels.
- **Text Hierarchy:**
  - Headings: Slate 50 (`#f8fafc`) bold, tight letter spacing.
  - Body: Slate 300 (`#cbd5e1`) for readability.
  - Muted/Metadata: Slate 400 (`#94a3b8`) or Slate 500 (`#64748b`).
- **Accent & Status Colors:**
  - Success: Emerald 400 (`#34d399`)
  - Warning/Pending: Amber 400 (`#fbbf24`)
  - Error: Red 400 (`#f87171`)

## 2. Typography
- **Font Family:** System sans-serif (`font-sans antialiased`).
- **Monospace Code / Text Areas:** JetBrains Mono / Fira Code fallback (`font-mono`).

## 3. Spacing & Layout Rhythm
- Consistent border radius: `rounded-xl` (12px) and `rounded-2xl` (16px) for cards and modals.
- Clean grid auto-fill structures and flexbox layouts with strict overflow handling.

## 4. Frontend Architecture
- 100% Client-side modular design.
- Zero server dependencies; pure browser-based execution via Web Workers (Tesseract.js) and WebAssembly (PDF.js).
- Reactive state management with immediate UI updates, real-time ETA calculation, and robust error handling.
