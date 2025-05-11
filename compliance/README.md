# Compliance Checker Module

Модуль проверки соответствия правилам и политикам компании.

## Структура

```
compliance/
├── checkers/          # Проверки
│   ├── content/      # Проверка контента
│   ├── pricing/      # Проверка цен
│   └── legal/       # Юридические проверки
├── rules/            # Правила
│   ├── policies/    # Политики
│   └── schemas/     # JSON схемы
├── validators/       # Валидаторы
│   ├── text/        # Валидация текста
│   └── data/        # Валидация данных
├── reporters/        # Генераторы отчетов
├── utils/           # Утилиты
├── tests/           # Тесты
└── api.py           # API модуля
```

## Возможности

- Проверка соответствия политикам
- Валидация цен и скидок
- Проверка маркетинговых материалов
- Анализ юридических рисков
- Генерация отчетов

## Зависимости

- JSON Schema
- bleach для очистки текста
- PyPDF2 для проверки PDF
- python-docx для проверки Word

## Установка

```bash
pip install -r requirements.txt
```

## Использование

```python
from compliance.checkers import ContentChecker, PricingChecker

# Проверка контента
content_checker = ContentChecker()
content_result = content_checker.check_text("Текст для проверки")

# Проверка цен
pricing_checker = PricingChecker()
pricing_result = pricing_checker.validate_discount(partner_level, discount_amount)
```

## Конфигурация

Параметры в `.env`:
- `RULES_DIR`
- `MAX_DISCOUNT`
- `ALLOWED_DOMAINS`
- `RESTRICTED_WORDS`
- `REPORT_TEMPLATE_DIR` 