
# 🚀 AI-Powered Newsletter Automation using n8n, Slack & Gmail

An end-to-end **AI-driven automation system** that generates and delivers newsletters in real time using Slack, n8n, and Gmail.

---

## 🔥 Project Overview

This project demonstrates how to build a real-world automation pipeline that:

- 📩 Takes user input directly from Slack  
- ⚙️ Triggers workflow in n8n  
- 🤖 Uses AI to generate newsletter content  
- 🧾 Formats content into email  
- 📧 Sends via Gmail  
- ✅ Confirms delivery in Slack  

---

## 🎯 Objective

- Automate newsletter creation using AI  
- Reduce manual effort  
- Enable real-time interaction  
- Deliver structured email output  
- Provide instant feedback  

---
## 🏗️ Architecture


Slack (User Input)
│
▼
n8n Webhook Trigger
│
▼
Input Processing (Code Node)
│
▼
Validation (IF Node)
│
▼
AI Model (Content Generation)
│
▼
Formatting (HTML Email)
│
▼
Gmail (Send Email)
│
▼
Slack Confirmation (Success/Error)

---

---

## 🔄 Workflow Explanation

### 🔹 Slack Trigger Node  
Captures user input and initiates the workflow.

### 🔹 Code Node (Input Processing)  
Extracts `$json.text` and cleans the input.

### 🔹 IF Node (Validation)  
Validates input and controls workflow execution.

### 🔹 AI Model Node  
Generates structured newsletter content.

### 🔹 Code Node (Formatting)  
Formats output into HTML email.

### 🔹 Gmail Node  
Sends the newsletter email.

### 🔹 Slack Node (Success)  
Confirms successful execution.

### 🔹 Slack Node (Error Handling)  
Handles invalid inputs and errors.

---

## ⚙️ Setup Instructions

1️⃣ Start n8n
n8n start
Access:
http://localhost:5678

2️⃣ Start ngrok
ngrok http 5678
Example:
https://xxxxx.ngrok-free.dev

3️⃣ Configure Slack App
Enable Event Subscriptions
Request URL:
https://<ngrok-url>/webhook/<your-webhook-id>/webhook
Subscribe to Events
message.channels
OAuth Permissions
channels:history
channels:read
chat:write

4️⃣ Add Bot to Channels
#newsletter
#newsletter-output
/invite @your-bot-name

5️⃣ Gmail OAuth Setup
Redirect URL:
http://localhost:5678/rest/oauth2-credential/callback
Add Gmail as test user
Connect Gmail in n8n

---

## 🧪 Test Scenarios
✅ Valid Input
AI in retail analytics
✔ Newsletter generated
✔ Email sent
✔ Slack confirmation

❌ Invalid Input
hi
✔ Error shown in Slack

---

## 📸 Screenshots

### 1. Slack Input
![Slack Input](screenshots/slack-input.png)

---

### 2. Workflow Execution
![Workflow](screenshots/workflow.png)

---

### 3. Email Received
![Email](screenshots/email.png)

---

### 4. Slack Output
![Slack Output](screenshots/slack-output.png)

---

## Key Features

•	End-to-end automation
•	AI-powered content generation
•	Slack integration
•	Email automation
•	Input validation
•	HTML formatting
---

## 🧠 Key Learnings

•	Automation + AI integration
•	Webhooks for real-time systems
•	Importance of validation
•	Workflow orchestration using n8n
•	AI as part of larger system

---

## 💼 Use Cases

•	Marketing newsletters
•	Business reports
•	Internal communication
•	Content automation

---

## ⚡ Future Improvements

•	Scheduled automation
•	Personalization
•	CRM integration
•	Multi-language support

---

## 👩‍💻 Developed By

Rachel Purnima J

---
📌 Note

This project was built as part of hands-on learning in:
•	n8n workflow automation
•	Slack integrations
•	Gmail OAuth
•	AI-powered content generation

---

## 🌟 Final Thought

Building GenAI systems is not just about generating content —
👉 It's about connecting systems, automating workflows, and delivering real value.

