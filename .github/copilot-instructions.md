# Copilot Instructions for OMG Happy Birthday

## Build, Test, and Lint Commands

**CRITICAL:** This project supports multiple technology stacks. Always check `config.md` to determine the active stack before running commands.

### Astro (Default)
- **Dev Server:** `npm run dev`
- **Build:** `npm run build`
- **Preview:** `npm run preview`
- **Scaffold:** `npm create astro@latest`

### Next.js
- **Dev Server:** `npm run dev`
- **Build:** `npm run build`
- **Start:** `npm run start`
- **Scaffold:** `npx create-next-app@latest`

### Static HTML
- **Serve:** `npx serve .`

## High-Level Architecture

- **Configuration Separation:**
  - `config.md`: Defines the **infrastructure** (framework, styling, deployment).
  - `data.md`: Defines the **content** (celebrant name, language, theme, messages).
- **Fork-per-Friend Strategy:** The repository is designed to be forked for each new celebration. Each deployment is isolated.
- **Automated Generation:** GitHub Actions workflows trigger on changes to `data.md` to regenerate content and rebuild the site, allowing non-developers to update the site just by editing markdown.
- **Mobile-First Experience:** The end result is a mobile-optimized surprise page with animations and audio.

## Key Conventions

- **Stack Agnostic Logic:** When generating code or components, **always read `config.md` first**. Do not assume a specific framework unless verified in config.
- **Data-Driven Content:** Never hardcode text, colors, or media. All personalization (names, messages, themes) must be derived from `data.md`.
- **Localization:** The system supports single-language deployment. Ensure all generated text and accessible labels match the `language` field in `data.md`.
- **Animation & Audio:**
  - Animations should be CSS-first where possible for performance.
  - Audio (YouTube embed) must handle autoplay restrictions (e.g., require user interaction).
- **Workflow Awareness:** Development follows the phases in `plan.md`. Check this file to understand the current implementation status.
