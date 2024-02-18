# Практическая работа №1. 
## «Делимся проектом с миром»
---

### Работа с консолью

#### Навигация


* ```pwd``` — показать рабочую папку
* ```cd``` — сменить директорию
* ```cd ..```— перейди на уровень выше, в родительскую папку;
* ```cd ~``` — перейди в домашнюю директорию (/Users/Username);
* ```cd /``` — перейди в корневую директорию.
* ```ls``` — отобразить содержимое директории
* ```ls -a```— покажи также скрытые файлы и папки, названия которых начинаются с символа .;


#### Работа с файлами и папками


* ```touch``` — создать файл
* ```mkdir``` — создать директорию
    * ```mkdir -p``` — создать структуру директории
* ```cp``` — копировать файл
    * Структура: ```cp что_копируем куда_копируем```
* ```mv``` — переместить файл
   * Структура: ```mv что_копируем куда_копируем```
* ```cat``` — прочитать файл
* ```rm``` — удалить файл
  * ```rm - r``` — рекурсивно удалить файлы из папки
* ```rmdir``` — удалить папку

#### Полезные возможности

* ```&&``` - выполнение нескольких команд сразу
* ```↑↓``` - перемещение по истории использования команд
* ```Tab``` - дополнение команды


### Работа с git


* ```init``` — сделать папку репозиторием 
* ```rm -rf .git``` — «разгитить» папку
* ```git status``` — проверить состояние репозитория
* ```git add``` — Подготовить файлы к сохранению 
* ```git add --all``` — Команда подготовит к сохранению сразу все файлы.
* ```git add .``` — c помощью можно добавить в репозиторий текущую папку со всеми файлами.
* ```git commit -m``` — Выполнить коммит c сообщением
* ```git log``` — Просмотреть историю коммитов
* ```git remote add``` — Привязать удалённый репозиторий к локальному
* ```git remote -v``` — Убедиться, что репозитории связаны
* ```git push``` — Отправить изменения на удалённый репозиторий


### Работа с github

**GitHub** — платформа для хранения IT-проектов и совместной работы над ними с использованием Git

#### SSH
Один из наиболее распространённых сетевых протоколов — **SSH** (от англ. **S**ecure **S**hell **P**rotocol). Он обеспечивает безопасный обмен данными в сети. С помощью этого протокола можно получать данные с удалённого компьютера или отправлять их на него. Трафик шифруется, поэтому протокол безопасен.
**SSH** использует пару ключей для обеспечения безопасности — публичный и приватный: 
* Приватный ключ (англ. private key) хранится только на вашем компьютере и не должен передаваться кому-либо ещё. Он используется для расшифровки данных.
* Публичный ключ (англ. public key) доступен всем и используется для шифрования данных. Они могут быть расшифрованы парным приватным ключом.

Проверка наличия SSH-ключа
1. ```cd ~``` — перейти в домашнюю директорию 
2. ```ls -la .ssh/ ``` — вывести список созданных ключей 


### Хеш в Git

Хеш (от англ. hash) в Git - это уникальный идентификатор коммита, создаваемый с помощью алгоритма SHA-1. Он используется для идентификации версий проекта.

#### Хеширование коммитов

Git преобразует информацию о коммите в уникальный хеш с помощью алгоритма SHA-1. Этот хеш является короткой строкой, обладающей уникальностью и свойством изменяться при изменении данных.

#### Использование хешей в Git

Хеш коммита служит основным идентификатором коммита в Git. Он используется для получения информации о коммите и управления версиями проекта.

#### Где хранятся хеши?

Хеши коммитов и соответствующая информация хранятся в служебных файлах в скрытой папке .git в корне репозитория.




### Логи коммитов в Git

При использовании команды git log вы получаете список коммитов с их описанием.

#### Элементы описания коммита

Описание коммита состоит из следующих элементов:
- Хеш коммита: строка из цифр и латинских букв после слова "commit".
- Author: имя автора и его электронная почта.
- Date: дата и время создания коммита.
- Сообщение коммита.

#### Получение сокращённого лога

Чтобы получить сокращённый лог, используйте команду git log с флагом --oneline. Это позволит увидеть первые несколько символов хеша каждого коммита и их комментарии.

Сокращённый лог полезен, особенно когда в репозитории много коммитов, так как позволяет быстро найти нужный коммит по его описанию.


### HEAD в Git


При вызове команды `git log` вы также могли заметить надпись `(HEAD -> master)` после хеша одного из коммитов. Давайте разберем, что она означает.

#### Файл HEAD

Файл HEAD (англ. "голова") — один из служебных файлов папки .git. Он указывает на последний сделанный коммит, то есть на самый новый.

Внутри HEAD находится ссылка на файл: `refs/heads/master` (или `refs/heads/main`, в зависимости от названия ветки). Если заглянуть в этот файл, можно увидеть хеш последнего коммита.

При работе с Git указатель HEAD используется довольно часто. Многие команды Git принимают в качестве параметра хеш коммита. Если нужно передать последний коммит, то вместо его хеша можно просто написать слово HEAD — Git поймет, что вы имели в виду последний коммит.




### Статусы файлов в Git

####  Статусы untracked/tracked, staged и modified

- **untracked**: файл не отслеживается Git, он существует, но не был добавлен в репозиторий.
- **staged**: файл добавлен в staging area и будет включен в следующий коммит.
- **tracked**: файл уже отслеживается Git, включая файлы, добавленные в staging area.
- **modified**: содержимое файла изменилось по сравнению с последней зафиксированной версией.

#### Жизненный цикл файла в Git

1. Файл создан и находится в состоянии untracked.
2. Файл добавлен в staging area с помощью `git add` и переходит в состояние staged (+ tracked).
3. Файл изменен и находится в состоянии staged, modified (+ tracked).
4. Файл снова добавлен в staging area и остается в состоянии staged (+ tracked).
5. Файл закоммичен и переходит в состояние tracked.
6. Файл изменен и находится в состоянии modified (+ tracked).
7. Процесс повторяется.


#### Примечания

- `git add` добавляет в staging area только текущее содержимое файла.
- Коммит с помощью `git commit` фиксирует состояние файлов из staging area.


#### Как читать git status

#### Какие состояния показывает git status

- **staged** (Changes to be committed): изменения файлов добавлены в staging area и будут включены в следующий коммит.
- **modified** (Changes not staged for commit): изменения файлов не добавлены в staging area.
- **untracked** (Untracked files): новые файлы, не добавленные в репозиторий.

