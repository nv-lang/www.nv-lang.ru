# nv-lang/www.nv-lang.ru

Зеркало [nv-lang/www](https://github.com/nv-lang/www) с CNAME для второго домена.

Этот репозиторий обслуживает `https://nv-lang.ru/` через GitHub Pages. Содержимое **не редактируется здесь напрямую** — GitHub Action `.github/workflows/sync-from-www.yml` каждые 15 минут (а также по ручному запуску) тянет последнюю версию из `nv-lang/www` и пушит её сюда, подменяя `CNAME` на `nv-lang.ru`.

Правки сайта делаются в `nv-lang/www`.

## Ручной запуск синхронизации

GitHub → Actions → **Sync from nv-lang/www** → Run workflow.
