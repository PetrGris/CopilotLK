# Pricing & Quoting Module

Модуль расчета цен и генерации коммерческих предложений.

## Структура

```
pricing/
├── calculators/        # Калькуляторы цен
│   ├── partner/       # Партнерские цены
│   └── msp/          # MSP цены
├── generators/        # Генераторы документов
│   ├── pdf/          # PDF генератор
│   └── excel/        # Excel генератор
├── templates/         # Шаблоны документов
│   ├── proposals/    # Шаблоны КП
│   └── quotes/       # Шаблоны квот
├── rules/            # Правила расчета цен
│   ├── discounts/    # Правила скидок
│   └── promotions/   # Акции
├── utils/            # Утилиты
├── tests/            # Тесты
└── api.py            # API модуля
```

## Возможности

- Расчет цен по разным моделям
- Применение скидок и акций
- Генерация PDF предложений
- Экспорт в Excel
- Валидация правил

## Зависимости

- WeasyPrint для PDF
- ReportLab для сложных PDF
- openpyxl для Excel
- Jinja2 для шаблонов

## Установка

```bash
pip install -r requirements.txt
```

## Использование

```python
from pricing.calculators import PartnerPriceCalculator
from pricing.generators import PDFGenerator

# Расчет цены
calculator = PartnerPriceCalculator()
price = calculator.calculate(product_id, quantity, partner_level)

# Генерация КП
generator = PDFGenerator()
pdf = generator.generate_proposal(price_data, template="standard")
```

## Конфигурация

Параметры в `.env`:
- `BASE_CURRENCY`
- `EXCHANGE_RATES_API`
- `DEFAULT_MARGIN`
- `PDF_TEMPLATE_DIR`
- `EXCEL_TEMPLATE_DIR` 