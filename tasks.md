# Folienmaster Migration Tasks

Open tasks for migrating PPTX reference to MARP Folienmaster.

## High Priority

### 1. Agenda Highlight
**Status:** ✅ Completed
**PPTX Reference:** Slide 14

Use `**bold**` to highlight current agenda item in red.

```markdown
<!-- _class: agenda -->

# Agenda

1. Erster Gliederungspunkt
2. **Zweiter hervorgehobener Gliederungspunkt**
3. Dritter Gliederungspunkt
```

---

### 2. 8-Person Contact Grid
**Status:** 🔧 Partial (currently 4 people)
**PPTX Reference:** Slide 27

Extend contact grid from 4 to 8 people.

**CSS changes:**
- Adjust `.msg-contact-grid` to support 2 rows of 4
- Reduce image/text sizes for 8-person layout

---

### 3. Timeline 8 Entries
**Status:** 🔧 Partial (currently 6)
**PPTX Reference:** Slide 45

Extend `timeline-extended` to support 8 entries in 2 rows.

**CSS changes:**
- Adjust spacing for 8 entries
- Consider `_class: timeline-8` variant

---

### 4. Steps Vertical Variant
**Status:** ❌ Missing
**PPTX Reference:** Slide 42

Add vertical layout for 6 steps (stacked vs horizontal).

**Proposed class:** `_class: steps-vertical`

---

## Medium Priority

### 5. Full-Bleed Image Slides
**Status:** ❌ Missing
**PPTX Reference:** Slides 33-34

Full-width background image with text overlay in corner.

**Proposed class:** `_class: image-full`

---

### 6. Image Row Below Columns
**Status:** ❌ Missing
**PPTX Reference:** Slide 30

Three text columns with image row below.

**Implementation:** Add example using existing multicolumn + image row

---

### 7. Full-Height Image Variants
**Status:** ❌ Missing
**PPTX Reference:** Slides 31-32

Large image taking 50% height on left/right side.

**CSS needed:** `.msg-image-left`, `.msg-image-right` layouts

---

## Low Priority / Nice to Have

### 8. Automotive Theme Examples
**Status:** 🔧 Partial
**PPTX Reference:** Slides 1-2, 10

Add explicit automotive-themed slide examples using `title-automotive.png` and `chapter-automotive.png`.

---

### 9. Accent Text in Titles
**Status:** 🔧 Partial
**PPTX Reference:** Slide 13

Document how to use `**bold**` for red emphasis in titles.

Currently works but not documented with example.

---

### 10. Subtitle Above Headline
**Status:** ❌ Missing (design decision)
**PPTX Reference:** Multiple slides

PPTX has "Optionaler Subtitle" appearing above headlines. Consider if needed for MARP.

---

## Completed ✅

- [x] Title slide (`_class: title`)
- [x] Chapter slide (`_class: chapter`)
- [x] Chapter numbered (`_class: chapter-numbered`) - red circle with white number, max-width 400px
- [x] Agenda slide (`_class: agenda`) - with highlight support using `**bold**`
- [x] End slide (`_class: end`)
- [x] Quote slide (`_class: quote`)
- [x] Steps slide (`_class: steps`)
- [x] Cycle/PDCA slide (`_class: cycle`)
- [x] Timeline slide (`_class: timeline`)
- [x] Timeline extended (`_class: timeline-extended`)
- [x] Statistics cards (`.msg-stat-card`)
- [x] Labels (`.msg-label` with colors)
- [x] Flow layout (`.msg-flow`)
- [x] Contact layout (`_class: msg-contact-layout`)
- [x] Multi-person contact (`.msg-contact-grid`)
- [x] Two/three column layouts (`div.multicolumn`)
- [x] Cards (`.msg-card`, `.msg-hero-card`, `.msg-feature-box`)
- [x] Grid layouts (`.msg-grid-2col`, `.msg-grid-3col`)
- [x] Table styling (automatic)
- [x] Footnotes (`div.footnote`)
- [x] Removed h1 divider underline (devider.png) - not used in new design
- [x] Image usage: `image14.jpeg` for title slides, `image20.jpeg` for chapter slides

---

## Reference Files

- **PPTX Content:** [.claude/pptx-slide-reference.md](.claude/pptx-slide-reference.md)
- **CSS Theme:** [themes/msg.css](themes/msg.css)
- **Examples:** [Folienmaster.md](Folienmaster.md)
- **Documentation:** [CLAUDE.md](CLAUDE.md)
