# api_final
Описание:

Yatube - это социальная сеть для блоггеров. Здесь можно писать свои посты, оставлять комментарии и подписываться на других авторов.
API позволяет отправлять GET, POST, PUT, PATCH, DEL запросы к БД.
У неаутентифицированных пользователей доступ к API только на чтение

Установка:

Проект работает на python 3.9

Для установки python на Windows сделайте следующее:

Перейдите по ссылке https://www.python.org/, далее в раздел downloads и выберите версию 3.9.10.
Запустите скачанный файл, в окне установки поставьте галочку возле пункта Add Python 3.9 to PATH и нажмите Install now.
При установке интерпретатора будет установлен пакетный менеджер pip, он нужен для установки модулей и библиотек для Python. 
Для проверки, что интерпретатор Python установлен и готов к работе, откройте приложение «Командная строка»: «Пуск» → «Все приложения» → «Служебные» — Windows → «Командная строка».
Выполните команду python --version для проверки версии интерпретатора.
Также для windows необходимо установить приложение Git Bash. Скачайте его по ссылке https://gitforwindows.org/

Для установки на Linux:

Проверьте версию предустановленного интерпретатора, открыв терминал сочетанием клавиш Alt+Ctrl+T. Используйте команду python3 --version.
Если текущая версия 3.9, у вас всё готово к работе. Если нет, нужно её установить. 
Введите в терминал команду:
sudo apt update && sudo apt upgrade
Далее можно запускать установку нужной версии Python и пакетов для неё. Выполните последовательно команды:
sudo apt install python3.9 -y
sudo apt install python3.9-venv
Убедитесь, что установка версии 3.9 прошла успешно. Выполните команду:
python3.9 --version 

Далее необходимо создать SSH ключи для GitHub для дальнейшей работы с ним, либо скачать просто ZIP архив и распаковать его на компьютере.
Запустите терминал или Git Bush, выполните команду:
ssh-keygen
Сохраните ключи в папку по умолчанию: для этого нажмите Enter
При создании ключей система попросит придумать пароль для доступа к ключам. Когда вы будете задавать пароль, в терминале ничего не отобразится, даже звёздочки:
Enter passphrase (empty for no passphrase):
Теперь необходимо сохранить открытый ключ в вашем аккаунте на GitHub. 
Выведите ключ в терминал командой:
cat .ssh/id_rsa.pub  
Скопируйте ключ от символов ssh-rsa , включительно, и до конца
Зайдите в свой аккаунт на GitHub, перейдите в раздел настроек
Выберите пункт SSH and GPG keys; для создания нового ключа нажмите на кнопку New SSH key в правом верхнему углу
В поле Key втавьте ключ
Нажмите кнопку Add SSH key

Клонировать репозитеорий к себе на компьютер при работе с Git:
скопируйте ссылку на репозиторий, нажав Code, local, SSH
Откройте терминал или git bush
Введите команду git clone <скопированная ссылка>
Перейдите в директорию с проектом с помощью команды 
cd api_final_yatube


Cоздать и активировать виртуальное окружение:

На linux:
python3 -m venv env
source env/bin/activate

На windows:
python -m venv venv
source venv/Scripts/activate

Установить зависимости из файла requirements.txt:

На linux:
python3 -m pip install --upgrade pip
pip install -r requirements.txt

На windows:
python -m pip install --upgrade pip
pip install -r requirements.txt

Выполнить миграции:

На linux:
python3 manage.py migrate

На windows:
python manage.py migrate

Запустить проект:

На linux:
python3 manage.py runserver

На windows:
python manage.py runserver

Примеры запросов к API:

Загрузка изображений осуществляется с помощью кодирования base64 в виде строки байтов

Получение списка всех постов осуществляется следующим GET запросом:
http://127.0.0.1:8000/api/v1/posts/

RESPONSE:
{
    "count": 123,
    "next": "http://api.example.org/accounts/?offset=400&limit=100",
    "previous": "http://api.example.org/accounts/?offset=200&limit=100",
    "results": [
    {...}
    ]
}

Получение конкретного поста осуществляется следующим GET запросом:
http://127.0.0.1:8000/api/v1/posts/{id}/

RESPONSE:
{
    "id": 0,
    "author": "string",
    "text": "string",
    "pub_date": "2019-08-24T14:15:22Z",
    "image": "string",
    "group": 0
}

Получение списка сообществ - GET запрос на эндпоинт:
http://127.0.0.1:8000/api/v1/groups/

RESPONSE:
[
    {
        "id": 0,
        "title": "string",
        "slug": "string",
        "description": "string"
    }
]

Получение информации о конкретном сообществе - GET запрос на эндпоинт:
http://127.0.0.1:8000/api/v1/groups/{id}/

