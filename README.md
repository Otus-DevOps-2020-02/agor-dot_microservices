# agor-dot_microservices
agor-dot microservices repository

 Запуск больше одного контейнера nginx с `--network host` не возможен
    из-за ошибки уже занятости пота,
    в отличие от запуска nginx с `--network none`, когда каждый раз создаётся отдельный network namespace.

  - Сервисы reddit_microservices запущены через `docker run` с использование двух сетей _front_net_ и _back_net_,
    так чтобы ui не имел доступа к mongodb.
    Для этого подсоединять контейнеры ко вторых сетям необходимо вручную.

  - Проведены исследования bridge-интерфейсов и сетей на docker-machine.

  - Добавлен `docker-compose.yml`,
    адаптирован под случай двух сетей (front_net, back_net),
    и параметризован с использованием файла `.env`.

  - Базовое имя проекта в docker-compose по-умолчанию - имя каталога, т.е. [src](./src).
    Чтобы изменить это можно:
      - задать переменную `COMPOSE_PROJECT_NAME` в _.env_
      - или передавать через ключ `-p, --project-name` команды `docker compose`:
       `docker-compose -p reddit up -d`

 Создан docker-compose.override.yml
 для запуска puma в режиме _debug_ с двумя воркерами,
 а также с возможностью динамического редактирования кода
