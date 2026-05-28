# Text to Visual Comparison

> **Transform any text into beautiful visual diagrams.** Paste a description, a comparison, a process, or an idea — and watch it render as an interactive visual layout in seconds. No design skills required.

[![Stack](https://img.shields.io/badge/Stack-Next.js%2015%20%2F%20React%2018%20%2F%20TypeScript-3178C6?style=flat-square)]()
[![Styling](https://img.shields.io/badge/Styling-Tailwind%20CSS-38B2AC?style=flat-square)]()
[![Status](https://img.shields.io/badge/Status-In%20Development-orange?style=flat-square)]()
[![License](https://img.shields.io/badge/License-Private-lightgrey?style=flat-square)]()

---

## Table of Contents

- [What It Does](#what-it-does)
- [Visual Layout Types](#visual-layout-types)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Getting Started](#getting-started)
- [Keyboard Shortcuts](#keyboard-shortcuts)
- [Planned Features](#planned-features)
- [Documentation](#documentation)
- [Project Status](#project-status)
- [Roadmap to Finish Line](#roadmap-to-finish-line)

---

## What It Does

Text to Visual Comparison takes natural language input and converts it into one of several visual diagram types. The user types or pastes text describing a concept, comparison, process, or relationship — and the app renders a clean, interactive visual.

Core goals:
- Generate multiple visual options within 10–30 seconds
- Visuals are fully customizable after generation
- Export to PNG, SVG, and PDF
- Light/dark mode with dynamic theming
- No design skills needed — text in, diagram out

---

## Visual Layout Types

Six layout components are built in `src/components/features/visualization/layouts/`:

| Layout | File | Best For |
|---|---|---|
| **Balance** | `balance-layout.tsx` | Side-by-side comparisons, pros/cons, A vs B |
| **Circular** | `circular-layout.tsx` | Cycles, feedback loops, recurring processes |
| **Fan** | `fan-layout.tsx` | One-to-many relationships, branching from a center |
| **Flower** | `flower-layout.tsx` | Categories radiating from a central concept |
| **Orbital** | `orbital-layout.tsx` | Core concept with surrounding related ideas |
| **Process** | `process-layout.tsx` | Step-by-step workflows, timelines, procedures |

The `layout-selector.tsx` component lets users switch between layouts after generation. The `style-options.tsx` component controls colors, fonts, and visual theming.

---

## Tech Stack

| Layer | Tool | Version |
|---|---|---|
| **Framework** | Next.js | ^15.0.3 |
| **UI Library** | React | ^18.3.1 |
| **Language** | TypeScript | ~5.3.3 |
| **Styling** | Tailwind CSS | ^3.4.15 |
| **Build Tool** | Turbopack (Next.js) | Built-in |
| **Linting** | ESLint + TypeScript ESLint | ^8 / ^6 |
| **Formatting** | Prettier | Configured |
| **Package Manager** | npm | — |

> The `turbopack-app/` directory contains a separate Turbopack-optimized build experiment.

---

## Project Structure

```
text-to-visual-comparison/
│
├── 📁 src/
│   ├── 📁 app/                              # Next.js App Router
│   │   ├── page.tsx                         # ← Main application page (4.4KB — core UI)
│   │   ├── layout.tsx                       # Root layout + metadata
│   │   ├── globals.css                      # Global styles
│   │   ├── error.tsx                        # Error boundary
│   │   ├── global-error.tsx                 # Global error handler
│   │   ├── not-found.tsx                    # 404 page
│   │   └── test/                            # Test routes
│   │
│   ├── 📁 components/
│   │   ├── 📁 features/
│   │   │   ├── 📁 text-input/
│   │   │   │   └── text-input-section.tsx   # Text input panel
│   │   │   └── 📁 visualization/
│   │   │       ├── comparison-visualization.tsx  # Main visualization renderer
│   │   │       ├── layout-selector.tsx           # Layout switcher UI
│   │   │       ├── style-options.tsx             # Color/theme controls
│   │   │       └── 📁 layouts/
│   │   │           ├── balance-layout.tsx         # A vs B comparison
│   │   │           ├── circular-layout.tsx        # Cycle/loop diagrams
│   │   │           ├── fan-layout.tsx             # Fan/branch diagrams
│   │   │           ├── flower-layout.tsx          # Radial category diagram
│   │   │           ├── orbital-layout.tsx         # Core + orbiting concepts
│   │   │           ├── process-layout.tsx         # Step-by-step flow
│   │   │           └── index.ts                   # Layout exports
│   │   └── 📁 ui/
│   │       └── text-area.tsx                # Reusable textarea component
│   │
│   ├── 📁 lib/
│   │   ├── shortcuts.ts                     # Keyboard shortcut definitions
│   │   ├── storage.ts                       # Local storage utilities
│   │   ├── styles.ts                        # Style/theme utilities
│   │   ├── types.ts                         # Core type definitions
│   │   ├── utils.ts                         # General utility functions
│   │   └── 📁 hooks/
│   │       └── useKeyboardShortcuts.ts      # Keyboard shortcut hook
│   │
│   └── 📁 types/                            # Global TypeScript types
│
├── 📁 src/backups/001/                      # Working state backup
│
├── 📁 docs/                                 # Full project documentation
│   ├── project-status.md                    # Current build status
│   ├── requirements-coverage.md             # Feature coverage checklist
│   ├── api/                                 # API documentation
│   ├── architecture/                        # System architecture docs
│   ├── database/                            # DB schema docs
│   ├── deployment/                          # Deployment guides
│   ├── design/                              # Wireframes + UX docs
│   ├── development/                         # Dev guidelines
│   ├── infrastructure/                      # Infra + scaling
│   ├── monitoring/                          # Performance monitoring
│   ├── requirements/                        # BRD, PRD, User Stories
│   ├── security/                            # Security architecture
│   ├── testing/                             # Testing strategy
│   └── user/                               # User manual
│
├── 📁 prompts/                              # AI generation prompts
├── 📁 scripts/                              # Dev utilities + backup scripts
├── 📁 turbopack-app/                        # Turbopack build experiment
│
├── 📄 App_Markdown.MD                       # Original requirements spec
├── 📄 Instructions.md                       # Development instructions
├── 📄 CHANGELOG.md                          # Version history
├── 📄 CONTRIBUTING.md                       # Contribution guidelines
├── 📄 CODE_OF_CONDUCT.md                    # Code of conduct
│
├── 📄 package.json                          # Dependencies + scripts
├── 📄 tsconfig.json                         # TypeScript config
├── 📄 .eslintrc.js / .eslintrc.json         # ESLint config
├── 📄 .prettierrc                           # Prettier config
└── 📄 .gitignore                            # Git ignore rules
```

---

## Getting Started

### Prerequisites

- Node.js 18+
- npm

### Install & run

```bash
# Clone
git clone https://github.com/jhcrypt/Test-App.git
cd Test-App

# Install dependencies
npm install

# Start dev server (Turbopack)
npm run dev
```

Open [http://localhost:3000](http://localhost:3000).

### Other commands

```bash
# Production build
npm run build

# Start production server
npm start

# Lint
npm run lint
```

---

## Keyboard Shortcuts

Shortcuts are defined in `src/lib/shortcuts.ts` and wired via `useKeyboardShortcuts.ts`:

| Shortcut | Action |
|---|---|
| `Ctrl/Cmd + Enter` | Generate visualization from current text |
| `Ctrl/Cmd + Z` | Undo last change |
| `Ctrl/Cmd + S` | Save current state |
| `Ctrl/Cmd + E` | Export current visualization |
| `Ctrl/Cmd + 1–6` | Switch layout (Balance, Circular, Fan, Flower, Orbital, Process) |

> See `src/lib/shortcuts.ts` for the full shortcut map.

---

## Planned Features

From the original requirements spec (`App_Markdown.MD`):

### Core (MVP)
- [x] Text input interface
- [x] 6 visual layout types built
- [x] Layout selector
- [x] Style options (color/theme)
- [x] Keyboard shortcuts
- [ ] AI-powered text parsing (NLP → visual data structure)
- [ ] Export to PNG / SVG / PDF
- [ ] Drag-and-drop visual editor
- [ ] Template library

### Backend
- [ ] AI processing API (text → diagram data)
- [ ] PostgreSQL — user and project persistence
- [ ] User authentication
- [ ] Project save/load
- [ ] Microservices: text analysis, image generation, style transfer

### Enhanced
- [ ] Real-time collaboration
- [ ] Version history per diagram
- [ ] Dark/light mode toggle
- [ ] Mobile responsive layout
- [ ] Share via URL

---

## Documentation

The `/docs` directory contains a full project documentation suite:

| Doc | Location | Description |
|---|---|---|
| Business Requirements | `docs/requirements/` | BRD — business goals, stakeholders, success criteria |
| Product Requirements | `docs/requirements/` | PRD — feature specs, performance targets |
| User Stories | `docs/requirements/` | MVP + enhancement + collaboration phases |
| Technical Architecture | `docs/architecture/` | System design, component map, data flow |
| Wireframes | `docs/design/` | Core UI layouts, responsive states, interaction flows |
| API Docs | `docs/api/` | Visualization endpoints, export endpoints |
| Security | `docs/security/` | Auth architecture, data protection |
| Testing Strategy | `docs/testing/` | Unit, integration, and E2E test plans |
| Deployment | `docs/deployment/` | Hosting, CI/CD, environment setup |
| User Manual | `docs/user/` | End-user guide |
| Project Status | `docs/project-status.md` | Current build status |
| Requirements Coverage | `docs/requirements-coverage.md` | Feature-by-feature coverage checklist |

---

## Project Status

**Current state:** Frontend scaffolding and all 6 layout components are built. The UI structure, keyboard shortcuts, style system, and local storage utilities are in place. The core text-to-visual parsing logic and backend have not been implemented yet.

### What's done ✅
- Next.js 15 + TypeScript project configured
- All 6 visualization layout components built
- Layout selector + style options UI
- Text input section
- Keyboard shortcut system
- Local storage utilities
- Full documentation suite (BRD, PRD, architecture, wireframes, user stories)

### What's next 🔲
- Connect text input → AI parsing → layout data
- Implement export (PNG/SVG/PDF)
- Add drag-and-drop editor
- Build template library
- Backend API + database
- User auth + project persistence

---

## Roadmap to Finish Line

The architecture and all 6 visual layouts are built. The missing piece is wiring the text input to an actual parsing layer. The fastest path to a working demo:

**Step 1 — Wire a simple parser (1–2 days)**
Use a prompt-based approach: send the user's text to Claude or GPT-4 with instructions to return structured JSON (title, items, layout type). Feed that JSON into the existing layout components. No custom NLP needed.

**Step 2 — Add export (1 day)**
Use `html2canvas` + `jsPDF` to export whatever is rendered. Both are drop-in npm packages.

**Step 3 — Deploy (half a day)**
Deploy to Vercel — it's a Next.js app, one command: `vercel --prod`.

**Step 4 — Template library (2–3 days)**
Pre-built JSON objects for common comparison types (pros/cons, before/after, steps 1–5) that users can select and customize.

The foundation is solid. Getting to a working demo is a 4–5 day sprint.

---

<div align="center">
  <strong>Text to Visual Comparison · Turn words into diagrams · Built with Next.js + TypeScript</strong>
</div>
