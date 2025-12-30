# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

| Command | Action |
|---------|--------|
| `npm run dev` | Start local dev server at `localhost:4321` |
| `npm run build` | Build production site to `./dist/` |
| `npm run preview` | Preview build locally |

## Architecture

This is an Astro-based static blog using TypeScript, Tailwind CSS, and Content Collections for blog posts.

### Content Collections

Blog posts are stored as Markdown files in `src/content/blog/` and managed through Astro Content Collections (`src/content/config.ts`). Each post requires frontmatter with:
- `title` - Post title
- `description` - Post description
- `pubDate` - Publication date (Date-coercible)
- `updatedDate` - Optional last updated date
- `heroImage` - Optional cover image path
- `tags` - Array of tags (defaults to empty array)

The collection name is `blog` (not `posts`). When using `getCollection('blog')`, remember that entries have a `slug` property used for routing.

### Routing

- Homepage: `src/pages/index.astro` - Lists all blog posts sorted by date (newest first)
- Blog posts: `src/pages/blog/[id].astro` - Dynamic route for individual posts, uses `BlogPost` layout

### Layouts

- `src/layouts/Layout.astro` - Base layout with header/footer, imports global styles
- `src/layouts/BlogPost.astro` - Blog post layout with `prose` class for Markdown styling

### Styling

- Tailwind CSS v3 with `@tailwindcss/typography` plugin
- Global styles in `src/styles/global.css`
- The `prose` class is used in BlogPost layout for Markdown content styling
- Build output format is `file` (not `directory`)

### Markdown

Code highlighting via Shiki with `github-dark` theme and line wrapping enabled.
