# 📚 AI Agent for Book Inventory Store — n8n

An intelligent AI agent built with **n8n** that manages a book inventory store. Simply chat with the agent to search for any book record or update inventory details — no manual database work needed.

---

## 📌 Overview

This agent connects a conversational AI interface to an **Airtable** database containing book records. You can ask it questions like *"Find me the record for Harry Potter"* or say *"Update the stock for Clean Code to 15"* — and it handles everything automatically using natural language.

---

## 🔄 Workflow

<img width="710" height="287" alt="n8n workflow diagram" src="https://github.com/user-attachments/assets/3320d902-ae5a-43f1-bee1-fb1361d698dd" />

```
When chat message received
        │
        ▼
    AI Agent  ──── Groq Chat Model (LLM)
        │       ──── Simple Memory (conversation history)
        │
        ├──── Search records in Airtable  (find a book)
        └──── Update record in Airtable   (update a book)
```

### Node Breakdown

| Node | Type | Purpose |
|------|------|---------|
| When chat message received | Trigger | Listens for incoming user chat messages |
| AI Agent | Core | Orchestrates the conversation and decides which tool to use |
| Groq Chat Model | LLM | Powers the agent's natural language understanding (Groq API) |
| Simple Memory | Memory | Remembers conversation context across messages |
| Search records in Airtable | Tool | Searches the book inventory for a matching record |
| Update record in Airtable | Tool | Updates a book's details in the inventory |

---

## 💬 Example Interactions

Below are real conversations with the agent showing results
<img width="251" height="167" alt="Screenshot 2026-06-24 105151" src="https://github.com/user-attachments/assets/f6825041-5eb5-44b0-b47d-90909ba6f4f7" />



**1. Searching for a book record**

<img width="224" height="204" alt="Screenshot 2026-06-24 110442" src="https://github.com/user-attachments/assets/8d642ed0-5e8c-4706-ba97-7ad199e5986c" />



**2. Fetching full book details**

<img width="244" height="128" alt="Screenshot 2026-06-24 105317" src="https://github.com/user-attachments/assets/7d71ec41-1ae6-4597-9130-28c3b0740447" />
<img width="248" height="206" alt="Screenshot 2026-06-24 105331" src="https://github.com/user-attachments/assets/3767e73d-aa01-4af0-9600-ababe4985cd2" />




---

## ⚙️ Setup Instructions

### Prerequisites

- [n8n](https://n8n.io) installed (self-hosted or cloud)
- A [Groq](https://console.groq.com) API key (free)
- An [Airtable](https://airtable.com) account with a book inventory base set up

### Airtable Base Structure

Create a base in Airtable with a table (e.g., `Books`) containing columns like:

| Field | Type |
|-------|------|
| Title | Single line text |
| Author | Single line text |
| Genre | Single line text |
| Stock | Number |
| Price | Currency |

### Steps

1. **Import the workflow**
   - Open your n8n instance
   - Go to **Workflows → Import from file**
   - Upload `workflow.json`

2. **Configure Groq Chat Model**
   - Add your Groq API key in the Groq Chat Model node
   - Select your preferred model (e.g., `llama3-8b-8192`)

3. **Configure Airtable nodes**
   - Connect your Airtable account in both Airtable nodes
   - Set the correct **Base** and **Table** name in each node

4. **Activate the workflow**
   - Toggle the workflow to **Active**
   - Open the built-in n8n chat interface to start talking to the agent

---

## 🛠️ Tech Stack

| Tool | Purpose |
|------|---------|
| [n8n](https://n8n.io) | Workflow automation & agent orchestration |
| [Groq API](https://groq.com) | Fast LLM inference (LLaMA 3) |
| [Airtable](https://airtable.com) | Book inventory database |
| Simple Memory | Maintains conversation history |

---

## 📁 Repository Structure

```
├── workflow.json       # n8n workflow export
├── README.md           # Project documentation
└── screenshots/        # Workflow and demo screenshots
```

---

## 🚀 Future Improvements

- Add support for **adding new books** to the inventory
- Add support for **deleting** out-of-stock records
- Connect to a **Telegram or WhatsApp** interface
- Generate **inventory summary reports** on request
- Add **low stock alerts** when a book's quantity drops below a threshold

---

## 👤 Author

**Muhammad Zuhaib**  
Computer Systems Engineering Student — Sukkur IBA University  
GitHub: [@Zuhaib23](https://github.com/Zuhaib23)

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).
