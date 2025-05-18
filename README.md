# 🧩 Configurations: Автоматизированное формирование DevOps-конфигураций

Веб-приложение для создания и управления конфигурационными файлами (YAML, JSON и др.) через визуальный интерфейс и шаблонную систему. Проект ориентирован на DevOps-инженеров, разработчиков и команды, которым важно ускорить процесс развёртывания инфраструктуры.

## 📂 Репозитории компонентов

- **Backend (FastAPI + PostgreSQL):** [Configurations-backend](https://github.com/Fristivan/Configurations-backend)  
- **Frontend (React + Vite):** [Configurations-frontend](https://github.com/Fristivan/Configurations-frontend)

## ⚙️ Возможности

- Регистрация и вход с верификацией по e-mail (одноразовые коды)
- Авторизация через JWT (в HTTP-only cookie)
- Создание и редактирование конфигураций
- Поддержка шаблонов конфигураций (Docker, CI/CD и др.)
- Генерация финального файла с параметрами
- Интеграция с платёжной системой **ЮKassa**
- Сброс пароля по e-mail
- Полная контейнеризация через Docker Compose
- Защита и маршрутизация через **Cloudflare Tunnel**

---

## 🚀 Быстрый запуск (Docker Compose)

В корне проекта уже находится файл `docker-compose.yml`, который описывает запуск всех компонентов. Вам нужно только подготовить переменные окружения.

### 1. Клонирование

```bash
git clone https://github.com/Fristivan/Configurations-backend
git clone https://github.com/Fristivan/Configurations-frontend
cd Configurations/
````

Убедитесь, что структура папок соответствует:

```
Configurations/
├── docker-compose.yml
├── .env
├── Configurations-backend/
└── Configurations-frontend/
```

### 2. Подготовка переменных окружения

Создайте файл `.env` в корне проекта и укажите:

```dotenv
POSTGRES_DB=configgen
POSTGRES_USER=postgres
POSTGRES_PASSWORD=postgres

JWT_SECRET=supersecretkey
JWT_ALGORITHM=HS256
ACCESS_TOKEN_EXPIRE_MINUTES=30
REFRESH_TOKEN_EXPIRE_DAYS=7

SMTP_SERVER=smtp.mail.ru
SMTP_PORT=587
SMTP_USER=your@mail.ru
SMTP_PASSWORD=yourpassword

YOKASSA_SHOP_ID=your_shop_id
YOKASSA_SECRET_KEY=your_secret_key

CLOUDFLARED_TOKEN=your_cloudflare_token
```

### 3. Запуск

```bash
docker-compose up --build
```

Доступ к сервису:

* **Frontend:** [http://localhost:3000](http://localhost:3000)
* **Backend API:** [http://localhost:8000/docs](http://localhost:8000/docs)
* **PostgreSQL:** порт 5432

---

## 📚 Стек технологий

* **Backend:** Python, FastAPI, Alembic, PostgreSQL, Jinja2/Mako
* **Frontend:** React.js, Vite, Tailwind CSS
* **DevOps:** Docker, Docker Compose, Cloudflared Tunnel
* **Безопасность:** JWT, HTTPS (через Cloudflare), bcrypt, SMTP

---

## 🛠 Структура проекта

```
Configurations/
├── docker-compose.yml
├── .env
├── Configurations-backend/
│   └── app/
│       ├── models/
│       ├── routes/
│       └── templates/
└── Configurations-frontend/
    └── src/
```

---

## 🧪 Тестирование

* **Backend:** `pytest`, Swagger UI доступен на `/docs`
* **Frontend:** запуск с `npm run dev` внутри контейнера или локально

---

> Проект создан в образовательных целях и может быть доработан для коммерческого использования или расширения под другие DevOps-сценарии.
