# Nibeg Pahlavi

**The first OpenType typeface to model Book Pahlavi's joining and ligature behaviour on its own palaeographic logic, rather than adapting Arabic's**

Version 0.9 (pre-release) · Built with HarfBuzz (GSUB/GPOS) · Planned licence: SIL Open Font License

## Why this project

Book Pahlavi is the cursive script of the Middle Persian Zoroastrian manuscript tradition. It has no dedicated Unicode block, and no existing typeface, to my knowledge, engineers its joining and ligature behaviour from the script's own rules.

Earlier efforts addressed the script's ligature complexity without solving this. Emily West and William Malandra's Khusro/Ardashir fonts pre-fragment glyphs onto keyboard keys, leaving the user to assemble joins manually, keystroke by keystroke: a solution predating OpenType shaping rather than an alternative to it. The one existing open-source Book Pahlavi font, Mehraban Book Pahlavi (Rosetta Type, 2023), does use OpenType shaping, but is architecturally an Arabic-script font: its GSUB tables register only the `arab`/`latn`/`DFLT` scripts, its joining and ligature rules operate entirely on Arabic Presentation Forms codepoints, and it has no mark-attachment positioning (GPOS) at all. Pahlavi's own joining behaviour and letter-merger patterns, documented across decades of Iranist palaeographic literature, are inherited from Arabic only where the two scripts happen to coincide, and patched by hand where they do not (e.g. dedicated glyphs for aleph, which Arabic lacks).

Nibeg Pahlavi (*nibēg*, "writing, scripture, book"; working name) is built the other way round: ligatures, variant forms, and joining rules are modelled directly on manuscript evidence and on the classification of ligatures and letter variants used in Middle Persian philology, then implemented as native GSUB/GPOS rules, not adapted from another script's shaping tables. Development builds on research begun in a 2024 MA thesis at Sapienza University of Rome and is a collaboration between the Project of Excellence based at Sapienza and the Ferdowsi Presidential Chair in Zoroastrian Studies at the University of California Irvine.

## Current status (v0.9)

Two-letter ligatures are implemented across the core letter set, together with initial and final forms and contextual spacing. Joining across longer sequences, further glyph coverage and kerning refinement are in progress.

## Technical approach

- **Ligatures and joining:** `rlig`, `rclt` and contextual substitutions in GSUB, built for Book Pahlavi's own joining rules rather than inherited from Arabic
- **Positioning:** GPOS for spacing and mark placement
- **Letter-identity handling:** graphically merged letters (gimel/daleth/yodh; aleph/heth) are disambiguated following established philological classification, resolved at the glyph level
- **Variants:** selectable via variation selectors and ZWJ/ZWNJ, so alternative manuscript forms remain reachable without altering the underlying text
- **Verification:** rendering tested with HarfBuzz

## Encoding note

Book Pahlavi is not yet encoded. For testing, glyphs are provisionally mapped onto the Inscriptional Pahlavi block (U+10B60–U+10B7F). This is a temporary arrangement and does not imply that the two scripts are equivalent. A proposal for a dedicated Book Pahlavi encoding is in preparation.

## Availability

The font is not yet available for download. It will be released under the SIL Open Font License once development reaches a stable stage, and this repository will be updated at that point.

## How to cite

Marruzzo, Cereti. *Nibeg Pahlavi: an OpenType typeface for Book Pahlavi*, version 0.9 (pre-release), 2026.

## Author

Andrea Marruzzo, Research Fellow, Dipartimento di Scienze dell'Antichità, Sapienza University of Rome.
Contact: amarruzzo@gmail.com

## Copyright

© 2026 Andrea Marruzzo. All rights are reserved until release. Screenshots and documentation may not be reused without permission.
