# PPTX Slide Reference for Migration

This document contains extracted content from `reference/m4a_Folienmaster_Präsentationsdesign_de.pptx` (46 slides) for step-by-step migration to Folienmaster.md.

## Migration Status Legend
- ✅ **Implemented** - Fully implemented in Folienmaster.md
- 🔧 **Partial** - Implemented but differs from PPTX
- ❌ **Missing** - Not yet implemented
- ⏭️ **Skip** - Not needed for MARP (info/reference only)

---

## Section 1: Title Slides (Slides 1-2, 10-13)

### Slide 1-2: Title (Automotive)
**Status:** ✅ Implemented
**MARP Class:** `_class: title`

**PPTX Content:**
```
msg for automotive
Folienmaster
```

**Current MARP:**
```markdown
<!-- _class: title -->

# Marp Theme msg
## Folienmaster - Alle Folienarten

![title h:720](themes/assets/title-msg.png)
```

**Migration Notes:**
- ✅ Title slide structure matches
- 🔧 PPTX uses "automotive" branding, MARP uses "msg" branding
- For automotive: use `title-automotive.png` background

---

### Slide 10: Title Branche Automotive
**Status:** ✅ Implemented (alternate background available)
**MARP Class:** `_class: title`

**PPTX Content:**
```
Titel
Branche Automotive (optional)
```

**Migration Notes:**
- Use `title-automotive.png` for automotive presentations

---

### Slide 11-12: Title with Subtitle
**Status:** ✅ Implemented
**MARP Class:** `_class: title`

**PPTX Content:**
```
Das ist eine Überschrift maximal zweizeilig
Subtitle einfügen
```

**Migration Notes:**
- ✅ Standard title slide with subtitle
- Two-line titles supported via line breaks

---

### Slide 13: Title with Accent Text
**Status:** 🔧 Partial
**MARP Class:** `_class: title`

**PPTX Content:**
```
Das ist eine Überschrift maximal zweizeilig
Subtitle einfügen
Es kann – je nach inhaltlicher Gewichtung – die erste oder zweite
Zeile der Überschrift in rot und Aptos Bold gesetzt werden.
```

**Migration Notes:**
- Use `**bold text**` in title for red emphasis (via CSS)
- Example: `# Das ist eine **Überschrift** maximal zweizeilig`

---

## Section 2: Corporate Design Info (Slides 3-9)

### Slide 3: General Information
**Status:** ⏭️ Skip (info only)

**PPTX Content:**
```
Optionaler Subtitle
Allgemeine Information
Die folgenden 7 Folien behandeln Grundlagen zum Corporate Design
und dürfen gelöscht werden.
```

---

### Slide 4: Bullet Points and Emphasis
**Status:** ⏭️ Skip (info only, documented in CLAUDE.md)

**PPTX Content:**
```
Aufzählungszeichen und Hervorhebungen
Textplatzhalter mit Fließtext Aptos 16 pt linksbündig, Hervorhebungen Aptos Bold
- Zweite Textebene
  - Dritte Textebene
    - Vierte Textebene
      - Fünfte Textebene

Um ein sauberes Arbeiten mit den Aufzählungszeichen zu ermöglichen,
bitte immer einen Textplatzhalter nutzen...
```

**Key Info for CLAUDE.md:**
- Font: Aptos 16pt (MARP uses Open Sans)
- Emphasis: Aptos Bold
- 5 levels of bullet points supported

---

### Slide 5: Fonts
**Status:** ⏭️ Skip (info only, documented in CLAUDE.md)

**PPTX Content:**
```
Schriften
Textplatzhalter mit Fließtext Aptos 16 pt light linksbündig,
Hervorhebungen Aptos Bold
Als zusätzlicher Schriftschnitt für Hervorhebungen kann Aptos auch kursiv gesetzt werden.
```

---

### Slide 6: Design Grid
**Status:** ⏭️ Skip (info only)

**PPTX Content:**
```
Das Gestaltungsraster
Das ist der Inhaltsbereich
Hier ist Platz für die Fußnote, 10 pt.
```

---

### Slide 7: Standard Colors
**Status:** ⏭️ Skip (documented in CLAUDE.md)

**PPTX Content:**
```
Standardfarben als Farbset für den Power Point Master.

Primärfarben für Text, Aufzählungspunkte und Hervorhebungen:
- Weiß #FFFFFF
- Schwarz #000000
- Mittelgrau #ACACAC
- Dunkelgrau #4A4A4A
- Rot #A01441

Sekundärfarben für komplexe Grafiken, Schaubilder und Diagramme:
- Petrol #1289A8
- Grün #70DC51

Zum Färben von Elementen bitte nur die 10 Designfarben verwenden.
```

