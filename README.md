# RAG Application - Learning Project

## Overview
This is a **learning project** built to understand and implement **Retrieval-Augmented Generation (RAG)** using LangChain and Ollama. It is **not a research-level project**, but rather a demonstration of applying newly learned concepts.

## What I Learned

### 1. **RAG (Retrieval-Augmented Generation)**
- How RAG works: retrieve relevant document chunks, then pass them to an LLM for grounded answers
- Why RAG matters: enables LLMs to answer questions about documents without hallucinating or exceeding context limits
- The difference between giving raw PDFs to an LLM vs. using retrieval-based approach

### 2. **LangChain Framework**
- Building chains: prompt → model → parser
- Document loaders: `PyMuPDFLoader` for PDF ingestion
- Vector stores: `DocArrayInMemorySearch` for semantic search
- Retrievers: converting vector stores into queryable interfaces
- Composition: using `|` (pipe) operator to chain components

### 3. **Embeddings & Vector Search**
- Using `OllamaEmbeddings` to convert text into vectors
- Building in-memory vector stores for retrieval
- Semantic search using embeddings

### 4. **Local LLM Integration**
- Running `phi3:mini` and `nomic-embed-text` models locally with Ollama
- No API calls = cost-free learning

## Project Structure

```
notebook.ipynb          # Main implementation
requirements.txt        # Project dependencies
NIPS-2017-*.pdf        # Sample PDF for RAG testing
```

## What the Application Does

1. **Loads a PDF** (attention paper) using PyMuPDFLoader
2. **Chunks and embeds** the document into vectors
3. **Stores** vectors in an in-memory search index
4. **Retrieves** relevant chunks when given a question
5. **Passes context to LLM** along with the question
6. **Returns grounded answer** based on the document

### Example Query
- **Question:** "What is attention?"
- **Output:** The model retrieves relevant sections from the paper and answers based on that context

## How to Run

### Prerequisites
- Python 3.10+
- [Ollama](https://ollama.ai) installed and running locally
- Models pulled: `ollama pull phi3:mini` and `ollama pull nomic-embed-text`

### Setup
```bash
pip install -r requirements.txt
jupyter notebook notebook.ipynb
```

Then run all cells sequentially.

## Technologies Used

- **LangChain** — Framework for chaining LLM components
- **Ollama** — Local LLM runtime (models: phi3:mini, nomic-embed-text)
- **PyMuPDF** — PDF parsing and text extraction
- **DocArray** — Vector store for semantic search
- **Pydantic** — Data validation

## Limitations & Future Improvements

This is a proof-of-concept implementation. Current limitations:
- In-memory vector store (not scalable to large datasets)
- Single PDF only
- No persistence (embeddings computed fresh each run)
- Basic chunking strategy (no overlap tuning)

**Possible enhancements:**
- Use FAISS for faster search and scalability
- Add caching to avoid recomputing embeddings
- Implement parallel embedding batching
- Add streaming responses
- Support multiple PDFs
- Add web UI

## Key Takeaway

This project demonstrates understanding of:
- How RAG solves the problem of grounding LLM responses
- How to build multi-component LLM applications with LangChain
- How local models can be integrated into workflows
- The importance of retrieval-based systems over naive in-context learning

It is a **hands-on learning exercise** and serves as a foundation for more advanced RAG systems.
