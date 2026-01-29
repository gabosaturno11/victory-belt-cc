# SATURNO COMMAND CENTER V3
## Victory Belt | The Art of Calisthenics

---

## What Is This

A single-file command center for managing the production of **The Art of Calisthenics** book by Gabo Saturno, published by Victory Belt Publishing. Built with the TITAN Design Language.

**Live:** Deployed to GitHub Pages
**State:** All data persists in `localStorage` under key `scc3`
**Password:** Required for Internal section access

---

## 14 Tabs

| Tab | Purpose |
|-----|---------|
| **TOC** | Dual-pane Table of Contents editor with drag-reorder, version comparison, and Part/Chapter/Section hierarchy |
| **Writing** | Quill.js rich text editor with per-chapter storage, TOC sidebar navigation, and optional preview pane |
| **Decisions** | Decision log + bottleneck tracker with timestamps and priority levels |
| **Research** | A/B/C/D research card framework — Core Concept, Supporting Evidence, Application, Contradictions |
| **HTMLs** | HTML file collection with dual iframe previews for comparison |
| **Matrix** | Cytoscape.js directed graph — 95 movement nodes, 119 edges, filterable by stage/pattern/discipline/type |
| **Taxonomy** | Sortable/filterable table of all movement nodes with click-to-inspect detail panel |
| **Workout** | Drag-and-drop workout builder from exercise library |
| **Mind Map** | Freeform draggable node map with SVG connections |
| **Barcode** | QR code generator (kjua) with presets and custom URL support |
| **Vault** | Knowledge Vault — document library with categories, cross-referencing, and search |
| **Dashboard** | Overview dashboard — stats, writing progress, matrix coverage, decisions, bottlenecks |
| **Export** | Centralized export hub — JSON, MD, HTML, Word, PDF, CSV, Full State Backup, Export Bundle |
| **Internal** | Password-protected deployment forge — storage usage, locked structures, build info, state import/export |

---

## Tech Stack

| Library | Version | Purpose |
|---------|---------|---------|
| Quill.js | 1.3.6 | Rich text editing |
| Sortable.js | 1.15.0 | Drag-and-drop reordering |
| Cytoscape.js | 3.28.1 | Graph visualization |
| pdfmake | 0.2.7 | PDF generation |
| kjua | 0.9.0 | QR code generation |

All loaded via CDN. No build step required.

---

## Data Files

```
data/
  movement_matrix.json       — 95 nodes, 119 edges, enums, toc_anchors
  research.json              — 10 research cards with A/B/C/D blocks
  toc.json                   — v1 (7 Parts) and v2 (25 Chapters) structures
  htmls.json                 — HTML file references
  saturno_7_patterns_complete.csv          — 72 movements (source)
  saturno_movement_matrix_foundation.csv   — 10 mobility roots (source)
  saturno_cross_cutting_categories.csv     — 13 infrastructure nodes (source)
  saturno_notes_to_matrix_integration.csv  — 12 chapter-to-node mappings (source)
```

---

## Movement Matrix Schema

**Node Types:**
- `MOVEMENT` — 72 nodes across 7 patterns
- `MOBILITY` — 10 root nodes (Stage 0)
- `INFRASTRUCTURE` — 13 cross-cutting nodes (scapular + core)
- `TOC` — 12 chapter anchor nodes

**Stages:**
- Stage 0 — Mobility & Preparation (10 nodes)
- Stage 1 — Creating the Base (32 nodes)
- Stage 2 — Building the Structure (33 nodes)
- Stage 3 — Continuous Mastering (20 nodes)

**Edge Transfer Scale:**
- `high` — Direct prerequisite
- `medium` — Supporting skill
- `low` — Indirect benefit
- `direct` — Same-pattern progression

---

## Design Language: TITAN

```css
--bg-void:    #0a0a0c
--bg-deep:    #0f1014
--bg-surface: #151519
--accent-gold: #ffaa00
```

**Fonts:** Sora (display) + JetBrains Mono (code/labels)

---

## Project Structure

```
saturno-command-center/
  index.html          — Complete app (single file, ~2944 lines)
  BB_EDITS.md         — Bug fix changelog (TITAN stabilization pass)
  README.md           — This file
  package.json        — gh-pages deployment config
  data/               — JSON + CSV data files
  icons/              — SVG icons (dropbox, onedrive)
  htmls/              — HTML file collection
  node_modules/       — gh-pages dependency
```

---

## Deployment

```bash
# Local preview
open index.html

# Deploy to GitHub Pages
npx gh-pages -d .
```

