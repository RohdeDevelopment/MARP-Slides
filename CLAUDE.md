# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a custom Marp theme for creating presentations with msg corporate branding. It's an unofficial theme that provides slide templates with msg styling, colors, and layouts. The theme is built using CSS and leverages Marp's presentation framework to convert Markdown files into HTML presentations.

## Quick Reference: Slide Classes

| Class | Use For |
|-------|---------|
| (default) | Standard content slide |
| `title` | First slide with background |
| `chapter` | Section divider |
| `chapter-numbered` | Section with number (01, 02) |
| `agenda` | Numbered topic list |
| `quote` | Centered quote/keymessage |
| `quote-image` | Quote with background image |
| `steps` | Horizontal chevron process |
| `cycle-flow` | PDCA cycle diagram |
| `doughnut` | Ring chart (3 sections) |
| `timeline` | 3-event timeline |
| `timeline-extended` | 6-8 event timeline |
| `msg-contact-layout` | Contact (1-2 persons) |
| `msg-contact-layout-extended` | Contact (3-8 persons) |
| `end` | Closing slide |

## Development Workflow

### Preview Changes
Use the Marp extension in VSCode to preview slides. The extension is configured in [.vscode/settings.json](.vscode/settings.json) to load local theme files:
- `themes/msg.css` - msg corporate branding (primary)
- `themes/rohde-consulting.css` - Rohde Consulting variant

Changes to CSS files are reflected immediately in Marp preview (no build process needed).

### Export to HTML
Use Marp CLI or the VSCode extension to export presentations:
```bash
# If using Marp CLI (not currently in package.json, but can be installed):
# marp Folienmaster.md -o output.html --theme themes/msg.css
```

### Testing Changes
Open [Folienmaster.md](Folienmaster.md) in VSCode with the Marp extension to test theme changes. This file contains examples of all slide types.

### Importing from PowerPoint (PPTX)
See [.claude/pptx-import-guide.md](.claude/pptx-import-guide.md) for detailed instructions on converting PPTX files to MARP presentations, including how to extract text content and images from the source file.

## Architecture

### Theme System
The theme is implemented in a single CSS file [themes/msg.css](themes/msg.css) that:
- Imports the default Marp theme and extends it
- Uses CSS custom properties for msg brand colors (defined in `:root`)
- Leverages CSS classes and pseudo-elements to create different slide layouts
- Embeds SVG graphics as base64 data URIs for logos and decorative elements

### Slide Types
The theme supports multiple slide types activated via Marp's `<!-- _class: type -->` directive:

**Basic Slides:**
- **Standard slide**: Default layout with header, footer, pagination
- **Title slide** (`_class: title`): Landing page with large title, subtitle, and decorative circle
- **Chapter slide** (`_class: chapter`): Section divider with background image
  - **IMPORTANT**: The background image can crop long subtitles. If the `##` subtitle is longer than ~25 characters, use `<br>` to add a line break (e.g., `## Long subtitle text<br>continues here`)
- **Chapter numbered** (`_class: chapter-numbered`): Chapter slide with red circle containing chapter number (01, 02, etc.)
  - Number displayed in small red circle with white text above the title
  - Title and subtitle have max-width of 400px to prevent overlap with background image
- **Agenda slide** (`_class: agenda`): Numbered list with custom counter styling
  - Use `**bold**` to highlight the current agenda item in red
- **End slide** (`_class: end`): Closing slide similar to title slide

**Quote & Keymessage:**
- **Quote slide** (`_class: quote`): Centered italic text for quotes or key messages
  - Use `**bold**` to highlight key words in red
  - Add author/source as `## Author Name` below the quote
- **Quote image slide** (`_class: quote-image`): Quote with full background image and white box overlay
  - White box has rounded corners (top-right and bottom-right)
  - Use `![quote-bg](path)` for background image
  - Use `.quote-box` div with `#### Quote text` and paragraph for author

**Process & Data:**
- **Steps slide** (`_class: steps`): Horizontal chevron-shaped process steps
  - Each step is a chevron arrow shape with black border
  - Use numbered list with `**01**`, `**02**`, etc. for the chevron content
  - Use `**_04_**` (bold + italic) to highlight the active/current step with gradient fill
  - Add `<span class="step-arrow">▼</span>` for down arrow indicator
  - Add `<span class="step-label">Label</span>` for text below arrow
  - Use `step-arrow-active` and `step-label-active` classes for highlighted step
