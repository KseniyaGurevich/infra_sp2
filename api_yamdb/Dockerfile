FROM python:3.7-slim

#запустить команду создания директории внутри контейнера
RUN mkdir /app

#сделать директорию /app/api_yamdb рабочей
WORKDIR /app/api_yamdb

#скопировать с локального компьютера файл зависимостей requirements.txt
#в директорию /app
COPY api_yamdb/requirements.txt /app

#выполнить установкеу зависимостей внутри контейнера
RUN pip3 install -r /app/requirements.txt --no-cache-dir

#скопировать содержимое директороии /api_yamdb с локального компьютера
#в директорию app
COPY ../ /app

#выполнить запуск сервера разработки при старте контейнера
CMD ["gunicorn", "api_yamdb.wsgi:application", "--bind", "0:8000" ]