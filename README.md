# agor-dot_microservices
agor-dot microservices repository

Команда параметр --pid host запускает контейнер в неймспейсе хостовой машины и он видит все ее процессы.

Установлены docker, docker-compose, docker-machine, gcloud-sdk. В GCP создан проект Docker. С помощью docker-machine создана виртуалка docker-host. Написан Dockerfile для устновки mongodb, ruby и приложения reddir в контейнере. Создан образ и залит на DockerHub.