RESPONSE:
{
    "id": 0,
    "title": "string",
    "slug": "string",
    "description": "string"
}

Получение информации о всех подписках пользователя - GET запрос на эндпоинт:
http://127.0.0.1:8000/api/v1/follow/

RESPONSE:
[
    {
        "user": "string",
        "following": "string"
    }
]

Получение информации о всех комментариях к посту - GET запрос на эндпоинт:
http://127.0.0.1:8000/api/v1/posts/{post_id}/comments/

RESPONSE:
[
    {
        "id": 0,
        "author": "string",
        "text": "string",
        "created": "2019-08-24T14:15:22Z",
        "post": 0
    }
]

Получение информации о конкретном комментарии к посту - GET запрос на эндпоинт:
http://127.0.0.1:8000/api/v1/posts/{post_id}/comments/{id}/

RESPONSE:
{
    "id": 0,
    "author": "string",
    "text": "string",
    "created": "2019-08-24T14:15:22Z",
    "post": 0
}

Создание нового поста осуществляется следующим POST запросом на эндпоинт:
http://127.0.0.1:8000/api/v1/posts/
Body:
{
    "text": "string",
    "image": "string",
    "group": 0
}

RESPONSE:
{
    "id": 0,
    "author": "string",
    "text": "string",
    "pub_date": "2019-08-24T14:15:22Z",
    "image": "string",
    "group": 0
}

Создание нового комментария к посту осуществляется следующим POST запросом на эндпоинт:
http://127.0.0.1:8000/api/v1/posts/{post_id}/comments/
Body:
{
    "text": "string"
}

RESPONSE:
{
    "id": 0,
    "author": "string",
    "text": "string",
    "created": "2019-08-24T14:15:22Z",
    "post": 0
}

Создание новой подписки - POST запрос на эндпоинт:
http://127.0.0.1:8000/api/v1/follow/
Body:
{
    "following": "string"
}

RESPONSE:
{
    "user": "string",
    "following": "string"
}


Обновление данных поста осуществляется PUT запросом на эндпоинт:
http://127.0.0.1:8000/api/v1/posts/{id}/
Body:
{
    "text": "string",
    "image": "string",
    "group": 0
}

RESPONSE:
{
    "id": 0,
    "author": "string",
    "text": "string",
    "pub_date": "2019-08-24T14:15:22Z",
    "image": "string",
    "group": 0
}

Обновление данных комментария осуществляется PUT запросом на эндпоинт:
http://127.0.0.1:8000/api/v1/posts/{post_id}/comments/{id}/
Body:
{
    "text": "string"
}

RESPONSE:
{
    "id": 0,
    "author": "string",
    "text": "string",
    "created": "2019-08-24T14:15:22Z",
    "post": 0
}


Частичное обновление поста осуществляется PATCH запросом на эндпоинт:
http://127.0.0.1:8000/api/v1/posts/{id}/
Body:
{
    "text": "string",
    "image": "string",
    "group": 0
}

RESPONSE:
{
    "id": 0,
    "author": "string",
    "text": "string",
    "pub_date": "2019-08-24T14:15:22Z",
    "image": "string",
    "group": 0
}

Частичное обновление комментария - PATCH запрос на эндпоинт:
http://127.0.0.1:8000/api/v1/posts/{post_id}/comments/{id}/
Body:
{
    "text": "string"
}

RESPONSE:
{
    "id": 0,
    "author": "string",
    "text": "string",
    "created": "2019-08-24T14:15:22Z",
    "post": 0
}

Удаление поста его автором - DELETE запрос на эндпоинт:
http://127.0.0.1:8000/api/v1/posts/{id}/

Удаление комментария его автором - DELETE запрос на эндпоинт:
http://127.0.0.1:8000/api/v1/posts/{post_id}/comments/{id}/

Получение токена для пользователя осуществляется POST запросом на эндпоинт:
http://127.0.0.1:8000/api/v1/jwt/create/
Body:
{
    "username": "string",
    "password": "string"
}

RESPONSE:
{
    "refresh": "string",
    "access": "string"
}

Обновление имеющегося токена осуществляется POST запросом на эндпоинт:
http://127.0.0.1:8000/api/v1/jwt/refresh/
Body:
{
    "refresh": "string"
}

RESPONSE:
{
    "refresh": "string"
}

Проверка токена осуществляется POST запросом на эндпоинт:
http://127.0.0.1:8000/api/v1/jwt/verify/
Body:
{
    "token": "string"
}
В случае отсутсвии такого токена в ответе будет выведена ошибка валидности токена



Подрообную документацию можно почитать перейдя по ссылке http://127.0.0.1:8000/redoc/ после запуска проекта
