🚀 AI-Powered Newsletter Automation using n8n, Slack & Gmail
🎯 Objective

This project automates newsletter generation using AI.
A user sends a topic via Slack, and the system:

Generates a structured newsletter using AI
Formats the content professionally
Sends it via email
Confirms delivery in Slack
🏗️ Architecture Overview

Flow:

Slack → n8n Trigger → AI Model → Processing → Email → Slack Confirmation

⚙️ Setup Instructions
1️⃣ Start n8n (Local Setup)
n8n start
2️⃣ Start ngrok (Expose Localhost)
ngrok http 5678

Copy the HTTPS URL generated (example: https://xxxxx.ngrok-free.dev
)

3️⃣ Configure Slack App
A. Enable Event Subscriptions
Go to Slack Developer Console
Enable Event Subscriptions
Add Request URL:
https://<ngrok-url>/webhook/<your-webhook-id>/webhook
B. Subscribe to Events

Add:

message.channels
C. OAuth Permissions

Add Bot Token Scopes:

channels:history
channels:read
chat:write

Install the app to your workspace.

4️⃣ Add Bot to Channel

Invite bot to channels:

#newsletter
#newsletter-output
/invite @your-bot-name
5️⃣ Gmail OAuth Setup
Create OAuth credentials in Google Cloud
Add redirect URL:
http://localhost:5678/rest/oauth2-credential/callback
Add Gmail as Test User
Connect Gmail in n8n using OAuth2
🔄 Workflow Explanation
🔹 1. Slack Trigger

Listens for new messages in Slack channel and captures the topic input.

🔹 2. Code Node (Input Processing)

Extracts message text from Slack JSON.

🔹 3. IF Node

Validates input and routes valid/invalid requests.

🔹 4. AI Model Node

Generates structured newsletter content using AI.

🔹 5. Code Node (Formatting)

Extracts AI output, converts to HTML, and formats headings, bullets, and structure.

🔹 6. Gmail Node

Sends the formatted newsletter via email.

🔹 7. Slack Node (Success)

Sends confirmation message.

🔹 8. Slack Node (Error Handling)

Handles invalid input and notifies user.

🧪 Test Scenarios
✅ Valid Input

Slack input:

AI in retail analytics

Result:

Email generated
Slack success message
❌ Invalid Input

Slack input:

hi

Result:

Error message in Slack
📸 Screenshots
1. Slack Input

Slack Input.png

2. Workflow Execution

Workflow Execution.png

3. Email Received

Email Received.png

4. Slack Output

Slack Output.png

🚀 Features
End-to-end automation
Slack-based trigger
AI-powered content generation
HTML email formatting
Error handling using IF node
Multi-system integration
🧠 Learnings
Webhooks using ngrok
Slack Event Subscriptions
OAuth2 authentication (Gmail)
AI integration in workflows
Data transformation in n8n
📌 Conclusion

This project demonstrates how AI and automation tools can be integrated to build a real-time content generation system, reducing manual effort and improving efficiency.