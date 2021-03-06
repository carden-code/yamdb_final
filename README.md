![example workflow](https://github.com/carden-code/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)

# Проект "Yamdb"

- Учебный проект для командной разработке API для веб приложения YaMDb, базируемых на фреймворке Django и модуле Django Rest Framework. Для обеспечения контороля прав доступа в проекте используется модуль JWT-токен.

## Описание проекта:

- Проект **YaMDb** собирает **отзывы** (**Review**) пользователей на **произведения** (**Titles**). Произведения делятся на категории: «Книги», «Фильмы», «Музыка». Список **категорий** (**Category**) может быть расширен администратором (например, можно добавить категорию «Изобразительное искусство» или «Ювелирка»).

- Сами произведения в **YaMDb** не хранятся, здесь нельзя посмотреть фильм или послушать музыку.
- В каждой категории есть **произведения**: книги, фильмы или музыка. Например, в категории «Книги» могут быть произведения «Винни-Пух и все-все-все» и «Марсианские хроники», а в категории «Музыка» — песня «Давеча» группы «Насекомые» и вторая сюита Баха.

- Произведению может быть присвоен **жанр** (**Genre**) из списка предустановленных (например, «Сказка», «Рок» или «Артхаус»). Новые жанры может создавать только администратор.

- Благодарные или возмущённые пользователи оставляют к произведениям текстовые **отзывы** (**Review**) и ставят произведению оценку в диапазоне от одного до десяти (целое число); из пользовательских оценок формируется усреднённая оценка произведения — **рейтинг** (целое число). На одно произведение пользователь может оставить только один отзыв.

## Установка и запуск проекта:

- Клонировать репозиторий и перейти в него в командной строке (испольщуем ssh):

`git clone git@github.com:carden-code/api_yamdb.git
`

- Переменные окружения:

`cd infra
`

```echo "SECRET_KEY=YourSecretKey 
   DB_ENGINE=django.db.backends.postgresql 
   DB_NAME=postgres 
   POSTGRES_USER=postgres 
   POSTGRES_PASSWORD=postgres 
   DB_HOST=db DB_PORT=5432" > .env
```

- Пример заполнения файла .env:

```DB_ENGINE=django.db.backends.postgresql # указываем, что работаем c postgresql

   DB_NAME=postgres # имя базы данных

   POSTGRES_USER=postgres # логин для подключения к базе данных

   POSTGRES_PASSWORD=postgres # пароль для подключения к БД (установите свой)

   DB_HOST=db # название сервиса (контейнера)

   DB_PORT=5432 # порт для подключения к БД

   SECRET_KEY=ваш секретный ключ
```

- Cборка docker-compose:

`cd infra
`

`sudo docker-compose up -d
`

- Выполните миграции:

`sudo docker-compose exec web python manage.py migrate
`

- Выполните команду collectstatic:

`sudo docker-compose exec web python manage.py collectstatic --no-input
`

- Заполните базу тестовыми данными:

`sudo docker-compose exec web python manage.py load_info
`

- Создайте суперпользователя:

`sudo docker-compose exec web python manage.py createsuperuser
`

- Получаем ключ авторизации для получения токена:

`sudo docker-compose exec web bash
`

`cd send_emails
`

`cat "файл с почтой"
`

### Примеры использования API:

- Дитальное описание и примеры работы API проекта представлены в документации: http://51.250.108.144/redoc/ в формате ReDoc. 

##### Используется:

- Python >= 3.7
- django==2.2.16
- djangorestframework==3.12.4
- djangorestframework-simplejwt==5.1.0
- django-filter==21.1
- PyJWT==2.1.0
- python-dotenv==0.20.0

### Участники:

#### [Борисенко Вячеслав](https://github.com/carden-code "Борисенко Вячеслав")

### Лицензия:
- Этот проект лицензируется в соответствии с лицензией MIT 

![](https://miro.medium.com/max/156/1*A0rVKDO9tEFamc-Gqt7oEA.png "1")

