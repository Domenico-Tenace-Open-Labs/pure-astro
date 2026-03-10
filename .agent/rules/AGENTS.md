# AGENTS Instructions – pure-astro

## Project overview

Personal website and blog built with [Astro](https://astro.build/), based on the [Milky-Way](https://github.com/ttomczak3/Milky-Way) template. Used as a portfolio and space for technical articles.

- **Framework**: Astro (static site generator)
- **Languages**: `.astro`, TypeScript, vanilla CSS
- **Package manager**: `pnpm`
- **Deploy**: static output in `dist/`

---

## Project structure

```
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
├── tsconfig.json
└── package.json
```

---

## Code conventions and style

### Astro components

- Components go in `src/components/`, layouts in `src/layouts/`.
- The frontmatter (between `---`) is TypeScript: always type props with an interface or type.
- Use `Astro.props` to receive props in components and layouts.
- SEO and Open Graph meta tags should be managed in the base layout, not in individual pages.

### Content collections

- Blog posts live in `src/content/` as `.md` or `.mdx` files.
- Always define the collection schema in `src/content/config.ts` using `zod`.
- Post frontmatter must include at least: `title`, `description`, `pubDate`.

### CSS

- Vanilla CSS only — no utility frameworks like Tailwind.
- Global styles live in `src/styles/`.
- Component-scoped styles go directly in the `.astro` file inside a `<style>` block.
- Avoid `!important` except in exceptional cases.

### TypeScript

- Use TypeScript strictly — config is in `tsconfig.json`.
- Always type component props.
- Avoid `any`: use `unknown` when the type is not known.

---

## Available commands

```bash
pnpm dev          # Start local dev server at localhost:4321
pnpm build        # Production build to ./dist/
pnpm preview      # Preview the local build
```

---

## Patterns and practices

### New components

When creating a new component:

1. Place it in `src/components/`.
2. Define props with a TypeScript interface in the frontmatter.
3. Add scoped styles in the `<style>` block of the component itself.

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
  .card { /* scoped styles */ }
</style>
```

### New pages

- Create the file in `src/pages/` — routing is file-based.
- Always use a layout (typically the base one in `src/layouts/`).
- Pass `title` and `description` to the layout for SEO.

### New blog posts

- Create a `.md` or `.mdx` file in `src/content/`.
- Follow the schema defined in `src/content/config.ts`.

### Images

- Static images (og-image, favicon, etc.) go in `public/`.
- Prefer `.webp` format for images.
- For Astro-optimized images use the `<Image />` component from `astro:assets`.

### Meta tags and SEO

- Handle `<title>`, `<meta name="description">`, Open Graph, and Twitter Card in the base layout.
- The og:image URL must be absolute — use `new URL("/og-image.jpg", Astro.site)`.
- Make sure `site` is configured in `astro.config.mjs`.

---

## What to avoid

- Do not use UI frameworks like React, Vue, or Svelte unless strictly necessary: this project uses pure `.astro`.
- Do not add Tailwind CSS: the project uses vanilla CSS.
- Do not modify files in `public/` expecting them to be processed: they are copied as-is.
- Do not put business logic in pages: extract reusable components instead.
- Do not use `npm` or `yarn`: the package manager is `pnpm`.
