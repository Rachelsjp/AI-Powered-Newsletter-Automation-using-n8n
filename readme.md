🚀 AI-Powered Newsletter Automation using n8n, Slack & Gmail
📌 Overview

This project demonstrates an end-to-end automation workflow that generates and delivers AI-powered newsletters in real-time.

A user provides a topic through Slack, which triggers an automated pipeline in n8n. The system processes the input, generates structured content using an AI model, formats it into a readable newsletter, sends it via Gmail, and confirms the delivery back in Slack.

This simulates a real-world automation use case for marketing, reporting, and communication workflows.

🎯 Objective

The goal of this project is to:

Automate newsletter creation using AI
Reduce manual effort in content generation
Enable real-time interaction through Slack
Deliver structured and formatted output via email
Provide instant feedback to the user
🏗️ Architecture
🔄 Workflow

Slack → n8n Trigger → AI Model → Processing → Gmail → Slack Confirmation

⚙️ Setup Instructions
1️⃣ Start n8n (Local Setup)
n8n start

This starts n8n at:
http://localhost:5678

2️⃣ Start ngrok (Expose Localhost)
ngrok http 5678

Copy the HTTPS URL generated
Example: https://xxxxx.ngrok-free.dev

3️⃣ Configure Slack App
🔹 Enable Event Subscriptions
Go to Slack Developer Console
Enable Event Subscriptions
Add Request URL:
https://<ngrok-url>/webhook/<your-webhook-id>/webhook
🔹 Subscribe to Events
message.channels
🔹 OAuth Permissions

Add Bot Token Scopes:

channels:history
channels:read
chat:write

Install the app to your workspace.

4️⃣ Add Bot to Channels

Add bot to:

#newsletter
#newsletter-output
/invite @your-bot-name
5️⃣ Gmail OAuth Setup

Add redirect URL:

http://localhost:5678/rest/oauth2-credential/callback
Add your Gmail as Test User
Connect Gmail in n8n
🔄 Workflow Explanation
🔹 Slack Trigger Node

Captures user input from Slack and starts the workflow.

🔹 Code Node (Input Processing)

Extracts $json.text and prepares clean input.

🔹 IF Node (Validation)

Validates input and routes flow (true/false).

🔹 AI Model Node

Generates structured newsletter content.

🔹 Code Node (Formatting)

Formats AI output into HTML email content.

🔹 Gmail Node

Sends the newsletter email.

🔹 Slack Node (Success)

Sends confirmation message after success.

🔹 Slack Node (Error Handling)

Handles invalid input and informs the user.

🧪 Test Scenarios
✅ Valid Input

AI in retail analytics

✔ Newsletter generated
✔ Email sent
✔ Slack confirmation

❌ Invalid Input

hi

✔ Error message shown in Slack

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

🚀 Features
End-to-end automation
AI-powered content generation
Slack integration
Email automation
Input validation
Structured HTML formatting
🧠 Learnings
Webhooks using ngrok
Slack Event Subscriptions
OAuth2 authentication (Gmail)
AI integration in workflows
Data transformation using n8n
📌 Conclusion

This project demonstrates how AI and automation tools can be combined to build a real-time content generation system, reducing manual effort and improving efficiency.
