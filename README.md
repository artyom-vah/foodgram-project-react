
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
http://51.250.87.151/admin - Админка (обращаю внимание что надо вводить почту и пароль чтобы войти в админку)
http://51.250.83.246/api/ - api для данного сервиса
http://51.250.87.151/signup - Создать аккаунт
http://51.250.87.151/signin - Вход/Выход
http://51.250.87.151/recipes - рецепты
http://51.250.87.151/subscriptions - подписки
http://51.250.87.151/recipes/create - создать рецепт
http://51.250.87.151/favorites - Избранное
http://51.250.87.151/cart - Список покупок
http://51.250.87.151/change-password - Изменить пароль

* - примечание: данные ссылки будут работать 2-3 дня после пуша на мой github, 
далее виртуалка на яндекс облаке будет удалена и ссылки станут недоступны
```

### Для проверки работы сайта были добавлены админ и 3 пользователя:
***Админ:***
````
почта: adm@mail.ru
пароль: adm
````
***Пользователи:***
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
#### ***1. Установка на локальную машину (на ваш ПК)***

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
TOKEN=p&l%385148kslhtyn^ #тут можно прописать любой токен
DEBUG=False
DB_ENGINE=django.db.backends.postgresql
DB_NAME=postgres
POSTGRES_USER=postgres
POSTGRES_PASSWORD=postgres
DB_HOST=db
DB_PORT=5432
ALLOWED_HOSTS=*
TIME_ZONE=UTC
USE_TZ=True
# * - примечание: хост должен быть ALLOWED_HOSTS=*
```
8. В файле settings.py у переменной DEBUG меняем значения на True:
```bash
DEBUG = True # os.getenv('DEBUG', default=True)
```
9. Переходим в папку backend/ производим миграции:  
```bash
cd backend/
python manage.py migrate
```

10. Загружаем данные ингридиентов и тегов для рецептов:
```bash
python manage.py load_data
# в консоли будет выведено:
# Старт команды
# Данные загружены
```
10. В папке с файлом manage.py запустите сервер:
```bash
python manage.py runserver
```
11. Проверим работу нашего api:
```bash
http://127.0.0.1:8000/api/
# в консоли будет выведено:
# HTTP 200 OK
# Allow: GET, HEAD, OPTIONS
# Content-Type: application/json
# Vary: Accept

# {
#     "ingredients": "http://127.0.0.1:8000/api/ingredients/",
#     "tags": "http://127.0.0.1:8000/api/tags/",
#     "recipes": "http://127.0.0.1:8000/api/recipes/",
#     "users": "http://127.0.0.1:8000/api/users/"
# }
```
12. В папке infra/ в файле docker-compose.yml в сервисах закоментируем image для докер-хаба:
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

13. Запустим докер-файлы backend и frontend:
```bash
# в консоли будет выведено:
cd backend/
docker build -t foodgram_backend .
# [+] Building 42.9s (14/14) FINISHED
#  => [internal] load build definition from Dockerfile                                                                    0.0s 
#  => => transferring dockerfile: 424B                                                                                    0.0s 
#  => [internal] load .dockerignore                                                                                       0.0s 
#  => => transferring context: 2B    
#  ...
#  => => naming to docker.io/library/foodgram_backend  


cd frontend/
docker build -t foodgram_frontend .
# в консоли будет выведено:
# [+] Building 4.8s (12/12) FINISHED
#  => [internal] load build definition from Dockerfile                                                                    0.0s 
#  => => transferring dockerfile: 201B                                                                                    0.0s 
#  => [internal] load .dockerignore    
#  ...
#   => => naming to docker.io/library/foodgram_frontend   
```

14. Переходим в папку infra/, cоберем статику:
```bash
cd infra/
docker-compose exec backend python manage.py collectstatic --no-input
# в консоли будет выведено:
# 195 static files copied to '/app/static'.
```

15. Пересобераем контейнеры и запускаем их 
```bash
docker-compose up -d --build
# в консоли будет выведено:
# [+] Running 5/5
#  ✔ Network infra_default        Created                                                                                 0.0s 
#  ✔ Container infra-db-1         Started                                                                                 0.8s 
#  ✔ Container foodgram_backend   Started                                                                                 1.4s 
#  ✔ Container foodgram_frontend  Started                                                                                 1.6s 
#  ✔ Container foodgram_nginx     Started 

далее при следующем выполнении команды:
docker-compose up -d --build 
# в консоли будет выведено:
# [+] Running 4/4
#  ✔ Container infra-db-1         Started                                                                                 2.4s 
#  ✔ Container foodgram_backend   Started                                                                                 2.5s 
#  ✔ Container foodgram_frontend  Started                                                                                 2.7s 
#  ✔ Container foodgram_nginx     Started                                                                                 2.8s 
```

