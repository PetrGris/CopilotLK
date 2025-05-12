# Sales Copilot — Техническое задание

## 1. Общий обзор
Sales Copilot — это интеллектуальный помощник для менеджеров по продажам и партнёрским менеджерам лаборатории Касперского.

Система анализирует историю переписки, генерирует черновики писем под разные цели (продажа, апсейл, продление, партнёрские предложения), автоматически подставляет описания продуктов, маркетинговые материалы, актуальные цены и проверяет соответствие написанному лучшим практикам и базе знаний компании. Так же помошник добавляя информацию о более ценных проуктах и услугах будет реализовывать стратегицескую цель по повышению выручки с клиента. 


## 2. Конкретные кейсы использования

### 2.1 Взаимодействие с конечными клиентами
- **Запрос информации**: клиент спрашивает о функциях Kaspersky Endpoint Security. Copilot анализирует переписку, предлагает сжатый обзор возможностей продукта и вставляет описание и сравнение. Результат: клиент сразу получает необходимую информацию. 
- **Предложение апсейла**: определив устаревшую версию, Copilot генерирует письмо с предложением перехода на Premium Plus или Premium и описывает преимущества для клиента. Клиент проанализировав плюсы и минусы выбирает покупку более дорогой поддержки. 
- **Проверка соответствия**: Менеджер в ответе пишет технические характеристики, которые не соответствуют реальности. Copilot предупреждает об этом, менеджер изменяет формулировки. В результате клиент не имеет неправильных ожиданий от продукта, повышение лояльности.
- **Маркетинговые материалы**: Проанализировав переписку Copilot выявляет потребности партнера в информации и рекомендует вставить его в качестве опционального предложения. Добавляет подготовленные департаментом маркетинга материалы. Партнер узнает о новых продуктах и услугах, увеличивает свои продажи и лояльность ЛК.
- **Конфликтная ситуация**: Клиент обращается с претензией на неработающее решение Copilot анализирует переписку, выявляет боли клиента, адресно, с учетом психологических практик предлагает драфт письма, который ведет к мнимизации конфликта.  


## 3. Функциональные модули

### 3.1 Интерфейсы
- Outlook/Exchange, Telegram, Web-чат (React/Next.js)
- Аутентификация: OAuth 2.0 для корпоративных аккаунтов, JWT для внутренних запросов

### 3.2 Context Analyzer
- Импорт истории переписки
- NER и intent recognition (spaCy/PyTorch)
- Выявление болей клиента, определение настроения и точек конфликта
- Генерация тезисов и поиск расхождений с документацией

### 3.3 Email Assistant
- Генерация черновиков с разными стилями (официальный, дружественный)
- Автоматическое дополнение технических и маркетинговых блоков

### 3.4 Pricing & Quoting Module
- Расчёт прайсовых цен с учётом уровней программы и объёмов по текстовому описанию продукта
- Подсказка менеджеру по предидущим заказам с данным клиентом. 

### 3.5 Compliance Checker
- Сравнение писем с базой знаний и документацией
- Выявление недостоверных или рискованных утверждений
- Выявление негативной лекисики

### 3.6 Content Inserter
- RAG-поиск (семантический + полнотекстовый)
- Автоматическая вставка ссылок на маркетинговые и продуктовые материалы

## 4. Архитектура системы

```
[Менеджер / Партнёр]
      ↓ HTTPS/OAuth2
[Bot UI: Outlook/Telegram/Web]
      ↓ MCP API (FastAPI)
┌──────────────┬─────────────────────┐
│   Context Analyzer          │
│   (spaCy, PyTorch)          │
└───┬─────────────────────┬───┘
    ↓                     ↓
[Pricing & Quoting]    [RAG Engine]
   (MSP/Affiliate)   (Elasticsearch + FAISS)
    ↓                     ↓
[Compliance Checker]  [Content Inserter]
    ↓                     ↓
      └────▶ GPT Module ◀───┘
```

## 5. Технологии и компоненты

| Модуль              | Технологии и библиотеки                        |
|---------------------|------------------------------------------------|
| UI                  | React/Next.js, aiogram, Outlook API            |
| MCP API             | FastAPI, Pydantic, Redis                       |
| Context Analyzer    | spaCy, PyTorch, Celery                         |
| RAG Engine          | LangChain, FAISS, Elasticsearch                |
| Compliance Checker  | JSON Schema, bleach                            |
| PDF Generator       | WeasyPrint, ReportLab                          |
| GPT-интеграция      | OpenAI, GigaChat, YaGPT (по выбору)            |
| Хранилище данных    | PostgreSQL, MinIO/S3                           |

## 7. Prompt для Coursor AI

```yaml
system: |
  You are Sales Copilot Architect. Create a Coursor AI board for a Kaspersky Sales Copilot:
    - Modules: Bot UI, MCP API, Context Analyzer, Pricing & Quoting,
      Compliance Checker, Content Inserter, LLM Module.
    - Channels: Outlook/Exchange, Telegram, Web.
    - Goals: Draft emails, analyze threads, insert pricing,
      marketing materials, check compliance.
tasks:
  - repo_init:
      description: |
        Setup monorepo dirs: /bot_ui, /mcp_api, /context, /pricing,
        /compliance, /content, /infra, /docs.
  - data_prep:
      description: |
        Import email threads via Exchange API.
        Build NER and topic modeling pipelines.
  - rag_engine:
      description: |
        Scaffold LangChain pipelines and configure ES + FAISS.
  - mcp_server:
      description: |
        Implement GET /tools/list, POST /tools/execute.
        Add OAuth2/JWT auth and rate limiting.
  - bot_integration:
      description: |
        Extend Telegram/Web/Outlook clients with “draft_email”, “analyze_thread”.
  - pricing_module:
      description: |
        Implement Partner/MSP pricing logic and PDF proposal generation.
  - compliance_checker:
      description: |
        Compare drafts to KB and flag risky statements.
  - content_inserter:
      description: |
        Extend RAG-chain for docs & marketing assets;
        generate descriptions and insert links.
  - llm_integration:
      description: |
        Configure Chat Completions client;
        define system prompts: DraftAssistant, ThreadAnalyzer, ContentInserter.
board:
  columns: [Backlog, In Progress, Review, Done]
  epics: [Bot UI, MCP API, Context Analyzer, Pricing & Quoting,
          Compliance Checker, Content Inserter, LLM Module,
          Testing, Infra]
milestones:
  - name: Prototype
    duration: 4 weeks
  - name: MVP
    duration: 8 weeks
  - name: Production
    duration: 12 weeks
```
