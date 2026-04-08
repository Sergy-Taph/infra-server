# 📚 Self-Hosted IT Hub (Wiki + Cloud + GitOps)

<p align="">
  <img src="https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white" />
  <img src="https://img.shields.io/badge/Nginx-009639?style=for-the-badge&logo=nginx&logoColor=white" />
  <img src="https://img.shields.io/badge/Wiki.js-1976D2?style=for-the-badge&logo=wikijs&logoColor=white" />
  <img src="https://img.shields.io/badge/Nextcloud-0082C9?style=for-the-badge&logo=nextcloud&logoColor=white" />
  <img src="https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white" />
  <img src="https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white" />
</p>

Персональная экосистема сервисов, развернутая на собственном сервере с использованием практик **IaC** (Infrastructure as Code) и автоматизированным управлением трафиком.

---

## 🐳 Архитектура системы

Проект реализован на базе микросервисной архитектуры в Docker-контейнерах:

*   **Wiki.js** — основная база знаний с поддержкой Markdown и Git-синхронизацией.
*   **Nextcloud** — приватное облачное хранилище для файлов и медиа.
*   **PostgreSQL 15** — единая СУБД для всех сервисов с кастомной инициализацией баз.
*   **Nginx Proxy Manager** — центральный узел маршрутизации и управления SSL (Let's Encrypt).
*   **Postgres-Backup** — сервис автоматического создания дампов БД по расписанию.

---

## 🔧 Технологический стек

*   **Infrastructure:** Docker, Docker Compose (IaC).
*   **OS:** Linux (SelectOS / Ubuntu) на базе Mini-PC.
*   **Networking:** MikroTik (маршрутизация, Port Forwarding, Static DNS).
*   **CI/CD & GitOps:** 
    *   Конфигурация сервера версионируется в данном репозитории.
    *   Двусторонняя синхронизация контента с приватным репозиторием GitHub в формате Markdown.
*   **Data Safety:** 
    *   Ежедневный бэкап всех БД (Wiki + Nextcloud) в локальное хранилище.
    *   Автоматическая синхронизация архивов с **Yandex Disk** через `rclone` и `cron`.

---

## 📦 Развертывание

1. **Клонирование проекта:**
    ```bash
    git clone https://github.com/Sergy-Taph/infra-server.git
    cd infra-server

2. **Настройка окружения:**
    ```bash
    cp .env.example .env
    nano .env
    
    #Укажите свои пароли и токен Яндекс.Диска
    
3. **Запуск**
    ```bash
    docker compose up -d

    #Скрипт в папке init-db автоматически создаст необходимые базы и права при первом запуске

---

## 🌍 Доступ к сервисам
*   **Knowledge Base:** [https://wiki.stafintsev.ru](https://wiki.stafintsev.ru)
*   **Cloud Storage:** [https://cloud.stafintsev.ru](https://cloud.stafintsev.ru)

---

## 🔐 Безопасность
- **SSL Termination:** Весь внешний трафик шифруется через Let's Encrypt.
- **Network Isolation:** Сервисы БД не имеют публичных портов и доступны только внутри Docker-сети.
- **3-2-1 Backup:** Данные хранятся локально, в Git и в облачном хранилище.
