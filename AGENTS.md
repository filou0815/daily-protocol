# Daily Protocol Agent Instructions

`AGENTS.md` is the canonical repository instruction source. Do not add a
`CLAUDE.md`, `CLAUDE.local.md`, or `.claude/CLAUDE.md` unless a concrete
compatibility requirement is documented; if one is required, keep only the
tool-specific delta and point back here.

## Purpose and structure

This repository is a small, local-first static Daily Protocol progressive web
app. It has no package manager, framework, build step, or automated test suite.

- `index.html` contains the protocol content, styling, markup, and application
  logic in one document.
- `manifest.json` contains installable-app metadata and icon references.
- `sw.js` contains the service-worker cache policy.
- `icon-192.png` and `icon-512.png` are app icons.
- `README.md` is currently only a repository identifier, not a detailed runbook.

## Change rules

- Edit the supplement routine, habits, safety notes, UI, and client-side behavior
  in `index.html`; there is no separate protocol-data file.
- Preserve the no-build, low-dependency architecture unless the request
  explicitly requires a larger stack.
- Avoid changing element IDs or the `localStorage` keys without a deliberate
  compatibility plan; they underpin daily completion state, habit history,
  low-stock flags, fasting state, and the ashwagandha cycle tracker.
- If the number of trackable supplement or habit items changes, update the
  progress calculation so percentages and completion states remain accurate.
- Keep `manifest.json`, icon paths, cache entries, and any service-worker
  registration consistent when PWA assets change.
- Preserve mobile safe-area handling and the narrow, touch-oriented layout.
- Treat protocol and safety text as user-authored health information. Do not
  silently alter doses, schedules, contraindications, or medical claims, and do
  not present repository content as medical advice.
- Do not commit personal credentials or unrelated sensitive data.

## Verification

Serve the repository over HTTP rather than relying on `file://` behavior:

```bash
python3 -m http.server 8000
```

Then inspect `http://localhost:8000/`. For every change, verify the browser
console is clean and the relevant behavior works. For UI or protocol changes,
also check:

- desktop and narrow/mobile layouts;
- supplement and habit completion plus reset/take-all controls;
- progress counts after any item additions or removals;
- state restoration from `localStorage` where affected;
- fasting, low-stock, and cycle-tracking behavior where affected;
- manifest, icon, and offline/cache behavior when PWA files change.

There is no compile or test command to run. Report browser checks actually
performed and do not imply that serving the files deployed them anywhere.

## Instruction maintenance

Keep only durable repository-wide constraints in this file. Put end-user usage
documentation in `README.md` if it is expanded, and keep implementation-specific
comments next to the relevant HTML, CSS, JavaScript, manifest, or service-worker
code.
