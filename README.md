# <a name="home"></a>  Github - HELP
> **Что такое Git, Github?** [Ссылка на статью. Работа с Git через консоль](https://htmlacademy.ru/blog/boost/tools/git-console). 

> **Git и Github. Простые рецепты. КОМАНДЫ!!!** [Ссылка на статью. Подробно описан процес и Команды работы с Git b Github](https://habr.com/ru/post/273897/).  

> **Git Book. Документация на русском!!!** [Ссылка на сайт с документацией по Git](https://git-scm.com/book/ru/v2).   

> **Git: вернуться к предыдущему коммиту** [Ссылка на статью. Git: вернуться к предыдущему коммиту](https://dev-gang.ru/article/git-vernutsja-k-predydusczemu-kommitu-1qctx8l7f6/)   
---
Файлы в дипозитории:    
*Язык разметки Markdown.txt*    
*Базовые команды для Bush Терминала.md*   
*HUB.удалённо-создание-репозитория-припомощи-hub*       


**СОДЕРЖАНИЕ**   
>[1. Установка Git на компьюторе](#instal_Git)<br>
>[2. Устанавливаем SSH-ключи](#ssh_key)<br>
>[3. Работа с репозиториями](#rep_work)<br>
  [1) Клонирование Репозитория c Github себе на компьютер, чтобы вести работу с кодом локально.](#rep_work_1)<br>
  [2) Работаем с кодом на компьюторе локально.](#rep_work_2)<br>
    >[а. Работа в Ветке на компьюторе](#rep_work_2_a)<br>
    >[b. Сохранение проекта на компьюторе локално](#rep_work_2_b)<br>
    >[с. Отправляем изменения с компьютора на Github в конкретную (не мастер) ветку](#rep_work_2_c_1)<br>
    >[d. Отправляем изменения с компьютора на Github в мастер ветку ](#rep_work_2_c_2)<br>
  [3) Загрузить на Компьютор изменения, сделанные на Github](#rep_work_3)<br>
>[4. Коротко-Команды Git в Терминале](#com's_git)<br>
  >[1) Если Репозиторий Уже создан онлайн на сайте Github](#com's_git_1)<br>
  >[2) Cоздание Репозитория на Github удаленно, на компьюторе в Терминале при помощи Hub](#com's_git_2)<br>
  >[3) Удаление в Терминале на компьюторе локального Репозитория](#com's_git_3)<br>
  >[4) Работа в Терминале с Ветками](#com's_git_4)<br>
  >[*) Полезные ссылки по Hub](#com's_git_10)<br>
  
  




# <a name="instal_Git"></a>    1. Установка Git на компьюторе
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

<br>[ОГЛАВЛЕНИЕ](#home)   




# <a name="ssh_key"></a>   2. Устанавливаем SSH-ключи  
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

<br>[ОГЛАВЛЕНИЕ](#home)




# <a name="rep_work"></a>  3. Работа с репозиториями    
> Для начала определим, что такое репозиторий. Это рабочая директория с вашим проектом. 

По сути, это та же папка с HTML, CSS, JavaScript и прочими файлами, что хранится у вас на компьютере, но находится на сервере GitHub. Поэтому вы можете работать с проектом удалённо на любой машине, не переживая, что какие-то из ваших файлов потеряются — все данные будут в репозитории при условии, что вы их туда отправите.  

## <a name="rep_work_1"></a>  1) Клонирование Репозитория c Github себе на компьютер, чтобы вести работу с кодом локально.    
Тут нам и пригодится SSH.  

Открываем консоль, переходим в директорию, где хотим сохранить папку с проектом, и вводим команду:
* *git clone git@github.com:your-nickname/your-project.git*  

Адрес репозитория: зайти на страницу проекта, нажать зелёную кнопку Clone or download (клонировать или скачать), выбрать Clone with SSH (клонировать по SSH) и скопировать адрес, который находится в текстовом поле. Этот адрес вы можете вставить в команду *git clone*.  

<br>[ОГЛАВЛЕНИЕ](#home)

## <a name="rep_work_2"></a>  2) Работаем с кодом на компьюторе локально.    

### <a name="rep_work_2_a"></a>  а. Работа в Ветке на компьюторе    
> Работу над проектом принято вести в ветках. В каждом репозитории есть как минимум одна ветка. Это основная ветка, которую создаёт сам Git, она называется *master* . Обычно в ней находится стабильная версия программы без ошибок.  

Создадим новую ветку. 
* *git branch*     
// она показывает список веток, с которыми мы работаем в проекте, и выделяет текущую   

Если мы находимся в master создаём новую ветку: 
* *git checkout -b имя-новой-ветки*

Если текущая ветка не master, сначала переключимся в основную ветку.  
* *git checkout master*      
// Эта команда позволяет переключаться между существующими ветками в проекте, после *git checkout* надо указать название нужной ветки.

Если вы ошиблись в названии, например, допустили опечатку, вы можете изменить название ветки с помощью команды:   
* *git branch -m старое-имя-ветки новое-имя-ветки*  
>**После того как вы создали ветку, поработали в ней у себя локально — нужно сохранить результат, чтобы он не пропал и в итоге оказался в репозитории.**

<br>[ОГЛАВЛЕНИЕ](#home)


### <a name="rep_work_2_b"></a>  b. Сохранение проекта на компьюторе локално    
Если вы хотите сохранить изменения не во всех файлах, для начала можно ввести команду:
* *git status*     
// Показывает текущее состояние в вашей ветке, а именно список с названиями изменённых файлов, если они есть, и укажет на те, которые ожидают записи и сохранения (обычно они выделены красным цветом).  

Перед тем, как зафиксировать изменения отдельных файлов, нужно добавить файлы в набор этих изменений.   
* *git add имя-файла*     
// Добавляет выбранные вами файлы с изменениями для передачи. Если название очень длинное, вы можете начать его писать, затем нажать Tab и консоль сама предложит вам продолжение пути к файлу.    

* *git add .*      
// Добавляет ВСЕ файлы с изменениями для передачи.   

* *git add -A*     
// Если вы хотите сохранить все изменения разом   

Теперь мы можем сделать **коммит**, то есть зафиксировать все сохранённые изменения и дать им название.    
* *git commit -m "ваше сообщение"*
>Текст сообщения должен быть лаконичным и в то же время сообщать о том, что делает коммит (внесённые изменения). Например, «добавляет имя наставника в Readme», «вводит функцию сортировки изображений», «правит ошибку в поиске городов на карте».  
**Изменения, которые мы внесли и сохранили, пока локальны. Их нужно послать на GitHub.**

<br>[ОГЛАВЛЕНИЕ](#home)


## <a name="rep_work_2_c_1"></a>  c. Отправляем изменения с компьютора на Github в конкретную (не мастер) ветку    
Чтобы отправить свои изменения *(коммиты)* в репозиторий на GitHub, ввести команду: 
* *git push origin название-текущей-ветки*    
// где *origin* означает репозиторий, который был склонирован на компьютер    
 
ПОСЛЕ ЭТОГО ЕСЛИ Я ХОЧУ ЭТУ ВЕТКУ СЛИТЬ С МАСТЕР ДЕЛАЕМ  пулреквест... (**надо еще разобраться**)


## <a name="rep_work_2_c_2"></a>  d. Отправляем изменения с компьютора на Github в мастер ветку    
В локальном репозитории вводим команду:
* *git checkout master*    
// При необходимости переходим в ветку master   

* *git push origin master*    
// Передаем изменения в мастер ветку на Github   

<br>[ОГЛАВЛЕНИЕ](#home)


## <a name="rep_work_3"></a>  3) Залить/Загрузить на Компьютор изменения, сделанные на Github 

Для получения обновлений с удаленного репозитория воспользуйтесь командой:   
* *git pull*   
Если вы изменили ваши локальные файлы, то команда *git pull* выдаст ошибку. Если вы уверены, что хотите перезаписать локальные файлы, файлами из удаленного репозитория то выполните команды:
* *git fetch --all*  
* *git reset --hard github/master*
//  Вместо *github* подставьте название вашего удаленного репозитория, которое вы зарегистрировали командой *git push -u*.




# <a name="com's_git"></a>  4. Коротко-Команды Git в Терминале


##   <a name="com's_git_1"></a>  1) Если Репозиторий Уже создан онлайн на сайте Github
   1. Сначала создаем новый репозиторий на сайте Github
   2. Затем уже на компьюторе в редакторе (например в VSCode) вызываем Terminal и начинаем вводить команды:
### Сreate a new repository on the command line
* *git init*      
// команда для создания папки .git в папке проекта (например с сайтом) на компьюторе    

* *git add .*     
// добавление Всех файлов в папку .git в папке проекта на компьюторе   
  или 
*  *git add README.md*     
// добавление, например файла README в папку .git в папке проекта на компьюторе   

* *git commit -m "first commit"*      
// Создаем **коммит**, добавления названия **коммит** в папку .git в папке проекта на компьюторе    

* *git remote add origin git@github.com:Oxana-S/js-practice.git*  
// Подключаем папку git проекта на компьюторе к удаленному репозиторию на Github    

* *git push -u origin master*     
// Отправляем созданный **коммит** из паки git проекта на компьюторе в удаленный репозиторий на Github    

### Push an existing repository from the command line   
Если (например в редакторе VSCode):  
- Репозиторий уже создан,    
- файлы добавленны в папку .git на компьюторе   
- **коммит** создан и ему присвоено название   
ТОГДА исрользуем только эти команды:

* *git remote add origin git@github.com:Oxana-S/js-practice.git*     
// Подключаем папку git проекта на компьюторе к удаленному репозиторию на Github   

* *git push -u origin master*    
// Отправляем созданный **коммит** из паки git проекта на компьюторе в удаленный репозиторий на Github  

<br>[ОГЛАВЛЕНИЕ](#home)


## <a name="com's_git_2"></a> 2) Cоздание Репозитория на Github удаленно, на компьюторе в Терминале при помощи Hub      
   Есть какой-то проект сайта в какойто папке на компьюторе. На компьюторе в редакторе (например в VSCode) открываем этот проект, вызываем Terminal и начинаем вводить команды:   
### Сreate a new repository on the command line
* *hub init*      
// команда для создания папки .git в папке проекта (например с сайтом) на компьюторе   

* *hub add . && git commit -m "first commit"*      
// добавление Всех файлов в папку .git в папке проекта на компьюторе и создание **коммита**    
  
* *hub create -d "Описание" -h "сайт.ru,если есть"*      
// Создание на компьюторе в терминале  репозитория на Github с названием папки, в которой на компьюторе лежит проект 

* *git commit -m "first commit"*      
// Создаем **коммит**, добавления названия **коммит** в папку .git в папке проекта на компьюторе     

* *hub push -u origin master*     
// Отправляем созданный **коммит** из паки git проекта на компьюторе в созданный из терминала, удаленный репозиторий на Github
<br>
<br>
** <a name="com's_git_3"></a>  Ссылки по Hub:**<br>

<br>[ОГЛАВЛЕНИЕ](#home)


## <a name="com's_git_3"></a> 3) Удаление в Терминале на компьюторе локального Репозитория       

чтобы избежать бесконечных подсказок (и принудительно вызывать команду рекурсивно), введите в командной строке следующее: в папке проекта:   

* *rm -rf .git*   

Затем из той же папки ex-repository, чтобы увидеть, скрыта ли скрытая папка .git:

* *ls -lah*  
// Выведется список всех файлов и папок в директории.  


## <a name="com's_git_4"></a> 4) Работа в Терминале с Ветками

// посмотреть ветки в локольном репозитории   
* *git branch*  
   
// создать ветку в локальном репозитории   
* *git branch -m [новое_имя]*   
  
// – переименовать локальную ветку  
* *git branch -m [old_name_branch]  [new_name_branch]*   
 
// перейти в другую ветку  
* *git checkout [name_branch]*   

// Если мы находимся в какойто ветке можем создать новую ветку:  
* *git checkout -b имя-новой-ветки*   

// удалить ветку из Git   
Сначала мы перемещаемся в главную ветку...
* *git checkout master*   
и уже от туда удаляем   
* *git branch -d [name_branch]*  


// просмотр какие есть удаленные репозитории у пректа:  
* *git remote*  

// можyj также указать ключ -v, чтобы просмотреть адреса для чтения и записи, привязанные к репозиторию:  
* *git remote -v*  

// Просмотр конкретного удаленного репозитория     
* *git remote show [origin]*     

// переименование удалённых репозиториев  
* *git remote rename [old_name] [new_name]*   

// удаление удалённых репозиториев   
git remote rm [имя_репозитория]  

// Добавление удалённых репозиториев   ??? надо разобраться   
* *it remote add <shortname> <url>*  
  пример: git remote add [new_repo] [https://github.com/Oxana-S/github-help]   

// Отправка изменений в удаленный репозиторий (Push)
* *git push <remote-name> <branch-name>*  
  

// Получение изменений из удалённого репозитория — Fetch и Pull  
* *git fetch [remote-name]*  
Важно отметить, что команда git fetch забирает данные в ваш локальный репозиторий, но не сливает их с какими-либо вашими наработками и не модифицирует то, над чем вы работаете в данный момент. Вам необходимо вручную слить эти данные с вашими, когда вы будете готовы.   

* *git pull [url]*   
автоматически получить изменения из удалённой ветки и слить их со своей текущей. 
  









## <a name="com's_git_10"></a>  Полезные ссылки:   
[Ссылка на команды Hub](https://hub.github.com/hub.1.html).       
[Ссылка на форум, ответ на вопрос: Как создать репозиторий на GitHub через командную строку](https://ru.stackoverflow.com/questions/504578/%D0%9A%D0%B0%D0%BA-%D1%81%D0%BE%D0%B7%D0%B4%D0%B0%D1%82%D1%8C-%D1%80%D0%B5%D0%BF%D0%BE%D0%B7%D0%B8%D1%82%D0%BE%D1%80%D0%B8%D0%B9-%D0%BD%D0%B0-github-%D1%87%D0%B5%D1%80%D0%B5%D0%B7-%D0%BA%D0%BE%D0%BC%D0%B0%D0%BD%D0%B4%D0%BD%D1%83%D1%8E-%D1%81%D1%82%D1%80%D0%BE%D0%BA%D1%83).  
[Ссылка на ресурс - hub: USE GITHUB FROM THE COMMAND-LINE](https://hub.github.com/#developer).        
<br>
<br>


**Переводы слов**:<br>
   remote - удаленный<br>
   kommit - совершать <br>
   
[ОГЛАВЛЕНИЕ](#home)
