# 🚀 Deploy to Render.com - Complete Guide

## Что нужно для деплоя на Render.com

### 1. **Аккаунт на Render.com**
   - Зарегистрируйтесь на https://render.com
   - Подключите ваш GitHub аккаунт

### 2. **Подготовленные файлы** (уже созданы):
   - ✅ `render.yaml` - конфигурация инфраструктуры
   - ✅ `.renderignore` - исключение лишних файлов
   - ✅ Backend готов к деплою

### 3. **Структура проекта для Render:**

```
Zenbittech/
├── 1/                          # Frontend (React + Vite)
│   ├── render.yaml            ⭐ Главный файл конфигурации
│   ├── .renderignore          ⭐ Исключения
│   ├── package.json
│   └── src/
├── backend/                    # Backend (NestJS + Prisma)
│   ├── package.json
│   ├── prisma/
│   └── src/
└── .git/
```

## 📋 Пошаговая инструкция

### Шаг 1: Загрузите код на GitHub
```bash
cd e:\TestTask\Zenbittech\1
git init
git add .
git commit -m "Initial commit with Render config"
git branch -M main
git remote add origin YOUR_GITHUB_REPO_URL
git push -u origin main
```

### Шаг 2: Создайте Blueprint на Render

1. Зайдите в Dashboard на Render
2. Нажмите **"New +"** → **"Blueprint"**
3. Выберите ваш репозиторий GitHub
4. Render автоматически прочитает `render.yaml`

### Шаг 3: Настройте переменные окружения

Render автоматически создаст:
- ✅ Базу данных PostgreSQL
- ✅ Backend сервис
- ✅ Frontend сервис

**Дополнительно настройте:**

#### Для Backend:
```
NODE_ENV=production
PORT=3000
JWT_SECRET=<сгенерируйте надежный секрет>
JWT_EXPIRES_IN=7d
CORS_ORIGIN=<URL вашего frontend>
DATABASE_URL=<автоматически из Render DB>
```

#### Для Frontend:
```
VITE_API_URL=<URL backend сервиса на Render>
VITE_APP_NAME=InvestProp
```

### Шаг 4: Деплой базы данных

Render автоматически создаст PostgreSQL базу с:
- Название: `investprop`
- Пользователь: `investprop_user`
- Пароль: автоматически сгенерирован

**Важно:** После первого деплоя выполните миграцию:

```bash
# В панели Render перейдите в консоль backend сервиса
npx prisma migrate deploy
npx prisma generate
```

### Шаг 5: Проверка работы

1. **Backend:** Откройте URL backend сервиса и перейдите на `/health`
2. **Frontend:** Откройте URL frontend сервиса
3. **API:** Проверьте эндпоинты через Swagger UI (`/api`)

## 🔧 Конфигурация сервисов

### Backend (NestJS + Prisma)
- **План:** Starter ($7/мес)
- **Регион:** Frankfurt (Германия)
- **Build Command:** `npm install && npm run build`
- **Start Command:** `npm run start:prod`
- **Health Check:** `/health`

### Frontend (React + Vite)
- **План:** Starter ($7/мес)
- **Регион:** Frankfurt (Германия)
- **Build Command:** `npm install && npm run build`
- **Publish Directory:** `dist`

### Database (PostgreSQL)
- **План:** Starter ($7/мес)
- **Регион:** Frankfurt (Германия)
- **Версия:** PostgreSQL 16

## 💰 Стоимость

Минимальная конфигурация:
- Backend: $7/мес
- Frontend: $7/мес (или бесплатно для статических сайтов)
- Database: $7/мес

**Итого: ~$21/мес**

## 🎯 Альтернативный вариант (через Dashboard)

Если не хотите использовать `render.yaml`:

### 1. Создайте Web Service для Backend:
- Root Directory: `backend`
- Build Command: `npm install && npm run build`
- Start Command: `npm run start:prod`
- Добавьте переменные окружения вручную

### 2. Создайте Static Site для Frontend:
- Root Directory: `1`
- Build Command: `npm install && npm run build`
- Publish Directory: `dist`
- Добавьте переменные окружения

### 3. Создайте PostgreSQL базу:
- Выберите тот же регион
- Подключите к backend сервису

## ⚠️ Важные замечания

1. **CORS:** Убедитесь, что backend разрешает запросы с frontend домена
2. **Миграции:** Выполните `prisma migrate deploy` после первого деплоя
3. **Секреты:** Никогда не коммитьте `.env` файлы в git
4. **Логи:** Используйте Render Dashboard для просмотра логов
5. **Auto-Deploy:** При каждом пуше в main ветку деплой автоматический

## 🐛 Решение проблем

### Ошибка подключения к базе
```bash
# Проверьте DATABASE_URL в переменных окружения
# Убедитесь, что база создана в том же регионе
```

### Frontend не видит API
```bash
# Проверьте VITE_API_URL
# Убедитесь, что CORS настроен на backend
```

### Prisma ошибки
```bash
# В консоли backend сервиса:
npx prisma generate
npx prisma migrate deploy
```

## 📞 Поддержка

- Документация Render: https://render.com/docs
- Статус серверов: https://status.render.com
- Сообщество: https://community.render.com

## 🎉 Готово!

После выполнения всех шагов ваше приложение будет доступно по URL:
- Frontend: `https://investprop-frontend.onrender.com`
- Backend: `https://investprop-backend.onrender.com`
- Database: Автоматически подключена к backend

---

**Следующий шаг:** Загрузите проект на GitHub и создайте Blueprint на Render!
