---
name: pptx
description: "Presentation creation, editing, and analysis. When Claude needs to work with presentations (.pptx files) for: (1) Creating new presentations, (2) Modifying or editing content, (3) Working with layouts, (4) Adding comments or speaker notes, or any other presentation tasks"
license: Proprietary. LICENSE.txt has complete terms
---

# PPTX Creation, Editing, and Analysis

## Overview

Work with .pptx files (PowerPoint presentations). Similar structure to DOCX - ZIP archives containing XML.

## Workflow Decision Tree

### Reading/Analyzing Content
- **Text extraction**: Extract slide content and notes
- **Raw XML access**: For layouts, themes, embedded media

### Creating New Presentation
Use **html2pptx** or direct OOXML creation

### Editing Existing Presentation
- **Simple changes**: Basic OOXML editing
- **Complex layouts**: Raw XML manipulation

## Reading Content

### Extract Presentation Structure
```bash
# Unpack presentation
python ooxml/scripts/unpack.py <file.pptx> <output_dir>

# Key files:
# ppt/slides/slide*.xml - Individual slides
# ppt/slideLayouts/ - Layout templates
# ppt/slideMasters/ - Master slides
# ppt/media/ - Images and media
# ppt/notesSlides/ - Speaker notes
```

## Creating New Presentations

### Using html2pptx
Convert HTML to PowerPoint format

**MANDATORY**: Read `html2pptx.md` before creating presentations

### Direct OOXML Creation
For complex presentations requiring precise control

**MANDATORY**: Read `ooxml.md` for OOXML structure

## Editing Existing Presentations

**Workflow:**
1. Read ooxml.md for presentation XML structure
2. Unpack: `python ooxml/scripts/unpack.py <file> <dir>`
3. Edit XML files directly or with custom scripts
4. Pack: `python ooxml/scripts/pack.py <dir> <file>`

## Key Components

### Scripts
- `ooxml/scripts/unpack.py` - Extract .pptx to XML
- `ooxml/scripts/pack.py` - Create .pptx from XML
- `ooxml/scripts/validate.py` - Validate OOXML structure

### References
- `html2pptx.md` - HTML to PowerPoint conversion guide
- `ooxml.md` - Complete OOXML editing guide
- `ooxml/schemas/` - XML schemas for validation

## Presentation Structure

### Slides (ppt/slides/)
- slide1.xml, slide2.xml, etc. - Individual slide content
- Each slide references a layout and master

### Layouts (ppt/slideLayouts/)
- Define reusable slide templates
- Control placeholder positions and types

### Masters (ppt/slideMasters/)
- Define overall theme and defaults
- Control fonts, colors, backgrounds

### Notes (ppt/notesSlides/)
- Speaker notes for each slide
- Separate XML file per slide

## Best Practices

1. **Preserve layout references** when editing slides
2. **Use existing layouts** when possible
3. **Validate** after modifications
4. **Test presentation** in PowerPoint after changes
5. **Back up** before major edits

## Common Tasks

### Add New Slide
1. Copy existing slide XML
2. Update slide number and relationships
3. Modify content while preserving structure
4. Update presentation.xml with new slide reference

### Change Slide Layout
1. Update layout reference in slide XML
2. Adjust content to fit new placeholders
3. Preserve content where compatible

### Add Media
1. Copy media file to ppt/media/
2. Create relationship in slide's .rels file
3. Reference media in slide XML

---

**Note**: This skill includes extensive OOXML documentation and schemas. Full presentation XML structure details are in bundled resources (ooxml.md, ooxml/schemas/).
