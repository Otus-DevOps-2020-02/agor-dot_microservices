# agor-dot_microservices
agor-dot microservices repository

 ###Устройство Gitlab CI. Построение процесса непрерывной поставки

 - Развернули Gitlab CI через Docker образ в режиме Omnibus
 - Зашли под пользователем root и скофигурировали безопасноть.
 - Создали группу проектов homework и проект example
 - Добавили наши исходники в проект и запушили его на CI
 - Создали pipeline и поигрались с ним в stag-и , job-ы, environment
 - Создали и зарегистрировали runner
 - Залили исходники reddit. создали Job для его сборки и деплоя
 - Сконфигурировали создание динамических окружений

###Введение в мониторинг. Системы мониторинга.

Ссылки на репы:

https://hub.docker.com/repository/docker/pr0t0ss12/prometheus
https://hub.docker.com/repository/docker/pr0t0ss12/post
https://hub.docker.com/repository/docker/pr0t0ss12/comment
https://hub.docker.com/repository/docker/pr0t0ss12/ui

- Развернули контейнер с Prometheus - посмотрели его встроенные метрики
- В ранее созадную конфигурацию микросервисов внесли сервис по мониторингу, и проверили что они выключились в endpoint
- Проверили health-checks для нашей конфигурации микросервисов
- Добавили NodeExporter в конфигурацию. проверили ее работу
