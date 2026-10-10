# СмартГід — навчальний SEO-проєкт

Статичний сайт: HTML5, CSS3, vanilla JS. Без збірки й залежностей.

## Структура репозиторію
Файли лежать **у корені репозиторію** (не в підпапці):

```
index.html, 404.html, favicon.svg, robots.txt, sitemap.xml
assets/{css,js,img}/
android-chy-iphone/  ihrovyi-smartfon/  kharakterystyky/  pro-proiekt/
.github/workflows/deploy.yml
```

## Деплой на GitHub Pages
1. Запуште код у гілку `main`.
2. Репозиторій → **Settings → Pages → Build and deployment → Source: GitHub Actions**.
3. Workflow `Deploy to GitHub Pages` запуститься сам (або вручну: Actions → Run workflow).

Сайт буде доступний за `https://<користувач>.github.io/<назва-репозиторію>/`
(або за власним доменом, якщо його налаштовано в Settings → Pages).

### Як працюють шляхи й адреси
- Внутрішні посилання, CSS, JS і favicon — **відносні** (`./`, `../`, `../../`), тому сайт працює і в підпапці
  `/<репозиторій>/`, і на власному домені, і локально.
- Плейсхолдер `__SITE_URL__` (canonical, og:url, og:image, JSON-LD, `sitemap.xml`, `robots.txt`) і
  `__BASE_PATH__` (лише `404.html`) workflow замінює на реальну адресу автоматично.
  **Не замінюйте їх вручну.** У збірці лишити плейсхолдер неможливо — деплой впаде з помилкою.
- Створюючи нову сторінку, використовуйте відносні шляхи за глибиною вкладеності та `__SITE_URL__` у мета-тегах.

## Локальний запуск
```
python3 -m http.server 8000
```
і відкрийте http://localhost:8000/ (canonical/og-теги локально показують `__SITE_URL__` — це нормально).

## Перед публікацією
- Додати контактну адресу на `/pro-proiekt/`, звірити всі «демонстраційні дані».
- За потреби додати `favicon.ico` / `apple-touch-icon.png`.
- Для SEO краще власний домен: `robots.txt` і `sitemap.xml` краще працюють у корені домену, а не в `/<репозиторій>/`.
