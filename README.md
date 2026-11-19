# RD Corporation

Одиночный idle-тайкун про студию, которая превращает разовые заказы в собственную программную платформу. Механики,
контент и этапы производства описаны в [GDD](docs/GDD.md).

## Запуск проекта

1. Разместите доступный вам репозиторий [UnityTemplates](https://github.com/denisPavlenko7610/UnityTemplates) рядом с
   `RD_Corporation`. Базовая проверенная ревизия записана
   в [Tools/UnityTemplates.revision](Tools/UnityTemplates.revision).
2. Из корня проекта выполните:

   ```powershell
   powershell -NoProfile -ExecutionPolicy Bypass -File Tools/Link-UnityTemplates.ps1
   ```

   Для другого расположения передайте `-TemplateProject 'D:\UnityTemplates'`.
3. Откройте проект в версии из [ProjectVersion.txt](ProjectSettings/ProjectVersion.txt). Для импорта Addressables нужен
   доступ к реестру Unity.

Каталоги `Runtime` и `Editor` внутри `Assets/TemplateSources` ведут в общий checkout. Git хранит метаданные папок и
скрипт восстановления связей. Для нового модуля добавьте его в список скрипта, подключите его зависимости, повторно
запустите скрипт и проверьте компиляцию. Исходники общего модуля сопровождаются в UnityTemplates.

## Структура проекта

| Путь                          | Назначение                                                                            |
|-------------------------------|---------------------------------------------------------------------------------------|
| `Assets/Scenes`               | Стартовая сцена Unity                                                                 |
| `Assets/Settings`             | Конфигурации URP для мобильных устройств и ПК                                         |
| `Assets/TemplateSources`      | Общие сборки и утилиты UnityTemplates                                                 |
| `Packages`, `ProjectSettings` | Зависимости и настройки Unity                                                         |
| `Assets/_Project`             | Целевой каталог игровых сцен, кода, UI, данных и тестов. Создаётся по мере разработки |
| `Tools`, `docs`               | Подключение зависимостей и проектная документация                                     |