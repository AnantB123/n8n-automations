# RSS to Discord Automation (n8n)

This workflow automatically fetches new articles from the **Wired RSS feed** and posts them to a **Discord channel** via webhook.

---

## ⚙️ How It Works

1. **Trigger:** The workflow runs every minute using the **RSS Feed Trigger** node.
2. **Processing:** A **JavaScript Code** node processes the feed data (you can add filters or formatting logic here).
3. **Action:** An **HTTP Request** node sends the article title and link to Discord using a webhook URL.

---

## 🧩 Setup Instructions

1. In your Discord server, go to **Server Settings → Integrations → Webhooks** and create a new webhook.
2. Copy the webhook URL and replace the `placeholder` in the workflow’s HTTP Request node with your URL.
3. Import the workflow JSON file into **n8n**.
4. Activate the workflow — it will start posting new articles automatically.

---

## 🧠 Example Output

> 📰 *New Article:* “The Wired Guide to AI”
> [https://www.wired.com/story/the-wired-guide-to-ai/](https://www.wired.com/story/the-wired-guide-to-ai/)

---

## 💡 Notes

* You can replace the Wired RSS feed URL with any RSS feed you want.
* The JavaScript node can be customized to add filters, summaries, or AI processing later.

---

**Author:** [Your Name]
**Built with:** n8n (Local Open Source)
