#  RAG Chatbot

A production-ready **Retrieval-Augmented Generation (RAG)** chatbot built with **LangChain, Groq, FAISS, HuggingFace Embeddings, and Gradio**.

The system allows organizations to upload their PDF knowledge base and instantly create an intelligent AI assistant capable of answering questions using only the provided documents.

---

##  Features

*  PDF Knowledge Base Ingestion
*  Smart Document Chunking
*  Multilingual Support (Arabic & English)
*  Semantic Search with FAISS
*  Context-Aware RAG Pipeline
*  Ultra-Fast Responses via Groq LLMs
*  Conversational Memory
*  Authentication System
*  Gradio Web Interface
*  Ready for Deployment
*  Hallucination Reduction through strict context grounding

---

##  System Architecture

```text
PDF Documents
      
PyPDFLoader
      
Text Cleaning
      
RecursiveCharacterTextSplitter

Multilingual E5 Embeddings
      
FAISS Vector Database
      
Retriever (MMR Search)
      
Groq LLM
      
Gradio Chat Interface

---

##  Tech Stack

| Component       | Technology                    |
| --------------- | ----------------------------- |
| LLM             | Groq                          |
| Framework       | LangChain                     |
| Vector Database | FAISS                         |
| Embeddings      | intfloat/multilingual-e5-base |
| Frontend        | Gradio                        |
| PDF Processing  | PyPDF                         |
| Authentication  | Custom Login System           |
| Memory          | ChatMessageHistory            |

---

##  Project Structure

```text
project/
│
├── app.ipynb
├── faiss_index/
├── documents/
├── requirements.txt
└── README.md
```

---

##  Installation

### Clone Repository

```bash
git clone https://github.com/yourusername/croco-it-rag.git

cd croco-it-rag
```

### Install Dependencies

```bash
pip install -r requirements.txt
```

or

```bash
pip install \
langchain \
langchain-community \
langchain-text-splitters \
langchain-groq \
langchain-huggingface \
faiss-cpu \
sentence-transformers \
groq \
pydantic \
pypdf \
gradio
```

---

##  Environment Variables

Create a `.env` file:

```env
GROQ_API_KEY=your_groq_api_key

VALID_USERNAME=admin
VALID_PASSWORD=password123
```

---

##  Upload Knowledge Base

Upload any company PDF documentation:

```python
uploaded = files.upload()

pdf_file = list(uploaded.keys())[0]
```

The system will:

* Load the PDF
* Split content into chunks
* Generate embeddings
* Build a FAISS vector database
* Enable semantic retrieval

---

##  Retrieval Strategy

The chatbot uses:

### Embedding Model

```python
intfloat/multilingual-e5-base
```

### Search Method

```python
MMR (Max Marginal Relevance)
```

Configuration:

```python
search_kwargs = {
    "k": 4,
    "fetch_k": 10,
    "lambda_mult": 0.5
}
```

Benefits:

* Better diversity
* Reduced duplicate contexts
* More accurate retrieval

---

##  RAG Workflow

### User Question

```text
What services does Croco IT provide?
```

### Retrieval

Relevant chunks are retrieved from FAISS.

### Context Injection

Retrieved chunks are injected into the prompt.

### LLM Response

Groq generates an answer strictly grounded in the retrieved information.

---

##  Authentication System

The application includes a login layer before users can access the chatbot.

Features:

* Username/password authentication
* Session-based access
* Isolated user conversations

---

##  Conversation Memory

Each user session maintains chat history using:

```python
ChatMessageHistory
```

Capabilities:

* Multi-turn conversations
* Context retention
* Session isolation

---

##  Multilingual Support

The chatbot automatically responds in the same language used by the user.

Supported examples:

* Arabic 🇪🇬
* English 🇺🇸
* Other languages supported by Multilingual-E5

---

##  Launch Application

```python
demo.launch(
    share=True
)
```

Gradio will generate a public URL.

---

##  Use Cases

### Company Assistant

Train on:

* Services
* Pricing
* FAQs
* Policies

### Internal Knowledge Base

Train on:

* SOPs
* Technical documentation
* Employee manuals

### Customer Support

Provide instant answers from company documentation.

### Educational Assistants

Train on:

* Courses
* Books
* Research papers

---

##  Hallucination Protection

The assistant follows strict rules:

* Uses only retrieved information
* Does not invent answers
* Refuses unsupported questions
* Maintains source-grounded responses

Example fallback:

```text
I don't have information about this question
```

---

##  Future Improvements

* Hybrid Search (BM25 + Vector Search)
* Re-ranking Models
* Multi-PDF Knowledge Bases
* Admin Dashboard
* User Analytics
* Document Upload from UI
* Persistent Database Storage
* Docker Deployment
* Cloud Hosting (AWS / GCP / Azure)

---

##  Contributing

Contributions, issues, and feature requests are welcome.

```bash
fork → create branch → commit → pull request
```

---

##  License

MIT License

---

##  Author

Built with  using:

* LangChain
* Groq
* FAISS
* HuggingFace
* Gradio

For production-grade AI assistants and enterprise RAG systems.
