## Laboratory work I

Данная лабораторная работа посвещена изучению утилит для разработки проектов

## Выполнение работы

```bash
  ~ ❯ export GITHUB_USERNAME=TheKamenski 
  ~ ❯ alias edit=vim
```

```sh
  ~ ❯ mkdir -p ${GITHUB_USERNAME}/workspace                             
  ~ ❯ cd ${GITHUB_USERNAME}/workspace
  ~/TheKamenski/workspace ❯ pwd   
/home/konstantin/TheKamenski/workspace
  ~/TheKamenski/workspace ❯ cd ..                          
  ~/TheKamenski ❯ pwd
/home/konstantin/TheKamenski

```

```sh
  ~/TheKamenski ❯ mkdir -p workspace/tasks/            
  ~/TheKamenski ❯ mkdir -p workspace/projects/
  ~/TheKamenski ❯ mkdir -p workspace/reports/ 
  ~/TheKamenski ❯ cd workspace
  ~/TheKamenski/workspace ❯ 
```

```sh
  ~/TheKamenski/workspace ❯ wget https://nodejs.org/dist/v6.11.5/node-v6.11.5-linux-x64.tar.xz
--2024-04-18 20:29:24--  https://nodejs.org/dist/v6.11.5/node-v6.11.5-linux-x64.tar.xz
Распознаётся nodejs.org (nodejs.org)… 104.20.22.46, 104.20.23.46, 2606:4700:10::6814:172e, ...
Подключение к nodejs.org (nodejs.org)|104.20.22.46|:443... соединение установлено.
HTTP-запрос отправлен. Ожидание ответа… 200 OK
Длина: 9356460 (8,9M) [application/x-xz]
Сохранение в: «node-v6.11.5-linux-x64.tar.xz»

node-v6.11.5-linux- 100%[===================>]   8,92M  13,9MB/s    за 0,6s    

2024-04-18 20:29:26 (13,9 MB/s) - «node-v6.11.5-linux-x64.tar.xz» сохранён [9356460/9356460]

  ~/TheKamenski/workspace ❯ tar -xf node-v6.11.5-linux-x64.tar.xz
  ~/TheKamenski/workspace ❯ rm -rf node-v6.11.5-linux-x64.tar.xz
  ~/TheKamenski/workspace ❯ mv node-v6.11.5-linux-x64 node
```

```sh
  ~/TheKamenski/workspace ❯ ls node/bin
node  npm
  ~/TheKamenski/workspace ❯ echo ${PATH}                       
/home/konstantin/.local/bin:/home/konstantin/bin:/usr/local/bin:/usr/local/sbin:/usr/bin:/usr/sbin
  ~/TheKamenski/workspace ❯  export PATH=${PATH}:`pwd`/node/bin
  ~/TheKamenski/workspace ❯ echo ${PATH}
/home/konstantin/.local/bin:/home/konstantin/bin:/usr/local/bin:/usr/local/sbin:/usr/bin:/usr/sbin:/home/konstantin/TheKamenski/workspace/node/bin
  ~/TheKamenski/workspace ❯ mkdir scripts
  ~/TheKamenski/workspace ❯ cat > scripts/activate<<EOF
export PATH=\${PATH}:`pwd`/node/bin
EOF
  ~/TheKamenski/workspace ❯ source scripts/activate
  ~/TheKamenski/workspace ❯ 
```


```sh
  ~/TheKamenski/workspace ❯  gem install gist 
Fetching gist-6.0.0.gem
Successfully installed gist-6.0.0
Parsing documentation for gist-6.0.0
Installing ri documentation for gist-6.0.0
Done installing documentation for gist after 0 seconds
1 gem installed

A new release of RubyGems is available: 3.4.10 → 3.5.9!
Run `gem update --system 3.5.9` to update your installation.

```

```sh
  ~/TheKamenski/workspace ❯ (umask 0077 && echo ${GIST_TOKEN} > ~/.gist)
```

##Report

```sh
  ~/TheKamenski/workspace ❯ export LAB_NUMBER=01
  ~/TheKamenski/workspace ❯ git clone https://github.com/tp-labs/lab$\{LAB_NUMBER\} tasks/lab${LAB_NUMBER}
Клонирование в «tasks/lab01»...
remote: Repository not found.
fatal: repository 'https://github.com/tp-labs/lab${LAB_NUMBER}/' not found
  ~/TheKamenski/workspace ❯ mkdir reports/lab${LAB_NUMBER}
  ~/TheKamenski/workspace ❯ cp tasks/lab${LAB_NUMBER}/README.md reports/lab${LAB_NUMBER}/REPORT.md 
  ~/TheKamenski/workspace ❯ cd reports/lab${LAB_NUMBER} 
  ~/T/w/reports/lab01 ❯ edit REPORT.md
  ~/T/w/r/lab01 ❯ gist REPORT.md
```
