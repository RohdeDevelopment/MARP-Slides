---
marp: true
theme: msg
header: Marp Theme msg
footer: © msg group | Marp Theme msg | 2025
paginate: true

---

<!-- _class: title -->

# Marp Theme msg

## Jan Tuttas

![title h:720](themes/assets/title-msg.png)

---

<!-- _class: agenda -->

# Agenda

1. Einführung
2. Folien mit Spalten
3. Layout-Komponenten
4. Tabellen & Spezialfolien

---

<!-- _class: chapter -->

# Einführung

## Optionaler Untertitel

![chapter h:720](themes/assets/chapter-msg.png)

---

# Folie erstellen

Folien werden mit --- getrennt

```markdown
# Folie 1

Ein bisschen Text für die erste Folie

---

# Folie 2

Dies ist der Text für Folie 2
```

--- 

# Folie mit Stichpunkten 

Textplatzhalter mit Fließtext
- Zweite Textebene
  - Dritte Textebene
    - Vierte Textebene
        - Fünfte Textebene

---

# Eine volle Folie mit einer zweizeiligen Überschrift benötigt ganz schön viel Text damit wir einen Zeilenumbruch haben

Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua. At vero eos et accusam et justo duo dolores et ea rebum. Stet clita kasd gubergren, no sea takimata sanctus est Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua. At vero eos et accusam et justo duo dolores et ea rebum. Stet clita kasd gubergren, no sea takimata sanctus est Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua. At vero eos et accusam et justo duo dolores et ea rebum. Stet clita kasd gubergren, no sea takimata sanctus est Lorem ipsum dolor sit amet.

Duis autem vel eum iriure dolor in hendrerit in vulputate velit esse molestie consequat, vel illum dolore eu feugiat nulla facilisis at vero eros et accumsan et iusto odio dignissim qui blandit praesent luptatum zzril delenit augue duis dolore te feugait nulla facilisi.

---

# Eine Folie mit vielen Überschriften

## Abschnitt 1
Duis autem vel eum iriure dolor in hendrerit in vulputate velit esse molestie consequat, ...

## Abschnitt 2
### Abschnitt 2.1
Duis autem vel eum iriure dolor in hendrerit in vulputate velit esse molestie consequat, ...

### Abschnitt 2.2
Duis autem vel eum iriure dolor in hendrerit in vulputate velit esse molestie consequat, ...

---

# Fußnoten

Lorem ipsum dolor sit amet¹, consetetur² sadipscing elitr³, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua. At vero eos et accusam et justo duo dolores et ea rebum. Stet clita kasd gubergren, no sea takimata sanctus est Lorem ipsum dolor sit amet.⁴

<div class=footnote>

1. Dies ist eine Fußnote und kann für Quellenangaben genutzt werden.
2. Info
3. Verweis
4. Eine weitere Quelle
</div>

---

<!-- _class: chapter -->

# Folien mit Spalten

## Optionaler Untertitel

![chapter h:720](themes/assets/chapter-msg.png)

---

# Folie mit Text und zwei Spalten

Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua. At vero eos et accusam et justo duo dolores et ea rebum. Stet clita kasd gubergren, no sea takimata sanctus est Lorem ipsum dolor sit amet.

<div class="multicolumn">
  Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua.

  Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua.
</div>

---

# Folie mit drei Spalten

<div class="multicolumn">
  Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua.

  Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua.

  Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua.
</div>

---

# Text mit zwei Spalten und Bild

Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua. At vero eos et accusam et justo duo dolores et ea rebum. Stet clita kasd gubergren, no sea takimata sanctus est Lorem ipsum dolor sit amet.

