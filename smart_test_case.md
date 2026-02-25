## What We Are Building (Clear Goal)
We will build: 
>  **A Smart Test Case Generator that learns from existing test cases and generates better new ones** 
<img width="1684" height="824" alt="image" src="https://github.com/user-attachments/assets/8f9bd0a2-6ce3-40a7-81e8-31b75f290a96" />

## Data Preparation (VERY IMPORTANT)
### Convert Each Row into One Document
Example document:
```
Test Case ID: TC002
Feature: Login
Steps: Enter valid email and invalid password
Expected Result: Error message shown
Type: Negative
```
**Rule:**
 👉 One test case = one semantic document

## Full RAG Architecture Diagram
```
┌──────────────────┐
│ Excel / CSV Data │
└─────────┬────────┘
          ↓
┌──────────────────┐
│ Document Loader  │
└─────────┬────────┘
          ↓
┌──────────────────┐
│ Text Splitter    │
└─────────┬────────┘
          ↓
┌──────────────────┐
│ Embedding Model  │
└─────────┬────────┘
          ↓
┌──────────────────┐
│ Vector Store     │
└─────────┬────────┘
          ↓
┌──────────────────┐
│ Retriever        │
└─────────┬────────┘
          ↓
┌──────────────────┐
│ Prompt Template  │
└─────────┬────────┘
          ↓
┌──────────────────┐
│ LLM              │
└─────────┬────────┘
          ↓
┌──────────────────┐
│ Generated Tests  │
└──────────────────┘
```

## Step-by-Step Langflow Implementation
### Step 1: Document Loader
**Purpose:** Load test cases
- CSV Loader
- Text Loader
Output:
- Raw test case documents

### Step 2: Text Splitter
**Why:** Ensure context stays together
Settings:
```
Chunk Size: 1000
Overlap: 100
```

### Step 3: Embedding Model
**Purpose:** Convert test cases to vectors
Example:
- OpenAI Embeddings
Output:
- Vector representations

### Step 4: Vector Store
**Purpose:** Store and search embeddings
Recommended:
- Chroma (for learning)
Metadata:
```
feature
type
priority
```

### Step 5: Retriever
**Purpose:** Fetch relevant test cases
Retriever config:
```
Top K = 4
Search Type = similarity
```

### Step 6: Prompt Template
Example prompt:
```
You are a senior QA engineer.
Context:
{retrieved_test_cases}
Task:
Generate additional test cases for:
{new_feature_description}
Rules:
- Do not duplicate existing cases
- Focus on edge cases
- Use same format
```

## Example End-to-End Execution
### User Input
```
Generate test cases for Password Reset feature
```

### Retrieved Context
- Login validation failures
- Email verification tests
- Error handling cases

### Output Generated
```
Test Case ID: TC_PR_01
Title: Password reset with expired token
Steps:
1. Click reset link after expiry
Expected Result: Token expired message

Test Case ID: TC_PR_02
Title: Multiple reset attempts
Expected Result: Rate limiting applied
```

## Next Extensions (Optional for Advanced Students)
- Jira auto-creation
- Automation feasibility tagging
- Playwright code generation
- Bug-to-test mapping