- **Cycle Flow** (`_class: cycle-flow`): Path-based PDCA with waypoint markers
  - Use `.msg-cycle-path` container with `.msg-cycle-waypoint` elements
  - Rounded rectangular track with monochromatic red circle markers (40%, 60%, 80%, 100% opacity)
  - Directional arrows integrated into the path showing clockwise flow
- **Doughnut Chart** (`_class: doughnut`): Ring chart with 3 sections
  - Use `.msg-doughnut` container with `.msg-doughnut-label` elements (`.label-1`, `.label-2`, `.label-3`)
  - Labels positioned around the ring with percentage (bold) + description text
  - **Variants:**
    - Default (no class): First section gradient highlight (teal→green→lime), others gray
    - `.gradients-b`: Petrol, Yellow, Pink gradients (Variante 1)
    - `.gradients-c`: Purple, Red, Green gradients (Variante 2)
- **Timeline slide** (`_class: timeline`): Horizontal timeline with 3 alternating events
- **Timeline extended** (`_class: timeline-extended`): Extended timeline for 6-8 events

### Layout Components

#### Core Components
- **msg logo**: Injected via `section::before` pseudo-element (different colors for different slide types)
- **Header**: Absolute positioned at top-left
- **Footer**: Absolute positioned at bottom-left
- **Pagination**: Injected via `section::after`
- **Footnotes**: Styled `div.footnote` element at bottom of slide
- **Columns**: `div.multicolumn` uses CSS Grid for multi-column layouts

#### Reusable Layout Components
Reusable layout components that can be used in any presentation without custom CSS:

**Grid Layouts:**
- `.msg-grid-2col`: 2-column grid layout with 20px gap
- `.msg-grid-3col`: 3-column grid layout with 20px gap

**Card Components:**
- `.msg-card`: Standard card with gradient background and top border accent (ideal for value propositions, features)
- `.msg-feature-box`: Feature box with bottom-bordered title and optional `.use-case` label (ideal for modes, categorized features)
- `.msg-hero-card`: Premium card with pink gradient, thick border, and top accent strip (for highlighted content)
  - Combine with `.msg-badge-number` for numbered badges in top-right corner
- `.msg-supporting-card`: Supporting card with left border accent (for secondary content)

**Section Components:**
- `.msg-section-container`: Container for sections with consistent spacing
- `.msg-section-intro`: Centered italic intro text for sections

**Contact Layout:**
- `<!-- _class: msg-contact-layout -->`: Full-page contact slide with split layout
  - `.msg-contact-left`: Left content area for contact person(s)
  - `.msg-contact-person`: Person container with circular image
  - `.msg-contact-info`: Info container with `.name`, `.role`, `.email` classes
  - `.msg-company-info`: Company information box
  - Background image: Use `![contact-bg h:720](path)` for right-side background

**Table Styling:**
- All tables automatically styled with msg branding (no class needed)
- First column bold and colored in msg-red
- Alternating row colors for readability

**Statistics & Labels:**
- `.msg-stat-card`: Card for displaying statistics/metrics with `.stat-number` and `.stat-label`
- `.msg-label`: Inline label/tag component with color variants (`.petrol`, `.yellow`, `.green`, `.purple`, `.pink`, `.gray`)

**Flow Layout:**
- `.msg-flow`: Container for start-to-end process flows
- `.msg-flow-start`, `.msg-flow-end`: Start and end point boxes
- `.msg-flow-arrow`: Arrow element between points

**Multi-Person Contact:**
- `.msg-contact-grid`: Grid layout for 4+ contact persons on one slide

### Brand Colors
Colors are defined as CSS custom properties (line 12-24 in msg.css):
- `--msg-red`: #A01441 (primary brand color)
- `--msg-dark-gray`: #6F6F6F
- `--msg-gray`: #ACACAC
- `--msg-petrol`: #139EAD
- `--msg-yellow`: #F5B510
- `--msg-green`: #70DC51
- `--msg-purple`: #5866E3
- `--msg-pink`: #D74B97

### Brand Guidelines (from Corporate Design)

**Typography:**
- **Primary font**: Open Sans (MARP) / Aptos (PowerPoint)
- **Headings**: Bold (700) for emphasis
- **Body text**: Light (300) or Regular (400)
- **Accent text**: First or second line of a headline can be set in red bold for emphasis

