# Copilot Instructions for OMG Happy Birthday

## Project Context
This is a static website generator for emergency birthday surprises. 
**Core Philosophy:** The project allows users to choose their preferred technology stack via `config.md` while keeping the content configuration in `data.md`.
**Current Status:** Early implementation phase. Follow `plan.md` for execution steps.

## High-Level Architecture
- **Configuration:** 
  - `config.md`: Determines the tech stack (Astro, Next.js, or vanilla HTML).
  - `data.md`: Determines the content (name, language, theme).
- **Automation:** GitHub Actions workflows use AI to generate content and build the site based on the selected stack.

## Build & Development
*Commands depend on the `stack` defined in `config.md`:*

### Astro (Default)
- **Scaffold:** `npm create astro@latest`
- **Dev:** `npm run dev`
- **Build:** `npm run build`

### Next.js
- **Scaffold:** `npx create-next-app@latest`
- **Dev:** `npm run dev`
- **Build:** `npm run build`

### Static HTML
- **Serve:** `npx serve .`

## Key Conventions
- **Stack Agnostic Logic:** When writing logic or components, check `config.md` first to determine the target framework.
- **Fork-per-Friend Strategy:** Each deployment is a separate fork.
- **Data-Driven Content:** All personalization must be derived from `data.md`.
- **Mobile-First:** Design primarily for mobile screens.
- **Localization:** The system must support single-language deployment based on `data.md`.

## Workflow
1. **Read `config.md`** to determine the technology stack.
2. **Read `data.md`** to understand the target persona and content requirements.
3. Follow `plan.md` to implement the specific stack's version of the site.