---

## State Management

All app state lives in a single `S` object, serialized to `localStorage` under key `scc3`.

**State keys:**
- `tocs` — TOC versions (v1, v2, v3, custom)
- `research` — Research cards
- `decisions` — Decision log entries
- `bottlenecks` — Active bottlenecks
- `mindmap` — Nodes and edges
- `documents` — Per-chapter content
- `htmlFiles` — HTML file references
- `exercises` — Exercise library
- `matrixData` — Full movement graph
- `stageNames` — Editable stage names
- `vault` — Knowledge Vault documents
- `savedWorkouts` — Named workout saves
- `savedMindmaps` — Named mindmap saves
- `currentWritingMode` — Active writing mode
- `_versions` — Version history (last 10 snapshots)

**Backup:** Export > "Backup All" or header export button
**Reset:** Header reset button restores last saved state
**Import:** Internal > Import State (accepts JSON)

---

## TITAN Stabilization Pass (Jan 29, 2026)

18 mandatory fixes applied across 6 categories:

- **A. State & Data** — Confirmation dialogs, save failure alerts, reset-to-saved, clean compare exit
- **B. Export** — Reliable cross-browser downloads, Export Bundle (all-in-one)
- **C. TOC UX** — Double-click edit, visual hierarchy, full labels, global sync
- **D. Writing Hub** — Preview toggle, per-chapter storage, title-to-TOC sync
- **E. Matrix** — Node deletion with confirm, searchable node selector, focus-and-zoom
- **F. Taxonomy** — Stage name + number display, editable stage names, click-to-inspect panel

---

## Second Stabilization Pass (Jan 29, 2026 — Night Session)

9 improvements applied:

- **SS1. Codex Bug Fix** — Taxonomy overflow layout restructured, no-results message added
- **SS2. Exercises from Taxonomy** — 115+ exercises auto-loaded from matrixData, stage color-coded
- **SS3. Cloud Links** — Dropbox and OneDrive quick-access buttons in TOC sidebar
- **SS4. CSV Parser** — Rebuild matrix from 4 source CSVs (96 movements + 12 TOC anchors)
- **SS5. Add Edge UI** — Create relationships between nodes via modal (type + transfer scale)
- **SS6. Matrix CRUD** — Filter counts, search highlighting, Enter focus, Edit-in-Codex bridge
- **SS7. Research A/B/C/D** — Expandable cards, per-block copy with toast, usage tracking/filtering
- **SS8. Workout Builder** — Stage filter, drag-to-build with Sets/Reps/Rest, named save, CSV export
- **SS9. Mindmap** — Connect Mode (click 2 nodes), PNG export, named save/load, edge labels

See `BB_EDITS.md` for complete documentation.

---

## Third Stabilization Pass — Apsis Quality Polish (Jan 29, 2026 — Late Night)

24 improvements across 8 categories + 2 new tabs:

- **M. Writing Hub** — 8 color-coded writing modes (Raw/Teacher/Philosopher/Prophet/Mystic/Companion/Confessor/Rebel), 5 writing commands (Compress/Expand/Simplify/Deepen/Polish), live word count with targets
- **N. TOC** — Professional typography (Part 16px gold CAPS / Chapter 14px white / Section 12px italic), v3 working draft, movement link badges, analytics panel
- **O. Workout** — 6 pre-built templates, visual card display, workout analytics (sets/reps/duration/patterns), PDF export
- **P. Taxonomy** — Discipline color-coded pills, sortable columns, discipline filter dropdown
- **Q. Knowledge Vault** — NEW TAB: Document library with categories, viewer, cross-referencing against research/TOC/matrix, export
- **R. Persistent Memory** — Version history (last 10 snapshots), session recovery notification
- **S. Mindmap** — 5 shape palette (rectangle/circle/diamond/hexagon/pill), curved + bidirectional edges, SVG export
- **T. Dashboard** — NEW TAB: Overview with 6 stat cards, writing progress, matrix coverage, recent decisions, active bottlenecks

See `BB_EDITS.md` for complete documentation.

---

## Locked Structures

These are finalized and should not be modified:

- Mobility Big 7 — LOCKED V4
- Movement Patterns (7) — LOCKED V2
- Six Disciplines — LOCKED
- Three Stages — LOCKED
- TOC (7 Parts / 25 Chapters) — ACTIVE (still evolving)

---

*Built for Gabo Saturno | Saturno Movement*
*Victory Belt Publishing | The Art of Calisthenics*
