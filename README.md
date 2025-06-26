# Документация для аналога TikTok
## «UML-модель для аналога TikTok. Диаграмма классов описывает основные сущности системы: пользователей, видео, лайки, комментарии и активность.

# 1. Диаграммы
- Class Diagram
  ![UML диаграмма классов](./diagrams/tiktok-class-diagram.png)

# 2. SQL Queries - запросы для работы с БД
## CREATE TABLE
  <details>
    ```SQL
    -- Таблица пользователей
    CREATE TABLE User (
        user_id SERIAL PRIMARY KEY,
        user_name VARCHAR(100) NOT NULL,
        password_hash VARCHAR(255) NOT NULL,
        email VARCHAR(255) UNIQUE NOT NULL
    );

    -- Таблица видео
    CREATE TABLE Video (
        video_id SERIAL PRIMARY KEY,
        author_id INTEGER NOT NULL,
        video_title VARCHAR(200),
        video_file_link TEXT,
        FOREIGN KEY (author_id) REFERENCES User(user_id)
            ON DELETE CASCADE
    );

    -- Таблица подписок (связь многие-ко-многим между User и User)
    CREATE TABLE Follow (
        follower_id INTEGER NOT NULL,
        following_id INTEGER NOT NULL,
        PRIMARY KEY (follower_id, following_id),
        FOREIGN KEY (follower_id) REFERENCES User(user_id)
            ON DELETE CASCADE,
        FOREIGN KEY (following_id) REFERENCES User(user_id)
            ON DELETE CASCADE
    );

    -- Таблица лайков видео
    CREATE TABLE "Like" (
        like_id SERIAL PRIMARY KEY,
        user_id INTEGER NOT NULL,
        video_id INTEGER NOT NULL,
        FOREIGN KEY (user_id) REFERENCES User(user_id)
            ON DELETE CASCADE,
        FOREIGN KEY (video_id) REFERENCES Video(video_id)
            ON DELETE CASCADE
    );

    -- Таблица комментариев
    CREATE TABLE Comment (
        comment_id SERIAL PRIMARY KEY,
        user_id INTEGER NOT NULL,
        video_id INTEGER NOT NULL,
        comment_body TEXT,
        FOREIGN KEY (user_id) REFERENCES User(user_id)
            ON DELETE CASCADE,
        FOREIGN KEY (video_id) REFERENCES Video(video_id)
            ON DELETE CASCADE
    );

    -- Таблица истории активности пользователя (просмотры и т.п.)
    CREATE TABLE UserActivityLog (
        activity_id SERIAL PRIMARY KEY,
        user_id INTEGER NOT NULL,
        video_id INTEGER NOT NULL,
        abstract_video_data TEXT,
        FOREIGN KEY (user_id) REFERENCES User(user_id)
            ON DELETE CASCADE,
        FOREIGN KEY (video_id) REFERENCES Video(video_id)
            ON DELETE CASCADE
    );
    ```
  </details>
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
