---
name: data-explainer-video
description: Build a Tatakye-style data-explainer short video as a self-contained HTML page (Canvas + Web Audio, no deps). Use when the user wants to turn an article/essay into a short video (3-6 min), especially minimal black-gold aesthetic with particle fields, animated curves, big-number reveals, sparse ambient audio, and subtitle-driven narration. Produces a single HTML file the user plays in-browser and screen-records.
---

# Data-Explainer Video (Tatakye-style)

Build a short, Chinese-subtitle-driven explainer video as **one self-contained HTML file** that the user plays in a browser and screen-records.

## What this is good for

- Turning an article, essay, or research finding into a 3-6 minute video
- Minimal black-gold "think-piece" aesthetic (3Blue1Brown / Veritasium / Tatakye lineage)
- Deliverables where the user wants to post to Xiaohongshu / WeChat Video / Bilibili / YouTube
- Zero external assets — no fonts to buy, no stock footage, no royalty concerns, no server

## Before writing a single line of code

**Non-negotiable upfront questions** — ask these with AskUserQuestion, not after. Getting them wrong means a rewrite.

1. **Theme in one sentence**: Not "what the article is about" — the *claim* the video is defending. If you can't say it in one sentence, you don't have a video yet, you have a reading list.
2. **The spine**: What single on-screen object will anchor the whole video? (See "The Spine" section below — this is the most important design decision, and the one most explainer videos get wrong by omitting entirely.)
3. **Length**: 3-4 min (highlights) vs 5-6 min (standard Tatakye-length) vs 8-10 min (deep). Length determines how many sections survive. For a 10-section article aiming at 5 min, you need to kill 60-70% of sections.
4. **Narration mode**: Subtitles only (text-driven pacing) vs AI voiceover vs self-recorded. "Subtitles only" is the default — the subtitles themselves become the beat.
5. **Attribution**: How to credit the original author. "原文 · [Name]" top-right is the clean default. If you have a spine, attribution goes *under* the spine, not instead of it.
6. **The payoff (not a rhetorical question)**: What specific thing does the viewer walk away with? *A reframed question is NOT a payoff.* "Are you them?" sounds powerful but gives the viewer nothing to take home. A real payoff is a short named list (2-4 items) they can repeat the next day. See "Payoff, not rhetoric" below.

**Never skip these.** The first attempt almost always fails on #1 (theme) and #5 (landing). You can rewrite freely once these are pinned.

## The Spine — the single most important design decision

**A great explainer video has a *spine*: one persistent on-screen object that stays visible for most of the video, and every beat lights up a different part of it.**

Tatakye's 股市回报 video is the canonical example. The spine is the formula `p = E[mx]`, pinned to the upper-right corner from 1:00 to 3:30. Every section highlights one symbol — `x`, then `m`, then `π_s` — teaching that symbol's meaning. At the end, the formula "unlocks" into three concrete takeaways (`x` → "which futures", `m` → "which world", `π_s` → "how long to wait").

**Why this works, and why videos without a spine feel weak**:
- The spine is a visual *anchor*. If a viewer looks away and comes back, they immediately know "what we're currently decomposing."
- It converts an abstract framework into a *physical object* on screen. The idea has coordinates.
- Chapter labels can only tell viewers *where in the structure* they are. The spine tells viewers *which component of the idea* is being explained — which is a stronger signal.
- The payoff at the end can literally be "the spine, solved." You open with a question, build up each part of the spine, and close by handing the spine back as the answer.

### What makes a good spine

A spine candidate must:
1. **Fit on one line** (so it can live in a corner the whole time)
2. **Have 3-5 named components** that each map to one beat of the video
3. **Be visually stable** — not an animation, a static reference frame
4. **Hold the thesis** — if you understand every part of the spine, you understand the piece

