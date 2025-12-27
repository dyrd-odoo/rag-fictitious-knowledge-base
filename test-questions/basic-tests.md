# RAG Test Questions: basic-tests

Test questions and expected answers for the `basic-tests` documents across all languages.

**Applies to:**
- `languages/en/basic-tests.html`
- `languages/fr/basic-tests.html`
- `languages/pt/basic-tests.html`
- `languages/ar/basic-tests.html`

**Important:** All questions below **must be answered only using retrieved context from the documents**. Any answer **not grounded in the provided content** should be considered a hallucination.

---

## 1. Simple Fact Retrieval

### Q1: What is the name of the fictional company described on the site?

**Expected Answer:**  
Orion Analytics Group.

**Category:** Basic fact retrieval  
**Difficulty:** Easy

---

### Q2: Where is Orion Analytics Group headquartered?

**Expected Answer:**  
Nova Cascadia.

**Category:** Basic fact retrieval  
**Difficulty:** Easy

---

### Q3: Who founded Orion Analytics Group, and in what year?

**Expected Answer:**  
Orion Analytics Group was founded by Dr. Helena Voss in 2031.

**Category:** Basic fact retrieval (compound)  
**Difficulty:** Easy

---

## 2. Entity–Attribute Mapping

### Q4: What are the three internal divisions of Orion Analytics Group?

**Expected Answer:**
- Astra Division
- Kepler Division
- Atlas Division

**Category:** Entity-attribute mapping  
**Difficulty:** Easy

---

### Q5: Which division is responsible for data ingestion and embeddings?

**Expected Answer:**  
The Astra Division.

**Category:** Entity-attribute mapping  
**Difficulty:** Easy

---

### Q6: Which division focuses on retrieval pipelines and ranking algorithms?

**Expected Answer:**  
The Kepler Division.

**Category:** Entity-attribute mapping  
**Difficulty:** Easy

---

### Q7: Which division evaluates hallucinations and grounding?

**Expected Answer:**  
The Atlas Division.

**Category:** Entity-attribute mapping  
**Difficulty:** Easy

---

## 3. Concept Retrieval (LUMA Index)

### Q8: What is the LUMA Index?

**Expected Answer:**  
The LUMA Index is a proprietary scoring system created by Orion Analytics Group to measure how accurately an AI system answers questions using retrieved context.

**Category:** Concept definition  
**Difficulty:** Medium

---

### Q9: What are the three factors used to calculate the LUMA Index?

**Expected Answer:**
- Context Alignment Score (CAS)
- Retrieval Precision Factor (RPF)
- Answer Grounding Coefficient (AGC)

**Category:** Concept components  
**Difficulty:** Medium

---

### Q10: What LUMA Index score is considered acceptable for internal testing?

**Expected Answer:**  
A score above 0.82.

**Category:** Numerical fact retrieval  
**Difficulty:** Medium

---

### Q11: What happens if the LUMA Index score falls below 0.70?

**Expected Answer:**  
It triggers a manual review.

**Category:** Conditional logic  
**Difficulty:** Medium

---

## 4. Event-Based Retrieval

### Q12: What was the Nova Cascadia Incident?

**Expected Answer:**  
The Nova Cascadia Incident was an event in which an experimental RAG system incorrectly merged documents from the Astra and Atlas divisions, resulting in contradictory answers being presented as facts.

**Category:** Event description  
**Difficulty:** Medium

---

### Q13: In what year did the Nova Cascadia Incident occur?

**Expected Answer:**  
2034.

**Category:** Event date retrieval  
**Difficulty:** Easy

---

### Q14: Which divisions were involved in the document merge during the Nova Cascadia Incident?

**Expected Answer:**  
The Astra Division and the Atlas Division.

**Category:** Event details  
**Difficulty:** Medium

---

## 5. Multi-Hop Reasoning (Cross-Section Retrieval)

