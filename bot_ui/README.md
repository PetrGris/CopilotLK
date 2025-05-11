# Bot UI Module

Модуль пользовательских интерфейсов для Sales Copilot.

## Компоненты

### Web Interface (Next.js)
- `/web` - веб-интерфейс на React/Next.js
  - `/src` - исходный код
  - `/public` - статические файлы
  - `/components` - React компоненты
  - `/styles` - CSS стили

### Telegram Bot
- `/telegram` - Telegram бот на aiogram
  - `/handlers` - обработчики команд
  - `/utils` - вспомогательные функции

### Outlook Integration
- `/outlook` - интеграция с Outlook/Exchange
  - `/handlers` - обработчики событий
  - `/utils` - вспомогательные функции

### Tests
- `/tests` - тесты для всех компонентов

## Установка и запуск

### Web Interface
```bash
cd web
npm install
npm run dev
```

### Telegram Bot
```bash
cd telegram
python bot.py
```

### Outlook Integration
```bash
cd outlook
python outlook_handler.py
```

## Конфигурация
Все конфигурационные параметры должны быть определены в `.env` файле:
- `TELEGRAM_BOT_TOKEN`
- `OUTLOOK_CLIENT_ID`
- `OUTLOOK_CLIENT_SECRET`
- `OUTLOOK_TENANT_ID`
- `WEB_API_URL` 