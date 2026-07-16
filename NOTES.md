# NOTES

## Round 1 — Module 1 (Hero, Waterjet)

- Added `HEAD.html` (Typekit link + scoped `.applied-landing-page *` font-stick rule) and `FOOTER.html` (video-autoplay script moved out of the module) per the architecture rules in the style handout.
- `modules/module-01-hero-waterjet.html`: only fonts, colors, and buttons changed, structure/copy untouched.
  - Colors: replaced off-brand `#007680` / `#005f68` (teal) and `#fdb81e` (yellow) with approved `#007b85` / `#005662`. Eyebrow ("Precision Waterjet Cutting") now plain teal `#007b85` text, no nested white span.
  - Font: set the DIN 2014 stack explicitly (`"din-2014", "DIN 2014", "DIN Next", "Helvetica Neue", Helvetica, Arial, sans-serif`) on the eyebrow, headline, subheadline, body copy, and both buttons instead of relying on inheritance. Headline weight capped at 700 (was already `bold`).
  - Buttons: rebuilt to spec — `border-radius: 6px`, `font-weight: 700`, `transition: all 0.25s ease`.
    - Primary ("Request a Quote"): fill/border `#007b85`, hover fill/border `#005662`, hover glow `0 6px 20px rgba(0,123,133,0.50)` (hero glow value), lift `translateY(-1px)`.
    - Secondary ("See Our Capabilities"): converted from a transparent outline button (disallowed outside the dark final CTA) to the spec's **hero secondary** style — white fill, teal text, white border; hover inverts to teal fill, white text, teal border, same glow and lift.
  - Moved the inline `<script>` for video autoplay into `FOOTER.html` (modules may not contain `<script>` blocks); it still exits early if `#hero-video-bg` isn't on the page.
- Files changed: `HEAD.html`, `FOOTER.html`, `modules/module-01-hero-waterjet.html`, `NOTES.md`

## Round 2 — Module 2 (Why Waterjet + Engineered) and full HEAD.html rebuild

