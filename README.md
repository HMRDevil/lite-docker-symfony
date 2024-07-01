## Образ докер для Symfony-приложений (Nginx, PHP 8.1, MySQL)

### Как использовать
```
Клонировать репозиторий
git clone  docker_project_name
Перейти в него и залить в папку app свое Symfony-приложение со всеми зависимостями
В .env файле Symfony-приложения настроить подключение к БД
DATABASE_URL="mysql://root:secret@mysql:3306/symfony?serverVersion=8.4.0&charset=utf8mb4"
Добавить в хост файл запись:
127.0.0.1       localhost
Запустить команду docker-compose up --build -d
Готово
```
Ваше приложение будет доступно по адресу https://localhost
