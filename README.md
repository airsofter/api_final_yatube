# api_final
Описание:

API для проекта Yatube.
Позволяет отправлять GET, POST, PUT, PATCH, DEL запросы к БД.
У неаутентифицированных пользователей доступ к API только на чтение

Установка:

Cоздать и активировать виртуальное окружение:
python3 -m venv env
source env/bin/activate

Установить зависимости из файла requirements.txt:
python3 -m pip install --upgrade pip
pip install -r requirements.txt

Выполнить миграции:
python3 manage.py migrate

Запустить проект:
python3 manage.py runserver

Примеры:

Подрообную документацию можно почитать перейдя по ссылке http://127.0.0.1:8000/redoc/ после запуска проекта
