# Github - HELP
> Что такое Git, Github?
   [Сссылка на интересную статью](https://htmlacademy.ru/blog/boost/tools/git-console).  
  
  Файлы в дипозитории:   
- Язык разметки Markdown.txt  
- Базовые команды для Bush Терминала.md 
- HUB.удалённо-создание-репозитория-припомощи-hub

# 1. Установка Git на компьюторе
> Прежде чем пользоваться git его надо установить на компьюторе.
> Проверяем установлен ли Git на компьюторе:
* *git --version*
> После этого надо настроить Git:
  После того как Git появился на компьютере, нужно ввести свои данные, а именно имя и адрес электронной почты. 

Откройте терминал и используйте следующую команду, чтобы добавить своё имя: 
* *git config --global user.name "ваше имя"*

Для добавления почтового адреса вводите: 
* *git config --global user.email адрес*

> Обратите внимание, что в командах, указанных выше, есть опция *--global*. Это значит, что такие данные будут сохранены для всех ваших действий в Git и вводить их больше не надо. Если вы хотите менять эту информацию для разных проектов, то в директории проекта вводите эти же команды, только без опции *--global*.
# 2. Устанавливаем SSH-ключи  
> Что такое SSH-ключ и зачем он нужен?  

Чтобы работать со своего компьютера с GitHub, иметь доступ к проектам, хранящимся на сервисе, выполнять команды в консоли без постоянного подтверждения пароля, нужно пройти авторизацию у сервера. В этом помогают SSH-ключи.  

Каждый SSH-ключ содержит пару: открытый (публичный) и закрытый (приватный) ключ. Открытый ключ отправляется на сервер, его можно не прятать от всех и не переживать, что кто-то его увидит и украдёт. Он бесполезен без своей пары — закрытого ключа. А вот закрытый ключ — секретная часть. Доступ к нему должен быть только у вас.

Вы отправляете какую-то информацию на сервер, где хранится ваш публичный ключ, сервер понимает, что вы это вы, то есть идентифицирует именно вас, и даёт вам какой-то ответ. И только вы можете расшифровать этот ответ, потому что только у вас есть подходящий закрытый ключ. Получается что-то вроде связки логин-пароль только намного безопасней. Ваш пароль кто-то может узнать или подобрать, а чтобы получить ваш приватный SSH-ключ, злоумышленнику придётся взломать ваш компьютер.  

Чтобы пройти авторизацию по SSH-ключу, его надо сгенерировать или найти уже ранее созданный ключ на своём компьютере.

Сначала проверим, есть ли уже на компьютере ключ. По умолчанию SSH-ключи хранятся в каталоге ~/.ssh, поэтому нужно проверить содержимое этого каталога.

Открываем консоль. Вводим команду, чтобы перейти в нужный каталог.:  
* *cd ~/.ssh*  

Вводим команду, чтобы увидеть список всех файлов в каталоге:  
* *ls*  

Ищем пару файлов с названиями вида имя и имя.pub. Обычно имя — id_rsa, id_dsa, id_ecdsa или id_ed25519. Файл с расширением .pub — ваш публичный ключ, а второй — ваш приватный, секретный ключ.  

Если таких файлов или даже каталога .ssh у вас нет, вы можете их сгенерировать. Для этого делаем следующее.  

**... Более подробно смотри по [ссылке](https://htmlacademy.ru/blog/boost/tools/git-console) в разделе: Устанавливаем SSH-ключи.**  

# 3. Работа с репозиториями  
> Для начала определим, что такое репозиторий. Это рабочая директория с вашим проектом. 

По сути, это та же папка с HTML, CSS, JavaScript и прочими файлами, что хранится у вас на компьютере, но находится на сервере GitHub. Поэтому вы можете работать с проектом удалённо на любой машине, не переживая, что какие-то из ваших файлов потеряются — все данные будут в репозитории при условии, что вы их туда отправите.  

## 1. Клонирование Репозитория c Github себе на компьютер, чтобы вести работу с кодом локально.  
Тут нам и пригодится SSH.  

Открываем консоль, переходим в директорию, где хотим сохранить папку с проектом, и вводим команду:
* *git clone git@github.com:your-nickname/your-project.git*  

Адрес репозитория: зайти на страницу проекта, нажать зелёную кнопку Clone or download (клонировать или скачать), выбрать Clone with SSH (клонировать по SSH) и скопировать адрес, который находится в текстовом поле. Этот адрес вы можете вставить в команду *git clone*.  
 
 ## 2. Работаем с кодом на компьюторе локально.
 
 ### а. Работа в Ветке на компьюторе
> Работу над проектом принято вести в ветках. В каждом репозитории есть как минимум одна ветка. Это основная ветка, которую создаёт сам Git, она называется *master* . Обычно в ней находится стабильная версия программы без ошибок.  

Создадим новую ветку. Вводим команды:
* *git branch*  // она показывает список веток, с которыми мы работаем в проекте, и выделяет текущую

Если мы находимся в master создаём новую ветку: 
* *git checkout -b имя-новой-ветки*

Если текущая ветка не master, сначала переключимся в основную ветку: 
* *git checkout master*  // Эта команда позволяет переключаться между существующими ветками в проекте, после *git checkout* надо указать название нужной ветки.

Если вы ошиблись в названии, например, допустили опечатку, вы можете изменить название ветки с помощью команды: 
* *git branch -m старое-имя-ветки новое-имя-ветки*  
>**После того как вы создали ветку, поработали в ней у себя локально — нужно сохранить результат, чтобы он не пропал и в итоге оказался в репозитории.**

### б. Сохранение проекта на компьюторе локално 
Если вы хотите сохранить изменения не во всех файлах, для начала можно ввести команду:
* *git status* // Команда покажет текущее состояние в вашей ветке, а именно список с названиями изменённых файлов, если они есть, и укажет на те, которые ожидают записи и сохранения (обычно они выделены красным цветом).
Перед тем, как зафиксировать изменения отдельных файлов, нужно добавить файлы в набор этих изменений.   
Воспользуйтесь командой:
* *git add имя-файла* // Если название очень длинное, вы можете начать его писать, затем нажать Tab и консоль сама предложит вам продолжение пути к файлу.
Если вы хотите сохранить все изменения разом, вводите команду:
* *git add -A*
Теперь мы можем сделать **коммит**, то есть зафиксировать все сохранённые изменения и дать им название. Это делается с помощью команды: * *git commit -m "ваше сообщение"*
>Текст сообщения должен быть лаконичным и в то же время сообщать о том, что делает коммит (внесённые изменения). Например, «добавляет имя наставника в Readme», «вводит функцию сортировки изображений», «правит ошибку в поиске городов на карте».  
**Изменения, которые мы внесли и сохранили, пока локальны. Их нужно послать на GitHub.**

## с. Отправляем изменения с компьютора на Github 
Чтобы отправить свои изменения *(коммиты)* в репозиторий на GitHub, ввести команду: 
* *git push origin название-текущей-ветки* // где *origin* означает репозиторий, который был склонирован на компьютер













# Команды Git в Терминале, 
##   ВАРИАНТ-1:
   1. Сначала создаем новый репозиторий на сайте Github
   2. Затем уже на компьюторе в редакторе (например в VSCode) вызываем Terminal и начинаем вводить команды:
## Сreate a new repository on the command line
* *git init*   //команда для создания папки .git в папке проекта (например с сайтом) на компьюторе
* *git add .*  
  или 
*  *git add README.md*   // команда для добавления файлов/или например файла README в папку .git в папке проекта на компьюторе 
* *git commit -m "first commit"*   // команда для создания и добавления названия Kommit в папку .git в папке проекта на компьюторе
* *git remote add origin git@github.com:Oxana-S/js-practice.git*
* *git push -u origin master*

## Push an existing repository from the command line

* *git remote add origin git@github.com:Oxana-S/js-practice.git*
* *git push -u origin master*


* Переводы слов:
   remote - удаленный
   kommit - совершать
