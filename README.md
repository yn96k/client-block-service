В базе данных предлагается хранить одну таблицу - лог блокировок/разблокировок.
---
1. Таблица client
   
|Имя атрибута|Тип данных|Описание|
|:----|:----|:----|
|client_id|CHAR(36) PK|UUID клиента|
|client_name|VARCHAR(30) NOT NULL|Название юридического лица|
|ogrn|DECIMAL(13) NOT NULL|ОГРН организации|
|is_blocked|BOOLEAN NOT NULL|Статус блокировки клиента|

2. Таблица block_type
   
|Имя атрибута|Тип данных|Описание|
|:----|:----|:----|
|block_type_id|INT PK AUTO_INCREMENT|ID причины блокировки|
|block_type_name|VARCHAR(30) NOT NULL|Название причины блокировки|


3. Таблица block
   
|Имя атрибута|Тип данных|Описание|
|:----|:----|:----|
|block_id|INT PK AUTO_INCREMENT|ID блокировки|
|client_id|CHAR(36) FK client(client_id)|UUID клиента|
|block_type_id|INT FK block_type(block_type_id)|ID причины блокировки|
|blocked_at|TIMESTAMP|Дата и время блокировки|




1. client - информация о клиенте, признаки, статус блокировки
2. block_types - словарь причин блокировок с описанием и кодом причины
3. block_history - список блокировок (Id блокировки, client_id FK, причина блокировки FK, дата блокировки, комментарий модератора)

Индексы расписать и почему именно такие - client_id


Расписать эндпоинты - что они делают по пунктам в README.md

