### Отчет по 9 лабораторной работе

#### Выбор базы данных

Для выполнения лабораторной работы была выбрана база данных MySQL (MariaDB), так как она подходит для проектов среднего и крупного масштаба, где необходима поддержка высокой производительности и масштабируемости.

#### Создание базы данных

Была создана база данных `Blog`.

```mysql
CREATE DATABASE IF NOT EXISTS Blog
```

#### Структура таблицы `Users`

| Поле | Тип | Описание |
| --- | --- | --- |
| id | INT | Первичный ключ |
| name | VARCHAR | Имя пользователя |
| surname | VARCHAR | Фамилия пользователя |
| email | VARCHAR | Уникальный ключ |

```mysql
CREATE TABLE IF NOT EXISTS User
(
    id      INT AUTO_INCREMENT PRIMARY KEY,
    name    VARCHAR(255) NOT NULL,
    surname VARCHAR(255) NOT NULL,
    email   VARCHAR(255) NOT NULL UNIQUE
);
```

#### Структура таблицы `Comments`

| Поле | Тип | Описание |
| --- | --- | --- |
| id | INT | Первичный ключ |
| user_id | INT | Внешний ключ на таблицу `users` |
| comment | TEXT | Текст комментария |

```mysql
CREATE TABLE IF NOT EXISTS Comments
(
    id INT AUTO_INCREMENT PRIMARY KEY,
    user_id INT NOT NULL,
    comment TEXT NOT NULL,
    FOREIGN KEY (user_id) REFERENCES User(id)
);
```

#### Экспорт базы данных

База данных была экспортирована в файл `blog.sql` и сохранена в директории `/data`.

#### Структура директории `/data`

-   blog.sql

#### Примечание

Данная структура базы данных предполагает хранение информации о пользователях блога и их комментариях. Таблица `users` содержит информацию о пользователях, включая их имена, фамилии и уникальные email адреса. Таблица `comments` содержит комментарии пользователей к различным публикациям на блоге, ссылаясь на соответствующих пользователей из таблицы `users` с помощью внешнего ключа `user_id`.