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
