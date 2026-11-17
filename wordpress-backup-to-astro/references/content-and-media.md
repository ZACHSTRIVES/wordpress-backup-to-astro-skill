# Content, layout, and media recovery

## Normalize with provenance

A useful starting record is `{id, type, status, slug, parentId, route, title, date, modified, excerpt, body, sections, taxonomy, featuredMediaId, seo, source}`. Adapt it to the site. Preserve original IDs as joins; do not use array positions as identifiers. Keep raw source and private extraction artifacts separate from publishable data.

Resolve the route inventory using the permalink setting, hierarchical parents, front page selection, post-type registration/rewrite evidence from theme/plugin source, menu links, and available sitemaps. Reading source code is useful; executing it is unnecessary. Map old internal links to verified target routes. Preserve external links and distinguish media URLs, query strings, fragments, and protocol-relative URLs. Decode/encode Unicode and spaces deliberately, and check filename case on case-sensitive hosting.

## Elementor and other builder data

When `_elementor_data` is present, decode the JSON and traverse containers/sections, columns, widgets and nested children in their stored order. Recover settings that affect content and layout: headings, rich text, buttons, image IDs/URLs, galleries, background images/overlays, spacing, widths, alignment, breakpoints, visibility and responsive overrides. Inspect global kit/template references for typography, colors, shared header/footer and popups relevant to static content.

Do not rely solely on `post_content`: a builder page may store most useful content in metadata. Conversely, do not assume every page uses Elementor. For Gutenberg/classic content, parse blocks or rich HTML and resolve shortcodes through the plugin/theme evidence. A shortcode string is not the rendered content. List unsupported widgets/shortcodes and implement the visible behavior when it can be established; do not claim a complete reconstruction after silently dropping them.

Custom fields, repeaters and custom post types may hold project galleries, specifications, teams, and testimonials. Resolve their relationships before choosing a component model. Identify form widgets and exclude them from extraction/rendering while retaining adjacent content.

## Media mapping

Build an index from attachment IDs, `_wp_attached_file`, decoded `_wp_attachment_metadata`, upload paths and actual files. A GUID is a historical identifier and may contain a stale domain; it is not proof of the current public URL.

Map each referenced source URL/path to a real local asset. Normalize the known source host and upload prefix without merging unrelated hosts or paths. Account for WordPress generated sizes, WebP copies, Elementor thumbnail directories, background images, CSS `url()`, `srcset`, posters, inline styles, and document downloads. Preserve a source-to-destination map and role-specific choices where different crops serve different components.

Use verified dimensions and visual inspection to choose the original or appropriate derivative. Never synthesize a file path by removing a `-300x200` suffix and assuming the original exists. Preserve SVG/font assets only when needed and safe for their use; verify font licensing before redistribution. Keep alt text from attachment/page context; use empty alternatives for decorative images.

Copy referenced assets, preserving needed relative CSS references or rewriting them through the map. Optimize after the mapping works, keeping aspect ratio, crop and acceptable quality. Include assets reached through CSS, client interactions, manifests, metadata/social cards, favicons and legacy redirects before deciding an upload is unused.

Do not copy entire uploads/plugin directories into public output. Raw backups, SQL, PHP, logs, configuration and private attachment/submission files do not belong there. Asset pruning must be based on a complete reference graph and must not delete the user's originals.

## SEO and historical URLs

Recover titles, descriptions, canonical intent, index/noindex, social images and breadcrumbs when evidenced by SEO metadata. Generate an XML sitemap for indexable canonical routes. Match trailing-slash behavior consistently. Preserve URLs where possible; map changed paths with hosting-compatible redirects and verify each target. Retain historic media URLs when needed by known backlinks or the requested compatibility scope. Do not redirect every unknown URL to the home page.

Create a real 404 page and verify the host returns status 404 for missing nested paths. Missing legal/policy documents remain explicit gaps; do not invent policy text or substitute unrelated PDFs.
