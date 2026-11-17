# Pinpoint AI

**Pin feedback on any element of a site. An AI picks it up, fixes it, and marks it done.**

Signed-in people press ✦ (or ⌘J), click an element or drag over an area, and type a note. Each note is saved with the page,
the element's selector, label, text, position, the viewport and a screenshot. Later you tell your AI **"check the notes"**:
it reads every open note through a secret rotating link or an MCP connector, fixes them, and closes each one with a
one-line resolution.

- **[SPEC.md](SPEC.md)** — the full, reusable spec (widget, data model, feed link, MCP tools, the AI's workflow, security, acceptance tests).
- **[CHANGELOG.md](CHANGELOG.md)** — what changed between versions.
- **[LICENSE](LICENSE)**

## Status

| | |
|---|---|
| Spec version | 1.2 · 2026-11-17 |
| Markers in the spec | 🔜 planned extension (not core yet) |

## How to use this repo

- **Adding Pinpoint AI to a project:** follow SPEC.md §12 (build order), then put the §8 block in the project's `CLAUDE.md` / `AGENTS.md`.
- **Changing the spec:** edit `SPEC.md`, bump the version line at the top, and add an entry to `CHANGELOG.md`
  (what changed, why, and which build it reflects). One change per commit, so the history reads as a log of decisions.
- **When a planned extension becomes core:** remove its 🔜 marker in the same commit and note it in the changelog.
