---
name: jaipur-living-docx-style
description: "Apply Jaipur Living's brand fonts, colors, and formatting to Microsoft Word documents (.docx). Use this skill whenever creating or editing Word documents for Jaipur Living, including reports, memos, proposals, letters, one-pagers, pricebooks, or any .docx deliverable. Triggers include: any request to create a Word document for Jaipur Living, any mention of 'brand formatting', 'Jaipur style', or 'on-brand document'. Also use when the user asks to standardize document output or apply brand styles. This skill works alongside the docx skill — use docx for the mechanics of creating/editing Word files, and this skill for the brand-specific styling decisions."
---

# Jaipur Living Word Document Style Guide

Apply these brand standards to every Word document created for Jaipur Living. This ensures visual consistency across all deliverables — reports, memos, proposals, pricebooks, presentations-as-docs, and internal communications.

## Color Palette

Use these exact hex values. The palette is clean and monochromatic, reflecting the professional presentation of Jaipur Living's brand materials.

### Primary Colors
| Name | Hex | RGB | When to Use |
|------|-----|-----|-------------|
| Black | #000000 | 0, 0, 0 | Body text, headings, table header backgrounds, primary fills |
| Pure White | #FFFFFF | 255, 255, 255 | Page backgrounds, text on dark backgrounds, table header text |

### Secondary Colors (Neutral Grays)
| Name | Hex | RGB | When to Use |
|------|-----|-----|-------------|
| Table Stripe | #D1D2D4 | 209, 210, 212 | Primary alternating table row shading |
| Light Stripe | #DBDCDE | 219, 220, 222 | Secondary alternating table row shading, subtle background fills |
| Border Gray | #D0D0D0 | 208, 208, 208 | Table borders, divider lines |

### Accent Colors (Internal Documents Only)
These warmer tones may be used sparingly in internal communications (memos, reports) but do **not** appear in customer-facing materials like pricebooks:

| Name | Hex | RGB | When to Use |
|------|-----|-----|-------------|
| Memo Red | #FF0000 | 255, 0, 0 | "MEMORANDUM: FOR INTERNAL USE ONLY" header text |
| Stone Gray | #7F8C8D | 127, 140, 141 | Captions, secondary text in internal docs |

## Typography

Jaipur Living uses a **Helvetica-family-only** type system. The brand typeface is Neue Haas Grotesk Display Pro for display/cover use, with Helvetica and Helvetica Neue for all other text. Arial serves as the system fallback when Helvetica is unavailable.

### Font Families
| Role | Font | Fallback | Why |
|------|------|----------|-----|
| Display/Cover Titles | Neue Haas Grotesk Display Pro (NHaasGroteskDSPro) | Helvetica, Arial | Premium brand typeface for high-visibility titles |
| Headlines & Section Titles | Helvetica Bold | Arial Bold | Clean, professional sans-serif |
| Subsection Headers | Helvetica Neue Medium (HelveticaNeue-Medium) | Helvetica, Arial | Slightly lighter weight for sub-headings |
| Body Text | Helvetica | Arial | Standard body copy |

### Type Scale for Word Documents
| Element | Font | Size (pt) | Weight | Color |
|---------|------|-----------|--------|-------|
| Display/Cover Title | NHaasGroteskDSPro-75Bd | 50 | Bold | Black #000000 |
| Cover Subtitle | NHaasGroteskDSPro-65Md | 15 | Medium | Black #000000 |
| Section Title (e.g. "Rugs") | Helvetica | 18 | Bold | Black #000000 |
| Heading 1 (e.g. T&C sections) | Helvetica | 11 | Bold | Black #000000 |
| Heading 2 (subsections) | Helvetica Neue Medium | 10 | Medium | Black #000000 |
| Body | Helvetica | 8 | Regular | Black #000000 |
| Table Header | Helvetica | 7 | Bold | White #FFFFFF |
| Table Body | Helvetica | 7 | Regular | Black #000000 |
| Table Body (collection name) | Helvetica | 7 | Bold | Black #000000 |
| Page Number | Helvetica | 14 | Regular | Black #000000 |
| Header/Footer Info | Helvetica | 9 | Regular/Bold | Black #000000 |
| Footnotes | Helvetica | 6 | Regular | Black #000000 |

**Note on docx-js**: Since Helvetica and Neue Haas Grotesk may not be available on all systems, use **Arial** as the font in docx-js code. Word will substitute Helvetica if installed; Arial provides a near-identical fallback.

## Document Layout Standards

### Page Setup — Portrait (Default)
- Page size: US Letter (8.5" x 11") — in DXA: width 12240, height 15840
- Margins: 1 inch all sides (1440 DXA each)
- Content width: 9360 DXA (for tables spanning full width)
- Use for: Cover pages, memos, letters, single-column reports

