# 📚 Self-Hosted IT Knowledge Base (GitOps Approach)

[![Docker](https://shields.io)](https://docker.com)
[![Nginx](https://shields.io)](https://nginxproxymanager.com)
[![PostgreSQL](https://shields.io)](https://postgresql.org)
[![Wiki.js](https://shields.io)](https://js.wiki)

Персональная база знаний и ИТ-справочник, развернутый на собственном сервере с использованием практик **IaC** (Infrastructure as Code) и **GitOps**.

---

## 🏗 Архитектура системы

Проект реализован на базе микросервисной архитектуры в Docker-контейнерах:

*   **Wiki.js** — мощный движок базы знаний на Node.js с поддержкой Markdown.
*   **PostgreSQL 15** — реляционная база данных для хранения метаданных и настроек.
*   **Nginx Proxy Manager** — Reverse Proxy, обеспечивающий безопасный доступ по HTTPS (Let's Encrypt).
*   **DB Backup Service** — автоматизированный сервис для создания дампов базы данных.

---

## 🛠 Технологический стек

*   **Infrastructure:** Docker, Docker Compose (IaC).
*   **OS:** Linux (SelectOS / Ubuntu) на базе Mini-PC.
*   **Networking:** MikroTik (маршрутизация, Port Forwarding, Static DNS).
*   **CI/CD & GitOps:** 
    *   Конфигурация сервера версионируется в данном репозитории.
    *   Двусторонняя синхронизация контента с приватным репозиторием GitHub в формате Markdown.
*   **Data Safety:** 
    *   Ежедневные бэкапы БД в локальное хранилище.
    *   Синхронизация архивов с **Yandex Disk** через `rclone`.

---

## 📦 Развертывание

1. **Клонирование проекта:**
   ```bash
   git clone https://github.com/Sergy-Taph/infra-server.git
   cd infra-server```
2. **Настройка окружения**
   ```bash
   cp .env.example .env
   nano .env```
3. **Запуск**
   ```bash
   docker compose up -d```

