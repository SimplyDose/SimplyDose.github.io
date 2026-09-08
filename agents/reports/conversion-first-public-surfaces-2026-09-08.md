# Conversion-first website lane report

## Commits

- Base candidate: `b340674` (`website: prepare conversion-first product hub`)
- Review remediation: `e147704` (`website: address public surfaces review`)
- Legal-page font rollback: `87a00a1` (`website: retain legal page system fonts`)

## Remediation

- Removed the legacy hero figure entirely. No product screenshot or source image is presented until a
  reviewed product commit and conductor fixture can produce real synthetic-data proof.
- Replaced the index shell's `min()` width with a `max-width` plus `calc()` width. The 320 px browser
  gate now compares `documentElement.scrollWidth` to `documentElement.clientWidth`.
- Added ordinary links from the history card to `tracking-template.html` and from the appointment card
  to `visit-summary.html`.
- Corrected account-deletion directions to `Profile → Manage My Data → Delete Account`.
- Removed the newly added Google Fonts requests from Privacy and Terms. Their legal wording remains
  unchanged and they use their existing system-font presentation.
- Removed all Google Fonts requests from the five marketing pages. They now use the local system-font
  stack, eliminating that third-party font-vendor request without changing page content.

## Verification

- At a CDP-emulated 320 by 568 viewport, all seven HTML pages had one H1 and `scrollWidth ==
  clientWidth == 320`; no element extended beyond the viewport.
- The index has no `assets/hero-phone.png` element, and both ordinary discovery links resolve in the
  browser DOM. The exact account-deletion route is present on `privacy-controls.html`.
- Browser console warnings/errors: none. `git diff --check`: PASS.
- The five marketing pages contain no `fonts.googleapis.com` or `fonts.gstatic.com` references and
  pass local HTTP checks at desktop, 390 px, and 320 px with visible keyboard focus and no console errors.

## Remaining gates

Final App Store captures remain blocked on the reviewed Tasks 2 and 3 product commit and the
conductor-owned synthetic fixture. Fresh independent review, substantive legal review of the hosted
Privacy wording, App Store Connect edits, and publication remain owner-controlled. In particular,
`privacy.html` still says SimplyDose has no marketing website beyond the Privacy Policy page; that
scope is false for this marketing-site candidate and remains an owner/legal publication blocker.
