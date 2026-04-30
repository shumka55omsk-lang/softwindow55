# Vercel-ready папка

Эту папку можно загружать в GitHub и подключать к Vercel.

## Структура

- `index.html` — главная страница
- `styles.css` — стили
- `script.js` — калькулятор и мессенджеры
- `api/send-telegram.js` — отправка заявки в Telegram
- `api/check-telegram.js` — проверка переменных Telegram
- `assets/` — картинки
- `robots.txt` — индексация
- `sitemap.xml` — карта сайта
- `vercel.json` — настройки Vercel
- `package.json` — Node.js настройки

## В Vercel добавить переменные

Project → Settings → Environment Variables:

TELEGRAM_BOT_TOKEN
TELEGRAM_CHAT_ID

После добавления переменных нажмите Redeploy.

## Проверка

Откройте:

/api/check-telegram

Если `telegramBotTokenConfigured` и `telegramChatIdConfigured` равны `true`, отправка формы готова.
