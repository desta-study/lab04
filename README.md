## Laboratory work III

Данная лабораторная работа посвещена изучению систем контроля версий на примере **Git**.

```bash
$ open https://git-scm.com
```

## Tasks

- [x] 1. Создать публичный репозиторий с названием **lab03** и с лиценцией **MIT**
- [x] 2. Ознакомиться со ссылками учебного материала
- [x]  3. Выполнить инструкцию учебного материала
- [x] 4. Составить отчет и отправить ссылку личным сообщением в **Slack**

## Tutorial

```ShellSession
$ export GITHUB_USERNAME=<имя_пользователя>  # добавляем переменную в среду окружения
$ export GITHUB_EMAIL=<адрес_почтового_ящика>  # добавляем переменную в среду окружения
$ alias edit=<nano|vi|vim|subl>   # переопределяем команду и подставляем в них параметры
```

```ShellSession
$ mkdir lab03 && cd lab03        #создаем новый каталог
$ git init       # запускаем все остальные процессы
$ git config --global user.name ${GITHUB_USERNAME}    # информация об имени и эл. ящике записана в ~/.gitconfig, и будет        применяться автоматически для всех репозиториев текущего пользователя системы.
$ git config --global user.email ${GITHUB_EMAIL}      # информация об имени и эл. ящике записана в ~/.gitconfig, и будет применяться автоматически для всех репозиториев текущего пользователя системы.
$ git config -e --global    # весь список настроек, применяемых для пользовательского репозитория
$ git remote add origin https://github.com/${GITHUB_USERNAME}/lab03   # добавить новый удаленный доступ
$ git pull origin master   #  замерджить все ветки с удаленного репозитория
$ touch README.md       # установка времени последнего изменения файла или доступа в текущее время
$ git status    # показывает статус рабочего дерева
$ git add README.md   #   отслеживает файла README.md
$ git commit -m"added README.md"  # фиксирует изменения, добавленные в staging area
$ git push origin master    #  вталкивает данные текущей ветви в ветвь master удалённого репозитория origin
```

Добавить на сервисе **GitHub** в репозитории **lab03** файл **.gitignore**
со следующем содержимом:

```ShellSession
*build*/
*install*/
*.swp
```

```ShellSession
$ git pull origin master     #  замерджить все ветки с удаленного репозитория
$ git log     # история фиксаций
```

```ShellSession
$ mkdir sources   #создаем новый каталог
$ mkdir include   #создаем новый каталог
$ mkdir examples  #создаем новый каталог
```

Создаем и записываем новый файл printf.cpp в папке sources

```
$ cat > sources/print.cpp <<EOF   # выводит последовательно указанные файлы
#include <print.hpp>

void print(const std::string& text, std::ostream& out) {
  out << text;
}

void print(const std::string& text, std::ofstream& out) {
  out << text;
}
EOF
```


Создаем и записываем новый файл printf.hpp в папке include


```ShellSession
$ cat > include/print.hpp <<EOF   
#include <string>
#include <fstream>
#include <iostream>

void print(const std::string& text, std::ostream& out = std::cout);
void print(const std::string& text, std::ofstream& out);
EOF
```

Создаем и записываем новый файл example1.cpp в папке examples

```ShellSession
$ cat > examples/example1.cpp <<EOF    # выводит последовательно указанные файлы
#include <print.hpp>

int main(int argc, char** argv) {
  print("hello");
}
EOF
```


Создаем и записываем новый файл example2.cpp в папке examples

```ShellSession
$ cat > examples/example2.cpp <<EOF    # выводит последовательно указанные файлы
#include <fstream>
#include <print.hpp>

int main(int argc, char** argv) {
  std::ofstream file("log.txt");
  print(std::string("hello"), file);
}
EOF
```

```ShellSession
$ edit README.md    # редактируем README.md
```

```ShellSession
$ git status    # показывает статус рабочего дерева
$ git add .     # добавляем все файлы и папки текущей директории в index
$ git commit -m"added sources"  # фиксирует изменения, добавленные в staging area
$ git push origin master  #  вталкивает данные текущей ветви в ветвь master удалённого репозитория origin
```

## Report

```ShellSession
$ cd ~/workspace/labs/  # переходим по заданному пути
$ export LAB_NUMBER=03  # включаем в дочерние процессы
$ git clone https://github.com/tp-labs/lab${LAB_NUMBER} tasks/lab${LAB_NUMBER}  # клонируем репозиторий
$ mkdir reports/lab${LAB_NUMBER}    #создаем новый каталог
$ cp tasks/lab${LAB_NUMBER}/README.md reports/lab${LAB_NUMBER}/REPORT.md  # копируем файлы в другие каталоги
$ cd reports/lab${LAB_NUMBER} # переходим по заданному пути
$ edit REPORT.md    # редактируем README.md
$ gistup -m "lab${LAB_NUMBER}"
```

## Links

- [GitHub](https://github.com)
- [Bitbucket](https://bitbucket.org)
- [Gitlab](https://about.gitlab.com)
- [LearnGitBranching](http://learngitbranching.js.org/)

```
Copyright (c) 2017 Братья Вершинины
```