**Migration Notes:**
- Already documented in CLAUDE.md
- CSS variables match these colors

---

### Slide 8: Footer Formatting
**Status:** ⏭️ Skip (info only)

**PPTX Content:**
```
Fußzeile formatieren
Um die Fußzeile zu formatieren, gehen Sie zu:
> Reiter Einfügen > Abschnitt Text > Kopf- und Fußzeile
```

---

### Slide 9: Grid for Photos
**Status:** ⏭️ Skip (info only)

**PPTX Content:**
```
Raster für austauschbare Fotos und abgerundete Ecken
Dieses 6 mm Raster kann zur schnellen und einfachen Positionierung
und Größenfestlegung der Bildinhalte verwendet werden...
```

---

## Section 3: Agenda (Slide 14)

### Slide 14: Agenda with Highlight
**Status:** 🔧 Partial (highlight not implemented)
**MARP Class:** `_class: agenda`

**PPTX Content:**
```
Agenda mit Highlight
01 Erster Gliederungspunkt
02 Zweiter hervorgehobener Gliederungspunkt  <-- HIGHLIGHTED
03 Dritter Gliederungspunkt
04 Vierter Gliederungspunkt
05 Fünfter Gliederungspunkt
06 Sechster Gliederungspunkt
07 Siebter Gliederungspunkt
```

**Current MARP:**
```markdown
<!-- _class: agenda -->

# Agenda

1. Titelfolien
2. Kapitelfolien
3. Inhaltsfolien
...
```

**Migration Notes:**
- ❌ Missing: Highlight effect for current agenda item
- Consider: Add `.highlight` class for emphasized items
- Consider: Add `<span class="highlight">` wrapper for highlighted items

**Proposed Implementation:**
```markdown
<!-- _class: agenda -->

# Agenda mit Highlight

1. Erster Gliederungspunkt
2. **Zweiter hervorgehobener Gliederungspunkt**
3. Dritter Gliederungspunkt
```

---

## Section 4: Chapter Slides (Slide 15)

### Slide 15: Chapter with Number
**Status:** ✅ Implemented
**MARP Class:** `_class: chapter-numbered`

**PPTX Content:**
```
01
Das ist ein neues Kapitel
Optionaler Untertitel
```

**Current MARP:**
```markdown
<!-- _class: chapter-numbered -->

<div class="chapter-number">01</div>

# Das ist ein neues Kapitel
## Optionaler Untertitel

![chapter-numbered h:720](themes/assets/chapter-msg.png)
```

**Migration Notes:**
- ✅ Fully implemented
- Number appears large on left side

---

## Section 5: Content Slides (Slides 16-22)

### Slide 16: Content with Bullets (1 Column)
**Status:** ✅ Implemented
**MARP Class:** (default)

**PPTX Content:**
```
Optionaler Subtitle
Ich bin eine Headline, in welcher manche wichtigen Begriffe auch fett geschrieben werden können.
Textplatzhalter mit Fließtext Aptos 16 pt light linksbündig
- Zweite Textebene
  - Dritte Textebene
    - Vierte Textebene
      - Fünfte Textebene
```

**Current MARP:**
```markdown
# Folie mit Stichpunkten

Textplatzhalter mit Fließtext
- Zweite Textebene
  - Dritte Textebene
    - Vierte Textebene
        - Fünfte Textebene
```

**Migration Notes:**
- ✅ Basic implementation exists
- 🔧 PPTX has "Optionaler Subtitle" above headline - not standard in MARP

---

### Slide 17: Two Columns
**Status:** ✅ Implemented
**MARP Class:** (default with `div.multicolumn`)

**PPTX Content:**
```
Optionaler Subtitle
Ich bin eine Headline, in welcher manche wichtigen Begriffe auch fett geschrieben werden können.

Linker Textplatzhalter          Rechter Textplatzhalter
- Zweite Textebene              - Zweite Textebene
  - Dritte Textebene              - Dritte Textebene
```

**Current MARP:**
```markdown
# Folie mit Text und zwei Spalten

Lorem ipsum...

<div class="multicolumn">

Linker Textplatzhalter...

Rechter Textplatzhalter...

</div>
```

**Migration Notes:**
- ✅ Two-column layout implemented

---

### Slide 18: Three Columns
**Status:** ✅ Implemented
**MARP Class:** (default with `div.multicolumn`)