16.  Переходим по адресу:
```bash
http://localhost/signin
```

17. Создаем аккаунт, вводим: 
```bash
# Например:
Имя: test
Фамилия: test
Имя пользователя: test
Адрес электронной почты: test@mail.ru
Пароль: 11test11
```
18.  Авторизуемся:
```bash
# Например:
 Электронная почта: test@mail.ru
 Пароль: 11test11
# Далее уже заходим, добавляем рецепты и пользуемся сайтом в свое удовольствие!
```
<br>

#### 
***2. Установка на виртуальную машину Яндекс.Облако(Ubuntu 20.04)***
```
Для тех, кто обучается на Яндекс.Практикуме по направлению Python-разработчик, этот проект стал наиболее сложным среди всех, 
которые я выполнял здесь. Мне потребовалось значительное количество времени, чтобы разобраться с ним, особенно в отношении
модуля "Управление проектом на удалённом сервере".
Кратко опишу, что вам не нужно полностью копировать свой проект на удалённый сервер и там разворачивать postgresql и т.д., 
как это было в 14-м спринте (а я делал именно так - это неверно). Вместо этого, все действия следует выполнить с помощью CI/CD. 
Вам необходимо установить Docker и Docker-compose на удалённый сервер, скоприровать файлы docker-compose.yml и nginx.conf из 
вашего проекта, добавить секреты Docker, базы данных, SSH_KEY и другие ваши секреты на GitHub (все секреты прописаны в 
.github\workflows), и запустить команду. После завершения всех операций в Actions на GitHub, выполните несколько команд 
(они будут описаны ниже) и откройте в браузере следующую ссылку: http://Ваш Публичный IPv4/recipes. И все сайт работает!)
Пожалуйста, цените чужой труд. Буду очень признателен за вашу поддержку и оценку проекта звездочками. Спасибо!
```

*****Если у вас заработал сайт на локальном компе и вы поняли как его запускть, это значит уже проделана половина работы!*****

1. Создаем новую виртуальную машину Ubuntu 20.04 и делаем ваш 'Публичный IPv4' статичным.

2. На github добавляем все нужные секреты:
```bash
DOCKER_PASSWORD
DOCKER_USERNAME
HOST
PASSPHRASE
SSH_KEY
TELEGRAM_TO
TELEGRAM_TOKEN
USER
```
3. В файле settings.py у переменной DEBUG меняем значение:
```bash
DEBUG = os.getenv('DEBUG', default=False)
```

4. В файле .env прорисываем в переменной ALLOWED_HOSTS ваш 'Публичный IPv4'
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
# ALLOWED_HOSTS=51.250.87.151
# TIME_ZONE=UTC
# USE_TZ=True
```

5. В папке infra/ в файле docker-compose.yml в сервисах закоментируем image для докер-хаба, лучше выложить на ваш dockerhub, создать и прописать свои образы:
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

6. Выполняем данные команды обновляем пакеты и устанавливаем docker и   docker-compose на наш сервер:
```bash
sudo apt update
sudo apt upgrade -y 
sudo apt install docker.io # подтверждаем Yes
sudo apt install docker-compose # подтверждаем Yes
```

7. Копируем файл docker-compose.yml и nginx.conf на удаленный сервер:
```bash
# я копировал файлы с локального компа на удаленный сервер так:
scp "D:\Dev\PUBLIC_REP\foodgram-project-react\infra\docker-compose.yml" helllsin@51.250.87.151:~/

scp "D:\Dev\PUBLIC_REP\foodgram-project-react\infra\nginx.conf" helllsin@51.250.87.151:~/
```

8. Собираем контейнеры, при помощи docker-compose:
```bash
sudo docker-compose up -d --build
# в консоли будет выведено:
# [+] Running 4/4
#  ✔ Container helllsin-db-1      Started                                    1.1s
#  ✔ Container foodgram_frontend  Started                                    2.4s
#  ✔ Container foodgram_backend   Running                                    0.0s
#  ✔ Container foodgram_nginx     Started                                    2.6s

```

9. Выполняем команды:
```bash
sudo docker-compose exec backend python manage.py migrate
sudo docker-compose exec backend python manage.py createsuperuser
sudo docker-compose exec backend python manage.py collectstatic --no-input
sudo docker-compose exec backend python manage.py load_data
```

10. Остановка проекта, удаляем все контейнеры:
```bash
sudo docker-compose down
# в консоли будет выведено:
# [+] Running 5/4
#  ✔ Container foodgram_frontend  Removed                                    0.3s
#  ✔ Container foodgram_nginx     Removed                                    0.7s
#  ✔ Container foodgram_backend   Removed                                    0.8s
#  ✔ Container helllsin-db-1      Removed                                    0.1s
#  ✔ Network helllsin_default     Removed                                    0.1s
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