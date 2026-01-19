# langchain-chatbot-pdf-interview

Repo: https://github.com/iceyisaak/langchain-chatbot-pdf-interview

StreamlitUI: https://langchain-chatbot-pdf-interview.streamlit.app/

---

A conversational RAG (Retrieval-Augmented Generation) application built with **Streamlit**, **LangChain**, and **Groq**. This tool allows users to upload multiple PDF documents and engage in a context-aware dialogue with an AI assistant that answers questions based on the uploaded content.

## 🚀 Features

* **Multi-PDF Support:** Upload and process multiple PDF files simultaneously.
* **Context-Aware Conversation:** Maintains a chat history to understand follow-up questions (e.g., "Tell me more about the first point").
* **Fast Inference:** Powered by **Llama-3.1-8b** via Groq for near-instant responses.
* **Vector Search:** Uses **ChromaDB** and **HuggingFace Embeddings** (`all-MiniLM-L6-v2`) for efficient document retrieval.
* **Session Management:** Support for unique Session IDs to keep different conversations organized.

---

## 🛠️ Tech Stack

| Component | Technology |
| --- | --- |
| **Frontend** | Streamlit |
| **LLM Orchestration** | LangChain |
| **LLM** | Llama 3.1 8B (Groq) |
| **Embeddings** | HuggingFace (Sentence Transformers) |
| **Vector Database** | ChromaDB |
| **Document Loading** | PyPDF |

---

## 📋 Prerequisites

Before running the application, ensure you have:

1. A **Groq API Key** (Get it at [Groq Cloud](https://console.groq.com/)).
2. A **HuggingFace Token** (Required for downloading embedding models).
3. Python 3.9 or higher installed.

---

## ⚙️ Installation & Setup

1. **Clone the repository:**
```bash
git clone https://github.com/iceyisaak/langchain-chatbot-pdf-interview.git
cd langchain-chatbot-pdf-interview

```


2. **Install dependencies:**
```bash
pip install streamlit langchain-groq langchain-huggingface langchain-chroma pypdf python-dotenv langchain-community

```


3. **Create a directory for temporary files:**
The app saves PDFs temporarily for processing.
```bash
mkdir document

```


4. **Run the Application:**
```bash
streamlit run app.py

```



---

## 💡 How to Use

1. **Enter Credentials:** Locate the sidebar and input your Groq API Key and HuggingFace Token.
2. **Upload PDFs:** Drag and drop your documents into the file uploader.
3. **Wait for Indexing:** The app will split the text into chunks and create vector embeddings.
4. **Chat:** Start asking questions in the chat input at the bottom!

---

## 🧠 System Architecture

The app follows these logical steps to provide accurate answers:

1. **Ingestion:** PDF text is extracted and split using `RecursiveCharacterTextSplitter`.
2. **Retrieval:** When you ask a question, the system searches the ChromaDB vector store for the top 5 most relevant document chunks.
3. **Contextualization:** The LLM rewrites your question into a "standalone" query based on chat history.
4. **Generation:** The `Stuff Documents Chain` combines the retrieved context with the prompt and generates a concise (max 3 sentences) answer.

---

## ⚠️ Important Notes

* **Data Privacy:** Uploaded PDFs are stored temporarily in the `./document/` folder. Ensure you do not upload highly sensitive information if running on a shared server.
* **Conciseness:** The system is prompted to keep answers brief (maximum 3 sentences) to ensure clarity and speed.

---
