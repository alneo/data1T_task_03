# Итоговая аттестация Задание 3.
![GitHub top language](https://img.shields.io/github/languages/top/alneo/data1T_task_02)
![GitHub issues](https://img.shields.io/github/issues/alneo/data1T_task_02)

## Создание Docker-контейнера с ClickHouse и SQL

## Цель:
Научиться разворачивать ClickHouse в Docker, создавать базы данных и настраивать роли с разными правами доступа с помощью SQL-запросов через DBeaver.

## Описание задания:

- Создайте директорию для проекта и необходимые файлы.
- В файле docker-compose.yml опишите конфигурацию для запуска контейнера с ClickHouse.
- Если у вас еще не установлен DBeaver, скачайте и установите его.
- В DBeaver, используя SQL-редактор, выполните SQL-запрос для создания базы данных test.
- Аналогично создайте базу данных main.
- В базе данных main создайте роль с правами на чтение.
- Создайте роль с правами на запись в БД main.
- Для проверки создайте пользователя, назначьте ему одну из созданных ролей и сделайте простой запрос к БД, подтверждающий, что роль работает корректно. Сделайте скриншот.

## Результат задания
После выполнения задания у вас будет:
- Развернутый в Docker ClickHouse, 
- Две базы данных (test и main) 
- Настроенные роли для управления доступом к базе данных main. 
- Вы можете подключаться к ClickHouse через DBeaver и выполнять SQL-запросы для настройки прав доступа.

## Выполнение
- Создание docker-compose.yml файла и открытие порта
- Исправление конфига users.xml для возможности создания пользователей
![Logotype](./screenshots/step_01.png)
- Подключение к ClickHouse через DBeaver
![Logotype](./screenshots/step_02.png)
- В DBeaver, используя SQL-редактор, выполните SQL-запрос для создания базы данных test.
```CREATE DATABASE IF NOT EXISTS test COMMENT 'Database TEST for data1t_task_03';```
![Logotype](./screenshots/step_03.png)
- Аналогично создайте базу данных main.
```CREATE DATABASE IF NOT EXISTS main COMMENT 'Database TEST for data1t_task_03';```
![Logotype](./screenshots/step_04.png)
- В базе данных main создайте роль с правами на чтение.
```CREATE ROLE r_read; GRANT SELECT ON main.* TO r_read; GRANT SHOW ON main.* TO r_read;```
![Logotype](./screenshots/step_05.png)
- В базе данных main создайте роль с правами на запись.
```CREATE ROLE r_write; GRANT INSERT ON main.* TO r_write;```
![Logotype](./screenshots/step_06.png)
- Для проверки создайте пользователя, назначьте ему одну из созданных ролей и сделайте простой запрос к БД, подтверждающий, что роль работает корректно. Сделайте скриншот.
```CREATE USER user_read IDENTIFIED WITH PLAINTEXT_PASSWORD BY 'pass1'; GRANT r_read TO user_read;```
![Logotype](./screenshots/step_07.png)
- Для проверки создадим соединение user_write и сделаем запросы
![Logotype](./screenshots/step_08.png)
- Запрос на вставку данных для пользователя user_write
![Logotype](./screenshots/step_09.png)
- Запрос на выборку данных для пользователя user_write
![Logotype](./screenshots/step_10.png)
- Для проверки создадим соединение user_read и сделаем запросы
![Logotype](./screenshots/step_11.png)
- Запрос на вставку данных для пользователя user_read
![Logotype](./screenshots/step_12.png)
- Запрос на выборку данных для пользователя user_read
![Logotype](./screenshots/step_13.png)
