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


## Исправление кнопки Telegram

В этой версии кнопка Telegram получает ссылку автоматически через `/api/telegram-link`.

Vercel берёт `TELEGRAM_BOT_TOKEN`, запрашивает username бота и отдаёт на сайт ссылку вида:

```text
https://t.me/username_бота
```

Проверка после деплоя:

```text
https://ваш-домен/api/telegram-link
```

Должно вернуться:

```json
{
  "ok": true,
  "username": "имя_бота",
  "url": "https://t.me/имя_бота"
}
```

Важно: при открытии `index.html` двойным кликом на ПК ссылка Telegram может не подтянуться, потому что `/api/telegram-link` работает на Vercel.


## Telegram-кнопка

Кнопка Telegram настроена на прямой личный профиль:

```text
https://t.me/Anvar_company
```

Она не ведет на бота. Отправка формы заявки в Telegram через Vercel при этом остается через `api/send-telegram.js`.
