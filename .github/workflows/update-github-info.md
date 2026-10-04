---
name: update-github-info
on:
  schedule: daily
  workflow_dispatch:

permissions:
  contents: read
  pull-requests: read

tools:
  edit:
  web-fetch:

network:
  allowed:
    - github.blog
    - github.com

safe-outputs:
  create-pull-request:
    draft: true
    max: 1
---

# Update GitHub Info

Keep Mona's GitHub Info content current using official GitHub announcements.

## Instructions

1. Read `notes/mona-notes.md` and follow its editorial guidance.
2. Read `site/content/github-info.md` to understand the existing sections, entries, and sources.
3. Use web-fetch to read https://github.blog/latest/ and https://github.blog/changelog/.
4. Identify recent announcements that are useful to developers and relevant to the site's editorial angle. Verify dates and details against the official pages, and do not add entries already covered in the content.
5. Use the edit tool to update `site/content/github-info.md`, keeping its existing structure and style. Keep summaries short and practical, include the publication date, and link each update to its original GitHub Blog or Changelog source.
6. If there are no meaningful new updates, make no changes and do not open a pull request.
7. When there are useful changes, request one draft pull request through the configured `create-pull-request` safe output. Explain the updates and cite their official sources so Mona can review them. Do not write directly to the default branch.