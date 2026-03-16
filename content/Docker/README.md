## Docker - документация и практические задачи

### Практические примеры

- [Быстрый старт](/content/Docker/Docker.md)
- [Codespace (в разработке)](/content/Docker/Docs/Codespace.md)
- [Готовые образы](/content/Docker/ImageLibrary/README.md)
- [Dockerfile](/content/Docker/DockerFile/README.md)
- [Docker Compose](/content/Docker/DockerCompose/DockerCompose.md)
- []()
- []()

### Видео

- [Docker Для Начинающих за 1 Час / Docker с Нуля](https://rutube.ru/video/b60fe155ceb1fbe0edc837681fd51ef3/)
- [Docker - Полный курс Docker Для Начинающих [3 ЧАСА]](https://rutube.ru/video/e2ee9fbaa95ba1fc563e548529bb83e1/)
- [Docker. Что это такое? | Docker для начинающих](https://rutube.ru/video/c405ceaf110c3d144a90a46f2694fc9d/)
- []()
- []()

### Документация

- [Что такое Docker?](/content/Docker/ThatIsDocker.md)
- [Docker Compose](/content/Docker/DockerCompose.md)
- [Dockerfile](/content/Docker/Dockerfile&DockerCompose.md)
- [Docker Hub](/content/Docker/DockerHub.md)
- [Docker образ](/content/Docker/DockerImages.md)
- [Docker-сети](/content/Docker/Network.md)
- [Prune](/content/Docker/Prune.md)
- [Stop и Down](/content/Docker/stopDown.md)
- [Жизненный цикл Docker-образа](/content/Docker/DockerImageLifecycle.md)
- [CLI Cheat Sheet](https://www.docker.com/resources/cli-cheat-sheet/)
- [Шпаргалка по Docker(моя)](/content/Docker/DockerReminder.md)
- [Шпаргалка по Docker на Alt Wiki](https://www.altlinux.org/Docker_Reminder)

### Полезные ссылки

- [DockerHub](https://hub.docker.com/)
- []()
- []()


# 🐳 Docker: История, Описание и Экосистема

![Docker Logo](https://cdn.iconscout.com/icon/free/png-256/docker-226068.png)  
*(Логотип Docker)*

**Docker** — это платформа с открытым исходным кодом для разработки, доставки и запуска приложений в изолированных средах, называемых **контейнерами**.

Этот документ содержит обзор истории Docker, его текущего состояния, а также описание ключевых инструментов: Docker Hub, Dockerfile и Docker Compose.

---

## 📑 Содержание

1. [Что такое Docker?](#-что-такое-docker)
2. [История появления и развития](#-история-появления-и-развития)
3. [Современное состояние](#-современное-состояние)
4. [Docker Hub и готовые образы](#-docker-hub-и-готовые-образы)
5. [Dockerfile](#-dockerfile)
6. [Docker Compose](#-docker-compose)
7. [Полезные ссылки](#-полезные-ссылки)

---

## 🔍 Что такое Docker?

Docker позволяет упаковать приложение со всеми его зависимостями (библиотеки, конфигурационные файлы, переменные окружения) в единый объект — **контейнер**.

### Ключевые отличия от виртуальных машин (VM):
| Характеристика | Виртуальные машины (VM) | Контейнеры (Docker) |
| :--- | :--- | :--- |
| **Изоляция** | Полная (своя ОС) | Процессная (общее ядро ОС) |
| **Размер** | Гигабайты | Мегабайты |
| **Запуск** | Минуты | Секунды |
| **Производительность** | Ниже (оверхед гипервизора) | Ближе к нативной |

---

##  История появления и развития

### Предыстория (до 2013)
Технологии изоляции процессов существовали давно:
*   **1979:** `chroot` в Unix (изоляция файловой системы).
*   **2000-е:** FreeBSD Jails, Linux VServer.
*   **2008:** Появление **LXC (Linux Containers)** — первый полноценный менеджер контейнеров.

### Рождение Docker (2013)
*   **Компания:** DotCloud (стартап, занимающийся PaaS).
*   **Создатель:** Соломон Хайкс (Solomon Hykes).
*   **Событие:** На конференции PyCon 2013 был представлен Docker как удобный инструмент поверх LXC.
*   **Успех:** Благодаря простоте использования и концепции "образов" (images), Docker стал стандартом де-факто за считанные месяцы. DotCloud переименовали в **Docker Inc.**

### Эпоха стандартизации (2015–2017)
*   **2015:** Создание **OCI (Open Container Initiative)** под эгидой Linux Foundation. Цель — стандартизировать формат контейнеров, чтобы они запускались везде одинаково.
*   **2017:** Docker Inc. передает проект контейнеризации (runtime) сообществу под названием **Moby Project**.
*   **Kubernetes:** Оркестратор Kubernetes становится стандартом для управления кластерами контейнеров, вытесняя Docker Swarm из продакшена крупных компаний.

### Лицензионные изменения (2020–настоящее время)
*   **2020:** Docker Desktop становится платным для крупных предприятий (более 250 сотрудников или $10 млн выручки).
*   **Альтернативы:** Рост популярности **Podman** (daemonless, от Red Hat) и **Colima** (для macOS).

---

## 🌍 Современное состояние

На сегодняшний день Docker остается главным инструментом для локальной разработки и CI/CD пайплайнов.

1.  **Стандарт индустрии:** Большинство облачных провайдеров (AWS, Google Cloud, Azure) поддерживают запуск контейнеров OCI.
2.  **Kubernetes:** Хотя в самом Kubernetes Docker Engine как runtime был устарен (в пользу containerd), Docker по-прежнему используется для *сборки* образов, которые затем запускаются в K8s.
3.  **Безопасность:** Улучшены сканеры уязвимостей, внедрено подписывание образов (Docker Content Trust).
4.  **DevEnvironments:** Появление облачных сред разработки (GitHub Codespaces, Gitpod), использующих контейнеры "под капотом".

---

## 🗄️ Docker Hub и готовые образы

**Docker Hub** — это публичный реестр (registry) для хранения и распространения Docker-образов. Аналог GitHub, но для бинарных образов приложений.

### Типы образов:
1.  **Official Images:** Поддерживаются самой компанией Docker и авторами ПО (например, `nginx`, `python`, `postgres`). Наиболее безопасны.
2.  **Verified Publishers:** Образы от проверенных компаний.
3.  **User Images:** Созданы сообществом. Требуют осторожности при использовании в продакшене.

### Пример использования:
```bash
# Поиск образа
docker search nginx

# Скачивание образа
docker pull nginx:latest

# Запуск контейнера из образа
docker run -d -p 80:80 --name my-web-server nginx
```

---

## 📝 Dockerfile

**Dockerfile** — это текстовый файл с инструкциями по сборке Docker-образа.

### Основные инструкции:
*   `FROM`: Базовый образ (например, `ubuntu`, `python:3.9`).
*   `WORKDIR`: Установка рабочей директории внутри контейнера.
*   `COPY` / `ADD`: Копирование файлов с хоста в контейнер.
*   `RUN`: Выполнение команд во время сборки (установка пакетов).
*   `EXPOSE`: Документирование порта (не открывает его автоматически).
*   `CMD` / `ENTRYPOINT`: Команда, запускаемая при старте контейнера.

### Пример Dockerfile (Python приложение):
```dockerfile
# Базовый образ
FROM python:3.9-slim

# Рабочая директория
WORKDIR /app

# Копирование зависимостей
COPY requirements.txt .

# Установка зависимостей
RUN pip install --no-cache-dir -r requirements.txt

# Копирование кода приложения
COPY . .

# Порт, который слушает приложение
EXPOSE 8000

# Команда запуска
CMD ["python", "main.py"]
```

**Сборка образа:**
```bash
docker build -t my-python-app .
```

---

## 🎼 Docker Compose

**Docker Compose** — это инструмент для определения и запуска многоконтейнерных приложений Docker. Использует файл `docker-compose.yml` (формат YAML).

Идеально подходит для локальной разработки, когда приложение состоит из нескольких сервисов (например: Бэкенд + База данных + Кэш).

### Пример docker-compose.yml:
```yaml
version: '3.8'

services:
  # Сервис базы данных
  db:
    image: postgres:15
    environment:
      POSTGRES_PASSWORD: example
    volumes:
      - pgdata:/var/lib/postgresql/data

  # Сервис приложения
  web:
    build: .
    ports:
      - "8000:8000"
    depends_on:
      - db
    environment:
      DATABASE_URL: postgres://postgres:example@db:5432/mydb

volumes:
  pgdata:
```

### Основные команды:
```bash
# Запуск всех сервисов
docker-compose up -d

# Просмотр логов
docker-compose logs -f

# Остановка и удаление контейнеров
docker-compose down
```

---

## 🔗 Полезные ссылки

*   [Официальная документация Docker](https://docs.docker.com/)
*   [Docker Hub](https://hub.docker.com/)
*   [Игра для обучения Docker (Play with Docker)](https://labs.play-with-docker.com/)
*   [Best practices for writing Dockerfiles](https://docs.docker.com/develop/develop-images/dockerfile_best-practices/)
*   [Open Container Initiative (OCI)](https://opencontainers.org/)
