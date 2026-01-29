---
name: docx
description: "Comprehensive document creation, editing, and analysis with support for tracked changes, comments, formatting preservation, and text extraction. When Claude needs to work with professional documents (.docx files)"
license: Proprietary. LICENSE.txt has complete terms
---

# DOCX Creation, Editing, and Analysis

## Overview

Work with .docx files (ZIP archives containing XML). Different workflows for creating, editing, and analyzing documents.

## Workflow Decision Tree

### Reading/Analyzing Content
- **Text extraction**: Use pandoc for markdown conversion
- **Raw XML access**: For comments, formatting, structure, media, metadata

### Creating New Document
Use **docx-js** workflow (JavaScript/TypeScript)

### Editing Existing Document
- **Simple changes**: Basic OOXML editing
- **Professional docs**: Redlining workflow (tracked changes)
- **Legal/Academic/Business**: Redlining workflow (required)

## Reading Content

### Text Extraction
```bash
# Convert to markdown with tracked changes
pandoc --track-changes=all input.docx -o output.md
```

### Raw XML Access
```bash
# Unpack document
python ooxml/scripts/unpack.py <file.docx> <output_dir>

# Key files:
# word/document.xml - Main content
# word/comments.xml - Comments
# word/media/ - Images and media
```

## Creating New Documents

Use **docx-js** library (JavaScript/TypeScript)

**MANDATORY**: Read `docx-js.md` completely before creating documents

**Workflow:**
1. Read docx-js.md for syntax and best practices
2. Create JS/TS file using Document, Paragraph, TextRun
3. Export with Packer.toBuffer()

## Editing Existing Documents

Use **Document library** (Python for OOXML)

**MANDATORY**: Read `ooxml.md` completely before editing

**Workflow:**
1. Read ooxml.md for Document library API
2. Unpack: `python ooxml/scripts/unpack.py <file> <dir>`
3. Edit with Document library (Python script)
4. Pack: `python ooxml/scripts/pack.py <dir> <file>`

## Redlining Workflow (Tracked Changes)

**Use for:** Professional, legal, academic, business documents

**Strategy:** Batch changes in groups of 3-10 for testing

## Key Components

### Scripts
- `ooxml/scripts/unpack.py` - Extract .docx to XML
- `ooxml/scripts/pack.py` - Create .docx from XML
- `ooxml/scripts/validate.py` - Validate OOXML structure
- `scripts/document.py` - Document library for editing
- `scripts/utilities.py` - Helper functions

### References
- `docx-js.md` - Complete docx-js library guide (~500 lines)
- `ooxml.md` - Complete OOXML editing guide (~600 lines)
- `ooxml/schemas/` - XML schemas for validation

### Templates
- `scripts/templates/` - XML templates for comments, extensions

## Best Practices

1. **Always read documentation completely** before working
2. **Test in batches** when making multiple changes
3. **Validate** after modifications
4. **Preserve formatting** unless explicitly changing
5. **Use redlining** for professional documents

## Dependencies

All required dependencies should be pre-installed. If missing:
- docx (JavaScript): npm install docx
- lxml (Python): pip install lxml

---

**Note**: This skill includes extensive documentation files (docx-js.md, ooxml.md) and XML schemas. For complete implementation details, refer to these bundled resources.
