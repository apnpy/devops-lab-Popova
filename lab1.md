## Изучение основ Docker

Установила Docker на свой компьютер и перешла в аккаунт

Проверила установку командой docker --version:

(base) maks_nekrasovmail.ru@Mac ~ % docker --version
Docker version 29.2.1, build a5c7197
Запустила тестовый контейнер: docker run hello-world



(base) maks_nekrasovmail.ru@Mac ~ % docker run hello-world
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
198f93fd5094: Pull complete 
Digest: sha256:ef54e839ef541993b4e87f25e752f7cf4238fa55f017957c2eb44077083d7a6a
Status: Downloaded newer image for hello-world:latest
Hello from Docker!
This message shows that your installation appears to be working correctly.
To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (arm64v8)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.
To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash
Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/
For more examples and ideas, visit:
 https://docs.docker.com/get-started/

Изучила базовые команды: docker images, docker ps, docker ps -a:
Команда docker images в командной строке показывает список всех Docker-образов, которые сохранены локально на компьютере

(base) maks_nekrasovmail.ru@Mac ~ % docker images
                                                            i Info →   U  In Use
IMAGE                           ID             DISK USAGE   CONTENT SIZE   EXTRA
hello-world:latest              ca9905c726f0        5.2kB             0B    U   
mcr.microsoft.com/azure-sql-edge:latest
                                9d0e27694fc9       1.84GB             0B    U   
mysql:latest                    c7c54c29e20d        544MB             0B        


Команда docker ps показывает список запущенных контейнеров Docker. В данном случае запущенные контейнеры отсутствуют.

(base) maks_nekrasovmail.ru@Mac ~ % docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES

Команда docker ps -a показывает все контейнеры Docker, которые есть на компьютере — и запущенные, и остановленные. Такие контейнеры имеются на машине. (Например hello world был запущен и завершился)

(base) maks_nekrasovmail.ru@Mac ~ % docker ps -a
CONTAINER ID   IMAGE                              COMMAND                  CREATED          STATUS                      PORTS                              NAMES
3e298c9edb64   hello-world                        "/hello"                 32 seconds ago   Exited (0) 31 seconds ago                                      modest_wiles
1f6335c5e6f1   mcr.microsoft.com/azure-sql-edge   "/opt/mssql/bin/perm…"   2 years ago      Exited (255) 2 years ago    1401/tcp, 0.0.0.0:1433->1433/tcp   sql

## Работа с готовыми образами

Скачала образ Ubuntu
Образ Ubuntu в Docker - это Docker-образ, содержащий минимальную операционную систему Ubuntu (Linux), подготовленную для запуска внутри контейнера.

(base) maks_nekrasovmail.ru@Mac ~ % docker pull ubuntu:latest
latest: Pulling from library/ubuntu
66a4bbbfab88: Pull complete 
Digest: sha256:d1e2e92c075e5ca139d51a140fff46f84315c0fdce203eab2807c7e495eff4f9
Status: Downloaded newer image for ubuntu:latest
docker.io/library/ubuntu:latest
What's next:
    View a summary of image vulnerabilities and recommendations → docker scout quickview ubuntu:latest
Запустила интерактивный контейнер

(base) maks_nekrasovmail.ru@Mac ~ % docker run -it ubuntu bash
root@896b491051df:/# 
Установила пакет curl

root@896b491051df:/# apt update && apt install -y curl
Сначала обновляется список доступных пакетов - затем, если все прошло успешно устанавливается программа curl (утилита для отправки HTTP-запросов из терминала)

Проверила установку пакета curl - выполнена успешно

root@896b491051df:/# curl --version
curl 8.5.0 (aarch64-unknown-linux-gnu) libcurl/8.5.0 OpenSSL/3.0.13 zlib/1.3 brotli/1.1.0 zstd/1.5.5 libidn2/2.3.7 libpsl/0.21.2 (+libidn2/2.3.7) libssh/0.10.6/openssl/zlib nghttp2/1.59.0 librtmp/2.3 OpenLDAP/2.6.10
Release-Date: 2023-12-06, security patched: 8.5.0-2ubuntu10.7
Protocols: dict file ftp ftps gopher gophers http https imap imaps ldap ldaps mqtt pop3 pop3s rtmp rtsp scp sftp smb smbs smtp smtps telnet tftp
Features: alt-svc AsynchDNS brotli GSS-API HSTS HTTP2 HTTPS-proxy IDN IPv6 Kerberos Largefile libz NTLM PSL SPNEGO SSL threadsafe TLS-SRP UnixSockets zstd

