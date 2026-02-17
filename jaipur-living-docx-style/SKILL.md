---
name: jaipur-living-docx-style
description: "Apply Jaipur Living's brand fonts, colors, and formatting to Microsoft Word documents (.docx). Use this skill whenever creating or editing Word documents for Jaipur Living, including reports, memos, proposals, letters, one-pagers, or any .docx deliverable. Triggers include: any request to create a Word document for Jaipur Living, any mention of 'brand formatting', 'Jaipur style', or 'on-brand document'. Also use when the user asks to standardize document output or apply brand styles. This skill works alongside the docx skill — use docx for the mechanics of creating/editing Word files, and this skill for the brand-specific styling decisions."
---

# Jaipur Living Word Document Style Guide

Apply these brand standards to every Word document created for Jaipur Living. This ensures visual consistency across all deliverables — reports, memos, proposals, presentations-as-docs, and internal communications.

## Color Palette

Use these exact hex values. The palette is inspired by the natural materials and earthy textures of Jaipur Living's handcrafted rugs.

### Primary Colors
| Name | Hex | RGB | When to Use |
|------|-----|-----|-------------|
| Jaipur Black | #151314 | 21, 19, 20 | Logo text, H1 headings, body text, table header backgrounds |
| Pure White | #FFFFFF | 255, 255, 255 | Page backgrounds, text on dark backgrounds |

### Secondary Colors (Earth Tones)
| Name | Hex | RGB | When to Use |
|------|-----|-----|-------------|
| Undyed Wool | #C4B7A6 | 196, 183, 166 | Decorative borders, divider lines, accent backgrounds |
| Natural Jute | #8B7355 | 139, 115, 85 | H3 headings, secondary accents, icons |
| Blanc de Blanc | #F5F3F0 | 245, 243, 240 | Alternating table row shading, subtle background fills |
| Angora | #D5C4A1 | 213, 196, 161 | Call-to-action highlights, warm accent backgrounds |

### Accent Colors
| Name | Hex | RGB | When to Use |
|------|-----|-----|-------------|
| Heritage Teal | #2C5F5D | 44, 95, 93 | H2 headings, sustainability content accents |
| Artisan Clay | #8B4513 | 139, 69, 19 | Heritage storytelling highlights |
| Stone Gray | #7F8C8D | 127, 140, 141 | Captions, secondary text, header/footer text |

## Typography

Jaipur Living uses a two-font system that balances heritage warmth with modern readability.

### Font Families
| Role | Font | Fallback | Why |
|------|------|----------|-----|
| Headlines & Titles | Georgia | Times New Roman | Serif warmth evokes heritage and craft tradition |
| Body Text & UI | Arial | Helvetica | Clean sans-serif ensures readability across platforms |

### Type Scale for Word Documents
| Element | Font | Size (pt) | Weight | Color |
|---------|------|-----------|--------|-------|
| Display/Cover Title | Georgia | 28-32 | Bold | Jaipur Black #151314 |
| Heading 1 | Georgia | 18 | Bold | Jaipur Black #151314 |
| Heading 2 | Georgia | 14 | Bold | Heritage Teal #2C5F5D |
| Heading 3 | Georgia | 12 | Bold | Natural Jute #8B7355 |
| Body | Arial | 11-12 | Regular | Jaipur Black #151314 |
| Caption/Footnote | Arial | 9-10 | Regular | Stone Gray #7F8C8D |
| Header/Footer | Arial | 8 | Regular | Stone Gray #7F8C8D |

## Document Layout Standards

### Page Setup
- Page size: US Letter (8.5" x 11") — in DXA: width 12240, height 15840
- Margins: 1 inch all sides (1440 DXA each)
- Content width: 9360 DXA (for tables spanning full width)

### Spacing
- Body paragraph spacing: 6pt after
- Line spacing: 1.15 for body text
- Heading 1 spacing: 18pt before, 10pt after
- Heading 2 spacing: 14pt before, 8pt after
- Heading 3 spacing: 10pt before, 6pt after

