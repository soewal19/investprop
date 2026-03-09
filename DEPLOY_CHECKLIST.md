# ✅ ЧЕКЛИСТ: Деплой на Render.com

## 📦 Что уже готово:
- [x] Файл `render.yaml` - конфигурация инфраструктуры
- [x] Файл `.renderignore` - исключение лишних файлов  
- [x] Backend настроен для работы с PostgreSQL через Prisma
- [x] Frontend настроен для работы с backend API
- [x] Удалены все зависимости Supabase

## 🎯 Что нужно сделать:

### 1. GitHub (5 минут)
```bash
cd e:\TestTask\Zenbittech\1
git init
git add .
git commit -m "Prepare for Render deployment"
git branch -M main
# Создайте репозиторий на GitHub и выполните:
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO.git
git push -u origin main
```

### 2. Render.com (10 минут)
- [ ] Зарегистрироваться на https://render.com
- [ ] Подключить GitHub аккаунт
- [ ] Нажать "New +" → "Blueprint"
- [ ] Выбрать ваш репозиторий
- [ ] Render прочитает `render.yaml` и предложит создать сервисы

### 3. Настройка переменных окружения (5 минут)

**Backend (в панели Render):**
```
NODE_ENV=production
PORT=3000
JWT_SECRET=<придумайте надежный секрет>
JWT_EXPIRES_IN=7d
CORS_ORIGIN=<URL frontend, например: https://investprop-frontend.onrender.com>
```

**Frontend (в панели Render):**
```
VITE_API_URL=<URL backend, например: https://investprop-backend.onrender.com>
VITE_APP_NAME=InvestProp
```

### 4. Инициализация базы данных (2 минуты)
После первого деплоя backend сервиса:
- Открыть Dashboard → Backend Service → Shell
- Выполнить команды:
```bash
npx prisma migrate deploy
npx prisma generate
```

### 5. Проверка (3 минуты)
- [ ] Открыть URL frontend
- [ ] Проверить регистрацию пользователя
- [ ] Проверить загрузку аватарок
- [ ] Проверить работу с deals

## 💰 Стоимость:
- Backend: $7/мес
- Frontend: $7/мес  
- Database: $7/мес
- **Итого: ~$21/мес**

## ⏱️ Общее время: ~25 минут

## 🚀 После деплоя:
При каждом `git push` в ветку `main` будет автоматический деплой!

---
**Вопросы?** Смотри подробную инструкцию в `DEPLOYMENT_GUIDE.md`
