# Backup extraction

## Identify before decoding

Inspect file signatures, archive listings, size, and available disk space. Extensions alone do not prove a format. An ordinary archive can be listed with the installed ZIP/TAR tooling. Plugin-specific formats such as `.wpress` require a format-aware extractor: inspect its implementation and documentation for the actual backup variant before use. Do not rename it to ZIP or invent header offsets. If encrypted, incomplete, or unsupported, request a supported export or the missing password through an appropriate private channel.

Extract into a new private staging directory. Reject absolute paths, `..` traversal, symlinks/hardlinks escaping staging, and unreasonable expansion sizes. Check destination resolution for each member before writing. Do not run theme/plugin installers, PHP, or bundled executables. Do not extract into `public/` or commit the backup.

## Inspect the database

Discover tables from the dump rather than assuming `wp_`. For multisite, identify the intended blog before combining tables; do not mix sites. Inspect table definitions and INSERT column lists. Large SQL statements may span lines and contain escaped quotes, commas, semicolons, Unicode, binary literals, or explicit column order. Line splitting and regular expressions are not a general SQL parser.

Prefer a tested dump parser for the observed dialect. If it cannot handle the dump, use a disposable local database with no production connection, no external network access, no shared filesystem mounts containing secrets, least privilege, and an import process that rejects unrelated executable statements. Importing an untrusted dump is not safe merely because it is local. Never execute the dump as a shell script or run it against a production database.

Extract only needed tables/columns:

| Source | Relevant evidence |
| --- | --- |
| `*_posts` | Published pages/posts/custom types, parent IDs, attachments, dates, titles, excerpts, body, slugs |
| `*_postmeta` | Builder JSON, custom fields, attachment metadata, featured image IDs, SEO fields |
| `*_terms`, `*_term_taxonomy`, `*_term_relationships` | Categories, custom taxonomy, relationships, navigation membership |
| `*_options` (selected keys) | `home`, `siteurl`, `show_on_front`, `page_on_front`, `page_for_posts`, `permalink_structure`, theme/navigation configuration |

Do not export the entire options table as site data; it can contain credentials. Navigation item meta includes target object IDs/URLs, parent IDs and ordering. Menus and widget/shared layout options may be PHP serialized. Decode serialized values with a parser that preserves string byte lengths and does not instantiate PHP objects. Never use `eval` or execute PHP to deserialize arbitrary objects. Keep repeated meta keys as lists until their semantics are known.

## Evidence and failure handling

Record source files, table prefix, extraction tool/version, relevant record counts and parse failures privately. Reject silent truncation or decoding replacement that changes text. Resolve escaping at the SQL, serialization, JSON and HTML layers separately; do not apply global backslash removal or domain search-and-replace to raw SQL/serialized data.

If only a WordPress XML export exists, treat it as a reduced input: its attachment URLs may point to unavailable external files, and theme options/builder data may be incomplete. State the limitation and migrate what can actually be recovered.
