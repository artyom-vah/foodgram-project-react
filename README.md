
![example workflow](https://github.com/artyom-vah/foodgram-project-react/actions/workflows/main.yml/badge.svg) [![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](https://opensource.org/licenses/MIT)


# Продуктовый помощник (Foodgram)

### Опиание проекта:  Foodgram - Продуктовый помощник
Добро пожаловать в Foodgram - онлайн-сервис и API, который станет вашим незаменимым помощником в кулинарных приключениях!
**Откройте новые гастрономические горизонты:** Делитесь своими уникальными рецептами, вдохновляйтесь блюдами других пользователей и делитесь своими кулинарными идеями.
**Общение и вдохновение:** Подписывайтесь на публикации других пользователей, находите новые интересные рецепты и оставляйте комментарии.
Избранное - соберите свою коллекцию: Добавляйте понравившиеся рецепты в личный список для быстрого доступа.
**Удобный список покупок:** Создайте сводный список продуктов для выбранных блюд перед походом в магазин.
Foodgram поможет вам наслаждаться гастрономическим творчеством, находить вдохновение и организовывать ваши покупки. Присоединяйтесь к нашему сообществу и начинайте свои кулинарные приключения уже сегодня!

****Foodgram - проект позволяет:****
- Просматривать рецепты
- Добавлять рецепты в избранное
- Добавлять рецепты в список покупок
- Создавать, удалять и редактировать собственные рецепты
- Скачивать список покупок

## Проект доступен по ссылкам (для ревьюера):
```
http://158.160.57.66/admin - Админка (обращаю внимание что надо вводить почту и пароль чтобы войти в админку)
http://158.160.57.66/api/ - api для данного сервиса
http://158.160.57.66/signup - Создать аккаунт
http://158.160.57.66/signin - Вход/Выход
http://158.160.57.66/recipes - рецепты
http://158.160.57.66/subscriptions - подписки
http://158.160.57.66/recipes/create - создать рецепт
http://158.160.57.66/favorites - Избранное
http://158.160.57.66/cart - Список покупок
http://158.160.57.66/change-password - Изменить пароль

* - примечание: данные ссылки будут работать 2-3 дня после пуша на мой github, 
далее виртуалка на яндекс облаке будет удалена и ссылки станут недоступны
```

## Для проверки работы сайта были добавлены админ и 3 пользователя:
#### ***Админ:***
````
почта: adm@mail.ru
пароль: adm
````
#### ***Пользователи:***
```
почта: test1@mail.ru
пароль: testtest77
```
```
почта: test2@mail.ru
пароль: testtest77
```
```
почта: test3@mail.ru
пароль: testtest77
```

### **Стек:**
![python version](https://img.shields.io/badge/Python-3.10-green) ![django version](https://img.shields.io/badge/Django-4.2.1-green) ![django version](https://img.shields.io/badge/djangorestframework-3.14.0-green)


## Инструкции по установке: 
#### ***1й этап - Установка на локальную машину (на ваш ПК)***

1. Клонируйте репозиторий и перейдите в него в командной строке:
```bash
git clone https://github.com/artyom-vah/foodgram-project-react
```
2. Переходим в папку backend/:
```bash
cd backend/
```
3. В папке backend/ создаем вируальное акружение venv:
```bash
python -m venv venv
source venv/Scripts/activate
```
или сразу так:
```bash
python -m venv venv && . venv/Scripts/activate
```
4. Обновляем менеджер пакетов pip:
```bash
python -m pip install --upgrade pip
```
5. Установите зависимости из файла requirements.txt:
```bash
pip install -r requirements.txt
# * - примечание: в случае если что-то не установится или будет какая-то ошибка, 
# то устанавливайте по одному пакету из файла requirements.txt (у меня лично таких ошибок не было)
```
6. В случае если в infra/ нет файла.env, то создаем его в папке infra/:
```bash
cd ..
cd infra/
touch .env
```
7. В нем прописываем 
```bash
TOKEN=TOKEN123 #тут можно прописать любой токен
DEBUG=False
DB_ENGINE=django.db.backends.postgresql
DB_NAME=postgres
POSTGRES_USER=postgres
POSTGRES_PASSWORD=postgres
DB_HOST=db
DB_PORT=5432
ALLOWED_HOSTS=* #158.160.57.66
TIME_ZONE=UTC
USE_TZ=True
# * - примечание: хост должен быть ALLOWED_HOSTS=*
```
8. В файле settings.py у переменной DEBUG меняем значения на True:
```bash
DEBUG = True # os.getenv('DEBUG', default=True)
```
9. В папке infra/ в файле docker-compose.yml в сервисах закоментируем image для докер-хаба:
```bash
# Должно быть так:
...
backend:
#  image: artyomvah/foodgram_backend # для запуская в облаке/на удаленном сервере
  image: foodgram_backend # для запуская на локальном компе
  ...
frontend:
#   image: artyomvah/foodgram_frontend # для запуская в облаке/на удаленном сервере
  image: foodgram_frontend # для запуская на локальном компе
  ...
* примечание - обязательно убедитесь что у вас на компе установлен докер 
и докеркомпоус.
```

10. Запустим докер-файлы backend и frontend:
```bash
# в консоли будет выведено:
cd backend/
docker build -t foodgram_backend .
# [+] Building 1.9s (10/10) FINISHED
#  => [internal] load .dockerignore                                                                           0.0s 
#  => => transferring context: 2B                                                                             0.0s 
#  => [internal] load build definition from Dockerfile                                                        0.0s 
#  => => transferring dockerfile: 278B                                                                        0.0s 
#  => [internal] load metadata for docker.io/library/python:3.9-slim                                          0.6s 
#  => [1/5] FROM docker.io/library/python:3.9-slim@sha256:5cde4e147c4165ad8dbf8a4df9631863766eeb0b79b890fafe  0.0s 
#  => [internal] load build context                         
#  ...
#  => => naming to docker.io/library/foodgram_backend  


cd frontend/
docker build -t foodgram_frontend .
# в консоли будет выведено:
# [+] Building 4.8s (12/12) FINISHED
#  => [internal] load build definition from Dockerfile       0.0s 
#  => => transferring dockerfile: 201B                       0.0s 
#  => [internal] load .dockerignore    
#  ...
#   => => naming to docker.io/library/foodgram_frontend   
```

11. Переходим в папку infra/ пересобераем контейнеры и запускаем их 
```bash
cd infra/
docker-compose up -d --build
# Первый раз в консоли будет выведено:
# [+] Running 15/2
#  ✔ nginx 5 layers [⣿⣿⣿⣿⣿]     0B/0B     Pulled     9.5s 
#  ✔ db 8 layers [⣿⣿⣿⣿⣿⣿⣿⣿]    0B/0B     Pulled     8.9s 
# [+] Running 5/5
#  ✔ Network infra_default        Created    0.1s 
#  ✔ Container infra-db-1         Started    2.6s 
#  ✔ Container foodgram_frontend  Started    1.6s 
#  ✔ Container foodgram_backend   Started    1.4s 
#  ✔ Container foodgram_nginx     Started 

далее при следующих запусках выполнении команды:
docker-compose up -d --build 
# в консоли будет выведено:
# [+] Running 5/5
#  ✔ Network infra_default       Created         0s 
#  ✔ Container infra-db-1        Started         8s 
#  ✔ Container infra-backend-1   Started       1.3s 
#  ✔ Container infra-frontend-1  Started       2.0s 
#  ✔ Container infra-nginx-1     Started       3.1s 
```
12. Создаем миграции и выполняемя их:
```bash
docker-compose exec backend python manage.py makemigrations
# в консоли будет выведено:
# Migrations for 'api':
#   api/migrations/0001_initial.py
#     - Create model FavoriteRecipe
#     - Create model Ingredient
#     - Create model Recipe
#     - Create model RecipeIngredient
#     - Create model ShoppingCart
#     - Create model Subscribe
#     - Create model Tag
#     ...
# Migrations for 'users':
#   users/migrations/0001_initial.py
#     - Create model User

docker-compose exec backend python manage.py migrate
# в консоли будет выведено:
# Operations to perform:
#   Apply all migrations: admin, api, auth, authtoken, contenttypes, sessions, users
# Running migrations:
#   Applying contenttypes.0001_initial... OK
#   Applying contenttypes.0002_remove_content_type_name... OK
#   Applying auth.0001_initial... OK
#   Applying auth.0002_alter_permission_name_max_length... OK
#   ...
#   Applying authtoken.0003_tokenproxy... OK
#   Applying sessions.0001_initial... OK
```
13. Создаем суперюзера(админа):
```bash
docker-compose exec backend python manage.py createsuperuser
# в консоли будет выведено:
# Email: adm@mail.ru
# Имя пользователя: adm
# Имя: adm
# Фамилия: adm
# Password: 
# Password (again):
```
14. Соберем статику:
```bash
docker-compose exec backend python manage.py collectstatic --no-input
# в консоли будет выведено:
# 160 static files copied to '/app/static'.
```

15. Загружаем теги и ингридиенты:
```bash
docker-compose exec backend python manage.py load_tags
# Все тэги загружены!
docker-compose exec backend python manage.py load_ingrs
# Все ингридиенты загружены!
```
16. Переходим по адресу чтобы увидеть работу нашего сайта:
```bash
http://127.0.0.1/signin
```
17. Документация к API доступнапо адресу:
```bash
http://127.0.0.1/api/docs/
```
18. Создаем любой аккаунт, вводим: 
```bash
# Например:
Имя: test
Фамилия: test
Имя пользователя: test
Адрес электронной почты: test@mail.ru
Пароль: 11test11
```
19.  Авторизуемся:
```bash
# Например:
 Электронная почта: test@mail.ru
 Пароль: 11test11
# Далее уже заходим, добавляем рецепты и пользуемся сайтом в свое удовольствие!
```

20. Остановка проекта, удаление всех контейнеров:
```bash
docker-compose down
# в консоли будет выведено:
# [+] Running 5/5
#  ✔ Container infra-nginx-1     Removed              0.5s 
#  ✔ Container infra-frontend-1  Removed              0.0s 
#  ✔ Container infra-backend-1   Removed              10.3s 
#  ✔ Container infra-db-1        Removed              0.0s 
#  ✔ Network infra_default       Removed              0.3s 
```
<br>

#### ***2й этап. Установка на виртуальную машину Яндекс.Облако(Ubuntu 20.04)***
```
Для тех, кто обучается на Яндекс.Практикуме по направлению Python-разработчик, этот проект стал наиболее сложным среди всех, 
которые я выполнял здесь. Мне потребовалось значительное количество времени, чтобы разобраться с ним, особенно в отношении
модуля "Управление проектом на удалённом сервере".
Кратко опишу, что вам не нужно полностью копировать свой проект на удалённый сервер и там разворачивать postgresql и т.д., 
как это было в 14-м спринте (а я делал именно так - это неверно). Вместо этого, все действия следует выполнять с помощью CI/CD. 
Вам необходимо установить Docker и Docker-compose на удалённый сервер, скоприровать файлы docker-compose.yml и nginx.conf из 
вашего проекта, добавить секреты Docker, базы данных, SSH_KEY и другие ваши секреты на GitHub (все секреты прописаны в 
.github\workflows), и запустить команду. После завершения всех операций в Actions на GitHub, выполните несколько команд 
(они будут описаны ниже) и откройте в браузере следующую ссылку: http://Ваш Публичный IPv4/recipes. И все сайт работает!)
Пожалуйста, цените чужой труд. Буду очень признателен за вашу поддержку и оценку проекта звездочками. Спасибо!
```

*****Если у вас заработал сайт на локальном компе и вы поняли как его запускть, это значит уже проделана половина работы!*****

1. Создаем новую виртуальную машину Ubuntu 20.04 и делаем ваш 'Публичный IPv4' статическим, заходим на сервер ssh username@Публичный IPv4
```bash
ssh helllsin@158.160.57.66
```
2. Обновляем пакеты на нашем удаленном сервере:
```bash
sudo apt update && sudo apt upgrade -y && sudo apt install curl -y
```
3. Устанавливаем docker и docker-compose на систему с использованием скрипта get-docker.sh
```bash
helllsin@foodgram:~$ sudo curl -fsSL https://get.docker.com -o get-docker.sh && sudo sh get-docker.sh && sudo rm get-docker.sh
# ждем пока все не установится, может занять несколько минут
```
4. Обновляем docker-compose до версии 1.29.2, а также установливаем необходимые права и разрешения для выполнения этих операции.
```bash
 sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```
5. Устанавливаем исполняемые права на файл docker-compose.
```bash
sudo chmod +x /usr/local/bin/docker-compose
```
6. Запускаем службу Docker настраиваем ее на автоматический запуск при загрузке системы.
```bash
sudo systemctl start docker.service && sudo systemctl enable docker.service
```
7. На github добавляем все нужные секреты:
```bash
DOCKER_PASSWORD
DOCKER_USERNAME
HOST # это наш - Публичный IPv4 158.160.57.66
PASSPHRASE  
SSH_KEY # его узнаем на локально компе cat ~/.ssh/id_rsa
TELEGRAM_TO
TELEGRAM_TOKEN
USER
```
8. В файле settings.py у переменной DEBUG меняем значение:
```bash
DEBUG = os.getenv('DEBUG', default=False)
```

9. В файле .env прорисываем в переменной ALLOWED_HOSTS ваш 'Публичный IPv4'
```bash
ALLOWED_HOSTS=Публичный IPv4
у меня этот файл такой:
# TOKEN=p&l%385148kslhtyn^
# DEBUG=False
# DB_ENGINE=django.db.backends.postgresql
# DB_NAME=postgres
# POSTGRES_USER=postgres
# POSTGRES_PASSWORD=postgres
# DB_HOST=db
# DB_PORT=5432
# ALLOWED_HOSTS=158.160.57.66
# TIME_ZONE=UTC
# USE_TZ=True
```

10. В папке infra/ в файле docker-compose.yml в сервисах закоментируем image для докер-хаба, лучше выложить на ваш dockerhub, создать и прописать свои образы:
```bash
# Должно быть так:
...
backend:
  image: artyomvah/foodgram_backend # для запуская в облаке/на удаленном сервере
#   image: foodgram_backend # для запуская на локальном компе
  ...
frontend:
  image: artyomvah/foodgram_frontend # для запуская в облаке/на удаленном сервере
#   image: foodgram_frontend # для запуская на локальном компе
  ...
```
11. Создаем папку infra в домашней директории /home/username/ и переходим в нее:
```bash
cd ~
mkdir infra
cd infra/
```

12. Копируем файл docker-compose.yml, default.conf и файл .env на удаленный сервер:
```bash
# я копировал файлы с локального компа на удаленный сервер так:
scp "D:\Dev\PUBLIC_REP\foodgram-project-react\infra\docker-compose.yml" helllsin@158.160.57.66:~/infra/

scp "D:\Dev\PUBLIC_REP\foodgram-project-react\infra\default.conf" helllsin@158.160.57.66:~/infra/

scp "D:\Dev\PUBLIC_REP\foodgram-project-react\infra\.env" helllsin@158.160.57.66:~/infra/
```

13. Собираем контейнеры, при помощи docker-compose:
```bash
sudo docker-compose up -d --build
# в консоли будет выведено:
# Creating network "infra_default" with the default driver
# Creating volume "infra_postgres_data" with default driver
# Creating volume "infra_static_value" with default driver
# Creating volume "infra_media_value" with default driver
# Creating volume "infra_data_value" with default driver
# Pulling db (postgres:14.6-alpine)...
# 14.6-alpine: Pulling from library/postgres
# 8921db27df28: Pull complete
# ...
# 32b7488a3833: Pull complete
# Digest: sha256:ed7f815851b5299f616220a63edac69a4cc200e7f536a56e421988da82e44ed8
# Status: Downloaded newer image for nginx:1.19.3
# Creating infra_db_1 ... done
# Creating infra_backend_1 ... done
# Creating infra_frontend_1 ... done
# Creating infra_nginx_1    ... done
```
14.  Выполняем команды для установки и удаления и запускаем опять:
```bash
sudo docker-compose stop
sudo docker-compose down -v
sudo docker-compose up -d --build
```
15.  Выполняем команды:
```bash
sudo docker-compose exec backend python manage.py makemigrations
# в консоли будет выведено:
# Migrations for 'api':
#   api/migrations/0001_initial.py
#     - Create model FavoriteRecipe
#     - Create model Ingredient
#     - Create model Recipe
#     - Create model RecipeIngredient
#     - Create model ShoppingCart
#     - Create model Subscribe
#     - Create model Tag
#   api/migrations/0002_initial.py
#     - Add field author to subscribe
#     - Add field user to subscribe
#     - Add field recipe to shoppingcart
#     - Add field user to shoppingcart
#     - Add field ingredient to recipeingredient
#     - Add field recipe to recipeingredient
#     - Add field author to recipe
#     - Add field ingredients to recipe
#     - Add field tags to recipe
#     - Add field recipe to favoriterecipe
#     - Add field user to favoriterecipe
#     - Create constraint unique_subscription on model subscribe
#     - Create constraint unique ingredient on model recipeingredient
# Migrations for 'users':
#   users/migrations/0001_initial.py
#     - Create model User
```
16.  Выполняем команды:
```bash
sudo docker-compose exec backend python manage.py migrate --noinput
# в консоли будет выведено:
# Operations to perform:
#   Apply all migrations: admin, api, auth, authtoken, contenttypes, sessions, users
# Running migrations:
#   Applying contenttypes.0001_initial... OK
#   Applying contenttypes.0002_remove_content_type_name... OK
#   Applying auth.0001_initial... OK
#   Applying auth.0002_alter_permission_name_max_length... OK
#   Applying auth.0003_alter_user_email_max_length... OK
#   Applying auth.0004_alter_user_username_opts... OK
#   Applying auth.0005_alter_user_last_login_null... OK
  # Applying authtoken.0003_tokenproxy... OK
  # Applying sessions.0001_initial... OK
```
17. Создаем суперюзера(админа)::
```bash
sudo docker-compose exec backend python manage.py createsuperuser
# создаем админа:
# Email:               adm@mail.ru
# Имя пользователя:    adm
# Имя:                 adm
# Password:            adm
# Password (again):    adm
```
18. Собераем статику и загружаем теги и ингридиенты::
```bash
sudo docker-compose exec backend python manage.py collectstatic --no-input
# 160 static files copied to '/code/static'.

sudo docker-compose exec backend python manage.py load_tags
# Все тэги загружены!

sudo docker-compose exec backend python manage.py load_ingrs
# Все ингридиенты загружены!
```

19. Остановка проекта, удаляем все контейнеры:
```bash
sudo docker-compose down
```

**Пример готового проекта**
***Вывод в браузер:***
![brows_1](https://github.com/artyom-vah/foodgram-project-react/blob/main/scrins/brows_1.jpg)
![brows_2](https://github.com/artyom-vah/foodgram-project-react/blob/main/scrins/brows_2.jpg)
![brows_3](https://github.com/artyom-vah/foodgram-project-react/blob/main/scrins/brows_3.jpg)
![brows_4](https://github.com/artyom-vah/foodgram-project-react/blob/main/scrins/brows_4.jpg)
![brows_5](https://github.com/artyom-vah/foodgram-project-react/blob/main/scrins/brows_5.jpg)
![brows_6](https://github.com/artyom-vah/foodgram-project-react/blob/main/scrins/brows_6.jpg)
![brows_7](https://github.com/artyom-vah/foodgram-project-react/blob/main/scrins/brows_7.jpg)
![brows_8](https://github.com/artyom-vah/foodgram-project-react/blob/main/scrins/brows_8.jpg)
![brows_9](https://github.com/artyom-vah/foodgram-project-react/blob/main/scrins/brows_9.jpg)
<br>

***Админка:***
![Admin_1](https://github.com/artyom-vah/foodgram-project-react/blob/main/scrins/admin_1.jpg)
![Admin_2](https://github.com/artyom-vah/foodgram-project-react/blob/main/scrins/admin_2.jpg)
![Admin_3](https://github.com/artyom-vah/foodgram-project-react/blob/main/scrins/admin_3.jpg)
![Admin_4](https://github.com/artyom-vah/foodgram-project-react/blob/main/scrins/admin_4.jpg)
![Admin_5](https://github.com/artyom-vah/foodgram-project-react/blob/main/scrins/admin_5.jpg)
![Admin_6](https://github.com/artyom-vah/foodgram-project-react/blob/main/scrins/admin_6.jpg)
![Admin_7](https://github.com/artyom-vah/foodgram-project-react/blob/main/scrins/admin_7.jpg)
![Admin_8](https://github.com/artyom-vah/foodgram-project-react/blob/main/scrins/admin_8.jpg)
<br>

***api:***
![api_1](https://github.com/artyom-vah/foodgram-project-react/blob/main/scrins/api_1.jpg)
![api_2](https://github.com/artyom-vah/foodgram-project-react/blob/main/scrins/api_2.jpg)
![api_3](https://github.com/artyom-vah/foodgram-project-react/blob/main/scrins/api_3.jpg)
![api_4](https://github.com/artyom-vah/foodgram-project-react/blob/main/scrins/api_4.jpg)
![api_5](https://github.com/artyom-vah/foodgram-project-react/blob/main/scrins/api_5.jpg)
![api_6](https://github.com/artyom-vah/foodgram-project-react/blob/main/scrins/api_6.jpg)
<br>
***Автор:*** Артем Вахрушев