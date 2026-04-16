# 🚀 Fully Autonomous AI SDR (n8n + Gemini 2.5 + NocoDB)

Hi everyone, today I'm sharing one of the **most complex workflows** I've built on n8n. It solves a big problem, and is a life-saver (and **budget-saver** too !) for founders who wants to launch a business but don't have much funds.

**The problem:** B2B Agencies and Scale-ups waste an average of 48 hours to reply to inbound leads. By that time, the prospect has already booked a call with a competitor. 

**The solution:** I built this "Speed-to-Lead" infrastructure. It intercepts inbound leads, scrapes their website, scores them with AI, and sends a hyper-personalized email in **under 90 seconds**. 

This repository contains the exported JSON workflows to build this complete, autonomous outbound/inbound sales system using n8n.

*<img width="1440" height="810" alt="Capture d’écran 2026-04-15 à 22 46 32" src="https://github.com/user-attachments/assets/d29f12e4-8b16-4d78-a54b-f1f506677a66" />*

---

## 🏗️ The Architecture (Core Workflows)

* **🧠 1. Lead Qualification:** Triggers every minute, fetches leads from NocoDB, scrapes their website via Browserless, and uses Gemini to score them /100 based on B2B buying signals (High-ticket, inbound strategy, etc.).
* **✉️ 2 & 3. Email Writing & Sending (10-Inbox Rotation):** Generates highly personalized cold emails based on scraped CTA buttons. Uses a custom Javascript routing system to distribute the sending load across 10 different email domains, incorporating randomized human-timing delays to bypass spam filters.
* **🤖 5 & 6. Speed-To-Lead & Intent Classifier:** An IMAP node reads all 10 inboxes simultaneously. It filters out bounces, and sends the actual replies to Gemini. Gemini classifies the intent (Positive, Question, Objection, Negative, Absent), tags the exact objection type, and drafts a contextual reply.
* **👾 Discord Command Center:** If human intervention is needed, the system pings a dedicated Discord channel with the prospect's message, the AI analysis, and the drafted response.

---

## ⚙️ How to Install & Use (For Builders)

1. Download the `.json` files from this repository.
2. Go to your n8n instance and select "Import from File".
3. **Re-configure your Credentials:** Connect NocoDB, your 10 SMTP/IMAP credentials, Browserless API, and Discord Bot Tokens.
4. **Customize the Prompts:** Open the Gemini nodes and replace `[YOUR COMPANY NAME]` and `[YOUR HIGH-TICKET PRICE]` with your actual ICP.
5. *Disclaimer: Review the Javascript nodes (especially the inbox routing regex) to adapt them to your own domain names.*

---

## 💼 Want this running in your agency by next week? (For Founders)

If you are a founder and you want to stop losing leads, but you don't have 40 hours to spend debugging API webhooks, writing Javascript regex, and setting up NocoDB databases... **I can build it for you.**

I install this exact Revenue Infrastructure for B2B companies. You get the system, the landing page, and the automation, entirely done-for-you.

👉 **[Send me a DM on Reddit here](https://www.reddit.com/message/compose/?to=OkPizza8463&subject=Interested%20in%20Custom%20AI%20SDR%20Setup)** or **[Book a free audit call with me here](https://cal.com/kilian-lrth-m3mlvh/audit)**.
*(I only take 2 custom setups per month to ensure quality).*