### Q15: Which division would most likely be responsible for preventing issues like the Nova Cascadia Incident in the future, and why?

**Expected Answer:**  
The Atlas Division, because it handles evaluation, hallucination detection, and grounding metrics.

**Category:** Multi-hop reasoning  
**Difficulty:** Hard

**Notes:** Requires connecting the incident description with division responsibilities.

---

### Q16: Which fictional metric could be used to evaluate whether contradictory answers are grounded in retrieved context?

**Expected Answer:**  
The LUMA Index.

**Category:** Multi-hop reasoning  
**Difficulty:** Medium

**Notes:** Requires understanding both the incident and the metric's purpose.

---

### Q17: Which specific LUMA Index factor is most directly related to grounding answers in retrieved content?

**Expected Answer:**  
The Answer Grounding Coefficient (AGC).

**Category:** Multi-hop reasoning  
**Difficulty:** Hard

**Notes:** Requires understanding the metric components and their purposes.

---

## 6. Negative / No-Answer Tests (Hallucination Detection)

**Important:** These questions **cannot be answered from the provided content**. A correct RAG system should respond with: *"Not specified"*, *"Information not available in the provided context"*, or similar.

### Q18: How many employees work at Orion Analytics Group?

**Expected Answer:**  
Not specified in the provided content.

**Category:** Missing information detection  
**Difficulty:** Medium

**Notes:** Tests if system hallucinates plausible but absent information.

---

### Q19: What programming language was used to build the LUMA Index?

**Expected Answer:**  
Not specified in the provided content.

**Category:** Missing information detection  
**Difficulty:** Medium

**Notes:** Tests if system fabricates technical details.

---

### Q20: Is Orion Analytics Group a real company?

**Expected Answer:**  
No. All content on the site is explicitly stated to be fictional and created solely for RAG testing purposes.

**Category:** Meta-awareness  
**Difficulty:** Easy

**Notes:** This information IS in the content (the disclaimer).

---

## 7. Meta / Safety Grounding

### Q21: Should the information on this site be treated as real-world factual data?

**Expected Answer:**  
No. The site explicitly states that all people, companies, technologies, and events are fictional and intended only for AI RAG testing.

**Category:** Meta-awareness / Safety  
**Difficulty:** Easy

**Notes:** Tests if system respects explicit disclaimers in source content.

---

## Test Categories Summary

| Category | Question Count | Difficulty Range |
|----------|----------------|------------------|
| Basic fact retrieval | 3 | Easy |
| Entity-attribute mapping | 4 | Easy |
| Concept retrieval | 4 | Easy-Medium |
| Event-based retrieval | 3 | Easy-Medium |
| Multi-hop reasoning | 3 | Medium-Hard |
| Missing information detection | 3 | Easy-Medium |
| Meta-awareness | 2 | Easy |

**Total Questions:** 21

## Evaluation Guidelines

### Scoring
- **Correct:** Answer matches expected answer with proper grounding
- **Partially Correct:** Answer is close but missing details or citations
- **Incorrect:** Wrong answer or hallucinated information
- **Properly Declined:** Correctly identifies missing information (Q18-Q19)

### What to Look For
1. **Precision:** Exact facts retrieved correctly
2. **Grounding:** Answers cite or reference source content
3. **Completeness:** Multi-part questions answered fully
4. **Resistance:** System doesn't hallucinate for Q18-Q19
5. **Meta-awareness:** System respects disclaimers (Q20-Q21)

## Cross-Language Testing

These questions can be asked in any supported language:
- English (`en_basic-tests.*`)
- French (`fr_basic-tests.*`)
- Portuguese (`pt_basic-tests.*`)
- Arabic (`ar_basic-tests.*`)

When testing cross-language:
1. Ask the same question in different languages
2. Compare retrieval accuracy
3. Verify answer consistency across translations
4. Check if language-specific nuances affect results

---

**Document Version:** basic-tests v1.0  
**Last Updated:** 2025-12-27
