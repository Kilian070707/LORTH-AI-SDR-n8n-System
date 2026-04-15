# 🚀 Fully Autonomous AI SDR (n8n + Gemini 2.5)

This repository contains the exported JSON workflows to build a complete, autonomous outbound/inbound sales system using **n8n, Google Gemini 2.5, and NocoDB**. 

It is designed to replace expensive sending tools (like Lemlist/Instantly) by handling inbox rotation natively, and acts as an AI Sales Rep by scoring leads, classifying replies, and drafting responses.

## 🏗️ The Architecture (Core Workflows)

* **🧠 1. Lead Qualification:** Triggers every minute, fetches leads from NocoDB, scrapes their website via Browserless, and uses Gemini to score them /100 based on B2B buying signals (High-ticket, inbound strategy, etc.).
* **✉️ 2 & 3. Email Writing & Sending (10-Inbox Rotation):** Generates highly personalized cold emails based on scraped CTA buttons. Uses a custom Javascript routing system to distribute the sending load across 10 different email domains, incorporating randomized human-timing delays to bypass spam filters.
* **🤖 5 & 6. Speed-To-Lead & Intent Classifier:** An IMAP node reads all 10 inboxes simultaneously. It filters out bounces, and sends the actual replies to Gemini. Gemini classifies the intent (Positive, Question, Objection, Negative, Absent), tags the exact objection type, and drafts a contextual reply.
* **👾 Discord Command Center:** If human intervention is needed (Question or Objection), the system pings a dedicated Discord channel with the prospect's message, the AI analysis, and the drafted response.

## ⚙️ How to Install & Use

1. Download the `.json` files from this repository.
2. Go to your n8n instance and create a new workflow.
3. Click on the top-right menu and select **"Import from File"** (or simply copy the raw JSON content and paste it directly onto the n8n canvas).
4. **Re-configure your Credentials:** For security reasons, all credentials have been sanitized. You will need to:
   * Reconnect your own NocoDB / Airtable nodes.
   * Add your own SMTP/IMAP credentials for your email sending domains.
   * Insert your Browserless API URL.
   * Insert your Discord Bot Token and Guild/Channel IDs where `YOUR_DISCORD_TOKEN` or `YOUR_CHANNEL_ID` are mentioned.
5. **Customize the Prompts:** Open the Gemini nodes and replace `[YOUR COMPANY NAME]` and `[YOUR HIGH-TICKET PRICE]` with your actual ICP and offers.

## ⚠️ Disclaimer
This system was built for a specific B2B RevOps agency use case. Make sure to review the Javascript nodes (especially the inbox routing and bounce management regex) to adapt them to your own domain names.

Happy building! 🛠️
