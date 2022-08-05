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

## Описание

«Продуктовый помощник»: это ресурс, на котором пользователи публикуют рецепты, добавляют чужие рецепты в избранное и подписываются на публикации других авторов. Сервис «Список покупок» позволит пользователям создавать список продуктов, которые нужно купить для приготовления выбранных блюд, а так же список покупок можно выгрузить в удобном PDF файле, который можно взять собой в магазин

## Установка локально

- Склонировать репозиторий к себе на компьютер:

```bash
git@github.com:FrosTiK1989/foodgram-project-react.git
cd foodgram-project-react
```

- Cоздать и активировать виртуальное окружение:

```bash
python -m venv venv
```

```bash
. venv/bin/activate
```

- Cоздайте файл `.env` в директории `/infra/` с содержанием:

```bash
cd infra/
touch .env
```

```
SECRET_KEY=<тут ваш секртеный ключ от Django>
DB_ENGINE=django.db.backends.postgresql
DB_NAME=postgres
POSTGRES_USER=postgres
POSTGRES_PASSWORD=postgres
DB_HOST=db
DB_PORT=5432
```

- Установите зависимости из файла requirements.txt:

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
- Выполните миграции:

```bash
docker-compose exec backend python manage.py migrate
```

- Запустите процесс загрузки ингредиентов:

```bash
docker-compose exec backend python manage.py load_ingrs
```

- Запустите процесс загрузки тегов:

```bash
docker-compose exec backend python manage.py load_tags
```

- Создайте суперпользователя:

```bash
docker-compose exec backend python manage.py createsuperuser
```

- Заупстите процесс сбора статики:

```bash
docker-compose exec backend python manage.py collectstatic --no-input
```

## Сайт

Сайт доступен по ссылке: <http://cookbook.hopto.org>

## Авторы

Маресов Д.А. - Python разработчик (Backend)

 > Email: frostik1989@yandex.ru
 
 > Telegram: @frostik1989

[Яндекс.Практикум](https://github.com/yandex-praktikum) Помогали и предоставили Frontend к сайту

 > Site: practicum.yandex.ru
