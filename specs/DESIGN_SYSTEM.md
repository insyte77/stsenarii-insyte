# INSYTE Design System
> Дизайн-система для проекта BOX FOR LIFE — выставочный демонстрационный дом, шоу-рум «Белая дача»

---

## Цветовая палитра

| Переменная     | HEX       | Название            | Применение |
|----------------|-----------|---------------------|------------|
| `--dark`       | `#0b1413` | Тёмно-зелёный       | Фон hero, шапка страниц, тёмные секции |
| `--dark2`      | `#0f1a19` | Глубокий тёмный     | Фон футера |
| `--ink`        | `#171d2c` | Чернильный          | Основной текст на светлом фоне |
| `--ink-soft`   | `#525d75` | Дымчатый синий      | Подписи, вторичный текст, описания |
| `--gold`       | `#c9a36a` | Золото              | Акцентный цвет: лого, линии, иконки, кнопки |
| `--gold-h`     | `#d9b67e` | Золото (hover)      | Состояние наведения золотых элементов |
| `--gold-lt`    | `#ede8de` | Светлое золото      | Бэджи, теги, светлые акценты |
| `--bg`         | `#f8f6f3` | Тёплый белый        | Основной фон страницы |
| `--secondary`  | `#f0ece4` | Бежевый             | Альтернативный фон секций, hover карточек |
| `--border`     | `#e0ddd8` | Граница             | Разделители, рамки элементов |
| `--line`       | `#d4cfc7` | Линия               | Тонкие сетки между карточками |
| `--white`      | `#ffffff` | Белый               | Текст на тёмном фоне, кнопки |

### Принципы применения цвета

- **Тёмные секции** (`--dark`): hero, комнаты, командный блок — текст белый, акцент золотой
- **Светлые секции** (`--bg`): основной контент — текст `--ink`, вторичный `--ink-soft`
- **Золото** — единственный яркий цвет в системе; всё остальное нейтрально
- **Без ярких RGB-цветов**: синий, зелёный, красный не используются в фирменном стиле

---

## Шрифты

### Display — Cormorant Garamond
```
font-family: 'Cormorant Garamond', 'Times New Roman', serif
```
- Класс: Display / Editorial serif
- Начертания: 400 (Regular), 500 (Medium), 600 (SemiBold)
- Стили: Normal, Italic
- Подключение: Google Fonts + встроен в HTML base64 (WOFF2, все Unicode-поддиапазоны)

**Используется для:**
- H1 героя: `font-size: clamp(22px, 2.5vw, 36px)`, weight 600, uppercase, letter-spacing 0.02em
- H2 секций: `font-size: clamp(32px, 3.5vw, 52px)`, weight 600, uppercase
- H3 карточек: `font-size: 26px`, weight 600, uppercase
- Числа статистики: `font-size: 36px`, weight 500
- Декоративные номера: `font-size: 13px`, weight 500, letter-spacing 0.1em
- Названия комнат: `font-size: 18px`, weight 500, uppercase
- Курсив (`<em>`): вторичные подзаголовки, затемнённый цвет

### Sans-serif — Inter
```
font-family: 'Inter', system-ui, sans-serif
```
- Класс: Geometric sans-serif
- Начертания: 300 (Light), 400 (Regular), 500 (Medium), 600 (SemiBold)
- Подключение: Google Fonts + встроен в HTML base64 (WOFF2)

**Используется для:**
- Основной текст body: `font-size: 14px`, weight 400, line-height 1.6
- Навигация: `font-size: 10px`, weight 500, uppercase, letter-spacing 0.22em
- Eyebrow / метки: `font-size: 10px`, weight 500, uppercase, letter-spacing 0.22em–0.32em
- Подписи под числами: `font-size: 9px–10px`, uppercase, letter-spacing 0.18em–0.2em
- Описания карточек: `font-size: 12px`, weight 400, line-height 1.7
- Теги и бэджи: `font-size: 9px`, weight 500, uppercase, letter-spacing 0.12em–0.22em

---

## Типографическая иерархия

