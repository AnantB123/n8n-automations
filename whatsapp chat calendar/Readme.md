# WhatsApp AI Calendar Chat  
An n8n automation workflow that turns WhatsApp into your personal AI-powered Google Calendar assistant.  
Ask about your schedule, create events, update appointments, or delete meetings — all through WhatsApp messages.

This workflow uses:
- **WhatsApp Trigger** (via n8n WhatsApp integration)
- **Google Gemini** as the LLM
- **Google Calendar Tools** (get, create, update, delete)
- **n8n Agent node** for natural-language tool calling

---

## 🚀 Features

### ✓ Read your schedule  
Ask things like:
- *"What’s on my calendar today?"*  
- *"Do I have time at 3 pm?"*  
- *"What meetings do I have tomorrow?"*

The bot retrieves events, summarizes them, and replies via WhatsApp.

---

### ✓ Create events  
Examples:
- *"Add a meeting with John tomorrow at 2 pm to 3 pm"*  
- *"Schedule a dentist appointment on Monday at 10"*  

If something is missing (title, time, etc.), the bot asks for clarification.

---

### ✓ Update events  
Examples:
- *"Move my 2 pm meeting to 4 pm"*  
- *"Change the title of my event to 'Project Sync'"*  
- *"Reschedule tomorrow’s call to next week"*  

The bot:
1. Retrieves matching events  
2. Asks you to confirm which one  
3. Updates it using the Google Calendar tool

---

### ✓ Delete events  
Examples:
- *"Cancel my meeting at 11"*  
- *"Delete my dentist appointment"*  

If needed, the bot lists recent events so you can choose which one to delete.

---

## 🧠 How It Works

The workflow uses an **AI Agent** node with a custom system prompt that teaches Gemini how to select the correct tool:

Tools available to the bot:
1. **Get Events Info** – fetch events by date range  
2. **Create an event** – title, start, end  
3. **Update an event** – modify existing event fields  
4. **Delete an event** – delete using event ID  

The AI decides which tool to call based on natural language in WhatsApp messages.

---

## 🏗️ Workflow Structure

**Nodes included:**
- WhatsApp Trigger  
- Google Gemini Chat Model  
- AI Agent  
- Get Events Info  
- Create an event  
- Update an event  
- Delete an event  
- Send WhatsApp Message  

**Flow:**

WhatsApp Message → AI Agent → Google Calendar Tools → AI Agent → WhatsApp Reply


The agent orchestrates everything.

---

## 📦 Installation

1. Import the workflow JSON into n8n.  
2. Add and configure:
   - WhatsApp credentials
   - Google Gemini (PaLM API) key
   - Google Calendar OAuth credentials  
3. Enable the workflow.  

You're ready.

---

## 💬 Example Conversations

**You:** What’s on my calendar today?  
**Bot:** You have 2 events:  
• Team Sync at 10:00  
• Gym at 18:00  

**You:** Move the team sync to 3 pm.  
**Bot:** Updated!

**You:** Delete the gym event.  
**Bot:** Done.

**You:** Add a meeting with Sarah tomorrow from 2 to 4.  
**Bot:** Event created.

---

