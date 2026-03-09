# n8n-first-automation: Telegram AI Agent & Workflows

**Production-ready** n8n workflows для Telegram AI-агента, автопостинга, обработки файлов и интеграций с LLM/CRM.

## Что делает проект

- Telegram-бот на базе n8n, который отвечает как AI-ассистент, обрабатывает файлы и запускает автоматизации.
- Автопостинг контента в Telegram-каналы и чаты по расписанию или по триггерам.
- Интеграции с LLM (OpenAI/Ollama) и CRM (через webhooks/API) для ведения диалогов и записи лидов.
- Оркестрация контент-пайплайна: генерация, модерация, публикация и логирование.

## Для кого

- L&D-специалисты и консалтеры, которые хотят быстро собрать **Telegram-агента** для обучения и онбординга.
- Маркетинг и контент-команды, которым нужен управляемый контент-пайплайн в n8n.
- Разработчики и no-code/low-code энтузиасты, которые хотят боевой пример n8n-стека с Docker/Postgres.

## Какие сценарии закрывает в n8n

- Telegram AI-ассистент: ответы на вопросы, работа с файлами, контекстные подсказки.
- Контент-автопостинг: посты по расписанию, репосты, цепочки сообщений.
- Интеграция с LLM: генерация ответов, резюме, постов, сценариев.
- Интеграция с CRM: создание/обновление контактов и лидов, логирование диалогов.
- Уведомления и алерты в Telegram для событий в других системах.

## Стек

- n8n (self-hosted, Docker).
- Docker + docker-compose.
- Postgres как основная БД n8n.
- Telegram Bot API (бот как основной фронтенд).
- OpenAI API и/или локальный Ollama.
- (Опционально) любая CRM с REST API или Webhooks.

## Quick Start за 5 минут

1. Клонируйте репозиторий  
   ```bash
   git clone https://github.com/bortichmila/n8n.git
   cd n8n
   ```
2. Создайте `.env` на основе примера  
   ```bash
   cp .env.example .env
   ```
   Заполните минимум: `N8N_HOST`, `N8N_PORT`, `N8N_ENCRYPTION_KEY`, `POSTGRES_*`, `TELEGRAM_BOT_TOKEN`, `OPENAI_API_KEY` или параметры Ollama.

3. Запустите Docker-контейнеры  
   ```bash
   docker-compose up -d
   ```
4. Откройте n8n в браузере  
   - URL по умолчанию: `http://localhost:5678`.

5. Импортируйте Telegram-агента  
   - Войдите в n8n UI → Import → загрузите `workflows/telegram-agent.json`.
   - Обновите значения переменных/credentials под свой бот и ключи.

6. Напишите боту в Telegram  
   - Найдите своего бота по @username, отправьте `/start` и протестируйте базовые команды.

## Структура workflow

- `workflows/telegram-agent.json` — основной AI-агент для Telegram (команды, обработка текста, файлов, вызовы LLM, логирование).
- (позже) `workflows/content-pipeline.json` — автопостинг и пайплайн контента.
- (позже) `workflows/crm-integration.json` — интеграция с CRM/таблицами.

Подробнее по структуре см. `docs/architecture.md`.

## Переменные окружения

Ключевые переменные (полный список см. `.env.example`):

- `N8N_HOST`, `N8N_PORT` — адрес и порт n8n.
- `N8N_ENCRYPTION_KEY` — ключ шифрования (обязательно задайте).
- `POSTGRES_USER`, `POSTGRES_PASSWORD`, `POSTGRES_DB`, `POSTGRES_HOST`, `POSTGRES_PORT`.
- `TELEGRAM_BOT_TOKEN` — токен вашего Telegram-бота.
- `OPENAI_API_KEY` — ключ OpenAI (если используете).
- `OLLAMA_BASE_URL` и модель — если используете локальный Ollama.

## Скриншоты и схема

- Скриншот UI workflow Telegram-агента (будет позже).
- Схема архитектуры (n8n ↔ Telegram ↔ LLM ↔ CRM) в `docs/architecture.md`.

## Roadmap

- [ ] Добавить workflow контент-пайплайна с автопостингом.
- [ ] Добавить примеры интеграций с популярными CRM.
- [ ] Добавить готовые промпты и пресеты для L&D-сценариев.
- [ ] Подготовить набор примерных use cases в `examples/use-cases.md`.
- [ ] Записать короткое видео-демо запуска и настройки.

## Как импортировать workflows

1. Зайдите в n8n UI.
2. Нажмите на кнопку **Import** в верхнем меню.
3. Выберите вкладку **File** и загрузите нужный `.json` из папки `workflows/`.
4. Проверьте/обновите credentials (Telegram, OpenAI/Ollama, CRM и т.д.).
5. Включите workflow (toggle Active) и протестируйте.

---

Лицензия: см. `LICENSE`.
