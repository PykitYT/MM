# MM
# 2D Minecraft + Моды

## Как играть
- **A/D или ←/→** — двигаться
- **W/Пробел/↑** — прыжок
- **ЛКМ** — удалить блок
- **ПКМ** — поставить блок (`grass` по умолчанию)
- **TAB** — открыть чит-меню (Tkinter)

## Функции в `Player`
- `update(world, keys)` — движение, гравитация, прыжок
- `draw(screen, camera_x)` — отрисовка
- `get_position()` → `(block_x, block_y)`
- `tp(block_x, block_y)` — телепорт в блок

> Добавь в `__init__`: `self.tp_queue = queue.Queue()`

## Функции в `World`
- `generate_world()` — генерирует мир
- `get_block(x, y)` → блок или `None`
- `set_block(x, y, type)` — ставит/удаляет блок (через очередь)
- `process_removals()` — обрабатывает удаления
- `get_blocks_around(rect)` — блоки вокруг
- `clear_world()` — очищает всё
- `fill_layer(y, type)` — заполняет слой
- `build_structure(cx, cy, list, type)` — строит из списка `[[dx, dy], ...]`

## Создание модов
1. Создайте файл в папке Mods
2. Напишите код так:
любые импорты
def background_task(world, player, BLOCK_SIZE, WORLD_WIDTH, pygame):
    ваш код

## Пример мода
```def background_task(world, player, _, _, _):
    print('[FlatWorldMod] Creating map...')
    for x in range(201):
        for y in range(201):
            world.set_block(x, y, "air")
    for x in range(201):
        world.set_block(x, 15, "stone")
    print('[FlatWorldMod] Done!')```

## Моды
- Папка `mods/`
- Функция: `background_task(world, player, BLOCK_SIZE, WORLD_WIDTH, pygame)`
- Пример: `auto_remove.py`, `tree_spawner.py`

## Полезно
- `BLOCK_SIZE = 32`
- `WORLD_WIDTH = 100`
- Безопасность: `set_block(..., 'air')`
