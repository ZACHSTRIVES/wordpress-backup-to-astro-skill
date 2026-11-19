---
name: wordpress-backup-to-astro
license: MIT
description: Migrate a WordPress backup into a standalone static Astro website by extracting database content, page-builder structure, theme assets, and uploads. Use for backup-based WordPress migrations, including Elementor sites; excludes form migration and submission services.
---

# WordPress backup to Astro

Turn an authorized WordPress backup into a maintainable Astro site that builds without WordPress, PHP, a database, or access to the original site. Work from source evidence rather than recreating pages from screenshots alone. Preserve content, URLs, visual hierarchy, and relevant interactions unless the user requests a redesign.

## Scope and inputs

Locate the backup and destination project in the available workspace. Inspect existing project instructions and build commands before changing files. Ask for the backup location only when it cannot be found. Determine whether the user wants faithful reconstruction or redesign; default to faithful reconstruction.

Supported workflow inputs include a database dump plus uploads/theme files, ordinary ZIP/TAR backups, and plugin-specific archives when their format can be verified. A database-only backup may lack images and layout assets; a files-only backup may lack content. Explain those gaps instead of inventing replacements.

Forms are outside this skill. Do not migrate form definitions, submissions, delivery endpoints, CAPTCHA, email credentials, or submission backends. Record affected page regions as excluded; do not present an inactive submit control as a working feature. Preserve unrelated page content. Existing working form integrations are not authorization to modify them.

## Workflow

### 1. Recover source evidence

Read [backup-extraction.md](references/backup-extraction.md) before unpacking or parsing. Keep raw files and intermediate data in a private working directory outside the site's public assets and build output. Never execute backup PHP or import SQL into a shared database.

Produce a compact inventory: backup format, table prefix, source origin, front page, post types and statuses, taxonomy, page-builder usage, theme assets, uploads, and missing inputs. Keep counts and gaps in a private migration report; do not echo credentials or unrelated personal records.

### 2. Normalize the content

Read [content-and-media.md](references/content-and-media.md). Build a normalized content model with source IDs and provenance. Recover published pages, posts/custom post types, hierarchy, categories, navigation, shared sections, media, and SEO fields that are relevant to the requested site.

Create a route inventory before writing templates: original URL, destination URL, content type, inclusion decision, and any redirect. Account for the configured front page, nested paths, archive pagination, and custom post type rewrite rules. Do not infer every URL from a slug or use GUIDs as canonical URLs.

Reconcile source totals against normalized records and routes. Drafts, private/password-protected content, revisions, trash, admin users, submissions, and plugin logs are not public content by default. Document intentional exclusions without copying their contents into reports.

### 3. Rebuild in Astro

Adapt to the destination project's installed Astro version and conventions. For a new project, verify current official Astro setup requirements before choosing dependencies. Keep content separate from components, shared layout, and interaction code. JSON, content collections, or Markdown are acceptable according to the recovered structure; do not force complex builder pages into plain Markdown.

Use an explicit route map for static generation. Reject duplicate destinations and traversal paths. Rebuild shared header/footer and representative page families first, then populate detail pages and archives. Recover builder layout as semantic Astro components; keep useful source CSS selectively, and replace selectors coupled to unavailable plugin markup.

Restore navigation, mobile menus, filters, galleries, lightboxes, pagination, and sliders only where source evidence calls for them. Provide keyboard support, visible focus, sensible image alternatives, and reduced-motion behavior. Sanitize recovered rich HTML and remove executable source scripts, event handlers, tracking configuration, and plugin runtime dependencies before rendering it.

Use local media with an explicit mapping, intrinsic dimensions, responsive variants where useful, and original crop intent. Avoid selecting images by filename guess or filesystem order. Preserve contact text and document links only when supported by the source; report missing documents instead of fabricating them.

### 4. Review fonts, animation, and every page

Read the visual and interaction guidance in [verification.md](references/verification.md). Verify recovered font families, files, weights and styles against the source, and restore source-supported animations and transitions with reduced-motion behavior.

Review every included route from the route inventory at desktop and mobile sizes, not only representative page families. Compare with available source evidence, exercise each page's interactions, fix discrepancies, and revisit affected pages after shared component or style changes. Track each route's review status, fixes and unresolved gaps in the private migration report. If source evidence or browser tools are missing, mark affected checks as unverified and explain the limitation.

### 5. Remove unused resources, code, and backup files

Follow the cleanup guidance in [verification.md](references/verification.md). Remove confirmed unused media/fonts, components, styles, scripts and dependencies, along with redundant backup copies and temporary extraction artifacts from the destination project. Check imports, content data, CSS URLs, dynamic references and generated routes before deleting candidates; absence from a text search alone does not establish that a file is unused.

Keep the original source backup safely outside the deliverable; never delete its only copy. Retain files required to build, maintain or license the site. Record cleanup scope in the private migration report, then rebuild and recheck local references and affected pages to catch regressions.

### 6. Validate and deliver

Read [verification.md](references/verification.md). Run the actual project's build and appropriate checks. Reconcile routes, content counts, references, and exclusions; confirm the page-by-page desktop and mobile review is complete or explicitly marked unverified. Report what was verified and what remains blocked by missing source material or unavailable browser tools.

The deliverable must build independently from the backup and temporary extraction files. Keep reusable extraction logic private to the migration project when useful; never delete the only source backup as cleanup. Hand off editable content locations, build instructions, URL changes, known gaps, and the form exclusion. A migration request alone does not authorize production deployment, DNS changes, or publication of the source backup.
