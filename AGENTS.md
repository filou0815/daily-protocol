# Daily Protocol Agent Instructions

`AGENTS.md` is the canonical persistent repository instruction file. Do not add `CLAUDE.md` or other client-specific copies of repository instructions.

## Repository purpose

This repository is a small static Progressive Web App called Daily Protocol. The current implementation is intentionally simple and self-contained:

- `index.html` — application markup, styling, and client-side behavior
- `manifest.json` — PWA metadata
- `sw.js` — service worker
- `icon-192.png` / `icon-512.png` — app icons
- `README.md` — minimal repository readme

Do not introduce a framework, package manager, build system, database, or backend merely to make a small change unless the request actually requires that architectural change.

## Validation

There is currently no `package.json`, automated test suite, lint script, or build command in this repository. Do not invent or claim such checks.

For changes:
- keep `index.html` valid and self-contained;
- verify referenced manifest, icon, and service-worker paths remain correct;
- keep `manifest.json` valid JSON;
- preserve service-worker registration/caching behavior when changing app assets;
- manually reason through the affected interaction/state path and, when browser execution is available, smoke-test the page/PWA behavior.

## Editing guardrails

- Prefer minimal, readable edits to the existing static implementation.
- Preserve mobile viewport and standalone/PWA behavior.
- Avoid adding remote dependencies unless they are genuinely needed and the privacy/offline trade-off is acceptable.
- Do not commit secrets or personal credentials.
- If changing persistent client-side state, preserve backward compatibility with existing stored data when practical.
- Keep UI changes usable on the current narrow/mobile layout.
- If a request expands the product materially enough to justify a framework or backend, treat that as an explicit architecture decision rather than an incidental refactor.

## Completion standard

Report exactly what changed and what was manually or automatically verified. Do not call a source edit deployed unless the live deployment was actually updated and checked.