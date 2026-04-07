# Self-Hosted IT Knowledge Base (GitOps Approach)

Персональный ИТ-справочник и база знаний, развернутая на собственном сервере с использованием современных DevOps-практик.

## 🚀 Архитектура проекта

Проект построен на базе микросервисной архитектуры в Docker-контейнерах:
*   **Wiki.js**: Движок базы знаний (Node.js).
*   **PostgreSQL**: Реляционная база данных для хранения метаданных и настроек.
*   **Nginx Proxy Manager**: Reverse Proxy для управления SSL-сертификатами (Let's Encrypt) и маршрутизации трафика.

## 🛠 Технологический стек
*   **Infrastructure**: Docker, Docker Compose
*   **Network**: Nginx, SSL (Certbot/Let's Encrypt), Port Forwarding
*   **CI/CD & GitOps**: 
    *   Конфигурация сервера хранится в этом репозитории (IaC).
    *   Контент статей автоматически синхронизируется с приватным GitHub-репозиторием в формате Markdown.
*   **OS**: Linux (SelectOS) на базе Mini-PC.

## 📦 Схема развертывания

1. Клонирование репозитория:

   git clone https://github.com/Sergy-Taph/infra-server.git
   cd infra-server

2. Настройка переменных окружения:

   Создайте файл .env на основе примера:

   cp .env.example .env

   Отредактируйте пароли в .env

3. Запуск инфраструктуры:

   docker compose up -d
