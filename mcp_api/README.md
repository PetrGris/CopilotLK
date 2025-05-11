# MCP API Module

FastAPI сервер для Sales Copilot.

## Структура

```
mcp_api/
├── api/              # API endpoints
│   ├── v1/          # API версии 1
│   └── deps.py      # Зависимости
├── core/            # Ядро приложения
│   ├── config.py    # Конфигурация
│   └── security.py  # Безопасность
├── db/              # Работа с базой данных
│   ├── models/      # SQLAlchemy модели
│   └── session.py   # Сессии БД
├── schemas/         # Pydantic модели
├── services/        # Бизнес-логика
├── tests/           # Тесты
└── main.py         # Точка входа
```

## Зависимости

- FastAPI
- Pydantic
- SQLAlchemy
- Redis
- Python-Jose
- Uvicorn

## Установка

```bash
pip install -r requirements.txt
```

## Запуск

Для разработки:
```bash
uvicorn main:app --reload
```

Для продакшена:
```bash
uvicorn main:app --host 0.0.0.0 --port 8000
```

## API Документация

После запуска сервера доступны:
- Swagger UI: http://localhost:8000/docs
- ReDoc: http://localhost:8000/redoc

## Конфигурация

Параметры в `.env`:
- `DATABASE_URL`
- `REDIS_URL`
- `SECRET_KEY`
- `ALGORITHM="HS256"`
- `ACCESS_TOKEN_EXPIRE_MINUTES=30` 