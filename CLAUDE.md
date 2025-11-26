# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a custom Marp theme for creating presentations with msg corporate branding. It's an unofficial theme that provides slide templates with msg styling, colors, and layouts. The theme is built using CSS and leverages Marp's presentation framework to convert Markdown files into HTML presentations.

## Development Workflow

### Preview Changes
Use the Marp extension in VSCode to preview slides. The extension is configured in [.vscode/settings.json](.vscode/settings.json) to load the local theme file:
```bash
# No build process needed - changes to themes/msg.css are reflected immediately in Marp preview
```

### Export to HTML
Use Marp CLI or the VSCode extension to export presentations:
```bash
# If using Marp CLI (not currently in package.json, but can be installed):
# marp Folienmaster.md -o output.html --theme themes/msg.css
```

### Testing Changes
Open [Folienmaster.md](Folienmaster.md) in VSCode with the Marp extension to test theme changes. This file contains examples of all slide types.

## Architecture

### Theme System
The theme is implemented in a single CSS file [themes/msg.css](themes/msg.css) that:
- Imports the default Marp theme and extends it
- Uses CSS custom properties for msg brand colors (defined in `:root`)
- Leverages CSS classes and pseudo-elements to create different slide layouts
- Embeds SVG graphics as base64 data URIs for logos and decorative elements

### Slide Types
The theme supports multiple slide types activated via Marp's `<!-- _class: type -->` directive:
- **Standard slide**: Default layout with header, footer, pagination
- **Title slide** (`_class: title`): Landing page with large title, subtitle, and decorative circle
- **Chapter slide** (`_class: chapter`): Section divider with background image
- **Agenda slide** (`_class: agenda`): Numbered list with custom counter styling
- **End slide** (`_class: end`): Closing slide similar to title slide
- **Timeline slide** (`_class: timeline`): Horizontal timeline with alternating events

### Layout Components

#### Core Components
- **msg logo**: Injected via `section::before` pseudo-element (different colors for different slide types)
- **Header**: Absolute positioned at top-left
- **Footer**: Absolute positioned at bottom-left
- **Pagination**: Injected via `section::after`
- **Footnotes**: Styled `div.footnote` element at bottom of slide
- **Columns**: `div.multicolumn` uses CSS Grid for multi-column layouts

#### Reusable Layout Components (NEW)
The theme now includes reusable layout components that can be used in any presentation without custom CSS:

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

### Brand Colors
Colors are defined as CSS custom properties (line 12-24 in msg.css):
- `--msg-red`: #A01441 (primary brand color)
- `--msg-dark-gray`: #6F6F6F
- `--msg-gray`: #ACACAC
- `--msg-petrol`, `--msg-yellow`, `--msg-green`, `--msg-purple`, `--msg-pink`: Additional accent colors

### Asset Management
Images are stored in [themes/assets/](themes/assets/) and referenced in Markdown:
- `title-msg.png`: Background for title/end slides
- `chapter-msg.png`: Background for chapter slides
- `chapter-automotive.png`, `title-automotive.png`: Alternative backgrounds
- SVG logos are embedded as base64 in CSS to eliminate external dependencies

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

**Example: Contact Slide**
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

**Company Name**

Address Line 1
Postal Code City

Phone
Fax

[email@msg.group](mailto:email@msg.group)

</div>
```

## Best Practices

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

## Key Constraints

- The theme assumes 16:9 aspect ratio (1280px x 720px)
- Font is Open Sans loaded from Google Fonts
- Padding and positioning are absolute pixel values, not responsive
- Logo and decorative elements are base64-encoded to make the CSS file self-contained
- All layout components are defined in msg.css - presentations should NOT include custom CSS unless absolutely necessary