**PPTX Content:**
```
Optionaler Subtitle
Ich bin eine Headline...

Linker Textplatzhalter    Mittlerer Textplatzhalter    Rechter Textplatzhalter
```

**Current MARP:**
```markdown
# Folie mit drei Spalten

<div class="multicolumn">

Linker Textplatzhalter...

Mittlerer Textplatzhalter...

Rechter Textplatzhalter...

</div>
```

**Migration Notes:**
- ✅ Three-column layout implemented

---

### Slides 19-22: Content with Images
**Status:** ✅ Implemented
**MARP Class:** (default with `div.multicolumn`)

**PPTX Content (various layouts):**
- Slide 19: Text left, image right (small)
- Slide 20: Text left, image right (medium)
- Slide 21: Image left, text right
- Slide 22: Large image with overlay text

**Current MARP:**
```markdown
# Text mit Bild

Lorem ipsum...

<div class="multicolumn">

Textplatzhalter mit Fließtext
- Zweite Textebene
- Dritte Textebene

![width:350px](https://picsum.photos/720?image=29)

</div>
```

**Migration Notes:**
- ✅ Basic text+image layouts implemented
- 🔧 Missing: Specific image-left/image-right variants
- 🔧 Missing: Full-width image with overlay

---

## Section 6: Quote Slides (Slides 23-26)

### Slides 23-24: Quote with Attribution
**Status:** ✅ Implemented
**MARP Class:** `_class: quote`

**PPTX Content:**
```
Zitat oder Keymessage einfügen
Dr. Jürgen Zehetmaier, Vorsitzender msg
```

**Current MARP:**
```markdown
<!-- _class: quote -->

# Zitat oder **Keymessage** einfügen

## Dr. Jürgen Zehetmaier, Vorsitzender msg
```

**Migration Notes:**
- ✅ Quote styling implemented
- ✅ Bold text in red (via `**text**`)
- ✅ Attribution via `##`

---

### Slides 25-26: Quote Variations
**Status:** ✅ Implemented

**PPTX Content:**
- Slide 25: Quote with attribution (different background)
- Slide 26: Quote with "Optionaler Subtitle" above

**Migration Notes:**
- ✅ Basic quote slide covers these variations

---

## Section 7: Contact Slides (Slides 27-28)

### Slide 27: Contact (8 People)
**Status:** 🔧 Partial
**MARP Class:** (default with `div.msg-contact-grid`)

**PPTX Content:**
```
Ansprechpartner & Ansprechpartnerinnen

[8 people with:]
Name Nachname
Berufsbezeichnung
name.nachname@msg.group
+49 171 12345678

msg for automotive GmbH
Robert-Bürkle-Straße 1
85737 Ismaning
+49 89 96101-0
+49 89 96101-1113
info@msg.group
```

**Current MARP:**
```markdown
# Ansprechpartner (Mehrere Personen)

<div class="msg-contact-grid">
[4 people shown]
</div>
```

**Migration Notes:**
- 🔧 Current implementation shows 4 people
- ❌ PPTX shows 8 people in grid layout
- Consider: Expand grid to support 8 contacts

---

### Slide 28: Contact (2 People with Background)
**Status:** ✅ Implemented
**MARP Class:** `_class: msg-contact-layout`

**PPTX Content:**
```
Ansprechpartner & Ansprechpartnerinnen

[2 people on left]
[Company info on right]
[Background image]
```

**Current MARP:**
```markdown
<!-- _class: msg-contact-layout -->

# Kontakt

<div class="msg-contact-left">
[Person info]
</div>

![contact-bg h:720](themes/assets/contact-msg.png)

<div class="msg-company-info">
[Company info]
</div>
```

**Migration Notes:**
- ✅ Layout matches PPTX

---

## Section 8: End Slide (Slide 29)

### Slide 29: Thank You
**Status:** ✅ Implemented
**MARP Class:** `_class: end`

**PPTX Content:**
```
Vielen Dank
```

**Current MARP:**
```markdown
<!-- _class: end -->

# Vielen Dank

![title h:720](themes/assets/title-msg.png)
```

**Migration Notes:**
- ✅ Fully implemented

---

## Section 9: Content with Images (Slides 30-34)

### Slide 30: Three Columns with Image Row
**Status:** 🔧 Partial

**PPTX Content:**
```
Optionaler Subtitle
Ich bin eine etwas längere Headline.

Linke Textbox          Mittlere Textbox          Rechte Textbox
Zweite Ebene           Zweite Ebene              Zweite Ebene

[Image row below]

Hinweis: Weitere Bilder können aus dem Bilderpool entnommen werden
```

