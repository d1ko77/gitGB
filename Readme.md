# Инструкция для работы с Git и удалёнными репозиториями

## Что такое Git?
Git - это одна из реализаций распределённых систем контроля версий, имеющая как и локальные, так и удалённые репозитории. Является самой популярной реализацией систем контроля версий в мире.

## Настройка Git
Вы установили себе Git. Давайте теперь его настроим, чтобы когда вы создавали снимок проекта, указывался автор.
Открываем терминал (Linux и MacOS) или консоль (Windows) и вводим следующие команды.

***git config --global user.name "ваше_имя"***

***git config --global user.email "адрес_почты@email.com"***

## Подготовка репозитория

Обычно вы получаете репозиторий Git одним из двух способов:

Вы можете взять локальный каталог, который в настоящее время не находится под версионным контролем, и превратить его в репозиторий Git, либо вы можете клонировать существующий репозиторий Git из любого места.
В обоих случаях вы получите готовый к работе Git репозиторий на вашем компьютере.

Создание репозитория в существующем каталоге. Если у вас уже есть проект в каталоге, который не находится под версионным контролем Git, то для начала нужно перейти в него. Если вы не делали этого раньше, то для разных операционных систем это выглядит по-разному:

![](.git/opera_oXsG2d0tKv.png)

Для создание репозитория необходимо выполнить команду ***git init***  в папке с репозиторием и у Вас создаться репозиторий (появится скрытая папка .git)
![](.git/explorer_Zb4G6EHM8g.png)


## Создание коммитов

Итак, у вас имеется настоящий Git-репозиторий и рабочая копия файлов для некоторого проекта. Вам нужно делать некоторые изменения и фиксировать *«снимки»* состояния (snapshots) этих изменений в вашем репозитории каждый раз, когда проект достигает состояния, которое вам хотелось бы сохранить.

Запомните, каждый файл в вашем рабочем каталоге может находиться в одном из двух состояний, под версионным контролем **(отслеживаемые)** и нет **(неотслеживаемые)**: 

* Отслеживаемые файлы — это те файлы, которые были в последнем снимке состояния проекта; они могут быть неизменёнными, изменёнными или подготовленными к коммиту. Если кратко, то отслеживаемые файлы — это те файлы, о которых знает Git.

* Неотслеживаемые файлы — это всё остальное, любые файлы в вашем рабочем каталоге, которые не входили в ваш последний снимок состояния и не подготовлены к коммиту. Когда вы впервые клонируете репозиторий, все файлы будут отслеживаемыми и неизменёнными, потому что Git только что их извлек и вы ничего пока не редактировали.

Как только вы отредактируете файлы, Git будет рассматривать их как изменённые, так как вы изменили их с момента последнего коммита. Вы индексируете эти изменения, затем фиксируете все проиндексированные изменения, а затем цикл повторяется.

![](.git/lifecycle.png)

### Git add
Для добавления измений в коммит используется команда ***git add***. Чтобы использовать команду ***git add*** напишите ***git add <имя файла>***, данная команда действует только для одного определенного файла, для того чтобы добавить все файлы нужно ввести комманду ***git add .***

### Просмотр состояния репозитория
Для того, чтобы посмотреть состояние репозитория используется команда ***git status***. Для этого необходимо в папке с репозиторием написать ***git status***, и вы увидите были ли измения в файлах, или их не было. Также можно ввести комманду ***git status -s*** или ***git status --short***, чтобы посмотреть изменения в более компактном виде.

### Создание коммитов
Для того, чтобы создать коммит(сохранение) необходимо выполнить команду ***git commit***. Выполняется она так: ***git commit -m "<сообщение к коммиту>***. Все файлы для коммита должны быть ***ДОБАВЛЕНЫ*** и сообщение к коммиту писать ***ОБЯЗАТЕЛЬНО***.

### Перемещение между сохранениями
Для того, чтобы перемещаться между коммитами, используется команда ***git checkout***. Используется она в папке с пепозиторием следующим образом: ***git checkout <номер коммита>***

### Журнал изменений
Для того, чтобы посмтреть все сделанные изменения в репозитории, используется команда ***git log***. Для этого достаточно выполнить команду ***git log*** в папке с репозиторием.

 Больше информации по теме  **создание коммитов** по ссылке: [Нажмите сюда](https://webdevkin.ru/courses/git/git-commit)

## Ветки в Git 

Почти каждая система контроля версий (СКВ) в какой-то форме поддерживает ветвление. Используя ветвление, Вы отклоняетесь от основной линии разработки и продолжаете работу независимо от неё, не вмешиваясь в основную линию. Во многих СКВ создание веток — это очень затратный процесс, часто требующий создания новой копии каталога с исходным кодом, что может занять много времени для большого проекта.

Некоторые люди, говоря о модели ветвления Git, называют ее «киллер-фича», что выгодно выделяет Git на фоне остальных СКВ. Что в ней такого особенного? Ветвление Git очень легковесно: 
* Операция создания ветки выполняется почти мгновенно, переключение между ветками туда-сюда, обычно, также быстро. 
* В отличие от многих других СКВ, Git поощряет процесс работы, при котором ветвление и слияние выполняется часто, даже по несколько раз в день. 
* Понимание и владение этой функциональностью дает вам уникальный и мощный инструмент, который может полностью изменить привычный процесс разработки.

## Создание ветки

Для того, чтобы создать ветку, используется команда ***git branch***. Делается это следующим образом в папке с репозиторием: ***git branch <название новой ветки>***

## Просмотр всех веток 

Для того чтобы посмотреть сколько веток у вас в наличии, нужно ввести комманду ***git branch***

## Переключение между ветками
Для этого используется команда ***git checkout <название ветки>***
Обратите внимание, если у вас есть незакоммиченные изменения, то переключиться на другую ветку не получится - git за этим следит

![](.git/opera_herBlyLpMi.png)

Поэтому сначала или закоммитьте изменения в ветке, или откатите эти изменения - а уже потом переключайтесь. Это может показаться странным, но так сделано для безопасности, чтобы случайно не потерять информацию.

## Слияние веток

Что такое мердж или слияние веток - это перенос кода из одной ветки в другую. Например, когда мы заканчиваем работу над веткой, например, сделали новый функционал или поправили багу, мы сливаем ее в мастер. В мастере код проверяется еще раз и выкладывается на боевой сервер.

Сливать друг в друга можно любые ветки. Технически, с точки зрения git нет никакой разницы, сливается ветка с новым функционалом в мастер или наоборот. Для нас мастер - это основная ветка разработки, а для git это просто ветка.

Для того чтобы добавить ветку в текущую ветку используется команда ***git merge <название ветки>***

## Удаление веток

Чтобы удалиdadть локальную ветку в Git нужно выполнить команду (вместо 'name branch' необходимо поставить название ветки, которую вы хотите удалить):

***"git branch -d 'name branch'"***

Обратите внимание на то, что ветка, которую вы удаляете, не должна быть вашей текущей веткой, в которой вы работаете, иначе отобразится ошибка вида:

    error: Cannot delete branch ’mybranch’ checked out at ’/path/to

Поэтому, если вам нужно удалить текущую ветку, то сначала нужно переключиться на какую-либо другую ветку, а только потом выполнять удаление.

Если вдруг возникает ошибка: 

    The branch ’mybranch’ is not fully merged. If you are sure you want to delete it 

и вы по прежнему хотите удалить ветку, то для принудительного удаления ветки можно воспользоваться опцией -D:

***git branch -D mybranch***
