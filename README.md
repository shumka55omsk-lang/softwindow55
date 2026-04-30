# Сайт «Мягкие окна в Омске»

Готовый лендинг под Vercel: SEO под Омск и Омскую область, форма расчета размеров окон, отправка заявки в Telegram-бота, кнопки звонка и мессенджеров.

## Что внутри

- `index.html` — SEO-лендинг.
- `styles.css` — адаптивная верстка под ПК и смартфоны.
- `script.js` — калькулятор размеров, кнопки WhatsApp / Telegram / Max, отправка формы.
- `api/send-telegram.js` — Vercel Serverless Function для отправки заявки в Telegram.
- `api/check-telegram.js` — проверка, видит ли Vercel переменные Telegram.
- `robots.txt` и `sitemap.xml` — базовые файлы индексации.
- `google0000000000000000.html` и `yandex_0000000000000000.html` — шаблоны файлов подтверждения. Их нужно заменить на реальные файлы из Google Search Console и Яндекс.Вебмастер.
- `assets/` — изображения для сайта.

## Как разместить на Vercel

1. Распакуйте ZIP.
2. Создайте репозиторий на GitHub и загрузите все файлы из папки.
3. В Vercel нажмите `Add New Project` → выберите репозиторий.
4. Framework Preset оставьте `Other`.
5. Build Command оставьте пустым.
6. Output Directory оставьте пустым.
7. После деплоя откройте `Project → Settings → Environment Variables`.
8. Добавьте:
   - `TELEGRAM_BOT_TOKEN`
   - `TELEGRAM_CHAT_ID`
9. Нажмите `Redeploy`.

Проверка Telegram:
`https://ваш-домен/api/check-telegram`

Если обе переменные `true`, форма должна отправлять заявки.

## Что заменить под себя

В `script.js`:
- `whatsapp` — номер WhatsApp в международном формате без плюса.
- `telegramUrl` — ссылка на ваш Telegram.
- `maxUrl` — ссылка Max.

В `index.html`, `robots.txt`, `sitemap.xml`:
- замените `https://example.com/` на ваш реальный домен.

В файлах верификации:
- удалите шаблонные `google0000000000000000.html` и `yandex_0000000000000000.html`;
- скачайте реальные файлы из Google Search Console и Яндекс.Вебмастер;
- положите их в корень сайта.


## Если на ПК не видно картинки

В этой версии пути к картинкам сделаны относительными: `assets/...`, поэтому изображения должны отображаться даже при открытии `index.html` двойным кликом на компьютере.

Важно: отправка формы в Telegram локально через двойной клик не заработает, потому что API `/api/send-telegram` запускается только на Vercel или через `vercel dev`. Для проверки отправки нужно загрузить сайт на Vercel.


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
