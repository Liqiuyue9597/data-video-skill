# data-explainer-video

A Claude Code skill for turning articles into Tatakye-style data-explainer videos (3-6 min) as self-contained HTML pages.

**Aesthetic**: minimal black-gold, animated curves, big-number reveals, particle fields, sparse ambient audio, subtitle-driven narration. Think 3Blue1Brown / Veritasium / Tatakye (小红书).

**Output**: one HTML file. User plays it fullscreen in Chrome, screen-records with QuickTime/OBS.

**Zero deps**: Canvas 2D + Web Audio API only. No fonts to buy, no stock footage, no server.

## Files

- `SKILL.md` — the skill. Load this via Claude Code's skill system.
- `template_v2.html` — **current reference implementation.** Spine-based: persistent top-right equation anchor, 3-item answer payoff, live SPEED slider, 3 total scenes evolving across the piece. **Use this as default.**
- `template_v1.html` — older implementation. Multi-scene without spine. Kept for comparison / to see what NOT to do.

## Install

Copy this folder into your Claude Code skills directory:

```bash
# system-wide
cp -r data-video-skill ~/.claude/skills/

# or project-local
mkdir -p .claude/skills && cp -r data-video-skill .claude/skills/
```

Then invoke in Claude Code with the skill name `data-explainer-video`.

## Hard-won lessons baked in

**Big wins (most explainer videos miss these)**:
- **Add a spine** — one persistent on-screen anchor (an equation / diagram / sequence) that stays visible for most of the video. Each beat lights up a different component. This is the #1 difference between "a video that teaches" and "a video that looks pretty."
- **Payoff, not rhetoric** — end on a named 2-4 item list the viewer can repeat the next day, not "are you them?"
- **Scene economy** — 3-5 scenes total, each 60-90s minimum. One visual evolves 2-3 minutes, not seven unrelated visuals.
- **Chapter labels = words from the spine**, not "ACT I/II/III."

**Craft details**:
- Theme in one sentence before writing anything (otherwise rewrite is coming)
- One claim, few chained beats — pick the structure that fits the claim, don't force a template
- Chinese OR English per label — never both duplicated
- No italics on Chinese text (CJK italics look bad)
- Chime audio events ≠ subtitle count (10x less dense)
- 160Hz high-pass on master to kill sub-bass discomfort
- `#0a0a0f` not `#000000`
- All big numbers count-up animate
- Scene changes always use blackout-blink, never hard-cut
- X-axis labels use narrative anchors ("现在", "未来") not past-years
- **SPEED is a live on-screen slider**, not a hardcoded const — users will always want to tune pacing

Full detail in `SKILL.md`.
