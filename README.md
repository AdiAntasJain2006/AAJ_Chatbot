
# AAJ RAG Chatbot

A multi-utility AI chatbot built with **LangGraph, LangChain, Hugging Face, Ollama, FAISS, and Streamlit**. The project explores document-based question answering through Retrieval-Augmented Generation (RAG), tool-enabled interactions, and stateful conversational workflows.

## Features

- **PDF-based RAG:** Upload a PDF and ask questions about its content.
- **Semantic Retrieval:** Uses Hugging Face embeddings and FAISS for document retrieval.
- **Local LLM:** Supports Llama 3.2 3B through Ollama in the RAG workflow.
- **Tool Calling:** Explores web search, calculator, and document retrieval tools.
- **LangGraph Workflows:** Uses graph-based orchestration for conversational and tool execution workflows.
- **Multi-Thread Conversations:** Supports creating and restoring chat sessions.
- **Persistent State:** Uses SQLite checkpointing to preserve conversation state.
- **Streamlit Interfaces:** Provides interfaces for chatbot interaction and document-based question answering.

## Applications

This repository contains two Streamlit implementations.

### 1. RAG Chatbot — Primary Application

**Files:** `rag_frontend.py`, `rag_backend.py`

The primary application focuses on document-based question answering using a RAG workflow.

Run from the repository root:

```bash
streamlit run rag_frontend.py
```

### 2. Tool-Enabled Chatbot — Alternative Application

**Files:** `Streamlit_frontend.py`, `backend_with_tools.py`

An alternative implementation for experimenting with tool-enabled chatbot interactions.

Run from the repository root:

```bash
streamlit run Streamlit_frontend.py
```

## RAG Pipeline

1. Upload a PDF through the Streamlit interface.
2. Extract document content using PyPDFLoader.
3. Split the content into overlapping chunks.
4. Generate embeddings using Hugging Face.
5. Store embeddings in a FAISS vector store.
6. Retrieve relevant chunks for a user query.
7. Pass the retrieved context to the language model.
8. Generate a context-aware response.

## Tech Stack

- **Language:** Python
- **LLM:** Llama 3.2 3B through Ollama in the RAG workflow
- **LLM Frameworks:** LangChain, LangGraph
- **Embeddings:** Hugging Face `all-MiniLM-L6-v2`
- **Vector Store:** FAISS
- **Document Processing:** PyPDFLoader
- **Frontend:** Streamlit
- **Conversation Persistence:** SQLite checkpointing
- **Tools:** DuckDuckGo Search, Calculator

## Architecture

```text
                    User
                      |
                      v
               Streamlit Frontend
                      |
                      v
               LangGraph Workflow
                      |
             +--------+--------+
             |        |        |
             v        v        v
            LLM    Web Search  Calculator
             |
             v
         RAG Workflow
             |
             v
          PDF Loader
             |
             v
        Text Chunking
             |
             v
     Hugging Face Embeddings
             |
             v
            FAISS
             |
             v
      Relevant Document Context
             |
             v
          LLM Response
```

*The diagram represents the intended RAG workflow. The exact execution path depends on the selected application and its implementation.*

## Getting Started

### Prerequisites

- Python
- Git
- Ollama and the required model for the local LLM workflow
- Any additional model credentials or configuration required by the selected application

### 1. Clone the Repository

```bash
git clone https://github.com/AdiAntasJain2006/AAJ_Chatbot.git
cd AAJ_Chatbot
```

### 2. Create a Virtual Environment

```bash
python -m venv .venv
```

**Windows PowerShell:**

```powershell
.\.venv\Scripts\Activate.ps1
```

**macOS / Linux:**

```bash
source .venv/bin/activate
```

### 3. Install Dependencies

```bash
python -m pip install -r requirements.txt
```

### 4. Run an Application

Start the primary RAG application:

```bash
streamlit run rag_frontend.py
```

Or start the alternative tool-enabled application:

```bash
streamlit run Streamlit_frontend.py
```

Configure any required model settings and credentials before running the selected application. Never commit API keys, tokens, or other secrets to GitHub.

## Future Improvements

- Investigate latency in the RAG pipeline.
- Improve error handling and dependency documentation.
- Add reproducible evaluation for retrieval and answer quality.
- Document configuration and troubleshooting for each application.

## Author

**Adi Antas Jain**

- [GitHub](https://github.com/AdiAntasJain2006)
- [LinkedIn](https://www.linkedin.com/in/adi-antas-jain/)
- [LeetCode](https://leetcode.com/u/Adi_Antas_Jain/)
