# RAG Pipeline and Chatbot
**AI Knowledge Retrieval & SOP-Bound Conversational Assistant**

A production-ready **Retrieval-Augmented Generation (RAG)** workflow built in **n8n** that ingests company documents, stores them in a vector database, and powers a chatbot that answers questions **strictly from approved internal knowledge**.

This system is designed for **employee support, internal SOP lookup, and client-facing knowledge bases**, with zero hallucination tolerance.

---

## 🎯 What This Workflow Does

- Automatically ingests documents from Google Drive
- Converts files into embeddings and stores them in Pinecone
- Exposes a chat interface that retrieves only relevant SOP content
- Enforces hard guardrails so the chatbot cannot answer outside the knowledge base
- Returns a fallback response when information is missing or unavailable

If it’s not in the SOP, the chatbot does not answer.

---

## 🚀 Key Features

### 📂 Automated Knowledge Ingestion
- Watches a specific Google Drive folder
- Triggers automatically when a new file is uploaded
- Supports continuous knowledge base updates without redeployments

### 🧠 Vector-Based Knowledge Storage
- Uses OpenAI embeddings
- Stores documents in Pinecone under a dedicated namespace
- Keeps ingestion and retrieval pipelines cleanly separated

### 💬 SOP-Bound Chatbot
- Chat-triggered conversational agent
- Must query Pinecone before every response
- Cannot rely on prior knowledge, reasoning, or assumptions

### 🔐 Zero-Hallucination Guardrails
- Hard system rules enforced at the agent level:
  - No guessing
  - No inference
  - No follow-up questions
- If data is missing, returns a fixed, approved message

### 🧩 Modular RAG Architecture
- Separate ingestion pipeline
- Separate retrieval and response pipeline
- Easy to extend to Slack, Telegram, web chat, or internal tools

---

## 🧠 RAG Architecture Overview

### 1. Document Ingestion
- Google Drive Trigger watches a specific folder
- Newly uploaded files are automatically downloaded
- Files are parsed using a document loader

### 2. Embedding & Indexing
- Documents are converted into vector embeddings via OpenAI
- Stored in Pinecone under a defined namespace (`SOP`)
- Existing vectors remain untouched unless manually cleared

### 3. Retrieval
- Chat messages trigger a Pinecone search
- Only relevant SOP passages are returned to the agent
- Pinecone acts as the single source of truth

### 4. Response Generation
- GPT model receives:
  - User query
  - Retrieved SOP content only
- Response must be fully grounded in retrieved data
- If no valid data exists → controlled fallback response

---

## 🛠️ Tech Stack

- n8n – Workflow orchestration
- Google Drive – Document source
- OpenAI – Embeddings and chat model
- Pinecone – Vector database
- LangChain (n8n nodes) – RAG orchestration
- Webhook Chat Trigger – Chat interface entry point

---

## 🗄️ Knowledge Base Setup

### Google Drive
- Upload all SOPs, policies, and internal documents to a single folder
- Any new file added is automatically indexed

### Pinecone
- Index: `clearpath-sop`
- Namespace: `SOP`
- Used for both vector insertion and retrieval

---

## 🤖 Chatbot Behavior & Guardrails

The chatbot is governed by strict rules:

- Must always query the Pinecone tool
- Can only respond using retrieved SOP content
- Cannot:
  - Guess
  - Infer
  - Use general knowledge
  - Ask follow-up questions

### Fallback Response
If the answer is not found in the SOP, the chatbot responds with:

> “I don’t have that information in the company SOP. Please contact support for further assistance.”

No deviations. No extra text.

---

## ⚙️ Installation & Configuration

### 1. Import Workflow
- Open n8n
- Import `RAG Pipeline and Chatbot.json`
- Activate once credentials are set

### 2. Configure Credentials
You’ll need:
- Google Drive OAuth2
- OpenAI API
- Pinecone API

### 3. Update Key Settings
- Google Drive folder ID (knowledge source)
- Pinecone index and namespace
- OpenAI model selection

---

## 🧪 How to Test

### Test Knowledge Ingestion
1. Upload a document to the connected Google Drive folder
2. Confirm vectors are created in Pinecone

### Test Chatbot Retrieval
1. Send a chat message referencing SOP content
2. Verify response matches the document exactly

### Test Guardrails
1. Ask a question not covered in the SOP
2. Confirm fallback message is returned

---

## 💡 Use Cases

- Internal employee SOP assistant
- Client-facing helpdesk chatbot
- Compliance-safe knowledge systems
- AI support agents for regulated industries
- Company policy and documentation lookup
