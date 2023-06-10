1. Найдите полный хеш и комментарий коммита, хеш которого начинается на aefea.
Решение:
git show aefea
Ответ: 
commit aefead2207ef7e2aa5dc81a34aedf0cad4c32545
CHANGELOG.md

2. Ответьте на вопросы.
- Какому тегу соответствует коммит 85024d3?
Решение:
git show 85024
Ответ:
commit 85024d3100126de36331c6982bfaac02cdab9e76 (tag: v0.12.23)

- Сколько родителей у коммита b8d720? Напишите их хеши.
Решение:
git show --pretty=format:"%P" b8d720
Ответ:
56cd7859e05c36c06b56d013b55a252d0bb7e158 
9ea88f22fc6269854151c571162c5bcf958bee2b

- Перечислите хеши и комментарии всех коммитов, которые были сделаны между тегами v0.12.23 и v0.12.24.
Решение:
git log v0.12.23..v0.12.24 --oneline
Ответ: 
33ff1c03bb (tag: v0.12.24) v0.12.24
b14b74c493 [Website] vmc provider links
3f235065b9 Update CHANGELOG.md
6ae64e247b registry: Fix panic when server is unreachable
5c619ca1ba website: Remove links to the getting started guide's old location
06275647e2 Update CHANGELOG.md
d5f9411f51 command: Fix bug when using terraform login on Windows
4b6d06cc5d Update CHANGELOG.md
dd01a35078 Update CHANGELOG.md
225466bc3e Cleanup after v0.12.23 release

- Найдите коммит, в котором была создана функция func providerSource, её определение в коде выглядит так: func providerSource(...) (вместо троеточия перечислены аргументы).
Решение:
git log -S"func providerSource(" --oneline
Ответ: 
8c928e8358 main: Consult local directories as potential mirrors of providers

- Найдите все коммиты, в которых была изменена функция globalPluginDirs.
Решение: 
git grep 'func globalPluginDirs'
git log -L :'func globalPluginDirs':plugins.go --oneline
Ответ:
78b1220558
52dbf94834

- Кто автор функции synchronizedWriters?
Решение:
git log -S"func synchronizedWriters(" --pretty=format:"%h - %an %ae"

bdfea50cc8 - James Bardin j.bardin@gmail.com
5ac311e2a9 - Martin Atkins mart@degeneration.co.uk

git show bdfea50cc8
git show 5ac311e2a9

Ответ:
Если посмотреть два коммита, то в итоге автором будет этот: Author: Martin Atkins mart@degeneration.co.uk 