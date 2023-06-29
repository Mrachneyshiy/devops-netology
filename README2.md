# Домашнее задание к занятию 2. «Применение принципов IaaC в работе с виртуальными машинами»

## Задача 1

- Опишите основные преимущества применения на практике IaaC-паттернов.
- Какой из принципов IaaC является основополагающим?

## Ответ:

- Основными преимуществами IaaC паттернов являются скорость, безопасность, документирование, маштабируемость и стандартизация. Так же, благодаря обеспечения прозрачности можно уменьшить затраты. Еще имеется эфективное восстановление в аварийных ситуациях.
- Идемпотентность — свойство объекта или операции при повторном применении операции к объекту давать тот же результат, что и при первом. 

## Задача 2

- Чем Ansible выгодно отличается от других систем управление конфигурациями?
- Какой, на ваш взгляд, метод работы систем конфигурации более надёжный — push или pull?

## Ответ:

- Ненужно устанавливать агенты на клиентах, использует SSH соединение. Для описания конфигурационных файлов используется удобный для чтения формат YAML. Ansible Galaxy - комьюнити, где можно найти необходимое решение.
- Более надёжным является push. Он позволяет определить когда, куда и какую конфигурацию отправить. Можно проконтролировать результат применения.

## Задача 3

Установите на личный компьютер:

VirtualBox,
Vagrant,
Terraform,
Ansible.
Приложите вывод команд установленных версий каждой из программ, оформленный в Markdown.

## Ответ:

VirtualBox
[skvorchenkov@localhost ~]$ vboxmanage —version
6.1.42_REDSOFTr155177

[skvorchenkov@localhost ~]$ vagrant —version
Vagrant 2.3.8.dev

[skvorchenkov@localhost ~]$ terraform —version
Terraform v1.3.9
on linux_amd64

[skvorchenkov@localhost ~]$ ansible —version
/usr/lib/python3.8/site-packages/paramiko/transport.py:219: CryptographyDeprecationWarning: Blowfish has been deprecated
"class": algorithms.Blowfish,
ansible 2.9.27
config file = /etc/ansible/ansible.cfg
configured module search path = ['/home/skvorchenkov/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']
ansible python module location = /usr/lib/python3.8/site-packages/ansible
executable location = /usr/bin/ansible
python version = 3.8.2 (default, Apr 14 2023, 00:00:00) [GCC 8.3.1 20191121 (Red Hat 8.3.1-6)

## Задача 4:

Воспроизведите практическую часть лекции самостоятельно.

- Создайте виртуальную машину.
- Зайдите внутрь ВМ, убедитесь, что Docker установлен с помощью команды docker ps,

## Ответ:

VM создалась и запустилась нормально:

[skvorchenkov@localhost vagrant]$ vagrant status
Current machine states:

server1.netology running (virtualbox)

А вот с докером проблема. Хотя Ansible установлел последней версии:

==> server1.netology: Running provisioner: ansible...
Vagrant gathered an unknown Ansible version:

and falls back on the compatibility mode '1.8'.

ansible-playbook: error: unrecognized arguments: —sudo
Ansible failed to complete successfully. Any error output should be
visible above. Please fix these errors and try again.



