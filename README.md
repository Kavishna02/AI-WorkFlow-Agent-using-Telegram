🧩 Project Name: n8n Telegram Email Assistant
Objective:

To create an automated workflow in n8n that connects Telegram with Email, enabling:

Auto-notification when new Telegram messages arrive.

Auto-email replies or forwarding of Telegram content.

Optional AI-generated email responses (if connected to OpenAI API or similar).

⚙️ Tools & Prerequisites

n8n (Self-hosted or Cloud)

Telegram Bot Token (from @BotFather
)

Email credentials (e.g., Gmail SMTP, Outlook, or custom domain)

Optional: OpenAI API key for smart replies

🔧 Setup Steps
Step 1: Create a Telegram Bot

Open Telegram and search for @BotFather.

Type /newbot → give it a name and username.

Copy the Bot Token provided — you’ll use this in n8n.

Step 2: Create Workflow in n8n
🧱 Trigger Node: Telegram Trigger

Node: Telegram Trigger

Operation: On New Message

Bot Token: (paste your Telegram bot token)

Save → Execute Node → Send a test message to your Telegram bot → Verify message received.

Step 3: Add Email Node

Node: Email Send

Connect it after Telegram Trigger.

Configure:

SMTP Host: (e.g., smtp.gmail.com)

Port: 587

User: your email address

Password/App Password: your app-specific password

From Email: same as user

To Email: your recipient email or dynamic field (e.g., $json["from"]["username"]@example.com)

Subject: New Telegram Message from {{$json["chat"]["username"]}}

Text: {{$json["text"]}}

Step 4: (Optional) Add OpenAI Node for Smart Replies

Node: OpenAI (Chat)

Prompt: “Generate a short professional email reply to this message: {{$json["text"]}}”

Connect output → Email Send Node to send the AI-generated reply automatically.

Step 5: Test and Activate

Save the workflow.

Send a message to your Telegram bot.

You’ll receive an email with that message content or auto-generated reply.

Activate workflow → Toggle to Active to run automatically.

🧠 Example Use Cases

Notify team via email when a client messages on Telegram.

Auto-reply to Telegram leads with a standard email response.

Forward Telegram inquiries to support inbox for tracking.

🛡️ Safety & Maintenance Tips

Never share your bot token or SMTP credentials.

Use environment variables in n8n for keys and passwords.

Limit access to trusted team members.

Regularly test workflow and check logs in case of delivery errors.

