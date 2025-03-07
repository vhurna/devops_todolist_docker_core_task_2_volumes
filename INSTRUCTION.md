# Інструкції з запуску додатку TodoList за допомогою Docker

## Запуск контейнера MySQL з прикріпленим томом

1.  Перейдіть до директорії з файлом `Dockerfile.mysql`.

2.  Побудуйте образ MySQL:

    ```
    docker build -f Dockerfile.mysql -t <vhurna>/mysql-local:1.0.0 .
    ```

    Замініть `<vhurna>` на своє ім'я користувача Docker Hub.

3.  Запустіть контейнер MySQL з прикріпленим томом:

    ```
    docker run --name mysql-container -p 3306:3306 -v mysql_data:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=rootpassword -e MYSQL_DATABASE=app_db -e MYSQL_USER=app_user -e MYSQL_PASSWORD=1234 -d <vhurna>/mysql-local:1.0.0
    ```

    *   `mysql_data` - це ім'я тому, який буде використано для збереження даних MySQL.
    *   `-e` параметри передають змінні середовища, необхідні для ініціалізації бази даних.

## Запуск контейнера Django

1.  Перейдіть до директорії з файлом `Dockerfile` (для Django-додатку).

2.  Побудуйте образ Django:

    ```
    docker build -t <vhurna>/todoapp:2.0.0 .
    ```

    Замініть `<vhurna>` на своє ім'я користувача Docker Hub.

3.  Запустіть контейнер Django:

    ```
    docker run --name todoapp-container -p 8000:8000 -d <vhurna>/todoapp:2.0.0
    ```

    *   Переконайтеся, що Django налаштовано на підключення до бази даних MySQL за адресою `127.0.0.1:3306`.

## Доступ до додатку через браузер

Відкрийте браузер та перейдіть за адресою `http://localhost:8000`.

## Docker Hub

Посилання на репозиторій Docker Hub з образом додатку:

[https://hub.docker.com/r/\<vhurna\>/todoapp](https://hub.docker.com/r/<vhurna>/todoapp)

Замініть `<vhurna>` на своє ім'я користувача Docker Hub.

