# Полный пример README.md (creative-system)

> **Источник:** `AzamatSafarov/creative-system` — реальный репозиторий с бейджами, ASCII-артом, эмодзи-деревом и статусной таблицей.

---

```markdown
# 🌀 Creative System

<div align="center">

```
╔═══════════════════════════════════════════════════════╗
║  Work → (System Observes) → Draft → Approve → Publish ║
║         Работа  →  Наблюдение  →  Черновик  →  Публикация   ║
╚═══════════════════════════════════════════════════════╝
```

[![GitHub](https://img.shields.io/badge/GitHub-AzamatSafarov%2Fcreative--system-161b22?style=flat-square&logo=github)](https://github.com/AzamatSafarov/creative-system)
[![Status](https://img.shields.io/badge/status-active-success?style=flat-square)](#)
[![Stack](https://img.shields.io/badge/stack-FastAPI%20%2B%20SQLite%20%2B%20D3.js-blue?style=flat-square)](#)
[![Posts](https://img.shields.io/badge/posts-2%20published-yellow?style=flat-square)](#)
[![Vault](https://img.shields.io/badge/vault-LLM--Wiki-8b5cf6?style=flat-square)](#)

> *Работаешь — система пишет. Ты только решаешь, публиковать или нет.*

</div>

## Что это

Перманентная творческая система: любая деятельность (код, размышления, обсуждение) автоматически превращается в черновики статей. Ручной апрув перед публикацией.

## Архитектура

```
┌─────────────┐    ┌─────────────────┐    ┌──────────────┐    ┌─────────────┐
│  LLM-Wiki   │───→│  Autoposting    │───→│   Telegram   │───→│  Опубликовано│
│  (Obsidian) │    │  (FastAPI)      │    │  @Azamat_    │    │  в Telegram  │
│             │    │  SQLite         │    │  Safar0v     │    │              │
└─────────────┘    └─────────────────┘    └──────────────┘    └─────────────┘
       ↑
       │    ┌─────────────────┐
       └───→│ Artifact-Journalist│
            │ (AI-наблюдатель) │
            └─────────────────┘
```

## Структура

```
creative-system/
├── 📖 README.md              ← ты здесь
├── 📜 CHANGELOG.md           ← история всех изменений
│
├── ⚙️ autoposting-pro/       ← FastAPI + SQLite движок
│   ├── main.py               ← Telegram publisher (рабочий)
│   ├── requirements.txt      ← зависимости
│   └── index.html            ← HTML-клиент
│
├── 📝 llm-wiki/              ← Obsidian vault (симлинк)
│   └── articles/             ← 20 папок под платформы
│       ├── 00-concepts/      ← философия, архитектура
│       ├── 02-telegram/     ← Telegram @Azamat_Safar0v
│       ├── 03-devto/         ← Dev.to (EN)
│       └── 99-archive/       ← опубликованное
│
├── 🔍 agent-journalist/      ← AI-наблюдатель
│   ├── scan.py               ← сканер git + wiki
│   └── render.py             ← HTML → PNG рендер
│
└── 🎨 assets/
    └── diagrams/             ← PNG-карты системы
```

## Статус платформ

| Платформа | Папка | Статус | Язык | Формат |
|-----------|-------|--------|------|--------|
| Telegram | `02-telegram/` | ✅ Работает | RU | Короткие посты |
| Dev.to | `03-devto/` | 🟡 Заглушка | EN | Технические статьи |
| Medium | `04-medium/` | 🟡 Заглушка | EN | Длинные статьи |
| X/Twitter | `08-x-twitter/` | 🟡 Заглушка | EN | Треды |
| VK | `09-vk/` | 🟡 Заглушка | RU | Посты |
| LinkedIn | `10-linkedin/` | 🟡 Заглушка | EN | Профессиональные |
| Habr | `17-habr/` | ❌ Нет API | RU | Ручная публикация |
| vc.ru | `18-vcru/` | ❌ Нет API | RU | Ручная публикация |

## Process Notes

### Инструменты
- HTML/SVG диаграммы: JetBrains Mono, dark theme
- Рендер: Playwright + headless Chromium
- Автопуш: cron + bash (`llm-wiki-autopush`)

### Что работает / не работает
- ✅ Telegram публикация через FastAPI API
- ✅ Cron push в GitHub каждый день в 23:00
- 🟡 Dev.to, Medium, X, VK, LinkedIn — заглушки, нужны API ключи
- ❌ Habr, vc.ru — нет API для публикации

## Где всё лежит

| Слой | Что | Где |
|------|-----|-----|
| Контент | Obsidian vault | `C:\Users\akuta\Documents\LLM-Wiki` |
| Backend | FastAPI + SQLite | `~/creative-system/autoposting-pro/` |
| Frontend | HTML-клиент | `index.html` |
| AI Agent | Сканер + рендер | `~/.hermes/skills/artifact-journalist/` |
| Backup | Git cron | `AzamatSafarov/llm-wiki` (private) |

## Авторство

**Собрал и систематизировал [Азамат Сафаров](https://github.com/AzamatSafarov)**

См. также:
- [hessen-collected-works](https://github.com/AzamatSafarov/hessen-collected-works) — собрание сочинений С.И. Гессена
- [gessen-timeline](https://github.com/AzamatSafarov/gessen-timeline) — интерактивный таймлайн 235 работ
```

---

## Ключевые элементы этого примера

| Элемент | Где в тексте | Зачем |
|---------|-----------|-------|
| ASCII баннер | Под заголовком | Мгновенное понимание сути |
| Shields row | Под ASCII | Статус, stack, метрики — одним взглядом |
| Italic pitch | Под shields | 15 слов, объясняющих «зачем это» |
| Emoji tree | `## Структура` | Визуальная навигация по папкам |
| Status table | `## Статус` | ✅🟡❌ — сканируется за 2 секунды |
| System map table | `## Где всё лежит` | Backend vs Frontend vs Agent |
| Author footer | Внизу | Атрибуция, связанные проекты |

## Бейджи (shields.io)

```markdown
[![GitHub](https://img.shields.io/badge/GitHub-USER%2FREPO-161b22?style=flat-square&logo=github)](URL)
[![Status](https://img.shields.io/badge/status-active-success?style=flat-square)](#)
[![Stack](https://img.shields.io/badge/stack-TECH-blue?style=flat-square)](#)
[![Posts](https://img.shields.io/badge/posts-N-yellow?style=flat-square)](#)
```

Color codes:
- `success` = зелёный, работает
- `blue` = информация, стек
- `yellow` = предупреждение, частично
- `red` = сломано / нет API
- `lightgrey` = архив / история

## Anti-slop пример

Плохо: «Как вы можете видеть, система работает хорошо. Важно отметить, что...»
Хорошо: «Telegram шлёт сообщения. Остальные платформы молчат — у них нет API ключей.»
