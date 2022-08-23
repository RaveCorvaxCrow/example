# ATF-WEB CRYPTODRAGONS

ATF-WEB CRYPTODRAGONS is framework for automated testing CRYPTODRAGONS web project.

- src/api/api.py - имплементация backend функций, необходимых для прекондишенов (на данный момент таких нет, пример из новатаров) 

- src/common/driver_actions.py - функции, расширяющие функционал драйвера, относящиеся к странице

- src/common/elements/page_element.py - функции, расширяющие функционал драйвера, относящиеся к конкретному web-элементу на странице

- src/common/elements/*.py - функции, расширяющие функционал драйвера, относящиеся к конкретному типу web-элемента 

- src/shared/ - [в разработке: будет реализация импорта vrt]

- src/domain/user.py - модели объектов (например User)

- src/pages - файлы с page objects

- src/exception.py - кастомные исключения

- src/utils.py - вспомогательные функции

- tests/test_*.py - файлы с тестами

- tests/conftest.py - файл с фикстурами и конфигурацией запуска драйвера 

Для запуска тестов необходимо передать параметры:

- browser: Type in browser name e.g. chrome
- apiUrl: URL where backend is running
- project: Project name or ID
- apiKey: User apiKey
- ciBuildId: Current git commit SHA
- branchName: Current git branch
- enableSoftAssert: Log errors instead of exceptions

Процесс тестирования

1. Тестируем в браузере Chrome в полноэкранном режиме

2. apiUrl, project, apiKey - сформированные по умолчанию при поднятии сервиса vrt

3. ciBuildId - это коммит с результатами каждого запуска тестирования. Необязательно должен меняться на каждый запуск, ciBuildId относится к тетсированию "билда", то есть для каждого нового процесса тестирования (с точки зрения функционала) должен быть новый коммит. Для нового коммита сначала проводится тестовый запуск для установки оригиналов. Также для каждой ветки могут быть свои коммиты. Коммит меняется после релиза. 

4. branchName - зависит от того, на каком окружении проходит тестирование (то есть напрямую зависит от тестируемой задачи). Если тестирование проводится на dev окружении, то branchName - develop, если регресс перед релизом - то staging.

На данный момент тестирование проводится локально на ПК тестировщика.