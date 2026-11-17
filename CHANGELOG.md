# Changelog

Newest first. Versions follow the line at the top of SPEC.md.

## 1.1 — 2026-11-17
- Spec made project-neutral: example data on example.com, reference table `pinpoint_notes`, generic CSRF header.
- Renamed from "Notes for Claude" to **Pinpoint AI**; vendor-neutral wording ("the AI").
- **Secret feed link** (§6): `/pinpoint/<token>` (Markdown), `.json`, `/shot/<id>`; HMAC token rotating every 30 days with
  3 days of grace; **New link now**; editable rules at the top of the feed; uniform 404s.
- **MCP** (§7): `resolve_notes` added next to `list_notes` and `get_note`.
- **Statuses** (§5): `done` and `wontfix`, with `resolution`, `done_by` and `commit_sha`; Reopen clears them.
- **Who can leave notes** (§3): superadmins, admins and editors; each note keeps its author's account and role;
  only superadmins see everyone's notes, the feed and MCP.
- **Phones** (§4.4, §4.5): note box and notes panel pinned to the **top** of the screen so the keyboard never covers them;
  16 px fields (no iOS zoom); full-width Send. Acceptance test 13 added.
- **Capture state** (§4.4): shimmer + spinner while the screenshot is made; sending early waits for it.

## 1.0 — 2026-11-14
- "Notes for Claude" in an admin and its site: ✦ button / ⌘J picker, element / area / whole-page targets, ↑/↓ to widen,
  screenshot per note, notes panel, Administration › Notes for Claude, MCP `list_notes` / `get_note` (superadmins only).
