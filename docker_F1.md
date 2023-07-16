для busybox (linux)
запуск sh:

docker run -i -t

docker run -it <name>

i - interactive
t - terminal

hostname - имя

hostname -i ip адрес

ping 8.8.8.8

Ctrl + c - прерываение пинга

docker images - все образы Docker, доступные на локальной машине

docker ps - запущенные контейнеры

docker ps -a - все контейнеры

docker ps -q - только идентификаторы контейнеров

docker stop $(docker ps -q) - остановка всех запущенных контейнеров

docker stop <id/name>

docker container prune удаление всех остановленных контейнеров

### для nginx

docker run nginx

docker run -d nginx - запуск в фоновом режиме без подключения к процессу

docker container inspect <id/name>

docker container inspect <id/name> | grep IPAdress <some_detail>

Команда grep не распознается в окружении Windows PowerShell, поскольку это команда, характерная для UNIX-подобных систем. Вместо использования grep, вы можете воспользоваться возможностями фильтрации, предоставляемыми PowerShell

docker container inspect 9d25c52fb687 | Select-String -Pattern 'IPAddress'