| Уровень        | Шрифт             | Размер                   | Weight | Case      | Letter-spacing |
|----------------|-------------------|--------------------------|--------|-----------|----------------|
| Hero H1        | Cormorant Garamond | clamp(22px, 2.5vw, 36px) | 600    | UPPERCASE | 0.02em         |
| Section H2     | Cormorant Garamond | clamp(32px, 3.5vw, 52px) | 600    | UPPERCASE | 0.02em         |
| Card H3        | Cormorant Garamond | 26px                      | 600    | UPPERCASE | 0.02em         |
| Stat number    | Cormorant Garamond | 36px                      | 500    | —         | —              |
| Room name      | Cormorant Garamond | 18px                      | 500    | UPPERCASE | —              |
| Eyebrow        | Inter              | 10px                      | 500    | UPPERCASE | 0.22em–0.32em  |
| Nav link       | Inter              | 10px                      | 500    | UPPERCASE | 0.22em         |
| Body text      | Inter              | 14px                      | 400    | —         | —              |
| Card desc      | Inter              | 12px                      | 400    | —         | —              |
| Tag / badge    | Inter              | 9px                       | 500    | UPPERCASE | 0.12em–0.22em  |
| Footer meta    | Inter              | 9px                       | 400    | UPPERCASE | 0.2em          |

---

## Принципы компоновки

- **Нет border-radius** — все элементы с острыми углами (`border-radius: 0 !important`)
- **Сетка карточек** — `gap: 1px; background: var(--line)` создаёт тонкую сетку-разделитель
- **Максимальная ширина контента** — `max-width: 1400px; margin: 0 auto`
- **Горизонтальный padding** — `40px–48px` на всех секциях
- **Золотая линия** — разделитель разделов: `border-top: 3px solid var(--gold)` или `border-bottom: 1px solid var(--border)`

---

## Компоненты

### Кнопка primary (CTA)
```css
background: var(--gold); color: var(--dark);
font: 500 10px/1 Inter; text-transform: uppercase; letter-spacing: .28em;
padding: 16px 28px;
```
Hover: `background: var(--gold-h)`

### Кнопка secondary (текстовая)
```css
color: rgba(255,255,255,.75); border-bottom: 1px solid rgba(201,163,106,.4);
font: 400 10px/1 Inter; text-transform: uppercase; letter-spacing: .28em;
```
Hover: `color: white; border-color: var(--gold)`

### Eyebrow (надпись над заголовком)
```css
font: 500 10px/1 Inter; text-transform: uppercase; letter-spacing: .22em;
color: var(--ink-soft);
```
Сопровождается горизонтальной линией `width: 32px; height: 1px; background: var(--gold)`.

### Карточка документа (doc-card)
- Фон `--bg`, hover → `--secondary`
- Номер документа: Cormorant Garamond 13px, `--gold`
- Заголовок: Cormorant Garamond 26px, uppercase
- Описание: Inter 12px, `--ink-soft`
- Кнопка перехода: фон `--ink`, hover → `--gold`

### Тег комнаты (rtag)
```css
font: 500 9px/1 Inter; text-transform: uppercase; letter-spacing: .12em;
padding: 2px 7px; background: rgba(201,163,106,.12); color: rgba(255,255,255,.65);
border: 1px solid rgba(201,163,106,.2);
```
Gold-вариант: `background: rgba(201,163,106,.25); color: var(--gold)`

---

## Структура страницы (box4life.html)

```
NAV (fixed, 72px) — логотип слева, ссылки справа
  │ прозрачный на hero, белый при scroll
HERO (min-height: 100vh, фон --dark)
  │ eyebrow → H1 → subtitle → stats → CTA → PDF-ссылки
STAT STRIP (8 колонок, светлый фон)
DOCUMENTS (2 колонки карточек)
ROOMS (4 колонки, тёмный фон)
NOTES (2 колонки)
TEAM BLOCK (тёмный фон, 2 колонки: IDEA HOUSE | INSYTE GROUP)
FOOTER (--dark2)
```

---

## Файлы

| Файл | Описание |
|------|----------|
| `specs/box4life.html` | Главная страница, **автономный** (шрифты + логотип встроены base64), ~2.3 MB |
| `specs/PIN_MAPPING_BIZNES_v1.3.html` | Пин-маппинг оборудования |
| `specs/LIGHTING_LOGIC_BIZNES_v1.3.html` | Логика освещения |
| `specs/SCENARIOS_BIZNES_v1.3.html` | Сценарии умного дома |
| `specs/AC_SCENARIOS_BIZNES_v1.3.html` | Кондиционирование и вентиляция |
| `specs/Logo INSYTE GOLD.png` | Логотип INSYTE (золото, прозрачный фон), высота в UI: 14px |
