# Web Viewer

> 🚧 **Planned** — заготовка для будущего React preview.

## Описание

Простой web-based viewer для:

- Превью Route Graph без Godot
- Тестирование UI контрактов
- Быстрый feedback loop

## Технологии (планируется)

- React + Vite
- Cytoscape.js (граф)
- CSS Variables (темы)

## Установка (будущее)

```bash
npm create vite@latest . -- --template react-ts
npm install
npm install cytoscape
```

## Структура (планируется)

```
web-viewer/
├── index.html
├── package.json
├── vite.config.ts
├── src/
│   ├── App.tsx
│   ├── components/
│   │   ├── Graph.tsx
│   │   ├── StoryPanel.tsx
│   │   ├── SystemPanel.tsx
│   │   └── ServicePanel.tsx
│   └── hooks/
│       ├── useLayout.ts
│       ├── useInteraction.ts
│       └── useBindings.ts
```

## Контракты

Читает из:
```
../../contracts/public/
```