**Migration Notes:**
- 🔧 Three-column text exists
- ❌ Missing: Image row below text columns
- Consider: Add example with images in separate row

---

### Slides 31-32: Text with Large Image
**Status:** 🔧 Partial

**PPTX Content:**
```
Optionaler Subtitle
Ich bin eine etwas längere Headline.

Textbox mit Fließtext
Zweite Ebene

[Large image on right/left side]
```

**Migration Notes:**
- 🔧 Basic text+image exists
- ❌ Missing: Full-height image variants

---

### Slides 33-34: Content with Background Image
**Status:** ❌ Missing

**PPTX Content:**
```
[Full-width background image]
[Text overlay in corner]
```

**Migration Notes:**
- ❌ No full-bleed image with text overlay in current implementation

---

## Section 10: Example Graphics Divider (Slide 35)

### Slide 35: Graphics Section Divider
**Status:** ⏭️ Skip

**PPTX Content:**
```
Beispielgrafiken
Subtitle einfügen
```

**Migration Notes:**
- This is just a section divider in the reference PPTX

---

## Section 11: Statistics (Slide 36)

### Slide 36: Percentage Statistics
**Status:** ✅ Implemented
**MARP Class:** (default with `.msg-stat-card`)

**PPTX Content:**
```
Optionaler Subtitle
Ich bin eine Headline...

29%               71%               71%
Beispieltext      Beispieltext      Beispieltext
```

**Current MARP:**
```markdown
# Statistik Cards

<div class="msg-grid-3col">

<div class="msg-stat-card">
<div class="stat-number">29%</div>
<div class="stat-label">Beispieltext</div>
</div>

...

</div>
```

**Migration Notes:**
- ✅ Implemented with `.msg-stat-card`

---

## Section 12: Map (Slide 37)

### Slide 37: Map with Locations
**Status:** ⏭️ Skip (too complex for MARP)

**PPTX Content:**
```
[Germany map with city markers]
Hamburg, Berlin, Görlitz, Braunschweig, Münster, Ismaning/München,
St. Georgen, Karlsruhe, Stuttgart, Ingolstadt, Passau, Nürnberg,
Frankfurt, Chemnitz, Lingen, Schortens/Wilhelmshaven, Hannover,
Düsseldorf, Essen, Köln, Dissen

7.000 Beispieltext
20.000 Beispieltext
500 Beispieltext
```

**Migration Notes:**
- ⏭️ Map graphics not suitable for MARP
- Use image export if map is needed

---

## Section 13: Table (Slide 38)

### Slide 38: Table with Labels
**Status:** ✅ Implemented
**MARP Class:** (default)

**PPTX Content:**
```
Optionaler Subtitle
Ich bin eine Headline...

        Label   Label   Label   Label   Label   Label   Label   Label
Label   Item    Item    Item    Item    Item    Item    Item    Item
Label   Item    Item    Item    Item    Item    Item    Item    Item
...
```

**Current MARP:**
```markdown
# Automatisches Tabellen-Styling

| Feature | Basic | Professional | Enterprise |
|---------|-------|--------------|------------|
| **Benutzer** | 5 | 50 | Unbegrenzt |
...
```

**Migration Notes:**
- ✅ Tables automatically styled
- ✅ First column bold and red

---

## Section 14: Labels (Slides 39-40)

### Slides 39-40: Content with Labels
**Status:** ✅ Implemented
**MARP Class:** (default with `.msg-label`)

**PPTX Content:**
```
Optionaler Subtitle
Ich bin eine Headline...

[Slide 40:]
Ich bin ein kleines Label    Ich bin ein kleines Label    Ich bin ein kleines Label
```

**Current MARP:**
```markdown
# Labels für Kategorisierung

<div class="msg-label">Standard</div>
<div class="msg-label petrol">Petrol</div>
<div class="msg-label yellow">Yellow</div>
...
```

**Migration Notes:**
- ✅ Label component implemented with color variants

---

## Section 15: Steps/Process (Slides 41-42)

### Slide 41: 5 Steps Horizontal
**Status:** ✅ Implemented
**MARP Class:** `_class: steps`

**PPTX Content:**
```
Optionaler Subtitle
Ich bin eine Headline...

01              02              03              04              05
Erste Textbox   Zweite Textbox  Dritte Textbox  Vierte Textbox  Fünfte Textbox
```

**Current MARP:**
```markdown
<!-- _class: steps -->

# Prozessschritte

1. **Erste Textbox**
Beschreibung
2. **Zweite Textbox**
Beschreibung
...
```

**Migration Notes:**
- ✅ Implemented with `_class: steps`

