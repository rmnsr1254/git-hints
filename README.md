# Шпаргалка по GIT

### Работа с GitBash

<details>
<summary><b>Навигация</b></summary>

**pwd** (от англ. print working directory, «показать рабочую папку») — покажи, в какой я папке;

**ls** (от англ. list directory contents, «отобразить содержимое директории») — покажи файлы и папки в текущей папке;

**ls -a** — покажи также скрытые файлы и папки, названия которых начинаются с символа .;

**cd first-project** (от англ. change directory, «сменить директорию») — перейди в папку first-project;

**cd first-project/html** — перейди в папку html, которая находится в папке first-project;

**cd ..** — перейди на уровень выше, в родительскую папку;

**cd ~** — перейди в домашнюю директорию (/Users/Username);

**cd /** — перейди в корневую директорию.
</details>

<details>
<summary><b> Работа с файлами и папками</b></summary>

#### Создание

**touch index.html** (англ. touch, «коснуться») — создай файл index.html в текущей папке;

**touch index.html style.css script.js** — если нужно создать сразу несколько файлов, можно напечатать их имена в одну строку через пробел;

**mkdir second-project** (от англ. make directory, «создать директорию») — создай папку с именем second-project в текущей папке.

#### Копирование и перемещение

**cp file.txt ~/my-dir** (от англ. copy, «копировать») — скопируй файл в другое место;

**mv file.txt ~/my-dir** (от англ. move, «переместить») — перемести файл или папку в другое место.

##### Чтение

**cat file.txt** (от англ. concatenate and print, «объединить и распечатать») — распечатай содержимое текстового файла file.txt.

##### Удаление

**rm about.html** (от англ. remove, «удалить») — удали файл about.html;

**rmdir images** (от англ. remove directory, «удалить директорию») — удали папку images;

**rm -r second-project** (от англ. remove, «удалить» + recursive, «рекурсивный») — удали папку second-project и всё, что она содержит.

</details>

<details>
<summary><b>Полезные возможности</b></summary>

Команды необязательно печатать и выполнять по очереди. Можно указать их списком — разделить двумя амперсандами (&&).

У консоли есть собственная память — буфер с несколькими последними командами. По ним можно перемещаться с помощью клавиш со стрелками вверх (↑) и вниз (↓).

Чтобы не вводить название файла или папки полностью, можно набрать первые символы имени и дважды нажать Tab. Если файл или папка есть в текущей директории, командная строка допишет путь сама.

Например, вы находитесь в папке dev. Начните вводить cd first и дважды нажмите Tab. Если папка first-project есть внутри dev, командная строка автоматически подставит её имя. Останется только нажать Enter.
</details>

---

## Работа с удаленным репозиторием

<details>
<summary><b>Генерация SSH-ключей</b></summary>

**Приватный ключ** (англ. private key) хранится только на вашем компьютере и не должен передаваться кому-либо ещё. Он используется для расшифровки данных.

**Публичный ключ** (англ. public key) доступен всем и используется для шифрования данных. Они могут быть расшифрованы парным приватным ключом

##### Проверка наличия ключей

cd ~ && ls -la .ssh/

##### Генерация ключей

ssh-keygen -t [ed25519/rsa] -C "e-mail"

##### Добавление ключей в GitHub

Скопировать содержимое ключа в буфер обмена:

clip < ~/.ssh/id_rsa.pub

Со стороны GitHub: Settings -> SSH and GPD keys -> Add SSH key

</details>

<details>
<summary><b>Связывание репозиториев</b></summary>

Создание локального репозитория и инициализация

Создать директорию локального репозитория

[Находясь в папке локального репозитория]

git init

</details>

<details>
<summary><b>Связывание репозиториев</b></summary>

Со стороны GitHub: Страница репозитория -> Скопировать ссылку для SSH

Со стороны GitBash:

[Находясь в папке локального репозитория]

git remote add origin [ссылка на проект]

_Примечание:_ origin - название главного удаленного репозитория

Убедиться, что репозитории связаны: 

git remote -v

</details>

<details>
<summary><b>Синхронизация репозиториев</b></summary>

[Находясь в папке локального репозитория]

git add [Имя файла] && git commit -m "Комментарий" && git push

_Примечание:_ для первого пуша явно указать

git push -u origin master

</details>

---

## Логи, хеши и ЖЦ файла

<details>
<summary><b>Логи, хеши и ЖЦ файла</b></summary>

git log [-oneline] - история коммитов [в однострочной форме]

Хеш коммита - его однозначный идентификатор

HEAD - файл со ссылкой на последний коммит

ЖЦ файла:

```mermaid

graph LR;

untracked -- "git add" --> staged;
staged -- "Изменение файла" --> tracked & modified;
staged -- "git commit -m" --> tracked & commited

```

</details>

