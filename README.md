# Wizzme · Share-first Onboarding — prototype + handover package

Everything needed to implement the new onboarding lives in this folder.

| What | Where |
|---|---|
| **Interactive prototype** (source of truth for look, copy, motion) | [`index.html`](index.html) · live: https://prathameshb-wizz.github.io/wizzme-onboarding-prototype/ |
| **Engineering handover** (requirements, per-screen specs, backend, analytics, QA) | [`handover.html`](handover.html) · live: https://prathameshb-wizz.github.io/wizzme-onboarding-prototype/handover.html |
| **All media assets** | [`assets/`](assets/) — mapped below |

Run locally: open `index.html` in a browser (no server needed), or `python3 -m http.server` in this folder.
Drive it: tap the phone / arrow keys / scene list in the sidebar. Deep-link any scene with `?scene=N` (1–13), freeze any moment with `&scrub=<seconds>`.

The prototype is one self-contained HTML file: all CSS, all GSAP timelines (scenes 1–7), and all app-screen logic (screens 8–13) are inline. External dependencies: GSAP 3 (CDN) and Google Fonts (Gentium Book Plus, Manrope, Kalam).

## Asset map — every media item and exactly where it is used

### Logos — `assets/`

| File | Used in |
|---|---|
| `wizzme-logo-stone.png` | Phone-chrome brand header (all film scenes); the big scene-7 lockup |
| `wizzme-logo-lilac.png` | Sidebar brand on the dark page background |
| `wizzme-logo.png`, `wizzme-logo-twilight.png` | Legacy from earlier prototype rounds; not referenced by `index.html`, kept for reference |

### People — `assets/people/` (the film's cast; scenes 1, 5, 6, 12)

| File | Character | Used in |
|---|---|---|
| `p-found-1.jpg` | **Arjun**, "Your junior from college", asks "Masters abroad, or a job here first?" | Scene 1 (dot + person 1) · scene 5 (he comments on your story) · scene 12 (destination row) |
| `p-found-2.jpg` | **Priya**, "Starting her first job in two weeks" | Scene 1 (dot + person 2) · scene 12 |
| `p-found-3.jpg` | **Meera**, "Just moved to your city" | Scene 1 (dot + person 3) · scene 12 |
| `p-ananya.jpg` | fourth searcher dot (no speaking role) | Scene 1 dots |
| `p-you.jpg` | **You** (the viewer's stand-in) | Scene 6 profile head · scene 11 answering avatar · scene 12 |

### Story covers — `assets/stories/`

**"Your" stories in the film** (watercolour, one palette each; also used as the topic→cover map in screens 11–13):

| File | Story / topic | Used in |
|---|---|---|
| `story-switching-streams.jpg` | "Why I switched streams and never looked back" — THE film story | Scenes 4, 5 (same card), 6 grid |
| `story-first-year.jpg` | "The year I thought everyone knew more" · topic map: Office life | Scene 6 grid · screens 11–13 when topic = work |
| `story-first-salary.jpg` | "What my first salary taught me" · topic map: Money | Scene 6 grid · screens 11–13 when topic = money |
| `story-friends.jpg` | "Friendship, after college" · topic map: Moving cities / Relationships | Scene 6 grid · screens 11–13 when topic = moving/rel |

**Real-story deck covers** (scene 7; cards are real public Wizzme stories, story IDs in `handover.html` §4):

| File | Card |
|---|---|
| `real-yc.jpg` | Aryan (Aryan Agarwal) — "What YC actually feels like from inside" |
| `real-campnou.jpg` | Anish (Anish Dokania) — "One ticket to Camp Nou" |
| `real-firstbike.jpg` | Pranay (Pranay Kumar Urma) — "My first bike, chosen on seating comfort" |
| *(no image — intentional)* | Shivani (Shivani Bajaj) — "The morning I couldn't smile" is a quote-only card by design; do not add art |

### Art style contract (for any new covers)

Light, airy watercolour on white paper, one figure filling the frame, one clear action readable at a glance, distinct palette per image, no dark backgrounds.

## Where things are specified

- Screen-by-screen requirements, routing rules, interview questions, backend/data needs, analytics events, QA checklist → `handover.html`
- Exact timings, easings, and choreography → the `scene1()…scene13()` functions in `index.html` (each scene is one GSAP timeline; `play(n)` rebuilds)
- Design tokens → `:root` in `index.html` + handover §6 (reconcile with the app's `DESIGN_SYSTEM.md` rather than duplicating hex values)
