# Migration verification

## Source parity

- Compare published source records with normalized records and generated routes by content type. Explain excluded records and pagination/archive differences; a total HTML count alone does not prove parity.
- Check representative source text, special characters, ordering, taxonomy joins, parent relationships, featured images and gallery order. Verify builder-only pages are not empty.
- Check that no draft, private/password-protected content or excluded form data entered the public data files or output.

## Build and static output

Run the project's configured build. Check generated routes against the route inventory, including the front page, nested content, categories and pagination. Detect duplicate route paths before generation can overwrite output.

Resolve local references relative to the containing document's actual URL, using the host's directory/index conventions. Check HTML `href`, `src`, `srcset`, posters, CSS URLs, downloaded documents and redirect destinations. Test fragments against IDs on the destination page, not only the current page. Report intentional external links separately from missing local assets. Avoid broad regex checks that misparse data URLs or complex CSS.

Check canonical origins, sitemap inclusion, robots/noindex behavior, document titles and meaningful heading structure. Verify old source-domain media/plugin runtime references are gone except for intentional compatibility links. Inspect source and output for secrets, raw backup/SQL/PHP files, logs, private data and accidental source maps containing sensitive content. A file-extension scan alone is not a privacy check.

## Visual and interaction checks

Use the route inventory as the page-by-page review checklist. Inspect every included page and archive/pagination route, plus the 404, at desktop and narrow mobile viewports. Start with shared layouts and distinct page families, then review every remaining route for content-specific issues. Compare each page against source evidence. Check typography, image crops, spacing, navigation, overflow, stacking, touch controls and image loading. If the original site is unavailable, compare with recovered builder settings, source assets and supplied screenshots; disclose the resulting fidelity limit.

### Fonts

Recover font declarations from theme/builder CSS and settings, including local files, family names, weights, styles and icon fonts. Check font URLs resolve in the built site and verify the browser actually renders the intended face rather than silently falling back. Compare heading/body typography, line height, letter spacing and line wrapping on desktop and mobile. Fix incorrect mappings, missing weights/styles and fallback-induced layout shifts; record unavailable source fonts and any substitutions.

### Animation

Inventory source-supported entrance, scroll, hover and slider effects from builder settings and theme code. Check triggers, timing, easing and initial/final states. Ensure content remains visible when motion is reduced or animation scripts fail, and remove stale WordPress animation classes that leave elements hidden. Fix broken or missing effects without reintroducing plugin runtime dependencies.

### Review and fix loop

For each route, record desktop/mobile review status, discrepancies, fixes and unresolved source gaps in the private migration report. Fix issues as they are found, reload and recheck the page, and revisit affected routes after changes to shared styles or components. Complete the route checklist before handoff; distinguish verified pages from checks blocked by missing evidence or tools.

Exercise navigation, filters, galleries/lightboxes, sliders and pagination where present, including keyboard behavior and reduced motion. Forms remain excluded and must not appear to submit successfully. If browser tools are unavailable, record visual/interaction checks as unverified rather than replacing them with a build success claim.

## Cleanup before final validation

- Identify unused images, font files, documents, components, CSS, scripts and package dependencies using the route inventory, imports, normalized content, media mappings and build configuration. Account for dynamic imports, generated paths, CSS URLs, responsive image variants and runtime-loaded assets before removal. Do not delete a public document simply because it has no internal link if its URL must be preserved.
- Remove confirmed unused files and dead code. Update package manifests and lockfiles together when removing dependencies. Preserve required build tools, license notices and editable source files.
- Remove redundant backup archives, SQL dumps, extracted WordPress files, temporary exports and obsolete generated output from the destination project. Preserve the original source backup outside the deliverable; if its only copy is inside the project, relocate it safely and verify the copy before removing the project copy. Keep useful migration reports and reusable extraction tools private and outside public assets/build output.
- Run a clean build after cleanup, recheck generated routes and local asset/document references, and revisit pages and interactions affected by removed resources or shared code. Fix regressions before handoff. Record removed categories and any retained uncertain candidates in the private migration report.

## Handoff

Provide build and preview commands, editable content/component locations, route/redirect changes, checks performed, missing assets or unsupported source features, and the form exclusion. Confirm the build no longer requires extraction files, the original website or a live WordPress database. Hosting status/redirect checks may require an authorized preview or deployment; mark them pending if only a local build was checked.
