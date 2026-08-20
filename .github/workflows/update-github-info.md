---
name: update-github-info
description: Keep Mona's GitHub Info content current with practical updates from official GitHub sources.
on:
  schedule: daily
  workflow_dispatch:
permissions:
  contents: read
  metadata: read
tools:
  github:
    toolsets: [repos]
  web-fetch:
  edit:
network:
  allowed:
    - defaults
    - github.blog
    - github.com
safe-outputs:
  create-pull-request:
    title-prefix: "[mona] "
    draft: false
    max: 1
---

You maintain the content for Mona's GitHub Info website.

1. Use the GitHub repository tools to read `notes/mona-notes.md` and the current `site/content/github-info.md`. Use repository API tools for these reads; do not use terminal, CLI, bash, or sandboxed commands to read repository guidance or reference files.
2. Use `web-fetch` to read https://github.blog/latest/.
3. Use `web-fetch` to read https://github.blog/changelog/.
4. Following Mona's notes, identify useful, current updates that help developers learn GitHub faster. Keep summaries short and practical, and mention whether each update came from the GitHub Blog or GitHub Changelog with its source URL.
5. Edit `site/content/github-info.md` with the curated updates. Preserve the file's existing structure and avoid unrelated changes.
6. Request the `create-pull-request` safe output with a concise title and body summarizing the updates and linking to every source. The pull request must propose the changes for Mona to review and must not write directly to the `main` branch.

If neither source has a useful update, leave the content unchanged and do not request a pull request.
