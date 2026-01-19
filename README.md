# langchain-chatbot-pdf-interview

Repo: https://github.com/iceyisaak/langchain-chatbot-pdf-interview

StreamlitUI: https://langchain-chatbot-pdf-interview.streamlit.app/

---

# 📚 RAG Chatbot: PDF Interview

A powerful, conversational AI application that allows users to upload multiple PDF documents and engage in a context-aware dialogue about their content. This app uses **Retrieval-Augmented Generation (RAG)** to provide accurate answers based specifically on the documents provided.

## 🚀 Features

* **Multi-PDF Support:** Upload one or several PDF files simultaneously.
* **Conversational Memory:** Remembers previous interactions within a session for follow-up questions.
* **Contextual Retrieval:** Uses a history-aware retriever to understand questions that refer back to earlier parts of the conversation.
* **Efficient Vector Search:** Powered by `ChromaDB` and `HuggingFace` embeddings for fast and relevant document retrieval.
* **Streamlit Interface:** A clean, user-friendly web interface with real-time status updates and spinners.

---

## 🛠️ Technical Stack

* **LLM:** Groq (Llama-3.1-8b-instant)
* **Orchestration:** LangChain
* **Vector Store:** ChromaDB
* **Embeddings:** HuggingFace (`all-MiniLM-L6-v2`)
* **Frontend:** Streamlit

---

## 📋 Prerequisites

Before running the app, ensure you have the following:

1. **Groq API Key:** Obtain one from the [Groq Console](https://console.groq.com/).
2. **HuggingFace Token:** Required for the embedding models.
3. **Python 3.9+** installed on your machine.

---

## ⚙️ Installation & Setup

1. **Clone the repository:**
```bash
git clone https://github.com/iceyisaak/langchain-chatbot-pdf-interview.git
cd langchain-chatbot-pdf-interview

```


2. **Install dependencies:**
```bash
pip install -r requirements.txt

```


*Note: Ensure you include `streamlit`, `langchain`, `langchain_groq`, `langchain_community`, `langchain_huggingface`, `chromadb`, and `pypdf` in your requirements file.*
3. **Run the application:**
```bash
streamlit run app.py

```



---

## 🖥️ How to Use

1. **API Configuration:** Enter your Groq API Key and HuggingFace Token in the sidebar.
2. **Upload Documents:** Drag and drop your PDF files into the file uploader.
3. **Indexing:** The app will automatically split the text into chunks and create a vector store.
4. **Chat:** Start asking questions! You can use a custom **Session ID** to maintain different conversation threads.

---

## 🧠 How it Works

1. **Ingestion:** PDFs are loaded, split into 5000-character chunks with a 200-character overlap.
2. **Embedding:** These chunks are converted into numerical vectors using HuggingFace.
3. **Contextualization:** When you ask a question, the LLM re-writes it to be a "standalone" question based on your chat history.
4. **Retrieval & Generation:** The system finds the top 5 most relevant snippets from your PDFs and sends them to the LLM to generate a concise, 3-sentence answer.

---
