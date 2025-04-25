# 🤖 AI-Powered Document Query Chatbot using n8n + Supabase

Built by **Ankit Choubey**, this project was born out of 6+ years navigating the complex, high-stakes world of sales. From EdTech boardrooms to real estate expose, I always saw one common challenge: **too much scattered information, and too little time to recall it** when it matters most.

So I built this — a **Retrieval-Augmented Generation (RAG)** agent powered by n8n, LangChain, and Supabase — designed not just to answer questions, but to **reason through documents like a sales-savvy assistant.**

---

## 🚀 Why This Matters

Imagine you're talking to a customer. They ask, "What’s the difference between Plan A and Plan B?" or "When does our next installation milestone hit?" or "Can you send me that ROI doc again?"

Instead of scrambling through folders or pinging your team, this agent **remembers**, understands, and **responds instantly**.

And that’s just the start.

- ✅ Acts like your **real-time sales co-pilot**
- 🧠 Recalls product specs, pricing docs, call summaries
- 📚 Reads and summarizes proposals, PDFs, and Excel data
- 💬 Works as a knowledge-driven support agent
- 🎯 Can track leads, respond to objections, or coach reps in live deals

> **This isn’t just a chatbot. It’s the future of intelligent sales enablement.**

---

## 🧠 Key Features

- 📂 **Live File Monitoring** – Google Drive triggers for new/updated documents
- 📄 **Multi-Format Support** – PDF, Google Docs, XLSX, CSV, plain text
- 🧩 **RAG Pipeline** – intelligently splits, embeds, and stores content
- 📊 **SQL Queries on Tables** – asks complex questions on structured data
- 💬 **Conversational Interface** – long-term memory via Postgres + OpenAI

---

## 🏗️ Architecture Overview

```
Google Drive
   └── Trigger → Download → Type Switch
         ├── PDF/TXT/DOC  → Text Extraction → Vector Embedding → Supabase
         └── Excel/CSV    → Row Parsing → JSON Storage → Postgres

User Query
   └── Chat Trigger → LangChain Agent → Tool Selection (RAG / SQL / Full Text)
```

---

## 🔧 Tech Stack

| Component     | Tool                         |
|--------------|------------------------------|
| Workflow     | n8n                          |
| File Storage | Google Drive                 |
| Vector Store | Supabase (pgvector)          |
| LLM          | OpenAI / OpenRouter          |
| Memory       | Postgres (per-session)       |
| Tables       | JSONB rows in `document_rows`|

---

## 📦 Setup Instructions

### 1. Import the Flow

- Upload `Rag_base_query_chat_bot-2.json` into your n8n instance.

### 2. Set Up Credentials

- Google Drive OAuth2
- Supabase API
- Postgres Connection
- OpenAI or OpenRouter key

### 3. Create Tables

Manually execute:
- `Create Documents Table and Match Function`
- `Create Document Metadata Table`
- `Create Document Rows Table`

These initialize `documents`, `document_metadata`, and `document_rows`.

### 4. Set Google Drive Folder

Update `folderToWatch` in `File Created` and `File Updated` trigger nodes.

### 5. Chat With Your Agent

Use the **`Chat Trigger`** node in your n8n UI to initiate queries. You can connect this to:

- A front-end chatbot (via WebSocket or HTTP API)
- A low-code UI (e.g., Streamlit, Flutterflow, Typedream)
- Slack, Discord, or WhatsApp integrations via webhook triggers

---

## 🧪 Example Use Cases

### 🔥 Real-Time Sales Assistant

- Remembers all product PDFs, pricing Excel sheets, FAQs
- Handles customer queries during demos or cold calls
- Suggests responses, sets reminders, answers follow-up questions

### 🙋‍♀️ Customer Support

- Reads internal docs, returns warranty info or onboarding steps
- Pulls answers from updated Google Drive folders
- Learns from past tickets, gets smarter over time

### 📈 Lead Management / Sales Enablement

- Stores call transcripts
- Finds pain points
- Triggers automation for next steps

**This agent becomes your battle-tested sales sidekick.**

---

## 🛠️ Inside the Workflow

- **Triggers**: File Created / Updated in Drive
- **Extractors**: PDF/Text vs Excel/CSV extractors
- **Storage**: Embeddings → Supabase, Tables → Postgres
- **LangChain Agent**: Selects right tool (RAG, SQL, full text)
- **Chat Memory**: Retains previous context per user/session

---

## 💡 Limitless Extensions

- Add Slack, WhatsApp, or Web chat interface
- Use summaries in CRM follow-ups
- Log chat analytics for training
- Expand knowledge base to include call notes, case studies, etc.

---

## 👤 About the Creator

I'm **Ankit Choubey** — with a background in EdTech, real estate, and now renewable energy. Over 6 years leading sales teams taught me this:

> The rep with the fastest, most accurate answer wins the deal.

This project is my vision of an AI assistant that closes more, forgets nothing, and works 24/7.

Let’s build smarter, together.

---

## 📎 License

MIT

