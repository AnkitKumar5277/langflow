### What Are Embedding Models?
Embedding models convert **text into numbers** (vectors) that represent **meaning**.
Example:
```
"Login test case"
→ [0.021, 0.884, -0.112, ...]
```

### Why Embeddings Are Needed
Computers cannot compare text meaning directly.
Embeddings allow:
- Semantic search
- Similarity matching
- Context retrieval

### QA Example
These two are **semantically similar**:
- “User logs in with valid credentials”
- “Successful authentication with correct email/password”
Embedding models **understand this similarity**.

### Popular Embedding Models
- OpenAI: `text-embedding-3-large` 
- Local: `nomic-embed-text` 
- Ollama embeddings

