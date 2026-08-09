# HTML Footer для визуализаций

> Копировать в каждый HTML-артефакт: таймлайн, диаграмма, интерактив.

## Базовый вариант (минималистичный, тёмная тема)

```html
<!-- Авторство -->
<div style="position:fixed;bottom:12px;left:50%;transform:translateX(-50%);z-index:10;
  color:#444460;font-size:11px;letter-spacing:0.5px;font-family:'Segoe UI',system-ui,sans-serif;
  pointer-events:none;">
  Собрал и визуализировал <span style="color:#7c83fd">Азамат Сафаров</span> ·
  <a href="https://github.com/AzamatSafarov/REPO" style="color:#666680;text-decoration:none;pointer-events:auto;">REPO</a>
</div>
```

## Расширенный вариант (с несколькими ссылками)

```html
<div id="author" style="position:fixed;bottom:12px;left:50%;transform:translateX(-50%);z-index:10;
  color:#444460;font-size:11px;letter-spacing:0.5px;font-family:'Segoe UI',system-ui,sans-serif;
  pointer-events:none;text-align:center;">
  Собрал и визуализировал <a href="https://github.com/AzamatSafarov" style="color:#7c83fd;text-decoration:none;pointer-events:auto;">Азамат Сафаров</a> ·
  <a href="https://github.com/AzamatSafarov/REPO1" style="color:#666680;text-decoration:none;pointer-events:auto;">REPO1</a> ·
  <a href="https://github.com/AzamatSafarov/REPO2" style="color:#666680;text-decoration:none;pointer-events:auto;">REPO2</a>
</div>
```

## Правила

1. **position: fixed; bottom: 12px** — всегда прибит к низу, не скроллится
2. **left: 50%; transform: translateX(-50%)** — идеальное центрирование
3. **z-index: 10** — поверх canvas/graph, но ниже tooltip (z-index: 100)
4. **color: #444460** — приглушённый, не отвлекает от контента
5. **pointer-events: none** на контейнере, **pointer-events: auto** на ссылках — кликабельны только ссылки
6. **Акцентный цвет для имени** — `#7c83fd` (философия) или `#58a6ff` (GitHub blue)

## CSS-вариант (если есть stylesheet)

```css
#author {
  position: fixed;
  bottom: 12px;
  left: 50%;
  transform: translateX(-50%);
  z-index: 10;
  color: #444460;
  font-size: 11px;
  letter-spacing: 0.5px;
  pointer-events: none;
  text-align: center;
}
#author a {
  color: #666680;
  text-decoration: none;
  pointer-events: auto;
  transition: color 0.2s;
}
#author a:hover { color: #58a6ff; }
#author .name { color: #7c83fd; }
```

## Примеры применения

- Таймлайн Гессена: `gessen-timeline`
- Диаграмма архитектуры: `autoposting-architecture`
- Карта системы: `SYSTEM-MAP`
- Любой p5.js / D3.js / Canvas проект