<div class="multicolumn">
  Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua.

  ![width:200px](https://picsum.photos/720?image=29)
</div>

---

<!-- _class: timeline -->

# Timeline

- <span>2014
Event 1</span>
- <span>2017
Event 2</span>
- <span>2021
Event 3</span>

---

<!-- _class: chapter -->

# Layout-Komponenten

## Wiederverwendbare Bausteine

![chapter h:720](themes/assets/chapter-msg.png)

---

# Cards im 2-Spalten-Grid

Ideal für Features, Benefits, Vergleiche

<div class="msg-grid-2col">

<div class="msg-card">

#### Feature A

- Erster Vorteil
- Zweiter Vorteil
- Dritter Vorteil

</div>

<div class="msg-card">

#### Feature B

- Erster Vorteil
- Zweiter Vorteil
- Dritter Vorteil

</div>

<div class="msg-card">

#### Feature C

- Erster Vorteil
- Zweiter Vorteil
- Dritter Vorteil

</div>

<div class="msg-card">

#### Feature D

- Erster Vorteil
- Zweiter Vorteil
- Dritter Vorteil

</div>

</div>

---

# Feature Boxes mit Use Cases

Perfekt für Modi, Kategorien, Optionen

<div class="multicolumn">

<div class="msg-feature-box">

#### Option 1

- Eigenschaft A
- Eigenschaft B
- Eigenschaft C

<div class="use-case">→ Für Anfänger geeignet</div>

</div>

<div class="msg-feature-box">

#### Option 2

- Eigenschaft A
- Eigenschaft B
- Eigenschaft C

<div class="use-case">→ Für Fortgeschrittene</div>

</div>

<div class="msg-feature-box">

#### Option 3

- Eigenschaft A
- Eigenschaft B
- Eigenschaft C

<div class="use-case">→ Für Experten</div>

</div>

</div>

---

# Hero Cards mit Nummern

Für Hauptvorteile und Highlights

<div class="msg-section-container">

<div class="msg-section-intro">
Die wichtigsten Vorteile unserer Lösung
</div>

<div class="msg-grid-2col">

<div class="msg-hero-card">
<div class="msg-badge-number">1</div>

#### Geschwindigkeit

- **Schnelle Implementierung** in Tagen statt Wochen
- Sofortige Ergebnisse
- Minimaler Aufwand

</div>

<div class="msg-hero-card">
<div class="msg-badge-number">2</div>

#### Qualität

- **Höchste Standards** eingehalten
- Geprüft und zertifiziert
- Langfristige Wartbarkeit

</div>

</div>

</div>

---

# 3-Spalten Hero Layout

Drei gleichwertige Punkte hervorheben

<div class="msg-grid-3col">

<div class="msg-hero-card">
<div class="msg-badge-number">1</div>

#### Punkt Eins

- Vorteil A
- Vorteil B
- Vorteil C

</div>

<div class="msg-hero-card">
<div class="msg-badge-number">2</div>

#### Punkt Zwei

- Vorteil A
- Vorteil B
- Vorteil C

</div>

<div class="msg-hero-card">
<div class="msg-badge-number">3</div>

#### Punkt Drei

- Vorteil A
- Vorteil B
- Vorteil C

</div>

</div>

---

<!-- _class: chapter -->

# Tabellen & Spezialfolien

## Weitere Elemente

![chapter h:720](themes/assets/chapter-msg.png)

---

# Automatisches Tabellen-Styling

Tabellen werden automatisch formatiert

| Feature | Basic | Professional | Enterprise |
|---------|-------|--------------|------------|
| **Benutzer** | 5 | 50 | Unbegrenzt |
| **Speicher** | 10 GB | 100 GB | 1 TB |
| **Support** | Email | Email & Chat | 24/7 Premium |
| **Preis** | 9€/Monat | 49€/Monat | Individuell |

Die erste Spalte ist automatisch fett und rot formatiert.

---

<!-- _class: msg-contact-layout -->

# Kontakt

<div class="msg-contact-left">

<div class="msg-contact-person">
<img src="https://via.placeholder.com/90" alt="Max Mustermann">
<div class="msg-contact-info">
<div class="name">Max Mustermann</div>
<div class="role">Themenverantwortlicher</div>
<div class="email">max.mustermann@msg.group</div>
</div>
</div>

</div>

![contact-bg h:720](themes/assets/contact-msg.png)

<div class="msg-company-info">

**msg systems ag**

Robert-Bürkle-Straße 1
85737 Ismaning

+49 89 96101-0

[info@msg.group](mailto:info@msg.group)

</div>

---

<!-- _class: end -->

# Vielen Dank

![title h:720](themes/assets/title-msg.png)
