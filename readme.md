# Заметки по Git и GitHub, включая работу в VS Code

## Содержание
* [Вступление](#вступление)
* [Установка и базовые настройки](#установка-и-базовые-настройки)
* [Начало работы](#начало-работы)

## Вступление
[Вернуться к содержанию](#содержание)

Данный файл написан для напоминания себе команд git если я их забуду. Возможно, этот файл поможет освоить git людям, которые только начинают работать с ним. Как я :wink:. 

Информация по git написана на основе [курса Наиля Алишева на Udemy](https://www.udemy.com/course/git-alishev/).

## Установка и базовые настройки
[Вернуться к содержанию](#содержание)

**Скачиваем** дистрибутив git'а для Windows [здесь](https://gitforwindows.org/).
При установке обязательно отметь галочку напротив GIT bash, чтобы его тоже поставить.

После установки нужно провести базовые настройки:
1. Открываем **git bash** (ПКМ на папке какой-нибудь, например, Рабочий стол :no_good:, если папка проекта еще не создана. Если создана, то открываем в ней и шаги 5 и 6 пропускаем).
2. Устанавливаем свое имя (имя указывай в кавычках):
```
git config --global user.name "Имя"
```
3. Устанавливаем почту (почту указывай без кавычек):
```
git config --global user.email example@ex.com
```
4. Включаем цвета (может быть уже включено):
```
git config --global color.ui true
```
5. Создаем папку проекта (если в названии папки есть пробел, то тогда имя папки пишем в кавычках):
```
mkdir название_проекта
```
6. Переходим в эту папку (также, в кавычках имя папки если в имени папки есть пробел)
```
cd название_проекта/
```
7. <span id="git-inizialization">_Выполняем инициализацию git репозитория_</span> (тогда появится скрытая папка .git в папке проекта и эта папка проекта будет работать с git):
```
git init
```

#### Дополнительные заметки:
1. **ВАЖНО!** Смотри, чтобы в git bash ты был в папке проекта перед тем как писать `git init` на 7м шаге.
2. На первом шаге git bash открывается из любой папки. Тогда в папку проекта можно перейти командой `cd имя_нужной_папки`. Но проще сразу зайти через Проводник или файловый менеджер в папку проекта и оттуда через контекстное меню (ПКМ) вызвать git bash - так в git bash будет открыта сразу папка проекта и никуда не нужно будет переходить командой `cd`. Можно пропустить шаги 5 и 6 если открыть git bash сразу в папке проекта (если она уже создана).

## Начало работы
[Вернуться к содержанию](#содержание)

Общий принцип добавления файлов и учет изменений после создания папки проекта и [инициализации git](#git-inizialization) в папке проекта такой:

1. Создаем новый файл. На этом этапе он еще не отслеживается git'ом и имеет статус **untracked**. Т.е. git не будет сохранять изменения этого файла, он его не воспринимает. После создания файла можно проверить статус репозитория (папки). Там должно быть указан список файлов, которые не отслеживаются. 
```
git status
```
2. Добавляем файл для отслеживания (имя файла в кавычках, если в нем есть пробелы). Если файл только создан и добавлен командой `git add`, то он сразу имеет статус **staged changes**. Это состояние, когда изменения готовы к коммиту (про коммиты позже), После изменений нужно будет всегда указывать `git add`, чтобы перевести файл в состояние **staged changes**:
```
git add имя_фалйа
```
3. Далее, когда файлы добавлены к отслеживанию, сохранены, получили статус **staged changes**, можно делать коммит. Здесь флаг `-m` говорит о том, что дальше у коммита будет сообщение. Это обязательно надо делать.
```
git commit -m "сообщение"
```
4. После можно опять проверить статус репозитория командой `git status` и увидеть, что ничего нет для коммита, нет изменений и т.д.
5. Дополнительно можно посмотреть список всех коммитов в репозитории:
```
git log
```
<!-- TODO Сделай еще сслыку на то, как в VS code эти статусы отображаются. -->
Здесь принцип измененя статусов следующий:
Что я сделал | Команда git | Статус файла
- | - | -
Инициализировал репозиторий | `git init` | -
Создал файл в Проводнике | - | untracked
Добавил файл для отслеживания | `git add имя_файла` | Staged changes
Сделал коммит | `git commit -m "Сообщение"` | -
Вношу изменения в файл и сохраняю его, потом проверяю статус | `git status` | modified *
\* - в VS Code в окне Source Control эти изменения будут отмечены в пункте Changes. Это значит, что в файле есть изменения по сравнению с версией файла из предыдущего коммита. 
<!-- TODO Добавить картинок про VS Code -->

#### Дополнительные заметки:
**Commit** (коммит) - это как сохранение в игре. В любом месте можно сохранить игру и потом в любой момент можно начать с этого сохранения. Также и тут. Делается слепок / снимок репозитория, и ты можешь потом к нему вернуться.