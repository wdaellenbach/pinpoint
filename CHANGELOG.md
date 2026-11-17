# Changelog

Newest first. Versions follow the line at the top of SPEC.md.

## 1.2 — 2026-11-17
- **Screenshots for AI tools** (§6.6, new): a table of how each kind of AI tool sees a note's screenshot (connector, browser,
  shell, database only, text-only fetch), and the rule that every screenshot is reachable at least one of those ways.
  Prompted by a "check the notes" run (Canadian Brass site) where the AI could read the notes from the database but
  couldn't see any screenshot: the full images were in the bucket, the admin route needed a session, and the feed
  secret sat in a KV store its tools couldn't read.
- **Inline preview** (§4.4, §5): each note also stores `shot_preview`, a ≤ 640 px JPEG data URL (≤ ~120 KB), next to the
  full screenshot in object storage. `.json?inline=1` carries it (§6.1).
- **Feed secret in the settings table** (§6.2): `PINPOINT_SECRET || settings.pinpoint_secret`, so a session with database
  access can derive the link with a small helper and open `/shot/<id>` without signing in. Copy an existing secret when
  moving it, so old links keep working.
- **Capture speed** (§4.4): only on-screen images are fetched, short per-resource timeout, ~10 s overall cap.
- **Scrolled pages** (§4.4): make the page copy tall enough before shifting it; paint the background behind it. Blank screenshots
  far down a page were the symptom. Acceptance test 17.
- Object storage for full screenshots is now core (was 🔜). Acceptance tests 14–16 added. Build: canadianbrass-web 836f2a2.

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
