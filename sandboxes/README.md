# Sandboxes

Локальные песочницы для тестирования контрактов и ассетов.

## Структура

```
sandboxes/
├── README.md
└── web-viewer/          # React preview (planned)
```

## web-viewer (planned)

Простой React-based viewer для превью контрактов без Godot.

### Функции (планируется)

- Загрузка layout, interaction, bindings
- Отображение Route Graph
- Тестирование взаимодействий
- Hot-reload при изменении контрактов

### Запуск (будущее)

```bash
cd sandboxes/web-viewer
npm install
npm run dev
```

## Godot sandbox

Основной sandbox находится в отдельном репозитории:
[utemix-godot-sandbox](https://github.com/utemix-lab/utemix-godot-sandbox)

Для связки с workspace используйте относительный путь:
```
../utemix-workspace/contracts/public/
```
