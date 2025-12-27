# RAG Fictitious Knowledge Base

A static, multilingual website containing **entirely fictional content** designed to evaluate Retrieval-Augmented Generation (RAG) systems.

[![Live Site](https://img.shields.io/badge/Live%20Site-GitHub%20Pages-blue)](https://dyrd-odoo.github.io/rag-fictitious-knowledge-base/)
[![Rendered Docs](https://img.shields.io/badge/Rendered%20Docs-DOCX%20|%20PDF%20|%20TXT-green)](https://github.com/dyrd-odoo/rag-fictitious-knowledge-base/tree/rendered-artifacts/rendered-docs)

## ⚠️ Important Notice

- All entities, events, metrics, and facts are **fictional**
- This repository exists solely for AI retrieval and grounding evaluation
- No content should be interpreted as real-world information

## 🌐 Available Languages

The knowledge base is available in four languages:

- **English** - [View HTML](https://dyrd-odoo.github.io/rag-fictitious-knowledge-base/languages/en/basic-tests.html)
- **Français** - [View HTML](https://dyrd-odoo.github.io/rag-fictitious-knowledge-base/languages/fr/basic-tests.html)
- **Português** - [View HTML](https://dyrd-odoo.github.io/rag-fictitious-knowledge-base/languages/pt/basic-tests.html)
- **العربية (Arabic)** - [View HTML](https://dyrd-odoo.github.io/rag-fictitious-knowledge-base/languages/ar/basic-tests.html)

## 📄 Pre-rendered Documents

All HTML files are automatically converted to multiple formats for easy integration with AI systems:

**[→ Browse Rendered Documents](https://github.com/dyrd-odoo/rag-fictitious-knowledge-base/tree/rendered-artifacts/rendered-docs)**

### Available Formats

Each language document is available in three formats:

- **DOCX** - Microsoft Word format for Odoo AI agents and document processors
- **PDF** - Portable format with proper RTL support for Arabic
- **TXT** - Plain text format for simple text processing

### File Naming Convention

Files follow the pattern: `{language}_{filename}.{extension}`

Examples:
- `en_basic-tests.pdf`
- `ar_basic-tests.docx`
- `pt_basic-tests.txt`
- `fr_basic-tests.pdf`

### Direct Download Links

You can download individual files directly from the `rendered-artifacts` branch:

```
https://github.com/dyrd-odoo/rag-fictitious-knowledge-base/raw/rendered-artifacts/rendered-docs/{filename}
```

Example:
```
https://github.com/dyrd-odoo/rag-fictitious-knowledge-base/raw/rendered-artifacts/rendered-docs/en_basic-tests.pdf
```

## 🎯 Intended RAG Use Cases

This knowledge base is designed for testing:

- **Document ingestion** - Chunking strategies and preprocessing
- **Semantic vs keyword retrieval** - Compare different search approaches
- **Multi-hop reasoning** - Questions requiring information from multiple sections
- **Grounded question answering** - Answers must cite source documents
- **Hallucination detection** - System behavior when answers are absent
- **Cross-language retrieval** - Consistency across translations

## 🏢 Fictional Domain Overview

The knowledge base centers around **Orion Analytics Group (OAG)**, a fictional AI research lab located in the fictional city of **Nova Cascadia**.

### Key Fictional Elements

- **Company**: Orion Analytics Group (OAG)
- **Founder**: Dr. Helena Voss (fictional researcher)
- **Location**: Nova Cascadia (fictional city)
- **Technology**: LUMA Index (fictional evaluation metric)
- **Event**: Nova Cascadia Incident (fictional RAG system failure in 2034)
- **Divisions**: 
  - Astra (data ingestion & embeddings)
  - Kepler (retrieval algorithms)
  - Atlas (evaluation & hallucination detection)

## 🚀 Quick Start

### For RAG Testing

1. Choose your preferred format (HTML, PDF, DOCX, or TXT)
2. Download from the [rendered documents](https://github.com/dyrd-odoo/rag-fictitious-knowledge-base/tree/rendered-artifacts/rendered-docs)
3. Ingest into your RAG system
4. Test with questions from [test-questions/basic-tests.md](test-questions/basic-tests.md)

### Test Questions

**📝 Complete test suite available:** [test-questions/basic-tests.md](test-questions/basic-tests.md)

The test suite includes 21 questions covering:
- Simple fact retrieval (Q1-Q3)
- Entity-attribute mapping (Q4-Q7)
- Concept understanding (Q8-Q11)
- Event-based retrieval (Q12-Q14)
- Multi-hop reasoning (Q15-Q17)
- Hallucination detection (Q18-Q19)
- Meta-awareness (Q20-Q21)

**Sample questions:**

**Basic Retrieval:**
- Where is Orion Analytics Group headquartered? → *Nova Cascadia*
- What does the Astra division focus on? → *Data ingestion and embeddings*

**Multi-hop Reasoning:**
- Which division would prevent future incidents like Nova Cascadia? → *Atlas (handles evaluation and hallucination detection)*

**Hallucination Detection:**
- How many employees work at Orion Analytics Group? → *Not specified* (correct answer is to acknowledge missing info)

See the [full test suite](test-questions/basic-tests.md) for all questions, expected answers, and evaluation guidelines.

## 🔄 Automatic Document Rendering

This repository includes a GitHub Actions workflow that automatically:

1. Detects changes to HTML files
2. Converts them to DOCX, PDF, and TXT formats
3. Commits the rendered files to the `rendered-artifacts` branch
4. Maintains proper Arabic/RTL support in PDFs

### Workflow Details

- **Trigger**: Automatically on push to any `.html` file, or manually via Actions tab
- **Processing**: Uses Pandoc with XeLaTeX for high-quality conversion
- **Arabic Support**: Includes DejaVu Sans font with bidirectional text support
- **Output**: Flattened directory structure in `rendered-docs/` folder

## 📁 Repository Structure

```
.
├── index.html              # Language selector homepage
├── languages/
│   ├── en/
│   │   └── basic-tests.html
│   ├── fr/
│   │   └── basic-tests.html
│   ├── pt/
│   │   └── basic-tests.html
│   └── ar/
│       └── basic-tests.html
├── .github/
│   └── workflows/
│       └── render-html.yml # Auto-rendering workflow
├── sitemap.xml
├── robots.txt
└── README.md
```

## 🛠️ Contributing

To add new content:

1. Edit or add HTML files under `languages/`
2. Commit and push changes
3. The workflow automatically generates DOCX, PDF, and TXT versions
4. Rendered files appear in the `rendered-artifacts` branch within minutes

## 📋 Technical Notes

### Font Support
- English, French, Portuguese: Standard Latin fonts
- Arabic: DejaVu Sans with bidirectional text support

### PDF Generation
- Engine: XeLaTeX via Pandoc
- Arabic PDFs: Automatic RTL detection and proper font handling
- Margins: 1 inch on all sides

### File Exclusions
- `index.html` is excluded from rendering (navigation page only)
- Only files under `languages/` directory are processed

## 📜 License

This is a fictional knowledge base for testing purposes. All content is intentionally fabricated and should not be used as factual information.

## 🔗 Links

- **Live Website**: https://dyrd-odoo.github.io/rag-fictitious-knowledge-base/
- **Rendered Documents**: https://github.com/dyrd-odoo/rag-fictitious-knowledge-base/tree/rendered-artifacts/rendered-docs
- **Workflow File**: [.github/workflows/render-html.yml](.github/workflows/render-html.yml)

---

**Created for RAG system testing and evaluation** • Hosted on GitHub Pages
