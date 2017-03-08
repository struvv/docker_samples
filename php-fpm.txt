#Создание контейнера
touch Dockerfile
vi ./Dockerfile

FROM php:5.6-fpm
EXPOSE 9000

#создание образа приложения
docker build -t php-fpm-5.6 ./
#запуск контейнера. Внутри контейнера php-fpm слушает дефолтный для  php-fpm порт 9000, снаружи контейнер мапит этот порт на 9001
#монтируем папку /var/www сервера в папку /var/www контейнера
docker run -d --name php-fpm-5.6-main -v /var/www:/var/www:ro -p 9001:9000 php-fpm-5.6

#запуск консоли внутри контейрена
docker exec -i -t php-fpm-5.6-main /bin/bash
