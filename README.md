# Домашнее задание к занятию "1. Введение в виртуализацию. Типы и функции гипервизоров. Обзор рынка вендоров и областей применения."

## Задача 1

Опишите кратко, как вы поняли: в чем основное отличие полной (аппаратной) виртуализации, паравиртуализации и виртуализации на основе ОС.

## Ответ:

Аппара́тная виртуализа́ция — виртуализация с поддержкой специальной процессорной архитектуры. В отличие от программной виртуализации, с помощью данной техники возможно использование изолированных гостевых операционных систем, управляемых гипервизором напрямую. Гостевая ОС не зависит от архитектуры хостовой платформы и реализации платформы виртуализации.

Паравиртуализация — техника виртуализации, при которой гостевые операционные системы подготавливаются для исполнения в виртуализированной среде, для чего их ядро незначительно модифицируется. Операционная система взаимодействует с программой гипервизора, который предоставляет ей гостевой API, вместо использования напрямую таких ресурсов, как таблица страниц памяти.

Виртуализация на основе ОС - ядро ОС поддерживает несколько изолированных экземпляров пространства пользователя и эти экземпляры с точки зрения пользователя полностью идентичны реальному серверу.

## Задача 2

Выберите один из вариантов использования организации физических серверов, в зависимости от условий использования.

Организация серверов:
- физические сервера,
- паравиртуализация,
- виртуализация уровня ОС.

Условия использования:
- Высоконагруженная база данных, чувствительная к отказу.
- Различные web-приложения.
- Windows системы для использования бухгалтерским отделом.
- Системы, выполняющие высокопроизводительные расчеты на GPU.

Опишите, почему вы выбрали к каждому целевому использованию такую организацию.

## Ответ:

1. физические сервера - Высоконагруженная база данных, чувствительная к отказу. Данная база высоконагруженная и поэтому требовательна к производительности. Лучше не использовать вертуалицацию, так как на нее необходимо тратить доп.ресурсы.
2. паравиртуализация - Windows системы для использования бухгалтерским отделом. Данные системы не сильно требовательны к производительности. Можно использовать паравиртуализацию для оптимизированного распределения ресурсов серверов.
3. виртуализация уровня ОС - Различные web-приложения. Данная виртуализация уже готова для приложений и позволит их быстро запускать.

## Задача 3

Выберите подходящую систему управления виртуализацией для предложенного сценария. Детально опишите ваш выбор.

## Сценарий 1:

1. 100 виртуальных машин на базе Linux и Windows, общие задачи, нет особых требований. Преимущественно Windows based инфраструктура, требуется 
реализация программных балансировщиков нагрузки, репликации данных и автоматизированного механизма создания резервных копий.

## Ответ 1:

VMWare VSphere - данный сервис позволит организовать кластера серверов для большей отказоустойчивости. Так же данный сервис имеет много дополнительных решений для бэкапа. В этом сервисе удобно создавать и обслуживать виртуальные машины.

## Сценарий 2:

2. Требуется наиболее производительное бесплатное open source решение для виртуализации небольшой (20-30 серверов) инфраструктуры на базе Linux и 
Windows виртуальных машин.

## Ответ 2:

KVM - бесплатное решение. Есть множество систем виртуализации на базе KVM. Так же есть множество инструментов для резервного копирования.

## Сценарий 3:

3. Необходимо бесплатное, максимально совместимое и производительное решение для виртуализации Windows инфраструктуры.

## Ответ 3:

MS HyperV - бесплатное решение, полностью совместимая с Windows.

## Сценарий 4:

4. Необходимо рабочее окружение для тестирования программного продукта на нескольких дистрибутивах Linux.

## Ответ 4:

Docker - можно запустить на большинстве дистрибутивов Linux. Сборку и развёртывание контейнеров можно автоматизировать.

## Задача 4

Опишите возможные проблемы и недостатки гетерогенной среды виртуализации (использования нескольких систем управления виртуализацией одновременно) и что необходимо сделать для минимизации этих рисков и проблем. Если бы у вас был выбор, то создавали бы вы гетерогенную среду или нет? Мотивируйте ваш ответ примерами.

## Ответ:

Очень трудно обслуживать и управлять ресурсами. Можно создать гетерогенную среду с помощью аппаратной виртуализации для оптимального управления ресурсами с возможностью централизованного бэкапа виртуальных машин. А далее запустить контейнеризацию, для быстрого разворачивания сервисов и экономии ресурсов. Если большая инфраструктура, то обазяательно это все нужно максимально автоматизировать.