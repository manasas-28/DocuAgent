
# 📄 DocuAgent — Agentic RAG Assistant

**DocuAgent** is an intelligent, agentic Retrieval-Augmented Generation (RAG) assistant that allows users to upload documents or paste raw text to have precise, context-aware conversations with their data. Powered by fast LLM inference, it breaks down text into manageable chunks and extracts answers backed by verifiable source citations.

### 🔗 [⚡ Click Here for the Live Demo](https://docu-agent--manasaaas.replit.app/)
---

## 🚀 Quick Start Example (Try It in 30 Seconds)

To test the application instantly on the live deployment, use this pre-verified benchmark example:

### 1. Copy This Sample Text
```text
IBM and ElevenLabs: Enterprise AI Finds its Voice
By Tom Chapman | June 24, 2026

A landmark partnership between IBM and ElevenLabs is moving enterprise AI beyond text, delivering natural, secure, and scalable voice-first agents.

Delivering Natural Voice Interactions
For decades, the promise of voice-driven technology remained out of reach due to rigid scripts, misunderstood phrases, and robotic responses. However, speech-to-text (STT) and text-to-speech (TTS) tech has entered a transformative era, acting as a gateway for advanced agentic AI by translating the nuance and intent of human speech in real time.

The collaboration brings together ElevenLabs’ TTS and STT technologies with IBM's watsonx Orchestrate. This platform allows clients to build security- and compliance-focused voice agents capable of communicating naturally across 70 languages, incorporating human emotion and rhythm.

"AI agents are becoming central to everyday work, and voice is where AI either earns trust or loses it," explains Mati Staniszewski, Co-Founder at ElevenLabs. "Together with IBM, we're helping organisations replace robotic interactions with AI agents that people actually want to talk to..."

Real-World Implications & Governance
The real-world applications span numerous sectors:

Government & Public Services: AI phone agents can converse seamlessly in dozens of languages and regional accents to assist constituents with vital health, education, and civic information.

Finance & Healthcare: Banks, insurance companies, and utilities can deploy voice agents for customer support, sales pipelines, and internal operations.

Crucially, the partnership ensures enterprise-grade protections, including PCI compliance for secured payment processing, Zero Retention Mode for HIPAA-compliant data handling, and strict data residency controls.

Key Statistics:

US$330m: ElevenLabs' annual recurring revenue (2025)

US$11bn: ElevenLabs' valuation as of February 2026 after its US$500m Series D funding round

10,000+: Number of voices in ElevenLabs' library

AWS Co-Founder Matt Domo: Why AI Investments are Stalling
By Tom Chapman | June 26, 2026

Recent analysis from Forrester discovered that only 10-15% of AI pilots successfully scale into long-term production, meaning most enterprise AI investments stall before delivering real impact. Matt Domo, a Co-Founder of Amazon Web Services (AWS) and creator of foundational Microsoft technologies, explains how organizations can overcome this hurdle.

Why Executive AI Initiatives Fail
Domo highlights that failure rarely stems from weak technology. Instead, it happens because the organization isn't aligned. The breakdown usually occurs in three places:

Unclear ownership of outcomes.

Misaligned incentives across teams.

Operating models that aren’t built for how AI changes decision-making.

Leaders often layer AI on top of existing workflows as a "technology project" rather than restructuring how the business actually operates.

Moving from Pilot to Scale
AI scales through standardization, not through running more pilots. Successful companies define a repeatable path from pilot to production, assign clear ownership, and completely integrate AI into core workflows.

ROI Metrics That Convince Boards
Boards are convinced by measurable impact tied directly to the P&L, not vague reporting like "usage" or "engagement." Domo advises focusing on three straightforward metrics:

Cost reduction

Revenue lift

Faster decision cycles

Avoiding "AI-Washing" and Speeding Up Decisions
To avoid AI-washing, organizations must start with the intended business outcome first, and only then determine where AI can improve the workflow.

Furthermore, speed in AI decision-making doesn't come from better models—it comes from clearer ownership and fewer handoffs. Organizations must define who owns the outcome and reduce the number of required approvals to turn AI-generated insights into quick real-world actions.

```

### 2. Run the Test

1. Open the [Live Demo](https://docu-agent--manasaaas.replit.app/).
2. Select **Paste Text** in the sidebar, paste the text block above into the area, and click the **Process Text** button.
3. Scroll down to the **💬 Ask Your Document** chat interface and submit this question:
> *"According to Matt Domo, what are the three main areas where AI initiatives typically break down at the executive level?"*



### 3. Analyze the Output

* **The AI Output:** Instantly extracts and formats the 3 distinct pain points.
* **Source Citation:** Notice the `[Chunk 2]` tracking tag appended directly next to the generated answers.
* **Verification:** Click the **📎 Source chunks** dropdown to view the exact raw text snippet the AI referenced to audit its validity.

---

## 🏗️ Technical Architecture & Pipeline

Behind the clean UI, DocuAgent implements a lightweight, high-performance RAG pipeline designed to run efficiently in-memory:

```
[PDF / Paste Text] ──> [PyPDF2 Parsing] ──> [LangChain Recursive Chunking]
                                                    │
                                                    ▼
[Groq API (Llama3)] <── [Context Retrieval] <── [ChromaDB + all-MiniLM-L6-v2]

```

1. **Ingestion & Parsing:** Text extraction is handled instantly via native text strings or parsed through `PyPDF2` for multi-page documents.
2. **Embedding & Vector Storage:** Document segments are embedded using the `all-MiniLM-L6-v2` transformer model from `sentence-transformers` and cataloged into an ephemeral, in-memory `ChromaDB` vector database.
3. **Contextual Retrieval:** The application queries ChromaDB semantically to isolate relevant text segments, enforcing strict grounding through an explicit system prompt layer (*"Answer only from the provided context. Cite the relevant section."*).
4. **State Management:** Keeps conversations fluid using standard session variables to retain the last **3 turns** of chat history for context-aware follow-up queries.

---

## 🛠️ Tech Stack

* **Frontend Interface:** Streamlit (Clean Dark Theme custom layout)
* **LLM Inference Engine:** `llama3-8b-8192` via **Groq API**
* **Orchestration & Chunking:** LangChain
* **Vector Database:** ChromaDB (Ephemeral, In-Memory)
* **Embedding Model:** `sentence-transformers/all-MiniLM-L6-v2`
* **Document Processor:** PyPDF2

---

## ✨ Core Features

* **Flexible Ingestion:** Switch instantly between uploading a standard PDF file or pasting raw text chunks.
* **Intelligent Text Chunking:** Automatically processes, cleans, and segments long-form text into optimized data blocks to maintain overarching context.
* **Source Grounding & Citations:** Tracks exactly which section of your document an information piece was extracted from, eliminating AI hallucinations.
* **Session Memory Management:** Supports ongoing multi-turn conversational sequences with a dedicated **🗑️ Clear Memory** option to flush active caches and initiate fresh semantic indexing.

