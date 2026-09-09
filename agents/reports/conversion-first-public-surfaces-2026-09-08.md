# Conversion-first website lane report

## Commits

- Base candidate: `b340674` (`website: prepare conversion-first product hub`)
- Review remediation: `e147704` (`website: address public surfaces review`)
- Legal-page font rollback: `87a00a1` (`website: retain legal page system fonts`)
- Remote-font removal: `af21c2c` (`website: remove remote font requests`)
- Compact-header fix: `4a59e1d` (`website: preserve compact header spacing`)
- Website correctness/accessibility checkpoint: `17ccab6` (`website: correct summary copy and table semantics`)

## Remediation

- Removed the legacy hero figure entirely. A reviewed final App Store capture set is now supplied on
  `docs/conversion-first-store-assets` at `f045e5b`, but it is not integrated into this website candidate;
  the website still presents no product screenshot or source image.
- Replaced the index shell's `min()` width with a `max-width` plus `calc()` width. The 320 px browser
  gate now compares `documentElement.scrollWidth` to `documentElement.clientWidth`.
- Added ordinary links from the history card to `tracking-template.html` and from the appointment card
  to `visit-summary.html`.
- Corrected account-deletion directions to `Profile → Manage My Data → Delete Account`.
- Removed the newly added Google Fonts requests from Privacy and Terms. Their legal wording remains
  unchanged and they use their existing system-font presentation.
- Removed all Google Fonts requests from the five marketing pages. They now use the local system-font
  stack, eliminating that third-party font-vendor request without changing page content.
- Fresh review found that three compact-page headers had no space between the wordmark and App Store
  CTA at 320 px. They now reuse the sibling page's 16 px navigation gap without changing copy or links.
- Corrected Visit Summary copy to match its 30-, 60-, and 90-day period selector, and replaced the
  printable template's faux table with a native semantic table without changing its visual geometry.

## Verification

- At a CDP-emulated 320 by 568 viewport, all seven HTML pages had one H1 and `scrollWidth ==
  clientWidth`; no element extended beyond the viewport.
- The index has no `assets/hero-phone.png` element, and both ordinary discovery links resolve in the
  browser DOM. The exact account-deletion route is present on `privacy-controls.html`.
- Browser console warnings/errors: none. `git diff --check`: PASS.
- The five marketing pages contain no `fonts.googleapis.com` or `fonts.gstatic.com` references and
  pass local HTTP checks at desktop, 390 px, and 320 px with visible keyboard focus and no console errors.
- The affected compact-page headers retain a measured 16 px wordmark-to-CTA gap at 320 px.
- Fresh 320 px screenshots were captured for all three affected pages. The full desktop, 390 px,
  and 320 px matrix, HTTP responses, sitemap entries, keyboard focus, and network checks passed with
  zero failed requests or remote font requests.
- At website source checkpoint `17ccab6`, focused HTML, internal-link, accessibility-role, responsive,
  print, and Playwright checks passed for `visit-summary.html` and `tracking-template.html`.

## Remaining gates

The reviewed final App Store capture set is supplied on a separate branch but is not integrated into
this website candidate. Any website-image integration requires its own reviewed change. Fresh independent
review, substantive legal review of the hosted Privacy wording, App Store Connect edits, and publication
remain owner-controlled. In particular, `privacy.html` still says SimplyDose has no marketing website
beyond the Privacy Policy page; that scope is false for this marketing-site candidate and remains an
owner/legal publication blocker.