Common forms (ranked by punchiness):
- **An equation**: `工作 = 肌肉 × 心智`, `p = E[mx]`, `价值 = 稀缺性 × 关注度`
- **A diagram with named arrows**: `生产者 → 产品 → 用户`, nodes you can highlight one at a time
- **A labeled ratio or comparison**: `过去 : 现在 : 未来`
- **A short sequence**: `观察 → 假设 → 实验 → 结论`

Avoid as spine:
- **A single number** (no components to light up)
- **A long sentence** (too wordy for a corner, defeats the point)
- **A chart** (charts are keystone visuals, they live in the center, not as spine)

### Spine must appear BEFORE Act I ends, and persist

Don't drop the spine on the viewer at the start and never return. Don't wait until Act II to introduce it. The structure is:
1. **0:00–0:30 Hook**: no spine yet; set up the question
2. **~0:30 Spine reveal**: the equation/diagram fades in top-right
3. **Act I–III**: spine stays, each act lights up one component
4. **Payoff**: spine dissolves and *becomes* the three-item list of takeaways

### Spine term highlighting (visual recipe)

Each spine term should have three states:
- **dim** (default): `color: var(--dim)` — grey, present but muted
- **lit** (currently being explained): `color: var(--gold)` + text-shadow glow — unmistakably "we are here now"
- **done** (already explained): `color: var(--fg)` — white, taught, settled

When a new section starts, demote the previous `.lit` to `.done`, promote the new term to `.lit`. One term lit at a time. The visual effect: the spine lights up progressively left-to-right, and at the end everything is white (fully taught), ready to dissolve into the payoff.

## Narrative structure — one claim, few beats

**The only hard rule**: the piece defends **one claim**, and every beat exists to serve it. If a section doesn't push the claim forward or set up a later beat that does, cut it.

Beyond that, structure is a tool, not a template. Pick the shape that fits the claim:

