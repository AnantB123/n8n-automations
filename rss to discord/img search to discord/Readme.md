# 🖼️ Image Search to Discord (n8n Workflow)

This workflow allows you to **type a word or phrase** and automatically **send an image related to it** to a Discord channel — all using **free APIs** and n8n’s native integrations.

---

## 🚀 Features

* Triggered by a **chat message input** inside n8n (e.g., “cat”, “Ferrari”, “mountain”).
* Searches Google Images for the query via **SearchAPI**.
* Downloads the first image result using **HTTP Request**.
* Sends the image and caption to a **Discord channel** automatically.
* Works entirely with the **free version of n8n** — no paid plugins or webhooks required.

---

## ⚙️ Workflow Overview

| Step | Node                           | Purpose                                                            |
| ---- | ------------------------------ | ------------------------------------------------------------------ |
| 1    | **When Chat Message Received** | Captures user input from the n8n chat interface.                   |
| 2    | **Search Google Images**       | Queries Google Images via SearchAPI using the input text.          |
| 3    | **HTTP Request**               | Downloads the first image result in binary format.                 |
| 4    | **Send a Message (Discord)**   | Uploads the image to a Discord channel with a descriptive caption. |

---

## 🧠 How It Works

1. You type a keyword in the n8n chat input (e.g., `Ferrari`).
2. The workflow searches Google Images for that keyword.
3. The first image result is downloaded as binary data.
4. The workflow sends that image to your chosen Discord server/channel.

---

## 🪄 Setup Instructions

### 1. **Import the Workflow**

* In your n8n dashboard, click **Import > From File** and upload the provided `.json` file.

### 2. **Add Credentials**

You’ll need:

* **SearchAPI account** → connect it under “SearchApi account”.
* **Discord OAuth2 connection** → connect your Discord account under “Discord account”.

### 3. **Configure Discord**

* In the **Send a Message** node:

  * Choose your **Server** and **Channel** from the dropdown list.
  * (Optional) Edit the message content if you want to customize formatting.

### 4. **Activate the Workflow**

Once configured, activate it and test by typing a word in the **chat input** panel.

---

## 🧩 Example Output

If you type:

```
Ferrari
```

The bot sends to Discord:

```
Here’s your image of a Ferrari:
```

*(with the first Google Image of a Ferrari attached)*

---

## 🧰 Requirements

* n8n (free version)
* Discord account (for OAuth2 authentication)
* SearchAPI account (for Google Images access)

---

## 📝 Notes

* Safe search is **disabled** by default. You can enable it in the **Search Google Images** node.
* You can modify the number of images fetched or use filters (e.g., color, type, size).
* For stability, it’s recommended to limit to **1 image per request** to avoid API rate limits.

---

## 🧑‍💻 Author

Created by [Your Name]
Part of an ongoing learning series exploring **automation, APIs, and workflow integration** with n8n.
