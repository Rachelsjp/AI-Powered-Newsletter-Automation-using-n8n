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
🔍 Explanation
Slack acts as the input interface
n8n orchestrates the workflow execution
AI generates the newsletter content
Gmail delivers the final output
Slack provides user feedback
⚙️ Setup Instructions
1️⃣ Start n8n (Local Setup)

Run the following command:

n8n start

This starts the n8n server locally (default: http://localhost:5678
).

2️⃣ Start ngrok (Expose Localhost)
ngrok http 5678

ngrok generates a public HTTPS URL that allows Slack to communicate with your local n8n instance.

Example:

https://xxxxx.ngrok-free.dev
3️⃣ Configure Slack App
🔹 Enable Event Subscriptions
Go to Slack Developer Console
Enable Event Subscriptions
Add Request URL:
https://<ngrok-url>/webhook/<your-webhook-id>/webhook

This allows Slack to send events to your n8n workflow.

🔹 Subscribe to Events

Add the following event:

message.channels

This ensures messages posted in the channel trigger the workflow.

🔹 OAuth Permissions

Add the following Bot Token Scopes:

channels:history
channels:read
chat:write

Install the app to your workspace after adding permissions.

4️⃣ Add Bot to Channels

Invite the bot to both channels:

#newsletter (input channel)
#newsletter-output (response channel)

Command:

/invite @your-bot-name
5️⃣ Gmail OAuth Setup
Create OAuth credentials in Google Cloud
Add redirect URL:
http://localhost:5678/rest/oauth2-credential/callback
Add your Gmail ID as a Test User
Connect Gmail in n8n using OAuth2
🔄 Workflow Explanation (Detailed)
🔹 1. Slack Trigger Node

This node listens for new messages in a specified Slack channel.

Captures user input (topic)
Acts as the entry point of the workflow

Why used:
It enables real-time automation by triggering the workflow whenever a message is posted.

🔹 2. Code Node (Input Processing)

This node extracts relevant data from the Slack payload.

Reads $json.text
Cleans and prepares input

Why used:
Slack sends complex JSON. This step simplifies it into usable input for the next nodes.

🔹 3. IF Node (Validation Logic)

This node checks whether the input is valid.

Filters meaningful topics
Routes flow into TRUE or FALSE branches

Why used:
Prevents invalid or irrelevant inputs from triggering AI and email processes.

🔹 4. AI Model Node

This node generates the newsletter content using an AI model.

Takes topic as input
Produces structured content (title, summary, insights)

Why used:
This is the core intelligence layer that replaces manual content creation.

🔹 5. Code Node (Formatting Logic)

This node formats the AI output into HTML.

Extracts text from AI response
Converts headings, bullets, and structure
Prepares email-ready content

Why used:
AI output is raw text. This step transforms it into a clean, readable newsletter format.

🔹 6. Gmail Node

This node sends the newsletter email.

Uses dynamic subject
Sends formatted HTML body

Why used:
Automates newsletter distribution without manual intervention.

🔹 7. Slack Node (Success Message)

Sends confirmation message back to Slack.

Example:

✅ Newsletter sent successfully!

Why used:
Provides feedback to the user that the workflow completed successfully.

🔹 8. Slack Node (Error Handling - False Branch)

Handles invalid input cases.

Example:

❌ Please enter a valid topic

Why used:
Improves user experience and prevents incorrect executions.

🧪 Test Scenarios
✅ Valid Input
AI in retail analytics

Expected Output:

Newsletter email generated
Slack confirmation message
❌ Invalid Input
hi

Expected Output:

Error message in Slack
📸 Screenshots
1. Slack Input

2. Workflow Execution

3. Email Received

4. Slack Output

🚀 Features
End-to-end automation
Real-time Slack integration
AI-generated structured content
HTML email formatting
Input validation logic
Multi-system orchestration
🧠 Learnings
Webhooks and event-driven architecture
Slack API and event subscriptions
OAuth2 authentication (Gmail)
AI integration into workflows
Data transformation using n8n
📌 Conclusion

This project showcases how AI and automation tools can be combined to build intelligent workflows. It demonstrates a practical use case where manual content creation is replaced with an automated, scalable, and real-time solution.
