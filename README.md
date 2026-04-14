# Практична робота №2: Контейнеризація додатку (Частина 1)

**Дисципліна:** Професійна практика програмної інженерії  
**Студентка:** Алієва Анастасія 
**Варіант:** 1 (REST API для нотаток)

## Мета роботи
Навчитися контейнеризувати реальні додатки, писати оптимізовані Dockerfile, налаштовувати docker-compose для мультисервісного середовища та використовувати AI для генерації конфігурацій.

## Технічні характеристики проекту
У проекті реалізовано наступні вимоги:
* **Multi-stage Dockerfile:** Використано 2 стадії (build + production) для мінімізації розміру образу.
* **Non-root user:** Контейнер запускається від імені безпечного користувача `nodeuser`.
* **Healthcheck:** Налаштовано автоматичну перевірку стану для основного сервісу та бази даних.
* **Docker Compose:** Описано 2 сервіси (Node.js API та PostgreSQL 16).
* **Розмір образу:** Завдяки використанню Alpine-образу та multi-stage build, розмір production-образу становить < 200MB.
* **Мережа:** Сервіси взаємодіють через спільну мережу `bridge`.

## Як запустити проект

1.  **Склонуйте репозиторій:**
    ```bash
    git clone [https://github.com/anastasiia-123/professional-practice-lab2.git](https://github.com/anastasiia-123/professional-practice-lab2.git)
    cd professional-practice-lab2
    ```

2.  **Запустіть контейнери:**
    ```bash
    docker compose up --build
    ```

3.  **Перевірте статус:**
    Після запуску API буде доступне за адресою: [http://localhost:3000](http://localhost:3000)

## Кінцеві точки API (Endpoints)
* `GET /health` — Перевірка стану сервісу (Healthcheck). Повертає `{"status": "ok"}`.
* `GET /notes` — Отримати список усіх нотаток.
* `POST /notes` — Створити нову нотатку.

## Використані технології
* **Backend:** Node.js, Express
* **Database:** PostgreSQL 16 (Alpine)
* **Infrastructure:** Docker, Docker Compose
