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

Compare source evidence with the built home page, one ordinary page, one detail page, an archive and the 404, plus any distinct page family. Use desktop and narrow mobile viewports. Check typography, image crops, spacing, navigation, overflow, stacking, touch controls and image loading. If the original site is unavailable, compare with recovered builder settings, source assets and supplied screenshots; disclose the resulting fidelity limit.

Exercise navigation, filters, galleries/lightboxes, sliders and pagination where present, including keyboard behavior and reduced motion. Forms remain excluded and must not appear to submit successfully. If browser tools are unavailable, record visual/interaction checks as unverified rather than replacing them with a build success claim.

## Handoff

Provide build and preview commands, editable content/component locations, route/redirect changes, checks performed, missing assets or unsupported source features, and the form exclusion. Confirm the build no longer requires extraction files, the original website or a live WordPress database. Hosting status/redirect checks may require an authorized preview or deployment; mark them pending if only a local build was checked.
