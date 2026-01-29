---
name: pdf-processing-pro
description: "Advanced PDF manipulation (OCR, forms, tables). Use this skill any time a user wants to: read, extract, merge, split, rotate, watermark, encrypt, decrypt, fill forms, extract tables, or perform OCR on PDF files"
license: Apache 2.0
---

# PDF Processing Pro

## Overview

Comprehensive PDF processing capabilities including OCR, form filling, table extraction, and document manipulation.

## Capabilities

### Document Manipulation
- **Merge PDFs**: Combine multiple PDFs into one
- **Split PDFs**: Extract pages or split into multiple files
- **Rotate pages**: Change page orientation
- **Add watermarks**: Text or image watermarks
- **Encrypt/Decrypt**: Password protection

### Content Extraction
- **OCR**: Extract text from scanned PDFs
- **Tables**: Extract tables to structured data
- **Images**: Extract embedded images
- **Text**: Extract searchable text content

### Form Processing
- **Fill forms**: Populate PDF form fields programmatically
- **Extract form data**: Read form field values
- **Analyze forms**: Detect form fields and structure

## Key Tools

### PyPDF2
Basic PDF manipulation (merge, split, rotate)

```python
from PyPDF2 import PdfReader, PdfWriter

# Merge PDFs
writer = PdfWriter()
for pdf in ['file1.pdf', 'file2.pdf']:
    reader = PdfReader(pdf)
    for page in reader.pages:
        writer.add_page(page)
writer.write('merged.pdf')
```

### Tesseract OCR
Extract text from scanned/image PDFs

```bash
# OCR a PDF
tesseract input.pdf output -l eng pdf

# Multi-language OCR
tesseract input.pdf output -l eng+por pdf
```

### Tabula/Camelot
Extract tables from PDFs

```python
import tabula

# Extract all tables
tables = tabula.read_pdf('document.pdf', pages='all')

# Extract specific area
tables = tabula.read_pdf('document.pdf', area=[0,0,100,100])
```

### pdftk
Advanced PDF toolkit

```bash
# Fill PDF form
pdftk form.pdf fill_form data.fdf output filled.pdf

# Rotate pages
pdftk input.pdf cat 1-endeast output rotated.pdf

# Add password
pdftk input.pdf output secured.pdf user_pw PASSWORD
```

## Workflows

### OCR Workflow
1. Check if PDF is searchable
2. If not, convert to images
3. Run OCR with Tesseract
4. Create searchable PDF

**Reference**: See `OCR.md` for detailed OCR guide

### Form Processing Workflow
1. Analyze form structure
2. Extract field names and types
3. Prepare form data
4. Fill form programmatically

**Reference**: See `FORMS.md` for form processing guide

### Table Extraction Workflow
1. Identify table pages
2. Extract with Tabula or Camelot
3. Clean and structure data
4. Export to CSV/Excel

**Reference**: See `TABLES.md` for table extraction guide

## Best Practices

1. **Test with sample pages** before processing entire document
2. **Preserve original files** - always work on copies
3. **OCR language selection** - specify correct language(s)
4. **Table extraction** - try both Tabula and Camelot for best results
5. **Form validation** - verify field names before filling

## Common Use Cases

### Merge Multiple PDFs
```python
# Simple merge
pdftk file1.pdf file2.pdf cat output merged.pdf
```

### Extract Specific Pages
```python
# Pages 1-5 and 10
pdftk input.pdf cat 1-5 10 output extracted.pdf
```

### OCR Scanned Document
```bash
# OCR with Portuguese + English
tesseract scan.pdf output -l por+eng pdf
```

### Extract Tables
```python
import tabula
df_list = tabula.read_pdf('report.pdf', pages='all')
for i, df in enumerate(df_list):
    df.to_csv(f'table_{i}.csv')
```

## Bundled Resources

### Documentation
- `OCR.md` - Complete OCR processing guide
- `FORMS.md` - PDF form handling guide
- `TABLES.md` - Table extraction guide

### Scripts
- `scripts/analyze_form.py` - Analyze PDF form structure

---

**Note**: This skill supports both Python (PyPDF2, tabula, camelot) and command-line tools (tesseract, pdftk). Ensure required tools are installed for full functionality.
