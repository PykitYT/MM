# MM
# 2D Minecraft + Моды

## Как играть
- **A/D или ←/→** — двигаться
- **W/Пробел/↑** — прыжок
- **ЛКМ** — удалить блок
- **ПКМ** — поставить блок (`grass` по умолчанию)

## Функции в `Player`
- `update(world, keys)` — движение, гравитация, прыжок
- `handle_collision_x(world)` — коллизии по X
- `handle_collision_y(world)` — коллизии по Y
- `draw(screen, camera_x)` — отрисовка
- `get_position()` → `(block_x, block_y)`
- `tp(block_x, block_y)` — телепорт в блок

## Функции в `World`
- `generate_world()` — генерирует мир
- `get_block(x, y)` → блок или `None`
- `set_block(x, y, type)` — ставит/удаляет блок (через очередь)
- `process_removals()` — обрабатывает удаления
- `get_blocks_around(rect)` — блоки вокруг

## Создание модов
1. Создайте файл в папке `mods`
2. Напишите код так:
```python
# любые импорты
def background_task(world, player, BLOCK_SIZE, WORLD_WIDTH, pygame):
    # ваш код
```

## Пример мода
```python
def background_task(world, player, _, _, _):
    print('[FlatWorldMod] Creating map...')
    for x in range(201):
        for y in range(201):
            world.set_block(x, y, "air")
    for x in range(201):
        world.set_block(x, 15, "stone")
    print('[FlatWorldMod] Done!')
```

## Моды
- Папка `mods/`
- Функция: `background_task(world, player, BLOCK_SIZE, WORLD_WIDTH, pygame)`

## Полезно
- `BLOCK_SIZE = 32`
- `WORLD_WIDTH = 100`
- Безопасность: `set_block(..., 'air')`