Вышла из контейнера

root@896b491051df:/# exit
exit

## Запуск веб-сервера

Запустила контейнер с nginx

(base) maks_nekrasovmail.ru@Mac ~ % docker run -d -p 8080:80 --name web-server nginx:alpine
Unable to find image 'nginx:alpine' locally
alpine: Pulling from library/nginx
d8ad8cd72600: Pull complete 
c5ad07fbd6e6: Pull complete 
31d394b0c9ed: Pull complete 
9084d2ffc283: Pull complete 
821790ca706f: Pull complete 
7833e4e4252c: Pull complete 
88799a707571: Pull complete 
da8475fa07c7: Pull complete 
Digest: sha256:1d13701a5f9f3fb01aaa88cef2344d65b6b5bf6b7d9fa4cf0dca557a8d7702ba
Status: Downloaded newer image for nginx:alpine
7bc597e320d0d88d96c0c53edfc06d6ec1c097417a9744fa3390173babcb0cf0

Докер скачал образ nginx:alpine, создал контейнер web-server, запустил внутри nginx. Теперь по адресу http://localhost:8080 станет доступен сайт.
При переходе по ссылке http://localhost:8080/ открывается страница

Посмотрела логи веб сервера:
(base) maks_nekrasovmail.ru@Mac ~ % docker logs web-server
/docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
/docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
/docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
10-listen-on-ipv6-by-default.sh: info: Getting the checksum of /etc/nginx/conf.d/default.conf
10-listen-on-ipv6-by-default.sh: info: Enabled listen on IPv6 in /etc/nginx/conf.d/default.conf
/docker-entrypoint.sh: Sourcing /docker-entrypoint.d/15-local-resolvers.envsh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/30-tune-worker-processes.sh
/docker-entrypoint.sh: Configuration complete; ready for start up
2026/03/06 21:18:12 [notice] 1#1: using the "epoll" event method
2026/03/06 21:18:12 [notice] 1#1: nginx/1.29.5
2026/03/06 21:18:12 [notice] 1#1: built by gcc 15.2.0 (Alpine 15.2.0) 
2026/03/06 21:18:12 [notice] 1#1: OS: Linux 6.12.72-linuxkit
2026/03/06 21:18:12 [notice] 1#1: getrlimit(RLIMIT_NOFILE): 1048576:1048576
2026/03/06 21:18:12 [notice] 1#1: start worker processes
2026/03/06 21:18:12 [notice] 1#1: start worker process 30
2026/03/06 21:18:12 [notice] 1#1: start worker process 31
2026/03/06 21:18:12 [notice] 1#1: start worker process 32
2026/03/06 21:18:12 [notice] 1#1: start worker process 33
2026/03/06 21:18:12 [notice] 1#1: start worker process 34
2026/03/06 21:18:12 [notice] 1#1: start worker process 35
2026/03/06 21:18:12 [notice] 1#1: start worker process 36
2026/03/06 21:18:12 [notice] 1#1: start worker process 37
192.168.65.1 - - [06/Mar/2026:21:30:54 +0000] "GET / HTTP/1.1" 200 615 "-" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/145.0.0.0 Safari/537.36" "-"
2026/03/06 21:30:54 [error] 30#30: *1 open() "/usr/share/nginx/html/favicon.ico" failed (2: No such file or directory), client: 192.168.65.1, server: localhost, request: "GET /favicon.ico HTTP/1.1", host: "localhost:8080", referrer: "http://localhost:8080/"
192.168.65.1 - - [06/Mar/2026:21:30:54 +0000] "GET /favicon.ico HTTP/1.1" 404 555 "http://localhost:8080/" "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/145.0.0.0 Safari/537.36" "-"

В логах можем увидеть успешный запуск контейнера, а также, что был выполнен запрос (я перешла на страницу браузера)
После этого, я подключилась к контейнеру

(base) maks_nekrasovmail.ru@Mac ~ % docker exec -it web-server sh
/ # 

После этого я уже нахожусь внутри контейнера и могу выполнять команды Linux.
Для дальнейшего выполнения работ выйдем из контейнера, выполнив запрос  “exit”

