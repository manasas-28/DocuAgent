# 📄 DocuAgent — Agentic RAG Assistant

DocuAgent is an intelligent, agentic Retrieval-Augmented Generation (RAG) assistant that allows users to upload documents or paste text and have context-aware, cited conversations with their data. Powered by fast LLM inference, it breaks down documents into manageable chunks and extracts precise answers with verifiable source grounding.

---

## ✨ Features

*   **Flexible Document Ingestion:** Support for direct text pasting and PDF uploads.
*   **Intelligent Text Chunking:** Automatically processes and segments text to maintain contextual integrity.
*   **Source Grounding & Citations:** Every answer includes references to the specific text chunks it was derived from, minimizing hallucinations.
*   **Session Memory Management:** Multi-turn conversation support with a dedicated "Clear Memory" function to reset context.
*   **Lightning-Fast Inference:** Optimized using highly efficient models via Groq.

---

## 🛠️ Tech Stack

*   **Frontend/UI:** Streamlit / Python-based web interface
*   **LLM Engine:** `llama3-8b-8192` via **Groq** (or configurable alternatives)
*   **RAG Framework:** Agentic pipeline handling document parsing, chunking, and semantic retrieval.

---

## 🚀 Getting Started

### Prerequisites

*   Python 3.10+
*   A Groq API Key (Sign up at [Groq Console](https://console.groq.com/))

### Installation

1. **Clone the repository:**
   ```bash
   git clone [https://github.com/yourusername/DocuAgent.git](https://github.com/yourusername/DocuAgent.git)
   cd DocuAgent
