# Block 08 Unpublished Website Candidate and QA

- **Branch:** `codex/block-08-web-qa`
- **Approved base:** `69451b4634c48c09b324f6dd06f490dbd3daa584`
- **Original August QA implementation commits:** `bb396b9`, `fc99105`, `269da70`, `e8f2d5e`, `23d7c5a`
- **Current website source checkpoint before this report refresh:** `17ccab6`
- **Local technical result:** PASS
- **Publication result:** OWNER-GATED
- **Candidate branch pushed:** Yes
- **Published or deployed:** No
- **Production or authenticated dashboard mutations:** None

## What changed

The original August QA changed exactly three website source files:

- `index.html`
- `privacy.html`
- `terms.html`

The landing page now:

- Uses factual tracking language instead of adherence guarantees, speed claims, medication-effectiveness implications, or blanket privacy promises.
- Describes the medication-level chart as an estimate based on recorded dose timing, not medication effectiveness.
- Removes the unsupported Android delivery promise.
- Uses CSS to show only the real app screen from the existing hero image, with visible and accessible sample-data labeling.
- Uses normal-text colors that meet at least 4.5:1 contrast on every applicable background.
- Reflows without page-level horizontal overflow from 320 pixels upward, including when Google Fonts is unavailable and the declared fallback fonts render.
- Keeps the wordmark and App Store button separated across every integer width from 320 through 520, including a simulated 15-pixel scrollbar gutter.
- Keeps the hidden mobile sticky CTA out of keyboard and accessibility navigation.
- Moves focus from the sticky CTA to the equivalent visible App Store CTA before applying hidden, inert, and aria-hidden state.
- Fully removes decorative/reveal motion when the user prefers reduced motion.

The Privacy page received only technical metadata, responsive table containment, focus semantics, and a corrected H1/H2 hierarchy. The Terms page received only the page-language declaration. No legal wording or legal date was changed.

The current cumulative branch diff from the approved base contains nine website source/configuration
files and these two reports. Later website commits added the conversion-first product hub, removed all
remote font requests, corrected compact-header spacing and Visit Summary period wording, and replaced
the printable template's faux table with a native semantic table.

`assets/hero-phone.png` remained byte-for-byte unchanged at SHA-256 `c5b335268227e41a0885cd3359b67985919f7147859ee9183a598c48b5d746e3`.

## Final full QA result

The final full rerun tested commit `23d7c5a` at:

`1440x900`, `1024x768`, `861x800`, `860x800`, `641x800`, `640x800`, `521x800`, `520x800`, `430x932`, `390x844`, `375x667`, `360x640`, `359x640`, and `320x568`.

All required Chromium/Playwright gates passed:

- Zero page-level horizontal overflow.
- A blocked-Google-Fonts sweep passed all 201 integer widths from 320 through 520. The minimum wordmark-to-CTA gap was 9.953125 px at width 321, with zero clipping or overflow.
- Zero visible decorative-vial pixels at every viewport, from 62,629 matching pixels in the protected source image.
- Exactly five App Store CTA destinations, all `https://apps.apple.com/app/id6767441916`.
- Correct image dimensions, non-empty alt text, one H1 per page, ordered headings, page language, accessible link names, keyboard order, and visible focus.
- Correct sticky CTA initial, shown, focused, and final-hidden states at both sides of the 641/640 breakpoint and every required mobile sentinel.
- Sixty-four fresh shown-focus-to-hidden sequences with zero console warnings or errors. Focus transferred to the final CTA when it was visible and to the sticky header CTA when scrolling upward, with no scroll jump. The prior intermittent aria-hidden warning did not recur.
- The 12-pixel promise eyebrow measured 4.714:1 contrast, passing the 4.5:1 requirement.
- Reduced-motion behavior removes reveal, sticky, button, and badge transitions and hover transforms.
- 200 percent and 400 percent reflow equivalents pass without page overflow.
- Privacy's wide table stays inside a named, focusable, locally scrollable region at 320 pixels.
- Privacy and Terms pass at 1440, 390, and 320 pixels.
- Zero failed requests, console warnings, console errors, page errors, or 4xx/5xx responses.
- Read-only server stopped cleanly and a post-stop probe confirmed it was no longer serving.

Screenshots and full measurements from that historical QA run are referenced repository-relatively at:

`.superpowers/sdd/block-08-creative-web-qa-2026-08-29/task-5-screenshots/`

The complete QA transcript is retained in:

`.superpowers/sdd/block-08-creative-web-qa-2026-08-29/task-5-report.md`

## Current Safari gate

On 2026-09-07, a clean local worktree at `9783950` received a bounded Safari 26.6 run on macOS 26.6. The retained screenshots support the visible desktop viewport, narrow viewport, and focus-ring state only. In the same manual session, the local Privacy and Terms pages loaded; those two observations do not have retained screenshots. The commit identity comes from the contemporaneous Git check, not from pixels in the images.

Retained external temporary evidence from that session, listed without machine-specific paths:

- `simplydose-safari-gate/desktop.png` — SHA-256 `183faa4be84938651fe887280d5a2cfd157837911382cd24ba71ce87a572fad2`
- `simplydose-safari-gate/narrow.png` — SHA-256 `92e85ca3c456c9db88b9eb4ffb0dd863cd1e73049b051a778d38ba8341d683d8`
- `simplydose-safari-gate/focus-option-tab.png` — SHA-256 `9dab5d2e88937558fab9808aa99cbeccc98d8482ebce6b08ae316e7b982c7bae`

This bounded Safari check supplements, rather than repeats, the exhaustive Chromium matrix above. It does not prove full-page clipping, keyboard input provenance, Reduce Motion, zoom, App Store handoff, or dashboard state. The candidate branch is now pushed, but it has not been published or deployed, and the legal/privacy/publication gates below remain unchanged.

## Publication owner gates

1. `privacy.html` says SimplyDose has no marketing website beyond the Privacy Policy page, while this branch is a marketing-site candidate. Joshua must approve legally reviewed wording and dates before publication.
2. The public App Store description, offer wording, subscription display names, and App Privacy label must be reconciled using `agents/reports/codex-block-08-creative-2026-08-29.md` before driving paid traffic.

The prior external-font gate is resolved at `af21c2c`: all website pages now use local system fonts and
contain no Google Fonts requests.

## Verification and non-fixes

- `git diff --check`: PASS.
- Source branch status after final QA: clean.
- The original final focus fix did not change reader-visible copy. Later checkpoint `17ccab6` made the
  separately reviewed Visit Summary period correction described above.
- `privacy.html`, `terms.html`, and the hero asset remained unchanged during the final focus fix.
- The current candidate branch is pushed; no website publication or deployment occurred.
- iOS build: not required because this branch contains static website HTML only.
- No substantive privacy or Terms edit, website publication, App Store edit, ad activation, purchase, or production mutation was performed.
