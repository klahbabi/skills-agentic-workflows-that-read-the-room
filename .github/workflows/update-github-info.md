---
name: update-github-info

engine:
  id: copilot
  model: gpt-5

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
    - awesome-copilot.github.com

safe-outputs:
  create-pull-request:
    draft: true
    max: 1
---

# Update GitHub Info

Keep Mona's GitHub Info content current using official GitHub announcements and Awesome Copilot workflows.

## Instructions

1. Read `notes/mona-notes.md` and follow its editorial guidance.
2. Read `site/content/github-info.md` to understand the existing sections, entries, and sources.
3. Use web-fetch to read https://github.blog/latest/, https://github.blog/changelog/, and https://awesome-copilot.github.com/workflows/.
4. Identify recent announcements and useful Awesome Copilot workflows that fit the site's editorial angle. Verify details against the source pages, and do not add entries already covered in the content.
5. Use the edit tool to update `site/content/github-info.md`, keeping its existing structure and style. Keep summaries short and practical, include the publication date where available, and link each item to its original GitHub Blog, Changelog, or Awesome Copilot source. Include https://awesome-copilot.github.com/workflows/ among the site's sources.
6. If there are no meaningful new updates, make no changes and do not open a pull request.
7. When there are useful changes, request one draft pull request through the configured `create-pull-request` safe output. Explain the updates and cite their official sources so Mona can review them. Do not write directly to the default branch.