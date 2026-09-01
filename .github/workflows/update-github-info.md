---
name: update-github-info
description: Update the site's GitHub information from Mona's notes and the latest GitHub announcements.
on:
  workflow_dispatch:
  schedule: daily
network:
  allowed:
    - github.blog
    - github.com
tools:
  edit:
  web-fetch:
safe-outputs:
  create-pull-request:
    title-prefix: "[mona] "
    draft: true
    fallback-as-issue: false
---

# Update GitHub Information

Read `notes/mona-notes.md` with GitHub repository API tools. Use the same GitHub
repository API tools for any other repository guidance or reference files; do
not use terminal, CLI, or sandboxed commands for those reads.

Fetch and review these public sources with `web-fetch`:

- https://github.blog/latest/
- https://github.blog/changelog/

Update `site/content/github-info.md` only when the notes and fetched sources
support an accurate, material improvement. When an update is warranted, use the
configured `create-pull-request` safe output to open a pull request for Mona to
review. Do not write directly to the default branch.

Use `noop` with a brief reason when the existing content is current or the
available sources do not provide enough reliable information for an update.
