# utemix-contracts

**Хаб контрактов** — UI-контракты и ассеты для всех рендеров экосистемы.

## Что это

`utemix-workspace` — это единственный источник истины для:

- **UI контрактов** — layout, interaction, bindings
- **Маршрутов** — route graphs в JSON
- **Сессий** — состояния пользовательских сессий
- **Ассетов** — иконки, фоны, аватары, изображения
- **Текстов** — контент для Story/System/Service

## Принцип

```
contracts/public/ — единственный "язык" между рендерами
```

Любой рендер (Godot sandbox, web-viewer, vovaipetrova-core) **читает** эти файлы и отображает их содержимое. Рендеры **не изменяют** контракты напрямую.

## Структура

```
utemix-workspace/
├── README.md
├── contracts/
│   ├── ASSETS_AND_TEXTS_GUIDE.md    # Инструкция по размещению
│   └── public/
│       ├── ui/
│       │   ├── layout/              # Расположение панелей
│       │   ├── interaction/         # Правила взаимодействия
│       │   └── bindings/            # Связи элементов с ассетами
│       ├── sessions/                # Состояния сессий
│       │   └── demo/
│       ├── routes/                  # Граф-маршруты
│       │   └── demo/
│       ├── exports/                 # Экспорты из других репо
│       │   ├── canon_graph.jsonl
│       │   └── pointer_tags_registry.json
│       ├── assets/                  # Медиа-ассеты
│       │   ├── ui/
│       │   ├── icons/
│       │   ├── avatars/
│       │   ├── logos/
│       │   ├── flags/
│       │   ├── images/
│       │   ├── audio/
│       │   └── video/
│       ├── texts/                   # Текстовый контент
│       │   ├── story/
│       │   ├── system/
│       │   └── service/
│       └── manifests/
│           └── assets.manifest.json
└── sandboxes/
    ├── README.md
    └── web-viewer/                  # (заготовка для React)
```

## Контракты

### Layout (`ui/layout/*.json`)

Определяют расположение панелей для desktop и mobile:

```json
{
  "layout": {
    "desktop": {
      "panels": {
        "story": { "position": "left", "width": "280px" },
        "system": { "position": "right-top" },
        "service": { "position": "right-bottom" },
        "graph": { "position": "center" }
      }
    }
  }
}
```

### Interaction (`ui/interaction/*.json`)

Правила обработки событий:

```json
{
  "rules": [
    {
      "trigger": { "event": "click", "target": { "type": "tag" } },
      "effects": [
        { "type": "highlight", "target": "panel:story" },
        { "type": "log", "message": "Tag clicked" }
      ]
    }
  ]
}
```

### Bindings (`ui/bindings/*.json`)

Связи элементов UI с ассетами и контентом:

```json
{
  "bindings": [
    {
      "elementId": "panel-story",
      "assets": { "frame": "assets/ui/frames/panel-story.svg" },
      "style": { "accentColor": "#facc15" }
    }
  ]
}
```

## Как использовать

### Godot sandbox

```gdscript
# Путь к workspace (локальная связка)
const WORKSPACE_PATH = "../utemix-workspace/contracts/public"

func load_layout():
    var file = FileAccess.open(WORKSPACE_PATH + "/ui/layout/visitor.layout.json", FileAccess.READ)
    var layout = JSON.parse_string(file.get_as_text())
    apply_layout(layout)
```

### Web viewer

```javascript
// Fetch контракты
const layout = await fetch('/contracts/public/ui/layout/visitor.layout.json')
  .then(r => r.json());
```

## Добавление контента

1. **Ассеты** → `assets/*` (см. [ASSETS_AND_TEXTS_GUIDE.md](contracts/ASSETS_AND_TEXTS_GUIDE.md))
2. **Тексты** → `texts/story|system|service/`
3. **Обновить манифест** → `manifests/assets.manifest.json`

## Рендеры

| Рендер | Репозиторий | Статус |
|--------|-------------|--------|
| Godot sandbox | [utemix-godot-sandbox](https://github.com/utemix-lab/utemix-godot-sandbox) | 🚧 WIP |
| Web viewer | `sandboxes/web-viewer/` | 📋 Planned |
| vovaipetrova-core | [vovaipetrova-core](https://github.com/utemix-lab/vovaipetrova-core) | 🎯 Target |

## Лицензия

MIT © utemix-lab
