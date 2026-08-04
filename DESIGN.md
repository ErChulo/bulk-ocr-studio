# DESIGN.md

## Aesthetic Direction
- **Style**: Precision Utility / Professional Developer Tool
- **Color Palette (OKLCH-aligned / Tailwind)**:
  - Canvas: Deep Slate 950 (`#020617`)
  - Containers: Slate 900 (`#0f172a`) with subtle 1px borders (`#1e293b`)
  - Accent: Vibrant Indigo (`#6366f1`) and Violet (`#8b5cf6`) with smooth gradients
  - Text: High-contrast Slate 50 (`#f8fafc`) for headings, Slate 300 (`#cbd5e1`) for body, Slate 400 (`#94a3b8`) for metadata
- **Typography**:
  - Sans: System sans-serif with tight letter spacing for UI headers
  - Mono: JetBrains Mono / Fira Code for extracted text previews and JSONC code blocks
- **Spatial Rhythm**:
  - Consistent 8px baseline grid (`p-3`, `p-5`, `space-y-4`)
  - Rounded corners: `rounded-2xl` and `rounded-3xl` for modern framing
- **Anti-Slop Rules**:
  - No generic overused font monoculture (clean sans + mono pairing)
  - No unmotivated purple-to-blue full background gradients; instead, purposeful focal accents on primary actions
  - Clear visual feedback states (loading spinners after 1s delay, live ETA estimation, status badges)
