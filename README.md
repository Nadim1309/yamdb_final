# Проект «API YAMDB»

### Описание
«API YAMDB» - Проект YaMDb собирает отзывы пользователей на произведения. 
Произведения делятся на категориии, такие как "Фильмы", "Музыка", "Книги". Сами произведения здесь не хранятся.

Произведениям можно присвоить жанр, например для произведения из категории "Музыка" может быть присвоен жанр "Рок".
Добавить произведения может только администратор. Пользователи могут оставлять к произведениям отзывы, 
ставить им оценку от 1 до 10, из оценок формируется рейтинг - среднее из всех оценок, оставленных произведению.

Добавить отзыв, комментарий или поставить оценку разрешается только аутентифицированным пользователям.
На одно произведение пользователь может оставить только один отзыв.


### Использумые технологии

[Python 3.7](https://docs.python.org/3.7/whatsnew/3.7.html)

[Django 2.2.16](https://docs.djangoproject.com/en/4.1/releases/2.2.16/)

[DjangoRestFramework 3.12.4](https://www.django-rest-framework.org/community/release-notes/)

[gunicorn 20.0.4](https://docs.gunicorn.org/en/stable/)

[Docker](https://docs.docker.com/)

### Как запустить проект:

Клонировать репозиторий и перейти в него в командной строке:

```
git clone git@github.com:Nadim1309/infra_sp2.git
```

```
cd infra_sp2/infra/
```

В директории infra создайте файл .env

```
touch .env
```

Наполните созданный файл по следующему шаблону:

```
DB_ENGINE=django.db.backends.postgresql # указываем, что работаем с postgresql
DB_NAME=postgres # имя базы данных
POSTGRES_USER=postgres # логин для подключения к базе данных
POSTGRES_PASSWORD=password # пароль для подключения к БД (установите свой)
DB_HOST=db # название сервиса (контейнера)
DB_PORT=5432 # порт для подключения к БД
```

Разверните и запустите проект:

```
docker-compose up -d --build
```

Выполните миграции:

```
docker-compose exec web python manage.py migrate
```

Создайте суперпользователя:

```
docker-compose exec web python manage.py createsuperuser
```


Соберите статику:

```
docker-compose exec web python manage.py collectstatic --no-input 
```

Проект будет доступен по адресу:

```
http://localhost/
```

## Примеры запросов к API
###  Регистрация пользователя
```
POST /api/v1/auth/signup/
{
  "email": "string",
  "username": "string"
}
```
###  Получение JWT-токена:
```
POST /api/v1/auth/token/
{
  "username": "string",
  "confirmation_code": "string"
}
```
###  Добавление категории:
```
POST /api/v1/categories/
{
  "name": "string",
  "slug": "string"
}
```
###  Удаление категории:
```
DELETE /api/v1/categories/{slug}/
```
###  Добавление произведения:
```
POST /api/v1/titles/
{
  "name": "string",
  "year": 0,
  "description": "string",
  "genre": [
    "string"
  ],
  "category": "string"
}
```

### Полная документация по эндпоинту /redoc/

Автор:

[Шакиржанов Надим](https://github.com/Nadim1309)