## Управление контейнерами

Просмотрела запущенные контейнеры

(base) maks_nekrasovmail.ru@Mac ~ % docker ps
CONTAINER ID   IMAGE          COMMAND                  CREATED          STATUS          PORTS                                     NAMES
7bc597e320d0   nginx:alpine   "/docker-entrypoint.…"   22 minutes ago   Up 22 minutes   0.0.0.0:8080->80/tcp, [::]:8080->80/tcp   web-server

Запущен 1 контейнер nginx:alpina (web server)

Просмотрим все контейнеры: docker ps -a


(base) maks_nekrasovmail.ru@Mac ~ % docker ps -a
CONTAINER ID   IMAGE                              COMMAND                  CREATED          STATUS                         PORTS                                     NAMES
7bc597e320d0   nginx:alpine                       "/docker-entrypoint.…"   24 minutes ago   Up 24 minutes                  0.0.0.0:8080->80/tcp, [::]:8080->80/tcp   web-server
896b491051df   ubuntu                             "bash"                   2 hours ago      Exited (0) About an hour ago                                             hardcore_raman
3e298c9edb64   hello-world                        "/hello"                 2 hours ago      Exited (0) 2 hours ago                                                   modest_wiles
1f6335c5e6f1   mcr.microsoft.com/azure-sql-edge   "/opt/mssql/bin/perm…"   2 years ago      Exited (255) 2 years ago       1401/tcp, 0.0.0.0:1433->1433/tcp          sql
Остановим контейнер: docker stop web-server


(base) maks_nekrasovmail.ru@Mac ~ % docker stop web-server
web-server

Страница недоступна: 
Перезапустим контейнер

(base) maks_nekrasovmail.ru@Mac ~ % docker start web-server
web-server

Страница снова доступна
Удалим контейнер

(base) maks_nekrasovmail.ru@Mac ~ % docker rm web-server
Error response from daemon: cannot remove container "web-server": container is running: stop the container before removing or force remove

Система не дает удалить контейнер, так как он запущен - остановим контейнер и снова попробуем удалить.


(base) maks_nekrasovmail.ru@Mac ~ % docker stop web-server
web-server
(base) maks_nekrasovmail.ru@Mac ~ % docker rm web-server
web-server
Проверим список контейнеров

(base) maks_nekrasovmail.ru@Mac ~ % docker ps -a
CONTAINER ID   IMAGE                              COMMAND                  CREATED       STATUS                     PORTS                              NAMES
896b491051df   ubuntu                             "bash"                   2 hours ago   Exited (0) 2 hours ago                                        hardcore_raman
3e298c9edb64   hello-world                        "/hello"                 2 hours ago   Exited (0) 2 hours ago                                        modest_wiles
1f6335c5e6f1   mcr.microsoft.com/azure-sql-edge   "/opt/mssql/bin/perm…"   2 years ago   Exited (255) 2 years ago   1401/tcp, 0.0.0.0:1433->1433/tcp   sql

Контейнер web server отсутствует
Удалим образ

(base) maks_nekrasovmail.ru@Mac ~ % docker rmi nginx:alpine
Untagged: nginx:alpine

## Работа с томами

Создала том



(base) maks_nekrasovmail.ru@Mac ~ % docker volume create my-volume
my-volume

Запустила контейнер с томом

(base) maks_nekrasovmail.ru@Mac ~ % docker run -it --name volume-test -d -v my-volume:/data ubuntu bash
f8d9df0dde2ed7389b4bed625b36b135e91f4b6c3701fc0efbf14358e2b82a2b

Подключилась к контейнеру



(base) maks_nekrasovmail.ru@Mac ~ % docker exec -it volume-test bash
root@f8d9df0dde2e:/# 
Создала файл в томе

root@f8d9df0dde2e:/# echo "Hello from volume" > /data/test.txt

Удалила контейнер и создала новый с тем же томом. Проверила наличие файла - файл сохранился.
(base) maks_nekrasovmail.ru@Mac ~ % docker stop volume-test
volume-test
(base) maks_nekrasovmail.ru@Mac ~ % docker run -it --name volume-test2 -v my-volume:/data ubuntu bash
root@0e1b7ab66718:/# cat /data/test.txt
Hello from volume
