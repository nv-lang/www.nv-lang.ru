# nv-lang/www.nv-lang.ru

Зеркало [nv-lang/www](https://github.com/nv-lang/www) с CNAME для
второго домена. Обслуживает `https://nv-lang.ru/` через GitHub Pages.

## Как это работает

`.github/workflows/sync-from-www.yml` периодически (`*/15 *`) и по
ручному запуску:

1. Клонирует upstream `nv-lang/www` (источник Astro).
2. Собирает сайт (`npm ci` + `npm run build` в `site/`).
3. Применяет .ru-специфичный post-process:
   - **CNAME** → `nv-lang.ru` (override апстрим `.org` CNAME).
   - **ru-RU hreflang** инжектируется в каждый HTML с canonical
     (после x-default), указывает на саму себя на .ru.
   - **sitemap.xml** — URL `nv-lang.org` → `nv-lang.ru` для отдельной
     submission в Google Search Console .ru property.
4. Деплоит через GitHub Pages API (actions/deploy-pages).

**SEO-политика:** canonical остаётся → `.org` (consolidate SEO, нет
duplicate-penalty). Дополнительный `ru-RU` hreflang даёт .ru
SEO-присутствие для RU-locale queries в Yandex / Google.ru.

**Зачем зеркало, не редирект:** fallback на случай блокировки .org
в РФ + нарратив «отечественный язык программирования».

## Editing

**Контент сайта** редактируется только в [nv-lang/www](https://github.com/nv-lang/www).
В этом репо — только workflow зеркала.

## Ручной запуск deploy

GitHub → Actions → **Build & deploy nv-lang.ru mirror** → Run workflow.

## Pages configuration

Settings → Pages → Build and deployment → Source = **GitHub Actions**.
Если установлено «Deploy from branch» — workflow упадёт на deploy
step (Pages API недоступен в branch mode).

## License

Same as upstream: содержимое сайта — CC BY 4.0; workflow — MIT.
