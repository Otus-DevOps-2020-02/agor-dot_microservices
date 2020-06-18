# agor-dot_microservices
agor-dot microservices repository

- Проект reddit-microservices скачан как src
- Последующие docker-команды выполняются на созданной в GCE docker-machine docker-host c внешним ip docker-host-ip
- Для каждого сервиса (post, comment, ui) создан Dockerfile и собран образ
- Контейнеры запущены с сетевыми алиасами, отличными от тех, что задаются в самих Dockerfile-ах. Dns сервисов передаются другим сервисам через --env аргументы команды docker run
```
docker run -d --network=reddit --network-alias=postdb --network-alias=commentdb mongo:latest
docker run -d --network=reddit --network-alias=post1 -e "POST_DATABASE_HOST=postdb" -e "POST_DATABASE=posts1"
docker run -d --network=reddit --network-alias=post1 -e "POST_DATABASE_HOST=postdb" -e "POST_DATABASE=posts1" pr0t0ss12/post:1.0
docker run -d --network=reddit --network-alias=comment1 -e "COMMENT_DATABASE_HOST=commentdb" -e "COMMENT_DATABASE=comments1"
docker run -d --network=reddit --network-alias=comment1 -e "COMMENT_DATABASE_HOST=commentdb" -e "COMMENT_DATABASE=comments1" pr0t0ss12/comment:1.0
docker run -d --network=reddit -p 9292:9292 -e "POST_SERVICE_HOST=post1" -e "POST_SERVICE_PORT=5000" -e "COMMENT_SERVICE_HOST=comment1" -e "COMMENT_SERVICE_PORT=9292" pr0t0ss12/ui:1.0

```
-  Произведена оптимизация (минимизация размера) образов ui и comment сервисов путём их сборки на основе Alpine-Linux
```text
pr0t0ss12/ui  1.0  770MB
pr0t0ss12/ui  3.0  207MB

```
При переносе comment и ui на alpine обнаружелась нехватка gem 'json'. После добавления и ребилда все встало как надо.

