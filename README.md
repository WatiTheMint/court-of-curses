# Суд Проклятий

Онлайн-игра: один накладывает проклятие, второй снимает его контерпиком из аниме, игр, фильмов или книг. Судит человек или ИИ (по промту). Дизайн в духе Nothing OS и ASCII.

Играть: `https://watithemint.github.io/court-of-curses/`

## Как устроено

- `index.html` - разметка, `style.css` - стили, `app.js` - логика (ES-модуль).
- Онлайн - Firebase: анонимный вход + Firestore. Конфиг проекта прямо в `app.js` (ключ Firebase публичный, базу защищают правила).
- `firestore.rules` - правила доступа к базе.
- `assets/stickers/` - стикеры.

## Данные в Firestore

- `matches/{code}` - стол: места, ники, фаза дела, протокол.
- `matches/{code}/presence/{uid}` - кто сейчас в зале (пульс раз в 25 секунд).
- `matches/{code}/events/{id}` - отправленные стикеры.

## Настройка Firebase (один раз)

1. Authentication → Sign-in method → **Anonymous** → Enable.
2. Firestore Database → Create database.
3. Firestore Database → **Rules** → вставить содержимое `firestore.rules` → Publish.
4. Authentication → Settings → Authorized domains → добавить `watithemint.github.io`.

## GitHub Pages

Settings → Pages → Deploy from a branch → `main` / `(root)` → Save.
