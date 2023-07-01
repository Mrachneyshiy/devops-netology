# Домашнее задание "Введение. Экосистема. Архитектура. Жизненный цикл Docker контейнера"


## Задача 1

Сценарий выполнения задачи:

создайте свой репозиторий на https://hub.docker.com;
выберите любой образ, который содержит веб-сервер Nginx;
создайте свой fork образа;
реализуйте функциональность: запуск веб-сервера в фоне с индекс-страницей, содержащей HTML-код ниже:
<html>
<head>
Hey, Netology
</head>
<body>
<h1>I’m DevOps Engineer!</h1>
</body>
</html>
Опубликуйте созданный fork в своём репозитории и предоставьте ответ в виде ссылки на https://hub.docker.com/username_repo.

## Ответ:
 
https://hub.docker.com/r/mrachneyshiy/devops-netology

## Задача 2
Посмотрите на сценарий ниже и ответьте на вопрос: "Подходит ли в этом сценарии использование Docker контейнеров или лучше подойдет виртуальная машина, физическая машина? Может быть возможны разные варианты?"

Детально опишите и обоснуйте свой выбор.

## Ответ:

- Высоконагруженное монолитное java веб-приложение;

Для данного сценария я бы использовал физический сервер, так как это приложение является высоконагруженным.

- Nodejs веб-приложение;

Для данного сценария я бы использовал Docker, так как для этого приложение лучше реализовать микропроцессорную архитектуру.

- Мобильное приложение c версиями для Android и iOS;

Для данного сценария я бы использовал ВМ, так как будет проще тестировать из-за размещения ВМ на одном хосте.

- Шина данных на базе Apache Kafka;

Для данного сценария я предпологаю использовать Docker. Увидел, что в Docker есть готовые образы для Apache Kafka. Легко будет откатит на стабильную версию, на случай каких-то багов.

- Elasticsearch кластер для реализации логирования продуктивного веб-приложения - три ноды elasticsearch, два logstash и две ноды kibana;

Для данного сценария я бы использовал ВМ. Можно использовать кластер для отказоустойчивости. Теоретически kudana и logstash можно вывести в Docker.

- Мониторинг-стек на базе Prometheus и Grafana;

Для данного сценария я бы использовал Docker, так как легко маштабировать, а в хранении данных нет необходимости.

- MongoDB, как основное хранилище данных для java-приложения;

Для данного сценария можно использовать ВМ или физических сервер, в зависимости от нагрузки.

- Gitlab сервер для реализации CI/CD процессов и приватный (закрытый) Docker Registry.

Для данного сценария я бы использовал ВМ и Docker. С помощью Docker легко масштабировать и обновлять приложение, а ВМ подойдет для удобного администрирования.

## Задача 3

- Запустите первый контейнер из образа centos c любым тегом в фоновом режиме, подключив папку /data из текущей рабочей директории на --хостовой машине в /data контейнера.
- Запустите второй контейнер из образа debian в фоновом режиме, подключив папку /data из текущей рабочей директории на хостовой машине в /data контейнера.
- Подключитесь к первому контейнеру с помощью docker exec и создайте текстовый файл любого содержания в /data.
- Добавьте ещё один файл в папку /data на хостовой машине.
- Подключитесь во второй контейнер и отобразите листинг и содержание файлов в /data контейнера.

## Ответ:

Запуск первого контейнера:
[skvorchenkov@localhost ~]$ sudo docker run -v /data:/data —name centos-container -d -t centos
Unable to find image 'centos:latest' locally
latest: Pulling from library/centos
a1d0c7532777: Pull complete
Digest: sha256:a27fd8080b517143cbbbab9dfb7c8571c40d67d534bbdee55bd6c473f432b177
Status: Downloaded newer image for centos:latest
894b9eabbe9a11d8efd3536196a854c4d8fcfc1355a4d5a0db52b098234c8f74

Запуск второго контейнера:
[skvorchenkov@localhost ~]$ sudo docker run -v /data:/data —name debian-container -d -t debian
Unable to find image 'debian:latest' locally
latest: Pulling from library/debian
bba7bb10d5ba: Pull complete
Digest: sha256:d568e251e460295a8743e9d5ef7de673c5a8f9027db11f4e666e96fb5bed708e
Status: Downloaded newer image for debian:latest
3f0e659c7858db95227a37afa44f6f8c3a9c74e287c18480db2aad48ab265812

Подключитемся к первому контейнеру с помощью docker exec и создаем текстовый файл любого содержания в /data:
[skvorchenkov@localhost ~]$ sudo docker exec centos-container /bin/bash -c "echo test>/data/readme_centos.md"

Добавляем ещё один файл в папку /data на хостовой машине:
[root@localhost skvorchenkov]# echo test_2 > /data/readme_host.md

Подключаемся во второй контейнер и отображаем листинг и содержание файлов в /data контейнера:
[root@localhost skvorchenkov]# docker exec -it debian-container /bin/bash
root@3f0e659c7858:/# cd /data/
root@3f0e659c7858:/data# ls -l
total 8
-rw-r--r--. 1 root root 5 Jul 1 19:21 readme_centos.md
-rw-r--r--. 1 root root 7 Jul 1 19:23 readme_host.md
root@3f0e659c7858:/data# cat readme_centos.md
test
root@3f0e659c7858:/data# cat readme_host.md
test_2





