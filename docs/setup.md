# Setup

## Предварительные требования

- Docker и docker-compose установлены локально или на сервере.
- Зарегистрированный Telegram-бот через @BotFather (получен токен).
- Ключ OpenAI **или** установленный Ollama (если хотите локальную LLM).

## Шаги

1. Клон репозитория и создание `.env`:
   ```bash
   git clone https://github.com/bortichmila/n8n.git
   cd n8n
   cp .env.example .env
   ```
2. Заполните `.env` своими значениями (бот, ключи, хосты).
3. Запустите:
   ```bash
   docker-compose up -d
   ```
4. Откройте n8n в браузере, импортируйте `workflows/telegram-agent.json` и настройте credentials.
5. Напишите своему Telegram-боту и протестируйте сценарии.
