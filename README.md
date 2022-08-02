# Запуск docker-compose

<div align="justify">

### Описание

Приложение состоит из нескольких сервисов, запущенных в связанных контейнерах:
- [Django-проекта](https://github.com/KseniyaGurevich/api_yamdb)
- базы данных Postgres
- сервера Gunicorn и nginx, отвечающие за раздачу статики

### Технологии проекта
- Python 3.7
- Django
- Django REST Framework
- SQLite3
- Simple-JWT
- gunicorn
- psycopg2-binary
- docker
- docker-compose

### Запуск проекта
- Клонировать репозиторий git clone git@github.com:KseniyaGurevich/infra_sp2.git
- Создайте файл .env (путь infra_sp2/infra/nginx) с переменными окружения для работы с базой данных :
```
DB_ENGINE=django.db.backends.<указываем, с какой БД работаем> 

DB_NAME=<Имя базы данных> 

POSTGRES_USER=<логин для подключения к базе данных>

POSTGRES_PASSWORD=<пароль для подключения к БД>

DB_HOST=<название сервиса (контейнера)>

DB_PORT=<порт для подключения к БД>
```
- Запустите контейнеры:
```
docker-compose up -d
```
- Выполните миграции:
```
docker-compose exec web python manage.py migrate
```
- Создайте суперюзера:
```
docker-compose exec web python manage.py createsuperuser
```
- Подгрузите статику:
```
docker-compose exec web python manage.py collectstatic --no-input
```
- Заполните базу данными:
```
python manage.py loaddata fixtures.json
```
- Теперь проект доступен по адресам:
<br> [http://localhost/](http://localhost/)
<br>[http://localhost/admin/]( http://localhost/admin) - админка
<br>[http://localhost/redoc/](http://localhost/redoc/) - документация проекта

</div>