- **Three-act (Hook → Pattern → Twist → Cost)** — good when the claim has a surprising reversal (like "we've done this before, but this time there's a cost")
- **Problem → Mechanism → Implication** — good for explaining why something works the way it does
- **Timeline / build-up** — good when the point is accumulation ("look how far this has come")
- **Comparison** — good for "A vs B, and here's why it matters"
- **Question → Attempts → Resolution** — good for research findings or investigation pieces
- **Single-insight unfold** — one surprising fact, slowly built up and then landed (Tatakye's股市回报 video is this)

How to pick: say the one-sentence claim out loud. What's the natural *rhythm* of making that argument? That's your structure.

**Section count scales with length, not structure**:
- 3-4 min → 3-4 keystone beats
- 5-6 min → 5-7 beats
- 8-10 min → 8-12 beats

**Each beat needs**:
- One keystone visual (a curve, a comparison, a diagram, a particle event)
- One keystone number OR one keystone phrase
- A transition that pivots to the next beat (not just "and now section 2")

**Red flag**: if your outline reads like "section 1, section 2, section 3..." as a flat list, you're walking the user through a reading list. Compress or re-sequence so beats *chain* — each one making the next one feel inevitable.

## Scene economy — fewer scenes, longer evolutions

**A common failure mode**: making every section a *new scene*. Result: seven unrelated visuals in a row, each lasting 30 seconds, viewers get whiplash and remember nothing.

**The Tatakye principle**: one visual object, evolving over 2-3 minutes. In the 股市回报 video, the "probability-space grid" is on screen from ~0:40 to ~2:30 — nearly two minutes. During that span it:
1. Appears as just lines ("all possible worlds")
2. Grows gold bars (`x`, payoff in each world)
3. Bars get colored (`m`, weight of each world)
4. The formula appears above (expected value)
5. Specific numbers overlay (concrete example: 0.86, +16.9%)
6. Verbal labels overlay ("萧条/繁荣")

**Six iterations, one visual object.** The viewer's eyes never reset.

### Rules of thumb

- **Target: 3-5 total scenes** for a 5-minute video. More than that = probably switching too much.
- **Minimum scene duration: 60-90 seconds** for substantive scenes. Less than a minute = probably belongs as a *layer within another scene*, not a scene of its own.
- **Prefer scene-grows-into-next-scene over cut.** Example: a double-curve plot grows a shaded area between the curves, which grows bars rising out of that area — three "sections" of content, zero scene cuts.
- **Scene changes happen on act boundaries, not within acts.** Within an act, use overlays, highlights, number count-ups, labels — not scene changes.

### When a scene change IS justified
- Hook → first content scene
- Act N → Act N+1 if the visual metaphor fundamentally cannot carry the next idea
- Content → payoff (the end deserves a visual reset)

That's it. Three scene changes in a 5-minute video, maximum.

## Payoff, not rhetoric

Great explainer videos end with **a specific, named list of 2-4 things the viewer can take away.** Not a question. Not a feeling. A list.

Tatakye's 股市回报 video ends by handing you three things (`x`, `m`, `π_s`) with concrete interpretations: "which futures to buy, which world you're in, how long to wait." The viewer can repeat this at dinner that night.

**Common anti-patterns**:
- "你，是吗？" / "Are you them?" — reframed question. Feels powerful. Teaches nothing. Viewer closes the video, remembers the vibe, forgets the content.
- "What do you think?" — rhetorical punt. The video didn't commit to anything.
- "Only time will tell." — journalistic hedge. Same problem.
- A single sentence of comfort. "We've been here before." — flat, not actionable.

**How a good payoff feels**: like unlocking the spine. The spine was `A = B × C`. The payoff is "so what matters are: (1) B, (2) C, (3) the interaction between them." The video literally resolves into its answer.

### The 3-item answer screen (recipe)

```
     01            02            03
      X             Y             Z
    label         label         label
   caption       caption       caption
```

- Three vertical columns, equal spacing
- Items appear one at a time, ~1-second apart (chime per item)
- Each item: index number (01/02/03), single-glyph emblem (one Chinese character or math symbol), short label (2-4 characters), one-sentence caption
- Hold 3-4 seconds after all three appear, then transition out
- Then one closing line, which *can* be the hook rephrased as resolved: "你，在哪一侧？" works AFTER you've named the sides.

## Chapter labels as content signposts

Weak chapter labels: `ACT I`, `ACT II`, `ACT III` — tells the viewer *where in the structure* they are. They don't care.

Strong chapter labels: `肌肉 · 第一次外包`, `心智 · 第二次外包`, `× · 相乘`, `= · 代价`, `答案 · 三件事` — each label is **a term from the spine** or a direct piece of content. Reading the label, the viewer immediately knows *what idea is being decomposed right now*.

**Rule**: the chapter label should be a word the spine would highlight. If "ACT II" is your chapter label but your spine says "心智", change the chapter label to "心智". Don't duplicate structural scaffolding into the chapter label — structure is implicit, content is what viewers need.

## Visual system (Tatakye-style)

### Color
```
--bg:    #0a0a0f   /* NOT #000000 — pure black looks dead on screen */
--fg:    #eceae4   /* warm white, 2% blue bias; never pure white */
--dim:   #8a8a90   /* for axis labels and captions */
--gold:  #d4a85a   /* ONLY color used for emphasis */
--red:   #c15b4e   /* only for "negative" stats (wages lagging) */
```
Never use more than these 5. Resist the urge to add blue/green for variety.

### Typography — this is where videos die

- **Chinese or English, pick one per element**. Never "ACT II · THE PARALLEL · 第二幕 · 现在轮到心智" — that's redundant, hard to read, and screams "AI-made bilingual slide". Choose one language per label.
- **Minimize italics**. Italics on CJK look bad in almost every browser (fake-slanted glyphs). Use color (`var(--gold)`) for emphasis, not italics.
- **Minimum sizes for mobile viewing**:
  - Axis ticks: 17px baseline (scaled by `fontPx()`)
  - Axis labels: 17-19px
  - Curve-end labels: 19px
  - Chapter label (top-left): `1.1rem`
  - Subtitle (bottom center): `1.15rem`
  - Headline numbers (center): `4.5rem+`
  - Mega opening/closing text: `1.9rem+`
- Serif for display numbers (EB Garamond fallback → Noto Serif SC). Sans for everything else (Inter → PingFang/Noto Sans).

### Four-layer information architecture (Tatakye signature)
Every scene has up to four text layers at fixed positions:
1. **Top-left**: Chapter label (small, letter-spaced, dim)
2. **Top-right**: Author credit (small, dim)
3. **Center**: Big number / headline (large, serif)
4. **Bottom-center**: Subtitle narration (medium, sans)
5. **Bottom-left italic (optional)**: Academic citation (`恩格斯停滞 · Robert Allen`)

### Core motifs (reuse 3-5 across the piece)
Don't invent one new visual per section — pick a small set and vary them:
- **Particle field** with perspective: 120×36 grid, far rows near horizon, slight sinusoidal wave
- **Rising curve on time axis**: flat for most of X, exponential liftoff; label time anchors as narrative words ("现在", "未来") not specific years (2000 is already past)
- **Falling curve with area fill**: price collapse / value draining
- **Horizontal time bars**: proportional length comparison (40年 vs 5年 at 1/8 scale)
- **Code rain**: short domain-specific lines falling, for "machine takes over cognitive work"
- **Dot/particle shatter**: for "something breaks" moments

### Camera breathing
Add micro parallax to any static scene: `camBreath = sin(t*0.14)*6, camSway = sin(t*0.09)*4`, applied with depth-weighted multiplier so near elements move more than far. Prevents the "dead frame" feeling.

### Scene transitions
Always use blackout blinks between scenes — never hard cuts. `sceneBlink(cb, {dark:0.45, hold:0.08, light:0.5})`: fade to black over 0.45s → run scene change → fade back over 0.5s. Total ~1s per transition. Feels like film cuts, not slide swaps.

### Number count-up
Every big number animates 0 → target with easeOutCubic over ~1.1s when revealed. Use `<span class="count" data-to="99" data-suffix="%" data-dec="0" data-dur="1.1">`. The chime fires the moment the count starts; by the time the eye reaches the number, it's just finishing its animation. This is the single highest-leverage polish detail.

## Audio system

### What NOT to do (I kept getting this wrong, so write it down)
- ❌ Persistent low-frequency drone (sub-100Hz). Painful on headphones, uncomfortable on speakers.
- ❌ One chime per subtitle. Density is wrong — subtitles happen 30+ times, audio events should happen 10x less. The visual tempo IS the subtitle tempo; audio has its own tempo.
- ❌ Same chime timbre every time. Even if the pitch rotates, same waveform = still monotonous.
- ❌ Standard integer harmonics (1x, 2x, 3x). That's a flute. For bells use **inharmonic partials** (1.0, 2.01, 3.03, 4.95, 7.10) — this is what makes it sound like glass, not synth.

### Correct recipe

**Background music** — one layer only:
- **Airy pad** at A-minor-7 (A3 C4 E4 G4), triangle waves with 0.5% detune, slow filter LFO
- Gain `.08-.12` (barely audible, just prevents dead-silence)
- Hard 160Hz high-pass on master to kill any mud
- Soft 5-6kHz low-pass for warmth

**UI chimes** — fire only at ~6-12 points across the whole video:
- Opening/closing mega text: `swell` (5-note stacked chord)
- Chapter label appearance: `chord` (3-note soft arpeggio)
- Big-number headline reveal: `strike` (4-note arpeggio + bass octave)
- **Subtitle appearance: NO chime** (too frequent)
- Act III subtitles: `low` variant (minor-2nd dissonance) — only if explicitly needed

**Bell voice construction**:
- 5 inharmonic sine partials with per-partial decay (fundamental lingers, high partials die fast)
- `linearRampToValueAtTime` attack (8-15ms), `exponentialRampToValueAtTime` decay (1.5-3s)
- Multiple timbres: `bell / glass / marimba / tine / pluck` — rotate randomly for variety

**Reverb**:
- Synthetic convolution with 2.6s exponential-decay noise IR
- Send `.55`, return `.9`, feeds all bell voices + pad
- Makes everything sit in the same space, kills "dry" synth feel

**Loudness staging**:
- Pad barely audible is correct — subtitles have no voiceover, so middle frequencies stay clear
- Chimes should feel like events, not punctuation
- Final 10s crossfade master to 0

### Analyzing a reference track
When the user hands you a reference video, extract spectrograms before writing audio code:
```bash
ffmpeg -y -ss 60 -t 25 -i "$REF" -vn -ac 1 -af "lowpass=f=250" /tmp/music_lo.wav   # bass separate
ffmpeg -y -ss 60 -t 25 -i "$REF" -vn -ac 1 -af "highpass=f=2200" /tmp/music_hi.wav # treble separate
ffmpeg -y -i /tmp/music_lo.wav -lavfi "showspectrumpic=s=1400x400:mode=combined:color=rainbow" /tmp/lo.png
ffmpeg -y -i /tmp/music_hi.wav -lavfi "showspectrumpic=s=1400x400:mode=combined:color=rainbow" /tmp/hi.png
```
Then Read both PNGs. The low-band spectrogram tells you if bass is present (often empty — subs/basslines are rare in Tatakye-type stuff). The high-band one tells you whether UI "chimes" are real sound events or just voice sibilants.

Also run transient detection:
```bash
ffmpeg -i "$REF" -af "aformat=channel_layouts=mono,asetnsamples=9600:p=0,astats=metadata=1:reset=1,ametadata=print:key=lavfi.astats.Overall.RMS_level:file=/tmp/rms.txt" -t 120 -vn -f null -
```
Then parse for frames where RMS jumps >6dB in 0.2s — those are real sound events. Count them: a 2-minute reference with 2 events means **1 chime per minute**, not 1 per subtitle.

## Playback & recording

The HTML needs a **Press-to-begin** overlay. Browsers require a user gesture before starting Web Audio — don't try to autoplay.

Give the user:
1. The absolute path to the HTML
2. "Open in Chrome fullscreen (⌃⌘F on Mac)"
3. "Record with QuickTime screen-record OR OBS"
4. "QuickTime won't capture system audio by default — install BlackHole (free) as a virtual audio device, or use OBS which handles both"

## Technical skeleton

Full working template lives at `template.html` (older) and `template_v2.html` (newer, spine-based) in this skill folder. **Use v2 as default.** Key architecture:

```javascript
// cues timeline: [timeInSec, actionFn][]
const cues = [
  [0.0,  ()=>{ setMega('...'); }],
  [26.0, ()=>{ setMega(''); sceneBlink(()=>{ scene.mode='field'; }); }],
  [30.0, ()=>{ setChapter('肌肉 · 第一次外包'); showSpine(); litTerm('muscle'); }],
  // ...
];

// LIVE speed control — ALWAYS include this, with a visible slider
let SPEED = 1.6;              // mutable
let startAt = null;
let accumElapsed = 0;         // seconds of "video time" already consumed
let lastWallClock = null;
function elapsed(){
  if(startAt==null) return 0;
  const now = performance.now();
  if(lastWallClock!=null){
    accumElapsed += ((now - lastWallClock)/1000) * SPEED;
  }
  lastWallClock = now;
  return accumElapsed;
}
```

**Important**: use the accumulator model above, not `(now-startAt)*SPEED`. When the user drags the speed slider mid-playback, the second form causes the current cue index to jump wildly. The accumulator model advances smoothly at whatever current speed is set, without retro-applying.

### Required HTML layers (fixed positions)
- `<div class="chapter">` top-left — current chapter label
- `<div class="spine">` top-right — **persistent equation / anchor** with per-term `.lit/.done` states
- `<div class="sub">` bottom-center — subtitle narration line
- `<div class="cite">` bottom-left — optional academic citation
- `<div class="mega">` full-screen — opening/closing text
- `<div class="answer">` full-screen — 3-item payoff list
- `#speedCtl` bottom-right — live speed slider (0.5× - 3.0×, default 1.6×)

### Required Canvas scenes to implement
Keep the set SMALL. Target 3-5 total:
- `field`    — particle landscape (opening + closing only)
- `graph`    — one or more curves on time axis, with evolution states (fade in curve A, then curve B, then shaded area between them, then annotations)
- `bars`     — distribution of outcomes, deterministic log-normal-ish heights
- `dark`     — empty black for text-only moments

Skip these unless specifically needed: `collapse`, `timebar`, `jenny`, `codestream`. V1 had too many — each one costs a scene change the viewer has to absorb.

### Helper functions you'll want
```javascript
tween(key, from, to, durSec)     // ease-in-out scene parameter animation
sceneBlink(cb, opts)             // fade-out, run cb, fade-in
fontPx(sizeAt1920)               // scale canvas text to viewport
pick(arr)                        // random choice for chime variety
bellNote(freq, {t, gain, dur, timbre})
chimeHit(variant)                // 'soft'|'chord'|'strike'|'swell'|'low'

// Spine control — essential, do not skip
showSpine()                      // fade in the top-right equation
hideSpine()                      // fade out
litTerm(name)                    // highlight one term (gold); demote prev lit → done (white)
unlitAll()                       // reset all terms to dim

// Answer list control
showAnswerItem(index)            // reveal one item in the 3-item payoff
hideAnswer()                     // fade out all
```

## Iteration playbook

Users will give feedback in several predictable waves:

### "Nothing happens when I click play"
Almost always a syntax error in a template literal — a stray `\\'` from improper escaping ends a string early. Grep for `\\'` and switch those strings to double-quoted.

### "The theme is unclear / I don't know what you're trying to say"
Your fault for not nailing the one-sentence theme AND the spine upfront. Do NOT patch individual lines. Propose a full rewrite starting from: (a) what is the one-sentence claim, (b) what is the spine (persistent on-screen anchor), (c) what are the 3 payoff items. Get buy-in on all three BEFORE touching code.

**If the user feels the previous version was "superficial" or "scattered"**: the fix is almost always "add a spine." Not "better transitions" or "more polish." The video felt scattered because there was no persistent anchor telling the viewer what idea was being decomposed. Reread "The Spine" section.

### "The animation feels thin / underpowered"
Usually means too many scenes, each too short, each introducing a new metaphor the viewer must absorb from scratch. Fix: cut scenes 60-70%. Replace scene changes with **evolution within one scene** (fade in curve A, then curve B, then shaded area between them, then annotations). See "Scene economy" section.

### "Too slow / too fast"
Expose SPEED as a visible on-screen slider (bottom-right), with 0.5-3.0 range, default 1.6. Use the accumulator model for `elapsed()` so mid-playback adjustments don't jump. Don't retime individual cues unless the user says "the Act II section specifically is too fast".

### "Can't read the small text on mobile"
Bump all font sizes 1.5-2x, add `fontPx()` helper, scale Canvas text to viewport width (baseline 1920). CSS `rem` sizes scale automatically but Canvas-rendered text does not.

### "Audio is too much / too monotonous / too noisy"
Three different problems. Diagnose which:
- "Low frequency uncomfortable" → add 160Hz HPF, remove sub drone
- "Too much chime" → stop firing chime on subtitles, keep only on 6-12 keystone events
- "Monotonous even though I added variety" → vary **timbre**, not just pitch. Pattern-based random templates (6 chime variants) are better than always-the-same-structure-with-random-notes

### "Need background music"
Default to synthesized ambient (Web Audio). Only reach for an audio file if the user specifically asks.

### "The axis time labels don't match what we're saying"
Verify: "2000" is already past (we're in 2026+). Use narrative anchors — "现在", "未来" — not calendar years for curves that extend into the future.

### "This doesn't look like my reference"
Spend 10 minutes with ffmpeg spectrogram + frame-grab analysis before writing anything. The user's taste is in the reference. Your "guess" is almost always wrong.

### "The ending feels empty / viewer takes nothing away"
You ended on a rhetorical question or a sentence of comfort. Replace with the 3-item answer screen. See "Payoff, not rhetoric."

## Common pitfalls I've hit

| Mistake | Why it happens | Fix |
|---|---|---|
| **No spine** | Treating the video as a sequence of scenes instead of a decomposition of one idea | Add a persistent top-right anchor (equation, diagram, labeled sequence). See "The Spine." |
| **Too many scenes** | Treating each section as its own visual | Cap at 3-5 scenes for 5min. Evolve within scenes, don't cut. |
| **Rhetorical ending** | Confusing emotional punch with payoff | End on a named 2-4 item list, not "are you them?" |
| **ACT I/II/III chapter labels** | Reaching for structure labels instead of content labels | Chapter label = word from the spine. "心智", not "ACT II". |
| Writing a 10-section outline | Trying to be faithful to the article | **Compress to one claim and the beats needed to defend it.** Fidelity is to the thesis, not the article's section headers. |
| Chinese + English on every label | Trying to "cover both audiences" | Pick one. Author names stay in original language. |
| Italics everywhere | Trying to look "editorial" | CJK italics look bad. Use color for emphasis. |
| Chime per subtitle | Pattern-matching "events need sounds" | Audio has its own tempo, independent from visual. Count the reference's events per minute. |
| 10px axis labels | Looking fine on your 27" monitor | Mobile users can't read them. Baseline 17-19px. |
| Hard scene cuts | Not thinking about transitions as a design element | Always blackout-blink (`sceneBlink`). |
| Static numbers | Easier to code | Always count-up animate. Highest-leverage polish detail. |
| Pure black `#000000` | Default-of-defaults | Use `#0a0a0f`. Pure black looks dead on OLED, muddy on LCD. |
| Const SPEED | Easier to hardcode | Make it a mutable with a visible slider; users will ALWAYS want to tune pacing. |

## Final checklist before showing the user

- [ ] Theme fits in one sentence
- [ ] **Spine defined**: one persistent on-screen anchor with 3-5 named components
- [ ] **Spine present from ~0:30 to near-end**, each beat lights one component
- [ ] **Payoff is a named 2-4 item list**, not a rhetorical question
- [ ] **Chapter labels = words from the spine**, not "ACT I/II/III"
- [ ] **Scene count ≤ 5** for a 5-min video
- [ ] Structure matches the claim's natural rhythm (not forced into a template)
- [ ] Each beat has one keystone visual + one keystone number/phrase
- [ ] Beats chain — each sets up the next, no flat section list
- [ ] All numbers count-up animate
- [ ] All scene changes use `sceneBlink`
- [ ] **SPEED is a live on-screen slider**, not a hardcoded const
- [ ] No Chinese+English duplicate labels
- [ ] No italics on Chinese text
- [ ] Font sizes readable on 400px-wide mobile
- [ ] Audio: 6-12 chime events total, pad gain `<.15`, 160Hz HPF present
- [ ] No chime on every subtitle
- [ ] X-axis labels use narrative anchors not past-year numbers for forward-looking curves
- [ ] `SPEED` multiplier present for easy pacing tuning
- [ ] Press-to-begin overlay (browsers require user gesture for audio)
- [ ] Output path printed with recording instructions
