# k8s-self-managed-platform

## Цель проекта: 
Развернуть Kubernetes-платформу, включающую:
- self-managed Kubernetes cluster;
- отказоустойчивую систему управления;
- мониторинг кластера и приложений;
- централизованное логирование;
- CI/CD pipeline для приложения;
- GitOps-подход к развертыванию компонентов платформы.

## MVP

В MVP входят:
- 3 control-plane узла с etcd
- 2 worker узла
- ingress-nginx
- ArgoCD
- Prometheus, Grafana, Alertmanager
- Loki + Vector
- тестовое приложение Online Boutique
- GitLab CI
Для логирования выбран Vector, так как он может собирать и обрабатывать логи кластера и приложений перед отправкой в Loki.

## План работ

1. Подготовка репозитория и структуры проекта.
2. Подготовка инфраструктуры Kubernetes.
3. Развертывание Kubernetes-кластера.
4. Установка GitOps-инструмента ArgoCD.
5. Установка мониторинга Prometheus/Grafana.
6. Установка централизованного логирования.
7. Настройка storage subsystem.
8. Подготовка demo-приложения.
9. Настройка CI/CD pipeline.

## Документация
- [Дневник проекта](docs/project-diary.md)
- [Архитектура платформы](docs/architecture.md)
- [Inventory](infrastructure/inventory.md)
