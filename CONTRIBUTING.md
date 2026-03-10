# Contributing Guidelines for Pure Astro

Thank you for your interest in contributing to **Pure Astro**! 🚀
This document provides guidelines for contributing to the development of this project, which serves as the engine and solid foundation for a personal website and blog dedicated to sharing technical articles, projects, and a complete portfolio.

## Table of Contents
- [Prerequisites](#prerequisites)
- [Project Setup](#project-setup)
- [Project Structure](#project-structure)
- [Code Conventions and Style](#code-conventions-and-style)
  - [Astro Components and Pages](#astro-components-and-pages)
  - [TypeScript](#typescript)
  - [CSS Styles](#css-styles)
  - [Content and Image Management](#content-and-image-management)
- [Pull Request Workflow](#pull-request-workflow)
- [What to Avoid](#what-to-avoid)

---

## Prerequisites

Before starting, make sure you have:
- **Node.js** (recommended version 18+ or 20+)
- **pnpm**: This is the official and default package manager for this project.

---

## Project Setup

To start working on the project locally:

1. **Fork** the repository and clone it to your machine:
   ```bash
   git clone https://github.com/YOUR-USERNAME/pure-astro.git
   cd pure-astro
   ```

2. Install dependencies using **pnpm**:
   ```bash
   pnpm install
   ```

3. Start the development server with live-preview:
   ```bash
   pnpm dev
   ```
   The local server will be accessible at `http://localhost:4321`.

### Other useful commands
- `pnpm build`: Creates the static production build in the `./dist/` folder.
- `pnpm preview`: Allows you to preview the local build generated with the build command.

---

## Project Structure

The project follows this file-system structure:

```text
/
├── public/           # Static assets (images, favicon, webp) — not processed by Astro
├── src/
│   ├── components/   # Reusable .astro components
│   ├── content/      # Content collections (blog posts in .md / .mdx)
│   ├── layouts/      # Shared Astro layouts
│   ├── pages/        # Pages and routes (file-based routing)
│   ├── styles/       # Global and component CSS
│   └── env.d.ts      # Astro type declarations
├── astro.config.mjs  # Astro configuration
├── tsconfig.json     # TypeScript configuration
└── package.json      # File for dependencies and Node scripts
```

---

## Code Conventions and Style

### Astro Components and Pages
- **Components**: Place new components in `src/components/` and layouts in `src/layouts/`.
- **Prop Types**: Use TypeScript in the frontmatter (the area between `---`). Always type the props received as input (`Astro.props`) via an interface (`interface Props`) or an explicit type.
- **Pages**: Create files inside `src/pages/` - routing is file-based. Always use a layout (typically the base one in `src/layouts/`) and pass properties like `title` and `description` to the layout to implement meta tags uniformly.
- **SEO/Meta-Tags**: Manage base tags, Open Graph, and Twitter Cards in the base layout, not individually on each page. Ensure the Open Graph image URL is absolute, using for example `new URL("/og-image.jpg", Astro.site)`.

Example of validating an `.astro` component:
```astro
---
interface Props {
  title: string;
  description?: string;
}
const { title, description } = Astro.props;
---

<div class="card">
  <h2>{title}</h2>
  {description && <p>{description}</p>}
</div>

<style>
  .card { /* scoped styles localized to the component */ }
</style>
```

### TypeScript
- The project uses TypeScript strictly as per the configuration present in `tsconfig.json`.
- Type functions, Props, and any iteration over data. Avoid using `any`: use `unknown` in edge cases where the type cannot be deduced upfront.

### CSS Styles
- The project relies on **Vanilla CSS** for custom logic (incorporating a base Bulma CSS file for the initial graphic architecture).
- Global styles reside entirely in `src/styles/`.
- Component-specific styles must reside inside a `<style>` tag within `.astro` files, remaining limited to that scope and encapsulating the style.
- Avoid using `!important` unless in rare and properly justified cases.

### Content and Image Management
- Blog posts must reside within the `src/content/` folder as Markdown (`.md`) or MDX (`.mdx`) files.
- Always respect the established schema defined in `src/content/config.ts` via `zod` validation. Any Content Collection frontmatter must include at least these base fields: `title`, `description`, and `pubDate`.
- **Images**: Place purely static images or those intended for pure metadata in `public/`. Strongly prefer the ultra-lightweight `.webp` format. For pictures to be included and processed in articles, allowing them to benefit from auto-optimization, use the `<Image />` component imported from `astro:assets` instead.

---

## Pull Request Workflow

To add formal changes to the project, strictly follow these instructions:

1. If possible, verify that there is no already open "Issue" for your intervention to avoid overlaps. Otherwise, open one yourself.
2. Create a dedicated **branch** for your change, starting from the updated reference branch (e.g., `main`):
   ```bash
   git checkout -b feature/my-new-feature
   # or
   git checkout -b fix/resolved-problem
   ```
3. Make commits with clear messages capable of correctly communicating the introduced changes to those reviewing them.
4. Push your progress to your forked repository:
   ```bash
   git push origin feature/my-new-feature
   ```
5. Open an explanatory **Pull Request** in this repository indicating which specific sections and cases the intervention covers.

---

## What to Avoid ❌

To keep the goals, SEO metrics, and high performance for which Pure Astro was born intact, we ask you to strictly adhere to the following prohibitions:

- **NO JS UI Frameworks**: Do not include UI frameworks and client-side libraries like React, Vue, or Svelte, unless you face an objectively unfeasible alternative in vanilla JS. This is a project in "pure" `.astro` format.
- **NO Tailwind CSS**: Do not introduce Tailwind or purely utility-first libraries of that kind; the project uses Vanilla CSS only.
- **NO Logic in Pages**: Do not place ad hoc business-logic blocks inside visible Pages (`src/pages/`); continuously extract, isolate, and reuse the algorithm in the form of a clean and reusable component.
- **NO Dynamic Management in Public**: Do not expect any visual optimization or graphic conversions on files introduced within `public/`, since files placed here bypass compilation and are copied directly into the final build as raw "assets" just as they are.
- **NO npm / yarn**: Do not alter or overwrite the native package manager by downloading modules with the base npm / yarn command: use only `pnpm`.

Thank you infinitely for your support and your valuable contribution to the repository! ❤️
