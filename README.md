# Sales Copilot

Интеллектуальный помощник для менеджеров по продажам и партнёрским менеджерам лаборатории Касперского.

## Структура проекта

```
CopilotLK/
├── bot_ui/          # Интерфейсы (Outlook/Exchange, Telegram, Web)
├── mcp_api/         # FastAPI сервер
├── context/         # Context Analyzer
├── pricing/         # Pricing & Quoting Module
├── compliance/      # Compliance Checker
├── content/         # Content Inserter
├── infra/          # Инфраструктура
└── docs/           # Документация
```

## Правила разработки

1. Все компоненты проекта должны находиться внутри папки CopilotLK
2. Каждый модуль должен иметь свой README.md с описанием
3. Все зависимости должны быть зафиксированы в requirements.txt или package.json
4. Код должен соответствовать PEP 8 для Python и Airbnb style guide для JavaScript
5. Все конфиденциальные данные должны храниться в .env файлах
6. Каждый модуль должен иметь тесты
7. Документация API должна быть в формате OpenAPI/Swagger

## Технологический стек

- **UI**: React/Next.js, aiogram, Outlook API
- **API**: FastAPI, Pydantic, Redis
- **Анализ**: spaCy, PyTorch, Celery
- **RAG Engine**: LangChain, FAISS, Elasticsearch
- **Compliance**: JSON Schema, bleach
- **PDF**: WeasyPrint, ReportLab
- **LLM**: OpenAI, GigaChat, YSGPT
- **Storage**: PostgreSQL, MinIO/S3

## Установка и запуск

```bash
# Клонирование репозитория
git clone <repository_url>
cd CopilotLK

# Установка зависимостей Python
python -m venv venv
source venv/bin/activate  # или venv\Scripts\activate на Windows
pip install -r requirements.txt

# Установка зависимостей Node.js
cd bot_ui/web
npm install

# Запуск API сервера
cd ../../mcp_api
uvicorn main:app --reload

# Запуск веб-интерфейса
cd ../bot_ui/web
npm run dev
```

## Разработка

1. Создайте ветку для новой функциональности:
   ```bash
   git checkout -b feature/название-функциональности
   ```

2. Внесите изменения и добавьте тесты

3. Убедитесь, что все тесты проходят:
   ```bash
   pytest
   ```

4. Создайте pull request

## Документация

Подробная документация доступна в папке `docs/` 