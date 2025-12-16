# RAG Test Questions and Expected Answers

This repository contains a **fictional knowledge base** designed exclusively for testing **Retrieval-Augmented Generation (RAG)** systems.

- All questions below **must be answered only using retrieved context from the website**.
    
- Any answer **not grounded in the provided content** should be considered a hallucination.
    

---

## 1. Simple Fact Retrieval

### Q1

**What is the name of the fictional company described on the site?**

**Expected Answer:**  
Orion Analytics Group.

---

### Q2

**Where is Orion Analytics Group headquartered?**

**Expected Answer:**  
Nova Cascadia.

---

### Q3

**Who founded Orion Analytics Group, and in what year?**

**Expected Answer:**  
Orion Analytics Group was founded by Dr. Helena Voss in 2031.

---

## 2. Entity–Attribute Mapping

### Q4

**What are the three internal divisions of Orion Analytics Group?**

**Expected Answer:**

- Astra Division
    
- Kepler Division
    
- Atlas Division
    

---

### Q5

**Which division is responsible for data ingestion and embeddings?**

**Expected Answer:**  
The Astra Division.

---

### Q6

**Which division focuses on retrieval pipelines and ranking algorithms?**

**Expected Answer:**  
The Kepler Division.

---

### Q7

**Which division evaluates hallucinations and grounding?**

**Expected Answer:**  
The Atlas Division.

---

## 3. Concept Retrieval (LUMA Index)

### Q8

**What is the LUMA Index?**

**Expected Answer:**  
The LUMA Index is a proprietary scoring system created by Orion Analytics Group to measure how accurately an AI system answers questions using retrieved context.

---

### Q9

**What are the three factors used to calculate the LUMA Index?**

**Expected Answer:**

- Context Alignment Score (CAS)
    
- Retrieval Precision Factor (RPF)
    
- Answer Grounding Coefficient (AGC)
    

---

### Q10

**What LUMA Index score is considered acceptable for internal testing?**

**Expected Answer:**  
A score above 0.82.

---

### Q11

**What happens if the LUMA Index score falls below 0.70?**

**Expected Answer:**  
It triggers a manual review.

---

## 4. Event-Based Retrieval

### Q12

**What was the Nova Cascadia Incident?**

**Expected Answer:**  
The Nova Cascadia Incident was an event in which an experimental RAG system incorrectly merged documents from the Astra and Atlas divisions, resulting in contradictory answers being presented as facts.

---

### Q13

**In what year did the Nova Cascadia Incident occur?**

**Expected Answer:**  
2034.

---

### Q14

**Which divisions were involved in the document merge during the Nova Cascadia Incident?**

**Expected Answer:**  
The Astra Division and the Atlas Division.

---

## 5. Multi-Hop Reasoning (Cross-Section Retrieval)

### Q15

**Which division would most likely be responsible for preventing issues like the Nova Cascadia Incident in the future, and why?**

**Expected Answer:**  
The Atlas Division, because it handles evaluation, hallucination detection, and grounding metrics.

---

### Q16

**Which fictional metric could be used to evaluate whether contradictory answers are grounded in retrieved context?**

**Expected Answer:**  
The LUMA Index.

---

### Q17

**Which specific LUMA Index factor is most directly related to grounding answers in retrieved content?**

**Expected Answer:**  
The Answer Grounding Coefficient (AGC).

---

## 6. Negative / No-Answer Tests (Hallucination Detection)

These questions **cannot be answered from the provided content**.  
A correct RAG system should respond with:

> “Not specified”, “Information not available in the provided context”, or similar.

---

### Q18

**How many employees work at Orion Analytics Group?**

**Expected Answer:**  
Not specified in the provided content.

---

### Q19

**What programming language was used to build the LUMA Index?**

**Expected Answer:**  
Not specified in the provided content.

---

### Q20

**Is Orion Analytics Group a real company?**

**Expected Answer:**  
No. All content on the site is explicitly stated to be fictional and created solely for RAG testing purposes.

---

## 7. Meta / Safety Grounding

### Q21

**Should the information on this site be treated as real-world factual data?**

**Expected Answer:**  
No. The site explicitly states that all people, companies, technologies, and events are fictional and intended only for AI RAG testing.

---

## 8. Intended Evaluation Outcomes

These questions are designed to test:

- Precision of factual retrieval
    
- Correct entity-to-attribute mapping
    
- Multi-hop reasoning across sections
    
- Resistance to hallucination
    
- Proper handling of missing information
    
- Respect for explicit disclaimers in source content
