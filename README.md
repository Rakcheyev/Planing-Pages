# Planing-Pages — публічний showcase статичних HTML

Публічний репозиторій **лише для зібраних HTML-артефактів** із приватних DE-репо.
Код і генератори залишаються в приватних репо; CI пушить сюди готові файли.

## URL-шаблон

```text
https://rakcheyev.github.io/Planing-Pages/<slug>/<entry>
```

Приклад (Planing Gantt):

```text
https://rakcheyev.github.io/Planing-Pages/planing/timeline_gantt.html
```

## Структура

```text
index.html          # hub — список опублікованих сторінок по source repo
.nojekyll           # вимикає Jekyll на GitHub Pages
planing/
  timeline_gantt.html
  assets/...
pbi/                # майбутнє
dataops/            # майбутнє
```

## Деплой

- **Planing:** `.github/workflows/pages.yml` → `peaceiris/actions-gh-pages` → цей репо
- Секрет у Planing: `PAGES_DEPLOY_TOKEN` (PAT з `repo` на цей публічний репо)
- GitHub Pages: Settings → Source → Deploy from branch `main` / root (одноразово)

## Додати новий source repo

1. Додати секцію в `config/pages_publish.toml` (у приватному source repo).
2. Додати рядок у `index.html` (hub).
3. Розширити CI matrix / job у source repo — output у `dist/<slug>/`.
4. `keep_files: true` у peaceiris зберігає папки других репо при частковому деплої.

## Початкове наповнення

Скопіюйте цей шаблон у корінь публічного репо (`gh repo create` + push), або дозвольте
перший CI-run Planing заповнити `planing/` (hub `index.html` копіюється з цього шаблону).
