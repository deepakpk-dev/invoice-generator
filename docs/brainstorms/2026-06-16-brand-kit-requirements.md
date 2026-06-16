---
date: 2026-06-16
topic: brand-kit
---

# Brand Kit — white-label branding for SwiftInvo invoices

## Summary

Add a **Brand Kit** to SwiftInvo's business settings so freelancers can make invoices look like their own brand instead of the shared default. A freelancer picks a preset look that sets layout, font pairing, and a default accent color, then optionally overrides accent color, font pairing, layout, and footer/thank-you text. The brand is saved once per business and applied to every invoice and its PDF.

## Problem Frame

Every SwiftInvo invoice currently renders with the same fixed identity: one ink-indigo accent, the Fraunces/Inter type pairing, and a single layout. A freelancer can add their logo and contact details, but the document still reads as "a SwiftInvo invoice" rather than "a Jane Doe Design invoice." For a tool meant as a shared free resource, that sameness is a ceiling on how professional and personal each user's invoices can feel — two unrelated freelancers send near-identical-looking documents. Branding is the difference between a generic template and something a freelancer is proud to put their name on.

## Key Decisions

- **Presets as starting points, all controls adjustable (Approach C).** A preset sets sensible defaults for layout + fonts + accent; the freelancer can then override each control individually. This avoids both the blank-canvas paralysis of fully independent controls and the boxed-in feeling of locked presets — important when most users of a free tool are not designers and a bad combination would make their invoice look worse than the default.
- **Brand is per-business, not per-invoice.** One freelancer carries one brand, set once in settings and applied to all invoices. Per-invoice branding overrides are out of scope.
- **Curated font pairings, not an arbitrary font picker.** Users choose from a small set of designed pairings rather than any font. Keeps the tool offline-friendly (a bounded set of font families) and guarantees every result is typographically coherent.
- **Single accent color, not a full palette.** One brand color drives the accent treatment everywhere it appears; multi-color theming (separate header/text/background colors) is out of scope.

## Requirements

**Brand controls**

- R1. A freelancer can choose a **preset look** from a small curated set (e.g. the current "Ledger", plus alternatives). Selecting a preset sets the layout, font pairing, and default accent color in one action.
- R2. A freelancer can set a **brand accent color**, overriding the preset default. The accent recolors the accent treatments across the invoice — at minimum the rule lines, totals emphasis, the status ink stamp, and the tally mark.
- R3. A freelancer can choose a **font pairing** from the curated set, overriding the preset default.
- R4. A freelancer can choose an **invoice layout** from the available layouts, overriding the preset default.
- R5. A freelancer can set custom **footer text** and a custom **thank-you line** that appear on the invoice in place of the defaults.
- R6. A freelancer can toggle off the **SwiftInvo mention in the web page footer** (the app chrome shown on screen, not the printed invoice).

**Persistence and application**

- R7. Brand Kit choices are saved per business (alongside the existing business profile) on the device, and persist across sessions.
- R8. Brand Kit choices apply automatically to the live preview and to every invoice without per-invoice setup.
- R9. The chosen accent color and any background/ink treatments render correctly in the exported PDF (colors are not dropped by the browser print path).
- R10. Brand Kit settings are included in the existing backup export and restored on import.

**Quality floor**

- R11. Any combination of preset, accent color, font pairing, and layout produces a legible, non-broken invoice — overrides cannot push the document into an unreadable or visually broken state.
- R12. When a freelancer has set no Brand Kit, invoices render exactly as they do today (the current default look is the implicit baseline preset).

## Acceptance Examples

- AE1. **Covers R1, R8.** Given a freelancer with no branding set, when they open the Brand Kit and select the "Bold Modern" preset, then the live preview immediately re-renders with that preset's layout, fonts, and accent, and the next new invoice opens already branded.
- AE2. **Covers R2, R9.** Given a freelancer who sets their accent color to their brand green, when they download the invoice as a PDF, then the rule lines, totals, ink stamp, and tally mark appear in that green in the saved PDF.
- AE3. **Covers R1, R3, R4.** Given a freelancer who selected a preset and then changed only the font pairing, when they revisit the Brand Kit, then the preset selection still reflects their starting point and the font override is shown as applied (a modified-preset state, not silently reset).
- AE4. **Covers R6.** Given a freelancer who toggles off the SwiftInvo footer mention, when they view the app, then the web page footer no longer shows the SwiftInvo line, while the printed invoice is unchanged (it never carried it).
- AE5. **Covers R12.** Given a freelancer who has never opened the Brand Kit, when they create an invoice, then it renders identically to the pre-feature default.

## Scope Boundaries

- Per-invoice branding overrides — brand is set once per business.
- Multiple saved brand profiles — one freelancer, one brand.
- Arbitrary font uploads or a free font picker — curated pairings only.
- Full multi-color palettes (separate header/body/background colors) — single accent color only.
- Removing SwiftInvo branding from the printed invoice/PDF — the invoice already carries none.

## Dependencies / Assumptions

- Builds on the existing business profile and its settings drawer, the existing logo upload, and the existing backup export/import — all already present in `index.html`.
- Assumes the curated font pairings load acceptably for the offline/static-hosting use case; the count and source of font families is a planning concern.
- Assumes the accent color is applied through the existing CSS accent variable(s), so most accent recoloring follows from a single source.

## Outstanding Questions

**Deferred to Planning**

- How many presets, layouts, and font pairings ship in v1, and what each one is.
- How the "modified preset" state (R3/AE3) is represented and shown to the user.
- The exact set of invoice elements the accent color touches beyond the named four, and whether any preset introduces background tints that also need print-color handling.
