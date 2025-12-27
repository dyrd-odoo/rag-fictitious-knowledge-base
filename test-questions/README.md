# Test Questions Directory

This directory contains test questions and expected answers for evaluating RAG systems against the fictional knowledge base.

## Available Test Sets

### [basic-tests.md](basic-tests.md)
Test questions for the `basic-tests` documents across all languages.

**Coverage:**
- Simple fact retrieval
- Entity-attribute mapping
- Concept understanding (LUMA Index)
- Event-based retrieval
- Multi-hop reasoning
- Hallucination detection
- Meta-awareness

**Languages:** English, French, Portuguese, Arabic  
**Questions:** 21 total  
**Difficulty:** Easy to Hard

---

## How to Use These Tests

### 1. Ingest the Documents

Choose your preferred format from the [rendered documents](https://github.com/dyrd-odoo/rag-fictitious-knowledge-base/tree/rendered-artifacts/rendered-docs):

```bash
# Example: Download English PDF
curl -L -o en_basic-tests.pdf \
  https://github.com/dyrd-odoo/rag-fictitious-knowledge-base/raw/rendered-artifacts/rendered-docs/en_basic-tests.pdf
```

### 2. Load into Your RAG System

```python
# Example with LangChain
from langchain.document_loaders import PyPDFLoader

loader = PyPDFLoader("en_basic-tests.pdf")
documents = loader.load()

# Create embeddings and index
# ... your RAG setup code ...
```

### 3. Run the Test Questions

Ask each question from the test file and compare the answer to the expected answer.

```python
# Example test
question = "What is the name of the fictional company described on the site?"
response = rag_system.query(question)

expected = "Orion Analytics Group"
assert expected in response.answer
```

### 4. Evaluate Results

Track:
- **Accuracy:** Percentage of correct answers
- **Grounding:** Are answers properly cited?
- **Hallucination Rate:** Did system fabricate info for Q18-Q19?
- **Completeness:** Multi-part questions fully answered?

## Test Categories

| Category | Purpose | Example Question |
|----------|---------|------------------|
| **Basic Retrieval** | Tests simple fact lookup | "Where is Orion Analytics Group headquartered?" |
| **Entity-Attribute** | Tests relationship understanding | "Which division is responsible for data ingestion?" |
| **Concept Definition** | Tests understanding of defined terms | "What is the LUMA Index?" |
| **Event Retrieval** | Tests temporal/event understanding | "What was the Nova Cascadia Incident?" |
| **Multi-Hop** | Tests reasoning across sections | "Which division would prevent future incidents?" |
| **Negative Tests** | Tests hallucination resistance | "How many employees work at OAG?" |
| **Meta-Awareness** | Tests understanding of disclaimers | "Is this real-world data?" |

## Adding New Test Sets

When adding new documents to the knowledge base:

1. **Create a new test file** following the naming pattern:
   ```
   test-questions/{document-name}.md
   ```

2. **Use this template structure:**
   ```markdown
   # RAG Test Questions: {document-name}
   
   [Description of what documents this covers]
   
   ## 1. [Category Name]
   
   ### Q1: [Question]
   
   **Expected Answer:**
   [Answer]
   
   **Category:** [Type]
   **Difficulty:** [Easy/Medium/Hard]
   ```

3. **Update this README** to list the new test set

4. **Include diverse question types:**
   - Simple retrieval
   - Complex reasoning
   - Negative tests (missing info)
   - Cross-reference questions

## Evaluation Best Practices

### Automated Testing

```python
import json

test_results = {
    "total": 0,
    "correct": 0,
    "incorrect": 0,
    "hallucinations": 0
}

for question in test_questions:
    response = rag_system.query(question["text"])
    test_results["total"] += 1
    
    if evaluate_answer(response, question["expected"]):
        test_results["correct"] += 1
    else:
        test_results["incorrect"] += 1
    
    if is_hallucination(response, question):
        test_results["hallucinations"] += 1

accuracy = test_results["correct"] / test_results["total"]
print(f"Accuracy: {accuracy:.2%}")
```

### Manual Review

For subjective evaluation:
1. Review each answer against expected answer
2. Check if source citations are correct
3. Verify multi-hop reasoning chain
4. Assess answer completeness

### Cross-Language Testing

Test the same questions across all languages:

```python
languages = ["en", "fr", "pt", "ar"]
results_by_language = {}

for lang in languages:
    # Load language-specific document
    doc = load_document(f"{lang}_basic-tests.pdf")
    
    # Run tests
    results = run_tests(doc, translated_questions[lang])
    results_by_language[lang] = results

# Compare consistency
compare_results(results_by_language)
```

## Interpreting Results

### Good RAG Performance
- ✅ 90%+ accuracy on basic retrieval (Q1-Q7)
- ✅ 80%+ on concept questions (Q8-Q11)
- ✅ 70%+ on multi-hop reasoning (Q15-Q17)
- ✅ Correctly identifies missing information (Q18-Q19)
- ✅ Respects disclaimers (Q20-Q21)

### Common Issues
- ❌ **Low basic retrieval**: Check chunking strategy
- ❌ **Poor multi-hop**: Improve context window or ranking
- ❌ **Hallucinations on Q18-Q19**: Strengthen grounding requirements
- ❌ **Ignoring disclaimers**: Review system prompt

## Contributing

When contributing new test questions:

1. Ensure questions are **answerable from the documents**
2. Include **clear expected answers**
3. Add **difficulty ratings**
4. Mix **easy and hard** questions
5. Include **negative tests** to catch hallucinations
6. Test across **all languages** for consistency

---

**Questions or suggestions?** Open an issue on GitHub.
