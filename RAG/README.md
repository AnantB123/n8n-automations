# 🧠 RAG Workflow in n8n (Gemini + Supabase + Postgres)

This repository contains a fully working **Retrieval-Augmented Generation (RAG)** workflow built inside **n8n**, using:

- **Google Gemini** for embeddings and chat generation  
- **Supabase** as a vector store for retrieval  
- **Postgres** for conversational memory  
- Optional **image and web search integrations**

It demonstrates how to ingest documents, embed them, store and retrieve relevant context, and generate grounded, low-hallucination answers.

---

### 🔄 Workflow Summary

1. **Manual or Chat Trigger** — starts the workflow  
2. **Google Drive Node** — downloads the document  
3. **Default Data Loader** — parses text from PDFs or other files  
4. **Gemini Embeddings** — converts text into 768-dimensional vectors  
5. **Supabase Vector Store (Insert)** — stores embeddings and metadata  
6. **Supabase Vector Store (Retrieve)** — retrieves contextually relevant chunks  
7. **Postgres Chat Memory** — manages short-term conversation memory  
8. **Gemini Chat Model** — generates concise answers  
9. **AI Agent Node** — orchestrates all tools, memory, and model logic  

---

## ⚙️ Setup Instructions

### 1. Prerequisites

You’ll need:
- [n8n](https://n8n.io) (cloud or self-hosted)
- A **Google Gemini API key**
- A **Supabase** project with `pgvector` enabled
- A **Postgres** database (can be your Supabase one)
- (Optional) **Tavily API key** for web search functionality

---

### 2. Import the Workflow

1. Open **n8n**  
2. Go to **Import Workflow** → upload `RAG.json`  
3. Update your credentials:
   - `Google Gemini(PaLM) API account`
   - `Supabase account`
   - `Postgres account`
4. Replace all `"YourID"` and `"PLACEHOLDER"` values  
5. Update your Webhook ID if you’re using the **Chat Trigger** node  

---

## 🧱 Node-by-Node Explanation

| Node | Type | Purpose |
|------|------|----------|
| **When clicking ‘Execute workflow’** | Trigger | Starts the workflow manually |
| **Google Drive (Download file)** | Integration | Downloads a document from Google Drive |
| **Default Data Loader** | Data Loader | Parses text and prepares it for embedding |
| **Embeddings Google Gemini** | Embedding | Converts text chunks into 768-dim vectors |
| **Supabase Vector Store (Insert)** | Database | Inserts embeddings into `geminidocuments` |
| **Supabase Vector Store (Retrieve)** | Database Tool | Retrieves relevant chunks for context |
| **Postgres Chat Memory** | Memory | Keeps short-term chat context |
| **Google Gemini Chat Model** | LLM | Generates context-aware answers |
| **AI Agent** | Controller | Coordinates memory, vector retrieval, and the chat model |
| **Chat Trigger (Optional)** | Trigger | Enables live chat interaction |

---

## 🧠 How It Works

1. The workflow downloads and processes a document.  
2. Text is chunked and embedded using **Gemini embeddings (768 dimensions)**.  
3. Embeddings are saved in **Supabase** for retrieval.  
4. When the user asks a question:
   - The **AI Agent** retrieves similar content from Supabase.  
   - The **Gemini Chat Model** answers based on that retrieved context.  
   - **Postgres Memory** maintains conversation history for follow-ups.  

This architecture ensures accurate, context-grounded responses while minimizing hallucination.

---

## 🧩 Notes & Troubleshooting

- If you see the error  
  > `expected 1536 dimensions, not 768`  
  it means your Supabase table uses a different vector size than Gemini’s embeddings.  
  Gemini embeddings produce **768 dimensions**, while OpenAI’s produce **1536**.  
  Make sure your table matches your chosen embedding model.

- You can add a **Function Node** after memory to extract recent entities (useful for image or follow-up search).  
- Extend your agent with:
  - **Google Image Search** to fetch relevant visuals
  - **Tavily Web Search** for live web results  

---

## 💡 Future Improvements

- Add **long-term summarization memory** for extended conversations  
- Introduce **metadata-based retrieval filters** (e.g., document type or topic)  
- Add **quality checks** or **hallucination detection nodes**  
- Deploy via **n8n Cloud** or a Docker container for persistent operation  

---

## 📊 Example Output

<p align="center">
  <img src="./images/sample-chat.png" width="450" alt="Example of Gemini RAG chat response">
</p>

---

## 🧾 License

**MIT License** — free to use, modify, and distribute.  
Please provide attribution if you fork or reference this workflow.

---

## 🧠 Author Notes

This workflow demonstrates how to build a modular, low-latency **RAG system**  
entirely within n8n using:

- **Gemini embeddings (768-dim)**  
- **Supabase** as the vector database  
- **Postgres** for conversation memory  

It’s designed for learning, experimentation, and real-world RAG projects —  
with full transparency and no hidden scripts or dependencies.

---

<p align="center">
  <sub>Built with 💡 by a psychology student passionate about AI workflows and mental-model engineering.</sub>
</p>