- The user provided the live `HEAD.html` for the whole campaign (it defines colors/fonts/buttons for every section via classes, not inline styles — Module 2's own markup has no inline styling to fix, so `modules/module-02-why-engineered.html` is unchanged from source). Replaced the Round 1 placeholder `HEAD.html` with this real, corrected file since it's the authoritative page-wide stylesheet.
- Font: removed the Google Fonts Barlow `<link>` tags entirely; replaced with the Typekit `<link>`s. `.applied-landing-page` base font-family switched to the DIN 2014 stack (Barlow removed from the fallback chain). Kept the scoped `.applied-landing-page, .applied-landing-page *` font-stick rule as the LAST rule in the file.
- Weight ceiling: every `font-weight: 800` on a heading (h2/h3 across Why Waterjet, Capabilities, Engineered, Contact, Map, Video Library sections) dropped to `700`.
- Colors — off-brand values replaced throughout every section's CSS:
  - `#007680` → `#007b85`, `#005f68` → `#005662` (teal, incl. gradients and their `rgba()` box-shadow/tint equivalents).
  - `#1B0F3A` / `#1b0f3a` (navy) — as **text** (headings, list items, tab/nav labels, location names) converted to black `#000000` per "navy is not a text color"; as **background/gradient/accent border** (card tops, icon gradients, tab active underline, nav button fill) converted to approved navy `#1E2F5C`, with darker-navy hover states using `#12203F`.
  - `#2d1a5e` (off-brand purple-navy gradient stop) removed.
  - `#FDB81E` / `#fdb81e` / `#e5a71a` (yellow) removed entirely — no exception carved out for the eyebrow, the engineered-section image badge, or the contact-card icon chips/links. Eyebrows now plain teal `#007b85`; the image badge became a teal-filled pill; contact-card icon chips and link-hover now use teal instead of yellow.
  - **Final CTA gradient** (`.aih-contact-card`): changed from the off-brand `linear-gradient(135deg, #1b0f3a 0%, #2d1a5e 100%)` to the spec's exact `linear-gradient(135deg, #1E2F5C 0%, #000000 100%)`.
  - Arbitrary off-ramp grays (`#444444`, `#333333`, `#4b5563`, `#1f2937`, `#9ca3af`, `#e5e7eb`, `#f1f5f9`, `#f9fafb`, `#f3f4f6`, `#f1f1f1`, `#888`, `#555`, `#666`) mapped to the nearest approved gray-ramp token (mostly `#424242`, `#E0E0E0`, `#F5F5F5`, `#FAFAFA`, `#EEEEEE`, `#9E9E9E`, `#757575`, `#616161`) or to black where the element is a heading.
  - **Category-dot legend** (interactive map tabs): `belt` (`#6B46C1`, purple — banned) and `reducer` (`#059669`, green — off-palette) collapsed to the gray ramp (`#757575` and `#424242`) per your call; `rubber`/`hose`/`all` now use the approved navy/teal. Flagging this here since it trades away some at-a-glance category distinctiveness — worth a design look if that legend needs to stay visually distinct.
- Buttons: `.carousel-btn` (video library prev/next nav) was a transparent-fill, navy-outline button on a white section background — the handout explicitly disallows outline-only buttons outside the dark final CTA. Converted it to the spec's **Navy** button: fill/border `#1E2F5C` at rest, hover fill/border `#12203F` with the `0 6px 18px rgba(30,47,92,0.40)` glow and `translateY(-1px)` lift, `transition: all 0.25s ease`. Kept its circular `border-radius: 50%` (icon nav control, not a rectangular CTA — the 6px radius rule targets text buttons). The `.applied-tab` map filters and `.aih-eng-image-badge`/rotator caption badge are non-CTA UI (tab nav, pill badge) so only their colors were fixed, not restructured into the button spec.
- No actual CTA button markup exists yet in the Contact/Request-a-Quote section (only text/rows) — when that module's HTML arrives, its buttons should follow the "dark final CTA" button rules (white-fill primary with navy text, outline secondary) since it sits on the `#1E2F5C → #000000` gradient.
- Files changed: `HEAD.html`, `modules/module-02-why-engineered.html`, `NOTES.md`

## Round 3 — Module 3 (In-House Capabilities)

- No changes needed. Module 3 only uses the `.aih-cap-*` classes (section, wrapper, header, grid, card, card--navy, card-icon-wrap, card-body), all of which were already corrected to spec in Round 2's `HEAD.html` rebuild (teal/navy colors, 700 weight cap, black headings). No inline font/color styles and no buttons in this module's markup.
- Files changed: `modules/module-03-capabilities.html` (added, unchanged from source), `NOTES.md`

## Round 4 — Module 7 (Request a Quote — Contact)

- This card sits on `.aih-contact-card`'s navy-to-black gradient — the handout's dark-final-CTA exception, with its own button spec (white fill, navy text, no colored border, neutral shadow) distinct from the standard primary/secondary/navy variants.
- Eyebrow: removed the inline `<span style="color: #ffffff;">` wrapper around "Request a Quote" so it falls through to `.aih-contact-card p.eyebrow` (plain teal `#007b85`, fixed in Round 2) instead of overriding to white.
- Button ("Request a Quote"): was yellow `#FDB81E` fill with navy `#1b0f3a` text and `font-weight: 800` — both banned (yellow) and over the DIN weight ceiling (800 renders in Helvetica, not DIN 2014). Rebuilt to the dark-final-CTA primary spec: white fill, navy `#1E2F5C` text (the one sanctioned place navy is text), no colored border, `font-weight: 700`, `border-radius: 6px` (unchanged), `transition: all 0.25s ease`, resting shadow `0 4px 14px rgba(0,0,0,0.2)`, hover deepens to `0 8px 24px rgba(0,0,0,0.3)` with a `translateY(-2px)` lift. Added the DIN 2014 font stack explicitly (was relying on inheritance).
- No other changes: `.aih-contact-*` classes for the rest of the card (headings, list, icon rows) were already corrected in Round 2's `HEAD.html`.
- Files changed: `modules/module-07-contact.html`, `NOTES.md`

## Round 5 — Module 5 (Service Map) + wrapper-scope bug fix on Modules 2, 3, 7

- Module 5 needed no font/color/button edits: it already wraps its content in `<div class="applied-landing-page">...</div>` (matching Module 1), and its `.applied-map-*`/`.applied-tab*`/`.applied-location-*` classes were already corrected in Round 2's `HEAD.html`. Saved as `modules/module-05-service-map.html`.
- **Bug caught while comparing modules**: Modules 2, 3, and 7 were missing that same `.applied-landing-page` wrapper around their outermost element. Per the handout's font-stick rule (section 2b), the universal `.applied-landing-page, .applied-landing-page *` selector in `HEAD.html` only reaches elements that are descendants of a literal `.applied-landing-page` wrapper — since each module pastes into its own separate HubSpot Custom HTML block, each module needs its own copy of that wrapper, not just Module 1's. Without it, those three modules would have rendered in HubSpot's default theme font instead of DIN 2014 despite `HEAD.html` being correct.
- Fixed by wrapping the full contents of `modules/module-02-why-engineered.html`, `modules/module-03-capabilities.html`, and `modules/module-07-contact.html` in `<div class="applied-landing-page">...</div>`. No other content in those files changed.
- Files changed: `modules/module-02-why-engineered.html`, `modules/module-03-capabilities.html`, `modules/module-07-contact.html`, `modules/module-05-service-map.html`, `NOTES.md`

## Round 6 — FOOTER.html bug fix (hero video not playing)

- Root cause of "background video not showing up" on Module 1: in Round 1, the hero video-autoplay script (originally inline in Module 1's source) was extracted into a `FOOTER.html` I scaffolded from scratch, since Module 1 was the first file in an empty repo and no real footer existed yet. The user has now shared the actual, pre-existing `FOOTER.html` (smooth-scroll, interactive-map-tabs, and video-carousel scripts) — it never included the hero video script, so once the real footer was pasted into HubSpot it silently dropped hero video playback. The `<video>` tag also has no `autoplay` attribute, so nothing else was calling `.play()`.
- Fix: merged the hero video-background script into the real `FOOTER.html` as its own labeled block (right after the smooth-scroll/scroll-animation block, before the map tabs script), keeping the map-tabs and video-carousel scripts byte-for-byte unchanged.
- No font/color/button changes here — this file is pure JS.
- Action needed: re-paste `FOOTER.html` into HubSpot Page Settings → Advanced Options → Footer HTML.
- Files changed: `FOOTER.html`, `NOTES.md`
