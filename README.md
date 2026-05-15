# API тесты для бук-клуба

Автотесты для проверки API книжного клуба.

## Что проверяют тесты

**test_clubs_list.py**
- статус ответа 200
- валидация JSON-схемы
- наличие полей count и results
- правильные типы данных

**test_club_detail.py**
- получение клуба по ID (1,2,3,4,5)
- статус 200 для существующих клубов
- валидация JSON-схемы
- проверка ID в ответе
- ошибка 404 для несуществующего клуба (ID 999999)

**test_clubs_pagination.py**
- ссылка на следующую страницу
- лимит 5 элементов на странице
- проверка страниц 1,2,3
- ссылка на предыдущую страницу

**test_clubs_search.py**
- поиск "Сети" -> результат есть
- поиск "Тестирование" -> результат есть
- поиск "Python" -> результат пустой
- поиск в разном регистре (сети/СЕТИ)

## Техническая структура

**conftest.py** - фикстуры
- base_url - адрес API из .env
- api_session - общая сессия для запросов

**schemas/club_schema.py** - JSON схемы
- CLUB_LIST_SCHEMA - для списка клубов
- CLUB_DETAIL_SCHEMA - для одного клуба

**pytest.ini** - настройки
- маркеры: smoke, regression, schema
- пути к тестам

**.env** - переменные окружения
- API_BASE_URL - базовый адрес
- TIMEOUT - таймаут запросов

## Запуск тестов

Установка зависимостей:
pip install -r requirements.txt

Запуск всех тестов:
pytest -v

Запуск с маркерами:
pytest -m smoke -v
pytest -m regression -v
pytest -m schema -v

Запуск конкретного файла:
pytest tests/test_clubs_list.py -v

Запуск одного теста:
pytest tests/test_clubs_list.py::test_get_clubs_list_status_code -v

## Результаты

Всего тестов: 23
Пройдено: 23
Упало: 0

## Используемые библиотеки

pytest - фреймворк для тестов
requests - HTTP запросы
jsonschema - валидация JSON
python-dotenv - переменные окружения

## Требования

Python 3.12 или выше
Windows / Linux / macOS

## Контакты

Автор: 1DimonNT
Репозиторий: https://github.com/1DimonNT/19_REST_API_part_II