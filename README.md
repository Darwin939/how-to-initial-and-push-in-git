# how-to-initial-and-push-in-git


Упражнение 1. Git

Пройдите туториал и продемонстрируйте преподавателю тестовый репозиторий на гитхабе.

1. Зарегистрируйтесь на github.com с некоторым именем пользователя, например Ivanov (тут и далее вместо Ivanov нужно подставлять имя вашего пользователя, а вместо ivanov.ivan@phystech.edu вашу настоящую почту).

    Создаем новый репозиторий https://github.com/new (или значок + в правом верхнем углу):
        В качестве имени репозитория задаем infa_2019_ivanov
        Доступ оставляем Public
        Не забываем поставить галочку "Initialize this repository with a README"

3. Откройте терминал (консоль) GNU/Linux или командную строку Git-bash под M$ Windows. Теперь git clone — склонируем получившийся репозиторий на свой компьютер и зайдем в папку с репозиторием:

$ git clone https://github.com/Ivanov/infa_2019_ivanov
Cloning into 'infa_2019_ivanov'...
remote: Counting objects: 3, done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), done.
$ ls
infa_2019_ivanov
$ cd infa_2019_ivanov
$ ls
README.md

Не забудем сконфигурить гит, представившись ему (это обязательно нужно сделать находясь в папке infa_2019_ivanov):

git config user.name "Ivanov Ivan"
git config user.email ivanov.ivan@phystech.edu

Почту указываем как при регистрации.

4. Теперь у нас локально есть полная и независимая версия нашего репозитория infa_2019_ivanov. Она никак явным образом не связана с версией на серверах github'а, однако в гите существуют инструменты для обмена данными между разными репозиториями. Иными словами, git - это распределенная система управлениями версиями.

    Команда git log возвращает историю нашего репозитория. В данный момент в нашей истории ровно один коммит (коммит - это некоторый набор изменений).

-> git log
commit eec733a21cerfb66973998a9327aab735fa40ba4
Author: Ivanov <ivanov.ivan@phystech.edu>
Date:   Wed Nov 9 13:36:38 2016 +0300

    Initial commit

6. Давайте отредактируем файл README.md и добавим в него что-нибудь. Откроем файл README.md и напишем в нем что-нибудь. После с помощью git diff посмотрим на текущие изменения. В диффе видно, что была добавлена строчка "it's test project".

-> git diff
diff --git a/README.md b/README.md
index 21e60f8..285eafa 100644
--- a/README.md
+++ b/README.md
@@ -1 +1,3 @@
-# infa_2019_ivanov
\ No newline at end of file
+# infa_2019_ivanov
+
+it's test project

7. Команда git status показывает текущий статус репозитория. Мы видим, что сейчас мы находимся в ветке master (основная ветка нашего репозитория). Ниже написано, что файл README.md был изменен. Однако он ещё не готов для коммита.

-> git status
# On branch master
# Changes not staged for commit:
#   (use "git add <file>..." to update what will be committed)
#   (use "git checkout -- <file>..." to discard changes in working directory)
#
#    modified:   README.md
#
no changes added to commit (use "git add" and/or "git commit -a")

    Сделаем git add, как рекомендует нам команда status.

-> git add README.md
-> git status
# On branch master
# Changes to be committed:
#   (use "git reset HEAD <file>..." to unstage)
#
#    modified:   README.md
#

Теперь git status показывает, что изменения в файле README.md готовы для коммита. Если сейчас снова измененить README.md, то нужно снова обязательно выполнить git add.

    git-commit — закоммитим наши изменения, то есть внесём "квант" изменений в историю развития проекта:

$ git commit -m "Added something to README"
[master 274f6d5] Added something to README
 Committer: Ivanov Ivan <ivanov.ivan@phystech.edu>

 1 file changed, 3 insertions(+), 1 deletion(-)

    Снова посмотрим (git log) на историю нашего репозитория:

$ git log
commit 8e2642d512b11ae43a97b0b4ac68e802d2626f14
Author: Ivanov Ivan <ivanov.ivan@phystech.edu>
Date:   Wed Nov 9 14:47:40 2016 +0300

    Added something to README

commit eec733a21cerfb66973998a9327aab735fa40ba4
Author: Ivanov Ivan <ivanov.ivan@phystech.edu>
Date:   Wed Nov 9 13:36:38 2016 +0300

    Initial commit

Теперь в нашем репозитории два коммита.

    Давайте сделаем git push — отправим ("запушим" на сленге программистов) наши изменения в оригинальный репозиторий на github.com.

$ git push
Username for 'https://github.com': <username>
Password for 'https://ivanov@github.com': <password>
To https://github.com/Ivanov/infa_2019_ivanov
   eec733a..8e2642d  master -> master

При git push необходимо будет ввести логин и пароль на GitHub (если, конечно, вы не настроили ssh-аутентификацию :-)). Теперь изменения будут доступны для всех.

    Существует парная команда git pull — которая забирает изменения с оригинального репозитория на сервере.

$ git pull
Already up-to-date.

