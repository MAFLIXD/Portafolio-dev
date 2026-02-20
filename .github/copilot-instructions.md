# AI Coding Guidelines for Portafolio-dev

## Project Overview
This is an **Astro-based personal portfolio website** showcasing Santiago Mafla's development skills and projects. Built with static site generation (Astro v5.9), styled with Tailwind CSS v4, and deployed as a dark-themed SPA.

## Architecture & Key Patterns

### Component Structure
- **Layout Components** ([`src/layouts/Layout.astro`](src/layouts/Layout.astro)): Root template with global styles, font loading (Onest), and decorative radial gradient backgrounds
- **Page Components** ([`src/pages/index.astro`](src/pages/index.astro)): Main landing page importing multiple feature sections
- **Reusable Components** ([`src/components/`](src/components/)): 
  - Section wrappers: `SectionContainer`, `Badge`, `SocialPill`, `LinkButton`
  - Feature sections: `Header` (navigation), `Projects`, `Footer`
  - Icon components: Custom `.astro` files in [`src/components/icons/`](src/components/icons/) (Java, Spring, GitHub, LinkedIn, etc.)

### Data Patterns
- **Projects** are defined as JavaScript objects in component scripts with metadata (title, description, tags, image, links)
- **Tags system** maps tech stacks to display configurations (name, class for styling, icon component)
- No database/API calls; all content is static and frontmatter-driven

### Styling Architecture
- **Tailwind CSS v4** with custom extensions in [`tailwind.config.mjs`](tailwind.config.mjs)
- **Dark mode enabled by default** (`darkMode: 'class'` with `<html class="dark">`)
- **Custom animations**: `background-shine` for badge gradient effects (defined in [`global.css`](src/styles/global.css))
- **Global utility class**: `.badge-shine` for animated gradient backgrounds
- **Inline event handlers** in Header navigation (onmouseover/onmouseout for text-shadow effects)

## Developer Workflows

### Building & Running
```bash
npm run dev      # Start Astro dev server (live reload)
npm run build    # Generate static production site to /dist
npm run preview  # Preview production build locally
npm run astro    # Direct astro CLI access
```

### Key Development Conventions
1. **Astro component syntax**: Use frontmatter (---) for component logic, template below
2. **Imports pattern**: Always import components from relative paths (e.g., `../components/`)
3. **Styling**: Prefer Tailwind utility classes; custom CSS only in `global.css`
4. **Icon components**: Create new icons as separate `.astro` files in `icons/` folder following existing naming
5. **Section organization**: Use `SectionContainer` wrapper for consistent spacing and max-width (each section has `id` for navigation)

## Project-Specific Patterns

### Component Composition Example
From [`Projects.astro`](src/components/Projects.astro):
```javascript
const TAGS = { JAVA: { name: "Java", class: "bg-black text-white", icon: Java } }
const PROJECTS = [{ title: "...", tags: [TAGS.JAVA], ... }]
```
This pattern allows reusable tag definitions mapped to visual styles and icon components.

### Navigation Structure
Header links use fragment anchors (`#sobre-mi`, `#proyectos`) pointing to section `id` attributes. All nav items have inline transition effects for hover states.

### Portfolio Content Areas
- **Hero section**: Profile image, greeting, availability badge, social links
- **About me**: Technical description, specializations, languages/tools
- **Projects**: Mapped grid of project cards with images, descriptions, tech tags
- **Courses/Certifications**: Additional sections with similar structure
- **Contact**: Footer with social/contact information

## Critical Files to Know
| File | Purpose |
|------|---------|
| [`src/pages/index.astro`](src/pages/index.astro) | Main portfolio page (228 lines) |
| [`src/layouts/Layout.astro`](src/layouts/Layout.astro) | Global layout with dark mode styling |
| [`src/components/Projects.astro`](src/components/Projects.astro) | Project grid with tag system (95 lines) |
| [`tailwind.config.mjs`](tailwind.config.mjs) | Tailwind extensions and animation definitions |
| [`src/styles/global.css`](src/styles/global.css) | Custom gradient animations and utilities |

## Technology Stack
- **Runtime**: Astro 5.9 (static site generation)
- **Styling**: Tailwind CSS 4.1.8 + @tailwindcss/vite plugin
- **Fonts**: @fontsource-variable/onest (Google Fonts variable font)
- **TypeScript**: Strict mode enabled (`astro/tsconfigs/strict`)
- **Build**: Vite (via Astro)

## Content Localization
The site is written in **Spanish** (title, headings, navigation). When adding content, match language conventions and cultural context.

---
*Last updated: 2026-02-20*
