# AAJ RAG Chatbot

A multi-utility AI chatbot built with **LangGraph, LangChain, Hugging Face, Ollama, FAISS, and Streamlit**. The application supports document-based question answering through Retrieval-Augmented Generation (RAG), web search, and calculator tools while maintaining conversation state across multiple chat threads.

## Features

- **PDF-based RAG** – Upload a PDF and ask questions about its content.
- **Semantic Retrieval** – Uses Hugging Face embeddings with FAISS for relevant document retrieval.
- **Local LLM** – Runs Llama 3.2 3B locally using Ollama.
- **Tool Calling** – Supports web search, calculator, and document retrieval tools.
- **LangGraph Workflow** – Uses a graph-based architecture for LLM and tool execution.
- **Multi-Thread Conversations** – Create and restore previous chat sessions.
- **Persistent State** – Uses SQLite checkpointing to maintain conversation state.
- **Streamlit Interface** – Interactive UI for chatting, PDF uploads, and tool execution.

## RAG Pipeline
- Upload a PDF through the Streamlit interface.
- Extract document content using PyPDFLoader.
- Split the document into overlapping chunks.
- Generate embeddings using Hugging Face.
- Store embeddings in a FAISS vector store.
- Retrieve the most relevant chunks for a user query.
- Pass retrieved context to the LLM.
- Generate a context-aware response.

## Tech Stack
- Language: Python
- LLM: Llama 3.2 3B, Ollama
- GenAI: LangChain, LangGraph
- Embeddings: Hugging Face all-MiniLM-L6-v2
- Vector Store: FAISS
- Document Processing: PyPDFLoader
- Frontend: Streamlit
- Database: SQLite
- Tools: DuckDuckGo Search, Calculator

## Architecture

```text
User
 │
 ▼
Streamlit Frontend
 │
 ▼
LangGraph Chatbot
 │
 ├── LLM (Llama 3.2 3B)
 │
 ├── Web Search Tool
 │
 ├── Calculator Tool
 │
 └── RAG Tool
       │
       ▼
   PDF Loader
       │
       ▼
 Text Chunking
       │
       ▼
Hugging Face Embeddings
       │
       ▼
     FAISS
       │
       ▼
Relevant Context
       │
       ▼
      LLM
       │
       ▼
Final Response
