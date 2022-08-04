# Foodgram - Продуктовый помощник

## Стек технологий

- Python
- Django
- Django REST Framework
- PostgreSQL
- Nginx
- Gunicorn
- Docker
- GitHubActions
- Yandex.Cloud

## Описание проекта

Foodgram это ресурс для публикации рецептов.  
Пользователи могут создавать свои рецепты, читать рецепты других пользователей, подписываться на интересных авторов, добавлять лучшие рецепты в избранное, а также создавать список покупок и загружать его в pdf формате

## Установка проекта локально

- Склонировать репозиторий на локальную машину:

```bash
git clone https://github.com/FrosTiK1989/foodgram-project-react.git
cd foodgram-project-react
```

- Cоздать и активировать виртуальное окружение:

```bash
python -m venv env
```

```bash
source env/bin/activate
```

- Cоздайте файл `.env` в директории `/infra/` с содержанием:

```
SECRET_KEY=секретный ключ django
DB_ENGINE=django.db.backends.postgresql
DB_NAME=postgres
POSTGRES_USER=postgres
POSTGRES_PASSWORD=postgres
DB_HOST=db
DB_PORT=5432
```

- Перейти в директирию и установить зависимости из файла requirements.txt:

```bash
cd backend/
pip install -r requirements.txt
```

- Выполните миграции:

```bash
python manage.py migrate
```

- Запустите сервер:

```bash
python manage.py runserver
```

## Запуск проекта в Docker контейнере

- Установите Docker.

Параметры запуска описаны в файлах `docker-compose.yml` и `nginx.conf` которые находятся в директории `infra/`

- Запустите docker compose:

```bash
docker-compose up -d --build
```  

  > После сборки появляются 3 контейнера:
  >
  > 1. контейнер базы данных **db**
  > 2. контейнер приложения **backend**
  > 3. контейнер web-сервера **nginx**
  >
- Примените миграции:

```bash
docker-compose exec backend python manage.py migrate
```

- Загрузите ингредиенты:

```bash
docker-compose exec backend python manage.py load_ingrs
```

- Загрузите теги:

```bash
docker-compose exec backend python manage.py load_tags
```

- Создайте администратора:

```bash
docker-compose exec backend python manage.py createsuperuser
```

- Соберите статику:

```bash
docker-compose exec backend python manage.py collectstatic --noinput
```

## Сайт

Сайт доступен по ссылке: <http://cookbook.hopto.org>

## Авторы

[Маресов Д.А.](https://github.com/FrosTiK1989) - Python разработчик (Backend)
[Яндекс.Практикум](https://github.com/yandex-praktikum) Frontend
