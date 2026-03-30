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

Install the app to your workspace.

4️⃣ Add Bot to Channels
#newsletter
#newsletter-output
/invite @your-bot-name
5️⃣ Gmail OAuth Setup
http://localhost:5678/rest/oauth2-credential/callback
Add Gmail as Test User
Connect in n8n
🔄 Workflow Explanation
🔹 Slack Trigger Node

Captures user input from Slack channel and starts the workflow.

🔹 Code Node (Input Processing)

Extracts the message text from Slack payload and prepares it for processing.

🔹 IF Node (Validation)

Checks whether the input is valid and routes the flow accordingly.

🔹 AI Model Node

Generates structured newsletter content based on the input topic.

🔹 Code Node (Formatting)

Formats the AI output into clean HTML for email readability.

🔹 Gmail Node

Sends the generated newsletter via email.

🔹 Slack Node (Success)

Sends a confirmation message after successful execution.

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

✔ Error message in Slack

📸 Screenshots
1. Slack Input

2. Workflow Execution

3. Email Received

4. Slack Output

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
