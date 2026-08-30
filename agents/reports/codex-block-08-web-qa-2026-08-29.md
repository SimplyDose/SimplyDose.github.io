# Block 08 Unpublished Website Candidate and QA

- **Branch:** `codex/block-08-web-qa`
- **Approved base:** `69451b4634c48c09b324f6dd06f490dbd3daa584`
- **Implementation commits:** `bb396b9`, `fc99105`, `269da70`, `e8f2d5e`, `23d7c5a`
- **Local technical result:** PASS
- **Publication result:** OWNER-GATED
- **Published, pushed, or deployed:** No
- **Production or authenticated dashboard mutations:** None

## What changed

Exactly three website source files changed:

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

Screenshots and full measurements are retained in:

`/Users/joshuamunger/Projects/SimplyDose/.codex-worktrees/block-07-integrated/.superpowers/sdd/block-08-creative-web-qa-2026-08-29/task-5-screenshots/`

The complete QA transcript is retained in:

`/Users/joshuamunger/Projects/SimplyDose/.codex-worktrees/block-07-integrated/.superpowers/sdd/block-08-creative-web-qa-2026-08-29/task-5-report.md`

## Narrow Safari residual

Safari desktop and native App Store handoff were verified on earlier website commits without activating Get, Redownload, or a purchase. During the final `e8f2d5e` rerun, Computer Use twice reported that the Mac was locked and could not unlock it automatically. Therefore no current-commit Safari responsive, zoom, sticky, legal-table, Reduce Motion, or App Store handoff result is claimed.

This is a tool-state residual permitted by the approved plan, not a Chromium PASS extrapolated to Safari. Repeat the bounded Safari checks after the Mac is unlocked and before publication.

## Publication owner gates

1. `privacy.html` says SimplyDose has no marketing website beyond the Privacy Policy page, while this branch is a marketing-site candidate. Joshua must approve legally reviewed wording and dates before publication.
2. `index.html` loads Google Fonts from Google. The current policy does not describe this website processing. Joshua must choose, with privacy review, whether to self-host fonts, remove them, or disclose the processing.
3. The public App Store description, offer wording, subscription display names, and App Privacy label must be reconciled using `agents/reports/codex-block-08-creative-2026-08-29.md` before driving paid traffic.

## Verification and non-fixes

- `git diff --check`: PASS.
- Source branch status after final QA: clean.
- Reader-visible website copy is unchanged by the final technical fixes.
- `privacy.html`, `terms.html`, and the hero asset remained unchanged during the final focus fix.
- iOS build: not required because this branch contains static website HTML only.
- No substantive privacy or Terms edit, website publication, App Store edit, ad activation, purchase, or production mutation was performed.