---

### Slide 42: 6 Steps Vertical
**Status:** 🔧 Partial
**MARP Class:** `_class: steps`

**PPTX Content:**
```
01 Beispieltext 1 mit zweiter Zeile
02 Beispieltext 2 mit zweiter Zeile
03 Beispieltext 3 mit zweiter Zeile
04 Beispieltext 4 mit zweiter Zeile
05 Beispieltext 5 mit zweiter Zeile
06 Beispieltext 6 mit zweiter Zeile
```

**Migration Notes:**
- 🔧 Current implementation is horizontal
- ❌ PPTX shows vertical layout for 6 items
- Consider: Add `_class: steps-vertical` variant

---

## Section 16: PDCA Cycle (Slide 43)

### Slide 43: PDCA Cycle
**Status:** ✅ Implemented
**MARP Class:** `_class: cycle`

**PPTX Content:**
```
Optionaler Subtitle
Ich bin eine Headline...

Plan                    Do
Beispieltext Plan       Beispieltext Do
mit zweiter Zeile       mit zweiter Zeile

Check                   Act
Beispieltext Check      Beispieltext Act
mit zweiter Zeile       mit zweiter Zeile
```

**Current MARP:**
```markdown
<!-- _class: cycle -->

# PDCA Zyklus

<div class="msg-cycle-container">

<div class="msg-cycle-item">

#### Plan
Beispieltext Plan mit zweiter Zeile

</div>

...

</div>
```

**Migration Notes:**
- ✅ Implemented with `_class: cycle`

---

## Section 17: Flow (Slide 44)

### Slide 44: Start-to-End Flow
**Status:** ✅ Implemented
**MARP Class:** (default with `.msg-flow`)

**PPTX Content:**
```
Optionaler Subtitle
Ich bin eine Headline...

Textbox am Startpunkt    →    Textbox am Endpunkt
Zweite Ebene                  Zweite Ebene
```

**Current MARP:**
```markdown
# Flow Layout

<div class="msg-flow">

<div class="msg-flow-start">

#### Startpunkt
Zweite Ebene

</div>

<div class="msg-flow-arrow">→</div>

<div class="msg-flow-end">

#### Endpunkt
Zweite Ebene

</div>

</div>
```

**Migration Notes:**
- ✅ Implemented with `.msg-flow`

---

## Section 18: Timeline (Slide 45)

### Slide 45: Timeline (8 Entries)
**Status:** 🔧 Partial
**MARP Class:** `_class: timeline-extended`

**PPTX Content:**
```
Optionaler Subtitle
Ich bin eine Headline...

[Year]          [Year]          [Year]          [Year]
Erste Textbox   Zweite Textbox  Dritte Textbox  Vierte Textbox
mit dritter Z.  mit dritter Z.  mit dritter Z.  mit dritter Z.

[Year]          [Year]          [Year]          [Year]
Fünfte Textbox  Sechste Textbox Siebte Textbox  Achte Textbox
mit dritter Z.  mit dritter Z.  mit dritter Z.  mit dritter Z.
```

**Current MARP (6 entries):**
```markdown
<!-- _class: timeline-extended -->

# Timeline (6 Einträge)

- <span>2018
Erste Textbox</span>
- <span>2019
Zweite Textbox</span>
...
```

**Migration Notes:**
- 🔧 Current implementation supports 6 entries
- ❌ PPTX shows 8 entries in 2 rows
- Consider: Extend CSS to support 8 entries

---

## Section 19: Icons Reference (Slide 46)

### Slide 46: Icons
**Status:** ⏭️ Skip (reference only)

**PPTX Content:**
```
Optionaler Subtitle
Icons
```

**Migration Notes:**
- Reference slide showing available icons
- Icons extracted to `themes/assets/folienmaster-reference/`

---

## Summary: Migration Priority List

### High Priority (Key differences)
1. **Agenda highlight** - Add highlight styling for current item
2. **8-person contact grid** - Extend from 4 to 8 people
3. **Timeline 8 entries** - Extend from 6 to 8 entries
4. **Steps vertical variant** - Add `_class: steps-vertical`

### Medium Priority (Nice to have)
5. **Full-bleed image slides** - Background image with text overlay
6. **Image row below columns** - Three columns with image row
7. **Full-height image variants** - Large image left/right

### Low Priority (Already covered)
8. Quote variations - Basic quote covers these
9. Content columns - Already implemented
10. Labels - Already implemented

### Skip (Not suitable for MARP)
- Map with locations (use image export)
- Corporate design info slides (documentation only)
- Icon reference (images extracted)
