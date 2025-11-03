# 🧠 X (Twitter) Automation Workflow using n8n + Gemini AI

This **n8n** workflow automatically generates tweet-sized posts from RSS feeds using **Google Gemini** (or any other AI model) — then sends them to **X (Twitter)**.

> ⚠️ **Important:** Due to Twitter API restrictions, you need a **Basic or Pro Twitter API subscription** to actually post tweets.

---

## ⚙️ Workflow Overview

### 🕒 1. Schedule Trigger

Runs the workflow at a scheduled time (e.g., once per day at 20:00).

### 📰 2. RSS Read

Fetches articles from any RSS feed.
Replace the sample URL in the node with your own feed source.

### 🔢 3. Limit

Restricts how many RSS items are processed per run (useful to avoid flooding).

### 🤖 4. AI Agent

Uses an AI model (like Gemini) to summarize and craft an engaging tweet.
It runs the following prompt:

```text
Use the information from {{ $json.title }} and {{ $json.summary }} to write a short, engaging tweet for X (Twitter).
Mention the {{ $json.author }} and include the website {{ $json.link }} as the source.
Visit the {{ $json.link }} to extract any extra useful context or key details that make the tweet more authentic or interesting.
The tweet must include the relevant image from the article.
Write naturally, as if you’re an experienced Twitter user who posts concise, scroll-stopping content. Use relevant hashtags.
Don’t ask for clarification or explain your reasoning.
Output only the tweet text itself — no introductions or commentary.
```

### 🧩 5. Any AI Chat Model

Connects to **Google Gemini** (or any supported AI model).
Add your API credentials for Gemini or another model provider.

### 🐦 6. Create Tweet

Posts the generated text to X (Twitter).
This step **requires** Twitter API **Basic or Pro** access.
If you’re on the free tier, the tweet won’t actually post — see alternatives below.

---

## 🚧 Limitations & Alternatives

### ❌ Free API Limitation

* The **free X API** cannot create or post tweets.
* Only **Basic** ($100/month) or **Pro** tiers allow write access.

### ✅ Workarounds

* Use **Buffer**, **Typefully**, or **Publer** for posting.
  You can connect them using an **HTTP Request Node** or **Webhook**.
* Or let this workflow only **generate and store** tweet drafts in Google Sheets, Notion, or Airtable for manual posting.

---

## 🧠 Setup Instructions

1. **Import** this workflow JSON file into n8n.
2. Update the **RSS Read** node with your preferred feed URL.
3. Connect credentials for:

   * Google Gemini (or another AI model)
   * Twitter (X), if you have API access
4. (Optional) Customize the AI prompt to match your preferred tone or niche.
5. Activate or manually run the workflow to test.

---

## 🖼️ Example Workflow Layout

![Workflow Preview](./94f02ab1-2558-47f7-834f-63ca5f42d259.png)

---

## 🪶 Notes

* This project is for **educational and experimental** purposes.
* You can easily adapt it for **LinkedIn**, **Mastodon**, or **Bluesky** posting instead.
* Remember to follow platform ToS and rate limits.

---

## 📜 License

**MIT License** — feel free to fork, adapt, and modify.

---

### 🌐 Repository Info

**Description:**
Automated AI-powered tweet generation from RSS feeds using n8n + Google Gemini.

**Tags:**
`n8n` `automation` `gemini` `twitter` `x-api` `rss` `ai-content` `workflow` `langchain`
