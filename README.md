# test_vidau
 Тестовые задания для Vidau
Тестовое задание для QA auto:

Вариант 1: «Автоматизация тестирования сетевых настроек»

Задание 1.1 (Python)

Название: Проверка и изменение сетевых настроек через веб-интерфейс.

Описание задачи:
 1. Необходимо открыть страницу с настройками сети в веб-интерфейсе (например, http://10.20.30.17:4000/control/device).
 2. Проверить корректность отображения всех интерфейсов (например, сравнив данные, полученные на странице, с данными, которые возвращает API GET http://10.20.30.17:4001/api/network).
 3. Изменить настройки одного из интерфейсов (например, изменить customer_name) и сохранить их.
 4. Убедиться, что изменения успешно применились в UI и при повторном запросе к API.

Дополнительные требования/рекомендации:
 • Использовать один из фреймворков для тестирования на Python (pytest, unittest, Robot Framework и т. д.).
 • Реализовать структуру теста, учитывая подготовку окружения (setup) и уборку после тестов (teardown).
 • Организовать логи и вывод результатов теста (например, использовать logging или встроенные механизмы фреймворка).
 • В случае ошибок в тесте предусмотреть, как будет осуществляться отладка (например, делать скриншот UI, выводить полученные данные и т.д.).


Задание 1.2 (Postman)

Название: Тестирование изменения сетевых настроек через POST-запрос.

Описание задачи:
 1. С помощью Postman отправить GET-запрос на http://10.20.30.17:4001/api/network, чтобы получить текущие сетевые настройки.
 2. Выполнить POST-запрос на тот же эндпоинт для изменения любой настройки.
 3. Проверить, что Postman успешно получает в ответе статус 200 (или соответствующий код успешной операции) и изменённые значения.
 4. Снова сделать GET-запрос, чтобы убедиться, что настройки действительно изменились.

Окружение и данные для авторизации:
 • Swagger: http://10.20.30.17:4001/swaggerui#
 • Интерфейс: http://10.20.30.17:4000/control/device
 • Логин и пароль: admin/password1234
 • Токен: Bearer 6SEmhLzmRq7skGn0w8CncUA2YlG1pNPnFwTbLB3j+vgPpDTCeOnI5EUtofmqd1InWeA5Wb1g51uOv56ZrbhqQw==

Дополнительные требования/рекомендации:
 • Настроить в Postman тест-скрипты для проверки статуса ответа (например, pm.test(...)).
 • Реализовать проверку, что именно нужное поле было изменено.
 • По желанию, сохранить успешные запросы/ответы в отдельной коллекции Postman или выгрузить коллекцию в JSON.



Вариант 2: «Управление устройствами и Syslog-сервером»

Задание 2.1 (Python)

Название: Автоматизация добавления, редактирования и удаления устройств разных типов.

Описание задачи:
 1. Зайти во вкладку «Инвентарь» в системе мониторинга (например, http://<ваш-сервис>/inventory) или воспользоваться специальным GUI/сервисом.
 2. Последовательно добавить устройства различных типов:
 • Устройство RPCM
 • Класс устройства: «Устройство»
 • Тип драйвера: RPCM driver
 • Версия драйвера: 0.1.0
 • Агент: «Недоступен»
 • Устройство IGW
 • Класс устройства: «Устройство»
 • Тип драйвера: Vidau IGW driver
 • Версия драйвера: 0.0.0
 • Агент: «Недоступен»
 • Модульная корзина Profitt
 • Класс устройства: «Модульная корзина»
 • Тип драйвера: Profitt driver
 • Версия драйвера: «Недоступна»
 • Агент: «Произвольный выбор»
 3. После добавления выполнить действия по редактированию/удалению одного или нескольких устройств, чтобы убедиться, что эти операции работают корректно.
 4. Убедиться, что после выполнения каждой операции интерфейс (или API) возвращает ожидаемые результаты (например, проверять статус-коды, содержимое ответа, наличие устройства в списке и т.д.).

Дополнительные требования/рекомендации:
 • При реализации использовать Python-библиотеки (например, requests для REST API) или Selenium (если это именно веб-GUI).
 • Придумать собственные проверки для убедительности теста: корректность названий драйверов, ожидаемое состояние устройств, корректные статус-коды.
 • По завершении теста желательно очистить тестовые данные (удалить добавленные тестовые устройства), если это возможно.


Задание 2.2 (Postman)

Название: Добавление и обновление Syslog-сервера.
Описание задачи:
 1. Использовать Postman для добавления нового Syslog-сервера (определить или уточнить конечный эндпоинт у разработчиков или в документации).
 2. После успешного добавления сервера проверить:
 • Ответ сервера (код 200, структура JSON и т. д.).
 • Наличие нового Syslog-сервера в списке настроек (GET-запрос).
 3. Выполнить обновление (PUT или POST, в зависимости от реализации API) существующего Syslog-сервера, например, изменить порт или IP-адрес.
 4. Проверить, что изменения отразились в системе (сделать повторный GET-запрос, убедиться в корректных данных).

Дополнительные требования/рекомендации:
 • Протестировать варианты с некорректными данными (например, неправильный формат IP).
 • Использовать тест-скрипты Postman для валидации ответов (assert по статусам и содержимому тела ответа).
 • При необходимости можно использовать окружения и переменные Postman для хранения токена и базового URL.



Вариант 3: «Работа с интерфейсами и контурами»

Задание 3.1 (Postman)

Название: Создание нового интерфейса и проверка валидации полей.

Описание задачи:
 1. С помощью Postman выполнить запрос на создание нового интерфейса (например, POST /api/network/ip_route/create).
 2. Предусмотреть проверку валидации обязательных полей (например, имя интерфейса, IP-адрес).
 3. Попробовать создать интерфейс с некорректными данными (пусть одна из валидаций не проходит) и проверить, что сервер вернёт ожидаемую ошибку (4xx).
 4. Вывести результат запросов (успешных и неуспешных) в консоль Postman или сохранить их в отдельном JSON-файле.

Дополнительные требования/рекомендации:
 • При проверке используйте pm.test() для валидации статус-кодов и содержимого ответа.
 • Заранее продумайте «позитивные» и «негативные» сценарии.
 • Если система позволяет, сделать GET-запрос для проверки, что созданный интерфейс добавился в общий список.


Задание 3.2 (Python)

Название: Создание контура, устройств, пользователей и проверка их состояния.

Описание задачи:
 1. Создать новый «контур» (логическую группу/сегмент) в тестируемой системе (используя REST API или UI, в зависимости от возможностей).
 2. Создать несколько устройств и пользователей, каждый с уникальными идентификаторами и привязать их к созданному контуру.
 3. После этого запросить список устройств и пользователей, чтобы убедиться, что все созданные сущности добавлены корректно и их статусы соответствуют ожиданиям (например, «Активен», «В сети», «Неактивен» и т.д.).
 4. По окончании теста вывести список устройств и пользователей и их актуальные состояния в консоль или лог.


Дополнительные требования/рекомендации:
 • Можно использовать Python (requests, Selenium, PyTest) или другой удобный инструмент.
 • Спроектируйте структуру теста с учётом возможности повторного запуска (например, чтобы в случае повторного создания контур с тем же именем не конфликтовал).
 • При необходимости реализовать очистку тестовых данных.
