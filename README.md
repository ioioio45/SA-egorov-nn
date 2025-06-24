# 1. Диаграммы
- UML ./diagrams/uml-example.png
- BPMN ./diagrams/bpmn-example.png
# 2. SQL Queries
## CREATE TABLE
  ```SQL
  CREATE TABLE table_name (
    Column1 datatype,
    Column2 datatype,
    Column3 datatype,
    ...
  )
  ```
  - Пример
  ```SQL
  CREATE TABLE users (
    id INT IDENTITY(1,1) PRIMARY KEY, /* Ключевое поле с автоинкрементом (1,2,3...) */
    name VARCHAR(255) NOT NULL,
    money MONEY,
    address VARCHAR(255) NOT NULL
  );
  ```
## ALTER TABLE
  ```SQL
  ALTER TABLE table_name
  { ADD column_name datatype | DROP COLUMN column_name | ALTER COLUMN column_name datatype };
  ```

  - Примеры
  ```SQL
  ALTER TABLE users
  ADD phone VARCHAR(10);
  ```

  ```SQL
  ALTER TABLE users
  DROP COLUMN address;
  ```

  ```SQL
  ALTER TABLE users
  ALTER COLUMN money INT NOT NULL;
  ```
## DROP TABLE
  ```SQL
  DROP TABLE users;
  ```
## TRUNCATE TABLE
   ```SQL
  TRUNCATE TABLE users;
  ```
## Примеры решения задач
  - './SQL/sql-examples.sql'
# 3. Документация
./
