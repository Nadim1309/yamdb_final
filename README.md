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

Для проекта настроен:  - автоматический запуск тестов на сервисе GitHub Actions.
                       - обновление образов на DockerHub
                       - автоматический деплой на боевой сервер при пуше в главную ветку main.

Запущенный проект доступен по адресу
http://158.160.6.133/
```

Статус выполнения workflow

![example workflow](https://github.com/nadim1309/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)

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

