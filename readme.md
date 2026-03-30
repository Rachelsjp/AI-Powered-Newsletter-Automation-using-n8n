🚀 AI-Powered Newsletter Automation using n8n, Slack & Gmail
📌 Overview

This project automates newsletter generation using AI. A user sends a topic via Slack, and the system automatically generates a structured newsletter, formats it, sends it via email, and confirms delivery in Slack.

🎯 Objective
Automate newsletter creation using AI
Reduce manual effort
Enable real-time content generation
Deliver formatted output via email
Provide instant feedback in Slack
🏗️ Architecture

Workflow:

Slack → n8n Trigger → AI Model → Processing → Gmail → Slack Confirmation

⚙️ Setup Instructions
1️⃣ Start n8n (Local Setup)
n8n start
2️⃣ Start ngrok (Expose Localhost)
ngrok http 5678

Copy the HTTPS URL generated (example: https://xxxxx.ngrok-free.dev
)

3️⃣ Configure Slack App
🔹 Enable Event Subscriptions
Go to Slack Developer Console
Enable Event Subscriptions
Add Request URL:
https://<ngrok-url>/webhook/<your-webhook-id>/webhook
🔹 Subscribe to Events

Add:

message.channels
🔹 OAuth Permissions

Add Bot Token Scopes:

channels:history
channels:read
chat:write

Then install the app to your workspace.

4️⃣ Add Bot to Channel

Invite bot to:

#newsletter
#newsletter-output
/invite @your-bot-name
5️⃣ Gmail OAuth Setup
Create OAuth credentials in Google Cloud
Add redirect URL:
http://localhost:5678/rest/oauth2-credential/callback
Add your Gmail as Test User
Connect Gmail in n8n
🔄 Workflow Explanation
🔹 Slack Trigger

Captures user input from Slack channel.

🔹 Code Node (Input Processing)

Extracts the topic from Slack payload.

🔹 IF Node

Validates input and routes flow.

🔹 AI Model Node

Generates structured newsletter content.

🔹 Code Node (Formatting)

Converts AI output into clean HTML format.

🔹 Gmail Node

Sends the newsletter via email.

🔹 Slack Node (Success)

Sends confirmation message to Slack.

🔹 Slack Node (Error Handling)

Handles invalid inputs.

🧪 Test Scenarios
✅ Valid Input
AI in retail analytics

Output:

Newsletter email sent
Slack confirmation message
❌ Invalid Input
hi

Output:

Error message in Slack
## 📸 Screenshots

### 1. Slack Input  
![Slack Input](Slack Input.png)

---

### 2. Workflow Execution  
![Workflow](Workflow Execution.png)

---

### 3. Email Received  
![Email](Email Received.png)

---

### 4. Slack Output  
![Slack Output](Slack Output.png)

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
Data transformation in n8n
📌 Conclusion

This project demonstrates how AI and automation tools can be combined to build a real-time content generation system. It significantly reduces manual effort and improves efficiency in communication workflows.