# Usage Guide: Rendered Documents

This guide explains how to use the pre-rendered documents from this repository with various AI and RAG systems.

## Quick Access

**Browse all rendered files**: https://github.com/dyrd-odoo/rag-fictitious-knowledge-base/tree/rendered-artifacts/rendered-docs

## Available Files

| Language | DOCX | PDF | TXT |
|----------|------|-----|-----|
| English | `en_basic-tests.docx` | `en_basic-tests.pdf` | `en_basic-tests.txt` |
| French | `fr_basic-tests.docx` | `fr_basic-tests.pdf` | `fr_basic-tests.txt` |
| Portuguese | `pt_basic-tests.docx` | `pt_basic-tests.pdf` | `pt_basic-tests.txt` |
| Arabic | `ar_basic-tests.docx` | `ar_basic-tests.pdf` | `ar_basic-tests.txt` |

## Downloading Files

### Option 1: Individual File Download

Click on any file in the [rendered-docs folder](https://github.com/dyrd-odoo/rag-fictitious-knowledge-base/tree/rendered-artifacts/rendered-docs), then click "Download" or "Raw" button.

**Direct download URL pattern:**
```
https://github.com/dyrd-odoo/rag-fictitious-knowledge-base/raw/rendered-artifacts/rendered-docs/{filename}
```

**Examples:**
```bash
# Download English PDF
curl -L -o en_basic-tests.pdf \
  https://github.com/dyrd-odoo/rag-fictitious-knowledge-base/raw/rendered-artifacts/rendered-docs/en_basic-tests.pdf

# Download French DOCX
curl -L -o fr_basic-tests.docx \
  https://github.com/dyrd-odoo/rag-fictitious-knowledge-base/raw/rendered-artifacts/rendered-docs/fr_basic-tests.docx

# Download Arabic TXT
curl -L -o ar_basic-tests.txt \
  https://github.com/dyrd-odoo/rag-fictitious-knowledge-base/raw/rendered-artifacts/rendered-docs/ar_basic-tests.txt
```

### Option 2: Clone the Rendered Branch

```bash
# Clone only the rendered-artifacts branch
git clone --single-branch --branch rendered-artifacts \
  https://github.com/dyrd-odoo/rag-fictitious-knowledge-base.git rendered-docs

cd rendered-docs/rendered-docs/
ls -la  # View all rendered files
```

### Option 3: Download All Files as ZIP

GitHub doesn't provide a direct way to download a branch as ZIP, but you can use this workaround:

1. Go to: https://github.com/dyrd-odoo/rag-fictitious-knowledge-base/tree/rendered-artifacts
2. Click the green "Code" button
3. Select "Download ZIP"
4. Extract and navigate to the `rendered-docs/` folder

## Using with Odoo AI Agents

### Method 1: Upload Files Directly

1. Go to your Odoo instance
2. Navigate to the AI agent configuration
3. Upload the DOCX or PDF files as knowledge sources
4. The agent will index the content automatically

### Method 2: Provide URLs

Configure your AI agent to fetch documents from GitHub URLs:

```
https://github.com/dyrd-odoo/rag-fictitious-knowledge-base/raw/rendered-artifacts/rendered-docs/en_basic-tests.pdf
https://github.com/dyrd-odoo/rag-fictitious-knowledge-base/raw/rendered-artifacts/rendered-docs/fr_basic-tests.pdf
https://github.com/dyrd-odoo/rag-fictitious-knowledge-base/raw/rendered-artifacts/rendered-docs/pt_basic-tests.pdf
https://github.com/dyrd-odoo/rag-fictitious-knowledge-base/raw/rendered-artifacts/rendered-docs/ar_basic-tests.pdf
```

## Using with Other RAG Systems

### LangChain Example

```python
from langchain.document_loaders import PyPDFLoader, TextLoader

# Load PDF
loader = PyPDFLoader("en_basic-tests.pdf")
documents = loader.load()

# Or load TXT
loader = TextLoader("en_basic-tests.txt")
documents = loader.load()

# Process with your RAG pipeline
# ...
```

### LlamaIndex Example

```python
from llama_index import SimpleDirectoryReader

# Load all documents
documents = SimpleDirectoryReader("./rendered-docs").load_data()

# Build index
from llama_index import VectorStoreIndex
index = VectorStoreIndex.from_documents(documents)
```

## Format Recommendations

| Use Case | Recommended Format | Why |
|----------|-------------------|-----|
| Odoo AI Agents | DOCX or PDF | Native support, preserves formatting |
| Simple text processing | TXT | Clean plain text, no parsing needed |
| Visual/layout testing | PDF | Preserves exact formatting and layout |
| Cross-platform compatibility | TXT | Works everywhere, smallest size |
| Arabic content | PDF or TXT | PDF has proper RTL support |

## Testing Your RAG System

### Complete Test Suite

**All test questions are available in [test-questions/basic-tests.md](test-questions/basic-tests.md)**

The test suite includes:
- **21 questions** across 7 categories
- **Expected answers** for each question
- **Difficulty ratings** (Easy, Medium, Hard)
- **Evaluation guidelines** and scoring criteria
- **Cross-language testing** instructions

### Sample Workflow

1. **Ingest Documents**
   ```bash
   # Download all TXT files for simple testing
   for lang in en fr pt ar; do
     curl -L -o ${lang}_basic-tests.txt \
       https://github.com/dyrd-odoo/rag-fictitious-knowledge-base/raw/rendered-artifacts/rendered-docs/${lang}_basic-tests.txt
   done
   ```

2. **Index in Your RAG System**
   - Load documents
   - Create embeddings
   - Store in vector database

3. **Run Test Questions**
   ```python
   # Example: Test basic retrieval
   question = "Where is Orion Analytics Group headquartered?"
   response = rag_system.query(question)
   
   expected = "Nova Cascadia"
   assert expected in response.answer
   ```
   
   See [test-questions/basic-tests.md](test-questions/basic-tests.md) for all 21 questions.

4. **Evaluate Performance**
   - **Accuracy** - Percentage of correct answers
   - **Grounding** - Are answers properly cited?
   - **Hallucination rate** - Did system fabricate info for negative tests?
   - **Completeness** - Multi-part questions fully answered?
   
   Detailed evaluation criteria in [test-questions/README.md](test-questions/README.md).

### Test Question Categories

| Category | Question Range | Purpose |
|----------|---------------|---------|
| **Basic Retrieval** | Q1-Q3 | Simple fact lookup |
| **Entity-Attribute** | Q4-Q7 | Relationship understanding |
| **Concept Definition** | Q8-Q11 | Understanding LUMA Index |
| **Event Retrieval** | Q12-Q14 | Temporal/event understanding |
| **Multi-Hop** | Q15-Q17 | Cross-section reasoning |
| **Hallucination Detection** | Q18-Q19 | Missing info handling |
| **Meta-Awareness** | Q20-Q21 | Disclaimer understanding |

**Full details:** [test-questions/basic-tests.md](test-questions/basic-tests.md)

## Updating Documents

The rendered documents are automatically updated whenever HTML source files change:

1. Edit HTML files in the main branch
2. Push changes
3. Wait 2-3 minutes for workflow to complete
4. New versions appear in `rendered-artifacts` branch

**No manual conversion needed!**

## Programmatic Access

### Python Script to Download All Files

```python
import requests
import os

base_url = "https://github.com/dyrd-odoo/rag-fictitious-knowledge-base/raw/rendered-artifacts/rendered-docs"
languages = ["en", "fr", "pt", "ar"]
formats = ["docx", "pdf", "txt"]

os.makedirs("rendered-docs", exist_ok=True)

for lang in languages:
    for fmt in formats:
        filename = f"{lang}_basic-tests.{fmt}"
        url = f"{base_url}/{filename}"
        
        print(f"Downloading {filename}...")
        response = requests.get(url)
        
        if response.status_code == 200:
            with open(f"rendered-docs/{filename}", "wb") as f:
                f.write(response.content)
            print(f"✓ {filename} downloaded")
        else:
            print(f"✗ Failed to download {filename}")

print("\nAll files downloaded to rendered-docs/")
```

### Bash Script

```bash
#!/bin/bash

mkdir -p rendered-docs
cd rendered-docs

BASE_URL="https://github.com/dyrd-odoo/rag-fictitious-knowledge-base/raw/rendered-artifacts/rendered-docs"

for lang in en fr pt ar; do
  for fmt in docx pdf txt; do
    file="${lang}_basic-tests.${fmt}"
    echo "Downloading ${file}..."
    curl -L -o "$file" "${BASE_URL}/${file}"
  done
done

echo "All files downloaded!"
```

## Troubleshooting

**Q: Files not updating?**
- Check the Actions tab for workflow status
- Workflow only runs when HTML files change
- Wait 2-3 minutes for completion

**Q: Arabic PDF shows garbled text?**
- The latest version uses DejaVu Sans with bidi support
- Re-download if you have an older version

**Q: Download link returns 404?**
- Ensure you're using the `rendered-artifacts` branch in the URL
- Check the exact filename (case-sensitive)

## Need Help?

- Check the main [README.md](README.md) for general information
- View the [workflow file](.github/workflows/render-html.yml) for technical details
- Open an issue on GitHub for problems or questions

---

**Last updated**: Check the commit history of the `rendered-artifacts` branch for the latest generation timestamp
