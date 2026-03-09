# Architecture

- Пользователь ↔ Telegram Bot API ↔ n8n (workflow Telegram AI Agent).
- n8n ↔ LLM (OpenAI/Ollama) для генерации ответов.
- n8n ↔ Postgres для хранения данных/истории.
- n8n ↔ CRM/другие сервисы через HTTP Request и webhooks.

Высокоуровневая схема:
- Вход: сообщения/файлы в Telegram.
- Обработка: парсинг, маршрутизация, вызовы LLM, бизнес-логика.
- Выход: ответы в Telegram, записи в CRM, уведомления.
