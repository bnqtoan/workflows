Telegram → Supabase → AI Recap → Telegram
This n8n workflow uses the following nodes:

- Telegram Trigger: listens for group messages
- Supabase: stores messages into a telegram_chat_logs table
- Schedule Trigger: runs daily at 7PM (UTC)
- LangChain AI (Gemini): summarizes messages into structured HTML
- Code + Split Out + Telegram: splits long text and sends recap via Telegram

Ideal for creating automated daily group chat summaries using Supabase + AI.
Supports HTML output for Telegram’s parse_mode. Includes fallback handling for low activity.