# Подготовка к защите лабораторной работы №1

Проект — frontend-каркас трекера лабораторных работ и домашних заданий. Реализованы ленты, задания, расписание, планер и уведомления.

## Главное по коду

`main.tsx` подключает React к `<div id="root">` из `index.html`. `BrowserRouter` хранит текущий URL, `Routes` выбирает экран, а `NavLink` выполняет переходы без перезагрузки.

`Layout` содержит общую навигацию. Массив маршрутов через `.map` превращается в кнопки: первый элемент пары — адрес `to`, второй — текст `label`, `key` нужен React для элементов списка.

`Dashboard` показывает статистику и вызывает `TaskList`. `TaskList` через `.map` превращает каждый объект `tasks` в `ListItem`.

`Tasks` хранит `title` и `shown` в `useState`. `TextField` получает `value={title}`, а `onChange` записывает новый текст через `setTitle`. Кнопка проверяет `title.trim()`, создаёт новую задачу и вызывает `setShown`. `shown` передаётся в `TaskListOverride` через prop.

`TaskListOverride` получает prop `tasks`, переименовывает его в `list` и выводит строки через `.map`. `Schedule` повторно использует этот компонент, `Planner` и `Notifications` возвращают свои экраны.

## Связь компонентов

```text
Layout → Routes → Dashboard → TaskList
Layout → Routes → Tasks → TaskListOverride
Layout → Routes → Schedule → TaskListOverride
Layout → Routes → Planner / Notifications
```

## План backend для лабораторной №2

Backend в первой лабораторной не реализуется. План: `React → FastAPI → SQLAlchemy → PostgreSQL`, маршруты `GET /api/tasks`, `POST /api/tasks`, `GET /api/courses`.

## Конфигурация

`package.json` хранит зависимости и команды npm. `package-lock.json` фиксирует версии пакетов. `tsconfig` настраивает проверку TypeScript. `vite.config.ts` подключает React-плагин Vite. `node_modules` создаётся через `npm install`, `dist` — через `npm run build`.
