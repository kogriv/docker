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

docker container prune удаление всех остановленных контейнеров

