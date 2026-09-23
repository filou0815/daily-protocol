# Daily Protocol Agent Instructions

> `AGENTS.md` is the canonical repository instruction source. Do not add `CLAUDE.md`, `CLAUDE.local.md`, or `.claude/CLAUDE.md` unless an explicit compatibility requirement is documented.

## Purpose

This repository is a deliberately simple local static Daily Protocol app.

- `daily.json` is the canonical source for protocol/routine content.
- `index.html` is the application shell and renderer.
- `README.md` contains the local serving/usage instructions.

## Change Rules

- When changing the actual daily protocol, edit `daily.json`; do not hard-code routine content into `index.html`.
- Change `index.html` only for application behavior, layout, rendering, interaction, or styling.
- Preserve the no-build, low-dependency static architecture unless the request explicitly requires a larger application stack.
- Do not introduce package managers, frameworks, servers, or build tooling merely for convenience.
- Keep the JSON valid and compatible with the renderer's current expectations.
- Avoid changing data keys/schema casually; if schema must change, update the renderer and existing data together.
- Do not silently remove protocol content or user-entered semantics while refactoring.

## Verification

Serve the repository over HTTP rather than opening `index.html` with `file://`:

```bash
python3 -m http.server 8000
```

Then verify the app from the local server (normally `http://localhost:8000`).

For UI changes, check at least:
- desktop layout;
- narrow/mobile layout;
- protocol sections render from `daily.json`;
- sliders/interactive blocks remain usable;
- overlays/panels do not clip or cover core controls.

For data-only changes, verify `daily.json` parses and the changed sections render correctly.

If the current environment cannot run the browser/server verification, say so explicitly.

## Repository Hygiene

- Keep personal secrets/credentials out of the repository.
- Prefer small, reversible changes.
- Preserve the static local-first behavior.
- Do not duplicate canonical protocol content across files.

## Instruction Maintenance

Use `AGENTS.md` for durable repository-wide operating rules only. Put user-facing setup/use instructions in `README.md`, protocol content in `daily.json`, and implementation behavior in `index.html`.