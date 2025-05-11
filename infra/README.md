# Infrastructure Module

Модуль инфраструктуры и развертывания.

## Структура

```
infra/
├── docker/           # Docker конфигурации
│   ├── api/         # API сервис
│   ├── web/         # Web UI
│   └── ml/          # ML сервисы
├── k8s/             # Kubernetes манифесты
│   ├── base/        # Базовые ресурсы
│   └── overlays/    # Окружения
├── terraform/       # IaC
│   ├── modules/     # Terraform модули
│   └── environments/# Окружения
├── monitoring/      # Мониторинг
│   ├── grafana/     # Дашборды
│   └── prometheus/  # Конфигурация
├── scripts/         # Скрипты
├── configs/         # Конфигурации
└── docs/           # Документация
```

## Возможности

- Docker контейнеризация
- Kubernetes оркестрация
- Terraform IaC
- Мониторинг и логирование
- CI/CD пайплайны

## Зависимости

- Docker
- Kubernetes
- Terraform
- Prometheus
- Grafana

## Установка

```bash
# Локальное окружение
docker-compose up -d

# Kubernetes
kubectl apply -k k8s/overlays/dev

# Terraform
cd terraform/environments/dev
terraform init
terraform apply
```

## Мониторинг

- Grafana: http://monitoring.local
- Prometheus: http://prometheus.local
- Kibana: http://kibana.local

## Конфигурация

Параметры в `.env`:
- `ENVIRONMENT`
- `DOCKER_REGISTRY`
- `K8S_NAMESPACE`
- `TERRAFORM_WORKSPACE`
- `MONITORING_DOMAIN` 