# Contributing to Vortex Docs

Thanks for helping make Vortex Documents better! This guide explains how to contribute documentation, report issues, and submit changes so your contribution gets reviewed and added.

## Contents

- [Hello and Intro](#hello-and-Intro)
- [How to contribute](#how-to-contribute)
  - [Report an issue](#report-an-issue)
  - [Propose a change (pull request)](#propose-a-change-pull-request)
- [Writing guidelines and style](#writing-guidelines-and-style)
- [File structure and assets](#file-structure-and-assets)
- [Commit messages and branch naming](#commit-messages-and-branch-naming)
- [Pull request checklist](#pull-request)
- [Review and merge process](#review-and-merge-process)

---

## Hello and Intro

Welcome! Thanks for taking the time to help improve Vortex Docs..

## How to contribute

There are two main ways to contribute:

1. Report an issue for a bug, missing doc, or suggestion.
2. Open a pull request (PR) with changes.

### Report an issue

- Create a new issue in this repository.
- Use a descriptive title and include in the context:
  - Screenshots, log snippets, or links
- Use labels or suggest them in the issue body if you think they apply (bug, docs, enhancement).
- You can also create an issue to request a new documentation page.

### Propose a change (pull request)

1. Fork the repo to your account.
2. Clone your fork:

   `git clone https://github.com/<your-username>/vortex-docs.git`

   `cd vortex-docs`

4. Create a branch for your work:

   `git checkout -b docs/<short-descriptive-name>`

5. Make your changes and commit them (see commit message guidelines below).
6. Push your branch to your fork and open a PR against `main` (or the repository default branch).
7. In the PR description, explain what you changed and why, and link any related issues.

For larger changes, open an issue first so we can discuss them.

## Writing guidelines and style

- Use clear, concise language aimed at users and contributors.
- Prefer active voice and consistent terminology.
- Use Markdown headings (H2/H3) to structure long pages.
- Include examples and commands in code blocks.
- Keep code blocks copy/paste-friendly (show full commands).
- When adding CLI examples, include the expected output where helpful.
- Avoid project-specific assumptions; where necessary, document environmental details (OS, versions).
- All paths must be relative.

## File structure and assets

- Keep docs in a top-level `docs/` directory or in the repo root per existing layout.
- Store images and binary assets in `docs/images/` or `assets/images/` and reference them with relative paths.
- Prefer SVG or PNG for diagrams and keep images optimized.
- Avoid committing large files (>10 MB); use external hosting or Git LFS if necessary.

## Commit messages and branch naming

- Branch names: `docs/<short-description>` or `fix/docs-typo-xyz`.
- Commit messages:
  - Start with a short summary: `docs: update installation section`
  - Optionally add a longer body describing why the change was needed.
  - Use present tense and be concise.

## Pull request

Before requesting review, ensure:

- The PR targets the repository's default branch (e.g., `main`).
- The PR description explains what, why, and any user-visible changes.
- Spelling and grammar have been checked.
- Links and images render correctly.
- Any necessary screenshots or examples are included.
- If the change affects a live site, the preview/build has been tested locally.
- Ensure all paths are relative.
- The PR relatively small and focused. (If change is large, consider splitting it into multiple PRs)
------------------------------------------------------------
Thanks for taking the time to contribute to Vortex Docs!
