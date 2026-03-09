# 🚀 Быстрый старт для деплоя на Render.com

## Минимальные действия (всего 3 шага):

### Шаг 1️⃣ Загрузить код на GitHub

```bash
# Перейдите в директорию проекта
cd e:\TestTask\Zenbittech\1

# Инициализируйте git (если еще не инициализирован)
git init

# Добавьте все файлы
git add .

# Сделайте коммит
git commit -m "Deploy to Render"

# Создайте ветку main
git branch -M main

# Создайте репозиторий на GitHub и подключите его
git remote add origin https://github.com/ВАШ_НИК/ВАШ_РЕПОЗИТОРИЙ.git

# Отправьте код на GitHub
git push -u origin main
```

### Шаг 2️⃣ Создать сервисы на Render

1. Откройте https://render.com и войдите через GitHub
2. Нажмите **"New +"** → выберите **"Blueprint"**
3. Выберите ваш репозиторий из списка
4. Render автоматически создаст:
   - ✅ Backend (NestJS + Prisma)
   - ✅ Frontend (React + Vite)  
   - ✅ PostgreSQL базу данных

### Шаг 3️⃣ Настроить переменные окружения

После создания сервисов откройте настройки каждого:

**Backend Service → Environment:**
```
NODE_ENV = production
PORT = 3000
JWT_SECRET = ваш_секретный_ключ_123456
JWT_EXPIRES_IN = 7d
CORS_ORIGIN = https://investprop-frontend.onrender.com
```

**Frontend Service → Environment:**
```
VITE_API_URL = https://investprop-backend.onrender.com
VITE_APP_NAME = InvestProp
```

> 🔑 **Важно:** Замените URL на актуальные (их можно увидеть в панели сервисов)

---

## ✅ Проверка работы

Откройте в браузере URL вашего frontend сервиса и проверьте:
- Регистрацию нового пользователя
- Вход в систему
- Загрузку аватарки
- Просмотр deals

---

## 💡 Если что-то пошло не так

### Backend не запускается
Откройте **Backend Service → Logs** и посмотрите ошибки

### Frontend не подключается к API
Проверьте переменную `VITE_API_URL` в настройках frontend

### Ошибки базы данных
Откройте **Backend Service → Shell** и выполните:
```bash
npx prisma migrate deploy
npx prisma generate
```

---

## 📚 Полная документация

- Подробная инструкция: `DEPLOYMENT_GUIDE.md`
- Чеклист: `DEPLOY_CHECKLIST.md`
- Конфигурация: `render.yaml`

---

## 💰 Стоимость

Тариф "Starter" для всех сервисов:
- Backend: $7/мес
- Frontend: $7/мес
- Database: $7/мес
- **Итого: $21/мес**

Можно начать с бесплатных тарифов для тестирования!

---

**Готово!** 🎉 Ваше приложение доступно по URL, который выдаст Render.
