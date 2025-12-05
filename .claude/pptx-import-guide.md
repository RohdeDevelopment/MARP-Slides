# Importing PowerPoint (PPTX) Presentations

This guide documents how to convert a PPTX file to a MARP presentation while extracting and using embedded images.

## PPTX File Structure

PPTX files are ZIP archives containing XML and media files:
```
pptx-file.pptx/
├── ppt/
│   ├── slides/
│   │   ├── slide1.xml, slide2.xml, ...
│   │   └── _rels/
│   │       └── slide1.xml.rels (image references per slide)
│   ├── media/
│   │   └── image1.png, image2.jpeg, ... (all embedded images)
│   └── slideLayouts/, slideMasters/ (template images)
└── docProps/
    └── thumbnail.jpeg
```

## Step 1: Extract Text Content from Slides

Use this command to extract text from each slide:
```bash
unzip -p "presentation.pptx" "ppt/slides/slide1.xml" 2>/dev/null | sed 's/<[^>]*>//g' | tr -s ' \n' ' '
```

Repeat for each slide number (slide1.xml, slide2.xml, etc.).

To list all slides:
```bash
unzip -l "presentation.pptx" 2>/dev/null | grep "ppt/slides/slide"
```

## Step 2: Extract All Images

Create an assets folder and extract all media:
```bash
mkdir -p presentations/your-presentation/assets
unzip -j "reference/presentation.pptx" "ppt/media/*" -d presentations/your-presentation/assets/
```

## Step 3: Map Images to Slides

Check which images belong to which slides by examining the relationship files:
```bash
unzip -p "presentation.pptx" "ppt/slides/_rels/slide5.xml.rels" 2>/dev/null
```

This returns XML like:
```xml
<Relationship Id="rId2" Type=".../image" Target="../media/image24.png"/>
```

The `Target` shows which image file is used on that slide.

## Step 4: View Images to Understand Content

Use Claude Code's Read tool to view extracted images:
```
Read file: presentations/your-presentation/assets/image24.png
```

This helps identify:
- Screenshots that should be included
- Diagrams that need to be recreated or imported
- Contact photos
- Background images (usually from slide layouts, not needed)

## Step 5: Create MARP Presentation

### Folder Structure
```
presentations/your-presentation/
├── Presentation Name.md
├── contact-photo.jpg
└── assets/
    ├── screenshot1.png
    └── diagram.png
```

### Image References in MARP
```markdown
# Slide with image on right
<div class="msg-grid-2col">
<div class="msg-feature-box">
Content here
</div>
<div>

![w:550](./assets/screenshot.png)

</div>
</div>

# Full-width centered image
![w:1100 center](./assets/diagram.png)

# Contact photo (in msg-contact-layout)
<img src="./contact.jpg" alt="Name">
```

## Common Image Types in PPTX

| Image Type | Location | Action |
|------------|----------|--------|
| Slide content (screenshots, diagrams) | `ppt/slides/_rels/slideX.xml.rels` | Import to assets/ |
| Contact photos | Usually last slide | Copy as contact photo |
| Template backgrounds | `ppt/slideLayouts/` | Usually not needed (use msg theme) |
| Logos | `ppt/slideMasters/` | Not needed (msg theme has logo) |
| EMF/WMF files | Various | Usually template elements, skip |

## Restyling Considerations

When converting, evaluate each slide for restyling:

1. **Title slides**: Use `_class: title` with msg background
2. **Agenda slides**: Use `_class: agenda` with numbered list
3. **Content with bullet points**: Use `msg-card` or `msg-feature-box`
4. **Screenshots**: Keep and reference from assets/
5. **Diagrams**: Either import as image or recreate with cards/grids
6. **Chapter dividers**: Use `_class: chapter` with msg background
7. **Contact slides**: Use `_class: msg-contact-layout`

## Cleanup

After import, you can delete unused images from assets/:
- Template backgrounds (usually large files like image1-20)
- EMF files (vector graphics from templates)
- SVG logos (msg theme has its own)
- Duplicate/similar images

Keep only the content-specific images that appear in slide relationships.
