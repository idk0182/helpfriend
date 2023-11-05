# Здарова это короче базовая шпаргалка по git/github

## тут располагается база по git

ls-список файлов/директорий(показ скрытых с -a)
touch-создать
mkdir-создать директорию(папку)
cp - copy
mv - move
cd-change directory
cat-прочитать(объединить и распечатать)
rm-remove(-r(recursive))
rmdir-remove directory
pwd-показывает нахождение в папке
add-добавить в репозиторий(можно --all, ., или конкретный файл/папку)
git commit -m - сохранить с комментарием(-m)
git init-создание репозитория(initialization)
rm -rf .git-удалить репозиторий
git status-статус
git log - список происходящего

## А вот здесь уже база по github(связка/синзронизация/создание ключей и т.п.)


### Связка удалённого проекта с локальным

```bash

git remote add

```
(добавление удалённого пространства(репозитория))<br>

```bash

$ cd ~/dev/first-project 

$ git remote add origin git@github.com:idk0182/first-project.git

```
(строки для привязки репозиториев(проектов))<br>

```bash

git remote -v

```
для проверки работы

## Синхронизация репозиториев

```bash

git push -u origin main

``` 

(отправка изменений(потом можно убрать часть после push))

### Создание ssh-ключей и перенос на GitHub

```bash

ls -la .ssh/

``` 

(вывод ключей в виде файлов)<br>

```bash

ssh-keygen -t ed25519 -C"электронная почта"

```

(создание самих ключей)<br>

```bash

rm -rf ~/.ssh

```

(Удаление ключей(в случае бага))

## MarkDown Пунктуация(пунктуация к этому файлу)

# Шпаргалка markdown
## Выделение текста 
Вы можете выделять текст в markdown с помощью символов `_` или `*`. Например: Пример _курсива_ и **жирного** текста. 
## Заголовки
Заголовки можно создавать с помощью символа `#`. 
Чем больше `#`, тем меньше заголовок.
Например:
# Заголовок первого уровня
## Заголовок второго уровня
### Заголовок третьего уровня
## Выделение кода
Чтобы выделить текст как код, поместите его в тройные кавычки ``` ```. 
```bash

mkdir my_project cd my_project git init 

```
Это лишь некоторые функции markdown.

# Хеш — идентификатор коммита
В процессе работы с Git вам будет часто встречаться понятие «хеш коммита». Эти странные строчки с бессмысленным (на первый взгляд) набором букв и цифр вы могли видеть, когда вызывали команду git log и выводили историю коммитов. Хеш — идентификатор коммита.


## Что такое хеш. Хеширование коммитов

Хеширование (от англ. hash, «рубить», «крошить», «мешанина») — это способ преобразовать набор данных и получить их «отпечаток» (англ. fingerprint).


Информация о коммите — это набор данных: когда был сделан коммит, содержимое файлов в репозитории на момент коммита и ссылка на предыдущий, или родительский (англ. parent), коммит.


Git хеширует (преобразует) информацию о коммите с помощью алгоритма SHA-1 (от англ. Secure Hash Algorithm — «безопасный алгоритм хеширования») и получает для каждого коммита свой уникальный хеш — результат хеширования.


Обычно хеш — это короткая (40 символов в случае SHA-1) строка, которая состоит из цифр 0—9 и латинских букв A—F (неважно, заглавных или строчных). Она обладает следующими важными свойствами:


* если хеш получить дважды для одного и того же набора входных данных, то результат будет гарантированно одинаковый;


* если хоть что-то в исходных данных поменяется (хотя бы один символ), то хеш тоже изменится (причём сильно).


Чтобы убедиться в этом, можно поэкспериментировать с SHA-1 на этом сайте — попробуйте ввести в поле input (англ. «ввод») разные символы, слова или предложения и понаблюдайте, как меняется хеш в поле output (англ. «вывод»).


## Хеш — основной идентификатор коммита


Git хранит таблицу соответствий хеш → информация о коммите. Если вы знаете хеш, вы можете узнать всё остальное: автора и дату коммита и содержимое закоммиченных файлов. Можно сказать, что хеш — основной идентификатор коммита.


При работе с Git хеши будут встречаться вам регулярно. Их можно будет передавать в качестве параметра разным Git-командам, чтобы указать, с каким коммитом нужно произвести то или иное действие.


Все хеши и таблицу хеш → информация о коммите Git сохраняет в служебные файлы. Они находятся в скрытой папке .git в репозитории проекта.

# Исследуем лог


В этом уроке рассмотрим подробнее, из каких элементов состоит описание коммита, а также как вывести сокращённый лог (от англ. log — «журнал [записей]»). Сокращённый лог полезен, если нужно быстро найти нужный коммит среди сотни других.


## Элементы описания коммита


После вызова git log появляется список коммитов.


### Разберём элементы, из которых состоит описание:

* строка из цифр и латинских букв после слова commit — это хеш коммита;
* Author — имя автора и его электронная почта;
* Date — дата и время создания коммита;
* в конце находится сообщение коммита.


Исходный код самого Git тоже хранится в Git-репозитории (тут уместно вспомнить про курицу и яйцо).


# Получить сокращённый лог — 
```bash
git log --oneline
```

Получить сокращённый лог можно с помощью команды git log с флагом --oneline (англ. «одной строкой»). В терминале появятся только первые несколько символов хеша каждого коммита и их комментарии.

## HEAD - Что это?

* В числе прочих файлов в папке .git есть служебный файл HEAD. Он указывает на самый свежий коммит.

* Вместо хеша последнего коммита можно написать слово HEAD — Git вас поймёт.

# Статусы файлов Git

* Статусом untracked помечается файл, о существовании которого Git знает, но не следит за изменениями в нём. Этот статус — противоположность tracked, в который попадают все файлы, отслеживаемые Git.

* Файл переходит в статус staged после выполнения git add.

* Статус modified означает, что файл был изменён.

* Большинство файлов в проектах «шагает» по следующему циклу: «изменён» → «добавлен в список на коммит» → «закоммичен» → «изменён» → и так далее.

## Чтение Git status

* Команда git status всегда подскажет, что происходит с файлом: например, он добавлен в список «на коммит» или ещё вообще не отслеживается, или изменён.

* git status показывает явно следующие состояния файлов: untracked, staged и modified.

* git status подсказывает, какие команды можно выполнить, чтобы поменять состояние файла.

# Описание коммитов!

Правильно описывать коммиты — искусство, к которому стоит приобщиться как можно раньше. Хорошо, когда:

* сообщение коммита легко читается;

* оно информативное;

* все сообщения оформлены в одном стиле.
