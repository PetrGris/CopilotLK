# Context Analyzer Module

Модуль анализа контекста для Sales Copilot.

## Структура

```
context/
├── analyzers/           # Анализаторы
│   ├── intent/         # Определение намерений
│   ├── sentiment/      # Анализ тональности
│   └── ner/           # Распознавание сущностей
├── models/             # ML модели
│   ├── classifiers/   # Классификаторы
│   └── embeddings/    # Векторные представления
├── processors/         # Обработчики текста
│   ├── cleaners/      # Очистка текста
│   └── tokenizers/    # Токенизация
├── utils/             # Утилиты
├── tests/             # Тесты
└── pipeline.py        # Основной пайплайн
```

## Возможности

- Анализ намерений пользователя
- Определение тональности
- Извлечение именованных сущностей
- Классификация тем
- Выявление ключевых моментов

## Модели

- spaCy для NER и базового NLP
- PyTorch для классификации
- Transformers для анализа тональности
- Собственные модели для специфических задач

## Установка

```bash
pip install -r requirements.txt
python -m spacy download ru_core_news_lg
```

## Использование

```python
from context.pipeline import ContextAnalyzer

analyzer = ContextAnalyzer()
result = analyzer.analyze_text("Ваш текст здесь")
```

## Конфигурация

Параметры в `.env`:
- `SPACY_MODEL`
- `TORCH_DEVICE`
- `BATCH_SIZE`
- `MAX_LENGTH`
- `CLASSIFICATION_THRESHOLD` 