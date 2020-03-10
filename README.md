# github-help
> Что такое Git, Github?
   [Сссылка на интересную статью](https://htmlacademy.ru/blog/boost/tools/git-console).  
  
  Файлы в дипозитории:   
- Язык разметки Markdown.txt  
- Базовые команды для Bush Терминала.md 
- HUB.удалённо-создание-репозитория-припомощи-hub

## Установка Git на компьюторе
> Прежде чем пользоваться git его надо установить на компьюторе.
> Проверяем установлен ли Git на компьюторе:
* git --version
> После этого надо настроить Git:
  После того как Git появился на компьютере, нужно ввести свои данные, а именно имя и адрес электронной почты. 

Откройте терминал и используйте следующую команду, чтобы добавить своё имя: 
* git config --global user.name "ваше имя"

Для добавления почтового адреса вводите: 
* git config --global user.email адрес

> Обратите внимание, что в командах, указанных выше, есть опция --global. Это значит, что такие данные будут сохранены для всех ваших действий в Git и вводить их больше не надо. Если вы хотите менять эту информацию для разных проектов, то в директории проекта вводите эти же команды, только без опции --global.
## Устанавливаем SSH-ключи  
Что такое SSH-ключ и зачем он нужен?  
Чтобы работать со своего компьютера с GitHub, иметь доступ к проектам, хранящимся на сервисе, выполнять команды в консоли без постоянного подтверждения пароля, нужно пройти авторизацию у сервера. В этом помогают SSH-ключи.  

## Команды Git в Терминале, 
###   ВАРИАНТ-1:
   1. Сначала создаем новый репозиторий на сайте Github
   2. Затем уже на компьюторе в редакторе (например в VSCode) вызываем Terminal и начинаем вводить команды:
### Сreate a new repository on the command line
* git init   //команда для создания папки .git в папке проекта (например с сайтом) на компьюторе
* git add .  
  или 
*  git add README.md   // команда для добавления файлов/или например файла README в папку .git в папке проекта на компьюторе 
* git commit -m "first commit"   // команда для создания и добавления названия Kommit в папку .git в папке проекта на компьюторе
* git remote add origin git@github.com:Oxana-S/js-practice.git
* git push -u origin master

### Push an existing repository from the command line

* git remote add origin git@github.com:Oxana-S/js-practice.git
* git push -u origin master


* Переводы слов:
   remote - удаленный
   kommit - совершать
