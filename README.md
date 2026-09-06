# 🤖 Lead Qualification Agent (n8n)

An AI-powered Telegram bot built with **n8n** that conducts a natural conversation with real estate leads, collects key information, scores the lead internally, saves the results to Google Sheets, and routes the lead based on their score — all without ever revealing the scoring logic to the user.

---

## 🧩 What it does

1. **Triggers** on any new message sent to a Telegram bot.
2. An **AI Agent** (powered via OpenRouter) engages the user in a friendly, step-by-step conversation to collect:
   - Property type (Apartment / Villa / Commercial)
   - Buy or Rent
   - New or Resale
   - First-time buyer status
   - Timeline to move in
   - Budget range
   - Full name & email
3. The agent **confirms** all details with the user before saving anything.
4. It calculates an **internal lead score (0–100)** based on weighted criteria (property type, urgency, budget, etc.) — this score is never shown to the user.
5. Once confirmed, it **saves the lead** to a connected Google Sheet via a tool call.
6. Based on the score:
   - **High score (≥80):** the bot invites the user to book a follow-up call.
   - **Medium/Low score (<80):** the bot lets them know a team member will follow up.
7. A **memory buffer** keeps track of the conversation per Telegram chat so the bot doesn't repeat questions.

---

## 🛠️ Tools & Nodes Used

| Node | Purpose |
|---|---|
| Telegram Trigger | Listens for incoming messages |
| If | Filters which chats are allowed to interact with the bot |
| AI Agent (LangChain) | Core conversational logic & lead scoring |
| OpenRouter Chat Model | LLM powering the agent |
| Simple Memory (Buffer Window) | Keeps conversation context per user |
| Google Sheets Tool | Saves qualified lead data |
| Telegram (Send Message) | Replies to the user |

---

## ⚙️ How to Use This Workflow

1. Import `Lead_Qualification_Agent.json` into your n8n instance (**Workflows → Import from File**).
2. Set up your own credentials for:
   - Telegram Bot API
   - OpenRouter API (or swap for any other LLM provider node)
   - Google Sheets OAuth2
3. Replace the placeholder values in the workflow:
   - `YOUR_TELEGRAM_CHAT_ID` — the chat ID(s) allowed to use the bot
   - `YOUR_GOOGLE_SHEET_ID` — your own Google Sheet ID for storing leads
4. Create a Google Sheet with these columns: `Property type`, `Buy/Rent`, `New/Resale`, `First purchase`, `Timeline`, `Budget`, `Name`, `Email`, `Score`.
5. Activate the workflow and start chatting with your Telegram bot 🚀

---

## 💡 Why I built this

Built as a hands-on project during an **AI Automation** course, to practice combining conversational AI agents, external tool calls, and structured data collection into a real, usable workflow.

---

## 📌 Note

All credentials and personal identifiers have been removed/replaced with placeholders in this repo for security. You'll need to plug in your own.
