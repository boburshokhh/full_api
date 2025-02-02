# 🚀 Шаблон API на Express.js с аутентификацией и сбросом пароля

![Node.js](https://img.shields.io/badge/Node.js-18.x-green?style=flat-square&logo=node.js)
![Express.js](https://img.shields.io/badge/Express.js-4.x-black?style=flat-square&logo=express)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-14.x-blue?style=flat-square&logo=postgresql)
![JWT](https://img.shields.io/badge/JWT-Authorization-orange?style=flat-square&logo=jsonwebtokens)

Этот проект представляет собой современный backend на **Express.js** с аутентификацией, регистрацией, email-подтверждением и сбросом пароля. Данные хранятся в **PostgreSQL**, а валидация пользователей осуществляется с помощью **JWT**.

## 📌 Функциональность
✅ Регистрация и авторизация пользователей  
✅ Подтверждение email через код  
✅ Защищённый доступ к профилю  
✅ Сброс пароля через email  
✅ Безопасное хранение паролей (**bcrypt**)  
✅ Валидация токенов (**JWT**)  
✅ Централизованная обработка ошибок  
✅ Логирование запросов  

---

## 📦 Установка и запуск

### 1️⃣ Клонирование репозитория
```sh
git clone https://github.com/yourusername/yourproject.git
cd yourproject
```

### 2️⃣ Установка зависимостей
```sh
npm install
```

### 3️⃣ Настройка `.env`
Создайте `.env` файл в корне проекта и добавьте:
```ini
PORT=5000
HOST=localhost
DATABASE_URL=postgres://user:password@localhost:5432/dbname
JWT_SECRET=your-secret-key
EMAIL_USER=your-email@example.com
EMAIL_PASS=your-email-password
RESET_TOKEN_EXPIRATION=15m
```

### 4️⃣ Запуск сервера
```sh
npm run dev
```
📌 API запустится на `http://localhost:5000`

---

## 🔥 API Эндпоинты

### 📌 **Аутентификация**
| Метод  | URL                        | Описание                      |
|--------|---------------------------|-------------------------------|
| `POST` | `/api/auth/register`       | Регистрация нового пользователя |
| `POST` | `/api/auth/login`          | Авторизация (получение токена) |
| `GET`  | `/api/auth/profile`        | Получение профиля (требуется токен) |

### 📌 **Подтверждение email**
| Метод  | URL                        | Описание                        |
|--------|---------------------------|---------------------------------|
| `POST` | `/api/auth/send-code`      | Отправка кода подтверждения     |
| `POST` | `/api/auth/verify-code`    | Подтверждение email по коду     |

### 📌 **Сброс пароля**
| Метод  | URL                        | Описание                          |
|--------|---------------------------|----------------------------------|
| `POST` | `/api/auth/forgot-password` | Запрос на сброс пароля            |
| `GET`  | `/api/auth/reset-password/:token` | Проверка токена сброса         |
| `POST` | `/api/auth/reset-password` | Установка нового пароля          |

---

## 🔑 Авторизация

После успешного входа сервер вернёт **JWT-токен**. Его нужно передавать в `Authorization` заголовке:

```http
GET /api/auth/profile
Authorization: Bearer <your-token>
```

---

## 📡 Примеры запросов

### Регистрация пользователя
```http
POST /api/auth/register
Content-Type: application/json

{
  "name": "Иван Иванов",
  "email": "ivan@example.com",
  "password": "securepassword"
}
```

### Авторизация (вход)
```http
POST /api/auth/login
Content-Type: application/json

{
  "email": "ivan@example.com",
  "password": "securepassword"
}
```
**Ответ:**
```json
{
  "token": "eyJhbGciOiJIUzI1NiIs...",
  "user": { "id": 1, "email": "ivan@example.com" }
}
```

### Запрос на сброс пароля
```http
POST /api/auth/forgot-password
Content-Type: application/json

{
  "email": "ivan@example.com"
}
```
**Ответ:**
```json
{
  "message": "Ссылка для сброса пароля отправлена на email"
}
```

---

## 🏗 Разработка и тестирование

### 🔹 Запуск сервера в режиме разработки
```sh
npm run dev
```

### 🔹 Запуск тестов
```sh
npm test
```

### 🔹 Форматирование кода
```sh
npm run lint
```

---

## 📌 Используемый стек
✅ **Backend:** Express.js, Node.js  
✅ **База данных:** PostgreSQL, Sequelize  
✅ **Безопасность:** JWT, bcrypt  
✅ **Email:** Nodemailer, Resend API  
✅ **Тестирование:** Jest, Supertest  
✅ **Логирование:** Winston  

---

## 📜 Лицензия
Этот проект распространяется под лицензией **MIT**.

---

## ✉️ Контакты
👨‍💻 Автор: **Ваше имя**  
📧 Email: [your.email@example.com](mailto:your.email@example.com)  
📌 GitHub: [yourusername](https://github.com/yourusername)  

