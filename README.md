# 

# \# Лабораторная работа №6

# 

# \*\*Тема:\*\* Система контроля версий

# 

# \*\*Выполнил:\*\* Фарсиев Р.И.

# 

# \*\*Группа:\*\* 4516

# 

# \## Цель работы

# 

# Изучение базовых возможностей системы управления версиями, получение опыта работы с Git API, локальным и удалённым репозиторием.

# 

# \## Ход выполнения работы

# 

# \### 1. Создание аккаунта GitHub

# 

# Для выполнения лабораторной работы использовался аккаунт GitHub.

# 

# \### 2. Создание Fork репозитория

# 

# Создана личная копия исходного репозитория Kurtyanik/LR6 с помощью функции Fork.

# 

# \[Мой репозиторий](https://github.com/spagettiboi123-cell/LR6)

# 

# \### 3. Установка Git

# 

# Установлена система контроля версий Git для Windows.

# 

# \### 4. Настройка Git

# 

# Выполнена настройка имени пользователя и электронной почты с помощью команды git config.

# 

![Настройка Git (config)](screenshots/04-config.png)

# \### 5. Клонирование репозитория

# 

# Личный репозиторий склонирован на компьютер с помощью git clone. Проверены удалённый адрес и существующие ветки.

# 

![Клонирование репозитория (clone)](screenshots/05-clone.png)

# \### 6. Синхронизация изменений

# 

# Через интерфейс GitHub создан файл test.txt. Изменения загружены в локальный репозиторий командой git pull.

# 

![Синхронизация изменений (pull)](screenshots/06-pull.png)

# \### 7. Просмотр истории операций

# 

# Получена история коммитов веток master и branch1, а также общий граф истории репозитория.

# 

![Просмотр истории операций (log)](screenshots/07-log.png)

# \### 8. Просмотр последних изменений

# 

# С помощью git show просмотрены последние коммиты, а командой git diff изучены различия между ветками.

# 

![Просмотр последних изменений (show)](screenshots/08-show.png)

![Просмотр последних изменений (diff)](screenshots/08-diff.png)

# \### 9. Слияние веток

# 

# Выполнено слияние branch1 в master. Возникший конфликт в mergefile.txt разрешён вручную, после чего создан коммит слияния.

# 

![Слияние веток (conflict)](screenshots/09-conflict.png)

![Слияние веток (merge)](screenshots/09-merge.png)

# \### 10. Удаление побочной ветки

# 

# После успешного слияния удалена удалённая ветка branch1. История её коммитов сохранена.

# 

![Удаление побочной ветки (delete)](screenshots/10-delete.png)

# \### 11. Фиксация изменений

# 

# В файл test.txt последовательно внесены три изменения. Каждое изменение зафиксировано отдельным коммитом.

# 

![Фиксация изменений (commits)](screenshots/11-commits.png)

# \### 12. Откат коммита

# 

# Выполнен откат последнего изменения с использованием git revert. Проверены история коммитов и содержимое файла.

# 

![Откат коммита (revert)](screenshots/12-revert.png)

# \### 13. Создание ветки отчёта

# 

# Создана отдельная ветка report для оформления отчёта.

# 

![Создание ветки отчёта](screenshots/13-report-branch.png)


## Лог выполненных команд

```bash
git config --global user.name "4516 Фарсиев Р.И."
git config --global user.email "spagettiboi123@gmail.com"
git config --global --list

mkdir -p ~/GitLabs
cd ~/GitLabs
git clone https://github.com/spagettiboi123-cell/LR6.git
cd LR6
git remote -v
git branch -a

git pull origin master
ls
git log --oneline -3

git log master --oneline
git log origin/branch1 --oneline
git log --all --oneline --graph --decorate

git show HEAD
git show origin/branch1
git diff master origin/branch1

git status
git merge origin/branch1
git status
git add mergefile.txt
git commit -m "Слияние branch1 в master, разрешение конфликта"

git branch -a
git push origin --delete branch1
git branch -a
git log --oneline --graph --all

git add test.txt
git commit -m "Первое изменение тестового файла"
git add test.txt
git commit -m "Второе изменение тестового файла"
git add test.txt
git commit -m "Третье изменение тестового файла"

git log --oneline -5
git status
git revert --no-edit HEAD
git log --oneline -6
git status

git switch -c report
git branch
git status

git add README.md screenshots/
git commit -m "Начало оформления отчёта по лабораторной работе"
git add README.md screenshots/
git commit -m "Добавлены скриншоты выполнения лабораторной работы"
git status

