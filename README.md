# [Автономный LLM-ассистент для ведущих НРИ](#автономный-llm-ассистент-для-ведущих-нри)

## Оглавление
- [Проблематика](#проблематика)
- [Сценарии использования](#сценарии-использования)
- [Основные функции](#основные-функции)
- [Технические особенности и варианты реализации](#технические-особенности-и-варианты-реализации)
- [Список задач](#список-задач)

Данный проект представляет собой автономного LLM-ассистента, предназначенного для поддержки гейммастеров (ГМ) в процессе генерации контента, ведения игр и взаимодействия с игроками. Целью является создание инструмента, который упростит и улучшит игровой процесс.

## [Проблематика](#проблематика)
В ходе разработки были выявлены основные проблемы, с которыми сталкиваются гейммастеры:
- Обширный объем информации, который необходимо удерживать в памяти, или наличие множества записей, содержащих эту информацию.
- Необходимость в оперативной генерации креативного контента в процессе игры.

## [Сценарии использования](#сценарии-использования)
1. **Создание кампейна**: ГМ, пишущий кампейн, может обратиться к ассистенту за информацией из предыдущих игр, что позволяет быстро находить нужные данные.
2. **Адаптация сюжета**: В случае, если история уходит в незапланированное русло, ГМ может запросить у ассистента карты местности, описания локаций, персонажей и другие материалы.
3. **Взаимодействие с НПЦ**: Во время игры, когда игроки общаются с неигровыми персонажами (НПЦ), ГМ может делегировать этот диалог ассистенту, который будет озвучивать реплики.

## [Основные функции](#основные-функции)
- Подбор и воспроизведение голоса персонажей (подбор интонации итд по персонажу)
- Создание диалога для неигровых персонажей
- Генерация НПС - Интеграция с https://donjon.bin.sh/ 
- Генерация данжей - Интеграция с https://donjon.bin.sh/ 
- Поиск информации из интернета, если его нет в базе знаний.
- Поиск по базе знаний - Интеграция с dnd.su 
- Возможность слушать игроков во время сессии и генерировать ответы на их запросы.

## [Дополнительные функции](#дополнительные-функции)
- Долгосрочная память на основе RAG с возможностью интеграции материалов из записей ГМ.
- Интеграция с виртуальными игровыми столами (например, FoundryTTV).
- Управление боевыми сценами.

## [Технические особенности и варианты реализации](#технические-особенности-и-варианты-реализации)
- **Модель LLM**: Для реализации требуется мощная мультимодальная модель. На данный момент наиболее подходящим вариантом является интеграция GPT-4 (или GPT-3.5, если будет доступен качественный API). Возможно, потребуется подписка на сервис, однако для аудио-озвучки потребуется интеграция с дополнительными сервисами, такими как Whisper. Также можно рассмотреть опенсорсные решения, хотя их мощность может быть ограничена. Альтернативно, возможно создание оркестра моделей, объединяющего LLM, визуальные и аудиогенеративные компоненты.
- **База данных**: Необходима векторная база данных с поддержкой ECS. Рассматривается возможность реализации графовой базы данных для более эффективного хранения базы знаний. (Neo4j)
- **Содержимое базы данных**: В базе данных будут храниться правила игры (с учетом возможных юридических вопросов), записи ГМ и парсинги основных сайтов с релевантной информацией.
- **Используемые фреймворки**: В проекте планируется использование langchain, однако также рассматривается возможность ручной разработки, как настаивает Коммисаров.
- **Интерфейс**: Предполагается разработка веб-интерфейса с возможностью создания десктопного приложения. Открыты предложения по улучшению интерфейса.

## [Список задач](#список-задач)

| Название спринта | Задачи |
|------------------|--------|
| **Спринт 1: Настройка проекта и исследование** | - Определить объем и цели проекта <br> - Исследовать существующие LLM и их возможности <br> - Выявить ключевые функции и функциональности <br> - Настроить систему контроля версий (например, Git) <br> - Создать начальную документацию проекта |
| **Спринт 2: Проектирование архитектуры** | - Спроектировать архитектуру системы (компоненты и взаимодействия) <br> - Выбрать технологический стек (языки программирования, фреймворки) <br> - Набросать схему базы данных и решения для хранения данных <br> - Создать каркас для пользовательского интерфейса |
| **Спринт 3: Разработка основной функциональности** | - Реализовать базовую интеграцию LLM <br> - Разработать функциональность долгосрочной памяти <br> - Создать модуль генерации контента <br> - Настроить систему справки по правилам |
| **Спринт 4: Взаимодействие с пользователями и управление НПЦ** | - Разработать систему управления диалогами НПЦ <br> - Реализовать обработку пользовательского ввода и генерацию ответов <br> - Создать базовый пользовательский интерфейс для взаимодействия <br> - Протестировать поток взаимодействия с пользователем |
| **Спринт 5: Расширенные функции и интеграция** | - Интегрироваться с внешними API для дополнительного контента <br> - Реализовать функциональность поиска недостающей информации <br> - Разработать функции генерации визуального и аудиоконтента <br> - Протестировать интеграцию с виртуальными игровыми столами |
| **Спринт 6: Тестирование и доработка** | - Провести модульное тестирование всех модулей <br> - Собрать отзывы от потенциальных пользователей (гейммастеров) <br> - Доработать функции на основе отзывов пользователей <br> - Исправить ошибки и улучшить производительность |