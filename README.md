# WordPress Backup to Astro

A reusable Codex skill for turning WordPress backups into standalone static Astro websites. It covers database and builder-content recovery, local media, component reconstruction, routes, SEO, and migration verification.

Form migration and submission services are excluded. No customer content, backups, credentials, or proprietary theme assets are bundled.

## Install

Copy the `wordpress-backup-to-astro` folder into your Codex skills directory (normally `~/.codex/skills/`). The folder itself contains `SKILL.md`; do not install the entire repository as one skill.

## Use

> Use $wordpress-backup-to-astro to migrate the WordPress backup at [local backup path] into the Astro project at [local project path]. Preserve the existing design and URLs. Exclude forms.

Provide the backup and any screenshots or source-site access you want used for visual comparison. Database-only or files-only exports can leave gaps. Plugin-specific archive formats require a verified compatible extractor; this package does not bundle a universal backup decoder.

## Package contents

- `SKILL.md`: task selection, scope and migration workflow.
- `references/`: extraction, content/media recovery and verification guidance.
- `agents/openai.yaml`: skill display metadata and example prompt.

This repository packages the migration method, not the original site's implementation. Publication to a public repository or marketplace is a separate action. Licensed under the [MIT License](LICENSE).
