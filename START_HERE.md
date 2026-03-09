# 🎯 ДЕПЛОЙ НА RENDER.COM - БЫСТРАЯ ИНСТРУКЦИЯ

## ⚡ САМЫЙ БЫСТРЫЙ ПУТЬ (3 команды + 2 клика)

### 1️⃣ Отправь код на GitHub

```bash
cd e:\TestTask\Zenbittech\1
git init; git add .; git commit -m "Deploy"; git branch -M main
git remote add origin https://github.com/ТВОЙ_НИК/ТВОЙ_РЕПОЗИТОРИЙ.git
git push -u origin main
```

### 2️⃣ Создай сервис на Render

1. Открой https://render.com и войди через GitHub
2. Нажми **New +** → **Blueprint**
3. Выбери свой репозиторий
4. Готово! 🎉

### 3️⃣ Настрой 5 переменных окружения

**Backend Service → Environment:**
```
NODE_ENV=production
PORT=3000
JWT_SECRET=any_secret_key_you_like
JWT_EXPIRES_IN=7d
CORS_ORIGIN=https://твой-frontend.onrender.com
```

**Frontend Service → Environment:**
```
VITE_API_URL=https://твой-backend.onrender.com
VITE_APP_NAME=InvestProp
```

---

## 📚 ЕСЛИ НУЖНЫ ПОДРОБНОСТИ

Читай файлы по порядку:

1. **READY_FOR_RENDER.md** - что уже готово ✅
2. **QUICK_START_RENDER.md** - быстрый старт 🚀
3. **DEPLOY_CHECKLIST.md** - чеклист шагов ✅
4. **DEPLOYMENT_GUIDE.md** - полная инструкция 📖

---

## 💰 СТОИМОСТЬ

~$21/мес за все сервисы (Backend + Frontend + Database)

---

## 🎉 ВСЁ!

Твоё приложение доступно по URL, который выдаст Render!

**Вопросы?** → Читай `DEPLOYMENT_GUIDE.md`
