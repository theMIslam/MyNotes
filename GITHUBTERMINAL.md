---

git reset --hard +hash commit = удалить коммит`

git branch название ветки  = создать ветку
git checkout название ветки = переключится на ветку
git branch -d название ветки = удалить локальную ветку

git remote -v = узнать к какому репозиторию подключен проект

git remote set-url origin "ссылка на нужный репозиторий" - обновить привязанный репозиторий 

git update-ref -d HEAD удалени первого единственного коммита 

git commit --amend -m "Новое название последнего коммита" = переименовать последний коммит

git config --global user.name "My Name"

git config --global user.email myEmail@example.com

wq выйти из vim terminal

## Здесь понять как использовать <>?
git commit --amend --author="Author Name < <email@address.com> >" --no-edit = изменить автора последнего коммита 

$ git checkout master
    $ git merge <name branch>

git push origin --delete <branch name> = удалить ветки на сервере
git push origin --all = запушить все локальные ветки

git checkout -b имя новой ветки = создать новую ветку и перейти на неё

git log = посмотреть все коммиты 
git branch = посмотреть все ветки

---
git status посмотреть всё

git remote remove origin = отвязать проект от удаленного репозитория
git reset . = отмена проиндексированных файлов

git rm -r --cached . = очистить индекс

---
