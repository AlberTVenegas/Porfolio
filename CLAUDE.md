# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

```bash
npm run dev       # Start dev server at localhost:4321
npm run build     # Build production site to ./dist/
npm run preview   # Preview production build locally
```

## Architecture

Single-page portfolio built with **Astro 5** and **Tailwind CSS 4**. All content is in Spanish.

**Rendering flow:**
- `src/pages/index.astro` → passes `title` prop to `src/layouts/Layout.astro`
- `Layout.astro` imports and renders all section components in order

**Section components** (in `src/components/`):
- `Header.astro` — fixed nav with anchor links (`#experiencia`, `#proyectos`, `#tecnologías`, `#sobremi`)
- `Resume.astro` — hero with profile image and `Icons.astro` (social links, email copy, CV download)
- `Experience.astro` + `ExperienceItem.astro` — timeline from inline `EXPERIENCE` array
- `Projects.astro` + `ProjectsItems.astro` — project showcase with inline project data
- `Skills.astro` — tech stack grid with inline SVG icons
- `SobreMi.astro` — biography section
- `Footer.astro` — footer

**Data:** All content (experience, projects, skills) is hardcoded in the components themselves — no external data sources or APIs.

**Assets:**
- `public/imgProjects/` — project screenshot images
- `public/img.webp` — profile photo
- `public/docs/` — CV document (linked from `Icons.astro`)
- `src/assets/` — SVG icons used in components

**Interactivity:** Minimal JS — only the email copy button in `Icons.astro` uses the Clipboard API.