**Design Principles:**
- Use msg-red (#A01441) as primary accent color
- Maintain consistent spacing and padding
- 16:9 aspect ratio (1280x720px)
- Logo placement: top-right corner

### Asset Management
Images are stored in [themes/assets/](themes/assets/) and referenced in Markdown:

**Main Theme Assets:**
- `title-msg.png`: Background for title/end slides (standard msg)
- `title-automotive.png`: Background for automotive-themed title slides
- `chapter-msg.png`: Background for chapter slides (standard msg)
- `chapter-automotive.png`: Background for automotive-themed chapter slides
- `contact-msg.png`: Background for contact slide right side
- SVG logos are embedded as base64 in CSS to eliminate external dependencies

**Folienmaster Reference Images:**
The `themes/assets/folienmaster-reference/` folder contains extracted images from the corporate PPTX template:

| Image Range | Type | Description |
|-------------|------|-------------|
| `image1-12` | Decorative | Title/chapter backgrounds, logos, decorative elements |
| `image13-14, 20-24` | Backgrounds | Automotive theme backgrounds (high-quality photos) |
| `image25-30` | Backgrounds | Modern design backgrounds with gradients |
| `image31-42` | Content | Diagrams, illustrations, content images |
| `image43-87` | Icons | SVG icons and small graphics |

**Recommended Image Usage:**
- `image13.jpg` (1920x1080): Automotive title background
- `image30.png` (1280x720): Gradient background for custom slides
- `image25-28.png`: Modern design backgrounds with transparency

## Usage Pattern

Users copy the [themes/](themes/) folder to their project and add this frontmatter to their Markdown:
```markdown
---
marp: true
theme: msg
header: Header text
footer: Footer text
paginate: true
---
```

### Using Layout Components

**Example: Value Grid with Cards**
```markdown
# Features

<div class="msg-grid-2col">

<div class="msg-card">

#### Feature 1
- Benefit A
- Benefit B

</div>

<div class="msg-card">

#### Feature 2
- Benefit A
- Benefit B

</div>

</div>
```

**Example: Hero Cards with Numbered Badges**
```markdown
# Main Advantages

<div class="msg-section-container">
<div class="msg-section-intro">
Our key differentiators
</div>

<div class="msg-grid-2col">

<div class="msg-hero-card">
<div class="msg-badge-number">1</div>

#### Speed
- Fast implementation
- Quick results

</div>

<div class="msg-hero-card">
<div class="msg-badge-number">2</div>

#### Quality
- Automated testing
- Clean code

</div>

</div>
</div>
```

**Example: Contact Slide (1-2 persons)**

Use `msg-contact-layout` for 1-2 contact persons. Each presentation should have exactly ONE contact slide as the last slide before the end slide. The company info box on the right side is mandatory.

```markdown
<!-- _class: msg-contact-layout -->

# Contact

<div class="msg-contact-left">

<div class="msg-contact-person">
<img src="path/to/photo.jpg" alt="Name">
<div class="msg-contact-info">
<div class="name">Max Mustermann</div>
<div class="role">Position</div>
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
```

**Example: Contact Slide (up to 8 persons)**

Use `msg-contact-layout-extended` when you need to display up to 8 contact persons. The contacts are arranged in a 2x4 grid, vertically centered. The company info box remains on the right side.

```markdown
<!-- _class: msg-contact-layout-extended -->

# Ansprechpartner

<div class="msg-contact-grid-extended">

<div class="msg-contact-person">
<img src="path/to/photo1.jpg" alt="Person 1">
<div class="msg-contact-info">
<div class="name">Name Nachname</div>
<div class="role">Berufsbezeichnung</div>
<div class="email">name@msg.group</div>
</div>
</div>

<!-- Repeat for each contact person (up to 8) -->

</div>

![contact-bg h:720](themes/assets/contact-msg.png)

<div class="msg-company-info">

**msg systems ag**

Robert-Bürkle-Straße 1
85737 Ismaning

+49 89 96101-0

[info@msg.group](mailto:info@msg.group)

</div>
```

**Contact Slide Guidelines:**
- Every presentation must have exactly **one contact slide**
- Always include the **company info box** on the right side
- Always include the **background image** (`contact-bg`)
- Choose the appropriate layout based on number of contacts:
  - `msg-contact-layout`: 1-2 persons (larger photos, more detail)
  - `msg-contact-layout-extended`: 3-8 persons (compact grid layout)

**Example: Quote/Keymessage Slide**
```markdown
<!-- _class: quote -->

# Zitat oder **Keymessage** einfügen

## Dr. Jürgen Zehetmaier, Vorsitzender msg
```

**Example: Quote with Background Image**
```markdown
<!-- _class: quote-image -->

![quote-bg](themes/assets/folienmaster-reference/image28.png)

<div class="quote-box">

#### Zitat oder **Keymessage** einfügen

Optionaler Subtitle

</div>
```

**Example: Steps/Process Slide (Chevron Style)**
```markdown
<!-- _class: steps -->

# Headline with **bold keywords** possible

1. **01**
<span class="step-arrow">▼</span>
<span class="step-label">First Step</span>
2. **02**
<span class="step-arrow">▼</span>
<span class="step-label">Second Step</span>
3. **03**
<span class="step-arrow">▼</span>
<span class="step-label">Third Step</span>
4. **_04_**
<span class="step-arrow-active">▼</span>
<span class="step-label-active">Active Step</span>
5. **05**
<span class="step-arrow">▼</span>
<span class="step-label">Fifth Step</span>
```

**Example: PDCA Cycle Flow Slide**

The cycle-flow slide automatically applies:
- Monochromatic red waypoint markers (40%, 60%, 80%, 100% opacity progression)
- Directional arrows showing clockwise flow
- Rounded rectangular path layout

```markdown
<!-- _class: cycle-flow -->

# PDCA Zyklus

<div class="msg-cycle-path">

<div class="msg-cycle-waypoint">

#### Plan

Ziele definieren und Maßnahmen planen

</div>

<div class="msg-cycle-waypoint">

#### Do

Maßnahmen umsetzen

</div>

<div class="msg-cycle-waypoint">

#### Check

Ergebnisse prüfen und bewerten

</div>

<div class="msg-cycle-waypoint">

#### Act

Anpassungen vornehmen

</div>

</div>
```

**Example: Doughnut Chart Slide (Default with highlight)**
```markdown
<!-- _class: doughnut -->

# Headline with **bold keywords** possible

<div class="msg-doughnut">

<div class="msg-doughnut-label label-1">

**30%**

Ich bin ein kleines Label

</div>

<div class="msg-doughnut-label label-2">

**35%**

Ich bin ein kleines Label

</div>

<div class="msg-doughnut-label label-3">

**35%**

Ich bin ein kleines Label

</div>

</div>
```

**Example: Doughnut Chart Variante 1 (Petrol, Yellow, Pink)**
```markdown
<!-- _class: doughnut -->

# Doughnut Chart **Variante 1**

<div class="msg-doughnut gradients-b">
  <!-- same label structure as above -->
</div>
```

**Example: Doughnut Chart Variante 2 (Purple, Red, Green)**
```markdown
<!-- _class: doughnut -->

# Doughnut Chart **Variante 2**

<div class="msg-doughnut gradients-c">
  <!-- same label structure as above -->
</div>
```

**Example: Statistics Cards**
```markdown
<div class="msg-grid-3col">

<div class="msg-stat-card">
<div class="stat-number">29%</div>
<div class="stat-label">Beispieltext</div>
</div>

<div class="msg-stat-card">
<div class="stat-number">71%</div>
<div class="stat-label">Beispieltext</div>
</div>

</div>
```

**Example: Flow Layout**
```markdown
<div class="msg-flow">

<div class="msg-flow-start">

#### Startpunkt

Beschreibung

</div>

<div class="msg-flow-arrow">→</div>

<div class="msg-flow-end">

#### Endpunkt

Beschreibung

</div>

</div>
```

## Best Practices

### Presentation Structure (REQUIRED)

Every presentation created with this theme MUST:

1. **Use the msg theme**: Always set `theme: msg` in the frontmatter and reference [themes/msg.css](themes/msg.css)
2. **Start with a Title slide**: First slide must use `<!-- _class: title -->` with background image
3. **Include an Agenda slide**: Second slide must use `<!-- _class: agenda -->` with numbered topics
4. **End with a Contact slide**: Last slide must use `<!-- _class: msg-contact-layout -->` with contact information

**Required Presentation Template:**
```markdown
---
marp: true
theme: msg
header: Presentation Title
footer: © msg group | Presentation Title | 2025
paginate: true
---

<!-- _class: title -->

# Presentation Title
## Subtitle

![title h:720](themes/assets/title-msg.png)

---

<!-- _class: agenda -->

# Agenda

1. First Topic
2. Second Topic
3. Third Topic

---

[... content slides ...]

---

<!-- _class: msg-contact-layout -->

# Contact

<div class="msg-contact-left">

<div class="msg-contact-person">
<img src="path/to/photo.jpg" alt="Name">
<div class="msg-contact-info">
<div class="name">Contact Name</div>
<div class="role">Role/Position</div>
<div class="email">email@msg.group</div>
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
```

### When to Use Custom CSS vs Layout Components

**Use Layout Components (Preferred):**
- Standard grids, cards, and layouts
- Value propositions, features, comparisons
- Contact pages, approval sections
- Any presentation content that fits existing patterns

**Benefits:**
- No custom CSS needed in presentations
- Consistent styling across all presentations
- Easier maintenance
- Better theme portability

**Only Use Custom CSS When:**
- Creating completely new layout patterns not covered by existing components
- Implementing highly specialized, one-off designs
- Prototyping new components (consider adding to msg.css if reusable)

### Adding New Components to msg.css

When creating new reusable components:
1. Use the `msg-` prefix for all class names
2. Follow the existing naming convention (e.g., `msg-grid-*`, `msg-card-*`)
3. Use CSS custom properties for colors (`var(--msg-red)`, etc.)
4. Add to the appropriate section in msg.css with clear comments
5. Document in CLAUDE.md with usage examples
6. Test with [Folienmaster.md](Folienmaster.md) or create an example slide

## Presentation File Organization

### Folder Structure
Each presentation should be in its own folder under `presentations/`:
```
presentations/
├── marp-for-business/
│   ├── MARP for Business.md
│   └── moritz.jpg              # Contact photo
├── claude-vw/
│   ├── ClaudeCode VW.md
│   └── contact.jpg
└── ikos-poznan/
    ├── IKoS-Poznan.md
    └── moritz.jpg
```

### Asset References from Presentation Folders
When presentations are in `presentations/<name>/`, use relative paths to theme assets:
```markdown
![title h:720](../../themes/assets/title-msg.png)
![chapter h:720](../../themes/assets/chapter-msg.png)
![contact-bg h:720](../../themes/assets/contact-msg.png)
```

For local assets (contact photos), use relative paths within the folder:
```markdown
<img src="./moritz.jpg" alt="Name">
```

### Content Patterns by Audience

**For Non-Technical Audiences (Business, Sales):**
- Use simple language, avoid jargon
- Focus on benefits, not technical details
- Use `.msg-hero-card` with numbered badges for key takeaways
- Keep bullet points short (3-4 words each)
- Use chapter slides to create clear sections

**For Technical Audiences:**
- Can include more detail and terminology
- Use `.msg-feature-box` with `.use-case` labels for categorization
- Tables work well for comparisons
- Code examples can be included in standard slides

### Example: Feature Box with Use-Case Pattern
```markdown
<div class="multicolumn">

<div class="msg-feature-box">

#### Feature Name

- Benefit one
- Benefit two
- Benefit three

<div class="use-case">→ When to use this</div>

</div>

</div>
```

## Key Constraints

- The theme assumes 16:9 aspect ratio (1280px x 720px)
- Font is Open Sans loaded from Google Fonts
- Padding and positioning are absolute pixel values, not responsive
- Logo and decorative elements are base64-encoded to make the CSS file self-contained
- All layout components are defined in msg.css - presentations should NOT include custom CSS unless absolutely necessary

## Troubleshooting

| Issue | Solution |
|-------|----------|
| Theme not loading | Check `markdown.marp.themes` in `.vscode/settings.json` points to correct CSS path |
| Background image not showing | Verify image path is correct; use `![title h:720](path)` syntax with height |
| Chapter subtitle cropped | Add `<br>` for subtitles longer than ~25 characters |
| Pagination overlaps content | Check footer/header aren't too long; content may need adjustment |
| HTML elements not rendering | Ensure blank lines before/after HTML blocks in Markdown |
| Contact photo not circular | Use `<img>` inside `.msg-contact-person`, not Markdown `![]()` syntax |
