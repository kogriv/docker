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

docker exec -it <id/name> <process: bash/sh..> - запуск доп процесса

Посмотрим страницу

cd /usr/share/nginx/html

cat index.html

docker run -d --name <name> <image_name> - создание контейнера с именем

docker run (-d) -p 8080:80 nginx - мэппинг портов -p publish

0.0.0.0:8080->80/tcp - можно вводить люой IP (lockalhost, 127.0.0.1)

docker run -v ${PWD}:/usr/share/nginx/html -p 8080:80 -d nginx - мэппинг томов -v. ${PWD} - переменная для пути к локальной папке

docker run -it --rm busybox - автоматическое удаление контейнера опцией --rm

Пример с переносом строк:
docker run \
  --name my-nginx \
  -v ${PWD}:/usr/share/nginx/html \
  -p 8888:80 \
  -d \
  --rm \
  nginx

В PowerShell для переноса строки можно использовать символ обратного апострофа "`" вместо "\"

docker run `
   --name my-nginx `
   -v ${PWD}:/usr/share/nginx/html `
   -p 8888:80 `
   -d `
   --rm `
   nginx

docker rmi <имя_образа>:<тег> - Для удаления образа Docker с вашего компьютера

docker login

docker rmi <имя_репозитория>/<имя_образа>:<тег> - удаление в репозитории

docker search <имя_пользователя_в_Docker_Hub> - Для просмотра образов в вашем репозитории на Docker Hub

docker build -t stable_image:1.0 -f path/to/Dockerfile.stable .

docker build -t final_image:1.0 -f path/to/Dockerfile.final --build-arg имя_стабильного_образа=stable_image:1.0 .

docker build -t ocr_5_base:1.0 -f Dockerfile.stable .

docker build -t ocr_5_model:1.0 -f Dockerfile.final .

docker run --rm -d -p 8010:8000 --name ocr ocr_5_model:1.0

docker stop ocr
docker rm ocr
docker rmi ocr_5_model:1.0
docker build -t ocr_5_model:1.0 -f Dockerfile.final .
docker run --rm -d -p 8010:8000 --name ocr ocr_5_model:1.0
docker run -d -p 8010:8000 --name ocr ocr_5_model:1.0
docker logs ocr
