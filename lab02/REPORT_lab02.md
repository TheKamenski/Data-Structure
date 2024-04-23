## Laboratory work II

Данная лабораторная работа посвещена изучению систем контроля версий на примере **Git**.

```sh
  ~ ❯ wget https://git-scm.com
--2024-04-18 21:06:54--  https://git-scm.com/
Распознаётся git-scm.com (git-scm.com)… 188.114.99.224, 188.114.98.224, 2a06:98c1:3123:e000::, ...
Подключение к git-scm.com (git-scm.com)|188.114.99.224|:443... соединение установлено.
HTTP-запрос отправлен. Ожидание ответа… 200 OK
Длина: нет данных [text/html]
Сохранение в: «index.html»

index.html           [ <=>      ]   7,14K  --.-KB/s    за 0,001s  

2024-04-18 21:06:54 (7,13 MB/s) - «index.html» сохранён [7313]
```

## Tasks

- [ ] 1. Создать публичный репозиторий с названием **lab02** и с лиценцией **MIT**
- [ ] 2. Сгенирировать токен для доступа к сервису **GitHub** с правами **repo**
- [ ] 3. Ознакомиться со ссылками учебного материала
- [ ] 4. Выполнить инструкцию учебного материала
- [ ] 5. Составить отчет и отправить ссылку личным сообщением в **Slack**


### Решение

```sh
  ~ ❯ export GITHUB_USERNAME=TheKamenski 
  ~ ❯ export GITHUB_EMAIL=k.kamenskiy@gmail.com
  ~ ❯ alias edit=vim

```

```sh
  ~ ❯ source scripts/activate
  ~ ❯ mkdir ~/.config  
  ~ ❯ cat > ~/.config/hub <<EOF
github.com:
- user: ${GITHUB_USERNAME}
  oauth_token: ${GITHUB_TOKEN}
  protocol: https
EOF

  ~ ❯ git config --global hub.protocol https  
```
Done

```sh
  ~ ❯ mkdir projects/lab02 && cd projects/lab02
  ~/Data-Structure   main ?2 ❯ git init              
Переинициализирован существующий репозиторий Git в /home/konstantin/Data-Structure/.git/
  ~/Data-Structure   main ?2 ❯ git config --global user.name ${GITHUB_USERNAME}
  ~/Data-Structure   main ?2 ❯  git config --global user.email ${GITHUB_EMAIL}
  ~/Data-Structure   main ?2 ❯ git config -e --global
  ~/Data-Structure   main ?2 ❯ git remote add origin https://github.com/$\{GITHUB_USERNAME\}/lab02.git
error: внешний репозиторий origin уже существует
  ~/Data-Structure   main ?2 ❯ git pull origin master

  ~/Data-Structure   main ?2 ❯ touch README.md
  ~/Data-Structure   main ?3 ❯ git status            
Текущая ветка: main
Эта ветка соответствует «origin/main».

Неотслеживаемые файлы:
  (используйте «git add <файл>...», чтобы добавить в то, что будет включено в коммит)
	.gitignor
	README.md
	lab02/

индекс пуст, но есть неотслеживаемые файлы
(используйте «git add», чтобы проиндексировать их)
  ~/Data-Structure   main ?3 ❯ git add README.md      
  ~/Data-Structure   main +1 ?2 ❯ git commit -m "added README.md"
[main 2f55af8] added README.md
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 README.md
  ~/Data-Structure   main ⇡1 ?2 ❯ git push origin master 

```

## Создали .gitignore, записали через vim:

```sh
  ~/Data-Structure/lab02   main ⇡1 ?2 ❯ touch .gitignore
  ~/Data-Structure/lab02   main ⇡1 ?2 ❯ vim .gitignore
  ~/Data-Structure/lab02   main ⇡1 ?2 ❯ vim .gitignore         1m 13s

```


```sh
  ~/Data-Structure/lab02   main ⇡1 ?2 ❯ mkdir sources
  ~/Data-Structure/lab02   main ⇡1 ?2 ❯ mkdir include
  ~/Data-Structure/lab02   main ⇡1 ?2 ❯ mkdir examples
  ~/Data-Structure/lab02   main ⇡1 ?2 ❯ cat > sources/print.cpp <<EOF
#include <print.hpp>

void print(const std::string& text, std::ostream& out)
{
  out << text;
}

void print(const std::string& text, std::ofstream& out)
{
  out << text;
}
EOF

```

```sh
  ~/Data-Structure/lab02   main ⇡1 ?2 ❯ cat > examples/example1.cpp <<EOF
#include <print.hpp>

int main(int argc, char** argv)
{
  print("hello");
}
EOF

```

```sh
  ~/Data-Structure/lab02   main ⇡1 ?2 ❯ cat > examples/example2.cpp <<EOF
#include <print.hpp>

#include <fstream>

int main(int argc, char** argv)
{
  std::ofstream file("log.txt");
  print(std::string("hello"), file);
}
EOF

```

## Пушим в git

```sh
$ git status
$ git add .
$ git commit -m"added sources"
$ git push origin master
```

## Report

```sh
$ cd ~/workspace/
$ export LAB_NUMBER=02
$ git clone https://github.com/tp-labs/lab${LAB_NUMBER}.git tasks/lab${LAB_NUMBER}
$ mkdir reports/lab${LAB_NUMBER}
$ cp tasks/lab${LAB_NUMBER}/README.md reports/lab${LAB_NUMBER}/REPORT.md
$ cd reports/lab${LAB_NUMBER}
$ edit REPORT.md
$ gist REPORT.md
```


