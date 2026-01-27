# custom-marp-theme

A custom Marp theme for creating presentations with msg corporate branding. This is an unofficial theme that provides slide templates with msg styling, colors, and layouts.

## Quick Start

1. Copy the `themes/` folder to your project
2. Copy the `.vscode/` folder for VSCode Marp extension settings
3. Create your presentation with this frontmatter:

```markdown
---
marp: true
theme: msg
header: Presentation Title
footer: © msg group | Presentation Title | 2025
paginate: true
---
```

## Slide Types

| Class | Description |
|-------|-------------|
| (default) | Standard slide with header, footer, pagination |
| `title` | Landing page with large title and decorative circle |
| `chapter` | Section divider with background image |
| `agenda` | Numbered list with custom counter styling |
| `end` | Closing slide similar to title slide |
| `timeline` | Horizontal timeline with alternating events |
| `msg-contact-layout` | Contact slide with split layout |

### Example: Title Slide

```markdown
<!-- _class: title -->

# Presentation Title
## Subtitle

![title h:720](themes/assets/title-msg.png)
```

### Example: Chapter Slide

```markdown
<!-- _class: chapter -->

# Chapter Title
## Subtitle

![chapter h:720](themes/assets/chapter-msg.png)
```

## Usage

This theme is designed for AI-assisted presentation creation using **Claude Code**. The AI reads the theme documentation in [CLAUDE.md](CLAUDE.md) and generates presentations following msg corporate guidelines.

### Creating Presentations with Claude Code

1. Open this repository in VSCode with Claude Code
2. Ask Claude to create a presentation, e.g.:
   - *"Create a presentation about our new product launch"*
   - *"Convert this PPTX to Marp format"*
   - *"Create an agenda slide with 5 topics"*
3. Claude will create the presentation in the `presentations/` folder
4. Preview using the Marp VSCode extension

### Folder Structure

Presentations are stored in `presentations/` (gitignored, not pushed to the repository):

```
custom-marp-theme/
├── themes/                    # Theme files (shared)
│   ├── msg.css
│   └── assets/
├── presentations/             # Your presentations (gitignored)
│   ├── product-launch/
│   │   ├── product-launch.md
│   │   └── speaker-photo.jpg
│   └── quarterly-review/
│       └── quarterly-review.md
├── Folienmaster.md            # Reference examples
└── CLAUDE.md                  # AI instructions
```

Each presentation lives in its own subfolder with any local assets (photos, images). Theme assets are referenced via relative paths:

```markdown
![title h:720](../../themes/assets/title-msg.png)
```

### Manual Creation

You can also create presentations manually. Every presentation should include:

1. **Title slide** (`_class: title`) - First slide
2. **Agenda slide** (`_class: agenda`) - Second slide
3. **Content slides** - Your presentation content
4. **Contact slide** (`_class: msg-contact-layout`) - Last slide

See [Folienmaster.md](Folienmaster.md) for examples of all slide types.

## Layout Components

The theme includes reusable layout components:

### Grid Layouts
- `.msg-grid-2col` - 2-column grid
- `.msg-grid-3col` - 3-column grid

### Card Components
- `.msg-card` - Standard card with gradient background
- `.msg-feature-box` - Feature box with bordered title
- `.msg-hero-card` - Premium card with pink gradient (use with `.msg-badge-number`)
- `.msg-supporting-card` - Secondary content card

### Example: Cards in Grid

```markdown
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

## Brand Colors

Available CSS custom properties:
- `--msg-red`: #A01441 (primary)
- `--msg-dark-gray`: #6F6F6F
- `--msg-gray`: #ACACAC
- `--msg-petrol`, `--msg-yellow`, `--msg-green`, `--msg-purple`, `--msg-pink`

## Preview & Export

**Preview**: Use the Marp extension in VSCode - changes to `themes/msg.css` are reflected immediately.

**Export**: Use Marp CLI or VSCode extension:
```bash
marp Folienmaster.md -o output.html --theme themes/msg.css
```

## Documentation

See [CLAUDE.md](CLAUDE.md) for detailed documentation including:
- Complete slide type reference
- All layout components with examples
- Presentation structure guidelines
- File organization best practices

See [Folienmaster.md](Folienmaster.md) for examples of all slide types.