### Headers & Footers
- **Header**: "JAIPUR LIVING" in Arial 8pt, Stone Gray, right-aligned, with 200 character spacing
- **Footer**: Thin border on top (Undyed Wool #C4B7A6), centered page number in Arial 8pt Stone Gray

## Table Formatting

Tables are a common element in Jaipur Living documents. Apply these standards:

- **Header row**: Jaipur Black (#151314) background, white text, Arial bold
- **Body rows**: Alternating white and Blanc de Blanc (#F5F3F0) for readability
- **Borders**: Light gray (#D0D0D0), single style, 1pt
- **Cell padding**: Top/bottom 80 DXA, left/right 120 DXA
- **Width**: Always use WidthType.DXA, never percentages
- **Shading**: Always use ShadingType.CLEAR, never SOLID

## Cover Page Pattern

When a document warrants a cover page:

1. Large top spacing (~1.5 inches) to center content visually
2. "JAIPUR LIVING" in Arial, bold, 28pt, 300 character spacing, centered
3. Document title in Georgia, 22pt, Heritage Teal, centered
4. Decorative divider: bottom border in Undyed Wool (#C4B7A6)
5. Subtitle/date in Arial, 12pt, Stone Gray, centered

## docx-js Style Configuration

When creating new documents with docx-js, use this style block:

```javascript
const COLORS = {
  jaipurBlack: "151314",
  white: "FFFFFF",
  undyedWool: "C4B7A6",
  naturalJute: "8B7355",
  blancDeBlanc: "F5F3F0",
  angora: "D5C4A1",
  heritageTeal: "2C5F5D",
  artisanClay: "8B4513",
  stoneGray: "7F8C8D",
};

// Use in Document styles config:
styles: {
  default: { document: { run: { font: "Arial", size: 24, color: COLORS.jaipurBlack } } },
  paragraphStyles: [
    {
      id: "Heading1", name: "Heading 1", basedOn: "Normal", next: "Normal", quickFormat: true,
      run: { size: 36, bold: true, font: "Georgia", color: COLORS.jaipurBlack },
      paragraph: { spacing: { before: 360, after: 200 }, outlineLevel: 0 },
    },
    {
      id: "Heading2", name: "Heading 2", basedOn: "Normal", next: "Normal", quickFormat: true,
      run: { size: 28, bold: true, font: "Georgia", color: COLORS.heritageTeal },
      paragraph: { spacing: { before: 280, after: 160 }, outlineLevel: 1 },
    },
    {
      id: "Heading3", name: "Heading 3", basedOn: "Normal", next: "Normal", quickFormat: true,
      run: { size: 24, bold: true, font: "Georgia", color: COLORS.naturalJute },
      paragraph: { spacing: { before: 200, after: 120 }, outlineLevel: 2 },
    },
  ],
},
```

## Headers and Footers Template

```javascript
headers: {
  default: new Header({
    children: [new Paragraph({
      alignment: AlignmentType.RIGHT,
      children: [new TextRun({
        text: "JAIPUR LIVING",
        font: "Arial", size: 16, color: COLORS.stoneGray, characterSpacing: 200
      })],
    })],
  }),
},
footers: {
  default: new Footer({
    children: [new Paragraph({
      alignment: AlignmentType.CENTER,
      border: { top: { style: BorderStyle.SINGLE, size: 1, color: COLORS.undyedWool, space: 4 } },
      children: [
        new TextRun({ text: "Page ", font: "Arial", size: 16, color: COLORS.stoneGray }),
        new TextRun({ children: [PageNumber.CURRENT], font: "Arial", size: 16, color: COLORS.stoneGray }),
      ],
    })],
  }),
},
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
  jaipurBlack: "151314",
  red: "FF0000",
  stoneGray: "7F8C8D",
};

// Load the logo from the skill assets folder
const logoPath = "<path-to-skill>/assets/jaipur-living-logo.png";
const logoData = fs.readFileSync(logoPath);

const doc = new Document({
  styles: {
    default: { document: { run: { font: "Arial", size: 22, color: COLORS.jaipurBlack } } },
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
- Keep documents clean and spacious. Jaipur Living's aesthetic values generous white space.
- When in doubt about a color choice, lean toward the earth tones (Undyed Wool, Natural Jute, Blanc de Blanc) — they reflect the brand's connection to natural materials.