### Page Setup — Landscape Spread (Pricebooks & Catalogs)
- Page size: US Letter Landscape (11" x 8.5") — in DXA: width 15840, height 12240
- Use for: Product tables, pricebooks, catalogs, side-by-side layouts
- Product pages in the pricebook use a two-column table layout (two independent tables side by side)

### Spacing
- Body paragraph spacing: 6pt after
- Line spacing: 1.15 for body text
- Heading 1 spacing: 18pt before, 10pt after
- Heading 2 spacing: 14pt before, 8pt after

### Headers & Footers (Pricebook Style)
- **Header (left side)**: "Diamond" in Helvetica-Bold 9pt + "2026 Pricebooks" in Helvetica 9pt, left-aligned
- **Header (right side)**: Page number in Helvetica 14pt
- **Footer**: Footnote text ("*Only available in certain designs") in Helvetica 6pt

### Headers & Footers (General Documents)
- **Header**: "JAIPUR LIVING" in Arial 8pt, Black, right-aligned, with 200 character spacing
- **Footer**: Centered page number in Arial 8pt Black

## Table Formatting

Tables are a core element of Jaipur Living documents, especially pricebooks. Apply these standards:

- **Header row**: Black (#000000) background, white (#FFFFFF) text, Helvetica/Arial Bold 7pt
- **Body rows**: Alternating white and Table Stripe (#D1D2D4) for readability
- **Borders**: Light gray (#D0D0D0), single style, 1pt
- **Cell padding**: Top/bottom 80 DXA, left/right 120 DXA
- **Width**: Always use WidthType.DXA, never percentages
- **Shading**: Always use ShadingType.CLEAR, never SOLID
- **Collection name rows**: Use Helvetica/Arial Bold for the collection name cell within the table body

### Pricebook Table Columns
Standard pricebook tables use these columns:
| Column | Content | Alignment |
|--------|---------|-----------|
| CATALOG CODE | 3-letter product code (e.g. "AMI") | Left |
| COLLECTION NAME | Full name (e.g. "Amity") | Left |
| SIZE | Dimensions (e.g. "8x10", "18\"x18\"") | Left |
| SHAPE | RECTANGLE, SQUARE, RUNNER, ROUND | Left |
| DIAMOND / Tier Price | Wholesale price | Right |
| MAP | Minimum advertised price | Right |
| MSRP | Manufacturer's suggested retail price | Right |

Price values are formatted with dollar sign and comma separators (e.g. "$1,385"). Use "NA" for unavailable prices.

## Cover Page Pattern

Based on the actual pricebook cover format:

1. Large top spacing to center content visually on the page
2. Subtitle line: "2026 PRICEBOOKS" in Neue Haas Grotesk Medium (or Arial) 15pt, Black, centered or left-aligned
3. Title: "Diamond" (or document name) in Neue Haas Grotesk Bold (or Arial Bold) 50pt, Black
4. Clean layout — no decorative borders, dividers, or accent colors
5. Portrait orientation for cover page even if content pages are landscape

## docx-js Style Configuration

When creating new documents with docx-js, use this style block:

```javascript
const COLORS = {
  black: "000000",
  white: "FFFFFF",
  tableStripe: "D1D2D4",
  lightStripe: "DBDCDE",
  borderGray: "D0D0D0",
};

// Use in Document styles config:
styles: {
  default: { document: { run: { font: "Arial", size: 16, color: COLORS.black } } },
  paragraphStyles: [
    {
      id: "Heading1", name: "Heading 1", basedOn: "Normal", next: "Normal", quickFormat: true,
      run: { size: 22, bold: true, font: "Arial", color: COLORS.black },
      paragraph: { spacing: { before: 360, after: 200 }, outlineLevel: 0 },
    },
    {
      id: "Heading2", name: "Heading 2", basedOn: "Normal", next: "Normal", quickFormat: true,
      run: { size: 20, bold: true, font: "Arial", color: COLORS.black },
      paragraph: { spacing: { before: 280, after: 160 }, outlineLevel: 1 },
    },
    {
      id: "SectionTitle", name: "Section Title", basedOn: "Normal", next: "Normal", quickFormat: true,
      run: { size: 36, bold: true, font: "Arial", color: COLORS.black },
      paragraph: { spacing: { before: 200, after: 120 } },
    },
  ],
},
```

## Headers and Footers Template (General Documents)

```javascript
headers: {
  default: new Header({
    children: [new Paragraph({
      alignment: AlignmentType.RIGHT,
      children: [new TextRun({
        text: "JAIPUR LIVING",
        font: "Arial", size: 16, color: COLORS.black, characterSpacing: 200
      })],
    })],
  }),
},
footers: {
  default: new Footer({
    children: [new Paragraph({
      alignment: AlignmentType.CENTER,
      children: [
        new TextRun({ text: "Page ", font: "Arial", size: 16, color: COLORS.black }),
        new TextRun({ children: [PageNumber.CURRENT], font: "Arial", size: 16, color: COLORS.black }),
      ],
    })],
  }),
},
```

## Headers and Footers Template (Pricebook Style)

```javascript
headers: {
  default: new Header({
    children: [new Paragraph({
      children: [
        new TextRun({ text: "Diamond", bold: true, font: "Arial", size: 18, color: COLORS.black }),
        new TextRun({ text: "\n" }),
        new TextRun({ text: "2026 Pricebooks", font: "Arial", size: 18, color: COLORS.black }),
      ],
    })],
  }),
},
footers: {
  default: new Footer({
    children: [new Paragraph({
      children: [new TextRun({
        text: "*Only available in certain designs",
        font: "Arial", size: 12, color: COLORS.black,
      })],
    })],
  }),
},
```

## Pricebook Table Template

```javascript
const { Table, TableRow, TableCell, WidthType, ShadingType, AlignmentType, BorderStyle } = require('docx');

// Table header row
function createPricebookHeader() {
  const headers = ["CATALOG CODE", "COLLECTION NAME", "SIZE", "SHAPE", "DIAMOND", "MAP", "MSRP"];
  return new TableRow({
    tableHeader: true,
    children: headers.map(text => new TableCell({
      shading: { type: ShadingType.CLEAR, fill: COLORS.black },
      children: [new Paragraph({
        children: [new TextRun({
          text, bold: true, font: "Arial", size: 14, color: COLORS.white,
        })],
      })],
    })),
  });
}

// Alternating body rows
function createPricebookRow(data, rowIndex) {
  const fill = rowIndex % 2 === 0 ? COLORS.white : COLORS.tableStripe;
  return new TableRow({
    children: data.map((text, colIndex) => new TableCell({
      shading: { type: ShadingType.CLEAR, fill },
      children: [new Paragraph({
        alignment: colIndex >= 4 ? AlignmentType.RIGHT : AlignmentType.LEFT,
        children: [new TextRun({
          text,
          bold: colIndex === 0 || colIndex === 1, // catalog code and collection name bold
          font: "Arial", size: 14, color: COLORS.black,
        })],
      })],
    })),
  });
}
```

## Memo Template Pattern

The memo is the most common internal document format at Jaipur Living. When the user asks for a memo, meeting notes, action items, or internal communication, follow this structure exactly. A logo image is bundled with this skill at `assets/jaipur-living-logo.png` (760x84px PNG).

### Memo Layout

**Header area** (centered):
1. Jaipur Living logo image, centered, ~2.24 inches wide x ~0.25 inches tall (2842260 x 313985 EMU)
2. Below logo: "MEMORANDUM: FOR INTERNAL USE ONLY" in red (#FF0000), Arial 11pt, centered

**Metadata block** (immediately after header, no extra spacing):
- Each field on its own line, no blank lines between them
- Format: **LABEL**: Value (label is bold, value is regular weight)
- Standard fields in order: DATE, SUBJECT, AUDIENCE (or TO/FROM/CC as needed)
- Use Arial 11pt for the entire metadata block

**Body content**:
- One blank line after the metadata block
- Section headers: bold + underlined, Arial 11pt (e.g., "Key Action Items:")
- One blank line after each section header before content begins
- Bullet lists for action items, formatted as "Person -- task description"
- Use en-dash (\u2013) for person-task separator, not hyphens

**Page setup specific to memos**:
- Top margin: 1980 DXA (~1.375") to accommodate the logo header
- Right/bottom/left margins: 1440 DXA (1")
- Header distance: 720 DXA, Footer distance: 402 DXA

**Footer** (centered):
- "1800 Cherokee Parkway \u2013 Acworth, Georgia 30102" in Arial 11pt, centered

### Memo Code Example

```javascript
const fs = require('fs');
const {
  Document, Packer, Paragraph, TextRun, ImageRun,
  Header, Footer, AlignmentType, LevelFormat, PageNumber
} = require('docx');

const COLORS = {
  black: "000000",
  red: "FF0000",
};

// Load the logo from the skill assets folder
const logoPath = "<path-to-skill>/assets/jaipur-living-logo.png";
const logoData = fs.readFileSync(logoPath);

const doc = new Document({
  styles: {
    default: { document: { run: { font: "Arial", size: 22, color: COLORS.black } } },
  },
  numbering: {
    config: [{
      reference: "bullets",
      levels: [{
        level: 0, format: LevelFormat.BULLET, text: "\u2022",
        alignment: AlignmentType.LEFT,
        style: { paragraph: { indent: { left: 720, hanging: 360 } } },
      }],
    }],
  },
  sections: [{
    properties: {
      page: {
        size: { width: 12240, height: 15840 },
        margin: { top: 1980, right: 1440, bottom: 1440, left: 1440, header: 720, footer: 402 },
      },
    },
    headers: {
      default: new Header({
        children: [
          // Centered logo
          new Paragraph({
            alignment: AlignmentType.CENTER,
            children: [new ImageRun({
              type: "png",
              data: logoData,
              transformation: { width: 224, height: 25 },
              altText: { title: "Jaipur Living", description: "Jaipur Living logo", name: "Logo" },
            })],
          }),
          // Red memorandum line
          new Paragraph({
            alignment: AlignmentType.CENTER,
            children: [new TextRun({
              text: "MEMORANDUM: FOR INTERNAL USE ONLY",
              font: "Arial", size: 22, color: COLORS.red,
            })],
          }),
        ],
      }),
    },
    footers: {
      default: new Footer({
        children: [new Paragraph({
          alignment: AlignmentType.CENTER,
          children: [new TextRun({
            text: "1800 Cherokee Parkway \u2013 Acworth, Georgia 30102",
            font: "Arial", size: 22,
          })],
        })],
      }),
    },
    children: [
      // DATE field
      new Paragraph({
        spacing: { after: 80 },
        children: [
          new TextRun({ text: "DATE", bold: true, font: "Arial", size: 22 }),
          new TextRun({ text: ":  MM/DD/YY", font: "Arial", size: 22 }),
        ],
      }),
      // SUBJECT field
      new Paragraph({
        spacing: { after: 80 },
        children: [
          new TextRun({ text: "SUBJECT", bold: true, font: "Arial", size: 22 }),
          new TextRun({ text: ": Subject Line Here", font: "Arial", size: 22 }),
        ],
      }),
      // AUDIENCE field
      new Paragraph({
        spacing: { after: 80 },
        children: [
          new TextRun({ text: "AUDIENCE:", bold: true, font: "Arial", size: 22 }),
          new TextRun({ text: " Team Name", font: "Arial", size: 22 }),
        ],
      }),
      // Blank lines before content
      new Paragraph({ children: [] }),
      new Paragraph({ children: [] }),
      // Section header (bold + underlined)
      new Paragraph({
        children: [new TextRun({
          text: "Key Action Items:",
          bold: true, underline: { type: "single" },
          font: "Arial", size: 22,
        })],
      }),
      new Paragraph({ children: [] }),
      // Bullet items
      new Paragraph({
        numbering: { reference: "bullets", level: 0 },
        children: [new TextRun({ text: "Person \u2013 task description", font: "Arial", size: 22 })],
      }),
    ],
  }],
});

Packer.toBuffer(doc).then(buf => fs.writeFileSync("memo.docx", buf));
```

### Adapting the Memo for Different Uses

The memo template works for several document types with minor adjustments:

| Document Type | Metadata Fields | Sections |
|---------------|----------------|----------|
| Meeting Notes | DATE, SUBJECT, ATTENDEES | Key Decisions, Action Items, Next Steps |
| Action Items | DATE, SUBJECT, AUDIENCE | Action Items (by person), Timeline, Dependencies |
| Project Update | DATE, SUBJECT, TO/FROM | Status Summary, Completed, In Progress, Blockers |
| Internal Memo | DATE, SUBJECT, TO/FROM/CC | Background, Recommendation, Next Steps |

The header (logo + "MEMORANDUM: FOR INTERNAL USE ONLY") and footer (address) remain constant across all memo variants.

## Assets

This skill bundles the following files in the `assets/` directory:

- **jaipur-living-logo.png** — The Jaipur Living wordmark logo (760x84px, PNG with transparency). Use in memo headers and document cover pages. When using in docx-js, read with `fs.readFileSync()` and embed via `ImageRun` with `type: "png"`.

## Reminders

- This skill provides the *styling decisions*. For the technical how-to of building .docx files (lists, images, TOC, tracked changes, etc.), also read the docx skill.
- Always set page size explicitly to US Letter — docx-js defaults to A4.
- Keep documents clean and spacious. Jaipur Living's aesthetic is minimalist and professional.
- The brand palette is **monochromatic** (black, white, grays). Do not introduce earth tones, teals, or other accent colors into customer-facing documents.
- For internal memos, the only accent color is red (#FF0000) for the "MEMORANDUM" header line.
- When building pricebook/catalog tables, use landscape orientation and the two-column table layout pattern.
- The brand typeface is Helvetica/Neue Haas Grotesk — always use Arial as the docx-js fallback font.
