# Домашнее задание к занятию 4. «Оркестрация группой Docker-контейнеров на примере Docker Compose»

## Задача 1
Создайте собственный образ любой операционной системы (например ubuntu-20.04) с помощью Packer (инструкция).

Чтобы получить зачёт, вам нужно предоставить скриншот страницы с созданным образом из личного кабинета YandexCloud.

## Ответ:
![](pic/1.jpg) 

## Задача 2
2.1. Создайте вашу первую виртуальную машину в YandexCloud с помощью web-интерфейса YandexCloud.

## Ответ:
![](pic/2.jpg) 

## Задача 3
С помощью Ansible и Docker Compose разверните на виртуальной машине из предыдущего задания систему мониторинга на основе Prometheus/Grafana. Используйте Ansible-код в директории (src/ansible).

Чтобы получить зачёт, вам нужно предоставить вывод команды "docker ps" , все контейнеры, описанные в docker-compose, должны быть в статусе "Up".

## Ответ:
![](pic/3.jpg)

## Задача 4
- Откройте веб-браузер, зайдите на страницу http://<внешний_ip_адрес_вашей_ВМ>:3000.
- Используйте для авторизации логин и пароль из .env-file.
- Изучите доступный интерфейс, найдите в интерфейсе автоматически созданные docker-compose-панели с графиками(dashboards).
- Подождите 5-10 минут, чтобы система мониторинга успела накопить данные.

## Ответ:
![](pic/4.jpg)




